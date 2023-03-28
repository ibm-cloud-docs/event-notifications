---

copyright:
  years: 2021, 2023
lastupdated: "2023-03-28"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications, disaster recovery

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# High availability and disaster recovery for {{site.data.keyword.en_short}}
{: #en-ha}

{{site.data.keyword.en_short}} service is a highly available, regional service that runs in multiple zones.
{: shortdesc}

## Service High Availability (HA)
{: #en-service-ha}

An availability zone is a logically and physically isolated location within an {{site.data.keyword.cloud_notm}} region where your data is processed and hosted.

- An availability zone has independent power, cooling, and network infrastructures that are isolated from other zones to strengthen fault tolerance by avoiding single points of failure between zones.
- An availability zone offers high bandwidth and low inter-zone latency within a region.

A region (location) is a geographically and physically separate group of one or more availability zones with independent electrical and network infrastructures that are isolated from other regions.

- Regions are designed to remove shared single points of failure with other regions and provide low inter-zone latency within the region.
- Each region has three different data centers (DC) for redundancy.
- In each supported region, traffic is load balanced across infrastructure in multiple availability zones, with no single point of failure.
- If all the data centers in a region fail, {{site.data.keyword.appconfig_short}} becomes unavailable in that region.

In each supported multizone region, every zone has its own {{site.data.keyword.cloud_notm}} Kubernetes service cluster with several worker nodes. Each worker node runs several instances of {{site.data.keyword.en_short}} service components. Each region is fronted by a global load balancer and a web application firewall.

{{site.data.keyword.en_short}} service persists tenant data in a highly available database. A single regional database stores data of all the {{site.data.keyword.en_short}} tenants in that particular region. The data is stored across multiple zones in each region. Data that is stored in the {{site.data.keyword.en_short}} service is encrypted and persisted in a database cluster that is spread across availability zones. All databases connections use TLS/SSL encryption for data in transit.

## Availability zones for {{site.data.keyword.appconfig_short}}
{: #en-zones-ha}

The following table lists the high-availability (HA) status for the regions (locations) where the {{site.data.keyword.en_short}} service is available:

| Geography | Region | HA Status |
|:----------|:-------|:----------|
| Asia-Pacific | Sydney (au-syd) | MZR |
| Europe | London (eu-gb) | MZR |
| Europe | Frankfurt (eu-de) | MZR |
| North America | Dallas (us-south)| MZR |
{: caption="Table 1. HA status for the regions" caption-side="bottom"}

Where:

- A *geography* is a geographic area or larger political body that contains one or more regions.
- A *region* is a defined geographic territory.
   - A region might be a specific postal code area, a town, a city, a state, a group of states, or even a group of countries.
   - A region contains [multiple availability zones](https://www.ibm.com/cloud/data-centers/) to meet local access, low latency, and security requirements for the region.
- `MZR` means multi-zone region. [Learn more](/docs/overview?topic=overview-locations#mzr-table).

## Disaster recovery (DR) for {{site.data.keyword.appconfig_short}} service in a region
{: #en-dr}

{{site.data.keyword.en_short}} service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all the data might not be recovered. However, a location recovery is possible and data can be restored from that location.
{: important}

If an entire MZR becomes inoperative (usually due to a catastrophic disaster or failure), {{site.data.keyword.IBM_notm}} runs disaster-recovery plans to restore service within 24 hours or less. {{site.data.keyword.IBM_notm}} restores the service in an alternative MZR from an IBM-managed backup. Existing DNS names are migrated to the backup deployment. When the disaster recovery process is complete, API traffic resumes automatically.

When the primary MZR is restored, the secondary deployment is migrated back to the primary site. After the migration is complete, the DNS is restored to its original routing.

For regional disaster recovery, you must create and maintain backup instances in other regions. To synchronize a service instance in one region with an instance in a different region, use the APIs.

If you need zero downtime during a regional disaster recovery, create and maintain backup instances in other regions. Review the API documentation and decide the data that you want backed up and restored if there is a disaster. To synchronize a service instance in one region with an instance in a different region, you can use the APIs mentioned [here](/apidocs/event-notifications).

Some API examples are as follows:

|Entity   | Endpoint | Description |
|---------|--------|-----------|
| sources | `/v1/instances/{instance_id}/sources` | Your platform sources |
| topics | `/v1/instances/{instance_id}/topics` | All registered topics |
| rules | `/v1/instances/{instance_id}/rules` | All rules created on topics |
| destinations | `/v1/instances/{instance_id}/destinations` | All registered destinations |
| subscriptions | `/v1/instances/{instance_id}/subscriptions` | All the subscriptions |
{: caption="Table 2. Example API endpoints" caption-side="top"}

For each data set that you need to back up and restore, use `GET` calls to get a copy of the data. And use the corresponding `PUT / POST API` to populate the new instance on a different region.

