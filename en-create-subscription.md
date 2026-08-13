---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} subscription
{: #en-create-en-subscription}

Destinations subscribe to topics. Multiple destinations can subscribe to a single topic. An email subscription is a list of all emails IDs, and an SMS subscription is a list of all phone numbers that a notification is routed to. A webhook subscription links a webhook destination to a topic.
{: shortdesc}

Of these, {{site.data.keyword.cloud_notm}} Email service and {{site.data.keyword.cloud_notm}} SMS service are supported out-of-the box.

## Creating a subscription
{: #en-create-subscription}

1. Click **Topics** in the {{site.data.keyword.en_short}} instance.
Create a new topic or select an existing topic to configure the subscription for.

1. If you are creating a new topic, configure **Topic**, **Filters**, and **Subscriptions** in the flow.
For an existing topic, click **Edit** in the **Options** menu and click the **Subscriptions** tab.

1. Enter the following subscription details in the **Create subscription** dialog:

   - **Subscription name**: Enter a name for the subscription.
   - **Subscription description**: Optionally, enter a description for the subscription.
   - **Topic**: Select a topic.
   - **Destination type**: Select a destination type. For more information, see [Selecting a destination type](/docs/event-notifications?topic=event-notifications-en-create-en-subscription#en-select-destination).

1. Click **Create subscription**.

### Enabling the subscription
{: #en-subscription-finish}

Click **Create subscription** in the subscription dialog to enable the subscription.

You can subscribe to or unsubscribe from a specific {{site.data.keyword.en_short}} subscription. Users can also opt out of receiving notifications for any subscription.
{: note}

## Selecting a destination type
{: #en-select-destination}

The destination type determines how notifications are delivered. The following sections describe the additional details required for each destination type.

### {{site.data.keyword.cloud_notm}} SMS service
{: #en-SMS-destination}

- You can add up to 3 phone numbers for the Lite plan and 100 phone numbers for the Standard plan to the recipient list.
- When you click **Create subscription** after adding phone numbers, the numbers are added to the **Invited** tab. The **Active** tab displays the phone numbers of recipients who confirmed receiving SMS notifications for the selected topic.
- When a recipient clicks the **Unsubscribe** link, the recipient's number is moved to the **Unsubscribed** tab. To restart the subscription, the recipient must contact the {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to the subscription.
- In some cases, the carrier service allows keywords like `START` and `STOP`. When a recipient sends a `STOP` response, notifications are disabled immediately. However, the phone number is moved to the **Unsubscribed** tab only on the next attempt to send an SMS to that number. The recipient can restart notifications by sending a `START` response.

### {{site.data.keyword.cloud_notm}} Email service
{: #en-Email-destination}
   
- You can add up to 10,000 email addresses to the recipient list. The **Invited** tab displays a list of users who have not yet accepted the invitation. The **Active** tab displays a list of recipient email addresses and the date that each address was activated. The **Unsubscribed** tab displays a list of recipients who have opted out of receiving email notifications for this subscription.
- Add any additional information that is required for the destination type.

If you are providing **Assigned to** and **Assignment group** values, make sure that they have proper settings and are linked otherwise ServiceNow will reject requests with 403. Also make sure that there are no Business Rule blocking assignment to these groups and users.
{: note}
         
