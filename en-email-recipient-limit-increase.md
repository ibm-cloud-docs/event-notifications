---

copyright:
  years: 2026
lastupdated: "2026-08-04"

keywords: event-notifications, event notifications, about event notifications, email, recipient limit, increase, custom domain, smtp

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Requesting a recipient limit increase for email destinations
{: #en-email-recipient-limit-increase}

Each send request supports up to 50 email recipients. This limit applies to both custom domain email destinations and the SMTP interface.

If you need to reach more than 50 recipients, you can send in batches — send the first 50 recipients in one request, then send subsequent requests with the remaining recipients.

If batching does not meet your use case requirements and you need a higher per-request limit, you can request an increase by opening a support case with {{site.data.keyword.en_short}}. To help process your request, answer the following questions:

```text
1. What is your use case for requesting an increase to the recipient limit?

2. Why is batching not a suitable solution for your use case?

3. What recipient limit are you requesting?

4. Who are the recipients of these emails?

5. How frequently will you send emails with the requested recipient limit?

6. Approximately how many emails do you expect to send per day?
```
{: codeblock}

To submit your request:

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
1. From the Contact support section, click **Create a case**.
1. Select under `Category`, `Topic` as Event Notifications and `Subtopic` as Others.
1. Under `Subject` add **Requesting a recipient limit increase for email destination**.
1. In the **Description** section, include your responses to the questions listed previously.
1. Add **Attachments** if you want to provide more evidence supporting your answers.
1. Add required email IDs in the **Watchlist** section. For more information about creating a support case, see [Creating support cases](/docs/support?topic=support-open-case&interface=ui){: external}.
