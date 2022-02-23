---

copyright:
  years: 2021, 2022
lastupdated: "2022-02-09"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications

subcollection: event-notifications

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:term: .term}


# High availability and disaster recovery for {{site.data.keyword.en_short}}
{: #en-ha}


{{site.data.keyword.en_short}} service is a highly available, regional service that runs in multiple zones.

In each supported multizone region, every zone has its own {{site.data.keyword.Bluemix_notm}} Kubernetes service cluster with several worker nodes. Each worker node runs several instances of {{site.data.keyword.en_short}} service components. Each region is fronted by a global load balancer and a web application firewall.
{: shortdesc}

{{site.data.keyword.en_short}} service persists tenant data in a highly available database. A single regional database stores data of all the {{site.data.keyword.en_short}} tenants in that particular region. The data is stored across multiple zones in each region. Data that is stored in the {{site.data.keyword.en_short}} service is encrypted and persisted in a database cluster that is spread across availability zones. All databases connections use TLS/SSL encryption for data in transit.

{{site.data.keyword.en_short}} service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all the data might not be recovered. However, a location recovery is possible and data can be restored from that location. 

For regional disaster recovery, you must create and maintain backup instances in other regions. To synchronize a service instance in one region with an instance in a different region, use the APIs.

Review the API documentation and decide the data that you want backed up and restored if there is a disaster. For more information, see [{{site.data.keyword.en_short}} API](/apidocs/event-notifications).

Some API examples are as follows:

|Entity   |Endpoint|Description|
|---------|--------|-----------|
|sources|/v1/instances/{instance_id}/sources|Your platform sources|
|topics| /v1/instances/{instance_id}/topics|All registered topics|
|rules| /v1/instances/{instance_id}/rules|All rules created on topics|
|destinations| /v1/instances/{instance_id}/destinations|All registered destinations|
|subscriptions| /v1/instances/{instance_id}/subscriptions|All the subscriptions|
{: caption="Table 1. Example API endpoints" caption-side="top"}

For each data set that you need to back up and restore, use `GET` calls to get a copy of the data. And use the corresponding `PUT / POST API` to populate the new instance on a different region.


## Locations
{: #en-ha-locations}

For more information about service availability within regions and data centers, see [Regions and endpoints](/docs/event-notifications?topic=event-notifications-en-regions-endpoints#en-regions).
