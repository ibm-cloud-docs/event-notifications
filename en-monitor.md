---

copyright:
  years: 2021
lastupdated: "2021-10-27"

keywords: event-notification, event notification, high availability, ha, monitoring, metrics, monitor apps

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{: note .note}
{:note: .note}
{: objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}

# Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.mon_full_notm}}
{: #en-monitoring}

<!-- All IBM Cloud® general availability (GA) services have a Service Level Agreement of 99.99% availability.  -->

Use {{site.data.keyword.mon_full_notm}} to gain operational visibility into the performance and health of your applications, services, and platforms. It offers administrators, DevOps teams, and developers full stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards.
{: shortdesc}

## Set up your {{site.data.keyword.mon_full_notm}} service instance
{: #en-setup-monitor}

To get started, you need to [provision {{site.data.keyword.Bluemix_notm}} Monitoring ](https://cloud.ibm.com/catalog/services/ibm-cloud-monitoring?callback=/observe/monitoring/create) instance on your {{site.data.keyword.IBM}} account. For more information, see [here. ](https://cloud.ibm.com/docs/monitoring?topic=monitoring-provision)


Currently, {{site.data.keyword.mon_full_notm}} integration is available for {{site.data.keyword.en_short}} service deployments in the following regions:

| Deployment region    | Monitoring region |
|-------------|-------------|
| Dallas| Dallas |
| London| London|
| Sydney| Sydney|

Before you can start with {{site.data.keyword.en_short}} monitoring metrics, you must first opt in and [enable platform metrics](https://cloud.ibm.com/docs/monitoring?topic=monitoring-platform_metrics_enabling)
{: note .note}

You can configure only one instance of the {{site.data.keyword.mon_full_notm}} service per region to collect platform metrics.
 - To configure the {{site.data.keyword.mon_full_notm}} instance, you must turn on the platform metrics configuration setting.
 - If a monitoring instance in a region is already enabled to collect platform metrics, metrics from enabled-monitoring services are collected automatically and available for monitoring through this instance. For more information about enabled-monitoring services, see {{site.data.keyword.Bluemix}} services.


 To monitor platform metrics, check that the {{site.data.keyword.mon_full_notm}} instance is provisioned in the same region where the {{site.data.keyword.Bluemix_notm}} instance is provisioned.
 {:note: .note}


 ## Access your {{site.data.keyword.mon_full_notm}} metrics
 {: #en-access-monitor}

 1. Launch the [{{site.data.keyword.mon_full_notm}} web UI](https://cloud.ibm.com/docs/monitoring?topic=monitoring-launch) from the <wintitle>Observability</wintitle> page
 2. Click DASHBOARDS
 3. In the Default Dashboards section, expand IBM
 4. Choose the {{site.data.keyword.en_short}} dashboard from the list.
 Access your deployment's monitoring dashboard from {{site.data.keyword.mon_full_notm}}, it's in the sidebar, under IBM.
 Next, change the scope or make a copy of the default dashboard to monitor an {{site.data.keyword.en_short}} service instance.

## Metrics available by Service Plan
 {: #en-metrics-by-plan}

 | Metric Name |
 | ------------|
 | [ibm_eventnotifications_total_ingested_notifications](#ibm_eventnotifications_total_ingested_notifications)|
 | [ibm_eventnotifications_total](#ibm_eventnotifications_total)|
 | [ibm_eventnotifications_failed](#ibm_eventnotifications_failed)|


### ibm_eventnotifications_total_ingested_notifications
{: ibm_eventnotifications_total_ingested_notifications}

Total number of notifications that are ingested. Ingested notifications are events from a source that has at least one condition that is defined on them for filtering.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_total_ingested_notifications` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`,  `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_source`  |



### ibm_eventnotifications_total
{: ibm_eventnotifications_total}

Total number of notifications for a particular type including successful and failed notifications

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_total` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`,  `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_source`, `ibm_eventnotifications_destination`, `ibm_eventnotifications_source`, `ibm_eventnotifications_type`   |


### ibm_eventnotifications_failed
{: ibm_eventnotifications_failed}

Total number of failed notifications of a particular type.

| Metadata   | Description |
|-------------|-------------|
| `Metric Name` | `ibm_eventnotifications_failed` |
| `Metric Type` | `gauge`|
| `Value Type` | `none`|
| `Segment By` | `ibm_scope`, `ibm_ctype`, `ibm_location`,  `ibm_service_name`, `ibm_service_instance`, `ibm_eventnotifications_destination`, `ibm_eventnotifications_source`, `ibm_eventnotifications_type`,  |

## Attributes for segmentation
{: attributes-en}

### Global Attributes
{: global-attributes-en}

The following attributes are available for segmenting all of the metrics previously listed.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of `public`, `dedicated`, or `local`. |
| `Location` | `ibm_location` | The location of the monitored resource, which can be a region, data center, or global. |
| `Scope` | `ibm_scope` | The scope is the account, organization, or space GUID associated with this metric. |
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance that the metric is associated with. |

### More attributes
{: additional-attributes-en}

The following attributes are available for segmenting one or more attributes as described in the previous tables. See the individual metrics for segmentation options.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Name of the destination` | `ibm_eventnotifications_destination` | A destination name with its associated id. |
| `Name of the source` | `ibm_eventnotifications_source` | A source name with its associated id. |
| `Type of event notification` | `ibm_eventnotifications_type` | The type of supported destination types. (email, sms or webhook) |

