---

copyright:
  years: 2025
lastupdated: "2025-10-29"

keywords: predefined templates

subcollection: event-notifications
---
{{site.data.keyword.attribute-definition-list}}

# Pre-defined templates
{: #en-predefinedTemplates}

You can use pre-defined templates to design and structure notification messages.

You can modify pre-defined templates to best suit your requirements and save it as a user-defined template. They are a ready reference of the significant fields in the notifications. Thus they help build relevant and actionable alert notifications. It is not necessary to create templates from the ground up, nor is an in-depth understanding of event payload structures required.

Pre-defined templates are detailed structures of event payloads to be sourced from various {{site.data.keyword.cloud_notm}} event services for each destination like Slack, Email, and MS Teams. A single pre-defined template is defined for a pair of source and destination each. For example, a pre-defined template is defined for Resource Lifecycle event as a source and Slack as a destination.
{: shortdesc}

However, if there is no user-defined template attached to the Subscription, the notification message structures itself based on the pre-defined template if present.
{: important}

Pre-defined template for In-built Email as a destination and any of the source types cannot be customized.
{: note}

## Use pre-defined templates to create user-defined templates
{: #en-createUserdefinedTemplates}

To create a new customized template by using pre-defined template, follow these steps,

1. Click **Templates** on the left panel of the Event Notifications instance console.

1. Click **Pre-defined** tab.

1. Click the pre-defined template for the destination you want to send the notification to and the required {{site.data.keyword.cloud_notm}} event source.

1. To customize the pre-defined template, read through the **Template details** section and click **Customize**.

1. You can edit the **Name**, **Description**, **Subject** fields.

1. Edit the template **Body** and click **Save**. It creates a new user-defined template. You can see this new template in the user-defined templates list in the **User-defined** tab.
