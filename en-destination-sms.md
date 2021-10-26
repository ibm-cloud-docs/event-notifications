---

copyright:
  years: 2020, 2021
lastupdated: "2021-10-26"

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



# {{site.data.keyword.Bluemix_notm}} SMS service
{: #en-destinations-sms}

{{site.data.keyword.Bluemix_notm}} SMS service is a destination provided out-of-the-box. When a new instance is created, you will see an entry `{{site.data.keyword.Bluemix_notm}} SMS service` in the destination tab. The SMS destination is pre-configured, and is ready to use.

## Adding an SMS destination
{: #en-sms-add}

 Provide the phone numbers that are interested in receiving notifications by creating subscriptions. A subscription allows you to associate a topic to the SMS destination, and enter a list of phone numbers. The recipients will be notified about events that have been routed to the topic belonging to this subscription.

By adding phone numbers, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added phone numbers pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{:note: .note}

## SMS charges
{: #en-sms-charge}

An incoming notification can be split into multiple segments based on the lenth of the message. {{site.data.keyword.en_short}} service considers `SMS Units` for charges applied.

The number of units consumed by a message will vary based on the destination country. {{site.data.keyword.en_short}} service charges vary based on the destination country.

| Country   | SMS Units|
|-------------|-------------|
| US| 1 unit|
{: caption="Table 1. Destination country and unit per segment" caption-side="top"}

For example if an incoming notification is split into three SMS segments, and the message is sent to five subscribed phone numbers, then the total consumed SMS units  for the incoming message will be:

**Total SMS units = (Number of Segments) x (Number of phone numbers) x (SMS Unit for the country)**

