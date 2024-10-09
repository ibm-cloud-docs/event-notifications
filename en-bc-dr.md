---

copyright:
  years: 2021, 2023
lastupdated: "2023-12-04"

keywords: HA for Event Notifications, high availability for Event Notifications, Event Notifications, disaster recovery

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# Understanding business continuity and disaster recovery for {{site.data.keyword.en_short}}
{: #en-bc-dr}

[Disaster recovery](#x2113280){: term} involves a set of policies, tools, and procedures for returning a system, an application, or an entire data center to full operation after a catastrophic interruption. It includes procedures for copying and storing an installed system's essential data in a secure location, and for recovering that data to restore normalcy of operation.
{: shortdesc}

## Responsibilities
{: #bc-dr-responsibilities}

For more information about your responsibilities when using {{site.data.keyword.en_short}}, see [Shared responsibilities](/docs/event-notifications?topic=event-notifications-en-responsibilities).

## Disaster recovery strategy
{: #bc-dr-strategy}

{{site.data.keyword.cloud_notm}} has [business continuity](#x3026801){: term} plans in place to provide for the recovery of services within hours if a disaster occurs. You are responsible for your data backup and associated recovery of your content.

{{site.data.keyword.en_short}} provides mechanisms to protect your data and restore service functions. Business continuity plans are in place to achieve targeted [recovery point objective](#x3429911){: term} (RPO) and [recovery time objective](#x3167918){: term} (RTO) for the service. The following table outlines the targets for {{site.data.keyword.en_short}}.

| Disaster recovery objective | Target Value   |
|---|---|
|  RPO | 24 hours |
|  RTO | 9 hours |
{: caption="Table 1. RPO and RTO for {{site.data.keyword.en_short}}" caption-side="bottom"}


## Locations
{: #ha-locations-dr}

For more information about service availability within regions and data centers, see [Service and infrastructure availability by location](/docs/event-notifications?topic=event-notifications-en-regions-endpoints).
