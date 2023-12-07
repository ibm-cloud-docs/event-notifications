---

copyright:
  years:  2023
lastupdated: "2023-10-10"

keywords: event notifications, event notification, notifications, integrations, destinations, test destinations

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Test destinations
{: #en-test-destination}

This document explains a feature designed to streamline the way you validate the functionality and reliability of your critical connections. With this functionality, you can effortlessly test a destination with a single click, whether it's a Slack hook or complex ServiceNow configuration.

In today's interconnected digital landscape, maintaining the health and integrity of your connections is paramount. Ensuring your destinations deliver events reliably and connection to the third party apps is always up to date is vital.

Our new feature empowers you to tackle this challenge with ease. Gone are the days of complex testing procedures and convoluted configurations. Instead, we've simplified the process, allowing you to quickly and efficiently assess the performance and correctness of your destinations.

So, let's embark to explore the capabilities of this feature, learn how to harness its power, and ensure that your digital destinations are always at their best.

Currently this functionality supports following destinations:

1. Slack
2. PagerDuty
3. ServiceNow
4. Microsoft&reg; Teams
5. IBM Cloud Code Engine
6. IBM Cloud Functions
7. IBM Cloud Object Storage

By following the steps outlined below, you will be able to quickly and efficiently ensure the integrity of your connections.

## 1. Prerequisites
{: #en-test-destination-prereqs}

Before using this feature, ensure you have the following prerequisites:

- A valid destination configuration
- Access to the Event Notifications UI or valid credentials for the API calls

## 2. Accessing the Feature
{: #en-test-destination-accessing-feature}

1. Navigate to the destinations tab from the left navigation menu on the UI or get the required credentials to run the Test API.
2. To test each destination, simply click on the three dots and select the 'Test' option.

## 3. Initiating the Test
{: #en-test-destination-initiating-test}

1. Select the 'Test' option and wait for the test to finish.

## 4. Reviewing Test Results
{: #en-test-destination-reviewing-results}

Once the test is completed, you will be presented with the results. These results will typically include:

- **Status**: Whether the test is successful or failed.
- **Response Code**: In the event of a test failure, the response code from the end destination client is returned.
- **Response Message**: In the event of a test failure, the response message from the end destination client is returned.
- **Destination Activity**: If test is successful, you will see a test event delivered onto the desired destination, which will create a new message in case of Slack, Microsoft&reg; Teams, a new incident in case of PagerDuty and ServiceNow, a new invoke in case of IBM Cloud Code Engine, and IBM Cloud Functions, and at last a new object created under a provided bucket in case of IBM Cloud Object Storage.
