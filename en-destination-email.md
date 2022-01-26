---

copyright:
  years: 2020, 2021, 2022
lastupdated: "2022-01-25"

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



# {{site.data.keyword.Bluemix_notm}} email service
{: #en-destinations-email}

{{site.data.keyword.en_short}} provides a built-in SMTP server for sending transactional and informational event notification emails to recipients who need to be aware of events happening within your IBM Cloud account.  
{: shortdesc}

The emails originate from `no-reply@cloud.ibm.com` or `event-notifications@cloud.ibm.com`, but you can add your own reply-to address.  Except for test emails, the content cannot be modified within Event Notifications.

## Adding an email service destination
{: #en-destinations-email-add}

{{site.data.keyword.Bluemix_notm}} email service is a destination provided out-of-the-box. When a new instance is created, you will see an entry `{{site.data.keyword.Bluemix_notm}} email service` in the destination tab. The email destination is pre-configured, and is ready to use.


## Using an {{site.data.keyword.Bluemix_notm}} email service destination
{: #en-destinations-email-use}

 To use the email service destination, add it to a subscription along with the email addresses of interest.  Within a single subscription, you can add up to 100 email recipients.   The subscription will also need a topic to filter events of interest from your sources.  When an event lands in the topic, {{site.data.keyword.en_short}} will immediately route the event notification to your email recipients. 

 If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who have opted in the {{site.data.keyword.en_short}} dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{:note: .note}

## Email charges
{: #en-destinations-email-charge}

Every message sent by the {{site.data.keyword.Bluemix_notm}} email service counts as one outbound digital message and is charged accordingly. For example, if a subscription has 100 email addresses and the subscription topic received 1000 events during the month:

Total Outbound Digital Messages = (number of email addresses) x (topic events)

In or example, the total outbound digital messages is:

100 x 1000 = 100000 outbound digital messages

You are charged for messages that are successfully sent by the {{site.data.keyword.Bluemix_notm}} email service regardless of whether or not the not the remote email server successfully delivered the message to the recipient. For example, bounced emails still count as outbound digital messages, so vet your email list carefully to prevent unnecessary charges.

You can monitor your email usage by setting up a monitoring dashboard through the Actions menu in the upper right corner of {{site.data.keyword.en_short}} dashboard.  See the "How To" documentation section for details.