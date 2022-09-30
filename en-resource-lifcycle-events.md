---

copyright:
  years: 2022
lastupdated: "2022-09-30"

keywords: event notifications, Resource lifecycle events

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} Resource lifecycle events
{: #en-resource-lifecycle-events}

{{site.data.keyword.en_short}} service uses the {{site.data.keyword.cloud_notm}} platform for authentication, access, self-service instance creation, metering, and billing.
{: shortdesc}

The {{site.data.keyword.cloud_notm}} provisioning layer manages the lifecycle of {{site.data.keyword.cloud_notm}} resources. A *resource* is anything that you can create from the {{site.data.keyword.cloud_notm}} catalog that is managed by and contained within a resource group.

Resource lifecycle events are events around the {{site.data.keyword.cloud_notm}} resources. For more information, see [Creating reources](https://cloud.ibm.com/docs/account?topic=account-manage_resource&interface=ui){: external}.

Some example of Resource lifecycle events are:

- Creating a resource instance
- Updating a resource instance
- Deleting a resource instance
- Service key credentials updates
- Resource groups updates

## Supported resource types and sub-types
{: #en-supported-resource-types}

1. Service instance type and sub-types

   | Event type | sub-type    | Description     |
   | :--------- | :---------- | :-------------- |
   | `instance` | `apply_promo_code` | An event created when a promo code is applied. |
   | `instance` | `create` | An event is generated when you provision a service instance. |
   | `instance` | `create_failure` | An event is generated when a service instance creation failed. |
   | `instance` | `create_inprogress` | An event is generated when a service instance creation is in progress. |
   | `instance` | `delete` | An event is generated when a service instance deleted. |
   | `instance` | `delete_failure` | An event is generated when a service instance deletion failed. |
   | `instance` | `delete_inprogress` | An event is generated when a service instance deletion is in progress. |
   | `instance` | `restore` | An event is generated when a service instance restored after deletion within reclamation period. |
   | `instance` | `schedule_reclaim` | An event is generated when a service instance scheduled for reclaim after deletion. |
   | `instance` | `update` | An event is generated when a service instance get updated. |
   | `instance` | `update_failure` | An event is generated when a service instance updation failed. |
   | `instance` | `update_inprogress` | An event is generated when a service instance updation is in progress. |
   | `instance` | `update_plan` | An event is generated when a service instance plan get updated. |
   | `instance` | `update_plan_failure` | An event is generated when a service instance plan updation failed. |
   | `instance` | `update_plan_inprogress` | An event is generated when a service instance plan updation is in progress. |
   | `instance` | `update_state` | An event is generated when a service instance state get updated. |
   | `instance` | `update_state_failure` | An event is generated when a service instance state updation failed. |
   {: caption="Table 1. Supported service instance type and sub-types" caption-side="bottom"}

1. Service key type resources

   | Event type | sub-type    | Description     |
   | :--------- | :---------- | :-------------- |
   | `key` | `create` | An event is generated when a service instance credentials are created successfully. |
   | `key` | `create_failure` | An event is generated when a service instance credentials creation failed. |
   | `key` | `delete` | An event is generated when a service instance credentials deleted successfully. |
   | `key` | `delete_failure` | An event is generated when a service instance credentials deletion failed. |
   {: caption="Table 2. Supported key credentials type and sub-types" caption-side="bottom"}

1. Resource Group resources

   | Event type | sub-type    | Description     |
   | :--------- | :---------- | :-------------- |
   | `Resource_group` | `create` | An event is generated when a resource group get created. |
   | `Resource_group` | `delete` | An event is generated when a resource group get deleted. |
   | `Resource_group` | `update` | An event is generated when a resource group get updated. |
   {: caption="Table 3. Supported resource group type and sub-types" caption-side="bottom"}

## Enabling resource lifecycle events
{: #en-enabling-resource-lifecycle-events}

{{site.data.keyword.cloud_notm}} Resource lifecycle events is a pre-defined source which publishes resource lifecycle events from {{site.data.keyword.cloud_notm}}. {{site.data.keyword.cloud_notm}} Resource lifecycle events is *Disabled* by default. You can go to the **Sources** page and enable it by using the toggle switch.

After enabling the source, you can publish the lifecycle events to the [Topic](/docs/event-notifications?topic=event-notifications-en-overview#en-topics) of your choice.

To learn more about working with **Topics**, see [here](/docs/event-notifications?topic=event-notifications-en-create-en-topic).
