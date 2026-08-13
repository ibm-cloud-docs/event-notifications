---

copyright:
  years: 2026
lastupdated: "2026-08-13"

keywords: event-notifications, event notifications, about event notifications, topics, mapping, event flow, sources, destinations

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Viewing the event flow mapping
{: #en-view-mapping}

Use the mapping view to trace the end-to-end path of an event flow in {{site.data.keyword.en_short}}. The mapping view is available from the **Options** menu on any source, topic, or destination. The context of the mapping changes depending on where you access it.
{: shortdesc}

## Viewing the mapping
{: #en-view-mapping-steps}

1. In the {{site.data.keyword.en_short}} instance, click **Sources**, **Topics**, or **Destinations** depending on the context from which you want to view the mapping.

1. Select the source, topic, or destination instance whose mapping you want to view.

1. Click the **Options** menu and select **View mapping**.

   The mapping view displays the end-to-end event flow based on the context of the selected item:

   - **From a source**: Shows the topics that are associated with the source and the destinations of their subscriptions.
   - **From a topic**: Shows the sources that are connected to the topic and the destinations that are configured to receive its notifications.
   - **From a destination**: Shows the topics for which the destination is a subscription and the sources that are connected to those topics.
