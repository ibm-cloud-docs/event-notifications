---

copyright:
  years: 2021, 2024
lastupdated: "2024-01-03"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 3m

---

{{site.data.keyword.attribute-definition-list}}

## {{site.data.keyword.cloud_notm}} Email Service with default domain
{: #en-destination-email-destination-default}

To use the email service destination, add it to a subscription along with the email addresses of interest. Within a single subscription, you can add up to 100 email recipients. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your email recipients.

If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who opt into the {{site.data.keyword.en_short}} dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you inform the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

After a subscription is created, the list of users in the **Invited** tab automatically receives initial message with information that they are invited to subscribe to the list, which is the "Opt-in" message.

Opt-in message contains user or account who invited the recipient, the name of the subscription, the purpose of the notifications, the frequency of expected notifications, a way to accept or reject the invitation, and expiration time for the invitation.

The {{site.data.keyword.en_short}} are only sent to the opted-in recipients.

You can either resend the invitation or remove the recipient from the **Invited** list. In the **Invited** tab, click and select the three vertical dots (overflow menu) and select **Resend invitation** for the recipient email address, to whom you need to resend the invitation. For deleting a user from the invited list, in the **Invited** tab, click the three vertical dots (overflow menu) and select **Delete** for the recipient email address, to whom you need to remove from the **Invited** list. For adding back a recipient after opted-out or not responded within the stipulated time that is mentioned in the invite email, you need to send a mail to the **Reply to** email address mentioned in the initial invite mail.
