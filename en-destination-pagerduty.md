---

copyright:
  years: 2022
lastupdated: "2022-11-30"

keywords: event-notifications, event notifications, destinations, pagerduty

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# PagerDuty
{: #en-destinations-pagerduty}

PagerDuty empowers users and organizations to prevent and resolve business-impacting incidents for exceptional customer experience. PagerDuty helps organizations with the insight to proactively manage events that may impact customers across their IT environment.
{: shortdesc}

When you select PagerDuty as service destination, any subscribed notification about an event can be sent as an **alert** to PagerDuty channels.

## Generate PagerDuty API key
{: #en-pd-generate-api-key}

Generate the PagerDuty API key as per the guidance [here](https://support.pagerduty.com/docs/api-access-keys){: external}.

## Generate PagerDuty routing key
{: #en-pd-generate-routing-key}

To integrate your PagerDuty service to {{site.data.keyword.en_short}} service destination, you need to generate a PagerDuty routing key. To generate a PagerDuty routing key, follow these steps: [Generate a new Integration Key](https://support.pagerduty.com/docs/services-and-integrations#generate-a-new-integration-key){: external}.

If you already integrated EventsV2 api with your PagerDuty service, jump to service directory, select **More** and select **View Integrations**. You will find the Integration key inside this view.
{: note}

## Configuring a PagerDuty destination
{: #en-pd-configure-destination}

You can configure a PagerDuty destination in the `Destinations` tab.

To configure a PagerDuty destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add new destination.

1. In the **Add a destination** side panel, provide the following details.

   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination**, for the **Type**, select **Pagerduty** from the drop-down as your destination type.
   - **API key** - Enter the API key that you have [generated](#en-pd-generate-api-key) earlier.
   - **Routing key** - Enter the routing key [generated](#en-pd-generate-routing-key) earlier.

1. Click **Add**.

## PagerDuty alert events supported by {{site.data.keyword.en_short}}
{: #en-pd-retry}

{{site.data.keyword.en_short}} supports only alert event of Pagerduty. For more information, see [here](https://developer.pagerduty.com/docs/ZG9jOjExMDI5NTgx-send-an-alert-event){: external}.

| {{site.data.keyword.en_short}} field | PagerDuty field | Supported |
| :---------- | :---------- | :----------|
| `routing_key` (Destination Config) | `routing_key` | Yes |
| `trigger` (default) | `event_action` | Partial |
| `ibmendefaultlong` | `payload.summary` | Yes |
| `critical` - HIGH, `error` - MEDIUM, `warning` - LOW, `info` - INFO, `Default Severity` - LOW | `payload.severity` | Yes |
| `time` (cloud events) | `payload.timestamp` | Yes |
| `data` | `payload.custom_details` | Yes |
| NA | `dedup_key` | No |
| NA | `payload.component` | No |
| NA | `payload.group` | No |
| NA | `payload.class` | No |
| NA | `images` | No |
| NA | `links` | No |
{: caption="Table 1. Supported PagerDuty alert events" caption-side="bottom"}

| {{site.data.keyword.en_short}} severity | PagerDuty severity |
| :---------- | :---------- |
| Critical | Critical |
| High | Error |
| Medium | Warning |
| Low | Info |
| Anything Else | Info |
{: caption="Table 2. {{site.data.keyword.en_short}} severity to PagerDuty severity mapping" caption-side="bottom"}

## PagerDuty retry policy
{: #en-pd-retry}

When calling a webhook, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (PagerDuty).

In addition, the following timeout conditions cause the PagerDuty call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the PagerDuty URL fails even after retry attempts, the notification is lost.
{: note}
