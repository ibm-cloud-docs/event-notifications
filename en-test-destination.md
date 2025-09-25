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

1. Go to the {{site.data.keyword.en_short}} console.
2. Click the **Destinations** tab.
3. For the destination that you want to test, click the overflow menu ![Overflow Menu](/images/overflow-menu.svg) and then select **Test**. Wait for the test to finish.
4. When the test is completed, you are presented with the results. Review your results. The results typically include the following information:

   - **Status**: Whether the test is successful or failed.
   - **Response Code**: If there is a test failure, the response code from the end destination client is returned.
   - **Response Message**: If there is a test failure, the response message from the end destination client is returned.
   - **Destination Activity**: If the test is successful, you see that a test event is delivered to the desired destination, which will create a new message in the case of Slack, Webhook and Microsoft&reg; Teams, a new incident in the case of PagerDuty and ServiceNow, a new invoke in the case of {{site.data.keyword.codeenginefull_notm}}, and a new object is created under a provided bucket in the case of {{site.data.keyword.cos_full_notm}}.
