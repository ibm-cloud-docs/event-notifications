---
copyright:
  years: 2026, 2026
lastupdated: "2026-11-09"

keywords: event-notifications, event notifications, email domain, domain verification, SPF, DKIM, email services

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Managing email services
{: #en-email-domains}

In {{site.data.keyword.en_short}}, an email domain is a shared resource at the instance level. After you register a domain and verify it for Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM), you can reuse it across any number of custom email destinations and SMTP configurations.
{: shortdesc}

Email domains are only available for Standard plan instances.
{: note}

## Before you begin
{: #en-email-domains-prereqs}

- You need a Standard plan {{site.data.keyword.en_short}} instance.
- To create, update, or verify a domain, you need the Manager, Writer, or Administrator IAM role on the {{site.data.keyword.en_short}} instance. To delete a domain, you need the Manager or Administrator role. For more information, see [Managing access for {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-service-access-management).
- You need access to the DNS configuration for the domain you want to register.

## Viewing your domains
{: #en-email-domains-view}

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations**.
2. Click the **Domains** tab.

The table lists each domain with its description, the **Domain status**, and the **{{site.data.keyword.en_short}} authorization status**.

## Creating an email domain
{: #en-email-domains-create}

A domain name is unique within an instance. If the domain already exists on the instance, you cannot create it again.
{: restriction}

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Domains**.
2. Click **Add**.
3. In the **Add new domain** panel, enter the **Domain name**. The domain name must be a fully qualified domain name that meets the following requirements:
   - Use only lowercase alphanumeric characters and hyphens (`-`).
   - Do not start or end a domain label with a hyphen.
   - The top-level domain (TLD) must have 2 to 63 alphabetic characters.
4. Enter a **Description** and click **Add**.

After you add the domain, verify your domain records before you use the domain.

## Verifying an email domain
{: #en-email-domains-verify}

Domain verification confirms that the DNS records for your domain are set up correctly. The **Verify domain** panel shows three statuses.

SPF status
:   Required for sending email over the API and over SMTP.

DKIM status
:   Required for sending email over the API and over SMTP.

{{site.data.keyword.en_short}} authorization status
:   Required for sending email over SMTP. For enhanced security, {{site.data.keyword.en_short}} performs this verification manually, and it does not depend on your DNS records. 

SPF and DKIM are verified at the domain level and apply to all email destinations associated with the domain. To set up your domain records, complete the following steps:

1. Create Sender Policy Framework (SPF), which is used to authenticate the sender of an email. SPF specifies the mail servers that are allowed to send email for your domain.
    * Ensure that the domain already exists as an A record in the DNS records.
    * Go to your DNS hosting provider for the domain name configured.
    * Create a new TXT record with your domain name registrar with the name and value provided in the configuration screen for SPF.
2. Create DomainKeys Identified Mail (DKIM), which allows an organization to take responsibility for transmitting a message by signing it. DKIM allows the receiver to verify that an email that claims to come from a specific domain was authorized by the owner of that domain.
    * Go to your DNS hosting provider for the domain name configured.
    * Create a new TXT record with your domain name registrar with the name and value provided in the configuration screen for DKIM.

### Requesting SMTP authorization
{: #en-email-domains-verify-smtp-auth}

For enhanced security, {{site.data.keyword.en_short}} manually verifies the SMTP interface requirements. Complete the questionnaire for the common questions (Q1–Q8) described in [Email sender verification questionnaire](/docs/event-notifications?topic=event-notifications-en-email-sender-questionnaire). The additional questions for the opt-out request do not apply here.

After completing the questionnaire, request enablement of the SMTP interface verification through a support ticket:

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
2. From the **Contact support** section, click **Create a case**.
3. Under **Category**, set **Topic** to **Event Notifications** and **Subtopic** to **Others**.
4. Under **Subject**, enter **Requesting for the Authorization to Enable SMTP Interface for Event Notifications**.
5. In the **Description** section, provide the {{site.data.keyword.en_short}} `instance id`, `region`, and a `DKIM Name` in the format `{{uuid}}._domainkey.{{domain}}`.
6. Include your responses to the questionnaire.
7. Add **Attachments** if you want to provide supporting evidence.
8. Add required email addresses in the **Watchlist** section. For more information about other options, see [Creating a support case](/docs/support?topic=support-open-case&interface=ui){: external}.

### Running verification
{: #en-email-domains-verify-run}

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Domains**.
2. Click the **Actions** icon (⋯) for the domain, and select **Verify**.
3. In the **SPF** section, check the **Name** and **Value**. Click **Download** to get a TXT record with SPF name and value that can be used in your DNS hosting provider.
4. In the **DKIM** section, check the **Name** and **Value**. Click **Download** to get a TXT record with DKIM name and value that can be used in your DNS hosting provider.
5. Click **Verify** to check the status of your setup.
6. Confirm that **SPF status** and **DKIM status** show **Verified**.
7. For SMTP, also confirm that **{{site.data.keyword.en_short}} authorization status** shows **Verified** after your support case is processed.

Verification can succeed immediately, but DNS changes typically take 30 minutes to 72 hours to propagate. Your domain is ready for use only after propagation is complete.
{: note}

### Troubleshooting domain verification
{: #en-email-domains-verify-troubleshoot}

Review these common verification issues:

* Ensure that the domain name is spelled correctly.
* Verify that the DNS records for the domain are updated correctly, including SPF and DKIM values.
* DNS propagation can take up to 72 hours to update across the internet.

{{site.data.keyword.en_short}} performs periodic checks on the SPF and DKIM TXT records of the configured domain. To ensure uninterrupted email delivery, keep the records in the DNS even after verifying them. If the SPF or DKIM fails a periodic check, email sending is suspended.
{: note}

## Editing a domain
{: #en-email-domains-update}

After a domain is created, you cannot change the domain name, because the SPF and DKIM records are specific to that name. You can update only the description.

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Domains**.
2. Click the **Actions** icon (⋯) for the domain, and select **Edit**.
3. In the **Edit domain details** panel, update the **Description** and save your changes.

## Deleting a domain
{: #en-email-domains-delete}

You cannot delete a domain that is still used by a custom email destination or an SMTP configuration. Remove all linked resources first, and then delete the domain.
{: important}

1. Remove or reconfigure all custom email destinations and SMTP configurations that use the domain.
2. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations** > **Domains**.
3. Click the **Actions** icon (⋯) for the domain, and select **Delete**.
4. In the **Delete domain** dialog, enter the domain name to confirm the deletion.
5. Click **Delete**.


## Next steps
{: #en-email-domains-next}

After you add a domain, you can use it to configure email:

- To configure email over SMTP, click **SMTP configurations** > **Configure email** > **SMTP**. The {{site.data.keyword.en_short}} authorization status is required for SMTP. If you have not requested SMTP authorization, see [Requesting SMTP authorization](#en-email-domains-verify-smtp-auth). To create an SMTP configuration and generate credentials, see [Using the {{site.data.keyword.en_short}} SMTP interface](/docs/event-notifications?topic=event-notifications-en-smtp-configurations).
- To configure email over the API (custom domain email), click **SMTP configurations** > **Configure email** > **API**. For the full steps, including how to request the opt-out capability, see [Configuring custom domain email](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email-api).
- You can also create a custom email destination from the **Destinations** page.

For more information, see [{{site.data.keyword.cloud_notm}} Email Service with Custom domain](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email) and [Using the {{site.data.keyword.en_short}} SMTP interface](/docs/event-notifications?topic=event-notifications-en-smtp-configurations).
