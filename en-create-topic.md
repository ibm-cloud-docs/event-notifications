---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-05"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} topic
{: #en-create-en-topic}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Create an {{site.data.keyword.en_short}} topic. Topics are based on a publish and subscription model. You can send notifications or alerts to multiple destination types, (for example, email, SMS, and others that are subscribed to a particular topic. Configure topics as needed and {{site.data.keyword.en_short}} handles the routing and delivering of alerts reliably to the right destinations.
{: shortdesc}

- Each topic is created under a registered source.
- Each topic can have its own set of rules, which routes the incoming payload to the respective topic.

## Select topics in the {{site.data.keyword.en_short}} console
{: #en-select-topics}
{: step}

Select `Topics` in the {{site.data.keyword.en_short}} console.

Click `Create`, and enter the following topic details:
- `Name`: enter a name for the topic.
- `Description`: add an optional description for the topic.
- `Source`: select a source from the dropdown list.

## Add rules to your topic
{: #en-topic-rules}
{: step}

Step 1 created a topic, step 2 provisions optional custom rules for the topic.
{: note}

Add the following rules to your topic:

- `Event type`: select event type from the dropdown list.
- `Event subtype`: select event sub type from the event sub type dropdown list.
- `Severity`: select severity from the severity dropdown list.
- `Advanced conditions`: create your own custom conditions, which must follow [jsonpath specifications](https://github.com/spyzhov/ajson). In the given link, there are many operators support is provided but currently we are only providing support for `==` operator. Example:

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

Based on the above input json following valid JSONPaths can be constructed:

```bash
1. $.data.severity=='LOW' 
Output: True

2. $.data.findings[1].severity == 'HIGH'
Output: True
```
{: codeblock}

## Finish adding rules to your topic
{: #en-topic-condition}
{: step}

Click `Add a condition`.

If you do not select any rules, a default rule is added, which means all notifications route to the topic by default.
{: note}

## Create a topic
{: #en-topic-create}
{: step}

Click `Create` in the topic wizard.
