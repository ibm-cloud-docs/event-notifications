---

copyright:
  years: 2025
lastupdated: "2025-09-25"

keywords: event-notifications, event notifications, about event notifications, templates, app configuration, app config

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.appconfig_short}} Notification Template
{: #en-app-configuration-notification-template}

{{site.data.keyword.appconfig_short}} is a centralized feature management and configuration service for use with web and mobile applications, microservices, and distributed environments.
{: shortdesc}

To learn more about the {{site.data.keyword.appconfig_short}} destination, see [App Configuration](/docs/event-notifications?topic=event-notifications-en-destination-app-configuration&interface=ui)

## Constructing an {{site.data.keyword.appconfig_short}} notification template
{: #en-construct-app-configuration-template}

Construct the template block. Make sure that the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.

Handlebars is a templating language that allows for dynamic content generation within templates. Handlebars can be used to customize notification messages by using template variables and conditional logic. See [Handlebars](/docs/event-notifications?topic=event-notifications-en-create-en-template&interface=ui#handlebars-integration) for more information on the various helpers available while creating templates.

Make sure you include `"enabled":"true"` or `"enabled":"false"` in your template depending on how you want your feature flag to behave when a notification is sent to the {{site.data.keyword.appconfig_short}} destination. Without this, there will be no action in the destination when the notification is sent and you may face errors when sending notifications from the API.
{: important}

### {{site.data.keyword.appconfig_short}} notification template example
{: #en-appconfig-template-example}


```handlebars
{
{{#if (equal severity "LOW")}}
"enabled": false
{{else}}
"enabled": true
{{/if}}
}
```



