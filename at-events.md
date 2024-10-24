---

copyright:
  years: 2021, 2024
lastupdated: "2024-09-06"

keywords:

subcollection: # Your subcollection value

---

{{site.data.keyword.attribute-definition-list}}

_Include your activity tracking events file in an Observability topic group in the How to nav group in your toc.yaml file._



# Activity tracking events for {{site.data.keyword.en_short}}
{: #at_events}



{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.en_short}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.



As of 28 March 2024, the {{site.data.keyword.at_full_notm}} service is deprecated and will no longer be supported as of 30 March 2025. Customers will need to migrate to {{site.data.keyword.logs_full_notm}} before 30 March 2025. During the migration period, customers can use {{site.data.keyword.at_full_notm}} along with {{site.data.keyword.logs_full_notm}}. Activity tracking events are the same for both services. For information about migrating from {{site.data.keyword.at_full_notm}} to {{site.data.keyword.logs_full_notm}} and running the services in parallel, see [migration planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).
{: important}

## Locations where activity tracking events are generated
{: #at-locations}



## Locations where activity tracking events are sent to {{site.data.keyword.at_full_notm}} hosted event search
{: #at-legacy-locations}



{{site.data.keyword.en_short}} sends activity tracking events to {{site.data.keyword.at_full_notm}} hosted event search in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where activity tracking events are sent in Americas locations" caption-side="top"}
{: #at-table-1}
{: tab-title="Americas"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #at-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where activity tracking events are sent in Europe locations" caption-side="top"}
{: #at-table-3}
{: tab-title="Europe"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

## Locations where activity tracking events are sent by {{site.data.keyword.atracker_full_notm}}
{: #atracker-locations}



{{site.data.keyword.en_short}} sends activity tracking events by {{site.data.keyword.atracker_full_notm}} in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where activity tracking events are sent in Americas locations" caption-side="top"}
{: #atracker-table-1}
{: tab-title="Americas"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #atracker-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where activity tracking events are sent in Europe locations" caption-side="top"}
{: #atracker-table-3}
{: tab-title="Europe"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

## Enabling activity tracking events for {{site.data.keyword.en_short}}
{: #at-enable}






As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.en_short}} service in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. Use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. You are also alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) Standard. For more information, see the [getting started tutorial for {{site.data.keyword.at_full_notm}}](/docs/activity-tracker?topic=activity-tracker-getting-started).


## Viewing activity tracking events for {{site.data.keyword.en_short}}
{: #at-viewing}



You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the {{site.data.keyword.en_short}} dashboard
{: #log-launch-integrated}



### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #logevents-launch-standalone}



For information on launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)


## List of platform events
{: #at_actions_platform}



The following table lists the activity tracking event actions that the {{site.data.keyword.cloud_notm}} platform generates {{site.data.keyword.en_short}} instances are processed.

| Action                                   | Description |
|------------------------------------------|---------|
| `event-notifications.instance.create`           | An event is generated when you provision a service instance. |
| `event-notifications.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `event-notifications.instance.delete`           | An event is generated when a service instance is deleted. |
| `event-notifications.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `event-notifications.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Actions that generate platform events" caption-side="bottom"}

The following table lists the actions that generate an event for managing service credentials that are associated with a service instance.

| Action                         | Description |
|--------------------------------|---------|
| `event-notifications.key.create` | An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI. |
| `event-notifications.key.delete` | An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI. |
{: caption="Actions that generate service credentials events" caption-side="bottom"}


## List of management events
{: #at_actions}



| Action             | Description      |
| -------------------| -----------------|
| `event-notifications.topics.read` | An event is generated when a topic is retrieved.|
| `event-notifications.topics.create` | An event is generated when a topic is created. |
| `event-notifications.topics.list` | An event is generated when you retrieve a list of topics.|
| `event-notifications.topics.update` | An event is generated when you update a topic.|
| `event-notifications.topics.delete` | An event is generated when you delete a topic.|
| `event-notifications.destinations.read` | An event is generated when you retrieve a destination.|
| `event-notifications.destinations.create` | An event is generated when you create a destination.|
| `event-notifications.destinations.list` | An event is generated when you retrieve the list of destinations.|
| `event-notifications.destinations.update` | An event is generated when you update a destination.|
| `event-notifications.destinations.delete` | An event is generated when you delete a destination.|
| `event-notifications.sources.read` |An event is generated when you retrieve a source. |
| `event-notifications.sources.create`|An event is generated when you create a source.|
| `event-notifications.sources.list`| An event is generated when you retrieve the list of sources. |
| `event-notifications.sources.update` |An event is generated when you update a source.|
| `event-notifications.sources.delete` | An event is generated when you delete a source. |
| `event-notifications.subscriptions.read` | An event is generated when you retrieve a subscription. |
| `event-notifications.subscriptions.create` | An event is generated when you create a subscription.|
| `event-notifications.subscriptions.list` | An event is generated when you retrieved the list of subscriptions.|
| `event-notifications.subscriptions.update` | An event is generated when you update a subscription.|
| `event-notifications.subscriptions.delete` | An event is generated when you delete a subscription.|
| `event-notifications.smtp_ibm.invite` | An event is generated when an invite is sent for Email subscription.|
| `event-notifications.sms_ibm.invite` | An event is generated when an invite is sent for SMS subscription.|
| `event-notifications.integrations.list` | List all the Key Management Services integrations. |
| `event-notifications.integrations.read` | Get a single Key Management Services integration. |
| `event-notifications.integrations.update` | Update an existing Key Management Services integration. |
| `event-notifications.pre-prod-destination-billing.set` | Set the billing unit for pre-prod destination after crossing the usage in the current unit. |
| `event-notifications.templates.create` | An event is generated when you create a template. |
| `event-notifications.templates.list` | An event is generated when you retrieve the list of templates. |
| `event-notifications.templates.update` | An event is generated when you update a template. |
| `event-notifications.templates.delete` | An event is generated when you delete a template. |
| `event-notifications.templates.read` | An event is generated when you get details of a template. |
{: caption="Actions that generate management events" caption-side="bottom"}

## Viewing events
{: #at_ui}

Events that are generated by {{site.data.keyword.en_short}} are automatically forwarded to the {{site.data.keyword.at_full_notm}} service instance available in the same location.

{{site.data.keyword.at_full_notm}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the same location where your service instance is available.

1. Create a service instance of [{{site.data.keyword.at_full_notm}}](/docs/activity-tracker?topic=activity-tracker-getting-started).
2. [Start the {{site.data.keyword.at_full_notm}} web console](/docs/activity-tracker?topic=activity-tracker-launch) to access your events.

## {{site.data.keyword.en_short}} resources that are deleted or updated as a result of user actions
{: #at_en_del}

Deleting some {{site.data.keyword.en_short}} resources causes associated resources to get deleted. A list of all such actions is as follows:

| EN-resource | Action | Associated resource | Comments |
|------------ |--------|---------------------|----------|
| Source | DELETE | Topics | Topics are updated and filters configured on them deleted. |
| Destination | DELETE | Subscription | All subscriptions that are associated with the deleted destination are deleted |
| Topic | DELETE | Subscription | All subscriptions that are associated with the deleted topic are deleted. |
{: caption="User action initiated update and delete" caption-side="top"}
