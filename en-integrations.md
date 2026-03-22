---

copyright:
  years:  2022, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event notification, notifications, integrations, key protect, key management, Collect Failed events

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Integrating {{site.data.keyword.en_short}} with other {{site.data.keyword.cloud_notm}} services
{: #en-integrations}

Integrations in {{site.data.keyword.en_short}} represent a list of other {{site.data.keyword.cloud_notm}} services that are connected to your {{site.data.keyword.en_short}} instance. You can encrypt the data that you store in {{site.data.keyword.cloud_notm}} databases by using encryption keys that you can control. For more information, see [Integrating with Key Protect](#en-int-key-management). You can also collect failed events and take appropriate action. For more information, see [Collecting failed events](/docs/event-notifications?topic=event-notifications-en-cfe-integrations).
{: shortdesc}

## Integrating with Key Protect
{: #en-int-key-management}

You can use customer-managed encryption keys through {{site.data.keyword.keymanagementservicelong_notm}} to encrypt your databases and backups with one of your own keys. {{site.data.keyword.keymanagementserviceshort}} is available in two deployment options:

- **Key Protect Multi-Tenant (BYOK):** A shared key management service that provides FIPS 140-2 Level 3 certified cloud-based hardware security modules (HSMs) for key protection. This option provides Bring Your Own Key (BYOK) capability.
- **Key Protect Dedicated (KYOK):** A single-tenant key management service that provides dedicated FIPS 140-2 Level 3 certified HSMs with exclusive control over your encryption keys. This option provides Keep Your Own Key (KYOK) capability for enhanced security and compliance.

Both Key Protect deployment options are suitable alternatives to Hyper Protect Crypto Services (HPCS), which is being deprecated.
{: note}

BYOK and KYOK capabilities are supported only for {{site.data.keyword.en_short}} Standard plan.
{: important}

For more information, see [Managing encryption](/docs/event-notifications?topic=event-notifications-en-managing-encryption).

If you are using {{site.data.keyword.en_short}} CLI or API to integrate with Key Protect, ensure that you have enabled authorization to grant access between services before integrating. For more information, see [Using authorizations to grant access between services](#en-using-auth-access-between-services).
{: important}

You can create and bring keys that are created by using {{site.data.keyword.keymanagementserviceshort}}. To get started, you need [{{site.data.keyword.keymanagementserviceshort}}](/catalog/services/key-protect){: external} provisioned on your {{site.data.keyword.cloud_notm}} account. You can choose either the Multi-Tenant or Dedicated deployment option based on your security and compliance requirements. For more information, see [Provisioning a Key Protect instance](/docs/key-protect?topic=key-protect-provision){: external}.

1. From your {{site.data.keyword.en_short}} service instance dashboard, click **Integrations**. By default, a Key Protect entry is listed that can be edited to configure the **Key Management** option, connecting to your {{site.data.keyword.en_short}} instance.

1. From the overflow menu of the default entry, click **Edit**. This displays the **Key Management** side panel.

1. For the **Instance**, select one of these options:
   - **Create a new instance** - Create a new instance of Key Protect. This takes you to the Key Protect provisioning page.
   - **Choose existing instance** - Select this option if you already have a {{site.data.keyword.keymanagementserviceshort}} instance. Select the **Service** instance and **Root key** from the drop-down list.

1. Click **Save** to apply the changes.

The updated **Key Management** information is listed in the **Integrations** dashboard.

By default, customer data is encrypted. You can use APIs, CLI, or the user interface to provide your own Key Protect details for data encryption. If you are using CLI or APIs, you need to get the default Key Protect integration ID through the [List all integrations](/apidocs/event-notifications#list-integrations) API. In case of default Key Protect integrations, except for the integration ID, all other values are empty. You need to use the integration ID to update the integration details with your own Key Protect details.
{: note}

## Using authorizations to grant access between services
{: #en-using-auth-access-between-services}

Use {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service. Use authorization delegation to automatically create access policies that grant access to dependent services.

### Creating an authorization in the console
{: #en-create-auth-console}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.
   * If the source service that needs access to the target service is in this account, select **This account**.
   * If the source service that needs access to the target service is in a different account, select **Other account**. Then, enter the **Account ID** of the source account.

1. Select a **Source service** as **Event Notifications**.

1. Specify whether you want the authorization to be for all resources or Resources based on selected attributes, If you selected Resources based on selected attributes, then specify the **Add attributes** only source resource group or only source service instance.

1. Select **Key Protect** as the **Target service**.

1. For the target service, specify whether you want the authorization to be for all instances, only a specific instance in the account, or instances only in a certain resource group.

1. Select a role to assign access to the source service that accesses the target service.

1. Click **Authorize**.

### Creating an authorization by using the CLI
{: #en-create-auth-cli}

To authorize a source service access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all of the parameters that are available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).
