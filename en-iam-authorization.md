---

copyright:
  years: 2025
lastupdated: "2025-04-14"

keywords: event-notifications, event notifications, managing service access, iam, account, authorizations, s2s

subcollection: event-notifications


---

{{site.data.keyword.attribute-definition-list}}


# Authorizing Event Notifications to access other services
{: #en-using-s2s-authorization}{: ui}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service. You must grant {{site.data.keyword.en_short}} the appropriate IAM service to service access for it to be able to send notifications and alerts to the various available destinations. You can find the list of available destinations [here](/docs/event-notifications?topic=event-notifications-en-destination).

If the source service that needs access to the target service is in the same account, select **This account**. The service-to-service authorization is created when the integration is created from the console. If the integration is being created by using the API, the users need to create the service-to-service authorization manually.
{: note}

## Creating an authorization in the console
{: #en-using-s2s-console}

If the source and target services are in different accounts or if the authorization is created manually, complete the following steps: 

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.

1. Select the **Source service** as **Event Notifications**.

1. Specify whether you want to authorize all {{site.data.keyword.en_short}} resources, specific resource group, resource ID, or a service instance. If you select specific resource group, resource ID, or a service instance you need specify the resource group,resource ID or service instance under **Add a condition**.

1. Select a **Target service**.

1. For the target service, specify whether you want to give {{site.data.keyword.en_short}} access to all resources of the target, only to a specific resource group, a region, a service instance, a resource type or a resource ID. 

1. Select the appropriate roles to grant {{site.data.keyword.en_short}} access to the target service.

1. Click **Authorize**.


# Creating an authorization by using the CLI
{: #en-create-auth-cli1}{: cli}

To authorize a source service to access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all the parameters available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).
