---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-25"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} destination
{: #en-create-en-destination}

Destinations are custom protocols, which are either services or user reachable entities. {{site.data.keyword.en_short}} supports **{{site.data.keyword.cloud_notm}} SMS service** and **{{site.data.keyword.cloud_notm}} Email service** out of the box. To learn more about the destinations supported by {{site.data.keyword.en_short}}, see [Working with event destinations](/docs/event-notifications?topic=event-notifications-en-destination).
{: shortdesc}

## Creating a destination
{: #en-create-destination-steps}

To create a new destination:

1. Click **Destinations** in your {{site.data.keyword.en_short}} instance. By default, **{{site.data.keyword.cloud_notm}} SMS service** and **{{site.data.keyword.cloud_notm}} Email service** are included, with their destination ID.

1. Click **Create** to create a new destination.

   When you select the destination type as any one of the push notification services (FCM, APNs, Chrome, Firefox, and Safari), you can select a Pre-production destination for developing and testing your environments at a low cost.
   {: note}

1. Provide **Name**, **Description** and **Destination type**. Configuration parameters differ by destination type. For more information about available destination types and steps to create and configure each one, see [Working with event destinations](/docs/event-notifications?topic=event-notifications-en-destination).

1. Configure your destination parameters and click **Create destination**. 

You can click the **Edit** in the **Options** menu to edit the destination. You can upgrade **Pre-production destination** to **Production destination**.

To understand the billing impact of upgrading a **Pre-production destination** to **Production destination**, see [Push charges for changing from pre-production destination to production destination](/docs/event-notifications?topic=event-notifications-en-destinations-push#en-destinations-push-charge-preprod-to-prod).

By default, each destination detail consists of **Name**, **Description**, **Type**, **Subscriptions**, **Collect failed events** (Off).

When you try to toggle the **Collect failed events** switch to **ON** without configuring a {{site.data.keyword.cos_full_notm}} bucket to collect the failed events, an appropriate error message displays. For more information on configuration and collecting failed events, see [Collecting failed events](/docs/event-notifications?topic=event-notifications-en-cfe-integrations).
{: note}

## Modifying an {{site.data.keyword.en_short}} destination
{: #en-modify-en-destination}

1. Select the pre-production destination from the list of destinations.

1. Click **Edit** in the **Options** menu.

1. Click the **Production destination** tile to change the destination.

1. Click **Add**.

You cannot change a **Production destination** to a **Pre-production destination**.
{: important}
