---

copyright:
  years: 2021, 2023
lastupdated: "2023-08-29"

keywords: event-notifications, event notifications, about event notifications, destinations, sms

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} SMS service with custom sms
{: #en-destinations-custom-sms}

This capability is available only for selected users. If you would like to leverage this capability, [contact us](mailto:mbluemix@in.ibm.com?subject=[Custom%20SMS]%20:%20%20Request%20for%20Presonalised%20numbers&body=Kindly%20provide%20the%20below%20details:%0D%0A%0D%0AEvent%20Notifications%20Instance%20ID:%0D%0AIBM%20Account%20ID:%0D%0AIBM%20User%20ID:%0D%0ARegion:).
{: tip}

## Configuring a custom sms destination
{: #en-destinations-custom-sms}

You can configure a custom sms destination in the Destinations tab.

## Custom sms personalised numbers
{: #en-destinations-custom-sms-numbers}

After creating the destination, you must explicitly request these numbers to use this destination for sending events. Open a support ticket, mentioning the destination ID, CRN of the event notification instance, along with the list of countries for which you need to send notifications using this destination.

## Using a Custom sms destination
{: #en-destinations-custom-sms-use}

To use the SMS service destination, add it to a subscription along with the phone numbers of the recipients. Within a single subscription, you can add up to 3 phone numbers for lite plan and 100 phone numbers for standard plan. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your SMS recipients.

To comply with the regulatory standards, you may need to get a consent (opt-in) from the SMS recipients to receive SMSs from each of the {{site.data.keyword.en_short}} subscriptions.

### Create a subscription with Custom SMS as destination
{: #en-create-subscription-custom-sms-destination}


1. From the {{site.data.keyword.en_short}} dashboard, click **Subscriptions** in the navigation menu.

1. Click `Create +` to display **Create a Subscription** side panel.

1. Complete the following subscription details:
   - `Name`: name of the subscription.
   - `Description`: add an optional description for this subscription

1. Select a `Topic` from the list.

1. Select custom SMS destination created as **Destination** from the list.

1. The **Recipients** section displays three tabs:
   - *Invited* - displays the list of phone numbers added to the subscription. Enter the phone numbers that need to receive SMS notifications and need to be part of the subscription.
   - *Active* - displays the list of phone numbers added to the subscription and confirmed by the user to receive SMS notifications.
   - *Unsubscribed* - displays the list of phone numbers added to the subscription and refused by the user not to receive SMS notifications.

   Add the user's phone numbers with a *+ and country code*, who needs to receive SMS messages as part of this subscription, with comma (,) as separator between the numbers.

1. Click **Create**. The recipient automatically receives initial message that they have been invited to subscribe to the topic. This is the `opt-in` message.

The Opt-in message contains:
- invitee name or account
- name of the subscription
- name of the topic
- a link that will take you to a web page. The web page contains information that the recipient is subscribed to receive SMS notifications to a topic and a **Confirm** button. When the recipient click the **Confirm** button, then the recipient's number is moved from *Invited* tab to *Active* tab. A confirmation message also displaying that the recipient has accepted to receive SMS notifications. The confirmation message also contains a link to **Unsubscribe**, which on clicking moves to recipient's number to the *Unsubscribed* tab.
- an expiration time for the opt-in message.

{{site.data.keyword.en_short}} are routed only to opted-in recipients. To stop receiving the notifications, recipient can click the **Unsubscribe** link in the message. Once unsubscribed, the recipients will not receive any notifications on the topic they have unsubscribed. To restart the subscription, the recipient need to contact {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to subscription.

In some cases, the carrier service allows keywords like `START` and `STOP` for receiving notifications and to stop notifications.

When a recipient doesn't wants to receive any SMS notification, they can opt out by sending a response `STOP`, which immediately disables sending notifications to the recipient. However, the phone number is moved to **Unsubscribed** tab only on the next attempt to send an SMS to the same number.

To add a recipient number back to active list, take the following steps:

1. Recipient needs to send `START` message back to the number from which SMS was received.
1. After sending `START` message, the recipient can contact their {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to subscription.

By adding phone numbers, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added phone numbers pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

## SMS segment
{: #en-destinations-sms-segment}

SMS segments are character batches (of length 160 characters) of an SMS message, used by carriers to measure the message size.

If a message contains less than 160 characters, then it is considered as one SMS segment. If a message contains over 160 characters, for example, of 200 characters, then it is considered as 2 segments, first segment has 160 character and the second segment has 40 characters.

## SMS charges
{: #en-destinations-sms-charge}


