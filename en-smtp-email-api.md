---
copyright:
  years: 2021, 2026
lastupdated: "2026-11-09"

keywords: event-notifications, event notifications, custom domain email, API, email, sandbox, production, configure email

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Configuring custom domain email
{: #en-destinations-custom-email-api}

Use the **API** tab in **SMTP configurations** > **Configure email** to set up custom domain email for the {{site.data.keyword.en_short}} API. The **Create API Email** flow sets up a custom domain email destination, a subscription, and an automatically created default topic and API source in two steps.
{: shortdesc}

Each {{site.data.keyword.en_short}} instance supports only one Sandbox configuration.
{: restriction}

For more information about Sandbox and Production modes, see [Custom domain email](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email).

Custom domain email is available only for Standard plan instances.
{: note}

## Selecting a domain
{: #en-destinations-custom-email-api-domain}

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Configure email**, and select the **API** tab.
2. Click **Create API**.
3. Enter a **Name** and **Description**. These values are used as the subscription name and description.
4. Under **Configuration type**, select **Sandbox** or **Production**.
   - **Sandbox**: Use for testing. Email delivery is limited to 10 recipients, and Sandbox is not intended for production use.
   - **Production**: Use for live email sending to up to 10,000 recipients.
5. Under **Verified domain**, select the domain that your emails are sent from in the **Domain** list. Only verified domains are shown. If your domain is not listed, click **Verify domain** to complete domain verification first.
6. Click **Next** and configure **Subscriptions**.

## Configuring subscriptions
{: #en-destinations-custom-email-api-subscriptions}

1. Under **Sender details**, enter the **Sender name**, **Sender email**, **Reply to name**, and **Reply to email**.

2. Under **Receiver details**, you can add up to 10 recipients for a Sandbox configuration, or up to 10,000 recipients for a Production configuration. The recipients are notified about events that are routed to the topic that belongs to the subscription. Add recipients by using one of the following methods:
   1. Enter email addresses in the **Receiver email** field, separated by commas, and click **Add**. Or,
   2. Click **Bulk upload**, and select a file of recipient addresses in the file browser. The maximum file size is 500 KB. The supported formats are `.csv` and `.txt`.

3. Under **Template (optional)**, select a template from the **Invitation template** tab or the **Notification template** tab. After you select a template, its content is shown. 

4. Under **Topic configuration**, review the **Automatic topic creation** message. {{site.data.keyword.en_short}} automatically creates a default topic and API source to send this email. The auto-generated names are shown in the **Default topic name** and **Default source name** fields. You can view and manage them later in **Topics** and **Sources**.
5. Click **Create**. The configuration appears in the **API** list.

To edit, delete, or upgrade an existing API configuration, click the overflow menu (⋮) for the configuration in the **API** list and select **Edit**, **Delete**, or **Upgrade**.

To change the topic or source later, see [Creating a topic](/docs/event-notifications?topic=event-notifications-en-route-create-topic) and [Creating subscriptions](/docs/event-notifications?topic=event-notifications-en-route-create-subscriptions).

To specify recipients and templates in the send notifications payload instead of using subscriptions, see [Requesting the opt-out capability](#en-destinations-custom-email-api-opt-out).

## Requesting the opt-out capability
{: #en-destinations-custom-email-api-opt-out}

Custom domain email configuration includes a default subscription process, where you specify your preferred email addresses and templates. The **{{site.data.keyword.en_short}} authorization status** of your domain is tagged **Optional for API**, so you can send email over the API without it.

If you prefer to customize the subscription experience, you can opt out of the default process by completing a questionnaire that helps {{site.data.keyword.en_short}} detect unauthorized activities and protect your reputation as a sender. You request the opt-out capability through a support case. For the questionnaire (Q1–Q10), the support case steps, and the rules that apply after opt-out is enabled, see [Custom domain email opt-out functionality](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out).

## Upgrading from Sandbox to Production
{: #en-destinations-custom-email-api-upgrade}

After you complete testing in sandbox mode and are ready to send notifications to real recipients, you can upgrade your sandbox configuration to production mode. Upgrading removes the sandbox domain and recipient limits, enabling live application workloads up to 10,000 recipients.

To upgrade from sandbox to production:

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Configure email**, and select the **API** tab.
2. Locate your sandbox configuration in the configurations list.
3. Click the overflow menu (⋮) for the configuration, and select **Upgrade**. Alternatively, select **Edit** and change **Configuration type** to **Production**.
4. Under **Verified domain**, select a verified domain from the list. If your domain is not yet verified, complete domain verification first. For more information, see [Verifying an email domain](/docs/event-notifications?topic=event-notifications-en-email-domains#en-email-domains-verify).
5. Click **Next** to update your subscription sender details, recipients, or templates as needed.
6. Click **Save** to complete the upgrade.

After the upgrade is complete, your configuration operates in production mode with your verified domain.
