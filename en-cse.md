---

copyright:
  years: 2022
lastupdated: "2022-10-26"

keywords: event-notifications, event notifications, about event notifications, service endpoints for {{site.data.keyword.en_short}}, network isolation in {{site.data.keyword.en_short}}

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Using service endpoints to privately connect to {{site.data.keyword.en_short}}
{: #en-service-connection}

To ensure that you have enhanced control and security over your data when you use {{site.data.keyword.en_short}}, you have the option of using private routes to {{site.data.keyword.cloud}} service endpoints. Private routes are not accessible or reachable over the internet. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data from threats from the public network and logically extend your private network.
{: shortdesc}

## Before you begin
{: #en-prereq-service-endpoint}

You must first enable virtual routing and forwarding in your account, and then you can enable the use of {{site.data.keyword.cloud_notm}} private service endpoints. For more information about setting up your account to support the private connectivity option, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

Keep in mind the following considerations:

- You can select a service endpoint option for a {{site.data.keyword.en_short}} instance only at its creation.
- The {{site.data.keyword.en_short}} service UI is not accessible for **Private only** instances.

## Setting up private endpoints for {{site.data.keyword.en_short}} in the UI
{: #en-endpoint-setup-ui}

After your account is enabled for VRF and service endpoints, you can provision a {{site.data.keyword.en_short}} service instance to connect over a private service endpoint.

1. In the {{site.data.keyword.cloud_notm}} console, go to the [{{site.data.keyword.en_short}} offering details page](/catalog/services/event-notifications){: external}.

1. In the **Create** tab, select the location that represents the geographic area (**Region**) where you want to provision your instance. Currently, Dallas (`us-south`), London (`eu-gb`), Frankfurt (`eu-de`), and Sydney (`au-syd`) region is supported.

1. **Select a pricing plan** - Based on your business requirements, select a pricing plan: Lite, and Standard.

1. Configure your resource by providing a **Service name** for your instance, or use the preset name.

1. **Select a resource group** - The resource group selection helps how you want resources to be organized in your account. The resource group that you select cannot be changed after the service instance is created.

1. Optionally, define **Tags** to help you to identify and organize the instance in your account. If your tags are billing related, consider writing tags as *key:value* pairs to help group-related tags, such as `costctr:124`.

1. Optionally, define **Access management tags** that are required to apply flexible access policies on specific resources. For example, `access:dev, proj:version-1`.

1. For the **Service endpoints**, from the list of endpoint options, select **Both public & private network**.

   By default, {{site.data.keyword.en_short}} instances accept API requests from both public and private endpoints.
   {: note}

1. Accept the licensing agreements and terms by clicking the checkbox.

1. Click **Create**. A new service instance is created and the {{site.data.keyword.en_short}} console displayed.

## Viewing your endpoint URLs
{: #en-viewing-endpoint-ui}

The service endpoint URLs are different for private and public network connections. For more information about your service endpoint URLs, see [Regions and endpoints](/docs/event-notifications?topic=event-notifications-en-regions-endpoints).
