---

copyright:
  years: 2021, 2026
lastupdated: "2026-09-09"

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

By default, the custom domain email destination uses the standard subscription flow. To use the opt-out capability instead, complete a brief questionnaire to customize your email preferences.

```text
1. Will the nature of the email content be Marketing or Transactional?

2. What is your website's URL?

3. Explain how you plan to use IBM Cloud Event Notifications to send email. To help us process your request, you should answer the following questions:

  a. What is your strategy for creating or obtaining your email subscriber list?

  b. What is your approach to managing bounced emails and handling recipient complaints?

  c. What methods do you have in place for recipients to unsubscribe from your email communications?

  d. How did you determine the sending rate or quota specified in your request?

  e. Are you regularly cleaning your email list to remove invalid or outdated email addresses?

4. Indicate the email addresses where you wish to receive account-related communications. You can provide a list of up to four email addresses, separated by commas.

5. In the Event Notifications subscription, you are asked to provide a Reply-To field. Confirm that this is a valid email-id with a mailbox.

6. Include a statement affirming your commitment to sending emails only to individuals who have explicitly requested them, and verify that you have established a procedure for managing bounce and complaint notifications.

7. Provide the reason to use your own procedure to invite or subscribe email ids instead of using the Event Notifications provided  invitation or subscription flow.

8. Whether you have a manual or automated process in place for handling unsubscribes, it's important to provide an "unsubscribe" link in the email payload you send. When recipients decide not to receive further emails, they can simply click on the 'unsubscribe' link and remove their email address from your mailing list. Add a statement that you agree to have an “unsubscribe” link in the email payload that you send.

9. Do you have a process in place to validate that the email templates that you use are well formatted? Alternatively, if you send the html content in the notification payload, do you have a process to validate this content is well formatted?

10. Provide your Event Notifications Instance/s and Destination-ID/s in which you want to enable Customer managed email Opt-in.
```
{: codeblock}

Upon receiving answers to the previously mentioned questions and if users want to proceed with modifying their email preferences, it is encouraged to initiate the next step by opening a support case with {{site.data.keyword.en_short}}:

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
1. From the Contact support section, click **Create a case**.
1. Select under `Category`, `Topic` as Event Notifications and `Subtopic` as Others
1. Under `Subject` add **Requesting for the Opt Out feature for the Custom Domain Email destination**
1. In the 'Description' section, include responses to the previously mentioned questionnaire. While many questions are self-explanatory, we've provided explanations for a few to help ensure clarity.
    * Provide Nature of email as **`Marketing` or `Transactional`**
        * Marketing email - These emails are distributed to a broad audience. They are a targeted list of prospects or customers containing marketing and promotional content such as to make a purchase, download information.
        * Transactional email - These emails are individualized for each recipient, typically triggered by specific user actions like making a website purchase or requesting a password reset.
    * **Website URL** is required to gain a clearer understanding of the type of content you intend to send.
    * A valid **Reply-To** email ID is required to receive rejected or bounced emails' information.
    * Well-formatted email content is required to prevent emails from being classified as spam by receivers. Emails that are not well-formatted (that is, not HTML) can cause email service providers to classify the messages as spam.
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
