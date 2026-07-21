---

copyright:
  years: 2020, 2026
lastupdated: "2026-07-20"

keywords: event-notifications, event notifications, about event notifications

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Registering event sources
{: #en-source}

An event source is a service or application on {{site.data.keyword.cloud_notm}} that emits event notifications and publishes them to a topic within the {{site.data.keyword.en_short}} service. A source is a registered entity in an {{site.data.keyword.en_short}} service instance. A source can be registered to an {{site.data.keyword.en_short}} service instance either as an `{{site.data.keyword.cloud_notm}} source`, an `API source`, or an `{{site.data.keyword.cloud_notm}} platform source`.
{: shortdesc}

A source can publish to multiple topics. In other contexts, sources are identified as producers or publishers.

From a billing perspective, ingested notifications are calculated for all incoming events. If a user has disabled a source or if the source is not connected to a topic, the user is not billed for the events from the {{site.data.keyword.cloud_notm}} source. However, if the source is **Enabled**, and a topic is connected to it, the ingested events include all incoming events (not only the events that are filtered in the topic).
{: important}

## {{site.data.keyword.cloud_notm}} sources
{: #en-ibm-sources-list}

The following IBM-provided sources are available:

- [Cloud Monitoring](/docs/monitoring?topic=monitoring-eventnotif)
- [Security and Compliance](/docs/workload-protection?topic=workload-protection-getting-started)
- [Cloud Logs](/docs/cloud-logs?topic=cloud-logs-event-notifications-configure)
- [Cloud Projects](/docs/secure-enterprise?topic=secure-enterprise-event-notifications-events&interface=ui)
- [Secrets Manager](/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui)
- [Toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd&interface=ui)
- [App Configuration](/docs/app-configuration?topic=app-configuration-ac-int-en)
- [watsonx.data](/docs/watsonxdata?topic=watsonxdata-event-notifications-events)
- [OpenPages](/docs/openpages?topic=openpages-event-notifications-events)
- [IBM Cloud Backup for VPC](/docs/vpc?topic=vpc-event-notifications-events)
- [Storage Ceph as a Service](/docs/cephaas?topic=cephaas-event-notifications-events)

## API sources
{: #en-api-sources}

You can send custom events from your backend application to the {{site.data.keyword.en_short}} service by using API sources. To do this, you must first add an `API source`.

To add an {{site.data.keyword.cloud_notm}} source or an API source, complete the steps that are provided in the [Add an {{site.data.keyword.en_short}} source tutorial](/docs/event-notifications?topic=event-notifications-en-add-source)

## {{site.data.keyword.cloud_notm}} platform sources
{: #en-ibm-cloud-platform-sources}

- [{{site.data.keyword.cloud_notm}} Platform Notifications](/docs/support?topic=support-add-users-distribution-list#event-notifications-distribution-list)
- [{{site.data.keyword.cloud_notm}} Resource lifecycle events](/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events)

## Periodic Timer Source
{: #periodic-timer-source}

The Periodic Timer is a built-in source that schedules events based on a user-defined time period. For more information, see [Periodic Timer](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer).
