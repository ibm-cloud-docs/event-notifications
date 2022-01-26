---

copyright:
  years: 2020, 2021, 2022
lastupdated: "2022-01-25"

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


{{site.data.keyword.en_short}} provides a built-in SMS service for sending transactional and informational event notification text messages to recipients who need to be aware of events happening within your IBM Cloud account.
{: shortdesc}

The text messages originate from IBM-owned phone numbers or alphanumeric sender IDs.  Except for test messages, the content cannot be modified within Event Notifications.

## Adding an SMS destination
{: #en-destinations-sms-add}

{{site.data.keyword.Bluemix_notm}} SMS service is a destination provided out-of-the-box. When a new instance is created, you will see an entry `{{site.data.keyword.Bluemix_notm}} SMS service` in the destination tab. The SMS destination is pre-configured and is ready to use.

## Using an {{site.data.keyword.Bluemix_notm}} SMS service destination
{: #en-destinations-sms-use}

 To use the SMS service destination, add it to a subscription along with the phone numbers of interest.  Within a single subscription, you can add up to 100 phone numbers.   The subscription will also need a topic to filter events of interest from your sources.  When an event lands in the topic, {{site.data.keyword.en_short}} will immediately route the event notification to your SMS recipients. 

 If you add an individual to the recipient list who does not want to receive SMS notifications, the recipient can opt out by clicking a link in the SMS or, in some areas, replying to message with keyword `STOP`. You can track recipients who have opted in the {{site.data.keyword.en_short}} dashboard.

By adding phone numbers, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added phone numbers pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{:note: .note}

## SMS charges
{: #en-destinations-sms-charge}

Because SMS delivery rates vary widely with location, SMS text messages are charged in terms of `SMS Units`.  An SMS unit is a fixed unit of cost.  The number of units consumed by a message will vary based on the destination country, and therefore {{site.data.keyword.en_short}} service charges vary based on the destination country.  Table 1 shows the current SMS Units by country.

| Country   | SMS Units|
|-------------|-------------|
| US| 1 unit|
{: caption="Table 1. Destination country and unit per segment" caption-side="top"}


Longer notifications (those greater than 160 characters) may be split into multiple segments. Each segment is considered a message, as is each recipient phone number.  For example, if an incoming notification is split into three SMS segments, and the message is sent to five subscribed phone numbers, then the total consumed SMS units for the incoming message will be:

**Total SMS units = (Number of Segments) x (Number of phone numbers) x (SMS Unit for the country)**

In our example, the total SMS units for messages sent to destination numbers in the United States is:

 3 x 5 x 1 = 15 SMS units

 You are charged for messages that are successfully sent by the {{site.data.keyword.Bluemix_notm}} SMS service to the local SMS provider regardless of whether or not the not the message was successfully delivered to the local device, so vet your phone number list carefully to prevent unnecessary charges.

You can monitor your SMS usage by setting up a monitoring dashboard through the Actions menu in the upper right corner of {{site.data.keyword.en_short}} dashboard.  See the "How To" documentation section for details.

