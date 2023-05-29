---

copyright:
  years: 2020, 2023
lastupdated: "2023-05-29"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} destination
{: #en-create-en-destination}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Create an {{site.data.keyword.en_short}} destination. Destinations are custom protocols, which are either services or user reachable entities. {{site.data.keyword.en_short}} supports the following destinations:

- {{site.data.keyword.cloud_notm}} Email
- {{site.data.keyword.cloud_notm}} SMS
- Push notifications (Android, iOS, Chrome, Firefox, and Safari)
- Huawei Cloud push
- Slack
- Microsoft&trade; Teams
- PagerDuty
- Webhook
- {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}
- ServiceNow
- {{site.data.keyword.cloud_notm}} {{site.data.keyword.codeengineshort}}
- {{site.data.keyword.cos_full_notm}}
{: shortdesc}

**{{site.data.keyword.cloud_notm}} SMS service** and **{{site.data.keyword.cloud_notm}} Email service** are supported out of the box.

By default, each destination detail consists of **Name**, **Description**, **Type**, **Subscriptions**, **Collect failed events** (Off).

When you try to toggle the **Collect failed events** switch to **ON** without configuring a {{site.data.keyword.cos_full_notm}} bucket to collect the failed events, an appropriate error message displays. For more information on configuration and collecting failed events, see [here](/docs/event-notifications?topic=event-notifications-en-cfe-integrations).
{: note}

## Create a destination
{: #en-create-destination}
{: step}

Click `Destinations` in the {{site.data.keyword.en_short}} console. By default, **{{site.data.keyword.cloud_notm}} SMS service** and **{{site.data.keyword.cloud_notm}} Email service** are included, with their `Destination ID`.

## Add destination details
{: #en-destination-details}
{: step}

Click **Add +** to add new destination.

Provide the new destination details:
- `Destination name`: add a name for the Destination.
- `Destination description`: add an optional description for the destination.
- `Destination type`: select a type from the list.

When you select the `Destination Type` as any one of the push notification services (FCM, APNs, Chrome, Firefox, and Safari), you can select a Pre-production destination for developing and testing your environments at a low cost.
{: note}

## Add the destination
{: #en-destination-finish}
{: step}

Click `Add`.

## Upgrading a Pre-production destination to Production destination
{: #en-destination-preprod-prod}

You can upgrade a **Pre-production destination** to **Production destination** after creating the destination by using the **Edit** option from the overflow menu.

To understand the billing impact of upgrading a **Pre-production destination** to **Production destination**, see [here](/docs/event-notifications?topic=event-notifications-en-destinations-push#en-destinations-push-charge-preprod-to-prod).

To modify the destination,
- Select the pre-production destination from the list of destinations
- Click the three vertical dots in the selected pre-production destination to access the overflow menu
- Click **Edit**, which brings the editable view of the selected destination.
- Click the **Production destination** tile to change the destination.
- Click **Add**.

You cannot change a **Production destination** to **Pre-production destination**.
{: important}
