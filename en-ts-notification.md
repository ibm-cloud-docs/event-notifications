---

copyright:
  years: 2019, 2020
lastupdated: "2021 -10-11"

keywords: question about event notifications, notification, notifications

subcollection: event-notifications

content-type: troubleshoot

---


{{site.data.keyword.attribute-definition-list}}


# Why is notification absent 
{: #troubleshoot-notification-topic}
{: troubleshoot}
{: support}

Notification is not received at the destinations.
{: shortdesc}

Notification is not received at the destinations (for example: SMTP_IBM, SMS_IBM).
{: tsSymptoms}

The most common mistake would be that conditions (rules) written for the topic does not match with the incoming payload.
{: tsCauses}

If you are using static events (event type, event subtype and severity)
{: tsResolve}
- When both event type and event subtype are provided then type attribute of incoming payload must be a combination of the type and subtype filter. For example, if event type is `bluemix.certificate_manager` and event subtype is expiring_in_90_days then type attribute in the incoming payload would be `bluemix.certificate_manager:expiring_in_90_days`

  ```
  "type":"bluemix.certificate_manager:expiring_in_90_days"
  ```
  {: codeblock}

- when only event type is provided in the stated example then type attribute would be `bluemix.certificate_manager'.

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
  {: codeblock}

- Event type, event subtype and severity are termed as event conditions. Additionally, user can provide advanced conditions.

  Remember, if both event conditions and advanced conditions are provided, then both condition types need to be satisfied for a notification to be routed to a topic.
  {:note: .note}






