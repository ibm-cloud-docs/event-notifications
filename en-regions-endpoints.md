---

copyright:
  years: 2021, 2022
lastupdated: "2022-02-09"

keywords: event-notifications, event notifications, regions, endpoints

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Regions and endpoints
{: #en-regions-endpoints}

Review region and connectivity options for interacting with {{site.data.keyword.en_full_notm}}.
{: shortdesc}

## Available regions
{: #en-regions}

{{site.data.keyword.en_full_notm}} is available in the following regions:

- Dallas
- London
- Sydney
- Frankfurt

You can create {{site.data.keyword.en_full_notm}} resources in one of the supported {{site.data.keyword.cloud_notm}} regions.

## Service endpoints
{: #en-endpoints}

The following table contains the base URLs for the {{site.data.keyword.en_full_notm}} API endpoints. When you call the API, use the URL that corresponds to the region where your service instance is deployed. Add the path for each method to form the complete API endpoint for your requests.

|Location     |Endpoint URL      |
|-------------|------------------|
|Dallas |`https://us-south.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
|London |`https://eu-gb.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
|Sydney |`https://au-syd.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
|Frankfurt |`https://eu-de.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
{: caption="Table 1. Service endpoints" caption-side="top"}
