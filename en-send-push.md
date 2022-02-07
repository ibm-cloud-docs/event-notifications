---

copyright:
  years: 2015, 2022
lastupdated: "2022-02-07"

keywords: event notifications, event-notifications, push, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 60m

---

{{site.data.keyword.attribute-definition-list}}

# Send a push notification using {{site.data.keyword.en_short}}
{: #en-send-push}
{: toc-content-type="tutorial"}
{: toc-completion-time="60m"}

This tutorial describes how to send push notifications using {{site.data.keyword.en_short}}.
{: shortdesc}

If you do not already have an instance of {{site.data.keyword.en_short}}, create one. See [Create an Event Notifications service instance](/docs/event-notifications?topic=event-notifications-en-create-en-instance) for more details.

## Overview
{: #en-send-push-overview}

To send push notifications, you must use the Event Notifications API or an {{site.data.keyword.en_short}} admin SDK. 

A summary of the tasks you complete is as follows:

- Configure {{site.data.keyword.en_short}} to route push notifications.

	- Create an API source to connect to your sending app. See [Create an {{site.data.keyword.en_short}} API source](/docs/event-notifications?topic=event-notifications-en-create-en-source) for more details.
	- Create a topic to accept incoming notifications. See [Create an {{site.data.keyword.en_short}} topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic) for more details.
	- Create a push destination to connect to your receiving app. See [Create an {{site.data.keyword.en_short}} push destination for Android (FCM)](/docs/event-notifications?topic=event-notifications-en-create-en-destination-push-fcm) for more details.
	- Create a subscription to tie everything together. See[Create an {{site.data.keyword.en_short}} subscription](/docs/event-notifications?topic=event-notifications-en-create-en-subscription) for more details.

- Instrument the receiving application.
- Test the receiving application with cURL or Postman.
- Instrument the sending application.
- Test the sending and receiving applications end-to-end.

When you have configured {{site.data.keyword.en_short}} to route push notifications, then continue to the following instrumentation steps:

## Instrument the receiving application
{: #en-send-push-instrument-receiving-app}
{: step}

To instrument your receiving mobile or web app, use one of the following SDKs:

- [Event Notifications Client SDK for Android](https://github.com/IBM/event-notifications-destination-android-sdk)

Each SDK repo contains instrumentation instructions for the selected platform.

To initialize the SDK you need credentials with IAM role of Device Manager. Create these credentials in the Service Credentials section of your {{site.data.keyword.en_short}} dashboard. You need `guid` and `apikey` from you credential set. `region` is also shown in the credential set if you need it.

In addition to the credentials you create, you need the destination ID of the push destination that you created. To find that ID, go to the `Destinations` section of the {{site.data.keyword.en_short}} dashboard, locate your push destination in the list, and click on it to reveal the destination ID.

## Test with cURL or Postman
{: #en-send-push-instrument-receiving-app}
{: step}

When you have configure your {{site.data.keyword.en_short}} instance and instrumenting your receiving application, but before instrumenting your sending application, verify that {{site.data.keyword.en_short}} is pushing to your app. Use an API testing app like cURL or Postman to verify that notifications are pushing to your app. 

You need the URL for the API source that you created in the first step. To find that URL, visit the `Sources` section of the {{site.data.keyword.en_short}} dashboard, and click `Edit` in the context menu of your API source. 

You also need an access token so that your API testing tool can access your {{site.data.keyword.en_short}} service. Follow the instructions in [Retrieving an access token](/docs/hs-crypto?topic=hs-crypto-retrieve-access-token) to generate a token.

## Instrument the sending application
{: #en-send-push-instrument-sending-app}
{: step}

To instrument your sending application, use one of the following SDKs:

- [Event Notifications Admin SDK for Node.js](https://github.com/IBM/event-notifications-node-admin-sdk)
- [Event Notifications Admin SDK for Go](https://github.com/IBM/event-notifications-go-admin-sdk)

Each SDK repo contains instrumentation instructions for the selected platform. The subtasks to instrument the sending application are as follows:

- Initialize your {{site.data.keyword.en_short}} SDK.
- Configure your message.
- Add code to send notifications.

### Initialize your {{site.data.keyword.en_short}} SDK
{: #en-init-sdk}

To initialize the SDK, you need credentials with IAM role of Manager. Create these credentials in the `Service Credentials` section of your {{site.data.keyword.en_short}} dashboard. You need `apikey` and `region` from you credential set.


### Configure your message
{: #en-config-msg}

Configure your message by adding message-specific parameter values. There are many parameters which are documented in the repo documentation.

### Add code to send notifications
{: #en-add-code-notif}

There are a few more parameters and lines of code needed to send the message. The parameter values needed include the API source URL and the API source ID. To find the source ID, visit the `Sources` section of the {{site.data.keyword.en_short}} dashboard, locate your API source in the `Sources` list, and click on it to reveal the source ID. To find API source URL, click `Edit` in the context menu for your API source.

## Test end-to-end
{: #en-send-push-test}
{: step}
