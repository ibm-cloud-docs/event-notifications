---
copyright:
  years: 2021, 2024
lastupdated: "2024-01-03"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications

content-type: tutorial
account-plan: standard
completion-time: 10m
---

{{site.data.keyword.attribute-definition-list}}

# Opting Out of Event Notifications with Custom Domain Email Opt-In
{: #en-destinations-custom-domain-opt-out}

{{site.data.keyword.en_short}} offers users a versatile option to deviate from the conventional subscription process by introducing an opt-out capability. This feature empowers users to seamlessly send notifications, allowing them to specify their preferred email addresses and templates within the send notifications payload. This not only simplifies the notification process but also elevates user control over their communication preferences.

It's worth noting that the opting-out functionality is not activated by default, and this deliberate choice is rooted in security considerations. Enabling the opt-out feature from the start helps prevent potential fraudulent activities and aids in the detection of unauthorized actions. This proactive security measure not only safeguards user data but also contributes to the overall protection of users' reputation as senders. By taking a cautious approach, {{site.data.keyword.en_short}} prioritizes security, ensuring a secure and trustworthy communication environment for its users.

## Requesting for the Opt Out feature for the Custom Domain Email destination
{: #en-destinations-custom-email-opt-out-request}

By default, the subscription flow seamlessly includes the custom domain email destination, providing users with a streamlined experience. However, for those who prefer to opt out, we have implemented a straightforward process. Users can access this option by completing a brief questionnaire that helps customize their email preferences.

This questionnaire ensures that users have the flexibility to tailor their subscription experience according to their specific needs. While the default setting optimizes convenience, the opt-out questionnaire empowers users to make personalized choices, enhancing their control over communication. This user-centric approach aligns with our commitment to providing a customizable and user-friendly platform.

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

**Upon receiving answers to the aforementioned questions and if users wish to proceed with modifying their email preferences, we encourage them to initiate the next step by opening a support case with {{site.data.keyword.en_short}}:**

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
1. From the Contact support section, click **Create a case**.
1. Select under `Category`, `Topic` as Event Notifications and `Subtopic` as Others
1. Under `Subject` add **Requesting for the Opt Out feature for the Custom Domain Email destination**
1. In the 'Description' section, please include responses to the aforementioned questionnaire. While many questions are self-explanatory, we've provided explanations for a few to ensure clarity.
    * Provide **Nature of email as `Marketing` or `Transactional`**
        * Marketing email - These emails are distributed to a broad audience. They are targeted list of prospects or customers containing marketing and promotional content such as to make a purchase, download information, etc.
        * Transactional email - These emails are individualized for each recipient, typically triggered by specific user actions like making a website purchase or requesting a password reset, etc.
    * **Website URL** is required to gain a clearer understanding of the type of content you intend to send.
    * A valid **Reply-To** email id is required to receive rejected or bounced emails' information.
    * Requirement of **Well Formatted** Email content is required to prevent emails classified as Spam at the receivers end. Email which are not well formatted (i.e not html) can result in Email Service Providers to classify the mails as spam.
1. Add **Attachments** if you want to provide more evidences supporting your answers
1. Add required email Ids in the **Watchlist** section. And to know more about other options while creating a support case refer [here](https://{DomainName}/docs/get-support?topic=get-support-open-case){: external}.

## Flexibility while using Opt-out flow

Flexibility within the opt-out flow signifies a user-centric approach, granting individuals the autonomy to personalize their engagement with the service. This empowers users to selectively pick email ids, templates tailoring their experience to align with individual preferences, needs, or changing circumstances. The opt-out flow is designed to be intuitive and adaptable, providing users with seamless control over their interactions and ensuring a more personalized and user-friendly experience.

* **Email-Ids handling rules**
    1. Email Ids sent via send notifications payload under `ibmenmailto` key gets preference, even if subscribed email list is already present under connected subscription
    2. If the key `ibmenmailto` is **Absent** in the payload then preference is given to the subscribed email list
* **Template handling rules**
    1. Template Ids sent via send notifcations payload under `ibmentemplates` key gets preference, even if a Notification Template is attached to the subscription.
    2. If the key `ibmentemplates` is **Absent** in the payload then preference is given to the Notification Template in the subscription
    3. If Template is **Absent** in the send notifications payload and also **Absent** in the subscription, then **Email Body** is picked from the `ibmendefaultlong` field from the send notifications payload and **Subject** is picked from the `ibmendefaultshort` field.
    4. If `ibmensubject` field is present in the send notifications payload then the Subject will be picked from the field irrespective of any of the above conditions.
