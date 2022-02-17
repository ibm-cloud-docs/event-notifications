---

copyright:
  years: 2015, 2022
lastupdated: "2022-02-16"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} subscription
{: #en-create-en-subscription}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Create an {{site.data.keyword.en_short}} subscription. Destinations subscribe to topics. Multiple destinations can subscribe to a single topic. An email subscription is a list of all emails IDs, and an SMS subscription is a list of all phone numbers that a notification is routed to. A webhook subscription links a webhook destination to a topic.
{: shortdesc}

Of these, SMTP_IBM and SMS_IBM are supported out-of-the box.


## Create a subscription
{: #en-create-subscription}
{: step}

Click `Subscriptions` in the {{site.data.keyword.en_short}} console.

## Add subscription details
{: #en-subscription-details }
{: step}

- Click `Create` to display subscription wizard.
- Fill in the following subscription details:
    - `Subscription name`: name of the subscription.
    - `Subscription description`: add an optional description.
- Under the `Subscribe to a topic` section, select a topic from the drop down list and select a destination from from the destination drop down list.
- Destination type; select type under `Destination`.

## Enable the subscription
{: #en-subscription-finish}
{: step}

- Click `Create` in the subscription wizard.

## Unsubscribe 
{: #en-unsubscribe-finish}
{: step}

You can subscribe to or unsubscribe from specific Event Notification email notifications. Also, users can opt out of receiving notifications for any subscription.

To unsubscribe, do the following:
- Under email subscription, click the `Unsubscribed` dialog to modify subscription settings and unsubscribe from mailing lists. 
- Select or deselect the `Unsubscribed` dialog, this automatically reflects in the subscription wizard. 
	 
-The role of an Admin:
- Only an admin can move or modify an unsubscribed email id to `Active`.
- Only an admin can clear unsubscribed email lists. 
- An admin cannot manually move or add users to the unsubscribed list.

