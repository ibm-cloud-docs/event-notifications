---

copyright:
  years: 2015, 2020, 2022
lastupdated: "2022-01-31"

keywords: event notifications, event-notifications, push, tutorials

subcollection: event-notifications

content-type: tutorial
services:
account-plan: lite
completion-time: 60m

---

{{site.data.keyword.attribute-definition-list}}

# Send a push notification using {{site.data.keyword.en_short}}
{: #en-send-push}

This tutorial describes how to send push notifications using {{site.data.keyword.en_short}}.
{: shortdesc}

If you do not already have an instance of {{site.data.keyword.en_short}}, <a href="/docs/event-notifications?topic=event-notifications-en-create-en-instance">create one now<a>.
## Overview
{: #en-send-push-overview}

To send push notifications, you will need to use the Event Notifications API or an {{site.data.keyword.en_short}} admin SDK.  Here is a summary of the tasks you will complete:

- Configure {{site.data.keyword.en_short}} to route push notifications.
	- <a href="/docs/event-notifications?topic=event-notifications-en-create-en-source">Create an {{site.data.keyword.en_short}} API source<a> to connect to your sending app.
	- <a href="/docs/event-notifications?topic=event-notifications-en-create-en-topic">Create an {{site.data.keyword.en_short}} topic<a> to accept incoming notifications.
	- <a href="/docs/event-notifications?topic=event-notifications-en-create-en-destination-push-fcm">Create an {{site.data.keyword.en_short}} push destination<a> to connect to your receiving app.
	- <a href="/docs/event-notifications?topic=event-notifications-en-create-en-subscription">Create and {{site.data.keyword.en_short}} subscription<a> to tie everything together.
- Instrument the receiving application.
- Test with CURL or Postman.
- Instrument the sending application.
- Test end to end.

Follow the links above to configure {{site.data.keyword.en_short}} to route push notifications.  Then continue to the instrumentation steps below.

## Instrument the receiving application
{: #en-send-push-instrument-receiving-app}
{: step}

To instrument your recieving application (mobile or web app), use one of the SDKs below:

- <a href="https://github.com/IBM/event-notifications-destination-android-sdk">Event Notifications Client SDK for Android<a>

Each SDK repo contains instrumentation instructions for the selected platform.

To initialize the SDK you will need credentials with IAM role of Device Manager.  Create these in the Service Credentials section of you {{site.data.keyword.en_short}} dashboard.  Specifically, you will need 'guid' and 'apikey' from you credential set.  'region' is also shown in the credential set if you need that.

In addition to the credentials you create, you will need the destination ID of the push destination you created above. To find that ID, visit the Destinations section of the {{site.data.keyword.en_short}} dashboard, locate your push destination in the list, and click on it to reveal the destination ID.

## Test with CURL or Postman
{: #en-send-push-instrument-receiving-app}
{: step}

After configuring you {{site.data.keyword.en_short}} instance and instrumenting your receiving application, but before instrumenting you sending application, it is often helpful to verify {{site.data.keyword.en_short}} is pushing to you app. You can use an API testing like CURL or Postman to do that.   

You will need the URL for the API source that you set up in the first step.  To find that URL, visit the Sources section of the {{site.data.keyword.en_short}} dashboard, and click 'Edit' in the context menu for your API source. 

You will also need an access token so that you API testing tool can access your {{site.data.keyword.en_short}} service.  Follow the instructions <a href="/docs/hs-crypto?topic=hs-crypto-retrieve-access-token">here<a> to generate a token.

## Instrument the sending application
{: #en-send-push-instrument-sending-app}
{: step}

To instrument your sending application, use one of the SDKs below:

- <a href="https://github.com/IBM/event-notifications-node-admin-sdk">Event Notifications Admin SDK for Node.js<a>
- <a href="https://github.com/IBM/event-notifications-go-admin-sdk">Event Notifications Admin SDK for Go<a>

Each SDK repo contains instrumentation instructions for the selected platform.  The subtasks will be:

- Initialize your {{site.data.keyword.en_short}} SDK.
- Configure your message.
- Add code to send notifications.

### Initialize your {{site.data.keyword.en_short}} SDK.

To initialize the SDK, you will need credentials with IAM role of Manager.  Create these in the Service Credentials section of you {{site.data.keyword.en_short}} dashboard.  Specifically, you will need 'apikey' and 'region' from you credential set.

To initialize the SDK you will need credentials with IAM role of Device Manager.  Create these in the Service Credentials section of you {{site.data.keyword.en_short}} dashboard.  'region' is also shown in the credential set if you need that.

### Configure your message.

Configure your message by adding message-specific parameter values.  There are many of them, so see the repo documentation for details.

### Add code to send notifications.

There are a few more parameters and lines of code to actually send the message.  The parameter values needed here include the API source URL and the API source ID. To find the source ID, visit the Sources section of the {{site.data.keyword.en_short}} dashboard, locate your API source in the Sources list, and click on it to reveal the source ID.  To find API source URL, click 'Edit' in the context menu for your API source.

## Test end-to-end
{: #en-send-push-test}
{: step}
