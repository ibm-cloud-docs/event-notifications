---

copyright:
  years: 2021, 2025
lastupdated: "2025-04-24"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} template
{: #en-create-en-template}

An {{site.data.keyword.en_full_notm}} template is a pre-defined layout that includes images, text, and dynamic content based on an event. You can use a template as a base and customize it rather than creating a new one from scratch each time. 
{: shortdesc}

## Creating a template
{: #en-create-template}

1. In the {{site.data.keyword.cloud_notm}} console, click the **menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Event notifications**. 
1. Click the name of your {{site.data.keyword.en_short}} instance. 
1. Select **Templates** from the left panel.
1. Enter details about the template such as the name and description, and select a template type. Event Notifications currently supports 4 templates:

    * [Custom Email Notification](/docs/event-notifications?topic=event-notifications-en-email-templates)
    * [Custom Email Invitation](/docs/event-notifications?topic=event-notifications-en-email-templates)
    * [Webhook Notification](/docs/event-notifications?topic=event-notifications-en-webhook-notifications-template)
    * [Slack Notification](/docs/event-notifications?topic=event-notifications-en-slack-notification-template)
    * [PagerDuty Notification](/docs/event-notifications?topic=event-notifications-en-pagerduty-notification-template)
    * [Event Streams Notification](/docs/event-notifications?topic=event-notifications-en-event-streams-notification-template)
   
1. Click **Add** to save your updates. 


## Handlebars Integration

Handlebars is a templating language that allows for dynamic content generation within templates. Handlebars can be used to customize notification messages using template variables ,conditional logic and various other helpers.

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

### Contains Helper

The contains helper allows users to check whether there is a specific word in any of the fields of the payload.

#### Example:

```
"data": 
{
	"message": "this is test alert from dev account"
}
```
Use the contains helpers like: 

```handlebars
{
{{#contains data.message "dev"}}
"environment": "development"
{{/contains}}
}
```

There are more helpers available for use that can be referenced from [here](https://github.com/aymerick/raymond?tab=readme-ov-file#built-in-helpers)
{: note}
