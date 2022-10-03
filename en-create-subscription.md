---

copyright:
  years: 2015, 2022
lastupdated: "2022-09-30"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} subscription
{: #en-create-en-subscription}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Create an {{site.data.keyword.en_short}} subscription. Destinations subscribe to topics. Multiple destinations can subscribe to a single topic. An email subscription is a list of all emails IDs, and an SMS subscription is a list of all phone numbers that a notification is routed to. A webhook subscription links a webhook destination to a topic.
{: shortdesc}

Of these, {{site.data.keyword.cloud_notm}} Email service and {{site.data.keyword.cloud_notm}} SMS service are supported out-of-the box.

## Create a subscription
{: #en-create-subscription}
{: step}

Click `Subscriptions` in the {{site.data.keyword.en_short}} console.

## Add subscription details
{: #en-subscription-details}
{: step}

- Click `Create` to display subscription side panel.
- Fill in the following subscription details:
    - `Name`: name of the subscription.
    - `Description`: add an optional description.
- Select a `Topic` from the drop down list.
- Select a Destination type from the **Destination** drop down list.
   - `IBM Cloud SMS service` - When you select this option, you can add upto 100 phone numbers to the recipient list. In the **Active** tab, add the Mobile numbers. When a recipient sends an response `STOP`, the recipients number will be moved to the **Unsubscribed** tab. The recipient can restart to receive the SMS by sending a response code `START`.
   - `IBM Cloud Email service` - When you select this option, you can add upto 100 email addresses of the recipient list. The **Invited** tab displays the list of users who not yet accepted the invitation to be a subscriber. The **Active** tab displays the list of recipients email addresses and the date activated. The **Unsubscribed** tab displays the list of recipients who don't want to receive any email notification for this subscription.
- Add additional information related to the respective destination type.
   - For `IBM Cloud Email service`
      - Select **Add notification payload**, which is optional.
      - Add the sender's name in the **From name**.
      - Add **Reply to** information - Enter the reply to name, to whom the reply to be addressed, and Email of the reply to name.
      - In the **Recipients**, select the **Invited** tab, and enter the Email of the recipient and click **Add +**. You can invite a maximum of 100 recipients.
- Click **Create**.

## Enable the subscription
{: #en-subscription-finish}
{: step}

- Click `Create` in the subscription side panel.

## Unsubscribe
{: #en-unsubscribe-finish}
{: step}

You can subscribe to or unsubscribe from specific Event Notification subscription. Also, users can opt-out of receiving notifications for any subscription.
