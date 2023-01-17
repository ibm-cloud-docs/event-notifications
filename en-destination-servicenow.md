---

copyright:
  years: 2023
lastupdated: "2023-01-17"

keywords: event-notifications, event notifications, about event notifications, destinations, ServiceNow, servicenow

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# ServiceNow
{: #en-destinations-servicenow}

A ServiceNow represents a service destination, where an incoming security event notification can be consumed programmatically to actions.
{: shortdesc}

<!-- add how to create/get a ServiceNow account/account info here -->

## Configuring a ServiceNow destination
{: #en-sn-configure-destination}

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
   - **Namespace**, **now**, and **URL** gets populated based on the value provided before.
   - **Client ID** - Enter the client ID needed to retrieve the OAuth access token.
   - **Client secret** - Enter the client secret required for authenticating the Client ID provided earlier.

1. Click **Add**.

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
