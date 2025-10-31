---

copyright:
  years: 2025
lastupdated: "2025-10-29"

keywords: markdown-formatted event notifications

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Markdown formatting
{: #en-markdown-formatted-notifications}

You can design an event notification message by using markdown formatting for Slack, Microsoft Teams, and Email destinations.
You include this message for one time in the event notification payload and it gets transformed to the required destination format syntax. You do not have to learn the destination format syntax.
{: shortdesc}

You can define templates to personalize the notifications sent for certain destinations like Email, Webhook, Slack, PagerDuty, and Event Streams.
You can use a template as a base and customize it to cater to upcoming requirements.

However, if you skip defining a template, you can still format notifications for Slack, Microsoft Teams, and Email that use markdown formatting.
To format notifications by using markdown formatting, you must include `ibmenmarkdown` field in the Event notifications payload.


## Precedence order for event notification structure and formatting
{: #en-markdown-formatted-precedence}

The notification has a certain structure and format for every destination. A precedence order is in place to transform the event notification payload structure into a meaningful message for each destination.

* A notification adheres to the user-defined template if you have defined one.

* A notification adheres to the pre-defined template if defined, if a user-defined template is not defined and a pre-defined template is defined for that pair of source and destination.

* If you do not define a template for a destination and not have a pre-defined template in place or have and include `ibmenmarkdown` field in the payload, a notification message maps to `ibmenmarkdown` field in the event notification payload.

* Else, if you do not include `ibmenmarkdown` field in the payload, a notification message maps to `ibmendefaultshort` and `ibmendefaultlong` fields in the event notification payload.

For Email as a destination, if you include `ibmenhtmlbody` field in the payload and do not define a template, a notification message maps to `ibmenhtmlbody` field. Else, a notification message maps to `ibmenmarkdown` field in the event notification payload.

## Structure event notifications payload by using Markdown formatting
{: #en-markdown-formatted-ibmenmarkdown}

The `ibmenmarkdown` field in the event notification payload must be a markdown-formatted text. It is designed one time and can be rendered in specific destination format at the Email, Slack, and Microsoft Teams destinations.

To use `ibmenmarkdown` field, refer to the following payload example.

```

{
  "id": "05f355bc-3560-4eee-be3c-81c8699ce698:api-20231208182311",
  "time": "2023-12-08 18:23:11.02356592 +0000 UTC m=+8401.056818844",
  "type": "*",
  "data": {
    "alert": "Alert from Event Notifications service for Toronto",
    "message": "Hi, Welcome from the IBM Cloud Event Notifications service. Reference-id: 09691643-a1f4-47b3-96a1-306f7abc3f3e"
  },
  "source": "de023095-70ab-48da-ad4d-5567886539cd:api",
  "subject": "Proactive monitoring test alert.",
  "specversion": "1.0",
  "ibmensourceid": "b291c708-8dea-463f-9448-70f8854c31db:api",
  "datacontenttype": "application/json",
  "ibmendefaultshort": "This is simple test alert from IBM Cloud Event Notifications service.",
  "ibmendefaultlong": "Hi, we are making sure from our side that the service is available for consumption.\n  If you are receiving this mail, it means we doing fine. Thank you.",
  "ibmenhtmlbody": "<head>",
  "ibmenmarkdown": "This is a *italic* message.\n- Item 1\n- Item 2\n**bold text** with more text data\n~~strike through~~\n1. order 1\n2. order 2\n```fenced code block```\n> block code\n`code`\n[Click here](https://example.com) for more info."
}

```

To understand the markdown formatting used to transform messages, check the [Markdown cheat sheet](https://markdownguide.offshoot.io/cheat-sheet/).

To understand the event notifications payload, check the [api specification](/apidocs/event-notifications#send-notifications) for sending a notification.

### Supported markdown elements
{: #en-supported-markdown-elements}

The following table lists the supported markdown elements for Slack, MS teams, and Email destinations.

|Elements                    | Markdown formatting              | Slack                               | MS teams                           |Email                               |
|----------------------------|---------------------------------|-------------------------------------|------------------------------------|------------------------------------|
| **Bold**                   | `**bold text**`                 | Supported                           | Supported                          | Supported                          |
| **Italic**                 | `*italic*`                      | Supported                           | Supported                          | Supported                          |
| **Ordered List**           | `1. Item`                       | Supported                           | Supported                          | Supported                          |
| **Unordered List**         | `- Item` or `* Item`            | Supported                           | Supported                          | Supported                          |
| **Links**                  |`[Text](http://example.com)`     | Supported                           | Supported                          | Supported                          |
| **Strikethrough**          |`~~strikethrough~~`              | Supported                           | Not Supported                      | Supported                          |
| **Inline Code**            | `` `code` ``                    | Supported                           | Not Supported                      | Supported                          |
| **Code Block**             | \```language code block ```     | Supported                           | Not Supported                      | Supported                          |
| **Blockquote**             | `> quote`                       | Supported                           | Not Supported                      | Supported                          |
| **Emojis**                 | `:emoji_name:` (for example, `:smile:`)| Supported                           | Not Supported                      | Not Supported                      |
{: caption="Supported markdown elements" caption-side="top"}


However, to know more about support for various markdown elements for Slack, check [Markdown support for Slack](https://markdownguide.offshoot.io/tools/slack/).

To learn more about support for various markdown elements for MS teams, check [Markdown support for MS Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/task-modules-and-cards/cards/cards-format?tabs=adaptive-md%2Cdesktop%2Cdesktop1%2Cdesktop2%2Cconnector-html).
