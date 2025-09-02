---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-30"

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

To post a slack notification, that you need to generate an incoming webhook URL. To generate the URL, follow these steps: [Incoming webhooks for Slack](https://docs.slack.dev/messaging/sending-messages-using-incoming-webhooks/){: external}.

## Configuring a slack destination
{: #en-slack-configure-destination}

Before you configure Slack as a destination for Direct Messages, ensure you have created and configured a Slack app with a bot token scope of `chat:write`. Refer to the Slack API documentation for more information: (https://api.slack.com/quickstart#creating).
{: note}


To configure a Slack destination, follow these steps:

1. Log in to your {{site.data.keyword.en_short}} instance dashboard and navigate to Destinations.

1. Click **Add** to add a new destination.

1. In the Add a destination side panel, provide the following details:

  - **Name**: Enter a name for your destination.
  - **Description**: Optionally, enter a description for your destination.
  - **Type**: Under Destination, select Slack from the list as your destination type.
  - **Send messages:** Choose one of the following options:
      - **Using incoming webhooks**: Provide the Slack Incoming Webhook URL.
      - **Using direct messages:** Provide the Bot User OAuth Token.


## Configuring a slack subscription
{: #en-slack-configure-sub}

1. Using Incoming Webhooks
   - You can add attachment color to individual Slack subscriptions based on a hex code. For example, use #0000FF to set the color to blue.
1. Using Direct Messages
   - You can provide a list of member ids and channel ids. If channel ids are provide then the application shall be integrated into the specified channels.

## How a default slack notification (without template) from Event Notifications looks
{: #en-how-a-slack-notification-from-en-looks}

Event notification generates slack notifications from incoming payload. The template event notification use to send to slack looks like following -

```sh
{
  "blocks": [
    {
      "type": "rich_text",
      "elements": [
        {
          "type": "rich_text_section",
          "elements": [
            {
              "type": "text",
              "text": "{{ibmendefaultshort}}", // Read from event payload
              "style": {
                "bold": true
              }
            }
          ]
        }
      ]
    },
    {
      "type": "section",
      "text": {
        "type": "plain_text",
        "text": "{{ibmendefaultlong}}", // Read from event payload
        "emoji": true
      }
    },
    {
      "type": "divider"
    },
    {
      "type": "context",
      "elements": [
        {
          "type": "mrkdwn",
          "text": "```{{event_payload}}```" // Full notification payload sent to /notifications endpoint
        }
      ]
    }
  ]
}
```

Here -

*ibmendefaultshort* is the default short payload that is provided in the incoming payload.
*ibmendefaultlong* is the default long payload that is provided in the incoming payload.
*data* is the data JSON provided in the incoming payload and format as JSON in the slack notification.

For more information on how to create and use slack notification templates , see [here](/docs/event-notifications?topic=event-notifications-en-slack-notification-template)

## Testing a Slack destination configuration
{: #en-slack-test-destination}

You can test a Slack destination in the options menu provided against the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).




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
