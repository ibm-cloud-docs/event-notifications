---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-24"

keywords: event notifications, IBM Cloud

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.en_short}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

This tutorial brings you through the steps that you need to take before you create an {{site.data.keyword.en_full_notm}} service.
{: shortdesc}

{{site.data.keyword.en_short}} is a routing service that tells you about critical events that occur in your {{site.data.keyword.Bluemix_notm}} account. You can filter and route event notifications from {{site.data.keyword.Bluemix_notm}} services like Monitoring, Security and Compliance Center, and Secrets Manager to communication channels like email, SMS, push notifications, and webhooks.

## Create a cloud account
{: #en-cloud-ac}
{: step}

You need an {{site.data.keyword.cloud}} account. If you don't have one, [Create an IBM Cloud account](https://cloud.ibm.com/registration/).

## Decide on a location
{: #en-decide-location}
{: step}

Decide on a location where your service will be hosted. Currently, the following locations are supported:

* Dallas (us-south)
* London (eu-gb)
* Sydney (au-syd)
* Frankfurt (eu-de)

## Decide on a pricing plan
{: #en-decide-pricing-plans}
{: step}

Based on your business requirements, decide on a pricing plan. Currently, the following plans are available: Lite, and Standard.

* `Lite`: This plan gives you unlimited ingested events, 10 topics, 2 filters per topic, 5 destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks, and 1000 notifications per push destination. Ten subscriptions are allowed, and a subscription can have a maximum of three email recipients.
* `Standard`: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (that is, the source is not associated with any topic), the incoming events are dropped, and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

## Choose an event source
{: #en-decide-event-source}
{: step}

You can create either an `API Source` or an `IBM Managed source`.

An `API source` indicates that the Event originated outside of the IBM Cloud and is sent to {{site.data.keyword.en_short}} service through API calls.

An `IBM managed source` indicates a service on {{site.data.keyword.Bluemix_notm}} that can emit events to {{site.data.keyword.en_short}} service.

The list of IBM provided sources is as follows:
- [IBM Cloud Monitoring](https://cloud.ibm.com/docs/monitoring?topic=monitoring-notifications)
- [IBM Cloud Security and Compliance Center](https://cloud.ibm.com/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui)
- [IBM Cloud Secrets Manager](https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui)

## Choose an event destination
{: #en-decide-event-destination}
{: step}

A destination is a delivery target for a notification. Two destination categories are supported: human and service.

### Human destinations
{: #en-destination-human}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported:

- [{{site.data.keyword.Bluemix_notm}} email service](docs/event-notifications?topic=event-notifications-en-destinations-email)
- [{{site.data.keyword.Bluemix_notm}} push notification service](/docs/event-notifications?topic=event-notifications-en-destinations-push)
- [{{site.data.keyword.Bluemix_notm}} SMS service](/docs/event-notifications?topic=event-notifications-en-destinations-sms)

### Service destinations
{: #en-destination-service}

Service destinations are cloud services or applications where notifications are consumed programmatically. The following service destination is supported:

- [Webhook: to a backend microservice](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
