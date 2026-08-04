---

copyright:
   years: 2026
lastupdated: "2026-08-04"

keywords: event notifications, filter, event filter, conditions

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Create event filters
{: #en-route-create-filters}

Event filters determine which events from your sources are routed to your topic. You can create multiple filters to target the events that you want to send to your destinations.
{: shortdesc}

## Before you begin
{: #en-route-filter-prereqs}

To use an {{site.data.keyword.IBM_notm}} managed service as a source, integrate it with {{site.data.keyword.en_short}} before creating a filter:

1. Go to the service's dashboard in the {{site.data.keyword.cloud_notm}} console. Find an existing instance in your **Resource List**, or create a new one from the [{{site.data.keyword.cloud_notm}} Catalog](https://cloud.ibm.com/catalog).
1. Integrate the service with {{site.data.keyword.en_short}} from that service's dashboard.
1. Select the newly integrated service from the **Source** drop-down list.

## Understanding filter conditions
{: #en-route-filter-conditions}

Event filters use conditions to evaluate incoming event data:

Basic conditions
:   Select from predefined fields such as event type, event subtype, and severity for supported {{site.data.keyword.cloud_notm}} sources.

Advanced conditions
:   Write custom JSONPath expressions to evaluate fields in the event payload.

## Creating an event filter
{: #en-route-create-filter-steps}

1. On the **Event filters** screen, click **Create filter**.

2. On the **Create event filter** dialog, enter the filter details:
   - **Filter name**: Enter a descriptive name for the filter.
   - **Source**: Select from available sources, including IBM Cloud sources (if already integrated), Periodic Timer, or IBM Resource Lifecycle Events.

3. Click **Integrate source** to create an API source or select an {{site.data.keyword.IBM_notm}} Cloud service on the **Integrate Source** dialog. Note that {{site.data.keyword.IBM_notm}} Cloud sources must be integrated from the source service instance. When you create an API source or select and configure an {{site.data.keyword.IBM_notm}} Cloud service, it appears in the **Source** drop-down list.

4. Choose how events are filtered:

   - **Allow all events**: All events from the selected source are routed to the topic. No filter conditions are applied.
   - **Apply filter conditions**: Configure specific conditions to filter events. Depending on the source type, set the following:

   **For IBM Cloud sources:**

   - **Event type**: Select the event type from the list.
   - **Event subtype**: Select the event subtype from the list.
   - **Severity**: Select the severity level from the list.
   - **Advanced conditions**: Add custom conditions to your topics. For more information, see [Advanced filtering conditions](/docs/event-notifications?topic=event-notifications-en-advanced-filtering).

   **For API sources:**

   You can add **Advanced conditions** rules to your topic. For more information, see [Advanced filtering conditions](/docs/event-notifications?topic=event-notifications-en-advanced-filtering).

   **For Periodic Timer sources:**

   See [Periodic Timer](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer) for steps to set rules for your topic.

   Click **Add a condition** to add conditions.
   To view a recent event payload emitted by the selected source, see [View event payloads](#en-route-view-payloads).
   To validate your conditions against a selected payload, see [Test all conditions](#en-route-test-conditions).

5. Click **Save** to create the filter.

6. Optional: Click **Create event filter** again to add more filters. You can also edit or delete the created filters by using the **Edit** and **Delete** options in the **Options** menu.

7. Click **Next** to proceed to the **Subscriptions** screen.

## View event payloads
{: #en-route-view-payloads}

Click **View payload details** to open a dialog that displays the last 10 event payloads received from the selected source, along with their fields.

Use this to understand the payload structure before writing or refining your filter conditions.

## Test all conditions
{: #en-route-test-conditions}

After you write your conditions, you can test them against recent event payloads:

1. Enable the conditions you want to test.

1. Click **Test all conditions**.

1. Optionally, define a custom payload by clicking the **+** icon.

1. Select the event payloads against which you want to test the conditions, then click **Select and test** in the dialog.

1. In the **Conditions** section, check the **Test result** column to see whether each condition matched the selected payload.

## Next steps
{: #en-route-create-filters-next}

[Create subscriptions](/docs/event-notifications?topic=event-notifications-en-route-create-subscriptions) to connect your topic to destinations.
