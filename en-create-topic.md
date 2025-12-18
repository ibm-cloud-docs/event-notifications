---

copyright:
  years: 2015, 2024
lastupdated: "2024-11-28"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} topic
{: #en-create-en-topic}

A topic is needed to filter the incoming events from the Source. Each source is connected to a topic through a user-defined filter. Notifications that pass into a topic are pushed to all subscribed destinations. A topic can connect to multiple sources and has an independent filter for each source that is connected to it. Configure topics as needed and {{site.data.keyword.en_short}} handles the routing and delivering of alerts reliably to the correct destinations.
{: shortdesc}

## Creating a topic
{: #en-create-topic}

1. Select **Topics** in the {{site.data.keyword.en_short}} console.

1. Click **Create**, and enter the following topic details:
   - **Name**: enter a name for the topic.
   - **Description**: add an optional description for the topic.
   - **Source**: select a source from the list. Sources are of 3 types:

      - {{site.data.keyword.IBM_notm}} Source
      - API Source
      - Periodic Timer Source

   
1. If your chosen source is an **{{site.data.keyword.IBM_notm}} Source**: 

   Add the following rules to your topic:

      - **Event type**: select event type from the list.
      - **Event subtype**: select event sub type from the event sub type list.
      - **Severity**: select severity from the severity list.
      - **Advanced conditions**: Add custom conditions to your topics. See [Advanced Filtering Conditions](/docs/event-notifications?topic=event-notifications-en-advanced-filtering) to learn more about adding advanced conditions to your topic.


If your chosen source is an **API source**, then you can add the "Advanced Conditions" rule to your topic.
{: note}

If your chosen source is a **Periodic Timer Source**, then refer [Periodic Timer](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer) for steps to set rules for your topic. 

Step 2 created a topic, step 3 provisioned optional custom rules for the topic.
{: note}

1. Click **Add a condition**.

    If you do not select any rules, a default rule is added, which means all notifications route to the topic by default.
    {: note}

1. Click **Create** in the topic wizard.
