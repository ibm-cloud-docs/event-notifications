---

copyright:
  years: 2020, 2023
lastupdated: "2023-04-21"

keywords: event notifications, event-notifications, source, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 15m

---

{{site.data.keyword.attribute-definition-list}}

# Add an {{site.data.keyword.en_short}} source
{: #en-add-source}
{: toc-content-type="tutorial"}
{: toc-completion-time="15m"}

Add an {{site.data.keyword.en_short}} source. Various services produce events that can be consumed by {{site.data.keyword.en_short}}. You can add these services as 'sources' within your {{site.data.keyword.en_short}} instance. When a source is added, you can filter the events from it by using topics, and then subscribe destinations to the topics.
{: shortdesc}

## Types of sources
{: #en-add-source-types}

Three types of sources are supported for {{site.data.keyword.en_short}}: {{site.data.keyword.cloud_notm}} sources, generic API sources, and {{site.data.keyword.cloud_notm}} platform sources.

With {{site.data.keyword.cloud_notm}} sources, events emit from managed services on {{site.data.keyword.cloud_notm}}. For example, {{site.data.keyword.monitoringfull_notm}}, {{site.data.keyword.cloud_notm}} Security and Compliance Center, {{site.data.keyword.secrets-manager_full_notm}}, {{site.data.keyword.appconfig_short}}, and Toolchain can all be added to {{site.data.keyword.en_short}} {{site.data.keyword.cloud_notm}} sources.

With generic API sources, events emanate from services or applications that are not managed by IBM. For example, if you create your own application that sends events to {{site.data.keyword.en_short}}, your application can be added as an API source.

API sources cannot route notifications to the {{site.data.keyword.cloud_notm}} email service and {{site.data.keyword.cloud_notm}} SMS service because these services deliver content that is generated exclusively from {{site.data.keyword.cloud_notm}} managed services.
{: note}

By default, {{site.data.keyword.cloud_notm}} Resource lifecycle events is provided as a source and is disabled. You can enable it, if you like to monitor the {{site.data.keyword.cloud_notm}} Resource lifecycle events, which you need to incur more charges. {{site.data.keyword.cloud_notm}} Resource lifecycle events are events around the {{site.data.keyword.cloud_notm}} resources like instance creation, updating an instance, deleting an instance and other events related to {{site.data.keyword.cloud_notm}} resources.

To see the current list of {{site.data.keyword.cloud_notm}} services available as {{site.data.keyword.en_short}} sources, go to the `Sources` section of your {{site.data.keyword.en_short}} dashboard, click `Add`, and select `{{site.data.keyword.cloud_notm}} sources`.

The connection protocols differ between source types, so the procedure for adding is different as described in the following sections.

## Add an {{site.data.keyword.cloud_notm}} source
{: #en-add-source-IBM-managed}

## Verify the {{site.data.keyword.cloud_notm}} service
{: #en-verify-manage-service}
{: step}

Verify that the {{site.data.keyword.cloud_notm}} service is available as a source for {{site.data.keyword.en_short}}.

- Go to the `Sources` section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select `{{site.data.keyword.cloud_notm}} source`.
- Confirm that the managed service of interest is shown.

## Create a service authorization
{: #en-create-service-auth}
{: step}

Create a service-to-service authorization between your {{site.data.keyword.cloud_notm}} service and {{site.data.keyword.en_short}}.

- From the {{site.data.keyword.cloud_notm}} console, select `Manage` >> `Access(IAM)` >> `Authorizations`.
- The Authorizations view contains drop-down list for `Source service` and `Target service`. Select your {{site.data.keyword.cloud_notm}} service as the source, and {{site.data.keyword.en_short}} as the target.
- Set the service access level to `Event Source Manager`.

## Find your instance of the {{site.data.keyword.cloud_notm}} service
{: #en-find-mg-serv-inst}
{: step}

- Find your existing service instances in your [account resource list](https://cloud.ibm.com/resources){: external}.
- Select the instance of interest and open its dashboard.

If you don't have an existing instance, create one from the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog){: external}.
{: tip}

## Configure your {{site.data.keyword.cloud_notm}} service instance to connect to {{site.data.keyword.en_short}}
{: #en-config-mgt-serv-inst}
{: step}

Follow the documentation for the selected service to configure the connection to {{site.data.keyword.en_short}}.

## Add a generic API source
{: #en-add-source-generic-API}

API Sources cannot be used to send notifications to out of the box destinations like email and SMS.
{: note}

- Go to the `Sources` section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select `API Source`.
- Type a name and an optional description and click `Add`.
- Because you are connecting from your own application or service, follow the instructions in the [{{site.data.keyword.en_short}} API documentation](https://cloud.ibm.com/apidocs/event-notifications/event-notifications?code=node), or in the SDK documentation for your programming language to configure the connection.
