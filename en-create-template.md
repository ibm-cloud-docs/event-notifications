---

copyright:
  years: 2020, 2023
lastupdated: "2023-08-29"

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

- Custom Email notification
- Custom Email invitation

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
   - For `Custom Email notification` template
      - Enter **Subject**, which is optional.
      - Enter **Body**, which is an html template.
      - The HTML template must include a placeholder for inserting the unsubscribe text, along with the unsubscription URL. This placeholder, represented as `{{ ibmen_unsubscription }}`, will be utilized to substitute the unsubscription URL.
      - Click on **Preview** to see the template preview.
      - Click on Add.
   - For `Custom Email invitation` template
      - Enter **Subject**, which is optional.
      - Enter **Body**, which is an html template.
      - The HTML template must include a placeholder for inserting the invitation text, accompanied by the subscription URL. This placeholder, represented as `{{ ibmen_invitation }}`, will be utilized to substitute the invitation URL.
      - Click on **Preview** to see the template preview.
      - Click on Add.


## Personalisation in templates
{: #en-template-personalisation} {: step}

- In the send notification payload add a `personalisation` parameter to enable it
```
 "personalisation": {
      "johnny.piquet@ibm.com": {
        "name": "John"
      }
    }
```

- While creating template to enable personalisation add a placeholder in the html handlebars format

```
{{ibmenreferer personalisation ibmenmailto 'name'}}
```
    - The `ibmenreferer` field is used to identify where to enable the personalisation
    - The second parameter `personalisation` helps to identify from where to pick personalisation values in the send notifications payload
    - Third field `ibmenmailto` helps to iterate through array of emails to which mapping can be done for personalisation
    - The last field helps to identify which value to pick from a key
