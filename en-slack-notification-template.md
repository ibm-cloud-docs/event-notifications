---

copyright:
  years: 2026
lastupdated: "2026-02-24"

keywords: event-notifications, event notifications, about event notifications, templates, slack

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# Slack Notification Template
{: #en-slack-notification-template}

Slack is a messaging platform that helps teams to connect and collaborate. When you select slack as a service destination, any subscribed notification about an event can be sent as a message to slack channels.
{: shortdesc}

For more information about the Slack destination, see [Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack).

## How to create a Slack Notification Template
{: #en-create-slack-template}

Construct stacks of blocks. For more details, see the [Slack Block Kit](https://docs.slack.dev/block-kit/){: external}.

Users can generate or validate a static JSON by using the [Block Kit builders](https://app.slack.com/block-kit-builder). This is added as a slack template in Event Notifications.

### Example Create Template Usage:
{: #en-slack-template}

The following sections describe how to create Slack notification templates using the Input API and JSON blocks.

#### Input API for Templates
{: #en-input-api}

The Input API for Templates provides a mechanism for users to define notification message templates programmatically. Users can generate JSON blocks representing Block Kit layouts by using the Block Kit Builder and encode them in base64 format to include in their templates.

#### JSON Blocks
{: #en-json-blocks}

JSON blocks represent the layout and structure of notification messages by using the Slack Block Kit format. Users can create rich and interactive message layouts by defining various block types such as sections, actions, and buttons. Handlebars can be used with JSON blocks for powerful integration. You can design your JSON blocks via the following builder - https://app.slack.com/block-kit-builder

##### Usage:
{: #en-usage}

The following examples demonstrate how to use different Slack block types in your notification templates.

###### Section Block
{: #en-template-section-type}

Section blocks display text content with optional accessories like buttons or images. To learn more about section blocks, refer [Section Block](https://docs.slack.dev/reference/block-kit/blocks/section-block).

**Character limit considerations**

As per Slack Block Kit limitations, a section block supports a maximum of 3000 characters in the text field. If the generated content exceeds this limit, slack will reject the payload and the notification will not be delivered. The following error message is returned: `Slack failed with an error message: 'invalid_blocks' and status code: 400`. Use [context blocks](/docs/event-notifications?topic=event-notifications-en-slack-notification-template#en-template-context-type) to avoid notification dropping for messages exceeding 3000 characters.
{: note}


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

###### Context Block
{: #en-template-context-type}

Context blocks display supplementary information with text and images in a compact format. To learn more about context blocks, refer [Context Block](https://docs.slack.dev/reference/block-kit/blocks/context-block/).

**Character limit considerations**

A context block supports a maximum of 16000 characters in the text field. If the generated content exceeds this limit, the message will be truncated but the notification will still be delivered successfully.
{: note}

```json
{
   "blocks": [
      {
         "type": "context",
         "elements": [
               {
                  "type": "image",
                  "image_url": "https://image.freepik.com/free-photo/red-drawing-pin_1156-445.jpg",
                  "alt_text": "images"
               },
               {
                  "type": "mrkdwn",
                  "text": "This is a notification message."
               }
         ]
      }
   ]
}
```

#### Base64 Encoding
{: #en-encoding}

To include JSON blocks in the template, they need to be encoded in base64 format. This helps ensure that the data is transmitted safely and can be decoded accurately when rendering the notification message.

##### Example Create Template Usage:
{: #en-slack-template-example}

The following example shows a complete template request with base64-encoded JSON blocks.

```json
{
	"name": "Template for TIP",
	"params": {
		"body": "eyJibG9ja3MiOlt7InR5cGUiOiJzZWN0aW9uIiwidGV4dCI6eyJ0eXBlIjoibXJrZG93biIsInRleHQiOiJUaGlzIGlzIGEgbm90aWZ5aW5nIG1lc3NhZ2UuIn19LHsidHlwZSI6ImRpdmlkZXIiLCJ0ZXh0Ijp7InR5cGUiOiJtbmF2IiwidGV4dCI6IlRoaXMgaXMgYSBuZXcgbm90aWZ5aW5nIG1lc3NhZ2UuIiwiZW1vamkiOnRydWV9fV0seyJ0eXBlIjoiYWN0aW9ucyIsImVsZW1lbnRzIjpbeyJ0eXBlIjoicGxhaW5fdGV4dCIsInRleHQiOnsic2VsZWN0aW9yIjp7InR5cGUiOiJwbGFpbl90ZXh0IiwidGV4dCI6IlZpZXcgRGV0YWlscyIsImVtb2ppIjp0cnVlfX19XX0="
	},
	"type": "slack.notification"
}
```
