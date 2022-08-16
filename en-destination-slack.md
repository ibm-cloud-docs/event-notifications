---

copyright:
  years: 2020, 2022
lastupdated: "2022-08-16"

keywords: event-notifications, event notifications, about event notifications, destinations, slack

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

# Slack
{: #en-destinations-slack}

A slack represents a service destination, where an incoming notification can be consumed programmatically. For example, an incoming notification about an event can trigger a slack notification based on the content of the incoming notification.
{: shortdesc}

When a message of length greater than 3000 characters is sent to slack, the message text will get truncated with leaders `[...]`.
{: note}

## Generate slack incoming webhook URL 
{: #en-generate-slack-incoming-webhook-url}

To post a slack notification you will need to generate an incoming webhook URL. To generate the URL, follow these steps: [Incoming webhooks for Slack](https://slack.com/intl/en-in/help/articles/115005265063-Incoming-webhooks-for-Slack){: external}.

## Configuring a slack destination
{: #en-slack-configure-destination}

You can configure a slack destination in the `Destinations` tab. As part of the configuration, enter the Slack Incoming Webhook URL. Create a subscription to associate the slack destination to a topic.

## Configuring a slack subscription
{: #en-slack-configure-sub}

You can add attachment color to individual slack subscription based on hex code for e.g. "#0000FF" for blue 

## How a slack notification from Event Notifications looks 
{: #en-how-a-slack-notification-from-en-looks}

Event notification generates slack notifications from incoming payload. The template event notification use to send to slack looks like following - 

```sh
{
   "text": "*{{event.ibmendefaultshort}}*",
   "attachments": [{
      "color": "{{config.subscription.attachment_color}}",
      "blocks": [{
         "type": "section",
         "text": {
            "type": "mrkdwn",
            "text": "{{event.ibmendefaultlong}}"
         }
      },
      {
         "type": "divider"
      },
      {
         "type": "section",
         "text": {
            "type": "mrkdwn",
            "text": "```{{event.data}} ```"
         }
      }
      ]
   }]
}
```

Here - 

*ibmendefaultshort* is the default short payload provided in the incoming payload.
*attachment_color* is the color that will be applied to the notification which was provided during subscription.
*ibmendefaultlong* is tbe default long payload provided in the incoming payload.
*data* is the data JSON provided in the incoming payload and will be formated as json in the slack notification.

## Slack retry policy
{: #en-slack-retry}

When publishing a slack notification, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (webhook).

In addition, the following timeout conditions cause the slack call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the Slack webhook URL fails even after retry attempts, the notification is lost.
{: note}
