---

copyright:
  years: 2023
lastupdated: "2023-10-10"

keywords: event-notifications, event notifications, about event notifications, destinations, ServiceNow, servicenow

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# ServiceNow
{: #en-destinations-servicenow}

A ServiceNow represents a service destination, where an incoming security event notification can be consumed programmatically to actions.
{: shortdesc}

An event that is routed to a ServiceNow destination triggers the creation of an Incident in the configured ServiceNow destination.
{: important}

## Configuring a ServiceNow destination
{: #en-sn-configure-destination}

The ServiceNow name follows the standard `https://xxx.service-now.com`, where `xxx` is your instance name. The ServiceNow instance name, Username, and Password can be fetched from your ServiceNow console. Navigate to your ServiceNow profile and go to **Manage Instance Password** to get the details.
{: important}

To configure a ServiceNow destination, complete the following steps:

1. From your {{site.data.keyword.en_short}} instance, click **Destinations**.

1. Click **Create** to add a new destination.

1. Enter the following destination details in the **Create destination** dialog:

   - **Name**: Enter a name for your destination.
   - **Description**: Optionally, enter a description for your destination.
   - **Type**: Under **Destination**, select **ServiceNow** from the dropdown list as your destination type.
   - **Instance Name**: Enter the name of your ServiceNow instance.
   - **Username**: Enter the username for connecting to the ServiceNow instance.
   - **Password**: Enter the password for authenticating the username in the ServiceNow instance.
   - **Namespace**: Defaults to `now` and cannot be changed.
   - **Table**: {{site.data.keyword.en_short}} currently allows creation of entries on the `Incident` table only and it cannot be changed.
   - **URL**: Gets populated based on the values provided.
   - **Client ID**: Enter the client ID needed to retrieve the OAuth access token.
   - **Client secret**: Enter the client secret required for authenticating the Client ID.

      **Client ID** and **Client secret** can be fetched from **System OAuth** > **Application Registries** in your ServiceNow instance console. Ensure that it is in an active state and applicable for connecting to external clients.
      {: note}

1. Click **Create destination**.

## {{site.data.keyword.en_short}} severity (ibmenseverity) to ServiceNow severity mapping
{: #en-sn-severity-mapping}

| {{site.data.keyword.en_short}} severity (ibmenseverity) | ServiceNow severity - Impact | ServiceNow severity - Urgency | ServiceNow severity - Priority |
| :---------- | :---------- | :---------- | :---------- |
| Critical | 1 | 1 | 1 |
| High | 1 | 2 | 2 |
| Medium | 2 | 2 | 3 |
| Low | 2 | 3 | 4 |
| Anything Else | 3 | 3 | 4 |
{: caption="{{site.data.keyword.en_short}} severity (ibmenseverity) to ServiceNow severity mapping" caption-side="bottom"}

## Testing a ServiceNow destination configuration
{: #en-sn-test-destination}

You can test a ServiceNow destination in the options menu next to the destination. You can test whether the provided configuration is correct with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).

## ServiceNow retry policy
{: #en-sn-retry}

When sending notifications to ServiceNow, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
