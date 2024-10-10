---
copyright:
  years: 2021, 2024
lastupdated: "2024-01-03"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Tracking Email Status
{: #en-destination-email-custom-domain-status}

This portion of the documentation provides an overview of the status tracking system that is integrated with {{site.data.keyword.en_short}} for emails sent from a custom domain. The system generates logs containing crucial data, such as the size of the email and masked sender and recipient email addresses, to ensure privacy and security.
The system tracks three primary email statuses: Delivered, Deferred, and Bounced, providing valuable insights into the success and potential issues with email delivery.

- ## Delivered
{: #en-destination-email-custom-domain-status-delivered}

When an email is delivered successfully, a "SENT" log is created. The log contains essential data, such as the size of the delivered email and the masked sender and recipient email addresses, to maintain privacy and security.
For example, a delivered log may look like this:

```text
An email of size 1xxx bytes is sent to each of the following destinataries: [g*e*m*n*h*a*i@yahoo.co.in], from the sender: t*s*<*o*e*l*@xyz.com>
```

- ## Deferred
{: #en-destination-email-custom-domain-status-deferred}

When an email delivery is temporarily delayed, it is considered deferred. In Postfix and SMTP contexts, deferral occurs when the receiving mail server cannot accept the email for a short period due to technical reasons. The system logs deferred emails until they are delivered or a timeout period of 5 days elapses. During this time, the email is retried with an exponential time out to ensure successful delivery.
For example, a deferred log may look like this:

```text
An email of size 1xxx bytes is deferred to each of the following : [y*s@test.com], from the sender: A*h*i*<*e*t@xyz.com>connect to test.com[x.x.x.x]:25: Connection timed out
```

- ## Bounced
{: #en-destination-email-custom-domain-status-bounced}

When an email fails to deliver successfully, it is marked as a bounce. The log for a bounced email contains information about the error reason and SMTP error code. SMTP error codes provide specific details about the nature of the delivery failure. {{site.data.keyword.en_short}} does not attempt to retry bounced emails.
It is crucial for users to take corrective action in case of bounced emails, as this can negatively impact the sender's reputation.
For example, a bounced log may look like this:

```text
An email of size 1xxx bytes is bounced ,Please check the authentacity of the emails: [g*a*g*n*1*3@in.ibm.com], from the sender: t*s*<*o*e*l*@xyz.com>host xyz.pphosted.com[] said: 550 5.1.1 User Unknown (in reply to DATA command )
```

### Common SMTP Error Codes for Bounced Emails:
{: #en-destinations-custom-email-status-smtp-error-codes}

| SMTP Code | Description |
| --- | --- |
| `500` | Syntax error, command unrecognised |
| `501` | Syntax error in parameters or arguments |
| `502` | Command not implemented |
| `503` | Bad sequence of commands |
| `504` | Command parameter not implemented |
| `510` | Bad email address |
| `511` | Bad email address syntax |
| `512` | DNS domain not found |
| `513` | Bad address syntax |
| `523` | Recipient mailbox full |
| `530` | Access denied |
| `541` | Recipient address rejected |
| `550` | Requested action not taken: mailbox unavailable |
| `551` | User not local; please try |
| `552` | Requested mail action aborted: exceeded storage allocation |
| `553` | Mailbox name not allowed |
| `554` | Transaction failed |
{: caption="Common SMTP Error Codes for Bounced Emails" caption-side="top"}

To understand the reason for the bounce, refer to the table and take appropriate action, such as updating recipient email addresses or resolving issues with the recipient's mailbox.

### Maximal duration of mail in the queue
At times, Email Service Providers receiving emails from the Event Notifications service may respond with a `DEFERRED` status. In such scenarios, Event Notifications will make delivery attempts for up to one day. The statuses of these notifications will be logged by Event Notifications into IBM Cloud Log Analysis. Please review the email status logs and contact the email administrator of the recipient email address for further assistance. If the SMTP server is unreachable from the IBM Cloud network, please open a support ticket for IBM Cloud Event Notifications for assistance.
