---

copyright:
  years: 2025
lastupdated: "2025-05-29"

keywords:

subcollection: event-notifications, markdown-formatted event notifications

---
{{site.data.keyword.attribute-definition-list}}

# Markdown formatting
{: #en-markdown-formatted-notifications}

You can design an event notification message by using markdown formatting for Slack, Microsoft Teams, and Email destinations.
You include this message for one time in the event notification payload and it gets transformed to the required destination format syntax. You do not have to learn the destination format syntax.
{: shortdesc}

You can define templates to personalize the notifications sent for certain destinations like Email, Webhook, Slack, PagerDuty, and Event Streams.
You can use a template as a base and customize it to cater to upcoming requirements.

However, if you skip defining a template, you can still format notifications for lack, Microsoft Teams, and Email that use markdown formatting.
To format notifications by using markdown formatting, you must include `ibmenmarkdown` field in the Event notifications payload.


## Precedence order for event notification structure and formatting
{: #en-markdown-formatted-precedence}

The notification has a certain structure and format for every destination. A precedence order is in place to transform the event notification payload structure into a meaningful message for each destination.

* A notification adheres to the defined template if you have defined one.

* If you do not define a template for a destination and include `ibmenmarkdown` field in the payload, a notification message maps to `ibmenmarkdown` field in the event notification payload.

* Else, if you do not include `ibmenmarkdown` field in the payload, a notification message maps to `ibmendefaultshort` and `ibmendefaultlong` fields in the event notification payload.

For Email as a destination, if you include `ibmenhtmlbody` field in the payload and do not define a template, a notification message maps to `ibmenhtmlbody` field. Else, a notification message maps to `ibmenmarkdown` field in the event notification payload.

## ibmenmarkdown field usage
{: #en-markdown-formatted-ibmenmarkdown}

The `ibmenmarkdown` field in the event notification payload must be a markdown-formatted text. It is designed one time and can be rendered in specific destination format at the Email, Slack, and Microsoft Teams destinations.

To understand the usage of `ibmenmarkdown` field, refer to the following payload example.

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

To understand the markdown formatting used to transform messages, check the [Markdown Cheat Sheet](https://markdownguide.offshoot.io/cheat-sheet/).
