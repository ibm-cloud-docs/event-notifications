---

copyright:
  years: 2025
lastupdated: "2025-04-22"

keywords: event-notifications, notifications payload, event sources

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Event source, Event types, and {{site.data.keyword.en_short}} payload details
{: #en-map-source-with-notification}

A source produces events of multiple types and subtypes. The format of the payload changes according to the requirements. It is good to understand the specifics of event types and the notification payload details before you begin sending or receiving the notifications. It helps you to validate and troubleshoot the notifications as well.

The following table links event types, subtypes, and the payload format details for each source.

|Source |Event types and subtypes |Payload format details |
| -------------- | -------------- | -------------- |
|{{site.data.keyword.logs_full_notm}} |[Event types](/docs/cloud-logs?topic=cloud-logs-cl-events-for-en#cl-events-for-en-types) |[Payload format details](/docs/cloud-logs?topic=cloud-logs-event-payload#event-payload-1) |
|Security and Compliance |[Event types](/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui#event-notifications-list) |[Payload format details](/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui#event-notifications-payload) |
|{{site.data.keyword.secrets-manager_short}} |[Event types](/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui#event-notifications-list) |[Payload format details](/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui#event-notifications-payload) |
|{{site.data.keyword.appconfig_short}} |[Event types](/docs/app-configuration?topic=app-configuration-ac-int-en#ac-en-int-events) |[Payload format details](/docs/app-configuration?topic=app-configuration-ac-int-en#ac-int-en-notifications-payload) |
|IBM Cloud Projects |[Event types](/docs/secure-enterprise?topic=secure-enterprise-event-notifications-events&interface=ui#event-notifications-list) |[Payload format details](/docs/secure-enterprise?topic=secure-enterprise-event-notifications-events&interface=ui#event-notifications-payload) |
|Toolchain |[Event types](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd&interface=ui#event-notifications-list-cd) |[Payload format details](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd&interface=ui#event-notifications-payload) |
|IBM Cloud Backup for VPC |[Event types](/docs/vpc?topic=vpc-event-notifications-events&interface=ui#event-notifications-list) |[Payload format details](/docs/vpc?topic=vpc-event-notifications-events&interface=ui#event-notifications-payload) |
|{{site.data.keyword.cloud_notm}} Platform Notifications |[Event types](/docs/account?topic=account-viewing-notifications#notification-types) |[Payload format details](/docs/account?topic=account-add-users-distribution-list#webhook-distribution-list) |
|{{site.data.keyword.cloud_notm}} Resource lifecycle events |[Event types](/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events#en-supported-resource-types) |[Payload format details](/docs/event-notifications?topic=event-notifications-en-resource-lifecycle-events#en-example-event) |
{: caption="Source, event types and subtypes and the payload format details" caption-side="bottom"}
