---

copyright:
  years: 2021, 2023
lastupdated: "2023-10-21"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications, disaster recovery

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# Understanding business continuity and disaster recovery for {{site.data.keyword.en_short}}
{: #bc-dr}

[Disaster recovery](#x2113280){: term} involves a set of policies, tools, and procedures for returning a system, an application, or an entire data center to full operation after a catastrophic interruption. It includes procedures for copying and storing an installed system's essential data in a secure location, and for recovering that data to restore normalcy of operation.
{: shortdesc}

## Responsibilities
{: #bc-dr-responsibilities}

For more information about your responsibilities when using {{site.data.keyword.en_short}}, see [Shared responsibilities for {{site.data.keyword.{{site.data.keyword.en_short}}](/docs/{{site.data.keyword.en_short}}?topic=yourproduct-full-keyref-responsibilities).

## Disaster recovery strategy
{: #bc-dr-strategy}

{{site.data.keyword.cloud_notm}} has [business continuity](#x3026801){: term} plans in place to provide for the recovery of services within hours if a disaster occurs. You are responsible for your data backup and associated recovery of your content.

{{site.data.keyword.en_short}} provides mechanisms to protect your data and restore service functions. Business continuity plans are in place to achieve targeted [recovery point objective](#x3429911){: term} (RPO) and [recovery time objective](#x3167918){: term} (RTO) for the service. The following table outlines the targets for {{site.data.keyword.en_short}}.

| Disaster recovery objective | Target Value   |
|---|---|
|  RPO |   |
|  RTO |   |
{: caption="Table 1. RPO and RTO for {{site.data.keyword.en_short}}" caption-side="bottom"}


If an entire MZR becomes inoperative (usually due to a catastrophic disaster or failure), {{site.data.keyword.IBM_notm}} runs disaster-recovery plans to restore service within 24 hours or less. {{site.data.keyword.IBM_notm}} restores the service in an alternative MZR from an IBM-managed backup. Existing DNS names are migrated to the backup deployment. When the disaster recovery process is complete, API traffic resumes automatically.

{{site.data.keyword.en_short}} service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all the data might not be recovered. However, a location recovery is possible and data can be restored from that location.
{: important}

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


## Locations
{: #ha-locations}

For more information about service availability within regions and data centers, see [Service and infrastructure availability by location](/docs/event-notifications?topic=event-notifications-en-regions-endpoints).



