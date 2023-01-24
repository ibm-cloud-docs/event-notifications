---

copyright:
  years: 2023
lastupdated: "2023-01-24"

keywords: event-notifications, event notifications, about event notifications, destinations, ServiceNow, servicenow

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# ServiceNow
{: #en-destinations-servicenow}

A ServiceNow represents a service destination, where an incoming security event notification can be consumed programmatically to actions.
{: shortdesc}

An event which is routed to a ServiceNow destination will trigger creation of an Incident in the configured ServiceNow destination.
{: important}

## Configuring a ServiceNow destination
{: #en-sn-configure-destination}

The ServiceNow name follows the standard `https://xxx.service-now.com`, where `xxx` is your instance name. The ServiceNow instance name, Username, and Password can be fetched from your ServiceNow console. Navigate to your ServiceNow profile and go to "Manage Instance Password" to get the details.
{: important}

To configure a ServiceNow destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add a new destination.

1. In the **Add a destination** side panel, provide the following details.

   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination**, for the **Type**, select **ServiceNow** from the drop-down as your destination type.
   - **Instance Name** - Enter the name of your ServiceNow instance.
   - **Username** - Enter the username to be used for connecting to the ServiceNow instance.
   - **Password** - Enter the password to be used for authenticating the username mentioned earlier to authenticate in the ServiceNow instance.
   - **Namespace** defaulting to `now` and it cannot be changed.
   - {{site.data.keyword.en_short}} currently allows creation of entries on "Incident" table only and it cannot be changed.
   - **URL** gets populated based on the value provided before.
   - **Client ID** - Enter the client ID needed to retrieve the OAuth access token.
   - **Client secret** - Enter the client secret required for authenticating the Client ID provided earlier.

      **Client ID** and **Client secret** can be fetched from `System Oauth` -> `Application Registries`. This is inside your {{site.data.keyword.en_short}} instance console (you can search by clicking on "All"). Make sure it is in active state and applicable for connecting to external clients.
      {: note}

1. Click **Add**.

## {{site.data.keyword.en_short}} severity (ibmenseverity) to ServiceNow severity mapping
{: #en-sn-severity-mapping}

| {{site.data.keyword.en_short}} severity (ibmenseverity) | ServiceNow severity - Impact | ServiceNow severity - Urgency | ServiceNow severity - Priority |
| :---------- | :---------- | :---------- | :---------- |
| Critical | 1 | 1 | 1 |
| High | 1 | 2 | 2 |
| Medium | 2 | 2 | 3 |
| Low | 2 | 3 | 4 |
| Anything Else | 3 | 3 | 4 |
{: caption="Table 1. {{site.data.keyword.en_short}} severity (ibmenseverity) to ServiceNow severity mapping" caption-side="bottom"}

## ServiceNow retry policy
{: #en-sn-retry}

When calling a webhook, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (webhook).

In addition, the following timeout conditions cause the ServiceNow call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the ServiceNow webhook URL fails even after retry attempts, the notification is lost.
{: note}
