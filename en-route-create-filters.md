---

copyright:
   years: 2026
lastupdated: "2026-06-09"

keywords: event notifications, filter, event filter, conditions

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Create event filters
{: #en-route-create-filters}

Event filters determine which events from your sources are routed to your topic. You can create multiple filters to target the events that you want to send to your destinations.
{: shortdesc}

## Understanding filter conditions
{: #en-route-filter-conditions}

Event filters use conditions to evaluate incoming event data:

Basic conditions
:   Select from predefined fields such as event type, event subtype, and severity for supported {{site.data.keyword.cloud_notm}} sources.

Advanced conditions
:   Write custom JSONPath expressions to evaluate fields in the event payload.

## Creating an event filter
{: #en-route-create-filter-steps}

1. On the **Event filters** screen, click **Create event filter**.

2. In the side panel, enter the filter details:
   - **Filter name**: Enter a descriptive name for the filter.
   - **Source**: Select from available sources, including IBM Cloud sources (if already integrated), Periodic Timer, or IBM Resource Lifecycle Events.

3. Click **Integrate source** to create an API source if needed. IBM Cloud sources must be integrated from the source service instance.

4. Configure the filter conditions for the selected source:

   **For IBM Cloud sources:**
   
   Add the following rules to your topic:
   - **Event type**: Select the event type from the list.
   - **Event subtype**: Select the event subtype from the list.
   - **Severity**: Select the severity level from the list.
   - **Advanced conditions**: Add custom conditions to your topics. For more information, see [Advanced filtering conditions](/docs/event-notifications?topic=event-notifications-en-advanced-filtering).
   
   **For API sources:**
   
   You can add **Advanced conditions** rules to your topic. For more information, see [Advanced filtering conditions](/docs/event-notifications?topic=event-notifications-en-advanced-filtering).
   
   **For Periodic Timer sources:**
   
   Refer to [Periodic Timer](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer) for steps to set rules for your topic.
   
   Click **Add a condition** to add additional filter rules.

5. Click **Save** to create the filter.

6. Optional: Click **Create event filter** again to add more filters. You can also edit or delete the created filters by using the **Edit** and **Delete** options in the **Options** menu.

7. Click **Next** to proceed to the **Subscriptions** screen.




## Next steps
{: #en-route-create-filters-next}

[Create subscriptions](/docs/event-notifications?topic=event-notifications-en-route-create-subscriptions) to connect your topic to destinations.
