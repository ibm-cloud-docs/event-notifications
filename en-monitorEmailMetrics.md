---

copyright:
  years: 2025
lastupdated: "2025-06-20"

keywords: event-notifications, metrics for email notifications, monitor metrics

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Monitor {{site.data.keyword.en_full}} metrics for email notifications
{: #en-manage-monitor-metrics}

You can track metrics for email notifications sent through custom domain email and SMTP, such as the number of emails delivered. This allows you to analyze customer behavior in real time and optimize your communication strategy.
{: shortdesc}

To monitor metrics for email notifications sent from custom domain or SMTP,click **Metrics** on your provisioned instance of {{site.data.keyword.en_short}} console.


## View metrics for email notifications
{: #en-view-email-metrics}

You can understand customer behaviour and use this information to optimize your notification strategy.
You can use these metrics to gain insights at any given time.

### View metrics for email notifications sent from custom domain
{: #en-view-email-metrics-customDomain}

To filter metrics for email notifications sent from custom domain email you must select **Destination Type** as **Custom Email** in the **Attributes** section.

To add more filter criteria, click **Filter** and select one of the following attribute from **Where** menu.

1. **Notification ID**

1. **Destination name**

1. **Source name**

1. **Email to**

1. **Subject**

You must provide valid values for **Notification ID** , **Email to** and **Subject** if added to the filter criteria. You can select required values from **Destination name** and **Source name** if added to the filter criteria.

You can view metrics for pre-defined time periods of **Last 24 hours**, **Last 7 days**, or **Last 30 days** or custom defined dates.
It helps you to form a new strategy or modify the existing one depending on the values of the below metrics.

1. **Emails sent** : The total number of emails that are sent to the recipients in the selected time period.

1. **Delivered** : The total number of emails that successfully reach to the recipients in the selected time period.

1. **Failed** : The total number of emails that fail to deliver successfully to the recipients in the selected time period.

1. **Open rate** : The percentage of emails that the receivers open upon delivery.

1. **Bounce rate** : The percentage of emails that do not deliver to the intended recipient and bounce back.

The visual represention using graphs can help you to understand pattern of metrics over a certain time period. You can understand percentage of **Delivered**, **Failed**, and **Opened** mails for the selected time period at a glance.

To download the metrics in your local system, go to **More** &gt; **Export to [desired format]**. Currently, you can export the graphs in CSV, PNG, and JPG formats.

You can also get a glimpse of the total number of **Bounced** or **Opened** notifications for the selected time period.


### View metrics for email notifications sent from SMTP configuration
{: #en-view-email-metrics-customDomain}

To filter metrics for email notifications sent from SMTP you must select **Destination Type** as **SMTP configuration** in the **Attributes** section. You must also choose the required **SMTP Configuration** from the **Select Menu**.

To add more filter criteria, click **Filter** and select one of the following attribute from **Where** menu.

1. **SMTP user name**

1. **Email from**

1. **Email to**

1. **Subject**

You must provide valid values for all the above attributes if added to filter criteria.

You can view metrics for pre-defined time periods of **Last 24 hours**, **Last 7 days**, or **Last 30 days** or custom defined dates.
It helps you to form a new strategy or modify the existing one depending on the values of the below metrics.

1. **Emails sent** : The total number of emails that are sent to the recipients in the selected time period.

1. **Delivered** : The total number of emails that successfully reach to the recipients in the selected time period.

1. **Failed** : The total number of emails that fail to deliver successfully to the recipients in the selected time period.

1. **Bounce rate** : The percentage of emails that do not deliver to the intended recipient and bounce back.


The visual represention using graphs can help you to understand pattern of metrics over a certain time period. You can understand percentage of **Delivered**, and **Failed** mails for the selected time period at a glance.

To download the metrics in your local system, go to **More** &gt; **Export to [desired format]**. Currently, you can export the graphs in CSV, PNG, and JPG formats.

You can also get a glimpse of the total number of **Bounced** notifications for the selected time period.
