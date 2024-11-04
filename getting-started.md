---

copyright:
  years: 2021, 2024
lastupdated: "2024-03-20"

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

{{site.data.keyword.en_short}} is a routing service that provides you about critical events that occur in your {{site.data.keyword.cloud}} account. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.compliance_short}}, {{site.data.keyword.secrets-manager_short}}, {{site.data.keyword.cloud_notm}} Projects, and Toolchain to communication channels like email, SMS, push notifications, Huawei Cloud Push, webhook, slack, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.cos_full_notm}}.

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
* Madrid (eu-es)

## Decide on a pricing plan
{: #en-decide-pricing-plans}
{: step}

Based on your business requirements, decide on a pricing plan. Currently, the following plans are available: Lite, and Standard.

- `Lite`: This plan gives you unlimited ingested events, 10 topics, 2 filters per topic, 5 destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks, and 1000 notifications per push destination. 10 subscriptions are allowed, and a subscription can have a maximum of 3 email recipients.

- `Standard`: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (that is, the source is not associated with any topic), the incoming events are dropped, and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

   You can use **Pre-production destination**, as low-cost push destination, for your development and test environments. You can change the **Pre-production destination** to **Production destination** post completion of your development and testing. This feature is only available for `Standard` pricing plan.
   {: note}

Changing plans from a chargeable plan (Standard) to free plan (Lite) is not permitted as this may result in disruption and data loss due to the plan limitations.
{: important}

## Choose an event source
{: #en-decide-event-source}
{: step}

You can create either an `API Source` or an `{{site.data.keyword.cloud_notm}}` source.

An `API source` indicates that the Event originated outside of {{site.data.keyword.cloud_notm}} and is sent to {{site.data.keyword.en_short}} service through API calls.

An `{{site.data.keyword.cloud_notm}} source` indicates a service on {{site.data.keyword.cloud_notm}} that can emit events to {{site.data.keyword.en_short}} service.

The source `{{site.data.keyword.cloud_notm}} Resource Lifecycle Events` is a built-in source.  This source emits resource lifecycle events to {{site.data.keyword.en_short}} service. This is disabled by default and needs to be enabled.

The other {{site.data.keyword.cloud_notm}} sources have to be first integrated from the respectice services to start emitting events to {{site.data.keyword.en_short}} service.

The list of IBM provided sources is as follows:
- [{{site.data.keyword.monitoringfull_notm}}](https://{DomainName}/docs/monitoring?topic=monitoring-eventnotif){: external}
- [Security and Compliance](https://{DomainName}/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui){: external}
- [{{site.data.keyword.secrets-manager_short}}](https://{DomainName}/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui){: external}
- [{{site.data.keyword.appconfig_short}}](https://{DomainName}/docs/app-configuration?topic=app-configuration-ac-int-en){: external}
- [IBM Cloud Projects](https://{DomainName}/docs/secure-enterprise?topic=secure-enterprise-event-notifications-events&interface=ui){: external}
- [Toolchain](https://{DomainName}/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd&interface=ui){: external}
- [watsonx.data](https://{DomainName}/docs/watsonxdata?topic=watsonxdata-event-notifications-events){: external}
- [OpenPages](https://{DomainName}/docs/openpages?topic=openpages-event-notifications-events){: external}


## Choose an event destination
{: #en-decide-event-destination}
{: step}

A destination is a delivery target for a notification. Two destination categories are supported: human and service.

### Human destinations
{: #en-destination-human}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported:

- [Email Destinations](/docs/event-notifications?topic=event-notifications-en-destinations-email)
   - [Inbuilt Email](/docs/event-notifications?topic=event-notifications-en-destination-email-destination-default)
   - [IBM Cloud Email service with custom domain](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email)
- [Inbuilt SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
- [Custom SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms-custom)
- [Microsoft&reg; Teams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams)
- [PagerDuty](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty)
- [Push notifications](/docs/event-notifications?topic=event-notifications-en-destinations-push)
   - [Android Push Notifications (FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
   - [iOS Push Notifications (APNs)](/docs/event-notifications?topic=event-notifications-en-push-apns)
   - [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
   - [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
   - [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)
   - [Huawei Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-huawei)
- [Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack)
- [ServiceNow](/docs/event-notifications?topic=event-notifications-en-destinations-servicenow)

### Service destinations
{: #en-destination-service}

Service destinations are cloud services or applications where notifications are consumed programmatically. The following service destinations are supported:

- [Webhook](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
- [{{site.data.keyword.codeengineshort}}](/docs/event-notifications?topic=event-notifications-en-destinations-codeengine)
- [{{site.data.keyword.cos_full_notm}}](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-object-storage)
