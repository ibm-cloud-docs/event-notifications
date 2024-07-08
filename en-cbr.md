---

copyright:
  years: 2023
lastupdated: "2024-07-08"

keywords: event-notifications, event notifications, about event notifications, context-based restrictions, access allowlist, network security

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Managing access with context-based restrictions
{: #en-access-control-cbr}

Context-based restrictions give account owners and administrators the ability to define and enforce access restrictions for IBM Cloud® resources based on the context of access requests. Access to IBM Cloud Event Notifications resources can be controlled with context-based restrictions and identity and access management policies.

These restrictions work with traditional IAM policies, which are based on identity, to provide an extra layer of protection. Unlike IAM policies, context-based restrictions don't assign access. Context-based restrictions check that an access request comes from an allowed context that you configure. Since both IAM access and context-based restrictions enforce access, context-based restrictions offer protection even in the face of compromised or mismanaged credentials.

After you set up your {{site.data.keyword.en_short}} service instance, you can manage access by using [context-based restrictions (CBR)](https://cloud.ibm.com/context-based-restrictions/overview){: external}.
{: shortdesc}

Any Activity Tracker or audit log events generated come from the context-based restrictions service, and not IBM Cloud Event Notifications. For more information, see [Monitoring context-based restrictions](/docs/account?topic=account-cbr-monitor).

## How IBM Cloud Event Notifications Service integrates with context-based restrictions
{: #en-manage-cbr-settings}

With [context-based restrictions](/docs/account?topic=account-context-restrictions-whatis), you can define and enforce user and service access restrictions to {{site.data.keyword.en_short}} resources based on specified criteria. These resources include Internet Protocol (IP) addresses that are linked to your {{site.data.keyword.en_short}} instance.

To restrict access, you must be the account owner or have an access policy with the administrator role on all account management services.
{: note}

You can create context-based restrictions (CBR) for IBM Cloud Event Notifications Service resources or for specific APIs. With Context-based restrictions, you can protect the following resources.

**Protect IBM Cloud Event Notifications service resources**

Restrict access to resource groups, regions, or instances.

**Protect specific APIs**

Restrict access to the resources of Event Notifications by applying CBR on Control Plane APIs or restrict access to the SMTP interface connection.

### Protecting cluster resources
{: #en-manage-cbr-cluster-resources}

You can create CBR rules on resource groups, regions, or instances.

**Regions**

Protects IBM Cloud Event Notifications Service resources in a specific region. If you select a region in your CBR rule, then only traffic from resources in the network zones that you associate with the rule can interact with resources in that region.

If you use the CLI, you can specify the `--region REGION` option to protect resources in a specific region.

If you use the API, you can specify `"name": "region","value": "REGION"` field in the resource attributes.

**Resource group**

Protects IBM Cloud Event Notifications Service resources in a specific resource group.

If you use the CLI, you can specify the -`-resource-group-id RESOURCE-GROUP-ID` option to protect resources in a specific resource group.

If you use the API, you can specify `"name": "resourceGroupId","value": "RESOURCE-GROUP-ID"` field in the resource attributes.

**Instances**

Protects specific instances of IBM Cloud Event Notifications Service.

If you use the CLI, you can specify the -`-service-instance INSTANCE-ID` option to protect a specific instance

If you use the API, you can specify `"name": "serviceInstance","value": "INSTANCE-ID"` field in the resource attributes.

### Protecting specific APIs
{: #en-manage-cbr-apis}

You can create CBR rules to protect the following API types for IBM Cloud Event Notifications.

**Control plane APIs**

Protects access to the APIs of the service, such as the APIs for doing CRUD operations on all the available entities in Event Notifications such as sources, topics, subscriptions and more. Also, it protects access while sending notifications and Push Destinations APIs as well. Full list of APIs is mentioned [here](https://cloud.ibm.com/apidocs/event-notifications).

If you select the cluster control plane APIs in your CBR rule, then only traffic from resources in the network zones that associate with that rule can interact with the cluster control plane APIs. All other requests are blocked.

If you use the CLI, you can specify the `--api-types` option and the `crn:v1:bluemix:public:context-based-restrictions::::api-type:control-plane` type.

If you use the API, you can specify `"api_type_id": "crn:v1:bluemix:public:context-based-restrictions::::api-type:control-plane"` in the `"operations"` spec.

**SMTP Configuration**

Protects access to the [SMTP interface](https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-smtp-configurations). If you select the SMTP configuration in your CBR rule, then only traffic from resources in the network zones that associate with that rule can interact with the SMTP configuration. All other requests are blocked. Since SMTP interface works based on username-password pair over the direct connectivity to the cluster, setting up CBR rule is mandatory for this functionality.

If you use the CLI, you can specify the `--api-types` option and the `crn:v1:bluemix:public:event-notifications-dev::::api-type:smtp-configuration` type.

If you use the API, you can specify `"api_type_id": "crn:v1:bluemix:public:event-notifications-dev::::api-type:smtp-configuration"` in the `"operations"` spec.

## Overview
{: #en-cbr-overview}

To restrict access, you must create [zones](/docs/account?topic=account-context-restrictions-create&interface=ui#network-zones-create) and [rules](/docs/account?topic=account-context-restrictions-create&interface=ui#context-restrictions-create-rules).

First, create a zone with the appropriate details for network or resource definitions. Then, attach that zone to the specified resource to restrict access. You can create zones and rules by using a ReSTful [API](/apidocs/context-based-restrictions#introduction) or with [context-based restrictions](https://cloud.ibm.com/context-based-restrictions/overview){: external}. After you create or update a zone or a rule, it might take a few minutes for the change to take effect.

CBR rules do not apply to provisioning or deprovision processes.
{: note}

## Understanding network zones
{: #en-cbr-network-zones}

By creating network zones, you can define an allowlist of network locations where access requests originate, to determine when a rule can be applied. The list of network locations can be specified by using IP addresses, such as individual addresses, ranges or subnets, and Virtual Private Cloud (VPC) IDs.

After you create a network zone, you can add it to a rule.

### Creating network zones by using the CBR API
{: #en-cbr-create-zones-api}

The API supports defining [network zones](/apidocs/context-based-restrictions#introduction) by connecting to public (for example, cbr.cloud.ibm.com) and private endpoints (for example, private.cbr.cloud.ibm.com).

Use `GET /v1/zones` to list the zones. By using `POST /v1/zones`, you can create a new zone with the appropriate information. For more information, including a request body example, see [Creating network zones by using the API](/docs/account?topic=account-context-restrictions-create&interface=api#network-zones-create-api).

You can determine which services are available by checking for [reference targets](/apidocs/context-based-restrictions#list-available-serviceref-targets).
{: note}

After you create zones, you can [update](/apidocs/context-based-restrictions#replace-zone) or [delete](/docs/account?topic=account-context-restrictions-remove&interface=ui) them.

### Creating network zones by using the CBR UI
{: #en-cbr-create-zone-ui}

After you set the prerequisites and requirements, you can create zones in the UI. For more information about the steps to follow, see [Creating context-based restrictions](/docs/account?topic=account-context-restrictions-create&interface=ui#network-zones-create).

Instead of creating a zone by using UI inputs, you can use the JSON code form to create a zone by clicking **Enter as JSON code**.
{: note}

After you create zones, you can also [update](/apidocs/context-based-restrictions#replace-zone) and [delete](/docs/account?topic=account-context-restrictions-remove&interface=ui) them.

## Understanding network rules
{: #en-cbr-network-rules}

After you create your zones, you can attach the zones to your network resources by creating rules. When you add resources to a rule, you can choose from the available [types of endpoints](/docs/account?topic=account-context-restrictions-whatis#context-restrictions-endpint-type) that are specific to your network topology.

### Create network rules by using the CBR API
{: #en-cbr-create-rules-api}

You can define network rules with the API by using the information that you collected from creating network zones.

By using `GET /v1/rules` with the endpoints that you chose, you can view a list of current rules. Use `POST /v1/rules` to create new rules. For more information, including a request body example, see [Creating rules by using the API](/docs/account?topic=account-context-restrictions-create&interface=api#context-restrictions-create-rules-api).

After you create rules, you can [update](/apidocs/context-based-restrictions#replace-rule) and [delete](/apidocs/context-based-restrictions#delete-rule) them.

### Creating network rules by using the CBR UI
{: #en-cbr-create-rules-ui}

After you set the prerequisites and requirements, you can create zones in the UI. For more information about the steps to follow, see [Creating context-based restrictions](/docs/account?topic=account-context-restrictions-create&interface=ui#network-zones-create).

You can use the CBR UI to [add resources and contexts](/docs/account?topic=account-context-restrictions-create&interface=ui#context-restrictions-create-rules) to your network rules. Keep in mind the limitations.

For example, when you create context-based restrictions for the IAM Access Groups service, users who don't satisfy the rule can't view any groups in the account, including the public access group.

Unlike IAM policies, context-based restrictions don't assign access. Context-based restrictions check that an access request comes from an allowed context that you configure. Also, the rules might not take effect immediately due to synchronization and resource availability.
{: important}

After you create rules, you can [update](/apidocs/context-based-restrictions#replace-rule) and [delete](/apidocs/context-based-restrictions#delete-rule) them.

## Next steps
{: #en-cbr-next-steps}

You must follow the creation or modification of zones or rules with adequate testing to ensure access and availability.

Users who attempt to access your resources outside of the defined zones receive `HTTP error 403` when the appropriate rules are not established.
{: note}
