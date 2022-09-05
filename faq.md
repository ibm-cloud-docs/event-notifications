---

copyright:
  years: 2020, 2022
lastupdated: "2022-07-21"

keywords: event-notification, event notification, faqs, Frequently Asked Questions, question, billing, service, invalid devices, device deletion, database

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:faq: data-hd-content-type='faq'}

# Operations FAQs for {{site.data.keyword.en_short}}
{: #en-faqs-operations}

FAQs for {{site.data.keyword.en_short}} provide answers to common operations issues.
{: shortdesc}

## Why are messages reported as delivered but not received by the user?
{: #faq-en-message}
{: faq}

Sometimes messages are reported as delivered but are not received by the user for the following reasons:

- They are rejected by the telecom operator. If the same message is repeated over a span of time, messages are classified as SPAM message by the operator.

A resolution is to add any `TransactionID` or `ReferenceID` to the message body. These IDs classify the SMS as transactional, and is not blocked by the operator.

- The user opts out. If the user opts out from messaging by sending opt-out text like `Opt Out`, `Stop` or `Exit`, then messages do not reach that user and the status report states that. The user can send an `Opt in` message to the same source to restart receiving messages.

## Why do some devices are marked invalid and deleted from database?
{: #faq-en-invalid-device-deletion}
{: faq}

Sometimes the devices are marked invalid and deleted from database, if they meet these invalid conditions:

- **FCM or Android devices**:

   - `invalidRegistration` - may be due to incorrect registration token format passed to the server.
   - `MismatchSenderID` - a mismatch in the senderID who is not part of the user group tied to a registration token.
   - `NotRegistered` - an invalid registration token due to various reasons (like client app getting unregistered with FCM, APNs tokens are invalid, registration token expires, client app updated but the new version not configured to receive messages). 

   For more information of error codes, see [FCM error response codes for downstream messages](https://firebase.google.com/docs/cloud-messaging/http-server-ref#error-codes){: external}.

- **APNS/Safari devices**:

   - `Unregistered` - the device token is inactive for the specified topic.
   - `BadDeviceToken` - the specified device token is invalid.
   - `DeviceTokenNotForTopic` - the device token doesn’t match the specified topic (bundle id).

   For more information on how to handle notification responses from apps, see [here](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/handling_notification_responses_from_apns){: external}.

- **Chrome or Firefox devices**:
   - `NotFound` - the subscription is expired and can’t be used.
   - `Gone` - the subscription is no longer valid. 

   For more information on the web push protocol, see [here](https://web.dev/push-notifications-web-push-protocol/).


## What is the difference between EN Topic Subscriptions and EN Tag Subsciptions to push devices?


**EN Topic Subscriptions**:
For the topic subscription, we start by creating a Topic and writing conditions on that topic.
This topic is responsible for routing the incoming notification which satisfies the topic condition.

We can subscribe to multiple EN destinations like email, SMS, webhooks, slack, and Microsoft team.
Also, we can subscribe push type destinations like android, ios firefox, chrome, and safari.

So if incoming notifications satisfy the condition written for Topic (T), it will route the notification to all the destinations subscribed or connected to Topic (T) irrespective of the type of destinations.


For example, let's say an `ACME` Bank wants to route maintenance event notifications to android and ios devices customers.
Acme Bank will follow the below steps
1) Create a topic named `ACME-Maintenance`.
2) Write Advance condition `$.notification-type == 'maintenance'`.
3) Subscribe push android and push ios destinations to the above topic.
4) Next they send a event notification with payload containing attribute   ``"notification-type":"maintenance"``and ``"ibmenpushto": "{\"platforms\":[\"push_android\",\"push_ios\"]]}"``, `notification-type` attribute is added so that it matches against the  topic condition and `ibmenpushto` because we are targeting customers with android and ios devices.

5) Event notification will get routed to customers with android and ios devices, since its payload contains ``"notification-type":"maintenance"`` which matches the condition for Topic `ACME-Maintenance` and ``"ibmenpushto": "{\"platforms\":[\"push_android\",\"push_ios\"]]}"`` as `ibmenpushto` mandatory for push type EN destinations.


***Note:*** All push devices will get registered under EN destination of type push. For example `push-android` , `push-ios`, etc.


**Tag Subscription to push devices**

Now in the above example let's say ACME Bank maintenance usually takes place in one region at a time.

ACME Bank wants to register each of their customer's android and ios devices under region-specific tags.

1) To achieve this they can use EN Android Client SDK and IOS Client SDK to subscribe to `Asia Pacific` customers' android and ios devices under the `AP` tag.
Follow the below links on how to subscribe tag to push devices using EN client SDKs

 - [Android Push Notifications (FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
 - [iOS Push Notifications (APNs)](/docs/event-notifications?topic=event-notifications-en-push-apns)
 - [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
 - [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
 - [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)

2) Next they send a notification with payload contianing attribute   ``"notification-type":"maintenance"``and ``"ibmenpushto": "{\"tags\":[\"AP\""]]}"``, `notification-type` atttribute is added so that it matches against the topic condition and `ibmenpushto` because we are targeting push customers with android and ios devices in Asia Pacific region `AP`.
