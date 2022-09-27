---

copyright:
  years: 2020, 2022
lastupdated: "2022-09-26"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} SMS service
{: #en-destinations-sms}

{{site.data.keyword.en_short}} provides a built-in SMS service for sending transactional and informational event notification text messages to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account.
{: shortdesc}

The text messages originate from IBM-owned phone numbers or alphanumeric sender IDs. Except for test messages, the content cannot be modified within {{site.data.keyword.en_short}}.

## Adding an SMS destination
{: #en-destinations-sms-add}

{{site.data.keyword.cloud_notm}} SMS service is a destination that provided out-of-the-box. When a new instance is created, you see an entry `{{site.data.keyword.cloud_notm}} SMS service` in the destination tab. The SMS destination is pre-configured and is ready to use.

## Using an {{site.data.keyword.cloud_notm}} SMS service destination
{: #en-destinations-sms-use}

`IBM Cloud SMS service` as the destination type is only supported for US and Canada numbers.
{: important}

To use the SMS service destination, add it to a subscription along with the phone numbers of the recipients. Within a single subscription, you can add up to 100 phone numbers. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your SMS recipients.

When you select `IBM Cloud SMS service` as the destination type, you can add upto 100 phone numbers to the recipient list. In the **Active** tab, add the Mobile numbers. When a recipient doesn's wants to receive any SMS notification, they can opt-out by sending an response `STOP`, the recipients number will be moved to the **Unsubscribed** tab.

To add a recipient number back to active list, take the following steps:

1. Recipient needs to send `START` message back to the number from which SMS was received.
1. After sending `START` message, the recipient can contact their {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}}  service administrator to add the number back to subscription.

By adding phone numbers, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added phone numbers pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

## SMS charges
{: #en-destinations-sms-charge}

Because SMS delivery rates vary widely with location, SMS text messages are charged in terms of `SMS Units`. An SMS unit is a fixed unit of cost. The number of units consumed by a message varies based on the destination country, and therefore {{site.data.keyword.en_short}} service charges vary. Table 1 shows the current SMS Units by country.

| Supported Country Code        | SMS Units |
|-------------------------------|-----------|
| +1 (United States and Canada) | 1 unit    |
{: caption="Table 1. Destination country and unit per segment" caption-side="top"}

Longer notifications (those greater than 160 characters) might be split into multiple segments. Each segment is considered a message, as is each recipient phone number. For example, if an incoming notification is split into three SMS segments, and the message is sent to five subscribed phone numbers, then the total consumed SMS units for the incoming message is as follows:

Total SMS units = (Number of Segments) x (Number of phone numbers) x (SMS Unit for the country)

In the example, the total SMS units for messages sent to destination numbers in the United States is:

3 x 5 x 1 = 15 SMS units

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} SMS service to the local SMS provider regardless of whether the message was successfully delivered to the local device. So vet your phone number list carefully to prevent unnecessary charges.

You can monitor your SMS usage by setting up a monitoring dashboard through the `Actions` menu in the {{site.data.keyword.en_short}} dashboard. See [Monitor Event Notifications service metrics with IBM Cloud Monitoring](/docs/event-notifications?topic=event-notifications-en-monitoring) for details.
