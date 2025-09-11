---

copyright:
  years: 2021, 2024
lastupdated: "2024-10-07"

keywords: event-notifications, event notifications, about event notifications, destinations, event destination

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Working with event destinations
{: #en-destination}

A destination is a delivery target for a notification. In other contexts, destinations are also called channels, sinks, or consumers.
{: shortdesc}

## Destination categories
{: #en-destination-categories}

Destinations are of two categories: human and service.

### Human destinations
{: #en-destination-human-1}

Human destinations are devices, servers, or applications that present notifications for human consumption. The following human destinations are supported by the {{site.data.keyword.en_short}} service:


- [Email Destinations](/docs/event-notifications?group=email-destinations)
   - [Inbuilt Email](/docs/event-notifications?topic=event-notifications-en-destination-email-destination-default)
   - [IBM Cloud Email service with custom domain](/docs/event-notifications?topic=event-notifications-en-destinations-custom-email)
- [SMS Destinations](/docs/event-notifications?group=sms-destinations)
   - [Inbuilt SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms)
   - [Custom SMS](/docs/event-notifications?topic=event-notifications-en-destinations-sms-custom)
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

The Inbuilt Email and Inbuilt SMS destinations are provided out of the box, and are available whenever you create an instance of {{site.data.keyword.en_short}}. Other destinations must be added manually and require configuration.

### Service destinations
{: #en-destination-service-1}

Service destinations are cloud services or application where notifications are consumed programmatically. The following service destination is supported by the {{site.data.keyword.en_short}} service:

- [Webhook](/docs/event-notifications?topic=event-notifications-en-destinations-webhook)
- [{{site.data.keyword.codeengineshort}}](/docs/event-notifications?topic=event-notifications-en-destinations-codeengine)
- [{{site.data.keyword.cos_full_notm}}](/docs/event-notifications?topic=event-notifications-en-destinations-cloud-object-storage)
- [{{site.data.keyword.messagehub}}](/docs/event-notifications?topic=event-notifications-en-destinations-event-streams&interface=ui)
