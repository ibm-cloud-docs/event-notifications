---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-30"

keywords: event-notifications, event notifications, about event notifications, destinations, slack

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}
{:codeblock: .codeblock}

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


To configure a Slack destination, complete the following steps:

1. click **Destinations** in the {{site.data.keyword.en_short}} instance.

1. Click **Create** to add a new destination.

1. Enter the following destination details in the **Create destination** dialog:

   - **Name**: Enter a name for your destination.
   - **Description**: Optionally, enter a description for your destination.
   - **Type**: Under **Destination**, select **Slack** from the list as your destination type.
   - **Send messages**: Choose one of the following options:
       - **Using incoming webhooks**: Provide the Slack Incoming Webhook URL.
       - **Using direct messages**: Provide the Bot User OAuth Token.

1. Click **Create destination**.


## Configuring a slack subscription
{: #en-slack-configure-sub}

To configure a slack subscription: 

1. **Using Incoming Webhooks**
   - You can add an attachment color to individual Slack subscriptions based on a hex code. For example, use #0000FF to set the color to blue.
1. **Using Direct Messages**
   - You can provide a list of member IDs and channel IDs. If channel IDs are provided, the application is integrated into the specified channels.

## How a default slack notification (without template) from Event Notifications looks
{: #en-how-a-slack-notification-from-en-looks}

{{site.data.keyword.en_short}} generates Slack notifications from the incoming payload. The template that {{site.data.keyword.en_short}} uses to send to Slack looks like the following example:

```json
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
              "text": "{{ibmendefaultshort}}",
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
        "text": "{{ibmendefaultlong}}",
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
          "text": "```{{event_payload}}```"
        }
      ]
    }
  ]
}
```
{: codeblock}

Where:

- `ibmendefaultshort` is the default short payload that is provided in the incoming payload.
- `ibmendefaultlong` is the default long payload that is provided in the incoming payload.
- `data` is the data JSON provided in the incoming payload and formatted as JSON in the Slack notification.

For more information on how to create and use Slack notification templates, see [Slack notification templates](/docs/event-notifications?topic=event-notifications-en-slack-notification-template).

## Testing a Slack destination configuration
{: #en-slack-test-destination}

You can test a Slack destination in the options menu next to the destination. You can test whether the provided configuration is correct with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).




## Slack retry policy
{: #en-slack-retry}

When publishing a Slack notification, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
