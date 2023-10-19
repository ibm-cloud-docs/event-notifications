---

copyright:
  years: 2020, 2023
lastupdated: "2023-10-10"

keywords: event-notifications, event notifications, about event notifications, destinations, slack

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Slack
{: #en-destinations-slack}

Slack is a messaging platform that helps teams to connect and collaborate. When you select slack as a service destination, any subscribed notification about an event can be sent as a message to slack channels.
{: shortdesc}

When a message of length greater than 3000 characters is sent to slack, the message text gets truncated with leaders `[...]`.
{: note}

## Generate slack incoming webhook URL
{: #en-generate-slack-incoming-webhook-url}

To post a slack notification, that you need to generate an incoming webhook URL. To generate the URL, follow these steps: [Incoming webhooks for Slack](https://api.slack.com/messaging/webhooks){: external}.

## Configuring a slack destination
{: #en-slack-configure-destination}

You can configure a slack destination in the `Destinations` tab. As part of the configuration, enter the Slack Incoming Webhook URL. Create a subscription to associate the slack destination to a topic.

## Configuring a slack subscription
{: #en-slack-configure-sub}

You can add attachment color to individual slack subscription based on hex code, for example, "#0000FF" for blue.

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

*ibmendefaultshort* is the default short payload that is provided in the incoming payload.
*attachment_color* is the color that is applied to the notification, which was provided during subscription.
*ibmendefaultlong* is the default long payload that is provided in the incoming payload.
*data* is the data JSON provided in the incoming payload and format as JSON in the slack notification.

## Testing a Slack destination configuration
{: #en-slack-test-destination}

You can test a Slack destination in the options menu provided againts the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

For more information on testing a destination, see [here](/docs/event-notifications?topic=event-notifications-en-test-destination).


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
