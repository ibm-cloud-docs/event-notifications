---

copyright:
  years: 2022
lastupdated: "2022-11-30"

keywords: event notifications, Resource lifecycle events

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} Resource lifecycle events
{: #en-resource-lifecycle-events}

{{site.data.keyword.en_short}} service uses the {{site.data.keyword.cloud_notm}} platform for authentication, access, self-service instance creation, metering, and billing.
{: shortdesc}

The {{site.data.keyword.cloud_notm}} provisioning layer manages the lifecycle of {{site.data.keyword.cloud_notm}} resources. A *resource* is anything that you can create from the {{site.data.keyword.cloud_notm}} catalog that is managed by and contained within a resource group.

Resource lifecycle events are events around the {{site.data.keyword.cloud_notm}} resources. For more information, see [Creating resources](https://cloud.ibm.com/docs/account?topic=account-manage_resource&interface=ui){: external}.

Some example of Resource lifecycle events are:

- Creating a resource instance
- Updating a resource instance
- Deleting a resource instance
- Service key credentials updates
- Resource groups updates

## Supported resource types and sub-types
{: #en-supported-resource-types}

1. Service instance type and sub-types

   | Event type | Sub-type    | Description     |
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

   | Event type | Sub-type    | Description     |
   | :--------- | :---------- | :-------------- |
   | `key` | `create` | An event is generated when a service instance credentials are created successfully. |
   | `key` | `create_failure` | An event is generated when a service instance credentials creation failed. |
   | `key` | `delete` | An event is generated when a service instance credentials deleted successfully. |
   | `key` | `delete_failure` | An event is generated when a service instance credentials deletion failed. |
   {: caption="Table 2. Supported key credentials type and sub-types" caption-side="bottom"}

1. Resource Group resources

   | Event type | Sub-type    | Description     |
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

## Event Schema for Resource Lifecycle Events
{: #en-schema-rc-events}

The following table describes the fields of a Resource Lifecycle event:

| Field Name | Type | Description |
|:-----------|:------|:-------------|
| `account_id` | String | The Account ID of the user who initiated the event. |
| `event_id` | String | A unique ID identifying the event on {{site.data.keyword.cloud_notm}}. It is a UUID. |
| `event_type` | String | Identifies the type of event. It can be any of the events specified [here](/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events#en-supported-resource-types). |
| `timestamp` | String | Time when the Event occurred. |
| `context` | Object | This JSON gives the context in which the event occurred. |
| `context.subject_id` | String | The IAM ID of the initiator of the Event. Note below to find your {{site.data.keyword.cloud_notm}} IAM ID. |
| `context.subject_name` | String | The email ID of the initiator of the email. Note below to find your {{site.data.keyword.cloud_notm}} subject_name. |
| `context.activity` | Object | This JSON gives details of the activity performed. |
| `context.activity.action` | String | Identifies the action taken by the user to trigger an event. |
| `context.activity.message` | String | A message describing the event. |
| `context.activity.outcome` | String | Result or outcome of an action. |
| `context.activity.reason_reasonCode` | Number | The response code from the respective resource for the triggered action. |
| `context.activity.target_name` | String | The name of the resource on which the action was triggered. |
| `event_properties` | Object | A JSON object containing the properties of the current event. |
| `event_properties.created_at` | String | The timestamp when the resource was created. |
| `event_properties.created_by` | String | The IAM ID who created the resource. |
| `event_properties.crn` | String | The CRN of the resource. |
| `event_properties.guid` | String | The guid of the resource. |
| `event_properties.name` | String | Name of the resource. |
| `event_properties.resource_group_id` | String | The Resource Group ID. |
| `event_properties.resource_id` | String | The Resource ID. This identifies the type of the resource in the {{site.data.keyword.cloud_notm}} catalog. |
| `event_properties.last_operation` | Object | JSON object identifying the last operation on the resource in question. |
| `event_properties.last_operation.description` | String | A message describing the last operation carried out on the resource. |
| `event_properties.last_operation.state` | String | Final state after the last operation was performed. |
| `event_properties.last_operation.type` | String | Event type of the last operation. |
| `event_properties.region_id` | String | The region of resource for which the action was done. |
| `event_properties.state` | String | The state of the resource after the action. |
| `event_properties.type` | String | The type of the resource: "service_instance" or "resource_instance". |
| `event_properties.restored_at` | String | Timestamp when the resource was restored. Available for restore resource action. |
| `event_properties.restored_by` | String | IAM ID who restored the resource. Available for restore resource action. |
| `event_properties.scheduled_reclaim_at` | String | Timestamp when the resource was reclaimed. Available for reclaim resource action. |
| `event_properties.scheduled_reclaim_by` | String | IAM ID who restored the resource. Available for restore resource action. |
| `event_properties.updated_at` | String | Timestamp which the last update on the resource was done. |
{: caption="Table 4. Event Schma for Resource Lifecycle Events" caption-side="bottom"}

### Example event
{: #en-example-event}

```javascript
{
   "account_id": "abcdef2595f4d598c1725d60fc77",
   "context": {
      "activity": {
         "action": "apprapp.instance.create",
         "message": "App Configuration: create instance App Configuration-0001",
         "outcome": "success",
         "reason_reasonCode": 201,
         "target_name": "App Configuration-0001"
      },
      "subject_id": "IBMid-xxxxxQExx",
      "subject_name": "xyz@ibm.com"
   },
   "event_id": "7ca39870-eb1b-6c50-88b1-48c04123494",
   "event_properties": {
      "created_at": "2022-09-30T16:18:54.926735545Z",
      "created_by": "IBMid-xxxxxQExx",
      "crn": "crn:v1:staging:public:apprapp:us-south:a/abcdf222595g44d598c178525i60jc77:f4fca3f2-fdd3-485e-b86c-1234dd3eabc4::",
      "guid": "a4bcc3f2-dee3-485f-a86b-4818dd3eabc4",
      "last_operation": {
         "description": "Completed create instance operation",
         "state": "succeeded",
         "type": "create"
      },
      "name": "App Configuration-z0",
      "region_id": "us-south",
      "resource_group_id": "ee24533eed37412e988179fe694062bc",
      "resource_id": "apprapp-a6bcce47-d840-45b0-8ab9-ad15354defgea",
      "state": "active",
      "type": "service_instance",
      "updated_at": "2022-09-30T16:18:55.295780335Z"
   },
   "event_type": "resource-controller.instance.create",
   "timestamp": "2022-09-30T16:18:55Z"
}
```
{: codeblock}
