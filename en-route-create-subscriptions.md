---

copyright:
   years: 2026
lastupdated: "2026-06-09"

keywords: event notifications, subscription, destination

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Create subscriptions
{: #en-route-create-subscriptions}

Subscriptions connect your topic to destinations, defining where notifications are sent. You can create multiple subscriptions for a topic to route notifications to different destinations.
{: shortdesc}

## Creating a subscription
{: #en-route-create-subscription-steps}

1. On the **Subscriptions** step, click **Create subscription**.

2. Enter the subscription details:
   - **Name**: Enter a descriptive name for the subscription.
   - **Destination type**: Select the type of destination.
   - **Destination**: Select the destination that you want to use.
   
   You can click **Integrate destination** to add a new destination not listed here.

4. Depending on the destination type, provide any additional details that are required. For example, for email or SMS destinations, add the recipients.

5. Click **Create** to create the subscription.

6. Optional: You can click **Create subscription** again to add more subscriptions. You can also edit or delete the created subscriptions by using the **Edit** and **Delete** options in the **Options** menu.

## Integrating a destination
{: #en-route-integrate-destination}

If you need a destination that is not already available, click **Integrate destination** in the subscription side panel. In the **Integrate destination** side panel, select the destination type that you want to add, and then click **Save**.

For more information about destination-specific configurations, see [Event Notifications destinations](/docs/event-notifications?topic=event-notifications-en-destination).

## Next steps
{: #en-route-create-subscriptions-next}

[Review and complete](/docs/event-notifications?topic=event-notifications-en-route-review) your routing configuration.
