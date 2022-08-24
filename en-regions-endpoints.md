---

copyright:
  years: 2021, 2022
lastupdated: "2022-08-10"

keywords: event-notifications, event notifications, regions, endpoints, private endpoints

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Regions and endpoints
{: #en-regions-endpoints}

Review region and connectivity options for interacting with {{site.data.keyword.en_full_notm}}.
{: shortdesc}

## Available regions
{: #en-regions}

{{site.data.keyword.en_full_notm}} is available in the following regions:

- Dallas (`us-south`)
- London (`eu-gb`)
- Sydney (`au-syd`)
- Frankfurt (`eu-de`)

You can create {{site.data.keyword.en_full_notm}} resources in one of the supported {{site.data.keyword.cloud_notm}} regions.

## Service endpoints
{: #en-service-endpoints}

{{site.data.keyword.en_short}} offers two connectivity options for interacting with its service APIs.

Public endpoints
:   By default, you can connect to resources in your account over the {{site.data.keyword.cloud_notm}} public network. Your data is encrypted in transit by default using the Transport Security Layer (TLS) 1.2 protocol.

Private endpoints
:   To further secure your connection, you can also enable [virtual routing and forwarding (VRF) and service endpoints](https://cloud.ibm.com/docs/account?topic=account-vrf-service-endpoint&interface=ui) for your infrastructure account. When you enable VRF for your account, you can [connect to {{site.data.keyword.en_short}} by using a private IP](/docs/event-notifications?topic=event-notifications-en-service-connection) that is accessible only through the {{site.data.keyword.cloud_notm}} private network.

### Public endpoints
{: #en-public-endpoints}

The following table contains the base URLs for the {{site.data.keyword.en_full_notm}} API endpoints. When you call the API, use the URL that corresponds to the region where your service instance is deployed. Add the path for each method to form the complete API endpoint for your requests.

| Location     | Endpoint URL      |
|--------------|-------------------|
| Dallas |`https://us-south.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| London |`https://eu-gb.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| Sydney |`https://au-syd.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| Frankfurt |`https://eu-de.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
{: caption="Table 1. Public endpoints for interacting with {{site.data.keyword.en_short}} by using APIs" caption-side="bottom"}

### Private endpoints
{: #en-private-endpoints}

If you need to manage your {{site.data.keyword.en_short}} resources over a private network, see the following table to determine the API endpoints to use when you connect to the {{site.data.keyword.en_short}} API.

| Region       | Endpoint URL      |
|--------------|-------------------|
| Dallas |`https://private.us-south.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| London |`https://private.eu-gb.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| Sydney |`https://private.au-syd.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
| Frankfurt |`https://private.eu-de.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{instanceid}` |
{: caption="Table 2. Private endpoints for interacting with {{site.data.keyword.en_short}} by using APIs" caption-side="bottom"}

