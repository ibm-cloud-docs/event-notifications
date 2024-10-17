---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} topic
{: #en-create-en-topic}

You can send notifications or alerts to multiple destination types, for example, email, SMS, and others that are subscribed to a particular topic. Configure topics as needed and {{site.data.keyword.en_short}} handles the routing and delivering of alerts reliably to the correct destinations.
{: shortdesc}

1. Select **Topics** in the {{site.data.keyword.en_short}} console.

1. Click **Create**, and enter the following topic details:
   - **Name**: enter a name for the topic.
   - **Description**: add an optional description for the topic.
   - **Source**: select a source from the list.

    Step 1 created a topic, step 2 provisions optional custom rules for the topic.
    {: note}

1. Add the following rules to your topic:

   - **Event type**: select event type from the list.
   - **Event subtype**: select event sub type from the event sub type list.
   - **Severity**: select severity from the severity list.
   - **Advanced conditions**: create your own custom conditions, which must follow [JSONpath specifications](https://goessner.net/articles/JsonPath/). The correctly written rule will extract the appropriate data from the incoming request payload. {{site.data.keyword.en_short}} supports the == operator for JSONPath evaluation. You can validate your JSONPath [here](https://jsonpath.com/).

      Example:

      ```JSON
      {
         "data": {
            "findings": [
               {
                  "severity": "LOW",
                  "provider": "cert-mgr"
               },
               {
                  "severity": "HIGH",
                  "provider": "secrets-mgr"
               }
            ],
            "severity": "LOW",
            "payloadType": "findings",
            "issuer": "IBM Cloud Security Advisor",
         }
      }
      ```

      Based on the previous JSON input, the following valid JSONPaths can be constructed:

      ```bash
      1. $.data.severity=='LOW'
      Output: True

      2. $.data.findings[1].severity == 'HIGH'
      Output: True
      ```
      {: codeblock}

1. Click **Add a condition**.

    If you do not select any rules, a default rule is added, which means all notifications route to the topic by default.
    {: note}

1. Click **Create** in the topic wizard.
