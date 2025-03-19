---

copyright:
  years: 2025
lastupdated: "2025-03-19"

keywords: event-notifications, event notifications, managing service access, iam, account, authorizations, s2s

subcollection: event-notifications


---

{{site.data.keyword.attribute-definition-list}}


# Using authorizations to grant access between services
{: #en-using-s2s-authorization}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service.

## Creating an authorization in the console
{: #en-using-s2s-console}

If the source service that needs access to the target service is in the same account, select **This account**. The service-to-service authorization is created when the integration is created from the console. If the integration is being created by using the API, the users need to create the service-to-service authorization manually.
{: note}

If the source and target services are in different accounts or if the authorization is created manually, follow the steps listed below : 

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** -> **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.

1. Select the **Source service** as **Event Notifications**.

1. Specify whether you want the authorization to be for all resources or Resources based on selected attributes. If you selected Resources based on selected attributes, then specify the **Add attributes**: only source resource group or only source service instance.

1. Select a **Target service**.

1. For the target service, specify whether you want the authorization to be for all instances, only to a specific instance in the account, or instances only in a certain resource group.

1. Select the desired roles to assign access to the source service that accesses the target service.

1. Click **Authorize**.

## Creating an authorization by using the CLI
{: #en-create-auth-cli1}

To authorize a source service to access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all the parameters available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).
