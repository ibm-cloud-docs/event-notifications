---

copyright:
  years: 2015, 2022
lastupdated: "2020-02-07"

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

{Create an {{site.data.keyword.en_short}} topic. Topics are based on a publish and subscription model. You can send notifications or alerts to multiple destination types, (for example, email, SMS, and others that are subscribed to a particular topic. Configure topics as needed and {{site.data.keyword.en_short}} handles the routing and delivering of alerts reliably to the right destinations.
{: shortdesc}

- Each topic is created under a registered source.
- Each topic can have its own set of rules, which routes the incoming payload to the respective topic.


## Select topics in the {{site.data.keyword.en_short}} console
{: #en-select-topics}
{: step}

Select topics in the {{site.data.keyword.en_short}} console.

![Create a topic](images/en-topic1.png "Topic"){: caption="Figure 1. Create a topic" caption-side="bottom"}


Click  `Create`, and enter the following topic details:
- Name: enter a name for the topic.
- Description: add an optional description for the topic.
- Source: select a source from the dropdown list.

![Add topic details](images/en-topic2.png "Topic"){: caption="Figure 2. Add topic details" caption-side="bottom"}

## Add rules to your topic
{: #en-topic-rules}
{: step}

Step 1 created a topic, step 2 provisions optional custom rules for the topic.
{: note}

Add the following rules to your topic:

- Event type: select event type from the dropdown list.
- Event sub type: select event sub type from the event sub type dropdown list.
- Severity: select severity from the severity dropdown list.
- Advanced conditions: write your own custom conditions, which follow [jsonpath specifications](https://jsonpath.com/).

![Add rules](images/en-topic3.png "Rules"){: caption="Figure 3. Add rules to topic" caption-side="bottom"}

## Finish adding rules to your topic
{: #en-topic-condition}
{: step}

Click `Add a condition`.

If you do not select any rules, a default rule gets added, which means all notifications route to the topic by default.
{: note}

![Add condition](images/en-topic4.png "Condition"){: caption="Figure 4. Add a condition" caption-side="bottom"}

## Create a topic
{: #en-topic-create}
{: step}

Click `Create` in the topic wizard.

![Click Create to finish](images/en-topic5.png "Create"){: caption="Figure 5. Finish creating a topic" caption-side="bottom"}
