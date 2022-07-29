---

copyright:
  years: 2020, 2022
lastupdated: "2022-07-29"

keywords: event-notifications, event notifications, about event notifications, destinations, email

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

# {{site.data.keyword.cloud_notm}} email service
{: #en-destinations-email}

{{site.data.keyword.en_short}} provides a built-in SMTP server for sending transactional and informational event notification emails to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account. 
{: shortdesc}

The emails originate from `no-reply@cloud.ibm.com` or `event-notifications@cloud.ibm.com`, but you can add your own reply-to address. Except for test emails, the content cannot be modified within {{site.data.keyword.en_short}}.

## Adding an email service destination
{: #en-destinations-email-add}

{{site.data.keyword.cloud_notm}} email service is a destination that is provided out-of-the-box. When a new instance is created, you see an entry `{{site.data.keyword.cloud_notm}} Email service` in the destination tab. The email destination is pre-configured, and is ready to use.

## Using an {{site.data.keyword.cloud_notm}} email service destination
{: #en-destinations-email-use}

To use the email service destination, add it to a subscription along with the email addresses of interest. Within a single subscription, you can add up to 100 email recipients. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your email recipients. 

If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who opt into the {{site.data.keyword.en_short}} dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

## Email charges
{: #en-destinations-email-charge}

Every message that is sent by the {{site.data.keyword.cloud_notm}} email service counts as one outbound digital message and is charged. For example, if a subscription has 100 email addresses and the subscription topic received 1000 events during the month is as follows:

Total Outbound Digital Messages = (number of email addresses) x (topic events)

In the example, the total outbound digital messages are as follows:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} email service regardless of whether the remote email server successfully delivered the message to the recipient. For example, bounced emails still count as outbound digital messages. So vet your email list carefully to prevent unnecessary charges.

You can monitor your email usage by setting up a monitoring dashboard through the `Actions` menu of the {{site.data.keyword.en_short}} dashboard. See [Monitor Event Notifications service metrics with IBM Cloud Monitoring](/docs/event-notifications?topic=event-notifications-en-monitoring#en-monitoring) for details.

## Unsubscribe 
{: #en-unsubscribe-email-destination}

You can subscribe to or unsubscribe from specific Event Notification email notifications. Also, users can opt out of receiving notifications for any subscription.

The **Active** tab displays the list of recipients email addresses and the date activated. The **Unsubscribed** tab displays the list of recipients who don't want to receive any email notification.

To unsubscribe, do the following:
- Under email subscription, click the `Unsubscribed` dialog to modify subscription settings and unsubscribe from mailing lists. 
- Select or deselect the `Unsubscribed` dialog, this automatically reflects in the subscription wizard. 
	 
-The role of an Admin:
- Only an admin can move or modify an unsubscribed email id to `Active`.
- Only an admin can clear unsubscribed email lists. 
- An admin cannot manually move or add users to the unsubscribed list.
