---

copyright:
  years: 2018, 2024
lastupdated: 2024-09-06"

keywords: IBM Cloud, observability

subcollection: observability-ibm

---

{{site.data.keyword.attribute-definition-list}}

_Include your monitoring topic in an Observability topic group in the How to nav group in your toc.yaml file._





# Monitoring metrics for {{site.data.keyword.en_full}}
{: #monitoring}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.en_full}}, generate platform metrics that you can use to gain operational visibility into the performance and health of the service in your account.
{: shortdesc}

{{site.data.keyword.mon_full_notm}} is a third-party cloud-native, and container-intelligence management system that can be included as part of your {{site.data.keyword.cloud_notm}} architecture. It offers administrators, DevOps teams, and developers full-stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards. For more information, see [Monitoring in IBM Cloud](/docs/monitoring?topic=monitoring-about-monitor).

You can use {{site.data.keyword.metrics_router_full_notm}}, a platform service, to route platform metrics in your account to a destination of your choice by configuring targets and routes that define where platform metrics are sent. For more information, see [About {{site.data.keyword.metrics_router_full_notm}} in {{site.data.keyword.cloud_notm}}](/docs/metrics-router?topic=metrics-router-about).

You can use {{site.data.keyword.mon_full}} to visualize and alert on metrics that are generated in your account and routed by {{site.data.keyword.metrics_router_full_notm}} to an {{site.data.keyword.mon_full_notm}} instance.

## Locations where metrics are generated
{: #mon-locations}



{{site.data.keyword.en_full}} sends metrics in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green}| [No]{: tag-red} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where metrics are sent in Americas locations" caption-side="top"}
{: #mon-table-1}
{: tab-title="Americas"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where metrics are sent in Asia Pacific locations" caption-side="top"}
{: #mon-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where metrics are sent in Europe locations" caption-side="top"}
{: #mon-table-3}
{: tab-title="Europe"}
{: tab-group="mon"}
{: class="simple-tab-table"}
{: row-headers}


## Enabling platform metrics for {{site.data.keyword.en_full}}
{: #monitoring-enable}

Before you can start with {{site.data.keyword.en_short}} monitoring metrics, you must first opt in and [enable platform metrics](https://cloud.ibm.com/docs/monitoring?topic=monitoring-platform_metrics_enabling)
{: note}

You can configure only one instance of the {{site.data.keyword.mon_full_notm}} service per region to collect platform metrics.

- To configure the {{site.data.keyword.mon_full_notm}} instance, you must turn on the platform metrics configuration setting.
- If a monitoring instance in a region is already enabled to collect platform metrics, metrics from enabled-monitoring services are collected automatically and available for monitoring through this instance. For more information about enabled-monitoring services, see {{site.data.keyword.cloud}} services.

To monitor platform metrics, check that the {{site.data.keyword.mon_full_notm}} instance is provisioned in the same region where the {{site.data.keyword.cloud_notm}} instance is provisioned.
{: note}



## Viewing metrics
{: #monitoring-view}

To monitor {{site.data.keyword.en_full}} metrics, you must launch the {{site.data.keyword.mon_full_notm}} web UI for the instance that is enabled for platform metrics in the region where your {{site.data.keyword.en_full}} instance is provisioned.
{: important}


### Launching {{site.data.keyword.mon_full}} from the Observability page
{: #monitoring-view-ob}

For more information about launching the {{site.data.keyword.mon_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.mon_full_notm}} documentation.](/docs/monitoring?topic=monitoring-launch)


## Monitoring {{site.data.keyword.en_full}}
{: #monitoring-monitor}

1. Start the [{{site.data.keyword.mon_full_notm}} web UI](https://cloud.ibm.com/docs/monitoring?topic=monitoring-launch) from the `Observability` page.

1. Click `DASHBOARDS`.

1. In the `Default Dashboards` section, expand `IBM`.

1. Choose the `{{site.data.keyword.en_short}}` dashboard from the list.

Access your deployment's monitoring dashboard from {{site.data.keyword.mon_full_notm}}, it's in the sidebar, under `IBM`.
Next, change the scope or make a copy of the default dashboard to monitor an {{site.data.keyword.en_short}} service instance.

### _Add entries per recommendation to monitor your {{site.data.keyword.en_full}}
{: #monitoring-monitor-1}



## serviceName predefined dashboards
{: #monitoring-dashboards}



## Metrics available by service plan
{: #monitoring-metrics-by-plan}

| Metric Name |
| ------------|
| [ibm_eventnotifications_total_ingested_notifications](#ibm_eventnotifications_total_ingested_notifications)|
| [ibm_eventnotifications_total](#ibm_eventnotifications_total)|
| [ibm_eventnotifications_failed](#ibm_eventnotifications_failed)|
| [ibm_eventnotifications_devices](#ibm_eventnotifications_devices)|
{: caption="Metrics available by service plan" caption-side="bottom"}

### ibm_eventnotifications_total_ingested_notifications
{: #ibm_eventnotifications_total_ingested_notifications-old}

Total number of notifications that are ingested. Ingested notifications are events from a source that has at least one condition that is defined on them for filtering.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_total_ingested_notifications` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`, `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_source`  |
{: caption="Ingestion metadata" caption-side="bottom"}

### ibm_eventnotifications_total
{: #ibm_eventnotifications_total-old}

Total number of notifications for a particular type includes successful and failed notifications.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_total` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`, `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_source`, `ibm_eventnotifications_destination`, `ibm_eventnotifications_source`, `ibm_eventnotifications_type`|
{: caption="Notifications metadata" caption-side="bottom"}

### ibm_eventnotifications_failed
{: #ibm_eventnotifications_failed-old}

Total number of failed notifications of a particular type.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_failed` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`, `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_destination`, `ibm_eventnotifications_source`, `ibm_eventnotifications_type`,  |
{: caption="Failed notifications metadata" caption-side="bottom"}

### ibm_eventnotifications_devices
{: #ibm_eventnotifications_devices-old}

Total number of push notification devices registered.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_devices` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`, `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_destination`, `ibm_eventnotifications_device_type`,  |
{: caption="Total devices registered" caption-side="bottom"}






## Attributes for segmentation
{: #monitoring-attributes}

### Global attributes
{: #monitoring-attributes-global}

The following attributes are available for segmenting all of the metrics previously listed.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of `public`, `dedicated`, or `local`. |
| `Location` | `ibm_location` | The location of the monitored resource, which can be a region, data center, or global. |
| `Scope` | `ibm_scope` | The scope is the account, organization, or space GUID associated with this metric. |
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance that the metric is associated with. |
{: caption="Segmentation attributes" caption-side="bottom"}

### Additional attributes
{: #monitoring-attributes-add}

The following attributes are available for segmenting one or more attributes as described in the previous tables. See the individual metrics for segmentation options.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Name of the destination` | `ibm_eventnotifications_destination` | A destination name with its associated ID. |
| `Name of the source` | `ibm_eventnotifications_source` | A source name with its associated ID. |
| `Type of event notification` | `ibm_eventnotifications_type` | The type of supported destination types. (email, SMS, or webhook) |
| `Type of push notification device` | `ibm_eventnotifications_device_type` | The type of supported push notification device.(push_android, push_ios) |
{: caption="More attributes" caption-side="bottom"}
