---

copyright:
  years: 2020, 2026
lastupdated: "2026-09-21"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Managing {{site.data.keyword.en_short}} subscriptions
{: #en-create-en-subscription}

Destinations subscribe to topics. Multiple destinations can subscribe to a single topic. An email subscription is a list of all emails IDs, and an SMS subscription is a list of all phone numbers that a notification is routed to. A webhook subscription links a webhook destination to a topic.
{: shortdesc}

To create a subscription, work through a topic in the route notifications flow. For more information, see [Creating subscriptions](/docs/event-notifications?topic=event-notifications-en-route-create-subscriptions).

Of these, {{site.data.keyword.cloud_notm}} Email service and {{site.data.keyword.cloud_notm}} SMS service are supported out-of-the box.

## Destination type details
{: #en-select-destination}

The destination type determines how notifications are delivered. The following sections describe the additional details required for each destination type.

### {{site.data.keyword.cloud_notm}} SMS service
{: #en-SMS-destination}


- When you add phone numbers to your subscription, you can add a maximum of 3 phone numbers if you're working with the Lite plan and 100 if you're working in the Standard plan.
- When you click **Create subscription** after adding phone numbers, the numbers are added to the **Invited** tab. The **Active** tab displays the phone numbers of recipients who confirmed receiving SMS notifications for the selected topic.
- When a recipient clicks the **Unsubscribe** link, the recipient's number is moved to the **Unsubscribed** tab. To restart the subscription, the recipient must contact the {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to the subscription.
- In some cases, the carrier service allows keywords like `START` and `STOP`. When a recipient sends a `STOP` response, notifications are disabled immediately. However, the phone number is moved to the **Unsubscribed** tab only on the next attempt to send an SMS to that number. The recipient can restart notifications by sending a `START` response.

### {{site.data.keyword.cloud_notm}} Email service
{: #en-Email-destination}

- You can add a maximum of 10,000 emails when you add email addresses to your subscription recipient list.
- The **Invited** tab displays a list of users who have not yet accepted the invitation. The **Active** tab displays a list of recipient email addresses and the date that each address was activated. The **Unsubscribed** tab displays a list of recipients who have opted out of receiving email notifications for this subscription.
- Add any additional information that is required for the destination type.

If you are providing **Assigned to** and **Assignment group** values, make sure that they have proper settings and are linked otherwise ServiceNow will reject requests with 403. Also make sure that there are no Business Rule blocking assignment to these groups and users.
{: note}
