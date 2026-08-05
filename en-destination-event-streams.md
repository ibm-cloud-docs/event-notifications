---

copyright:
  years: 2026
lastupdated: "2026-08-04"

keywords: event-notifications, event notifications, about event notifications, destinations, Event Streams, event streams

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.messagehub}}
{: #en-destinations-event-streams}

{{site.data.keyword.messagehub}} is a message bus that is built by using Apache Kafka. It has high throughput and is optimized for event ingestion into {{site.data.keyword.cloud_notm}} and event stream distribution between your services and applications. In Event Streams, applications can send data by creating messages and sending to a topic. To receive messages, the application subscribes to a topic and can choose to receive all the messages of the topic or share the messages between them.
{: shortdesc}

{{site.data.keyword.messagehub}} represents a service destination. Since {{site.data.keyword.messagehub}} is a Kafka managed service, incoming notifications cannot be stored and consumed programmatically because Kafka does not store the data once it has been read.

## Before you begin
{: #en-event-streams-prerequisites}

- Make sure that an {{site.data.keyword.messagehub}} instance is [created and configured](/docs/EventStreams?topic=EventStreams-quick_setup_guide&interface=ui).

- To create and configure an {{site.data.keyword.en_short}} instance, see [Getting started with {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-getting-started)

## Configuring an {{site.data.keyword.messagehub}} destination in the console
{: #en-destinations-event-streams-configure}

If you are using {{site.data.keyword.en_short}} CLI or API to configure an {{site.data.keyword.messagehub}} service instance as a destination, ensure that you have enabled authorization to grant access between services before integrating with {{site.data.keyword.messagehub}}. For more information, see [Using authorizations to grant access between services](#en-using-s2s-console-event-streams).
{: important}

To configure an {{site.data.keyword.messagehub}} destination, complete the following steps:

1. From your {{site.data.keyword.en_short}} instance, click **Destinations**.

1. Click **Create** to add a new destination.

1. Enter the following destination details in the **Create destination** dialog:

   - **Name**: Enter a name for your destination.
   - **Description**: Optionally, enter a description for your destination.
   - **Type**: Under **Destination**, select **{{site.data.keyword.messagehub}}** from the list as your destination type.
   - **Account**: Select the account where the {{site.data.keyword.messagehub}} instance is located.

      If the {{site.data.keyword.messagehub}} instance is in the same account as your {{site.data.keyword.en_short}} instance:

      1. Select the name of the {{site.data.keyword.messagehub}} instance to send notifications to.
      2. After the instance is selected, the **Endpoint** field is filled automatically from the selected instance.
      3. Select the **Topic** to send or receive messages from. For more information, see [Topic](#en-topic).

      If the {{site.data.keyword.messagehub}} instance is in a different account, provide the following details:

      1. Enter the {{site.data.keyword.messagehub}} CRN. For more information, see [CRN](#en-crn).
      2. Enter the {{site.data.keyword.messagehub}} endpoint URL. For more information, see [Endpoint URL](#en-event-streams-endpoint-url).
      3. Select the topic to send or receive messages from. For more information, see [Topic](#en-topic).

1. Click **Create destination**.

### Finding the {{site.data.keyword.messagehub}} service instance details
{: #en-event-streams-details}

1. Log in to your {{site.data.keyword.cloud_notm}} account.

1. Navigate to **Resource List** in the menu.

1. Navigate to **Integration** in the Resource list.

1. Click the {{site.data.keyword.messagehub}} instance name to open your {{site.data.keyword.messagehub}} console.

1. From the {{site.data.keyword.messagehub}} console:

#### CRN
{: #en-crn}

Copy the **CRN** to use in the destination creation process.

#### Endpoint URL
{: #en-event-streams-endpoint-url}

Copy the **HTTP API endpoint** to use in the destination creation process.

#### Topic
{: #en-topic}

Click **Topics** in the menu to view the list of available topics. Select the topic that you want to send or receive messages from, and copy the **Topic Name** to use in the destination creation process.

## Creating an authorization in the console
{: #en-using-s2s-console-event-streams}

An authorization is required to grant one service access to another service. You must grant {{site.data.keyword.en_short}} the appropriate IAM service-to-service access so that it can publish messages to {{site.data.keyword.messagehub}}.

For more information, see [Authorization between services](/docs/event-notifications?topic=event-notifications-en-using-s2s-authorization).

## {{site.data.keyword.messagehub}} retry policy
{: #en-event-streams-retry}

When sending notifications to {{site.data.keyword.messagehub}}, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
