---

copyright:
  years: 2021, 2025
lastupdated: "2025-07-28"

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
- Madrid (`eu-es`)
- Toronto (`ca-tor`)
- Tokyo (`jp-tok`)
- Osaka (`jp-osa`)
- Sao Paulo (`br-sao`)
- Montreal (`ca-mon`)
- Washington DC (`us-east`)

You can create {{site.data.keyword.en_full_notm}} resources in one of the supported {{site.data.keyword.cloud_notm}} regions.

## Service endpoints
{: #en-service-endpoints}

{{site.data.keyword.en_short}} offers two connectivity options for interacting with its service APIs.

Public endpoints
:   By default, you can connect to resources in your account over the {{site.data.keyword.cloud_notm}} public network. Your data is encrypted in transit by default that uses the Transport Security Layer (TLS) 1.2 protocol.

Private endpoints
:   To further secure your connection, you can also enable [virtual routing and forwarding (VRF) and service endpoints](/docs/account?topic=account-vrf-service-endpoint&interface=ui){: external} for your infrastructure account. When you enable VRF for your account, you can [connect to {{site.data.keyword.en_short}} by using a private IP](/docs/event-notifications?topic=event-notifications-en-service-connection) that is accessible only through the {{site.data.keyword.cloud_notm}} private network.

### Public endpoints
{: #en-public-endpoints}

The following table contains the base URLs for the {{site.data.keyword.en_full_notm}} API endpoints. When you call the API, use the URL that corresponds to the region where your service instance is deployed. Add the path for each method to form the complete API endpoint for your requests.

| Location     | Endpoint URL      |
|--------------|-------------------|
| Dallas |`https://us-south.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| London |`https://eu-gb.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Sydney |`https://au-syd.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Frankfurt |`https://eu-de.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Madrid |`https://eu-es.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Toronto |`https://ca-tor.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Tokyo |`https://jp-tok.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Osaka |`https://jp-osa.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Sao Paulo | `https://br-sao.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Montreal | `https://ca-mon.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Washington DC | `https://us-east.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
{: caption="Public endpoints for interacting with {{site.data.keyword.en_short}} by using APIs" caption-side="bottom"}

### Private endpoints
{: #en-private-endpoints}

If you need to manage your {{site.data.keyword.en_short}} resources over a private network, see the following table to determine the API endpoints to use when you connect to the {{site.data.keyword.en_short}} API.

| Region       | Endpoint URL      |
|--------------|-------------------|
| Dallas |`https://private.us-south.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| London |`https://private.eu-gb.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Sydney |`https://private.au-syd.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Frankfurt |`https://private.eu-de.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Madrid |`https://private.eu-es.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Toronto |`https://private.ca-tor.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Tokyo |`https://private.jp-tok.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Osaka |`https://private.jp-osa.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Sao Paulo |`https://private.br-sao.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Montreal |`https://private.ca-mon.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
| Washington DC |`https://private.us-east.event-notifications.cloud.ibm.com/event-notifications/v1/instances/{guid}` |
{: caption="Private endpoints for interacting with {{site.data.keyword.en_short}} by using APIs" caption-side="bottom"}
