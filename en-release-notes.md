---

copyright:
  years: 2021, 2022
lastupdated: "2022-09-27"

keywords: event-notifications, event notifications, about event notifications

subcollection: event-notifications

content-type: release-note

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:release-note: data-hd-content-type='release-note'}

# Release notes for {{site.data.keyword.en_short}}
{: #release-notes}

Looking for {{site.data.keyword.cloud_notm}} status, platform announcements, security bulletins, or maintenance notifications? See [{{site.data.keyword.cloud_notm}} status](https://cloud.ibm.com/status?selected=status).
{: note}

## 27 Sep 2022
{: #event-notifications-Sep2722}
{: release-note}

New supported {{site.data.keyword.cloud_notm}} source: {{site.data.keyword.cloud_notm}} Platform Notifications
:  {{site.data.keyword.cloud_notm}} Platform Notifications is now available as new supported {{site.data.keyword.cloud_notm}} source. For more information, see [Enabling Event Notifications for the notification distribution list](https://cloud.ibm.com/docs/account?topic=account-add-users-distribution-list#event-notifications-distribution-list).

## 29 Aug 2022
{: #event-notifications-Aug2522}
{: release-note}

New destination: {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}
:  {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}} is now available as a destination. You can send notifications to your {{site.data.keyword.openwhisk_short}} instance using Event Notifications. [Send notifications to your {{site.data.keyword.openwhisk_short}} instance using Event Notifications](/docs/event-notifications?topic=event-notifications-en-destinations--cloud-functions).

Support for changing a **Pre-production destination** to **Production destination**
:  You can now change a **Pre-production destination** to **Production destination** after your development and testing. For more information, see [Modify a Pre-production destination to Production destination](/docs/event-notifications?topic=event-notifications-en-create-en-destination#en-destination-preprod-prod).

## 16 Aug 2022
{: #event-notifications-Aug1622}
{: release-note}

Support for Private endpoints
:  To ensure that you have enhanced control and security over your data when you use Event Notifications, you have the option of using private routes to {{site.data.keyword.cloud_notm}} service endpoints. For more information, see [Using service endpoints to privately connect to Event Notifications](/docs/event-notifications?topic=event-notifications-en-service-connection).

## 31 Jul 2022
{: #event-notifications-July3122}
{: release-note}

New Pre-production destination
:  You can now use **Pre-production destination**, as low-cost push destination, for your development and test environments. For more information, see [{{site.data.keyword.cloud_notm}} Push notification service](/docs/event-notifications?topic=event-notifications-en-destinations-push).

Support for SMS opt-out
:  You can now monitor users who opt out for receiving SMS. For more information, see [{{site.data.keyword.cloud_notm}} Push notification service](/docs/event-notifications?topic=event-notifications-en-destinations-sms).

## 29 Jun 2022
{: #event-notifications-June2922}
{: release-note}

New destination: Microsoft Teams
:  Microsoft Teams is now available as a destination. You can send notifications to your Microsoft Teams using Event Notifications. [Send notifications to your Teams using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-destinations-msteams).

## 31 May 2022
{: #event-notifications-May3122}
{: release-note}

New destination: Slack
:  Slack is now available as a destination. You can send notifications to your slack channels using Event Notifications. [Send notifications to your slack channels using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-destinations-slack).


## 29 Apr 2022
{: #event-notifications-Apr2922}
{: release-note}

New destinations: Web Push Notifications for Chrome and Firefox
:   Push Notifications to Chrome is now available as a destination. Send push notifications from your application to Chrome. For more information, see [Create and send push notifications to Chrome web using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome).
:   Push Notifications to Firefox is now available as a destination. Send push notifications from your application to Firefox. For more information, see [Create and send push notifications to Firefox web using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox).

## 25 Mar 2022
{: #event-notifications-Mar2522}
{: release-note}

Event Notifications is now available in the Frankfurt region.

## 28 Feb 2022
{: #event-notifications-Feb2822}
{: release-note}

New destination: Apple Push Notification Service (APNs) for iOS
:   Push Notifications to iOS (APNs) is now available as a destination. Send push notifications from your application to iOS devices. For more information, see [Create and send push notifications to iOS mobile using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-push-apns).

## 03 Feb 2022
{: #event-notifications-Feb0322}
{: release-note}

New source: {{site.data.keyword.secrets-manager_full}}
:   Integrating {{site.data.keyword.secrets-manager_short}} with Event Notifications can help you route life cycle events for your secrets by using supported channels. For more information, see [Enabling event notifications for Secrets Manager](/docs/secrets-manager?topic=secrets-manager-event-notifications&interface=ui).

## 31 Jan 2022
{: #event-notifications-Jan3122}
{: release-note}

New destination: Firebase Cloud Messaging (FCM) push notifications for Android
:   Push Notifications for Android devices (FCM) is now available as a destination. Send push notifications from your application to Android devices. For more information, see [Create and send push notifications to Android mobile using IBM Cloud® Event Notifications](/docs/event-notifications?topic=event-notifications-en-push-fcm).

## 14 Dec 2021
{: #event-notifications-Dec1421}
{: release-note}

New source: {{site.data.keyword.compliance_full}}
:   Integrating {{site.data.keyword.compliance_short}} with Event Notifications can help you route security events via supported channels. For more information, see [Enabling event notifications for {{site.data.keyword.compliance_short}}](/docs/security-compliance?topic=security-compliance-event-notifications&interface=ui).

## 28 Oct 2021
{: #event-notifications-Oct2821}
{: release-note}

Introducing Event Notifications
:   Event Notifications is Generally Available. IBM Cloud Monitoring as a source is supported to route events to communication channels like email, SMS and webhooks.
