---

copyright:
  years: 2024
lastupdated: "2024-07-05"

keywords: event-notifications, event notifications, about event notifications, data security, compliance, data security and compliance, ciphers

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring {{site.data.keyword.en_full}} metrics
{: #en-view-manage-monitor-metrics}

After you set up your {{site.data.keyword.en_full_notm}} service
instance, you can manage monitoring metrics by using this feature.
{: shortdesc}

## Metrics settings
{: #en-manage-metrics-policy}

Metrics for {{site.data.keyword.en_short}} service instances is
a policy that allows you to receive the notfication metrics for your
{{site.data.keyword.en_short}} instance. When you enable this
policy, {{site.data.keyword.en_short}} can be used to track your notifications metrics in real-time.

{{site.data.keyword.en_short}} metrics is currently only available
Custom Email Domains.
{: preview}

### View metrics for your {{site.data.keyword.en_short}} instance with the Console
{: #enable-metrics-instance-policy-ui}

After creating a {{site.data.keyword.en_short}} instance, complete the following steps to enable the metrics:

1. [Log in to the {{site.data.keyword.cloud_notm}} console](/login/){: external}.

1. Go to **Menu** &gt; **Resource List** to view a list of your resources.

1. From your {{site.data.keyword.cloud_notm}} resource list, select your
    provisioned instance of {{site.data.keyword.en_short}}.

1. Click `Metrics` in the {{site.data.keyword.en_short}} console.

## Understanding the dashboard
{: #en-understand-dashboard}

As you evaluate your resources, the results are returned via the service UI in graphical and detailed formats.

### Filter your metrics
{: #en-understand-dashboard-attributes}

Use the listed attributes to filter your results in the dashbaord:

 * **Destination Type**

   Select the type of destination set for your notification to filter.

   This is currently available for Custom Email Domains.
   {:note: .note}


 * **Destination name**

    Select the destination.

 * **Subject**

   Enter the subject line of the email notification sent.

 * **Notification ID**

   Enter the notification ID.

 * **Source name**

   Select the source name of the event notification.

 * **Email to**

   Enter the reciever's email address.


When you visit the dashboard, there are three visual representations of data that has been aggregated from your scans. You see the:

Select the required time period tab on the right to filter and view your metrics graphs. The default time period is **24 hours**.
{:note: .note}

* **Notification Status**

   The section provides you with various metrics according to your selected filter attributes. The metrics tiles are:

    * **Emails sent**

        The total number of emails sent for the selected time period.

    * **Delivered**

        The total number of emails succesfully delivered for the selected time period.

    * **Failed**

        The total number of emails that did not deliver succesfully for the selected time period.


    * **Open rate**

        The percentage of delivered emails that have been opened by the recievers.

    * **Bounce rate**

        The percentage of emails that are returned to the sender because they failed to be delivered to the intended recipient.


* **Notification metrics Graph**

   This is graphical reperesntation of the percentage of Delivered, Failed, and Opened mails for the selected time period.

   To download the metrics in your local system, go to **More** &gt; **Export to [desired format]**. Currently, you can export the graphs in CSV, PNG, and JPG formats.
{:note: .note}


* **Bounced and Opened notification**

    The total number of notification bounces or fail per day for the selected time period.
