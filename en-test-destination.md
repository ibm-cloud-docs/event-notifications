---

copyright:
  years:  2023, 2024
lastupdated: "2024-02-21"

keywords: event notifications, event notification, notifications, integrations, destinations, test destinations

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Testing destinations
{: #en-test-destination}

Maintaining the health and integrity of your connections is paramount. Making sure that your destinations deliver events reliably and the connection to the third-party apps is always up to date, is vital. To verify that the connection to your destination is correct, you can run a test.
{: shortdesc}

Currently the following destinations support this functionality:

1. Slack
2. PagerDuty
3. ServiceNow
4. Microsoft&reg; Teams
5. IBM Cloud Code Engine
6. IBM Cloud Object Storage
7. Webhook
8. App Configuration

## Before you begin
{: #en-test-destination-prereqs}

Before you can start testing your destinations, you must have the following prerequisites in place:

* A valid destination configuration.
* Access to the {{site.data.keyword.en_short}} console or the valid credentials for the API calls.

## Testing your destination
{: #en-test-destinations}

1. From your {{site.data.keyword.en_short}} instance, click **Destinations**.
1. For the destination that you want to test, click the **Options** menu and select **Test**. Wait for the test to finish.
1. When the test is complete, review your results. The results typically include the following information:

   - **Status**: Whether the test is successful or failed.
   - **Response Code**: If there is a test failure, the response code from the end destination client is returned.
   - **Response Message**: If there is a test failure, the response message from the end destination client is returned.
   - **Destination Activity**: If the test is successful, a test event is delivered to the destination. The activity varies by destination type: a new message is created for Slack, Webhook, and Microsoft&reg; Teams; a new incident is created for PagerDuty and ServiceNow; a new invocation occurs for {{site.data.keyword.codeenginefull_notm}}; and a new object is created in the specified bucket for {{site.data.keyword.cos_full_notm}}.
