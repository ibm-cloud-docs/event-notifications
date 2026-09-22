---

copyright:
  years: 2026
lastupdated: "2026-09-22"

keywords: event-notifications, event notifications, email, smtp, questionnaire, sample answers, sender verification

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Email sender verification questionnaire
{: #en-email-sender-questionnaire}

When you request enablement of the SMTP interface or the custom domain email opt-out capability, you must complete a questionnaire to verify that you are a responsible email sender. This topic provides the full list of questions, guidance on how to answer each question, and sample answers to help you complete the questionnaire.
{: shortdesc}

The questionnaire is required for the following requests:
- [Enabling the SMTP interface](/docs/event-notifications?topic=event-notifications-en-smtp-configurations#en-smtp-configurations-requirements)
- [Requesting the custom domain email opt-out capability](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out)

## Common questions
{: #en-email-sender-questionnaire-sample-answers}

The following questions apply to both the SMTP interface request and the custom domain email opt-out request.

### Q1. Will the nature of the email content be Marketing or Transactional?
{: #en-email-sender-questionnaire-q1}

**How to answer:** State whether the emails are marketing, transactional, or a combination of both. Briefly describe the purpose of the emails and what typically triggers them.

**Sample answer:**
> The emails are primarily transactional in nature. They are triggered by application events, user actions, or system activity, such as account notifications, workflow updates, or service alerts. No promotional or marketing content is included.

### Q2. What is your website's URL?
{: #en-email-sender-questionnaire-q2}

**How to answer:** Provide the primary website or domain associated with your organization, application, or service. You can provide your organization's primary public-facing website and briefly explain its relationship to the application or service using {{site.data.keyword.en_short}}.

**Sample answer:**
> `https://www.your-organization.com`

### Q3. Explain how you plan to use IBM Cloud Event Notifications to send email.
{: #en-email-sender-questionnaire-q3}

#### a. What is your strategy for creating or obtaining your email subscriber list?
{: #en-email-sender-questionnaire-q3a}

**How to answer:** Explain where recipient email addresses come from and how you determine who is eligible to receive notifications. If applicable, clarify that recipients are not obtained through purchased or third-party lists.

**Sample answer:**
> Recipients are sourced from users or customers who are registered or authorized to use the application. Email addresses are maintained through the organization's user, account, or identity-management processes, and notifications are sent only to recipients who are eligible to receive the applicable communication.

#### b. What is your approach to managing bounced emails and handling recipient complaints?
{: #en-email-sender-questionnaire-q3b}

**How to answer:** Describe how you monitor delivery failures and recipient complaints, and what actions you take when an address is permanently undeliverable or a complaint is received.

**Sample answer:**
> We monitor email delivery results and have processes in place to identify and address bounced emails and recipient complaints. Permanently undeliverable addresses are removed or suppressed from future sends, while complaints are reviewed by the appropriate operations or support team. Recurring issues are evaluated to improve recipient data and notification practices.

#### c. What methods do you have in place for recipients to unsubscribe from your email communications?
{: #en-email-sender-questionnaire-q3c}

**How to answer:** Explain how recipients can manage their notification preferences, particularly for optional communications. If some notifications are mandatory, explain how those are handled.

**Sample answer:**
> Recipients can manage their notification preferences through mechanisms such as in-application settings or an unsubscribe option for applicable notification types.

#### d. How did you determine the sending rate or quota specified in your request?
{: #en-email-sender-questionnaire-q3d}

**How to answer:** Explain how you estimated your expected email volume. Consider factors such as your user base, notification frequency, expected event volume, peak usage, and any capacity buffer.

**Sample answer:**
> The requested quota was estimated based on expected operational usage, including the number of eligible recipients, anticipated notification frequency, expected event volume, and potential peak or burst traffic. Additional capacity may be included to accommodate variations in usage.

#### e. Are you regularly cleaning your email list to remove invalid or outdated email addresses?
{: #en-email-sender-questionnaire-q3e}

**How to answer:** Describe how you keep recipient information current and how invalid or inactive addresses are identified and handled.

**Sample answer:**
> Recipient information is maintained through normal user and account lifecycle processes. Invalid or permanently undeliverable addresses are identified through delivery feedback and are removed or suppressed from future communications. Recipient data is also reviewed periodically to help maintain an accurate and current list.

### Q4. Indicate the email addresses for account-related communications. You can provide a list of up to four email addresses, separated by commas.
{: #en-email-sender-questionnaire-q4}

**How to answer:** Provide active, monitored email addresses for the people or teams responsible for the IBM Cloud account, {{site.data.keyword.en_short}} instance, or related operations.

**Sample answer:**
> `platform-owner@your-org.com, it-admin@your-org.com`

### Q5. In the Event Notifications subscription, you are asked to provide a Reply-To field. Confirm that this is a valid email address with an active mailbox.
{: #en-email-sender-questionnaire-q5}

**How to answer:** Confirm that the Reply-To address is valid, active, and monitored by an appropriate team.

**Sample answer:**
> We confirm that the Reply-To address is a valid and active mailbox monitored by the appropriate platform, operations, or support team. Replies received at this address can be reviewed and handled by the responsible team.

### Q6. Include a statement affirming your commitment to sending emails only to individuals who have explicitly requested them, and verify that you have established a procedure for managing bounce and complaint notifications.
{: #en-email-sender-questionnaire-q6}

**How to answer:** Confirm that emails are sent only to appropriate recipients and briefly describe how you manage bounces, complaints, and recipient eligibility.

**Sample answer:**
> We confirm that emails are sent only to authorized or eligible recipients associated with our application or service. We maintain processes to monitor delivery outcomes, suppress invalid or permanently bounced addresses, and review recipient complaints. No unsolicited marketing or cold-outreach emails are sent through {{site.data.keyword.en_short}}.

### Q7. Confirm that you will include an unsubscribe link in your email payloads.
{: #en-email-sender-questionnaire-q7}

**How to answer:** Confirm how you will provide unsubscribe functionality for notification types where an opt-out is applicable. If some communications are mandatory, explain how those are managed.

**Sample answer:**
> We acknowledge this requirement and will provide an unsubscribe mechanism for applicable notification types. Recipients will be provided with an unsubscribe mechanism and will be removed from future notifications upon request.

### Q8. Do you have a process to validate that your email templates and HTML payloads are well formatted?
{: #en-email-sender-questionnaire-q8}

**How to answer:** Briefly describe how you test and validate email templates before they are used in production. This may include HTML validation, template testing, test emails, rendering checks, or peer review.

**Sample answer:**
> Yes. Email templates and HTML payloads are validated before production use. The process may include checking HTML formatting, testing template variables and placeholders, sending test emails to internal recipients, and reviewing rendering across common email clients.

## Additional questions for the opt-out request
{: #en-email-sender-questionnaire-opt-out}

If you are requesting the custom domain email opt-out capability, you must also answer the following additional questions in addition to the common questions above.

### Q9. Provide the reason to use your own procedure to invite or subscribe email IDs instead of using the Event Notifications provided invitation or subscription flow.
{: #en-email-sender-questionnaire-opt-out-reason}

**Sample answer:**
> Our application manages a dynamic recipient list that changes frequently based on real-time conditions. Using the {{site.data.keyword.en_short}} invitation flow introduces latency that is not acceptable for time-sensitive operational notifications. We maintain our own opt-in and unsubscribe records and take full responsibility for recipient consent management.

### Q10. Provide your Event Notifications instance ID(s) and destination ID(s) in which you want to enable customer-managed email opt-in.
{: #en-email-sender-questionnaire-opt-out-ids}

**Sample answer:**
> - {{site.data.keyword.en_short}} Instance ID(s): `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`
> - Custom Email Destination ID(s): `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`

**Guidance:** You can find the instance ID on the **Service credentials** page of your {{site.data.keyword.en_short}} instance, and the destination ID in the **Destinations** list. You can provide multiple instance and destination IDs if required.
