---

copyright:

years: 2020, 2021, 2022
lastupdated: "2022-01-25"


keywords: event-notifications, event notifications, about event notifications, destinations, push

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



# {{site.data.keyword.Bluemix_notm}} push notification service
{: #en-destinations-push}

{{site.data.keyword.en_short}} provides a push notification service for sending event notications to mobile devices. 

{: shortdesc}

## Adding an push service destination
{: #en-destinations-push-add}


Add an {{site.data.keyword.Bluemix_notm}} push notification destination to your instance of Event Notifications by clicking the `Add` button in the Destinations view of the {{site.data.keyword.en_short}} dashboard. After a new push destination is created, you will see an entry `{{site.data.keyword.Bluemix_notm}} push service` in the Destination list. You will need to configure your push destination by adding credentials for Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).  See the "Tutorials" documentation section for more details.

Each application and platform will require a separate push destination.

## Using an {{site.data.keyword.Bluemix_notm}} push service destination
{: #en-destinations-push-use}

 To use the push service destination, simply add it to a subscription.  The subscription will also need a topic to filter events of interest from your sources.  When an event lands in the topic, {{site.data.keyword.en_short}} will immediately route the event notification to your registered devices. 

The push service works in conjunction with an app on your end users' mobile devices.  You must instrument the app with the {{site.data.keyword.en_short}} push SDK.  The app should ensure users to consent to notifications, and then the SDK will help register their mobile device.  See the "How To" documentation section for details.

## Push charges
{: #en-destinations-push-charge}

The {{site.data.keyword.Bluemix_notm}} push service has two components to pricing:  a destination instance fee and a consumption price.

The destination instance fee is a fixed amount charged monthly.  Every push destination added to your {{site.data.keyword.en_short}} instance will incur the fee.

The consumption price is based on outbound digital messages.  Every push notification sent by the {{site.data.keyword.Bluemix_notm}} push service counts as one outbound digital message and is charged accordingly. For example, let's say you send messages to two platforms (iOS and Android) and have created a subscription has that has 100 phone numbers.  The subscription topic received 1000 events during the month:

Destination instances:  2 

Consumption:

Total Outbound Digital Messages = (number of phone numbers) x (topic events)

In or example, the total outbound digital messages is:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.Bluemix_notm}} push service to the push provider regardless of whether or not the not the message was successfully delivered to the local device, so vet your device list carefully to prevent unnecessary charges.

You can monitor your push usage by setting up a monitoring dashboard through the Actions menu in the upper right corner of {{site.data.keyword.en_short}} dashboard.  See the "How To" documentation section for details.

