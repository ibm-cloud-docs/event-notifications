---

copyright:
  years: 2021
lastupdated: "2021-08-02"

keywords: HA for _service-name_, high availability for _service-name_

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

# High availability and disaster recovery for Event Notifications
{: #ha}

<!-- The title of your H1 should be Understanding high availability for _service-name_, where _service-name_ is the non-trademarked short version conref. Include your service name as a search keyword at the top of your Markdown file. See the example keywords above. -->

<!-- The short description should be a single, concise paragraph that contains one or two sentences and no more than 50 words. Summarize your offering's strategy for HA. The following is a suggested short description._
{: shortdesc} -->

Event Notifications service is a highly available, regional service that runs in multiple zones.

In each supported multizone region, every zone has its own IBM Cloud Kubernetes Service cluster with several worker nodes. Each worker node runs several instances of Event Notifications service components. Each region is fronted by a global load balancer and a web application firewall.

Event Notifications service persists tenant data in highly available database. A single regional database is used to store data of all the Event Notifications tenants in that particular region. The data is stored across multiple zones in each region. Data that is stored in Event Notifications service is encrypted and persisted in a database cluster that is spread across availability zones. All databases connections use TLS/SSL encryption for data in transit.

Event Notifications service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all data might not be recovered. However, a location recovery is possible and all data can be restored. If there is a need for regional disaster recovery, it is recommended that you create and maintain backup instances in other regions. European data does not leave the EU. To synchronize a service instance in one region with an instance in a different region, you can use the APIs mentioned here.

Review the API documentation to consider the important data that you want to back up and restore.

For example, you might start with the following to be backed up:

sources :  /v1/instances/{instance_id}/sources - Your platform sources
topics: /v1/instances/{instance_id}/topics -  All registered topics
rules: /v1/instances/{instance_id}/rules – All rules created on topics
destinations: /v1/instances/{instance_id}/destinations – All registered destinations
subscriptions: /v1/instances/{instance_id}/subscriptions - All the subscriptions
For each of the data set that you need to back up and restore, use the GET calls to get a copy of the data, and use corresponding the PUT / POST API to populate the new instance on a different region


## Locations
{: #ha-locations}

For more information about service availability within regions and data centers, see [here](https://test.cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-regions-endpoints#en-regions).
