---

copyright:
  years: 2021, 2024
lastupdated: "2024-01-03"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Email Destinations
{: #en-destinations-email}

{{site.data.keyword.en_short}} provides the followng two Email Destination types.
{: shortdesc}

- [Inbuilt Email](/docs/event-notifications?topic=event-notifications-en-destination-email-destination-default)
Inbuilt Email destination provides a SMTP relay for sending transactional and informational event notification emails to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account. This destination can be used to send email notifications for events originating only from IBM Cloud sources.  The content cannot be modified within {{site.data.keyword.en_short}}. This destination is provided out of the box, and is available whenever you create an instance of {{site.data.keyword.en_short}}. These emails originate from `no-reply@cloud.ibm.com` or `event-notifications@cloud.ibm.com`, while you can add your own reply-to address. 

- [IBM Cloud Email service with custom domain](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain)
Custom Domain Email destination empowers you to tailor your communication by adding your own domain. You now have the flexibility to send emails using the email address associated with your specific domain, creating a personalized touch to your correspondence, by sending your own email content. In addition, this destination type also supports Email Templates and Personalization. 


## Adding an email service destination
{: #en-destinations-email-add}

Upon the creation of a new {{site.data.keyword.en_short}} instance, you will notice the presence of the  pre-configured `{{site.data.keyword.cloud_notm}} Email Service` in the destination tab. This pre-configured email destination is poised to meet your immediate communication needs, providing a hassle-free setup for instant usability. Follow [the detailed steps](/docs/event-notifications?topic=event-notifications-en-destination-email-destination-default) to get started with default domain email destination.

If you would like to send your own content in the email or send emails from your own domain, then choose `Custom Email`. Click on  Add destinations, and select`Custom Email` destination to create a new destination. Follow [the detailed steps](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain) to get started with custom domain email destination.

Read through and follow [the suggested etiquettes](/docs/event-notifications?topic=event-notifications-en-email-bestpractices) when utilizing the IBM Cloud email service.

## Subscription workflow
{: #en-destinations-email-subscription-flow}

Both the {{site.data.keyword.en_short}} Email Destinations support a subscription workflow. This workflow triggers an invitation email to all email-ids which are subscribed to an Email Destination. The invitation contains a link to accept further notification from the subscription. All notificaiton emails will be sent to the subscribed email-id only if the recipent accepts the invitation.  

The followiing diagram shows depicts the workflow, from invited to subscribed and to unsubsubscribed.

![Email state-diagram](images/en-email-state-diagram.png "Email state diagram"){: caption="Figure 1. Email state diagram" caption-side="bottom"}


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

## Email charges
{: #en-destinations-email-charge}

Every message that is sent by the {{site.data.keyword.cloud_notm}} email service counts as one outbound digital message and is charged. For example, if a subscription has 100 email addresses and the subscription topic received 1000 events during the month is as follows:

Total Outbound Digital messages = (number of email addresses) x (topic events)

In the example, the total outbound digital messages are as follows:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} email service regardless of whether the remote email server successfully delivered the message to the recipient. For example, bounced emails still count as outbound digital messages. So vet your email list carefully to prevent unnecessary charges.

You can monitor your email usage by setting up a monitoring dashboard through the `Actions` menu of the {{site.data.keyword.en_short}} dashboard. See [Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.monitoringfull_notm}}](/docs/event-notifications?topic=event-notifications-en-monitoring#en-monitoring) for details.
