---

copyright:

  years: 2021, 2026
lastupdated: "2026-07-20"

keywords: event notifications, IBM Cloud

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.en_short}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

This tutorial walks you through the steps that you need to take before you create an {{site.data.keyword.en_full_notm}} service.
{: shortdesc}

{{site.data.keyword.en_short}} is a routing service that provides you with information about critical events that occur in your {{site.data.keyword.cloud}} account. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services and applications to human destinations, such as Email, SMS, and Push notifications, or to service destinations, such as Webhooks and cloud services.

## Create an {{site.data.keyword.cloud_notm}} account
{: #en-cloud-ac}
{: step}

If you don't have an {{site.data.keyword.cloud_notm}} account, [create one](https://{DomainName}/registration){: external}.

## Decide on a location
{: #en-decide-location}
{: step}

Decide on a location where your service will to be hosted. Currently, the following locations are supported:

* Dallas (us-south)
* London (eu-gb)
* Frankfurt (eu-de)
* Sydney (au-syd)
* Madrid (eu-es)
* Toronto (ca-tor)
* Tokyo (jp-tok)
* Osaka (jp-osa)
* Sao Paulo (br-sao)
* Montreal (ca-mon)
* Washington DC (us-east)
* Chennai (in-che)
* Mumbai (in-mum)

## Decide on a pricing plan
{: #en-decide-pricing-plans}
{: step}

Based on your business requirements, decide on a pricing plan. Currently, the following plans are available: Lite, and Standard.

- `Lite`: This plan gives you unlimited ingested events, 10 topics, two filters per topic, five destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks (including Slack, with a limit of 20 Slack messages), and 1000 notifications per push destination (cumulative per instance, including Android, iOS, Huawei devices, and Chrome, Firefox, Safari browsers; the instance is disabled once the limit is reached). Ten subscriptions are allowed, and a subscription can have a maximum of three email recipients.

   Custom Email and Custom SMS destinations are not supported by Lite Plan.
   {: note}

- `Standard`: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (that is, the source is not associated with any topic), the incoming events are dropped, and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

   You can use **Pre-production destination**, as a low-cost push destination, for your development and test environments. You can change the **Pre-production destination** to **Production destination** post completion of your development and testing. This feature is only available for `Standard` pricing plan.
   {: note}

Changing plans from a chargeable plan (Standard) to free plan (Lite) is not permitted as this may result in disruption and data loss due to the plan limitations.
{: important}

## Choose an event source
{: #en-decide-event-source}
{: step}

You can create either an `API Source` or an `{{site.data.keyword.cloud_notm}}` source. To learn more about the process of adding a source, see [Adding an Event Notifications source](/docs/event-notifications?topic=event-notifications-en-add-source).

An `API source` indicates that the Event originated outside of {{site.data.keyword.cloud_notm}} and is sent to {{site.data.keyword.en_short}} service through API calls.

An `{{site.data.keyword.cloud_notm}} source` indicates a service on {{site.data.keyword.cloud_notm}} that can emit events to {{site.data.keyword.en_short}} service.

The source `{{site.data.keyword.cloud_notm}} Resource Lifecycle Events` is a built-in source. This source emits resource lifecycle events to {{site.data.keyword.en_short}} service. This is disabled by default and must be enabled.

The other {{site.data.keyword.cloud_notm}} sources must be first integrated to start emitting events to {{site.data.keyword.en_short}} service.

For the full list of supported {{site.data.keyword.cloud_notm}} sources, see [Registering event sources](/docs/event-notifications?topic=event-notifications-en-source).

## Choose an event destination
{: #en-decide-event-destination}
{: step}

A destination is a delivery target for a notification. Two destination categories are supported:

- **Human destinations** are devices, servers, or applications that present notifications for human consumption.
- **Service destinations** are cloud services or applications where notifications are consumed programmatically.

For the full list of supported destinations, see [Working with event destinations](/docs/event-notifications?topic=event-notifications-en-destination).

To learn more about the process of creating a destination, see [Creating an Event Notifications destination](/docs/event-notifications?topic=event-notifications-en-create-en-destination).


## Route notifications to destinations
{: #en-getting-started-create-topic}
{: step}

Event routing connects your sources to your destinations through topics, filters, and subscriptions.

- A **topic** organizes incoming events from one or more sources. Each source is connected to a topic through a user-defined filter.
- **Filters** define which events from each source are routed to the topic.
- A **subscription** connects a topic to a destination, so that matching events are delivered to the right people or services.

You can set up the complete routing flow — topic, filters, subscriptions, and review — in a single guided experience.

To set up event routing, see [Route notifications to destinations](/docs/event-notifications?topic=event-notifications-en-create-en-topic).

After you save the routing configuration, notifications are delivered to the chosen destinations whenever a matching event occurs.


## Alternative: Use Terraform
{: #en-getting-started-terraform}

As an alternative to the console, you can provision and configure {{site.data.keyword.en_short}} instances by using [Terraform IBM Modules (TIM)](https://cloud.ibm.com/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-about-tim) for Infrastructure as Code (IaC) automation. The [TIM for {{site.data.keyword.en_short}}](https://registry.terraform.io/modules/terraform-ibm-modules/event-notifications/ibm/latest){: external} provides a standardized, tested, and enterprise-ready approach that follows {{site.data.keyword.cloud_notm}} security best practices.
