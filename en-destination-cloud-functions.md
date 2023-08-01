---

copyright:
  years: 2022
lastupdated: "2022-12-26"

keywords: event-notifications, event notifications, about event notifications, destinations, IBM Cloud Functions, cloud functions

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}
{: #en-destinations-cloud-functions}

A {{site.data.keyword.openwhisk_short}} represents a service destination, where an incoming notification can be consumed programmatically to actions.
{: shortdesc}

## Generate {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}} endpoint
{: #en-generate-cf-incoming-webhook-url}

To post a {{site.data.keyword.openwhisk_short}} notification, you need to generate an endpoint. To generate the endpoint, follow these steps:

1. Create a [{{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}](https://{DomainName}/functions/create) instance. If you already have an {{site.data.keyword.openwhisk_short}} instance, go to step 3.

1. Create a **Namespace**. For more information, see [here](https://{DomainName}/docs/openwhisk?topic=openwhisk-namespaces#create_iam_namespace).

1. Create an **Action**. For more information, see [here](https://{DomainName}/docs/openwhisk?topic=openwhisk-actions).

1. Select **Endpoints** from the left menu.

   Make sure to uncheck `Enable as Web Action` and `Raw HTTP handling` options in the Web Action section for an effective usage of {{site.data.keyword.openwhisk_short}} as a destination.
   {: note}

1. Copy the URL mentioned and use it in **Destination Configuration** in {{site.data.keyword.en_short}} instance.

## Generate API key for your namespace
{: #en-generate-cf-api-key}

1. From your {{site.data.keyword.cloud_notm}} dashboard, go to **Manage > Access (IAM)**.

1. Select **Service IDs**.

1. Select your namespace.

1. Select **API keys**.

1. Unlock if the API key is locked by going to **Actions > Unlock**.

1. Click **Create** and provide a **Name**. This gives you the apikey for the namespace you selected.

1. Copy **api_key** and use it in **Destination Configuration** in {{site.data.keyword.en_short}} instance.

{{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}} Cloud Foundary based namespace is not supported. Only IAM-based namespace is supported.
{: note}

## Configuring a {{site.data.keyword.openwhisk_short}} destination
{: #en-cf-configure-destination}

You can configure a {{site.data.keyword.openwhisk_short}} destination in the `Destinations` tab.

To configure a {{site.data.keyword.openwhisk_short}} destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add new destination.

1. In the **Add a destination** side panel, provide the following details.

   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination**, for the **Type**, select **{{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}** from the drop-down as your destination type.
   - **URL** - Enter the {{site.data.keyword.openwhisk_short}} incoming webhook URL. This is the URL that you have [generated](#en-generate-cf-incoming-webhook-url) earlier.
   - **API key** - Enter the API key that you have [generated](#en-generate-cf-api-key) earlier.

1. Click **Add**.

## {{site.data.keyword.openwhisk_short}} retry policy
{: #en-cf-retry}

When calling a webhook, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (webhook).

In addition, the following timeout conditions cause the {{site.data.keyword.openwhisk_short}} call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the {{site.data.keyword.openwhisk_short}} webhook URL fails even after retry attempts, the notification is lost.
{: note}
