---

copyright:
  years: 2023
lastupdated: "2023-04-18"

keywords: event-notifications, event notifications, about event notifications, destinations, IBM Cloud Object Storage, cloud object storage, object storage

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cos_full_notm}}
{: #en-destinations-cloud-object-storage}

{{site.data.keyword.cos_full_notm}} is a highly scalable cloud storage service, which is designed for high durability, resiliency, and security. Store, manage, and access your data through the self-service portal and RESTful APIs. The files that are uploaded into {{site.data.keyword.cos_full_notm}} are called **objects**. The uploaded objects are organized into **buckets** that serve as containers for objects.
{: shortdesc}

A {{site.data.keyword.cos_full_notm}} represents a service destination, where an incoming notification can be stored and consumed programmatically to actions.

Make sure that you have an {{site.data.keyword.cos_full_notm}} instance is [created and configured](https://cloud.ibm.com/objectstorage/create). For more information, [Getting started with {{site.data.keyword.cos_full_notm}}]https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage).
{: note}

## Configuring a {{site.data.keyword.cos_full_notm}} destination
{: #en-destinations-cos-configure}

To configure a {{site.data.keyword.cos_full_notm}} destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add new destination.

1. In the **Add a destination** side panel, provide the following details.

   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination**, for the **Type**, select **{{site.data.keyword.cos_full_notm}}** from the list as your destination type.
   - **Instance name** - Select the {{site.data.keyword.cos_full_notm}} instance name from the list, if you already have an {{site.data.keyword.cos_full_notm}} instance, otherwise, click the **Click new instance** link, to create one.
   - **Bucket name** - Enter the Bucket name to be used for connecting to the {{site.data.keyword.cos_full_notm}} instance.
   - **Endpoint** - Enter the {{site.data.keyword.cos_full_notm}} endpoint URL.

1. Click **Add**.

## {{site.data.keyword.openwhisk_short}} retry policy
{: #en-destinations-cos-retry}

When calling a webhook, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (webhook).

In addition, the following timeout conditions cause the {{site.data.keyword.cos_full_notm}} call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the {{site.data.keyword.cos_full_notm}} URL fails even after retry attempts, the notification is lost.
{: note}
