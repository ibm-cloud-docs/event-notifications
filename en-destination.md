---

copyright:
  years: 2020, 2022
lastupdated: "2022-07-05"

keywords: event-notifications, event notifications, about event notifications, destinations, event destination

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}

# Event destinations
{: #en-destination}

A destination is a delivery target for a notification. In other contexts, destinations are also called channels, sinks, or consumers.
{: shortdesc}

## Destination categories
{: #en-destination-categories}

There are two destination categories: human and service.

### Human destinations
{: #en-destination-human-1}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported by the {{site.data.keyword.en_short}} service:
- [{{site.data.keyword.cloud_notm}} email service](/docs/event-notifications?topic=event-notifications-en-destinations-email)
- [{{site.data.keyword.cloud_notm}} push notification service](/docs/event-notifications?topic=event-notifications-en-destinations-push)
- [{{site.data.keyword.cloud_notm}} SMS service](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
- [{{site.data.keyword.cloud_notm}} Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack)
- [Microsoft Teams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams)

Both email and SMS destinations are provided out of the box, and are available whenever you create an instance of {{site.data.keyword.en_short}}. {{site.data.keyword.cloud_notm}} push notification service must be added manually and requires configuration.

### Service destinations
{: #en-destination-service-1}

Service destinations are cloud services or application where notifications are consumed programmatically. The following service destination is supported by the {{site.data.keyword.en_short}} service:

- [Webhook: to a backend microservice](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
