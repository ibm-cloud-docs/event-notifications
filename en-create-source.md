---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event-notifications, source, tutorials

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Adding an {{site.data.keyword.en_short}} source
{: #en-add-source}

Various services produce events that can be consumed by {{site.data.keyword.en_short}}. You can add these services as 'sources' within your {{site.data.keyword.en_short}} instance. When a source is added, you can filter the events from it by using topics, and then subscribe destinations to the topics.
{: shortdesc}

## Types of sources
{: #en-add-source-types}

There are now four types of sources that are supported for {{site.data.keyword.en_short}}: {{site.data.keyword.cloud_notm}} sources, generic API sources, {{site.data.keyword.cloud_notm}} platform sources and the Periodic Timer.

With {{site.data.keyword.cloud_notm}} sources, events emit from managed services on {{site.data.keyword.cloud_notm}}. For example, {{site.data.keyword.monitoringfull_notm}}, {{site.data.keyword.cloud_notm}} Security and Compliance Center, {{site.data.keyword.secrets-manager_full_notm}}, {{site.data.keyword.appconfig_short}}, IBM Cloud Projects, and Toolchain can all be added to {{site.data.keyword.en_short}} {{site.data.keyword.cloud_notm}} sources.

With generic API sources, events emanate from services or applications that are not managed by IBM. For example, if you create your own application that sends events to {{site.data.keyword.en_short}}, your application can be added as an API source.

API sources cannot route notifications to the {{site.data.keyword.cloud_notm}} email service and {{site.data.keyword.cloud_notm}} SMS service because these services deliver content that is generated exclusively from {{site.data.keyword.cloud_notm}} managed services.
{: note}

By default, {{site.data.keyword.cloud_notm}} Resource lifecycle events is provided as a source and is disabled. You can enable it, if you like to monitor the {{site.data.keyword.cloud_notm}} Resource lifecycle events, which you need to incur more charges. {{site.data.keyword.cloud_notm}} Resource lifecycle events are events around the {{site.data.keyword.cloud_notm}} resources like instance creation, updating an instance, deleting an instance and other events related to {{site.data.keyword.cloud_notm}} resources.

The Periodic Timer source is also provided as a default source. It is used to schedule events based on a period defined by the user. It is disabled by deafult and you can enable it to schedule events periodically. 

To see the current list of {{site.data.keyword.cloud_notm}} services available as {{site.data.keyword.en_short}} sources, go to the **Sources** section of your {{site.data.keyword.en_short}} dashboard, click **Add**, and select **{{site.data.keyword.cloud_notm}} sources**.

The connection protocols differ between source types, so the procedure for adding is different as described in the following sections.

## Adding a source
{: #en-add-source-IBM-managed}

1. Verify that the {{site.data.keyword.cloud_notm}} service is available as a source for {{site.data.keyword.en_short}}.
   - Go to the **Sources** section of the {{site.data.keyword.en_short}} dashboard.
   - Click **Add** and select **{{site.data.keyword.cloud_notm}} source**.
   - Confirm that the managed service of interest is displayed.

1. Create a service-to-service authorization between your {{site.data.keyword.cloud_notm}} service and {{site.data.keyword.en_short}}.
   - From the {{site.data.keyword.cloud_notm}} console, navigate to **Manage** > **Access(IAM)** > **Authorizations**.
   - Select your {{site.data.keyword.cloud_notm}} service as the source, and {{site.data.keyword.en_short}} as the target from the authorisation view.
   - Set the service access level to **Event Source Manager**.

1. Find your existing service instances in your [account resource list](https://cloud.ibm.com/resources){: external} and select the instance of interest and open its dashboard.

If you do not have an existing instance, create one from the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog){: external}.
{: tip}

## Adding a generic API source
{: #en-add-source-generic-API}

API Sources cannot be used to send notifications to out-of-the-box destinations like email and SMS.
{: note}

1. Go to the **Sources** section of the {{site.data.keyword.en_short}} dashboard.
1. Click **Add** and select **API Source**.
1. Type a name and an optional description and click **Add**.

Follow the instructions in the [{{site.data.keyword.en_short}} API documentation](/apidocs/event-notifications), or in the SDK documentation for your programming language to configure the connection as you are connecting from your own application or service.
