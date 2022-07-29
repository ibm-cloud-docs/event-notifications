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
