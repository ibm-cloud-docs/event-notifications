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

To post a slack notification, that you need to generate an incoming webhook URL. To generate the URL, follow these steps: [Incoming webhooks for Slack](https://api.slack.com/messaging/webhooks){: external}.

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

## Testing a Slack destination configuration
{: #en-slack-test-destination}

You can test a Slack destination in the options menu provided againts the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

For more information on testing a destination, see [here](/docs/event-notifications?topic=event-notifications-en-test-destination).


## Handlebars Integration

Handlebars is a templating language that allows for dynamic content generation within templates. In the context of IBM Event Notification Slack Destination, Handlebars can be used to customize notification messages using template variables and conditional logic.

### Template Variables

Template variables are placeholders within the notification message templates that get replaced with actual data when a notification is triggered. These variables allow users to personalize messages and include relevant information from the event being notified.

#### Usage:

```handlebars
{{variable_name}}
```

Example:
```handlebars
Event Name: {{event_name}}
```

### Conditional Logic Helper

Conditional logic allows users to define conditions within the message templates, enabling dynamic content generation based on the values of variables. This feature is useful for creating flexible notification messages that adapt to different scenarios.

#### Usage:

```handlebars
{{#if condition}}
   
{{else}}
   
{{/if}}
```

Example:
```handlebars
{{#if severity}}
   Severity: {{severity}}
{{else}}
   No severity information available
{{/if}}
```

Note - There are more helpers available for use that can be referenced from here - https://github.com/aymerick/raymond?tab=readme-ov-file#built-in-helpers

## Input API for Templates

The Input API for Templates provides a mechanism for users to define notification message templates programmatically. Users can generate JSON blocks representing Block Kit layouts using the Block Kit Builder and encode them in base64 format to include in their templates.

### JSON Blocks

JSON blocks represent the layout and structure of notification messages using the Slack Block Kit format. Users can create rich and interactive message layouts by defining various block types such as sections, actions, and buttons. Handlebars can be used with json blocks for powerful integration.You can design your json blocks via following builder - https://app.slack.com/block-kit-builder

#### Usage:

```json
{
   "blocks": [
      {
         "type": "section",
         "text": {
            "type": "mrkdwn",
            "text": "This is a notification message."
         }
      },
      {
         "type": "divider"
      },
      {
         "type": "actions",
         "elements": [
            {
               "type": "button",
               "text": {
                  "type": "plain_text",
                  "text": "View Details",
                  "emoji": true
               },
               "url": "https://example.com/details"
            }
         ]
      }
   ]
}
```

### Base64 Encoding

To include JSON blocks in the template, they need to be encoded in base64 format. This ensures that the data is transmitted safely and can be decoded accurately when rendering the notification message.

#### Example Create Template Usage:

```plaintext
{
	"name": "Template for",
	"params": {
		"body": "eyJibG9ja3MiOlt7InR5cGUiOiJzZWN0aW9uIiwidGV4dCI6eyJ0eXBlIjoibXJrZG93biIsInRleHQiOiJUaGlzIGlzIGEgbm90aWZ5aW5nIG1lc3NhZ2UuIn19LHsidHlwZSI6ImRpdmlkZXIiLCJ0ZXh0Ijp7InR5cGUiOiJtbmF2IiwidGV4dCI6IlRoaXMgaXMgYSBuZXcgbm90aWZ5aW5nIG1lc3NhZ2UuIiwiZW1vamkiOnRydWV9fV0seyJ0eXBlIjoiYWN0aW9ucyIsImVsZW1lbnRzIjpbeyJ0eXBlIjoicGxhaW5fdGV4dCIsInRleHQiOnsic2VsZWN0aW9yIjp7InR5cGUiOiJwbGFpbl90ZXh0IiwidGV4dCI6IlZpZXcgRGV0YWlscyIsImVtb2ppIjp0cnVlfX19XX0="
	},
	"type": "slack.notification"
}
```


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
