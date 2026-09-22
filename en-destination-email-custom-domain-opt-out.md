---

copyright:
  years: 2021, 2026
lastupdated: "2026-09-22"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Custom domain email opt-out functionality
{: #en-destinations-custom-domain-opt-out}

{{site.data.keyword.en_short}} provides an opt-out capability that allows you to send notifications by specifying your preferred email addresses and templates directly in the send notifications payload, without following the standard subscription flow.

The opt-out functionality is not enabled by default. This deliberate choice is rooted in security considerations. Keeping opt-out disabled by default helps prevent potential fraudulent activities and aids in the detection of unauthorized actions, safeguarding sender reputation and user data.

## Requesting the opt-out feature for the custom domain email destination
{: #en-destinations-custom-email-opt-out-request}

By default, the custom domain email destination uses the standard subscription flow. To use the opt-out capability instead, complete the questionnaire described in [Email sender verification questionnaire](/docs/event-notifications?topic=event-notifications-en-email-sender-questionnaire). Answer all questions, including the additional questions for the opt-out request (Q9–Q10).

Upon receiving your answers, if you want to proceed with modifying your email preferences, open a support case with {{site.data.keyword.en_short}}:

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
1. From the Contact support section, click **Create a case**.
1. Select under `Category`, `Topic` as Event Notifications and `Subtopic` as Others
1. Under `Subject` add **Requesting for the Opt Out feature for the Custom Domain Email destination**
1. In the **Description** section, include your responses to the questionnaire from [Email sender verification questionnaire](/docs/event-notifications?topic=event-notifications-en-email-sender-questionnaire).
1. Add **Attachments** if you want to provide more evidence supporting your answers
1. Add required email IDs in the **Watchlist** section. For more information about other options when creating a support case, see [Creating support cases](/docs/support?topic=support-open-case&interface=ui){: external}.

## Flexibility while using Opt-out flow
{: #en-destinations-custom-email-opt-out-rules}

Flexibility within the opt-out flow signifies a user-centric approach, granting individuals the autonomy to personalize their engagement with the service. This empowers users to selectively pick email ids, templates tailoring their experience to align with individual preferences, needs, or changing circumstances. The opt-out flow is designed to be intuitive and adaptable, providing users with seamless control over their interactions and ensuring a more personalized and user-friendly experience.

* Email ID handling rules
    1. Email Ids sent via send notifications payload under `ibmenmailto` key gets preference, even if subscribed email list is already present under connected subscription
    2. If the key `ibmenmailto` is **Absent** in the payload then preference is given to the subscribed email list
* Template handling rules
    1. Template IDs sent via send notifications payload under `ibmentemplates` key gets preference, even if a Notification Template is attached to the subscription.
    2. If the key `ibmentemplates` is **Absent** in the payload then preference is given to the Notification Template in the subscription
    3. If Template is **Absent** in the send notifications payload and also **Absent** in the subscription, then **Email Body** is picked from the `ibmendefaultlong` field from the send notifications payload and **Subject** is picked from the `ibmendefaultshort` field.
    4. If `ibmensubject` field is present in the send notifications payload then the Subject will be picked from the field irrespective of any of the previously described conditions.
