---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-18"

keywords: app-configuration, app configuration, managing service access, iam, account

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

# Managing service access
{: #ac-service-access-management}

{{site.data.keyword.appconfig_short}} uses {{site.data.keyword.iamlong}} (IAM) to perform authorization and authentication.
{: shortdesc}

Access to {{site.data.keyword.appconfig_short}} service instances for users in your account is controlled by {{site.data.keyword.iamlong}} (IAM). Every user in your account, who needs access to {{site.data.keyword.appconfig_short}}, must be assigned with an IAM role with specific access policy. The access policy determines what actions a user can perform within the context of the service or instance that you select. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles.

Policies help you to grant access at different levels. Some of the options are,
- Access across all instances of the service in your account.
- Access to an individual service instance in your account.
- Access to a specific resource within an instance.

## Roles and permissions
{: #ac-roles-permissions}

With {{site.data.keyword.cloud_notm}} IAM, you can manage and define access for users and resources in your account. {{site.data.keyword.appconfig_short}} service aligns with {{site.data.keyword.cloud_notm}} IAM roles so that each user has a different view of the service, according to the role assigned. 

*Roles* define the actions that a user or service ID can run. There are different types of roles in the  {{site.data.keyword.cloud_notm}}:

-	*Platform management roles* enable users to perform tasks on service resources at the platform level, for example assign user access for the service, create or delete service IDs, create instances, assign policies for your service to other users, and bind instances to applications.
-	*Service access roles* enable users to be assigned varying levels of permission for calling the service's API.

{{site.data.keyword.appconfig_short}} uses both the **Platform and Service management roles**. You can set policies about who can create a instance at the platform level, and then use the service roles to manage interaction with the instance itself. As the creator of a instance, you do not need to set any IAM policies to view or work with your {{site.data.keyword.appconfig_short}} entities.

For complete IAM documentation, see [Managing access](/docs/account?topic=account-cloudaccess) in {{site.data.keyword.cloud_notm}}.
{: note}

Review the platform and service roles available and the actions that are mapped to each to help you assign access. If you're using the API to assign access, use `apprapp` for the service name.

| Role | Description |
| ----- | :----- |
| Viewer | As a viewer, you can view service instances, but you can't modify them. |
| Administrator | As an administrator, you can perform all platform actions based on the resource this role is being assigned, including assigning access policies to other users. |
| Operator | As an operator, you can perform platform actions that are required to configure and operate service instances, such as viewing a service's dashboard. |
| Editor | As an editor, you can perform all platform actions except for managing the account and assigning access policies. |
{: row-headers}
{: caption="Table 2. Platform roles - {{site.data.keyword.appconfig_short}}" caption-side="top"}
{: #platform-roles-table1}
{: tab-title="Platform roles"}
{: tab-group="app-rapp"}
{: class="simple-tab-table"}
{: summary="Use the tab buttons to change the context of the table. This table has row and column headers. The row headers provide the platform role name and the column headers identify the specific information available about each role."}

| Role | Description |
| ----- | :----- |
| Manager | As a manager, you haver permissions beyond the writer role to complete privileged actions as defined by the service. In addition, you can create and edit service-specific resources. |
| Reader | As a reader, you can perform read-only actions within a service such as viewing service-specific resources. |
| Writer | As a writer, you have permissions beyond the reader role, including creating and editing service-specific resources. |
| Config Operator | As a Config Operator, you can toggle the feature state. |
{: row-headers}
{: caption="Table 2. Service roles - {{site.data.keyword.appconfig_short}}" caption-side="top"}
{: #service-roles-table1}
{: tab-title="Service roles"}
{: tab-group="app-rapp"}
{: class="simple-tab-table"}
{: summary="Use the tab buttons to change the context of the table. This table has row and column headers. The row headers provide the service role name and the column headers identify the specific information available about each role."}

| ID | Roles | Description |
| ----- | :----- | :----- |
| `apprapp.dashboard.view` | Manager, Reader, Writer, Operator, Administrator, Editor, Config Operator | View {{site.data.keyword.appconfig_short}} dashboard |
| `apprapp.collections.list` | Manager, Reader, Writer, Administrator, Config Operator | Get list of collection. |
| `apprapp.collections.create` | Manager, Administrator | Create a collection. |
| `apprapp.collections.update` | Manager, Administrator | Update the collection name, tags, and description. |
| `apprapp.collections.delete` | Manager, Administrator | Delete the collection. |
| `apprapp.environments.create` | Manager, Administrator | Create an environment. |
| `apprapp.environments.update` | Manager, Administrator | Update an environment. |
| `apprapp.environements.delete` | Manager, Administrator | Delete an environment. |
| `apprapp.environments.list` | Manager, Reader, Writer, Config Operator | Get list of environments. |
| `apprapp.features.list` | Manager, Reader, Writer, Administrator, Config Operator | Get list of feature flags. |
| `apprapp.features.create` | Manager, Administrator | Create a feature flag. |
| `apprapp.features.update` | Manager, Administrator | Update a feature flag. |
| `apprapp.features.delete` | Manager, Administrator | Delete a feature flag. |
| `apprapp.segments.list` | Manager, Reader, Writer, Administrator, Config Operator | Get list of segments. |
| `apprapp.segments.update` | Manager, Writer, Administrator | Update the segments. |
| `apprapp.segments.create` | Manager, Writer, Administrator | Create a segment of users. |
| `apprapp.segments.delete` | Manager, Writer, Administrator | Delete a segment. |
| `apprapp.features.patch` | Writer | Update a feature flag. |
| `apprapp.features.toggle` | Manager, Writer, Administrator, Config Operator | Toggle a feature flag |
| `apprapp.properties.list` | Manager, Reader, Writer, Config Operator | Get list of properties. |
| `apprapp.properties.update` | Manager, Administrator | Update a property. |
| `apprapp.properties.create` | Manager, Administrator | Create a property. |
| `apprapp.properties.delete` | Manager, Administrator | Delete a property. |
| `apprapp.properties.patch` | Writer | Update a property. |
{: caption="Table 2. Service actions - {{site.data.keyword.appconfig_short}}" caption-side="top"}
{: #actions-table1}
{: tab-title="Actions"}
{: tab-group="app-rapp"}
{: class="simple-tab-table"}
{: summary="Use the tab buttons to change the context of the table. This table provides the available actions for the service, descriptions of each, and the roles that each action is mapped to."}
