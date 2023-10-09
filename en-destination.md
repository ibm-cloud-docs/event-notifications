---

copyright:
  years: 2021, 2023
lastupdated: "2023-09-25"

keywords: event-notifications, event notifications, about event notifications, destinations, event destination

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Event destinations
{: #en-destination}

A destination is a delivery target for a notification. In other contexts, destinations are also called channels, sinks, or consumers.
{: shortdesc}

## Destination categories
{: #en-destination-categories}

Destinations are of two categories: human and service.

### Human destinations
{: #en-destination-human-1}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported by the {{site.data.keyword.en_short}} service:

- [Inbuilt Email](/docs/event-notifications?topic=event-notifications-en-destinations-email)
- [IBM Cloud Email service with custom domain](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email)
- [Inbuilt SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
- [Microsoft&reg; Teams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams)
- [PagerDuty](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty)
- [Push notifications](/docs/event-notifications?topic=event-notifications-en-destinations-push)
   - [Android Push Notifications (FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
   - [iOS Push Notifications (APNs)](/docs/event-notifications?topic=event-notifications-en-push-apns)
   - [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
   - [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
   - [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)
   - [Huawei Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-huawei)
- [Slack](/docs/event-notifications?topic=event-notifications-en-destinations-slack)
- [ServiceNow](/docs/event-notifications?topic=event-notifications-en-destinations-servicenow)

Both Email and SMS destinations are provided out of the box, and are available whenever you create an instance of {{site.data.keyword.en_short}}. {{site.data.keyword.cloud_notm}} push notification service must be added manually and requires configuration.

### Service destinations
{: #en-destination-service-1}

Service destinations are cloud services or application where notifications are consumed programmatically. The following service destination is supported by the {{site.data.keyword.en_short}} service:

- [Webhook](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
- [{{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-functions)
- [{{site.data.keyword.codeengineshort}}](/docs/event-notifications?topic=event-notifications-en-destinations-codeengine)
- [{{site.data.keyword.cos_full_notm}}](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-object-storage)

### Test destinations
{: #en-destination-test}

This functionality allows you to test a destination with just a single click. The feature simplifies the process of verifying whether a destination is functioning correctly. Currently this functionality supports following destinations:

1. Slack
2. PagerDuty
3. ServiceNow
4. Microsoft&reg; Teams
5. IBM Cloud Code Engine
6. IBM Cloud Functions

By following the steps outlined below, you will be able to quickly and efficiently ensure the integrity of your connections.

### 1. Prerequisites

Before using this feature, ensure you have the following prerequisites:

- A valid destination configuration
- Access to the Event Notifications UI or valid credentials for the API calls

### 2. Accessing the Feature

1. Navigate to the destinations tab from the left navigation menu on the UI or get the required credentials to run the Test API.
2. In front of each destination you need to click on the 3 dots and select the `Test` option.

### 3, Initiating the Test

1. Click on the `Test` option to wait for the test to complete

### 4. Viewing Test Results

Once the test is completed, you will be presented with the results. These results will typically include:

- **Status**: Whether the test is successful or failed
- **Response Code**: If test fails, then the response code sent from the end destination client is returned
- **Response Message**: If test fails, then the response message sent from the end destination client is returned
