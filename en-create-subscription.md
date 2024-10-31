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

1. Click **Subscriptions** in the {{site.data.keyword.en_short}} console.

1. Enter subscription details: 

   - Click **Create** to display the subscription side panel.
   - Enter the following subscription details.
   - Select a topic. 
   - Select a destination type. For more information on how to select a destination, see [Selecting a destination type](/docs/event-notifications?topic=event-notifications-en-create-en-subscription#en-select-destination). 

1. Click **Create**.

### Enabling the subscription
{: #en-subscription-finish}

Click **Create** in the subscription side panel to enable the subscription.

You can subscribe to or unsubscribe from specific {{site.data.keyword.en_short}} subscription. Also, users can opt out of receiving notifications for any subscription.
{: note}

## Selecting a destination type
{: #en-select-destination}

### {{site.data.keyword.cloud_notm}} SMS service
{: #en-SMS-destination}

- You can add up to 3 phone numbers for the lite plan, and 100 phone numbers for stsandard plan to the recipient list. 
- When you click **Create** subscription after adding the phone numbers, the number are added to the **Invited** tab. The **Active** tab, displays the phone number of recipients who confirmed receiving SMS notifications for the topic selected in the invite.
- When a recipient clicks the **Unsubscribe** link, the recipients number is moved to the **Unsubscribed** tab. To restart the subscription, the recipient should contact {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to subscription.
- In some cases, the carrier service allows keywords like `START` and `STOP`. When a recipient sends a response `STOP`, the services for recipient is disabled immediately. However, the phone number is moved to **Unsubscribed** tab only on the next attempt to send an SMS to the same number. The recipient can restart to receive the SMS by sending a response code `START`. 

### {{site.data.keyword.cloud_notm}} Email service
{: #en-Email-destination}
   
- You can add up to 10,000 email addresses of the recipient list. The **Invited** tab displays a list of users who have not yet accepted the invitation to be a subscriber. The **Active** tab displays a list of recipients email addresses and the date they were activated. The **Unsubscribed** tab displays a list of recipients who have opted out of receiving any email notifications for this subscription.
- Add additional information that is related to the respective destination type as required.

If you are providing **Assigned to** and **Assignment group** values, make sure they have proper settings and linked otherwise ServiceNow will reject requests with 403. Also make sure there are no Business Rule blocking assignment to these groups and users.
{: note}
         
