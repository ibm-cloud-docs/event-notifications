---

copyright:
  years: 2023
lastupdated: "2023-04-19"

keywords: event-notifications, event notifications, about event notifications, destinations, IBM Cloud Object Storage, cloud object storage, object storage

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cos_full_notm}}
{: #en-destinations-cloud-object-storage}

{{site.data.keyword.cos_full_notm}} is a highly scalable cloud storage service, which is designed for high durability, resiliency, and security. Store, manage, and access your data through the self-service portal and RESTful APIs. The files that are uploaded into {{site.data.keyword.cos_full_notm}} are called **objects**. The uploaded objects are organized into **buckets** that serve as containers for objects.
{: shortdesc}

A {{site.data.keyword.cos_full_notm}} represents a service destination, where an incoming notification can be stored and consumed programmatically to actions.

## Configuring a {{site.data.keyword.cos_full_notm}} destination in the UI
{: #en-destinations-cos-configure}

Before you configure {{site.data.keyword.cos_full_notm}} as a destination, make sure that you have an {{site.data.keyword.cos_full_notm}} instance [created and configured](https://cloud.ibm.com/objectstorage/create) in the same account as your {{site.data.keyword.en_short}} instance. Also you need to have IAM role Manager for {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}}, and [IAM service-to-service authorization](#en-using-s2s-auth1).
{: note}

If you are using {{site.data.keyword.en_short}} CLI or API to configure {{site.data.keyword.cos_full_notm}} service instance as a destination, ensure that you have enabled authorization to grant access between services before integrating with {{site.data.keyword.cos_full_notm}}. For more information, see [Using authorizations to grant access between services](#en-using-s2s-auth1).
{: important}

To configure a {{site.data.keyword.cos_full_notm}} destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add new destination.

1. In the **Add a destination** side panel, provide the following details.

   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination**, for the **Type**, select **{{site.data.keyword.cos_full_notm}}** from the list as your destination type.

   - **Instance name** - Select the {{site.data.keyword.cos_full_notm}} instance name from the list, if you already have an {{site.data.keyword.cos_full_notm}} instance. Otherwise, click the **Click new instance** link, to create an {{site.data.keyword.cos_full_notm}} instance.

      When you are creating a new {{site.data.keyword.cos_full_notm}} instance by **Click new instance** option, the authorization between the services will be created internally between the two services, {{site.data.keyword.en_short}} and {{site.data.keyword.cos_full_notm}}.
      {: note}

   - **Bucket name** - Enter the Bucket name to be used for connecting to the {{site.data.keyword.cos_full_notm}} instance. {{site.data.keyword.en_short}} creates a new object per notification into the {{site.data.keyword.cos_full_notm}} Bucket name. The pattern that {{site.data.keyword.en_short}} uses to name the object is **----Information to come from Pankaj----**.

   - **Endpoint** - Enter the {{site.data.keyword.cos_full_notm}} endpoint URL. For more information, see [Endpoint url]().

1. Click **Add**.

## Using authorizations to grant access between services
{: #en-using-s2s-auth1}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service. Use authorization delegation to automatically create access policies that grant access to dependent services.

### Creating an authorization in the console
{: #en-using-s2s-console}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.
   * If the source service that needs access to the target service is in this account, select **This account**.
   * If the source service that needs access to the target service is in a different account, select **Other account**. Then, enter the **Account ID** of the source account.

1. Select a **Source service** as **Event Notifications**.

1. Specify whether you want the authorization to be for all resources or Resources based on selected attributes. If you selected Resources based on selected attributes, then specify the **Add attributes**: only source resource group or only source service instance.

1. Select a **Target service** as **{{site.data.keyword.cos_full_notm}}**.

1. For the target service, specify whether you want the authorization to be for all instances, only to a specific instance in the account, or instances only in a certain resource group.

1. Select a role to assign access to the source service that accesses the target service.

1. Click **Authorize**.

### Creating an authorization by using the CLI
{: #en-create-auth-cli1}

To authorize a source service to access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all of the parameters that are available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).

## How to find the Endpoint URL of the {{site.data.keyword.cos_full_notm}} service?
{: #en-endpoint-url}

Endpoints are used with your credentials (Bucket name, API Key, SDK) to tell your service where to look for your bucket.

1. Login to your {{site.data.keyword.cloud_notm}} account.

1. Navigate to **Resource List** in the menu.

1. Navigate to **Storage** in the Resource list.

1. Click the {{site.data.keyword.cos_full_notm}} name that will display your {{site.data.keyword.cos_full_notm}} console.

1. In the {{site.data.keyword.cos_full_notm}} console, navigate to **Endpoints**.

1. In the **Endpoints**, **Select resiliency** and **Select location** to narrow down your selection.

1. Navigate to **Legacy Endpoints** section and copy your Global public or private endpoints as required. Use this value as the **Endpoint** in the [Configuring a {{site.data.keyword.cos_full_notm}} destination](#en-destinations-cos-configure) section.
