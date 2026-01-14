---

copyright:
  years: 2018, 2026
lastupdated: "2025-07-28"

keywords: IBM Cloud, observability

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring metrics for {{site.data.keyword.en_short}}
{: #monitoring}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.en_full}}, generate platform metrics that you can use to gain operational visibility into the performance and health of the service in your account.
{: shortdesc}

{{site.data.keyword.mon_full_notm}} is a third-party cloud-native, and container-intelligence management system that can be included as part of your {{site.data.keyword.cloud_notm}} architecture. It offers administrators, DevOps teams, and developers full-stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards. For more information, see [Monitoring in IBM Cloud](/docs/monitoring?topic=monitoring-about-monitor).

You can use {{site.data.keyword.metrics_router_full_notm}}, a platform service, to route platform metrics in your account to a destination of your choice by configuring targets and routes that define where platform metrics are sent. For more information, see [About {{site.data.keyword.metrics_router_full_notm}} in {{site.data.keyword.cloud_notm}}](/docs/metrics-router?topic=metrics-router-about).

You can use {{site.data.keyword.mon_full_notm}} to visualize and alert on metrics that are generated in your account and routed by {{site.data.keyword.metrics_router_full_notm}} to an {{site.data.keyword.mon_full_notm}} instance.

## Locations where metrics are generated
{: #mon-locations}

{{site.data.keyword.en_full}} sends metrics in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington DC (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) | Montreal (`ca-mon`) |
|---------------------|-------------------------|-------------------|----------------------|----------------------|
| [Yes]{: tag-green}| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where metrics are sent in Americas locations" caption-side="top"}
{: #mon-table-1}
{: tab-title="Americas"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red} |
{: caption="Regions where metrics are sent in Asia Pacific locations" caption-side="top"}
{: #mon-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|----------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where metrics are sent in Europe locations" caption-side="top"}
{: #mon-table-3}
{: tab-title="Europe"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}

## Enabling platform metrics for {{site.data.keyword.en_short}}
{: #monitoring-enable}

Before you can start with {{site.data.keyword.en_short}} monitoring metrics, you must first opt in and [enable platform metrics](/docs/monitoring?topic=monitoring-platform_metrics_enabling).
{: note}

You can configure only one instance of the {{site.data.keyword.mon_full_notm}} service per region to collect platform metrics.

- To configure the {{site.data.keyword.mon_full_notm}} instance, you must turn on the platform metrics configuration setting.
- If a monitoring instance in a region is already enabled to collect platform metrics, metrics from enabled-monitoring services are collected automatically and available for monitoring through this instance. For more information about enabled-monitoring services, see {{site.data.keyword.cloud}} services.

To monitor platform metrics, check that the {{site.data.keyword.mon_full_notm}} instance is created in the same region where the {{site.data.keyword.cloud_notm}} instance is created.
{: note}

## Viewing metrics
{: #monitoring-view}

To monitor {{site.data.keyword.en_short}} metrics, you must launch the {{site.data.keyword.mon_full_notm}} web UI for the instance that is enabled for platform metrics in the region where your service instance is created.
{: important}

### Launching {{site.data.keyword.mon_full}} from the Observability page
{: #monitoring-view-ob}

For more information about launching the {{site.data.keyword.mon_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.mon_full_notm}} documentation.](/docs/monitoring?topic=monitoring-launch)

## Monitoring {{site.data.keyword.en_short}}
{: #monitoring-monitor}

1. Start the [{{site.data.keyword.mon_full_notm}} web UI](/docs/monitoring?topic=monitoring-launch) from the Observability page.
1. Click **DASHBOARDS**.
1. In the Default Dashboards section, expand **{{site.data.keyword.IBM_notm}}**.
1. Select the {{site.data.keyword.en_short}} dashboard from the list.
1. Access your deployment's monitoring dashboard from {{site.data.keyword.mon_full_notm}} located in the sidebar under **{{site.data.keyword.IBM_notm}}**.
1. Change the scope or make a copy of the default dashboard to monitor a service instance.

## Metrics available by service plan
{: #monitoring-metrics-by-plan}

| Name | Description |
| ------------ | ------------ |
| ibm_eventnotifications_total_ingested_notifications| The total number of notifications that are ingested. Ingested notifications are events from a source that has at least one condition that is defined on them for filtering. |
| ibm_eventnotifications_total | The total number of notifications for a particular type includes successful and failed notifications. | 
| ibm_eventnotifications_failed | The total number of failed notifications of a particular type. |
| ibm_eventnotifications_devices | The total number of push notification devices registered. |
{: caption="Metrics available by service plan" caption-side="bottom"}



## Attributes for segmentation
{: #monitoring-attributes}

### Global attributes
{: #monitoring-attributes-global}

The following attributes are available for segmenting all of the metrics previously listed.

| Attribute | Name | Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of `public`, `dedicated`, or `local`. |
| `Location` | `ibm_location` | The location of the monitored resource, which can be a region, data center, or global. |
| `Scope` | `ibm_scope` | The scope is the account, organization, or space GUID associated with this metric. |
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance that the metric is associated with. |
{: caption="Global segmentation attributes" caption-side="bottom"}

### Additional attributes
{: #monitoring-attributes-add}

The following attributes are available for segmenting one or more attributes as described in the previous tables. See the individual metrics for segmentation options.

| Attribute | Name | Description |
|-----------|----------------|-----------------------|
| `Name of the destination` | `ibm_eventnotifications_destination` | A destination name with its associated ID. |
| `Name of the source` | `ibm_eventnotifications_source` | A source name with its associated ID. |
| `Type of event notification` | `ibm_eventnotifications_type` | The type of supported destination types. (email, SMS, or webhook) |
| `Type of push notification device` | `ibm_eventnotifications_device_type` | The type of supported push notification device.(push_android, push_ios) |
{: caption="Additional segmentation attributes" caption-side="bottom"}
