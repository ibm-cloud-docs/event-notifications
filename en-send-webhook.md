---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-05"

keywords: event notifications, event-notifications, webhook, slack, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Trigger a Slack Webhook using {{site.data.keyword.en_short}} Webhook Destination
{: #en-send-webhook}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

This tutorial describes how to trigger Slack webhook using {{site.data.keyword.en_short}}.
{: shortdesc}

If you do not already have an instance of {{site.data.keyword.en_short}}, create one. See [Create an Event Notifications service instance](/docs/event-notifications?topic=event-notifications-en-create-en-instance) for more details.

## Overview
{: #en-send-webhook-overview}

To trigger a slack webhook, you must use the Event Notifications API in Binary Mode by following [Cloud Event Spec](https://github.com/cloudevents/spec)

A summary of the tasks you complete before triggering a webhook is as follows:

- Configure {{site.data.keyword.en_short}} to route push notifications.

	- Create an API source to connect to your sending app. See [Create an {{site.data.keyword.en_short}} API source](/docs/event-notifications?topic=event-notifications-en-create-en-source) for more details.
	- Create a topic to accept incoming notifications. See [Create an {{site.data.keyword.en_short}} topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic) for more details.
	- Create a Webhook destination register your application using Webhook URL. See [Create an {{site.data.keyword.en_short}} push destination for Webhook](/docs/event-notifications?topic=event-notifications-en-create-en-destination-webhook) for more details.
	- Create a subscription to tie everything together. See[Create an {{site.data.keyword.en_short}} subscription](/docs/event-notifications?topic=event-notifications-en-create-en-subscription) for more details.

- Test the receiving application with cURL or Postman.
- Instrument the sending application.
- Test the sending and receiving applications end-to-end.

## Test with cURL or Postman
{: #en-test-with-curl-or-postman}
{: step}

You have configured your {{site.data.keyword.en_short}} instance, but before instrumenting your sending application, verify that {{site.data.keyword.en_short}} is pushing to your registered webhook. Use an API testing app like cURL or Postman to verify that notifications are pushing to your app. 

You need the URL for the API source that you created in the first step. To find that URL, visit the `Sources` section of the {{site.data.keyword.en_short}} dashboard, and click `Edit` in the context menu of your API source. 

You also need an access token so that your API testing tool can access your {{site.data.keyword.en_short}} service. Follow the instructions in [Retrieving an access token](/docs/hs-crypto?topic=hs-crypto-retrieve-access-token) to generate a token.

Sample cURL to trigger slack webhook - 

```curl
 curl --location --request POST '<<EN_REGION_URL>>/event-notifications/v1/instances/<<EN_INSTANCE_ID>>/notifications' \
--header 'Accept: application/json' \
--header 'ce-id: id' \
--header 'ce-specversion: 1.0' \
--header 'ce-type: type' \
--header 'ce-source: source ' \
--header 'ce-ibmensourceid: <<YOUR_EN_SOURCE>>' \
--header 'Authorization: Bearer <<YOUR_API_TOKEN>>' \
--header 'Content-Type: application/json' \
--data-raw '{
   <<JSON Body Supported by Slack - https://api.slack.com/messaging/webhooks>>
}'
```

The above request is in Binary Mode as mandatory Cloud Events headers are part of header. Any payload and headers coming to EN will be transferred to webhook as it is. No modifications will be done to paylod or header. 
