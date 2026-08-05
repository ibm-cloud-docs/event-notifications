---

copyright:
  years: 2022, 2023
lastupdated: "2023-10-10"

keywords: event-notifications, event notifications, destinations, pagerduty

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# PagerDuty
{: #en-destinations-pagerduty}

PagerDuty empowers users and organizations to prevent and resolve business-impacting incidents for exceptional customer experience. PagerDuty helps organizations with the insight to proactively manage events that may impact customers across their IT environment.
{: shortdesc}

When you select PagerDuty as service destination, any subscribed notification about an event can be sent as an **alert** to PagerDuty channels.

## Generate PagerDuty routing key
{: #en-pd-generate-routing-key}

To integrate your PagerDuty service to {{site.data.keyword.en_short}} service destination, you need to generate a PagerDuty routing key. To generate a PagerDuty routing key, follow these steps: [Generate a new Integration Key](https://support.pagerduty.com/main/docs/services-and-integrations#generate-a-new-integration-key){: external}.

If you already integrated EventsV2 API with your PagerDuty service, go to the service directory, select **More**, and select **View Integrations**. The Integration key is available in this view.
{: note}

## Configuring a PagerDuty destination
{: #en-pd-configure-destination}

You can configure a PagerDuty destination in the **Destinations** tab.

To configure a PagerDuty destination, complete the following steps:

1. From your {{site.data.keyword.en_short}} instance, click **Destinations**.

1. Click **Create** to create a new destination.

1. Enter the following destination details in the **Create destination** dialog:

   - **Name**: Enter a name for your destination.
   - **Description**: Optionally, enter a description for your destination.
   - **Type**: Under **Destination**, select **PagerDuty** from the dropdown list as your destination type.
   - **Routing key**: Enter the routing key [generated](#en-pd-generate-routing-key) earlier.

1. Click **Create destination**.

## PagerDuty alert events supported by {{site.data.keyword.en_short}}
{: #en-pd-retry}

{{site.data.keyword.en_short}} supports only alert events of PagerDuty. For more information, see [Send an alert event](https://developer.pagerduty.com/docs/ZG9jOjExMDI5NTgx-send-an-alert-event){: external}.

| {{site.data.keyword.en_short}} field | PagerDuty field | Supported |
| :---------- | :---------- | :----------|
| `routing_key` (Destination Config) | `routing_key` | Yes |
| `trigger` (default) | `event_action` | Partial |
| `ibmendefaultlong` | `payload.summary` | Yes |
| `critical` - HIGH, `error` - MEDIUM, `warning` - LOW, `info` - INFO, `Default Severity` - LOW | `payload.severity` | Yes |
| `time` (cloud events) | `payload.timestamp` | Yes |
| `data` | `payload.custom_details` | Yes |
| `source` | `payload.source` | Yes |
| NA | `dedup_key` | No |
| NA | `payload.component` | No |
| NA | `payload.group` | No |
| NA | `payload.class` | No |
| NA | `images` | No |
| NA | `links` | No |
{: caption="Supported PagerDuty alert events" caption-side="bottom"}

| {{site.data.keyword.en_short}} severity | PagerDuty severity |
| :---------- | :---------- |
| Critical | Critical |
| High | Error |
| Medium | Warning |
| Low | Info |
| Anything Else | Info |
{: caption="{{site.data.keyword.en_short}} severity to PagerDuty severity mapping" caption-side="bottom"}

## Testing a PagerDuty destination configuration
{: #en-pd-test-destination}

You can test a PagerDuty destination in the options menu next to the destination. You can test whether the provided configuration is correct with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).

## PagerDuty retry policy
{: #en-pd-retry-policy}

When sending notifications to PagerDuty, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
