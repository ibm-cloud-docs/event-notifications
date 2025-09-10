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

Maintaining the health and integrity of your connections is paramount. Helping ensure that your destinations deliver events reliably and the connection to the third-party apps is always up to date, is vital. To help ensure that the connection to your destination is correct, you can validate it with a test.
{: shortdesc}

Currently this functionality supports the following destinations:

1. Slack
2. PagerDuty
3. ServiceNow
4. Microsoft&reg; Teams
5. IBM Cloud Code Engine
6. IBM Cloud Object Storage
7. Webhook

## Before you begin
{: #en-test-destination-prereqs}

Before you can start testing your destinations, you must have the following prerequisites:

* A valid destination configuration.
* Access to the Event Notifications UI or the valid credentials for the API calls.

## Testing your destination
{: #en-test-destinations}

1. Go to the Event Notifications UI.
2. Click the **Destinations** tab.
3. In the row for the destination that you want to test, click the overflow menu ![Overflow Menu](/images/overflow-menu.svg) and then select **Test**. Wait for the test to finish.
4. Review your results. When the test is completed, you are presented with the results. The results typically include the following information.

   - **Status**: Whether the test is successful or failed.
   - **Response Code**: If there is a test failure, the response code from the end destination client is returned.
   - **Response Message**: If there is a test failure, the response message from the end destination client is returned.
   - **Destination Activity**: If test is successful, you see that a test event is delivered to the desired destination, which will create a new message in case of Slack, webhook and Microsoft&reg; Teams, a new incident in case of PagerDuty and ServiceNow, a new invoke in case of IBM Cloud Code Engine, and a new object created under a provided bucket in case of IBM Cloud Object Storage.
