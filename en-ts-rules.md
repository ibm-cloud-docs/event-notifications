---

copyright:
  years: 2019, 2022
lastupdated: "2022-02-09"

keywords: question about event notifications, rules, topic

subcollection: event-notifications

content-type: troubleshoot

---


{{site.data.keyword.attribute-definition-list}}


# Why can't I write rules for the topic?
{: #troubleshoot-rules-topic}
{: troubleshoot}
{: support}

The section to add conditions (rules) for the topic is not visible.
{: shortdesc}

When you create a topic, you cannot see the section to add conditions (rules) for the topic.
You see a message, 'No sources available to configure conditions'.
{: tsSymptoms}

![Unable to create rules](images/en-ts-rules.png "Unable to add conditions for the topic"){: caption="Figure 1. Unable to add conditions for the topic" caption-side="bottom"}

Either of the following issues might cause this error message:

- {{site.data.keyword.en_short}} service is not integrated with IBM Managed Service (for example: {{site.data.keyword.compliance_short}}).
- {{site.data.keyword.en_short}} service is integrated with IBM Managed service but source service is not added and authorized.
{: tsCauses}

Provide service-to-service authorization between the IBM Managed service and {{site.data.keyword.en_short}}.
Integrate {{site.data.keyword.en_short}} service with IBM Managed service, which registers IBM Managed service (for example, {{site.data.keyword.compliance_short}}) as source with {{site.data.keyword.en_short}} service instance.
{: tsResolve}

![Add conditions](images/en-ts-rules2.png "Add conditions for the topic"){: caption="Figure 2.  Add conditions for the topic)" caption-side="bottom"}

When the source is registered with {{site.data.keyword.en_short}} service, you can add conditions (rules) to the topic.