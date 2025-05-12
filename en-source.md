---

copyright:
  years: 2020, 2025
lastupdated: "2025-05-12"

keywords: event-notifications, event notifications, about event notifications

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Registering event sources
{: #en-source}

An event source is a service or application on {{site.data.keyword.cloud_notm}} that emits event notifications and publishes them to a topic within the {{site.data.keyword.en_short}} service. A source is a registered entity in an {{site.data.keyword.en_short}} service instance. A source can be registered to an {{site.data.keyword.en_short}} service instance either as an `{{site.data.keyword.cloud_notm}} source` or an `API source` or an `{{site.data.keyword.cloud_notm}} platform source`.
{: shortdesc}

A source can publish to multiple topics. In other contexts sources are identified as producers or publishers.

From a billing perspective, ingested notifications are calculated for all incoming events. If a user has disabled a source or if the source is not connected to a topic, the user is not billed for the events from the {{site.data.keyword.cloud_notm}} source. However, if the source is **Enabled**, and a topic is connected to it, the ingested events include all incoming events (not only the events that are filtered in the topic).
{: important}

## {{site.data.keyword.cloud_notm}} sources
{: #en-ibm-sources-list}

The list of IBM provided sources is as follows:
- [{{site.data.keyword.logs_full_notm}}](https://{DomainName}/docs/cloud-logs?topic=cloud-logs-event-notifications-configure){: external}
- [{{site.data.keyword.monitoringfull_notm}}](https://{DomainName}/docs/monitoring?topic=monitoring-eventnotif){: external}
- [Security and Compliance](https://{DomainName}/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui){: external}
- [{{site.data.keyword.secrets-manager_short}}](https://{DomainName}/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui){: external}
- [{{site.data.keyword.appconfig_short}}](https://{DomainName}/docs/app-configuration?topic=app-configuration-ac-int-en){: external}
- [IBM Cloud Projects](https://{DomainName}/docs/secure-enterprise?topic=secure-enterprise-event-notifications-events&interface=ui){: external}
- [Toolchain](https://{DomainName}/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd&interface=ui){: external}
- [watsonx.data](https://{DomainName}/docs/watsonxdata?topic=watsonxdata-event-notifications-events){: external}
- [OpenPages](https://{DomainName}/docs/openpages?topic=openpages-event-notifications-events){: external}
- [IBM Cloud Backup for VPC ](/docs/vpc?topic=vpc-event-notifications-events){: external}

## API sources
{: #en-api-sources}

You can send custom events from your backend application to the {{site.data.keyword.en_short}} service by using API sources. To do this, you need to add an `API source` first.

To add an {{site.data.keyword.cloud_notm}} source or an API source, complete the steps that are provided in the [Add an {{site.data.keyword.en_short}} source tutorial](/docs/event-notifications?topic=event-notifications-en-add-source)

## {{site.data.keyword.cloud_notm}} platform sources
{: #en-ibm-cloud-platform-sources}

- [{{site.data.keyword.cloud_notm}} Platform Notifications](https://{DomainName}/docs/account?topic=account-add-users-distribution-list#event-notifications-distribution-list){: external}
- [{{site.data.keyword.cloud_notm}} Resource lifecycle events](https://{DomainName}/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events)

## Periodic Timer Source
{: #periodic-timer-source}

This is a built in source that is used to schedule events based on a user defined time period. To know more about the source and using , refer [here](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer).
