---

copyright:
  years: 2020, 2023
lastupdated: "2023-08-25"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} template
{: #en-create-en-template}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Create an {{site.data.keyword.en_short}} template. Template is a pre-defined layout, that may include content like images, text and dynamic content based on event. Rather than creating a new content from scratch each time, you can use a template as a base and configure them in subscription. {{site.data.keyword.en_short}} supports the following templates:

- Custom Email invitation
- Custom Email notification
{: shortdesc}

## Create a template
{: #en-create-template}
{: step}

Click `Templates` in the {{site.data.keyword.en_short}} console.

## Add template details
{: #en-template-details}
{: step}

- Click `Create` to display template side panel.
- Complete the following template details:
    - `Name`: name of the template.
    - `Description`: add an optional description.
- Select a Template type from the **Template** list.
   - For `Custom Email invitation` template
      - Enter **Subject**, which is optional.
      - Enter **Body**, which is a html template.
      - Html template should contain a placeholder for inserting the invitation text along with the URL to subscribe.
      - Click on  **Preview**, to view the template preview.
   - For `Custom Email notification` template
      - Enter **Subject**, which is optional.
      - Enter **Body**, which is a html template.
      - Html template should contain a placeholder for inserting the unsubscribe text along with the URL to unsubscribe.
      - Click on  **Preview**, to view the template preview.

## Add the template
{: #en-template-finish}
{: step}

Click `Save`.