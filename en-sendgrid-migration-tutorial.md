---

copyright:
  years: 2026
lastupdated: "2026-10-01"

keywords: sendgrid migration, email migration, smtp migration, event notifications migration

subcollection: event-notifications

content-type: tutorial
services: event-notifications
account-plan: standard
completion-time: 2h

---

{{site.data.keyword.attribute-definition-list}}

# Migrating from SendGrid to {{site.data.keyword.en_short}}
{: #sendgrid-migration-tutorial}
{: toc-content-type="tutorial"}
{: toc-services="event-notifications"}
{: toc-completion-time="2h"}

This tutorial guides you through migrating your email delivery service from SendGrid to {{site.data.keyword.en_full}}. You can migrate using either SMTP or the Custom API method, depending on your current implementation.
{: shortdesc}

During the transition from SendGrid to {{site.data.keyword.en_short}}, there is no downtime. However, certain configurations need to be changed and authorizations obtained (24-48 hours). Keep your SendGrid accounts active during this transition to ensure no disruption to your service.
{: important}

## Objectives
{: #sendgrid-migration-objectives}

In this tutorial, you will:
- Create an {{site.data.keyword.en_short}} instance
- Configure email delivery using SMTP or Custom API
- Verify your custom domain
- Set up context-based restrictions
- Configure email subscriptions
- Monitor email metrics

## Before you begin
{: #sendgrid-migration-prereqs}

Before you start the migration, ensure you have:

- An {{site.data.keyword.cloud_notm}} account with appropriate permissions.
- Your SendGrid configuration details (SMTP endpoint, port, credentials).
- A custom domain for sending emails.
- Access to your DNS records for domain verification.

## Create an {{site.data.keyword.en_short}} instance
{: #sendgrid-migration-create-instance}
{: step}

First, create an {{site.data.keyword.en_short}} instance with the Standard plan, which includes email capabilities.

1. In the {{site.data.keyword.cloud_notm}} console, go to the [catalog](https://cloud.ibm.com/catalog#all_products).

2. Search for **Event Notifications** and select the service.

3. Select the **Standard** plan for production use.

4. Configure your instance:
   - Enter a service name
   - Select a resource group
   - Choose a region

5. Review the summary and click **Create**.

After successful creation, you are redirected to the {{site.data.keyword.en_short}} **Overview** page.

## Create an API key
{: #sendgrid-migration-create-apikey}
{: step}

Before configuring email delivery, create an API key for your {{site.data.keyword.en_short}} instance.

1. In the {{site.data.keyword.cloud_notm}} console, go to **Manage** > **Access (IAM)**.

2. Click **API keys** in the navigation.

3. Click **Create**.

4. Enter a name and description for your API key.

5. Click **Create** and save the API key securely.

You need this API key for SDK integration and authentication.
{: tip}

## Choose your migration path
{: #sendgrid-migration-choose-path}
{: step}

{{site.data.keyword.en_short}} supports two methods for sending emails. Choose the method that best matches your current SendGrid implementation:

SMTP interface
:   Use this method if you currently use SendGrid's SMTP relay. This requires minimal code changes and works with existing SMTP client libraries.

Custom API
:   Use this method if you want to integrate {{site.data.keyword.en_short}} directly into your application using the SDK. This provides more flexibility and features like templates and subscription management.

The following sections provide detailed steps for both methods. Complete only the section that matches your chosen migration path.

### Option 1: Migrate using SMTP
{: #sendgrid-migration-smtp}
{: step}

Follow these steps if you are migrating from SendGrid SMTP to {{site.data.keyword.en_short}} SMTP.

#### Add an SMTP configuration
{: #sendgrid-migration-smtp-add}
{: step}

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** in the navigation.

2. Click **Add**.

3. Enter the following information:
   - **Name**: A descriptive name for your SMTP configuration
   - **Description**: Optional description
   - **Domain**: Your custom domain (for example, `notifications.example.com`)

4. Click **Add**.

Your domain appears in the SMTP configurations list with a "Not verified" status.

#### Verify your domain
{: #sendgrid-migration-smtp-verify}
{: step}

Domain verification requires three steps: Event Notification authorization, SPF verification, and DKIM verification.

##### Request Event Notification authorization
{: #sendgrid-migration-smtp-auth}
{: step}

1. Click the **Help** icon in the console header and select **Support Center**.

2. Click **Create a case**.

3. Configure the support case:
   - **Category**: Event Notifications
   - **Topic**: Event Notifications
   - **Subtopic**: Others
   - **Subject**: Requesting for the Authorization to enable SMTP Interface for Event Notifications

4. In the **Description** field, provide:
   - {{site.data.keyword.en_short}} instance ID
   - Region where the instance was created
   - DKIM name in the format `{{uuid}}._domainkey.{{domain}}`

5. Answer the questions in the description. For sample answers to help you complete this step, see the [Sample answers](/docs/event-notifications?topic=event-notifications-en-email-sender-questionnaire#en-email-sender-questionnaire-sample-answers) section of the Email sender verification questionnaire. The additional questions for the opt-out request do not apply here.

6. Click **Submit**.

Authorization typically takes 24-48 hours.
{: note}

##### Verify SPF and DKIM records
{: #sendgrid-migration-smtp-dns}
{: step}

1. In the SMTP configurations list, click the actions menu (⋯) next to your domain.

2. Click **Verify**.

3. Copy the SPF and DKIM TXT values displayed in the UI.


4. Add the TXT records through your DNS provider.

5. After the DNS records are added and propagated, click **Verify** in the {{site.data.keyword.en_short}} console.

DNS propagation can take up to 72 hours.
{: important}

All three verification statuses (Event Notification Authorization, SPF, DKIM) must show "Verified" before proceeding.

#### Configure context-based restrictions
{: #sendgrid-migration-smtp-cbr}
{: step}

Set up context-based restrictions to control access to your SMTP configuration.

1. In your {{site.data.keyword.en_short}} instance, click **Manage context-based restrictions**.

2. Click **Create**.

3. Select **Event Notifications** as the service.

4. Select **SMTP Configuration** in the APIs field.

5. Choose whether to scope restrictions to all resources or specific resources.

6. Create a network zone:
   - Click **Create** in the Network zones section.
   - Add all allowed IP addresses and VPCs.
   - Click **Create**.

7. Select the network zone you created.

8. Click **Add**.

9. Review the details and click **Create**.

#### Generate SMTP credentials
{: #sendgrid-migration-smtp-credentials}
{: step}

1. In the SMTP configurations list, click the actions menu (⋯) next to your verified domain.

2. Click **Settings**.

3. Click **Create credentials**.

4. Save the following information securely:
   - SMTP endpoint
   - STARTTLS port
   - Username

5. Create a Service ID and configure your {{site.data.keyword.en_short}} instance as part of an access policy. To learn how to create and configure Service IDs, see [Creating and working with service IDs](/docs/iam?topic=iam-serviceids&interface=ui) and [Assigning access in the console](/docs/iam?topic=iam-account-services&interface=ui).

6. Assign the SMTP role to the Service ID. This role grants the Service ID permission to authenticate to the SMTP interface. Confirm your access policy, resource, and the role.

7. Create one or more API keys for the Service ID. To learn how to create and manage API keys, see [Managing service ID API keys](/docs/iam?topic=iam-serviceidapikeys&interface=ui).

8. Use the API key as the password when authenticating to the SMTP interface. The username remains the SMTP username you received in step 4.

Password-based SMTP authentication is deprecated. Use a Service ID API key as your SMTP password instead.
{: important}

#### Update your application
{: #sendgrid-migration-smtp-update}
{: step}

Update your application code to use the new {{site.data.keyword.en_short}} SMTP credentials:

```javascript
const smtpConfig = {
  smtpServer: '<smtp_endpoint>',
  smtpPort: '<STARTTLS_port>',
  username: '<smtp_username>',
  password: '<service_id_api_key>'   // Use the Service ID API key, not a plain password
};
```
{: codeblock}

Replace the SendGrid SMTP configuration with these values in your email client. Use the Service ID API key you created as the `password` value.

### Option 2: Migrate using Custom API
{: #sendgrid-migration-api}
{: step}

Follow these steps if you want to use the {{site.data.keyword.en_short}} Custom API for more advanced features.

#### Create an API source
{: #sendgrid-migration-api-source}
{: step}

1. In your {{site.data.keyword.en_short}} instance, click **Sources** in the navigation.

2. Click **Add** > **API Source**.

3. Enter a name and description for your API source.

4. Click **Add**.

5. Note the source ID that is generated. You need this for SDK integration.

#### Integrate the SDK
{: #sendgrid-migration-api-sdk}
{: step}

Integrate the {{site.data.keyword.en_short}} SDK into your application. The SDK requires the source ID, instance ID, and service credentials.

For detailed SDK documentation, see the [API documentation](/apidocs/event-notifications).

#### Create a custom email destination
{: #sendgrid-migration-api-destination}
{: step}

1. In your {{site.data.keyword.en_short}} instance, click **Destinations** in the navigation.

2. Click **Add**.

3. Select **Custom Email** as the destination type.

4. Enter your custom domain name.

5. Click **Add**.

Your domain appears in the destinations list with a "Not verified" status.

#### Verify your custom domain
{: #sendgrid-migration-api-verify}
{: step}

1. In the destinations list, click the actions menu (⋯) next to your domain.

2. Click **Configure**.

3. Copy the SPF and DKIM TXT values displayed.


4. Add the TXT records through your DNS provider.

5. After the DNS records are added and propagated, click **Verify**.

Both SPF and DKIM statuses must show "Verified" before proceeding.

#### Create a topic, migrate your template, and set up a subscription
{: #sendgrid-migration-api-topic}
{: step}

In {{site.data.keyword.en_short}}, topics, filters, and subscriptions are configured together in a single guided flow. You can also migrate your SendGrid template as part of this process.

**Step 1: Migrate your SendGrid template**

Before setting up routing, migrate your SendGrid email template so it is ready to select during subscription creation.

1. In SendGrid, open the template you want to migrate and copy its Handlebars template content.

2. In your {{site.data.keyword.en_short}} instance, click **Templates** in the navigation menu.

3. Click **Create** to create a new user-defined template.

4. Enter a **Name** and optional **Description** for your template.

5. Select **Custom Email** as the template type.

6. Enter a **Subject line** for the email.

7. Paste the SendGrid template content into the **Body** area.

8. Click **Create** to save the template.

**Step 2: Create a topic with filters and a subscription**

1. Click **Topics** in the navigation.

2. Click **Create**.

3. Enter a **Name** and optional **Description** for your topic.

4. Select the API source you created and add filter conditions to route the right events:
   - Click **Add a condition**.
   - Define your filter using JSONPath expressions.
   - Click **Add a condition** to add more filters if needed.

   For more information about JSONPath, see the [JSONPath documentation](https://goessner.net/articles/JsonPath/).

5. Click **Next** to go to the **Subscriptions** step.

6. Optional: Click **Create subscription** and enter the following details:
   - **Name**: Enter a descriptive name for the subscription.
   - **Destination type**: Select **Custom Email**.
   - **Destination**: Select the custom email destination you created.
   - **Template**: Select the template you migrated from SendGrid.
   - **Recipients**: Add the recipient email addresses.

   Click **Create subscription**.

8. Click **Next** to review your configuration, then click **Save**.

Recipients receive an opt-in email with a link to subscribe. You can track active and unsubscribed recipients in the subscription details.

##### Request opt-out (optional)
{: #sendgrid-migration-api-optout}
{: step}

If you want to manage your own subscription list without the opt-in flow, you can request an appoval to opt out. You can then send the recipient list in the payload.
Follow these steps to request approval for the opt out feature.

1. Click the **Help** icon and select **Support Center**.

2. Click **Create a case**.

3. Configure the support case:
   - **Category**: Event Notifications
   - **Topic**: Event Notifications
   - **Subtopic**: Others
   - **Subject**: Requesting for the Opt Out feature for the Custom Domain Email Destination

4. In the **Description** field, provide:
   - {{site.data.keyword.en_short}} instance ID
   - Region where the instance was created

5. Answer the questions in the description. For the full list of questions and sample answers to help you complete this step, see [Email sender verification questionnaire](/docs/event-notifications?topic=event-notifications-en-email-sender-questionnaire).

6. Click **Submit**.

## Monitor email metrics
{: #sendgrid-migration-monitor}
{: step}

{{site.data.keyword.en_short}} provides metrics to track email delivery and bounce rates.

1. Click **Metrics** in the navigation.

2. Select the metric type:
   - **Custom email destination**: View metrics for API-based email delivery
   - **SMTP configuration**: View metrics for SMTP-based email delivery

3. Review the following metrics:
   - Emails sent
   - Emails delivered
   - Bounce rate
   - Open rate (if tracking is enabled)

Use these metrics to monitor the health of your email delivery and identify issues.

## Next steps
{: #sendgrid-migration-next}

After completing the migration:

- Test email delivery thoroughly before decommissioning SendGrid.
- Monitor email metrics for the first few weeks.
- Set up alerts for bounce rates and delivery failures.
- Review and optimize your email templates.
- Consider implementing [email best practices](/docs/event-notifications?topic=event-notifications-en-email-bestpractices).

## Related information
{: #sendgrid-migration-related}

- [{{site.data.keyword.en_short}} API documentation](/apidocs/event-notifications)
- [{{site.data.keyword.en_short}} pricing](/docs/event-notifications?topic=event-notifications-en-new-pricing)
- [SMTP configurations](/docs/event-notifications?topic=event-notifications-en-smtp-configurations)
- [Email best practices](/docs/event-notifications?topic=event-notifications-en-email-bestpractices)
- [Custom Domain Email Opt-out functionality](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out)
