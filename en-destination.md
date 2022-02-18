---

copyright:
  years: 2020, 2022
lastupdated: "2022-02-18"

keywords: event-notifications, event notifications, about event notifications

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
​{: #en-destination-categories}

There are two destination categories : human and service.

### Human destinations
{: #en-destination-human}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported by the {{site.data.keyword.en_short}} service:
- {{site.data.keyword.Bluemix_notm}} email service
- {{site.data.keyword.Bluemix_notm}} push notification service
- {{site.data.keyword.Bluemix_notm}} SMS service

Both email and SMS destinations are provided out of the box, and are available whenever you create an instance of {{site.data.keyword.en_short}}. {{site.data.keyword.Bluemix_notm}} push notification service must be added manually and requires configuration.

### Service destinations
{: #en-destination-service}

Service destinations are cloud services or application where notifications are consumed programmatically. The following service destination is supported by the {{site.data.keyword.en_short}} service:

- Webhook: to a backend microservice.


