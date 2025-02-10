---

copyright:
  years: 2021, 2023
lastupdated: "2023-03-03"

keywords: event-notifications, event notifications, about event notifications, destinations, push

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Push notifications
{: #en-destinations-push}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

{{site.data.keyword.en_short}} provides a push notification service for sending transactional and informational event notifications to mobile devices.
{: shortdesc}

## Adding a push service destination
{: #en-destinations-push-add}

Add an {{site.data.keyword.cloud_notm}} push notification destination to your instance of {{site.data.keyword.en_short}} by clicking `Add` in the `Destinations` view of the {{site.data.keyword.en_short}} dashboard. After a new push destination is created, you see an entry `{{site.data.keyword.cloud_notm}} push service` in the `Destination` list. You must configure your push destination by adding credentials for Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).

Each application and platform requires a separate push destination.

You can use **Pre-production destination**, as low-cost push destination, for your development and test environments. You can change the **Pre-production destination** to **Production destination** post completion of your development and testing. This feature is only available for `Standard` pricing plan.
{: note}

## Using a push service destination
{: #en-destinations-push-use}

To use a push service destination, add it to a subscription. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your registered devices.

The push service works along with an app on your users' mobile devices. You must instrument the app with the {{site.data.keyword.en_short}} push SDK. The app must ensure that users consent to notifications, and then the SDK helps to register their mobile devices. For more information, see [Create an {{site.data.keyword.en_short}} destination](/docs/event-notifications?topic=event-notifications-en-create-en-destination).

## Push troubleshooting and telemetry
{: #en-destinations-push-ts-and-telemetry}

Troubleshooting and telemetry information for push notifications is available in the {{site.data.keyword.la_full}} service. You can see the dispatch status as well as *delivered* and *opened* information for individual devices. For more information, see [Logging for {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-logging).

## Push charges
{: #en-destinations-push-charge}

The {{site.data.keyword.cloud_notm}} push service has two components to pricing: a destination instance fee and a consumption price.

The destination instance fee is a fixed amount charged monthly. Every push destination added to your {{site.data.keyword.en_short}} instance incurs the fee.

The consumption price is based on outbound digital messages. Every push notification that is sent by the {{site.data.keyword.cloud_notm}} push service counts as one outbound digital message and is charged. For example, you send messages to two platforms (iOS and Android) and you create a subscription that has 100 phone numbers. The subscription topic received 1000 events during the month:

Destination instances: 2

Consumption:

Total Outbound Digital messages = (number of phone numbers) x (topic events)

In the example, the total outbound digital messages are:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} push service to the push provider regardless of whether the message was successfully delivered to the local device. So vet your device list carefully to prevent unnecessary charges.

You can monitor your push usage by setting up a monitoring dashboard through the `Actions` menu in the {{site.data.keyword.en_short}} dashboard. For more information, see [Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.monitoringfull_notm}}](/docs/event-notifications?topic=event-notifications-monitoring).

### Push charges for pre-production destination
{: #en-destinations-push-charge-preprod-destination}

The {{site.data.keyword.cloud_notm}} push service has two components to pricing: a destination instance fee and a consumption price.

A pre-production destination instance fee is charged monthly. Every pre-production destination added to your {{site.data.keyword.en_short}} instance incurs the fee.

Consumption: Only 500 devices or 5000 outbound digital messages is permitted per pre-production destination. If either the number of devices or the number of outbound digital messages exceeds the permitted limit, the permitted number of devices is moved by additional 500 devices or by additional 5000 messages and charged.

For example, if you tried to send 5001th message, the message cap automatically is raised to 10000 (another 5000 messages are added) for the month and the device cap is raised to 1000 (another 500 devices are added) per month. Notice that both limits are always raised even if only one cap has been exceeded.

### Push charges for changing from pre-production destination to production destination
{: #en-destinations-push-charge-preprod-to-prod}

You can change a pre-production destination to a production destination at any particular time and the charges are calculated accordingly.

The push service has two components to pricing: a destination instance fee and a consumption price.

A pre-production destination instance fee is charged monthly. Every pre-production destination added to your {{site.data.keyword.en_short}} instance incurs the fee.

A production destination instance fee is also charged monthly and allows unlimited devices and outbound messages.

If you change a pre-production destination to a production destination, the charges for the transition month would be the pre-producdtion fee + pro-rated charge for the production instance.

For example, assume the pre-production instance fee is $15 per month and the production instance fee is $50 per month.

These prices are assumed for this example only. Current pricing may be different from the amounts shown in the example. See the {{site.data.keyword.en_short}} catalog page for current pricing.
{: note}

- As of 31 July, you create a pre-production destination and does not register any devices or send messages, the charges for July will be $15.
- As of 1 August, you register 500 devices and 5001 messages sent. The charges for August will be $30 (This is due to the message threshold exceeds the permitted limit.)
- As of 5 August, you change from pre-production destination to production destination. Then, the charges for August will be $30 plus pro-rata charges of consumption price, which will be equal to

   Amount charged = $30 + $ (50/31) x (remaining number of days in the month) = $30 + [(50/31) x 26] = $71.86.

- If you create a pre-production destination on 1 August and do not register any devices and do not sent any message, but on 5th August change from pre-production destination to a production destination, then the charges will be:

   Amount charged = $15 + $ (50/31) x (remaining number of days in the month) = $15 + [(50/31) x 26] = $56.86.
