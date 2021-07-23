---

copyright:
  years: 2021
lastupdated: "2021-03-19"

keywords: app-configuration, app configuration, data model, high availability, ha

subcollection: app-configuration

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}

# High availability
{: #ac-ha}

<!-- All IBM Cloud® general availability (GA) services have a Service Level Agreement of 99.99% availability.  -->

{{site.data.keyword.IBM_notm}} {{site.data.keyword.appconfig_short}} is a service that is offered in the<!-- five --> regions: Dallas, London, and Sydney. Every region supported, has its own IBM Cloud Kubernetes Service cluster with several worker nodes. Each worker node runs several instances of {{site.data.keyword.appconfig_short}} service components. Each region is fronted by a global load balancer and a web application firewall.  
{: shortdesc}

{{site.data.keyword.appconfig_short}} service persists tenant data in highly available database. A single regional database is used to store the data of all tenants in that particular region. The data is stored across multiple zones in each region for high availability. Data that is stored is encrypted and persisted in a database cluster that is spread across availability zones. All databases connections use TLS/SSL encryption for data in transit.

{{site.data.keyword.appconfig_short}} service is a regional service. It does not provide automated cross-regional failover or cross-regional disaster recovery. If a regional disaster occurs, all data might not be recovered. However, a location recovery is possible and all data can be restored. If there is a need for regional disaster recovery, it is recommended that you create and maintain backup instances in other regions. To synchronize a service instance in one region with an instance in a different region, you can use the APIs mentioned [here](https://cloud.ibm.com/apidocs/app-configuration).
