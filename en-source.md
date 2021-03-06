---

copyright:
  years: 2020, 2022
lastupdated: "2022-07-05"

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

## IBM managed sources
{: #en-ibm-sources-list}

The list of IBM provided sources is as follows:
- [IBM Cloud Monitoring](https://cloud.ibm.com/docs/monitoring?topic=monitoring-notifications)
- [IBM Cloud Security and Compliance Center](https://cloud.ibm.com/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui)
- [IBM Cloud Secrets Manager](https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui)

## API sources
{: #en-api-sources}

You can send custom events from your backend application to the {{site.data.keyword.en_short}} service using API sources. To do this, you need to add an `API source` first.

To add an IBM managed source or an API source, complete the steps provided in the [Add an Event Notifications source tutorial](/docs/event-notifications?topic=event-notifications-en-add-source)
