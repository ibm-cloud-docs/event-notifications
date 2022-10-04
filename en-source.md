---

copyright:
  years: 2020, 2022
lastupdated: "2022-09-30"

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

# Event sources
{: #en-source}

An event source is a service or application on {{site.data.keyword.cloud_notm}} that emits event notifications and publishes them to a topic within the {{site.data.keyword.en_short}} service. A source is a registered entity in an {{site.data.keyword.en_short}} service instance. A source can be registered to an {{site.data.keyword.en_short}} service instance either as an `IBM managed source` or an `API source`.
{: shortdesc}

A source can publish to multiple topics. In other contexts sources are identified as producers or publishers.

From a billing perspective, ingested notifications is calculated for all incoming events. If a user has disabled a source or if the source is not connected to a topic, the user is not billed for the events from the {{site.data.keyword.cloud_notm}} source. However, if the source is **Enabled**, and a topic is connected to it, the ingested events will include all incoming events (not only the events filtered in the topic).
{: important}

## {{site.data.keyword.cloud_notm}} sources
{: #en-ibm-sources-list}

The list of IBM provided sources is as follows:
- [{{site.data.keyword.monitoringfull_notm}}](https://{DomainName}/docs/monitoring?topic=monitoring-notifications){: external}
- [{{site.data.keyword.cloud_notm}} Platform Notifications](https://{DomainName}/docs/account?topic=account-add-users-distribution-list#event-notifications-distribution-list){: external}
- [{{site.data.keyword.secrets-manager_full_notm}}](https://{DomainName}/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui){: external}
- [{{site.data.keyword.compliance_long}}](https://{DomainName}/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui){: external}

## API sources
{: #en-api-sources}

You can send custom events from your backend application to the {{site.data.keyword.en_short}} service using API sources. To do this, you need to add an `API source` first.

To add an IBM managed source or an API source, complete the steps provided in the [Add an Event Notifications source tutorial](/docs/event-notifications?topic=event-notifications-en-add-source)

## {{site.data.keyword.cloud_notm}} platform sources
{: #en-ibm-cloud-platform-sources}

- [{{site.data.keyword.cloud_notm}} Resource lifecycle events](/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events)
