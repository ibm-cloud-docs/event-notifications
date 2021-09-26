---

copyright:
  years: 2019, 2020
lastupdated: "2020-11-26"

keywords: question about event notifications, notification, notifications

subcollection: event-notifications

content-type: troubleshoot

---


{{site.data.keyword.attribute-definition-list}}


# Why is notification absent 
{: #troubleshoot-rules-topic}
{: troubleshoot}
{: support}

Section to add conditions (rules) for the topic are not visible.
{: shortdesc}

Notification is not received by the required destinations (eg: SMTP_IBM, SMS_IBM).
{: tsSymptoms}

The most common mistake would be that conditions (rules) written for the topic does not match with the incoming payload.
{: tsCauses}

If you are using static events (event type, event subtype and severity)

- When both event type and event subtype are provided then type attribute of incoming payload should be a combination of the type and subtype filter. For example, if event type is `bluemix.certificate_manager` and event sub-type is expiring_in_90_days then type attribute in the incoming payload would be `bluemix.certificate_manager:expiring_in_90_days`

```
"type":"bluemix.certificate_manager:expiring_in_90_days"
```
{: codeblock}

- when only event type is provided in the above example then type attribute would be `bluemix.certificate_manager'.

```
"type":"bluemix.certificate_manager:expiring_in_90_days"
```
{: codeblock}

- when event type, event subtype and severity are provided, where event type is `bluemix.certificate_manager`, event subtype is `expiring_in_90_days` and severity is LOW then type would be
`bluemix.certificate_manager:expiring_in_90_days` and severity would be LOW.

```
"type":"bluemix.certificate_manager:expiring_in_90_days",
"severity": "LOW"
```

Event type, event subtype and severity are  termed as event conditions. User can additionally provide advanced conditions. Just remember, if both event conditions and advanced conditions are provided, then both condition types need to be satisfied for a notification to be routed to a topic.
{: codeblock}
{: tsResolve}

![Add conditions](images/en-ts-rules2.png " Add conditions for the topic){: caption="Figure 2.  Add conditions for the topic)" caption-side="bottom"}

