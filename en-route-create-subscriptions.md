---

copyright:
   years: 2026
lastupdated: "2026-08-04"

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
   - **Destination**: Select the destination you want to use.

   Click [**Integrate destination**](#en-route-integrate-destination) to add a new destination not listed here.

3. Depending on the destination type, provide the required details. For example, for email or SMS destinations, add the recipients.

4. Click **Create subscription**.

5. Optional: Click **Create** again to add more subscriptions. You can also edit or delete the subscriptions by using the **Edit** and **Delete** options on the **Options** menu.

## Integrating a destination
{: #en-route-integrate-destination}

If you need a destination that is not listed, click **Integrate destination** on the subscription dialog. In the **Integrate destination** dialog, select the destination type to add, and then click **Save**.

For more information about destination-specific configurations, see [Event Notifications destinations](/docs/event-notifications?topic=event-notifications-en-destination).

## Next steps
{: #en-route-create-subscriptions-next}

[Review and complete](/docs/event-notifications?topic=event-notifications-en-route-review) your routing configuration.
