---

copyright:
  years: 2020, 2022
lastupdated: "2022-10-28"

keywords: event-notifications, event notifications, about event notifications, destinations, sms

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} SMS service
{: #en-destinations-sms}

{{site.data.keyword.en_short}} provides a built-in SMS service for sending transactional and informational event notification text messages to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account.
{: shortdesc}

The text messages originate from IBM-owned phone numbers or alphanumeric sender IDs. Except for test messages, the content cannot be modified within {{site.data.keyword.en_short}}.

## Adding an SMS destination
{: #en-destinations-sms-add}

{{site.data.keyword.cloud_notm}} SMS service is a destination that provided by default and ready for immediate use. When a new instance is created, you see an entry `{{site.data.keyword.cloud_notm}} SMS service` in the destination tab. The SMS destination is pre-configured and is ready to use.

## Using an {{site.data.keyword.cloud_notm}} SMS service destination
{: #en-destinations-sms-use}

`{{site.data.keyword.cloud_notm}} SMS service` as the destination type is only supported for US and Canada numbers.
{: important}

To use the SMS service destination, add it to a subscription along with the phone numbers of the recipients. Within a single subscription, you can add up to 3 phone numbers for lite plan and 100 phone numbers for standard plan. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your SMS recipients.

When you select `{{site.data.keyword.cloud_notm}} SMS service` as the destination type, you can add up to 3 phone numbers for lite plan and 100 phone numbers for standard plan, to the recipient list. To comply with the regulatory standards, you may need to get a consent (opt-in) from the SMS recipients to receive SMSs from each of the {{site.data.keyword.en_short}} subscriptions.

### Create a subscription with IBM SMS service as destination
{: #en-create-subscription-sms-destination}

1. From the {{site.data.keyword.en_short}} dashboard, click **Subscriptions** in the navigation menu.

1. Click `Create +` to display **Create a Subscription** side panel.

1. Complete the following subscription details:
   - `Name`: name of the subscription.
   - `Description`: add an optional description for this subscription

1. Select a `Topic` from the list.

1. Select `{{site.data.keyword.cloud_notm}} SMS service` as **Destination** from the list.

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

## SMS charges
{: #en-destinations-sms-charge}

Because SMS delivery rates vary widely with location, SMS text messages are charged in terms of `SMS Units`. An SMS unit is a fixed unit of cost. Therefore, the number of units that are consumed by a message varies based on the destination country, and {{site.data.keyword.en_short}} service charges vary. Table 1 shows the current SMS Units by country.

| Supported Country Code        | SMS Units |
|-------------------------------|-----------|
| +1 (United States and Canada) | One unit    |
{: caption="Table 1. Destination country and unit per segment" caption-side="top"}

Longer notifications (notifications greater than 160 characters) might be split into multiple segments. Each segment is considered a message, as is each recipient phone number. For example, if an incoming notification is split into three SMS segments, and the message is sent to five subscribed phone numbers, then the total consumed SMS units for the incoming message is as follows:

Total SMS units = (Number of Segments) x (Number of phone numbers) x (SMS Unit for the country)

In the example, the total SMS units for messages that are sent to destination numbers in the United States is:

3 x 5 x 1 = 15 SMS units

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} SMS service to the local SMS provider regardless of whether the message was successfully delivered to the local device. So vet your phone number list carefully to prevent unnecessary charges.

You can monitor your SMS usage by setting up a monitoring dashboard through the `Actions` menu in the {{site.data.keyword.en_short}} dashboard. See [Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.monitoringfull_notm}}](/docs/event-notifications?topic=event-notifications-en-monitoring) for details.
