---

copyright:
  years: 2020, 2023
lastupdated: "2023-09-20"

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

Email personalization refers to the practice of tailoring email content and messaging to individual recipients or specific segments of your email list based on their personal preferences, behaviors, demographics, or interactions with your brand. The goal of email personalization is to create a more engaging and relevant email experience for each recipient, which can lead to higher open rates, click-through rates, and conversions. Here are some common ways email personalization can be implemented:

- Personalized Greetings: Addressing the recipient by their first name in the email's salutation can make the email feel more personalized and less generic.

- Product Recommendations: Analyzing a recipient's past purchases or browsing history and suggesting products or services that are relevant to their interests.

- Dynamic Content: Creating email templates with dynamic content blocks that can change based on recipient data, such as location, recent interactions, or purchase history.

- Personalized Recommendations: Providing personalized content recommendations, such as blog posts, articles, or videos, based on the recipient's previous engagement with your content.

- Location-Based Personalization: Customizing content or promotions based on the recipient's geographic location or time zone.

- In the send notification payload add a `personalisation` parameter to enable it

Let's look at the detailed flow with an example

**Step 1: Send Notification Payload**

```JSON
{
    "id": "b2198eb8-04b1-48ec-a78c-ee87694dd845",
    "time": "06/06/2022, 14:23:01",
    "source": "apisource/git",
    "specversion": "1.0",
    "ibmensourceid": "d6f08a53-05f6-465f-903e-03db3fa91b64:api",
    "data": {
      "greet": "Evening",
      "severity": "LOW",
      "short_description": "Success! Your Event Notifications instance is now able to send personalised notifications",
      "transaction_id": "e539778e-4915-4586-b4c9-48e44af5c010",
      "name": "IBM Cloud Event Notifications",
      "price": "100",
      "rating": "4.9"
    },
    "datacontenttype": "application/json",
    "ibmendefaultlong": "This is a original long message",
    "ibmendefaultshort": "IBM Cloud Event Notifications is a routing service that provides information about critical events in your IBM Cloud account",
    "ibmenmailto": "[\"john.piquet@ibm.com\"]",
    "personalization": {
      "john.piquet@ibm.com": {
        "name": "JOHN ALFA PIQUET"
      }
    }
}
```

**Step 2: While creating template to enable personalisation add a placeholder in the html handlebars format**

```JSON
{{ibmenreferer personalisation ibmenmailto 'name'}}
```

Full template payload

```HTML
<html lang="en">
    <head>
    </head>
    <body>
        <div class="container">
            <h1>
                New Product Information
            </h1>
            <p>
                Hello {{ibmenreferer personalisation ibmenmailto 'name'}}, Good {{data.greet}}
            </p>
            <div class="product-info">
                <h2>
                    {{data.name}}
                </h2>
                <p>
                    Price: ${{data.price}}
                </p>
                <p>
                    Description: {{ibmendefaultshort}}
                </p>
                <p>
                    Rating: {{data.rating}}
                </p>
            </div>
            <p>
                Thank you for your interest in our new product!
            </p>
            <p>
                Best regards,
            </p>
            <p>
                IBM Cloud
            </p>
            <h5>
                If you don't wish to receive these messages click here:{{ibmen_unsubscription}}
            </h5>
        </div>
    </body>
</html>
```

**Step 3: Explanation about the personalisation tag**

- The `ibmenreferer` field is used to identify where to enable the personalisation
- The second parameter `personalisation` helps to identify from where to pick personalisation values in the send notifications payload
- Third field `ibmenmailto` helps to iterate through array of emails to which mapping can be done for personalisation
- The last field helps to identify which value to pick from a key
