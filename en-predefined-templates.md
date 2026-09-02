---

copyright:
  years: 2025, 2026
lastupdated: "2026-09-02"

keywords: predefined templates

subcollection: event-notifications
---
{{site.data.keyword.attribute-definition-list}}

# Managing pre-defined templates for notification messages
{: #en-predefinedTemplates}

You can use pre-defined templates to design and structure notifications that are managed by using {{site.data.keyword.en_short}}. {{site.data.keyword.cloud_notm}} services source these payloads and destinations like Slack, email and Microsoft Teams render them in a user-defined template structure.
{: shortdesc}

For more custom messages, you can modify an existing template to better suit your needs and save it as a user-defined template.
{: tip}

A pre-defined template definition maps to a pair of a source and a destination and has a single instance. For example, a pre-defined template definition maps to a Resource Lifecycle event as a source and a Slack as a destination.

The pre-defined templates are a ready reference to the significant fields in the notifications. Thus they help build relevant and actionable alert notifications. You might not need to create templates from the ground up, nor you might require an in-depth understanding of event payload structures.

If the subscription doesn't define any user-defined template, the notification message structures itself based on the pre-defined template if present.
{: restriction}

You can't customize a pre-defined template for In-built email as a destination for any of the source types.
{: exception}

## Use pre-defined templates to create user-defined templates
{: #en-createUserdefinedTemplates}

To create a customized template by using pre-defined template, follow these steps:

1. Click **Templates** on the {{site.data.keyword.en_short}} instance page.

1. Click **Pre-defined** tab.

1. Select the pre-defined template for the destination you want to send the notification to and the required {{site.data.keyword.cloud_notm}} event source.

1. Click **Customize template** to edit the pre-defined template details.

1. Edit the name, template body and click **Save**. It creates a user-defined template. You can see this template in the user-defined templates list in the **User-defined** tab.
