---

copyright:
  years: 2021, 2022
lastupdated: "2022-10-28"

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

This tutorial brings you through the steps that you need to take before you create an {{site.data.keyword.en_full_notm}} service.
{: shortdesc}

{{site.data.keyword.en_short}} is a routing service that provides you about critical events that occur in your {{site.data.keyword.cloud}} account. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like Monitoring, Security and Compliance Center, and Secrets Manager to communication channels like email, SMS, push notifications, webhook, slack, Microsoft&reg; Teams, and {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}.

## Create an {{site.data.keyword.cloud_notm}} account
{: #en-cloud-ac}
{: step}

If you don't have an {{site.data.keyword.cloud_notm}} account, [create one](https://{DomainName}/registration){: external}.

## Decide on a location
{: #en-decide-location}
{: step}

Decide on a location where your service to be hosted. Currently, the following locations are supported:

* Dallas (us-south)
* London (eu-gb)
* Frankfurt (eu-de)
* Sydney (au-syd)

## Decide on a pricing plan
{: #en-decide-pricing-plans}
{: step}

Based on your business requirements, decide on a pricing plan. Currently, the following plans are available: Lite, and Standard.

- `Lite`: This plan gives you unlimited ingested events, 10 topics, 2 filters per topic, 5 destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks, and 1000 notifications per push destination. Ten subscriptions are allowed, and a subscription can have a maximum of three email recipients.

- `Standard`: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (that is, the source is not associated with any topic), the incoming events are dropped, and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

   You can use **Pre-production destination**, as low-cost push destination, for your development and test environments. You can change the **Pre-production destination** to **Production destination** post completion of your development and testing. This feature is only available for `Standard` pricing plan.
   {: note}

## Choose an event source
{: #en-decide-event-source}
{: step}

You can create either an `API Source` or an `{{site.data.keyword.cloud_notm}}`.

An `API source` indicates that the Event originated outside of {{site.data.keyword.cloud_notm}} and is sent to {{site.data.keyword.en_short}} service through API calls.

An `{{site.data.keyword.cloud_notm}}` indicates a service on {{site.data.keyword.cloud_notm}} that can emit events to {{site.data.keyword.en_short}} service.

`{{site.data.keyword.cloud_notm}} platform sources` indicates a {{site.data.keyword.cloud_notm}} resource that emits resource lifecycle events around the {{site.data.keyword.cloud_notm}} resources.

The list of IBM provided sources is as follows:
- [IBM Cloud Monitoring](/docs/monitoring?topic=monitoring-notifications)
- [IBM Cloud Security and Compliance Center](/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui)
- [IBM Cloud Secrets Manager](/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui)

## Choose an event destination
{: #en-decide-event-destination}
{: step}

A destination is a delivery target for a notification. Two destination categories are supported: human and service.

### Human destinations
{: #en-destination-human}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported:

- [{{site.data.keyword.cloud_notm}} Email](/docs/event-notifications?topic=event-notifications-en-destinations-email)
- [Push notifications](/docs/event-notifications?topic=event-notifications-en-destinations-push)
   - [Android Push Notifications (FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
   - [iOS Push Notifications (APNs)](/docs/event-notifications?topic=event-notifications-en-push-apns)
   - [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
   - [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
   - [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)
- [{{site.data.keyword.cloud_notm}} SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
- [Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack)
- [Microsoft&reg; Teams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams)

### Service destinations
{: #en-destination-service}

Service destinations are cloud services or applications where notifications are consumed programmatically. The following service destinations are supported:

- [Webhook](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
- [{{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-functions)
