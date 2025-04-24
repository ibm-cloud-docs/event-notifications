---

copyright:
  years: 2021, 2025
lastupdated: "2025-04-24"

keywords: event notifications, event-notifications, email.templates
subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Email Templates
{: #en-email-templates}

There are 2 types of Email templates that are supported by {{site.data.keyword.en_short}}:

   * [Custom Email notification](#en-custom-email-notification)
   * [Custom Email invitation](#en-custom-email-invitation)

## Personalizing templates
{: #en-template-personalization}

Email personalization refers to the practice of tailoring email content and messaging to individual recipients or specific segments of your email list based on their personal preferences, behaviors, demographics, or interactions with your brand. The goal of email personalization is to create a more engaging and relevant email experience for each recipient, which can lead to higher open rates, click-through rates, and conversions. See the following list of common ways you might personalize the email messaging:

   * Personalized greetings: Address the recipient by their first name in the email's salutation to make the email feel more personalized and less generic.
   * Product recommendations: Suggest products or services that are relevant to the recipient based on their past purchases.
   * Dynamic content: Use dynamic content blocks that can change based on recipient data, such as location, recent interactions, or purchase history.
   * Personalized content recommendations: Provide recommendations to specific information sources, such as blog posts, articles, or videos, based on the recipient's previous engagement with your content.
   * Location-based personalization: Customize content or promotions based on the recipient's geographic location or time zone.


When you create a template to enable personalization, add a placeholder in the HTML Handlebars format, for example: 

    ```
    {{ibmenreferer personalization ibmenmailto 'name'}}
    ```

The personalization tags are described in the following list:

   * `ibmenreferer`: Specifies where to enable the personalization. 
   * `personalization`: Specifies from where to select personalization values in the send notifications payload.
   * `ibmenmailto`: Iterate through an array of emails to which mapping can be done for personalization.
   * `name`: Specifies which value to select from a key. 


## Custom Email Notification
{: #en-custom-email-notification}

Provide a subject and construct the body. Include a placeholder for inserting the unsubscribe text, along with the unsubscription URL. This placeholder, represented as `{{ibmen_unsubscription}}`, is used to substitute the unsubscription URL.

In the send notification payload, add a `personalization` parameter to enable it. See the following examples for more details.


### Send notification payload example
{: #send-payload}

```json
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

### Notification template payload example
{: #full-payload}


``` html
    <html lang="en">
        <head>
        </head>
        <body>
            <div class="container">
                <h1>
                    New Product Information
                </h1>
                <p>
                    Hello {{ibmenreferer personalization ibmenmailto 'name'}}, Good {{data.greet}}
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

## Custom Email Invitation
 {: #en-custom-email-invitation}

 Provide a subject and construct the body. Include a placeholder for inserting the invitation text, accompanied by the subscription URL. This placeholder, represented as `{{ibmen_invitation}}`, is used to substitute the invitation URL.

### Invitation Template Payload Example
 {: #invitation-payload}

 ``` html
 <html>
     <head>
         <title>
             IBM Event Notifications
         </title>
     </head>
     <body>
         <p>
             Hello! Invitation template
         </p>
         <table>
             <tr>
                 <td>
                     Hello invitation link:{{ibmen_invitation }} 
                 </td>
             </tr>
         </table>
     </body>
 </html>
 ```
