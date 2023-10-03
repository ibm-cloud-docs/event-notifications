---

copyright:
  years: 2020, 2023
lastupdated: "2023-02-09"

keywords: event-notification, event notification, faqs, Frequently Asked Questions, question, billing, service, invalid devices, device deletion, database

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for {{site.data.keyword.en_short}}
{: #en-faqs-operations}

FAQs for {{site.data.keyword.en_short}} provide answers to common operations issues.
{: shortdesc}

## Why are messages reported as delivered but not received by the user?
{: #faq-en-message}
{: faq}

Sometimes messages are reported as delivered but are not received by the user for the following reasons:

- They are rejected by the telecom operator. If the same message is repeated over a span of time, messages are classified as SPAM message by the operator.

A resolution is to add any `TransactionID` or `ReferenceID` to the message body. These IDs classify the SMS as transactional, and is not blocked by the operator.

- The user opts out. If the user opts out from messaging by sending opt-out text like `Opt Out`, `Stop`, or `Exit`, then messages do not reach that user and the status report states that. The user can send an `Opt in` message to the same source to restart receiving messages.

## Why do some devices are marked invalid and deleted from database?
{: #faq-en-invalid-device-deletion}
{: faq}

Sometimes the devices are marked invalid and deleted from database, if they meet these invalid conditions:

- **FCM or Android devices**:

   - `invalidRegistration` - might be due to incorrect registration token format passed to the server.
   - `MismatchSenderID` - a mismatch in the senderID who is not part of the user group that is tied to a registration token.
   - `NotRegistered` - an invalid registration token due to various reasons (like client app getting unregistered with FCM, tokens are invalid, registration token expires, client app that is updated but the new version that is not configured to receive messages).

   For more information, see [FCM error response codes for downstream messages](https://firebase.google.com/docs/cloud-messaging/http-server-ref#error-codes){: external}.

- **APNS or Safari devices**:

   - `Unregistered` - the device token is not active for the specified topic.
   - `BadDeviceToken` - the specified device token is invalid.
   - `DeviceTokenNotForTopic` - the device token doesn’t match the specified topic (bundle ID).

   For more information on how to handle notification responses from apps, see [here](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/handling_notification_responses_from_apns){: external}.

- **Chrome or Firefox devices**:
   - `NotFound` - the subscription is expired and can’t be used.
   - `Gone` - the subscription is no longer valid.

   For more information, see [web push protocol](https://web.dev/push-notifications-web-push-protocol/).


## What is the difference between {{site.data.keyword.en_short}} Topic Subscriptions and {{site.data.keyword.en_short}} Tag Subsciptions to push devices?
{: #faq-en-topic-tag-subscriptions}
{: faq}

- **{{site.data.keyword.en_short}} Topic subscriptions**:

   For the topic subscriptions, start by creating a **Topic** and write conditions on that topic. This topic is responsible for routing the incoming notification that satisfies the topic conditions.

   You can subscribe to multiple {{site.data.keyword.en_short}} destinations like email, SMS, webhooks, slack, and Microsoft teams. Also, you can subscribe push type destinations like android, iOS, Firefox, chrome, and safari.

   If the incoming notifications satisfy the condition written for Topic (T), it routes the notification to all the destinations subscribed or connected to Topic (T) irrespective of the type of destinations.

   For example, `ACME` Bank wants to route maintenance event notifications to customers by using android and iOS devices. Acme Bank is following these steps:

   1. Create a topic named `ACME-Maintenance`.
   1. Write Advance condition `$.notification-type == 'maintenance'`.
   1. Subscribe push android and push iOS destinations to the above topic.
   1. Next, send an event notification with payload containing attribute ``"notification-type":"maintenance"``and ``"ibmenpushto": "{\"platforms\":[\"push_android\",\"push_ios\"]]}"``, `notification-type` attribute is added so that it matches against the topic condition and `ibmenpushto` for targeting customers with android and iOS devices.
   1. {{site.data.keyword.en_short}} will get routed to customers with android and iOS devices, since its payload contains ``"notification-type":"maintenance"`` which matches the condition for Topic `ACME-Maintenance` and ``"ibmenpushto": "{\"platforms\":[\"push_android\",\"push_ios\"]]}"`` as `ibmenpushto` is mandatory for push type {{site.data.keyword.en_short}} destinations.

   All push devices will get registered under {{site.data.keyword.en_short}} destination of type push. For example, `push-android`, `push-ios`, and others.
   {: note}

- **{{site.data.keyword.en_short}} Tag subscriptions to push devices**

   For example, `ACME` Bank wants to route maintenance event notifications to customers by using android and iOS devices. ACME Bank maintenance usually takes place in one region at a time.

   ACME Bank wants to register each of their customer's android and iOS devices under region-specific tags.

   1. To achieve this the bank can use {{site.data.keyword.en_short}} Android Client SDK and iOS Client SDK to subscribe to `Asia Pacific` customers' android and iOS devices under the `AP` tag.

   Follow the below links on how to subscribe tag to push devices by using {{site.data.keyword.en_short}} client SDKs:
   - [Android Push Notifications (FCM)](/docs/event-notifications?topic=event-notifications-en-push-fcm)
   - [iOS Push Notifications (APNs)](/docs/event-notifications?topic=event-notifications-en-push-apns)
   - [Chrome Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-chrome)
   - [Firefox Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-firefox)
   - [Safari Push Notifications](/docs/event-notifications?topic=event-notifications-en-push-safari)
   {: note}

   1. Next, the bank sends a notification with payload containing attribute ``"notification-type":"maintenance"``and ``"ibmenpushto": "{\"tags\":[\"AP\""]]}"``, `notification-type` attributes is added so that it matches against the topic condition and `ibmenpushto` as the message is for targeting push customers with android and iOS devices in Asia Pacific region `AP`.

## Why don't I see Email or SMS notifications that I have sent after configuring {{site.data.keyword.en_short}} for Email and SMS?
{: #faq-en-message-email-sms}
{: faq}

Email and SMS are supported only for {{site.data.keyword.IBM_notm}} Managed Sources ({{site.data.keyword.cloud_notm}} services). You can send a notification from API source to all other destinations, except Email and SMS.

## Where do I specify the Slack channel name in the Slack Destination configuration?
{: #faq-en-slack-destination}
{: faq}

{{site.data.keyword.en_short}} supports the Slack destination using Slack's “Incoming Webhook” feature. An incoming webhook is linked directly to a Slack channel. Hence, there is no need to separately specify the Slack channel.

## Is it possible to customize the message that is generated from {{site.data.keyword.cloud_notm}} services (({{site.data.keyword.cloud_notm}} sources)?
{: #faq-en-sms-customize}
{: faq}

You cannot customize messages that are generated from {{site.data.keyword.cloud_notm}} services (({{site.data.keyword.cloud_notm}} sources). These notifications are generated by the respective {{site.data.keyword.cloud_notm}} service such as {{site.data.keyword.secrets-manager_short}}, and {{site.data.keyword.compliance_short}}. The message content cannot be modified by the end user before it is sent out to a destination.

## Why do I get a 422 error response for the Send Notifications API call?
{: #faq-en-send-notification-error-422}
{: faq}

{{site.data.keyword.en_short}} service is unable to process your request. This is usually seen when there is no condition or filter associated with the topic to which the notification is sent. Check your topic and verify that it is connected to the correct source, with the intended conditions.

## Why my email notifications sent didn’t reach customers even though in the logs I can see successfully sent notifications?
{: #faq-en-email-notifications-missing}
{: faq}

This may be due to your {{site.data.keyword.en_short}} instance has a subscription created for the smtp_ibm destination and has no email ID added as a recipient to the list for the subscription.

Make sure your {{site.data.keyword.en_short}} instance has a subscription created for the smtp_ibm destination and has at least one email ID added as a recipient to the list for the subscription.

## Is it possible to send notifications to more than one destination using Event Notifications?
{: #faq-en-notifications-multiple-destination}
{: faq}

Yes. You can send notifications to more than one destination.

## What is the difference between a custom domain email destination and an IBM Cloud email destination for event notifications?
{: #faq-en-notifications-email-destinations}
{: faq}

Emails sent via an IBM Cloud email destination are sent on behalf of IBM Cloud from a source (i.e., The sender's email domain will always have ".event-notifications.cloud.ibm.com"). On the other hand, a custom email destination allows you to add your own domain address through which a sender can send emails.

Also, API sources cannot send notifications to IBM Cloud email destination, because of the security reasons, on the other hand, a custom domain email destination can receive notifications from any kind of source.

## What is SPF verification?
{: #faq-en-notifications-spf-verification}
{: faq}

SPF (Sender Policy Framework) verification is an email authentication method designed to prevent email spoofing and phishing by allowing email recipients to verify that an email message originates from an authorized source. SPF works by defining a list of authorized mail servers (IP addresses) for a particular domain. When an email is received, the recipient's mail server can check whether the sending mail server's IP address is on the list of authorized servers for the sender's domain.

SPF helps prevent unauthorized sources from sending emails on behalf of a domain, reducing the likelihood of phishing attacks and spam. However, it's important to note that SPF alone does not provide end-to-end email security. Other email authentication mechanisms, such as DKIM (DomainKeys Identified Mail) and DMARC (Domain-based Message Authentication, Reporting, and Conformance), are often used in combination with SPF for a more comprehensive email authentication and anti-phishing strategy.

## What is DKIM verification?
{: #faq-en-notifications-dkim-verification}
{: faq}

DKIM (DomainKeys Identified Mail) verification is an email authentication method used to verify the authenticity and integrity of email messages. DKIM helps prevent email spoofing, phishing, and tampering by allowing email recipients to check whether an email message was sent from an authorized source and whether it has been altered during transit.

DKIM verification provides a strong mechanism for email authentication because it cryptographically verifies the sender's identity and ensures the email's integrity. It's often used in conjunction with other email authentication methods like SPF (Sender Policy Framework) and DMARC (Domain-based Message Authentication, Reporting, and Conformance) to provide a comprehensive email security framework.

By implementing DKIM, domain owners can increase the trustworthiness of their email communications, reduce the likelihood of their domain being used for phishing attacks, and improve email deliverability.

## How does SPF verification work?
{: #faq-en-notifications-spf-verification-works}
{: faq}

1. The sender publishes an SPF Record: The owner of a domain (the sender) publishes an SPF record in their domain's DNS (Domain Name System) records. This SPF record specifies which mail servers are authorized to send email on behalf of that domain.

2. Email Sent: When an email is sent from that domain, the recipient's mail server may perform an SPF check by looking up the SPF record for the sender's domain.

3. SPF Record Check: The recipient's mail server checks if the IP address of the sending mail server is listed in the SPF record as an authorized sender. If it is, the email is considered legitimate; if not, it may be marked as suspicious or rejected.

4. Result: The SPF check produces one of three results:

   - Pass: The sending server's IP address is listed in the SPF record, indicating that the email is legitimate.
   - Fail: The sending server's IP address is not listed in the SPF record, suggesting that the email may be unauthorized.
   - Soft Fail: The SPF record suggests caution, but the email is not immediately rejected.

## How does DKIM verification work?
{: #faq-en-notifications-spf-verification-works}
{: faq}

1. Message Signing: When an email is sent from a domain that has DKIM enabled, the sending mail server digitally signs the email message using a private key. This signature includes information about the email's content and the sender's domain.

2. DNS Record: The sender's domain publishes a DKIM public key in its DNS (Domain Name System) records. This public key is used by receiving mail servers to verify the signature applied in step 1.

3. Email Transmission: The email is transmitted to the recipient's mail server.

4. DKIM Verification: Upon receiving the email, the recipient's mail server performs DKIM verification by retrieving the DKIM public key from the sender's DNS records using the domain found in the "From" header of the email.

5. Signature Verification: The recipient's mail server uses the DKIM public key to verify the digital signature on the email. If the signature is valid, it means that the email has not been tampered with during transit and that it originated from an authorized source.

6. Result: The DKIM verification process results in one of the following outcomes:

   - Pass: The email's DKIM signature is valid, indicating that the email is legitimate and hasn't been tampered with.
   - Fail: The DKIM signature is invalid or missing, suggesting that the email may be suspicious or forged.

## What is Email personalisation?
{: #faq-en-notifications-email-personalisation}
{: faq}

Email personalization refers to the practice of tailoring email content and messaging to individual recipients or specific groups of recipients based on their preferences, behaviors, demographics, or other data. The goal of email personalization is to create more relevant and engaging email experiences for recipients, which can lead to higher open rates, click-through rates, and conversions.

## What are two types of templates?
{: #faq-en-notifications-template-types}
{: faq}

There are two types of templates: Invitation templates and Notification templates. An Invitation template is used to send customized email invitations to all those added to the subscriptions, while a Notification template is used when sending an email for an event. It can include HTML tags, handlebars support, and personalization support.
