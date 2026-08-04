---

copyright:
  years: 2024
lastupdated: "2024-10-17"

keywords: event-notifications, event notifications, destinations, Huawei

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Creating push notifications to Huawei using {{site.data.keyword.en_short}}
{: #en-push-huawei}

{{site.data.keyword.en_short}} provides a push notification service for sending transactional and informational event notifications to Huawei mobile devices.
{: shortdesc}

## Creating a Huawei Push Destination
{: #en-create-destination-huawei}

To create a Huawei Push destination, complete the following steps:

1. Log in to your {{site.data.keyword.cloud_notm}} account.

1. If you already have an {{site.data.keyword.en_short}} service instance, navigate to your {{site.data.keyword.en_short}} service instance from the **Resource list** and select the required {{site.data.keyword.en_short}} service instance. Otherwise, you can [create a new {{site.data.keyword.en_short}} service instance](/docs/event-notifications?topic=event-notifications-getting-started#en-cloud-ac).

1. Click **Destinations** in the {{site.data.keyword.en_short}} instance and click **Create**.

1. Enter the following destination details in the **Create destination** dialog:
   - **Name**: add a name for the Destination.
   - **Description**: add an optional description about the destination.
   - **Destination type**: select **Huawei Push Notifications** from the list.

1. Select a destination plan. You can select a **Pre-production destination** for developing and testing your environments at a low cost. You can upgrade a **Pre-production destination** to **Production destination** after creating the destination by using the **Edit** option from the overflow menu after your development and testing. For more information, see [Upgrading a Pre-production destination to Production destination](#en-destination-preprod-prod1). There will be a change in cost when you upgrade.

1. Retrieve Huawei credentials (**Client ID** and **Client secret**) for your application. For more information, see [Retrieving Huawei credentials](#en-retrieve-huawei-credentials).

1. Add **Client ID** and **Client secret**.

1. Click **Create destination**.

## Retrieving Huawei Credentials
{: #en-retrieve-huawei-credentials}

To complete the Huawei Push Notification setup, you need a **Client ID** and **Client secret**. Obtain these from the Huawei AppGallery Connect portal.

1. Sign into the Huawei [AppGallery Connect](https://developer.huawei.com/consumer/en/service/josp/agc/index.html#/).

1. Click **My projects**. Select an existing project or click **Add project** to create one.

1. Click **Add app** if there are no applications in the project, or select the existing application.

1. Enable Push Kit to see the app details. For more information, see [Enabling Push Kit](https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/android-config-agc-0000001050170137#section9471122085218).


1. Go to the **App information** section, where you can find OAuth 2.0 **Client ID**. Copy the **Client ID** and **Client secret** values into the respective fields.

## Upgrading a Pre-production Destination to Production Destination
{: #en-destination-preprod-prod1}

You can upgrade a **Pre-production destination** to **Production destination** after creating the destination by using the **Edit** option from the overflow menu.

To understand the billing impact of upgrading a **Pre-production destination** to **Production destination**, see [Upgrading a pre-production destination to production](/docs/event-notifications?topic=event-notifications-en-destinations-push#en-destinations-push-charge-preprod-to-prod).

To modify the destination:
- Select the pre-production destination from the list of destinations.
- Click **Edit** in the **Options** menu, which opens the editable view of the selected destination.
- Click the **Production destination** tile to change the destination.
- Click **Save destination**.

You cannot change a **Production destination** to **Pre-production destination**.
{: important}
