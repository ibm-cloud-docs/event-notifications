---

copyright:
  years: 2021, 2025
lastupdated: "2025-04-11"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications, disaster recovery

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# {{site.data.keyword.en_short}} high availability and disaster recovery
{: #en-high-availability}

[High availability](#x2284708){: term} (HA) is a core discipline in an IT infrastructure to keep your apps up and running, even after a partial or full site failure. The main purpose of high availability is to eliminate potential points of failures in an IT infrastructure.
{: shortdesc}

IBM Event Notifications is a highly available, multi-tenant, regional service.

## Service High Availability (HA)
{: #en-service-high-availability}

An availability zone is a logically and physically isolated location within an {{site.data.keyword.cloud_notm}} region where your data is processed and hosted.

- An availability zone has independent power, cooling, and network infrastructures that are isolated from other zones to strengthen fault tolerance by avoiding single points of failure between zones.
- An availability zone offers high bandwidth and low inter-zone latency within a region.

A region (location) is a geographically and physically separate group of one or more availability zones with independent electrical and network infrastructures that are isolated from other regions.

- Regions are designed to remove shared single points of failure with other regions and provide low inter-zone latency within the region.
- Each region has three different data centers (DC) for redundancy.
- In each supported region, traffic is load balanced across infrastructure in multiple availability zones, with no single point of failure.
- If all the data centers in a region fail, {{site.data.keyword.en_short}} becomes unavailable in that region.

## Availability zones for {{site.data.keyword.en_short}}
{: #en-zones-ha}

{{site.data.keyword.en_full_notm}} service is a highly available, regional service. In each supported region, the service exists in multiple availability zones with no single point of failure. 

The following table lists the high-availability (HA) status for the regions (locations) where the {{site.data.keyword.en_full_notm}} service is available:

 Geography| Region| HA Status |
|----------|-------|-----------|
| Asia-Pacific| Sydney (au-syd)|MZR|
| Asia-Pacific| Tokyo (jp-tok)|MZR|
| Asia-Pacific| Osaka (jp-osa)|MZR|
| Europe | London (eu-gb)|MZR|
| Europe | Frankfurt (eu-de)|MZR|
| Europe | Madrid (eu-es)|MZR|
| North America | Dallas (us-south)|MZR|
| North America | Toronto (ca-tor)|MZR|
| Brazil | Sao Paulo (br-sao) | MZR |
{: caption="HA status for the regions" caption-side="bottom"}

Where:

- A *geography* is a geographic area or larger political body that contains one or more regions.
- A *region* is a defined geographic territory.
   - A region might be a specific postal code area, a town, a city, a state, a group of states, or even a group of countries.
   - A region contains [multiple availability zones](https://www.ibm.com/solutions/cloud-data-centers) to meet local access, low latency, and security requirements for the region.
- `MZR` means multi-zone region. [Learn more](/docs/overview?topic=overview-locations#table-mzr).

## Locations
{: #ha-locations}

For more information about service availability within regions and data centers, see [Service and infrastructure availability by location](/docs/event-notifications?topic=event-notifications-en-regions-endpoints).


## Responsibilities
{: #ha-responsibilities}

For more information about your responsibilities when using {{site.data.keyword.en_short}}, see [Shared responsibilities](/docs/event-notifications?topic=event-notifications-en-responsibilities).


## What level of availability does {{site.data.keyword.cloud_notm}} offer?
{: #ha-service}

To learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}, see [How do I ensure zero downtime?](/docs/resiliency?topic=resiliency-ha-redundancy) or [Service Level Agreements](/docs/overview?topic=overview-slas).


## Disaster recovery (DR) for {{site.data.keyword.en_short}} service in a region
{: #ac-dr}

{{site.data.keyword.en_short}} is a regional service, and does not offer automatic cross-regional failover or cross-regional disaster recovery. If all of the availability zones in a region fail, {{site.data.keyword.en_short}} becomes unavailable in that region.
{: important}

If an entire MZR becomes inoperative (usually due to a catastrophic disaster or failure), {{site.data.keyword.IBM_notm}} runs disaster-recovery plans to restore service within 24 hours or less. {{site.data.keyword.IBM_notm}} restores the service in an alternative MZR from an IBM-managed backup. Existing DNS names are migrated to the backup deployment. When the disaster recovery process is complete, API traffic resumes automatically.

When the primary MZR is restored, the secondary deployment is migrated back to the primary site. After the migration is complete, the DNS is restored to its original routing.

If you need zero downtime during a regional disaster recovery, create and maintain backup instances in other regions. To synchronize a service instance in one region with an instance in a different region, you can use the APIs mentioned [here](/apidocs/event-notifications).
