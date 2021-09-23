---

copyright:
  years: 2021
lastupdated: "2021-08-24"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications

subcollection: _your-subcollection_

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

<!--Name your file `ha.md` and include it in the **Reference** nav group in your `toc` file.-->

# High availability and disaster recovery for {{site.data.keyword.en_short}}
{: #en-ha}


{{site.data.keyword.en_short}} service is a highly available, regional service that runs in multiple zones.

In each supported multizone region, every zone has its own {{site.data.keyword.Bluemix_notm}} Kubernetes service cluster with several worker nodes. Each worker node runs several instances of {{site.data.keyword.en_short}} service components. Each region is fronted by a global load balancer and a web application firewall.
{: shortdesc}

{{site.data.keyword.en_short}} service persists tenant data in highly available database. A single regional database is used to store data of all the {{site.data.keyword.en_short}} tenants in that particular region. The data is stored across multiple zones in each region. Data that is stored in {{site.data.keyword.en_short}} service is encrypted and persisted in a database cluster that is spread across availability zones. All databases connections use TLS/SSL encryption for data in transit.

{{site.data.keyword.en_short}} service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all the data might not be recovered. However, a location recovery is possible and data can be restored. 

For regional disaster recovery, it is recommended that you create and maintain backup instances in other regions. To synchronize a service instance in one region with an instance in a different region, use the APIs.

Review the [API documentation](/apidocs/event-notifications) and decide the data that you want backed up and restored, in an eventuality.

 Examples to start with:
|Entity   |Endpoint|Description|
|---------|--------|-----------|
|sources|/v1/instances/{instance_id}/sources|Your platform sources|
|topics| /v1/instances/{instance_id}/topics|All registered topics|
|rules| /v1/instances/{instance_id}/rules|All rules created on topics|
|destinations| /v1/instances/{instance_id}/destinations|All registered destinations|
|subscriptions| /v1/instances/{instance_id}/subscriptions|All the subscriptions|

For each of the data set that you need to back up and restore, use `GET` calls to get a copy of the data. And use the corresponding `PUT / POST API` to populate the new instance on a different region.


## Locations
{: #en-ha-locations}

For more information about service availability within regions and data centers, see [here](https://test.cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-regions-endpoints#en-regions).
