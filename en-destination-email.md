---

copyright:
  years: 2021, 2022
lastupdated: "2022-10-17"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} Email service
{: #en-destinations-email}

{{site.data.keyword.en_short}} provides a built-in SMTP server for sending transactional and informational event notification emails to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account.
{: shortdesc}

The emails originate from `no-reply@cloud.ibm.com` or `event-notifications@cloud.ibm.com`, but you can add your own reply-to address. Except for test emails, the content cannot be modified within {{site.data.keyword.en_short}}.

## Adding an email service destination
{: #en-destinations-email-add}

{{site.data.keyword.cloud_notm}} email service is a destination that is provided as ready for immediate use. When a new instance is created, you see an entry `{{site.data.keyword.cloud_notm}} Email service` in the destination tab. The email destination is pre-configured, and is ready to use.

## Using an {{site.data.keyword.cloud_notm}} email service destination
{: #en-destinations-email-use}

To use the email service destination, add it to a subscription along with the email addresses of interest. Within a single subscription, you can add up to 100 email recipients. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your email recipients.

If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who opt into the {{site.data.keyword.en_short}} dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you inform the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

After a subscription is created, the list of users in the **Invited** tab automatically receives initial message with information that they are invited to subscribe to the list, which is the "Opt-in" message.

Opt-in message contains user or account who invited the recipient, the name of the subscription, the purpose of the notifications, the frequency of expected notifications, a way to accept or reject the invitation, and expiration time for the invitation.

The {{site.data.keyword.en_short}} are only sent to the opted-in recipients.

You can either resend the invitation or remove the recipient from the **Invited** list. In the **Invited** tab, click and select the three vertical dots (overflow menu) and select **Resend invitation** for the recipient email address, to whom you need to resend the invitation. For deleting a user from the invited list, in the **Invited** tab, click the three vertical dots (overflow menu) and select **Delete** for the recipient email address, to whom you need to remove from the **Invited** list. For adding back a recipient after opted-out or not responded within the stipulated time that is mentioned in the invite email, you need to send a mail to the **Reply to** email address mentioned in the initial invite mail.

## Email charges
{: #en-destinations-email-charge}

Every message that is sent by the {{site.data.keyword.cloud_notm}} email service counts as one outbound digital message and is charged. For example, if a subscription has 100 email addresses and the subscription topic received 1000 events during the month is as follows:

Total Outbound Digital messages = (number of email addresses) x (topic events)

In the example, the total outbound digital messages are as follows:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} email service regardless of whether the remote email server successfully delivered the message to the recipient. For example, bounced emails still count as outbound digital messages. So vet your email list carefully to prevent unnecessary charges.

You can monitor your email usage by setting up a monitoring dashboard through the `Actions` menu of the {{site.data.keyword.en_short}} dashboard. See [Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.monitoringfull_notm}}](/docs/event-notifications?topic=event-notifications-en-monitoring#en-monitoring) for details.

## Unsubscribe
{: #en-unsubscribe-email-destination}

You can subscribe to or unsubscribe from specific {{site.data.keyword.en_short}} email notifications. Also, users can opt out of receiving notifications for any subscription.

The **Active** tab displays the list of recipients email addresses and the date activated. The **Unsubscribed** tab displays the list of recipients who don't want to receive any email notification.

To unsubscribe, do the following steps:
- Under email subscription, click the `Unsubscribed` dialog to modify subscription settings and unsubscribe from mailing lists.
- Select or deselect the `Unsubscribed` dialog, which automatically reflects in the subscription wizard.

The role of an Admin:
- Only an admin can move or modify an unsubscribed email ID to `Active`.
- Only an admin can clear unsubscribed email lists.
- An admin cannot manually move or add users to the unsubscribed list.
