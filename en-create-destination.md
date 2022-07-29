---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-29"

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

Create an {{site.data.keyword.en_short}} destination. Destinations are custom protocols, which are either services or user reachable entities. Currently, {{site.data.keyword.en_short}} supports the following destinations:

- IBM Cloud Email
- IBM Cloud push notification service
- IBM Cloud SMS
- Webhook
- Slack
- Microsoft&trade; Teams
{: shortdesc}

email-ibm and email-sms are supported out of the box.

## Create a destination
{: #en-create-destination}
{: step}

Click `Destinations` in the {{site.data.keyword.en_short}} console. By default, **IBM Cloud SMS service** and **IBM Cloud Email service** are included, with their `Destination ID`.

## Add destination details
{: #en-destination-details}
{: step}

Click **Add +** to add new destination. 

Provide the new destination details:
- `Destination name`: add a name for the Destination.
- `Destination description`: add an optional description for the destination.
- `Destination type`: select a type from the dropdown list.

When you select the `Destination Type` as any one of the push notification service (FCM, APNs, Chrome, Firefox, and Safari), you can select a Pre-production destination for developing and testing your environments at a lower-cost.
{: note}

## Add the destination
{: #en-destination-finish}
{: step}

Click `Add`.
