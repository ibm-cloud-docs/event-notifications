---

copyright:
  years: "2025, 2026"
lastupdated: "2026-09-01"

keywords: event-notifications, metrics for email notifications, monitor metrics

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring metrics for email notifications
{: #en-manage-monitor-metrics}

In {{site.data.keyword.en_full}}, you can track metrics for email notifications sent through custom domain email and SMTP, such as the number of emails delivered. This allows you to analyze customer behavior in real time and optimize your communication strategy.
{: shortdesc}

## How can I view metrics?
{: #en-view-metrics}

To monitor metrics for email notifications sent from either a custom domain or an SMTP, click **Metrics** on your provisioned {{site.data.keyword.en_short}} instance in the console.

## Filtering metrics
{: #en-filter-metrics}

You can use the filters available in the console to specify specific time periods or types of data that you want to review. By reviewing your metrics, you can infer information about your customer database that can inform your notification strategy. From your metrics, you are able to see the following information:

	* **Email address**: The email address of the receiver.
	* (Custom only) **Subscription**: The subscription to which the notifications are sent.
	* (SMTP only) **Timestamp**: The timestamp of the bounced notification.
	* **Bounce Reason**: The reason behind the notification bounce.
	* **Subject**: The subject of the bounced email.

## How can I filter metrics for emails that are sent from a custom domain?
{: #en-filter-email-metrics-customDomain}

To view metrics for email notifications that are sent from custom domains, you can filter it according to the following options.

1. In the **Attributes** section, select **Custom email** from the **Destination type** options.
2. Filter your attributes by using following options in the **Where** menu.

   * Notification ID
   * Destination name
   * Source name
   * Email to
   * Subject
   * Subscription name

	The values provided for Notification ID, Email to, and Subject must be exact if they are used as filter criteria. You can slect required values from destination name and source name if they are used as criteria to filter.
	{: tip}

3. Select a pre-defined time period such as **Last 24 hours**, **Last 7 days**, or **Last 30 days**, or provide specific dates that you want to review.


## How can I filter metrics for emails that are sent from an SMTP?
{: #en-filter-email-metrics-smtp}

To view metrics for email notifications that are sent from an SMTP, you can filter it according to the following options.

1. In the **Attributes** section, select **SMTP configuration** from the **Destination type** options.
2. Select the **SMTP configuration** that you are working with from the **Select** menu.
3. Filter your attributes by using following options in the **Where** menu.

   * SMTP user name
   * Email from
   * Email to
   * Subject

	The values provided must be exact if they are used as filter criteria in order for the search to be successful.
	{: tip}

4. Select a pre-defined time period such as **Last 24 hours**, **Last 7 days**, or **Last 30 days**, or provide specific dates that you want to review.

## How do I know whether my email was received?
{: #en-notifications-email-bounce-rate}

By reviewing your metrics, you can see which emails were not received because they bounced.

	* **Email address**: The email address of the receiver.
	* (Custom only) **Subscription**: The subscription to which the notifications are sent.
	* (SMTP only) **IP Address**: The IP address of the sender
	* **Timestamp**: The timestamp of the bounced notification.
	* **Bounce Reason**: The reason behind the notification bounce.
	* **Subject**: The subject of the bounced email.

## Downloading metrics?
{: #en-download-metrics}

To download Event Notifications metrics to your local system, you can use the following steps.

1. In the Event Notifications UI go to **More** > **Export to [desired format]**
2. Select the type of format that you want to export to. Options include **CSV**, **PNG**, and **JPG**.
