---

copyright:
  years: 2021, 2024
lastupdated: "2024-10-30"

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

1. In the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Event notifications**. 
1. Click the name of your {{site.data.keyword.en_short}} instance. 
1. Enter details about the template, and select a template type:
  
   * **Custom Email notification**: Provide a subject and construct the body. Include a placeholder for inserting the unsubscribe text, along with the unsubscription URL. This placeholder, represented as `{{ibmen_unsubscription}}`, is used to substitute the unsubscription URL.
   * **Custom Email invitation**: Provide a subject and construct the body. Include a placeholder for inserting the invitation text, accompanied by the subscription URL. This placeholder, represented as `{{ibmen_invitation}}`, is used to substitute the invitation URL.
   * **Slack notification**: Construct stacks of blocks. For more details, see the [Slack Block Kit](https://api.slack.com/block-kit){: external}.
   * **Webhook notification**: Construct the template block. Make sure the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.

Click **Preview** to get a preview of your updates.
{: tip}

1. Click **Add** to save your updates. 

## Personalizing templates
{: #en-template-personalization}

Email personalization refers to the practice of tailoring email content and messaging to individual recipients or specific segments of your email list based on their personal preferences, behaviors, demographics, or interactions with your brand. The goal of email personalization is to create a more engaging and relevant email experience for each recipient, which can lead to higher open rates, click-through rates, and conversions. See the following list of common ways you might personalize the email messaging:

   * Personalized greetings: Address the recipient by their first name in the email's salutation to make the email feel more personalized and less generic.
   * Product recommendations: Suggest products or services that are relevant to the recipient based on their past purchases.
   * Dynamic content: Use dynamic content blocks that can change based on recipient data, such as location, recent interactions, or purchase history.
   * Personalized content recommendations: Provide recommendations to specific information sources, such as blog posts, articles, or videos, based on the recipient's previous engagement with your content.
   * Location-based personalization: Customize content or promotions based on the recipient's geographic location or time zone.

In the send notification payload, add a `personalization` parameter to enable it. See the following examples for more details.

### Send notification payload example
{: #send-payload}

    ```
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

### Full template payload example
{: #full-payload}

    ```
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

When you create a template to enable personalization, add a placeholder in the HTML Handlebars format, for example: 

    ```
    {{ibmenreferer personalization ibmenmailto 'name'}}
    ```

The personalization tags are described in the following list:

   * `ibmenreferer`: Specifies where to enable the personalization. 
   * `personalization`: Specifies from where to select personalization values in the send notifications payload.
   * `ibmenmailto`: Iterate through an array of emails to which mapping can be done for personalization.
   * `name`: Specifies which value to select from a key. 

### Notification payload for Webhook and Slack notifications
{: #notification-payload-slack-webhook}

    ```
    {
        {{#equal data.alert_definition.severity "Critical"}}
                "severity": 1,
            {{/equal}}
        {{#equal data.alert_definition.severity "Info"}}
                "severity": 2,
            {{/equal}}
        {{#equal data.alert_definition.severity "Error"}}
                "severity": 2,
            {{/equal}}
        "console": "toc",
        "version": "1.0",
        "crn": {
            "version": "v1",
            "ctype": "public",
            "cname": "bluemix",
            "resource_type": "object",
            "resource": "event-notifications",
            "service_name": "event-notifications"
            },
        "alert_id": "{{data.alert_definition.id}}",
        "tribe_name": "Mobile",
        "disable_pager": "false",
        "source": "{{source}}",
        "tip_msg_type": "create.notice",
        "situation": "{{ibmendefaultshort}}",
        "customer_impacting": "false",
        "runbook_toc_enabled": "false",
        "short_description": "{{ibmendefaultshort}}",
        "product_ready_compliance": "true",
        "long_description": "{{data.alert_definition.description}}",
        "timestamp": "{{time}}",
        "alert_ui_url": "{{data.links.view_alert}}",
        "runbook_url": "{{data.alert_definition.meta_labels.runbook}}"
    }
    ```

### Slack notification template example
{: #slack-template}

    ```
    {
	"name": "Template for TIP",
	"params": {
        "body": "eyJibG9ja3MiOlt7InR5cGUiOiJzZWN0aW9uIiwidGV4dCI6eyJ0eXBlIjoibXJrZG93biIsInRleHQiOiJUaGlzIGlzIGEgbm90aWZ5aW5nIG1lc3NhZ2UuIn19LHsidHlwZSI6ImRpdmlkZXIiLCJ0ZXh0Ijp7InR5cGUiOiJtbmF2IiwidGV4dCI6IlRoaXMgaXMgYSBuZXcgbm90aWZ5aW5nIG1lc3NhZ2UuIiwiZW1vamkiOnRydWV9fV0seyJ0eXBlIjoiYWN0aW9ucyIsImVsZW1lbnRzIjpbeyJ0eXBlIjoicGxhaW5fdGV4dCIsInRleHQiOnsic2VsZWN0aW9yIjp7InR5cGUiOiJwbGFpbl90ZXh0IiwidGV4dCI6IlZpZXcgRGV0YWlscyIsImVtb2ppIjp0cnVlfX19XX0="
	},
	"type": "slack.notification"
    }
    ```

### Webhook notification template example
{: #webhook-template}

    ```
    {
	"name": "Template for TIP",
	"params": {
		"body": "ewogIHt7I2VxdWFsIGRhdGEuYWxlcnRfZGVmaW5pdGlvbi5zZXZlcml0eSAiQ3JpdGljYWwifX0KCQkic2V2ZXJpdHkiOiAxLAoJe3svZXF1YWx9fQogIHt7I2VxdWFsIGRhdGEuYWxlcnRfZGVmaW5pdGlvbi5zZXZlcml0eSAiSW5mbyJ9fQoJCSJzZXZlcml0eSI6IDIsCgl7ey9lcXVhbH19CiAge3sjZXF1YWwgZGF0YS5hbGVydF9kZWZpbml0aW9uLnNldmVyaXR5ICJFcnJvciJ9fQoJCSJzZXZlcml0eSI6IDIsCgl7ey9lcXVhbH19CiAgImNvbnNvbGUiOiAidG9jIiwKICAidmVyc2lvbiI6ICIxLjAiLAogICJjcm4iOiB7CiAgICAgICJ2ZXJzaW9uIjogInYxIiwKICAgICJjdHlwZSI6ICJwdWJsaWMiLAogICAgImNuYW1lIjogImJsdWVtaXgiLAogICAgInJlc291cmNlX3R5cGUiOiAib2JqZWN0IiwKICAgICJyZXNvdXJjZSI6ICJldmVudC1ub3RpZmljYXRpb25zIiwKICAgICJzZXJ2aWNlX25hbWUiOiAiZXZlbnQtbm90aWZpY2F0aW9ucyIKICAgIH0sCiAgImFsZXJ0X2lkIjogInt7ZGF0YS5hbGVydF9kZWZpbml0aW9uLmlkfX0iLAogICJ0cmliZV9uYW1lIjogIk1vYmlsZSIsCiAgImRpc2FibGVfcGFnZXIiOiAiZmFsc2UiLAogICJzb3VyY2UiOiAie3tzb3VyY2V9fSIsCiAgInRpcF9tc2dfdHlwZSI6ICJjcmVhdGUubm90aWNlIiwKICAic2l0dWF0aW9uIjogInt7aWJtZW5kZWZhdWx0c2hvcnR9fSIsCiAgImN1c3RvbWVyX2ltcGFjdGluZyI6ICJmYWxzZSIsCiAgInJ1bmJvb2tfdG9jX2VuYWJsZWQiOiAiZmFsc2UiLAogICJzaG9ydF9kZXNjcmlwdGlvbiI6ICJ7e2libWVuZGVmYXVsdHNob3J0fX0iLAogICJwcm9kdWN0X3JlYWR5X2NvbXBsaWFuY2UiOiAidHJ1ZSIsCiAgImxvbmdfZGVzY3JpcHRpb24iOiAie3tkYXRhLmFsZXJ0X2RlZmluaXRpb24uZGVzY3JpcHRpb259fSIsCiAgInRpbWVzdGFtcCI6ICJ7e3RpbWV9fSIsCiAgImFsZXJ0X3VpX3VybCI6ICJ7e2RhdGEubGlua3Mudmlld19hbGVydH19IiwKICAicnVuYm9va191cmwiOiAie3tkYXRhLmFsZXJ0X2RlZmluaXRpb24ubWV0YV9sYWJlbHMucnVuYm9va319Igp9"
	},
	"type": "webhook.notification"
    }
    ```
