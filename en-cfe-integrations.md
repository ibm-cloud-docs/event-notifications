---

copyright:
  years:  2023, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event notification, notifications, integrations, collect failed events

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Collecting failed events
{: #en-cfe-integrations}

As part of the Integrations in {{site.data.keyword.en_short}}, you can enable collecting failed events and take appropriate action.
{: shortdesc}

Collect failed events helps you to identify which messages have failed and can take remedial action.

When a message fails to be delivered a set number of times, the failed message ends up in a {{site.data.keyword.cos_full_notm}} bucket. You can able to identify the subscription or topic to which that failed message belongs and take further action, if required.

Before you enable collecting failed events in **Destinations**, make sure that you have an {{site.data.keyword.cos_full_notm}} instance [created and configured](https://{DomainName}/objectstorage/create) in the same account as your {{site.data.keyword.en_short}} instance.
{: note}

If you are using {{site.data.keyword.en_short}} CLI or API to configure {{site.data.keyword.cos_full_notm}} service instance, ensure that you have enabled authorization to grant access between services before integrating with {{site.data.keyword.cos_full_notm}}. For more information, see [Using authorizations to grant access between services](#en-using-s2s-auth2).
{: important}

If you want to enforce access restrictions based on IP addresses, it is recommended to use context-based restrictions instead of a legacy bucket firewall.  For details, see [Restricting access by network context](/docs/cloud-object-storage?topic=cloud-object-storage-setting-a-firewall) in the Object Storage documentation.  If your setup must continue use of a legacy firewall, use the [Support Center](/unifiedsupport/supportcenter){: external} to create a support case for assistance with the IP range information.
{: note}

To configure and collect failed events, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Integrations**. By default, Key Management and Collect Failed Events tile will be displayed.

1. Click **Connect** in the **Collect Failed Events** tile. The **Collect Failed Events** side panel displays.

1. **Instance name** - Select the {{site.data.keyword.cos_full_notm}} instance name from the list, if you already have an {{site.data.keyword.cos_full_notm}} instance. Otherwise, click the **Create new instance** link, to create an {{site.data.keyword.cos_full_notm}} instance.

   When you select an {{site.data.keyword.cos_full_notm}} instance, the authorization between the services will be created internally between the two service instances, if the authorization between the services doesn't exist.
   {: note}

1. **Bucket name** - Enter the Bucket name to be used for storing the failed events.

   You can get the bucket name from your {{site.data.keyword.cos_full_notm}} instance. For more information, see [Bucket name](#en-cos-bucket-name2).

   The pattern (is a combination of destination name and notification ID) that {{site.data.keyword.en_short}} uses to store the object in {{site.data.keyword.cos_full_notm}} bucket is similar to the following example :

   `Rhonda Macejkovic/013f87bc-0537-4dad-8511-8cb054890ffc.json`,

   where `Rhonda Macejkovic` is destination name and `013f87bc-0537-4dad-8511-8cb054890ffc` is notification ID. `.json` is the payload format.

1. **Endpoint** - Enter the {{site.data.keyword.cos_full_notm}} endpoint URL. For more information, see [Endpoint url](#en-endpoint-url2).

1. Click **Save**.

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click the toggle switch to **ON** status under the **Collect failed events** column for the destination for which you want to collect the failed events. A success message is displayed for switching ON for collecting failed events for the selected destination.

## Available list of destinations for collecting failed events
{: #en-collect-failedevents-destinationslist}

The following destinations can collect failed events:

* [Email Destinations](/docs/event-notifications?topic=event-notifications-en-destinations-email)
   * [Inbuilt Email](/docs/event-notifications?topic=event-notifications-en-destination-email-destination-default)
   * [Custom Domain Email](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email)
* [SMS Destinations](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
   * [Inbuilt SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
   * [Custom SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms-custom)
* [Webhook](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
* [Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack)
* [MSTeams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams)
* [PagerDuty](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty)
* [ServiceNow](/docs/event-notifications?topic=event-notifications-en-destinations-servicenow)
* [CodeEngine](/docs/event-notifications?topic=event-notifications-en-destinations-codeengine)
* [IBM Cloud Object Storage](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-object-storage)
* Push Notifications
   * [Android Push Notifications(FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
   * [iOS Push Notifications(APN's)](/docs/event-notifications?topic=event-notifications-en-push-apns)
   * [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
   * [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
   * [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)
   * [Huawei Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-huawei)


After configuration and enabling collecting of failed events for a destination, the failed events gets added to the {{site.data.keyword.cos_full_notm}} bucket. You can take further action on the failed events as per your requirements.

If you disconnect **Collect Failed Events** from the **Integrations** > **Collect Failed Events** overflow menu option, then all the destinations that are enabled to collect the failed events, will be switched to **OFF** state.
{: note}

## Using authorizations to grant access between services
{: #en-using-s2s-auth2}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service.

### Creating an authorization in the console
{: #en-using-s2s-console2}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.
   * If the source service that needs access to the target service is in this account, select **This account**.

1. Select a **Source service** as **Event Notifications**.

1. Specify whether you want the authorization to be for all resources or Resources based on selected attributes. If you selected Resources based on selected attributes, then specify the **Add attributes**: only source resource group or only source service instance.

1. Select a **Target service** as **{{site.data.keyword.cos_full_notm}}**.

1. For the target service, specify whether you want the authorization to be for all instances, only to a specific instance in the account, or instances only in a certain resource group.

1. Select both the roles (Reader, and Object Writer) to assign access to the source service that accesses the target service.

   If you have selected only one of these two roles (Reader or Object Writer) during the service to service authorization, you cannot write or read from the {{site.data.keyword.cos_full_notm}} bucket. You will get an error for service to service authorization failure in these cases. Make sure to recreate an authorization between the services with both the roles selected.
   {: important}

1. Click **Authorize**.

### Creating an authorization by using the CLI
{: #en-create-auth-cli2}

To authorize a source service to access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all of the parameters that are available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).

## How to find the Bucket name in the {{site.data.keyword.cos_full_notm}} service instance?
{: #en-cos-bucket-name2}

1. Login to your {{site.data.keyword.cloud_notm}} account.

1. Navigate to **Resource List** in the menu.

1. Navigate to **Storage** in the Resource list.

1. Click the {{site.data.keyword.cos_full_notm}} name that will display your {{site.data.keyword.cos_full_notm}} console.

1. In the {{site.data.keyword.cos_full_notm}} console, navigate to **Buckets**.

1. Select and copy the required Bucket name. Use this copied Bucket name in the **Collect Failed Events** screen.

## How to find the Endpoint URL of the {{site.data.keyword.cos_full_notm}} service instance?
{: #en-endpoint-url2}

Endpoints are used with your credentials (Bucket name, API Key, SDK) to tell your service where to look for your bucket.

`private` {{site.data.keyword.cos_full_notm}} endpoints will not be supported for new integrations, since {{site.data.keyword.en_short}} now uses VPC network. It is recommended to use `direct` {{site.data.keyword.cos_full_notm}} endpoints while creating new integrations. Existing integrations over `private` endpoints will continue to work.
{: note}

1. Login to your {{site.data.keyword.cloud_notm}} account.

1. Navigate to **Resource List** in the menu.

1. Navigate to **Storage** in the Resource list.

1. Click the {{site.data.keyword.cos_full_notm}} name that will display your {{site.data.keyword.cos_full_notm}} console.

1. In the {{site.data.keyword.cos_full_notm}} console, navigate to **Buckets** in the menu.

1. Click the required **Bucket name** to view the **Bucket configuration** details.

1. Navigate to **Endpoints** section and copy your public or private endpoints as required.
