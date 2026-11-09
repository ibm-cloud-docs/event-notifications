---

copyright:
  years: 2025, 2026
lastupdated: "2026-11-09"

keywords: event-notifications, metrics for email notifications, monitor metrics, email services, delivery metrics, unique clicks, deliverability

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring metrics for email notifications
{: #en-manage-monitor-metrics}

In {{site.data.keyword.en_full}}, you can track metrics for email notifications sent through custom domain email (API) and SMTP, such as the number of emails delivered. This allows you to analyze customer behavior in real time and optimize your communication strategy.
{: shortdesc}

## Viewing metrics
{: #en-view-metrics}

To monitor metrics for email notifications that are sent through the API or SMTP, complete the following steps.

1. In your {{site.data.keyword.en_short}} instance, click **SMTP configurations**.
2. Click the **Metrics** tab.
3. In the **Dashboard settings** section, select a time interval and, optionally, filters. For more information, see [Setting the time interval and filters](#en-metrics-dashboard-settings).
4. Review the data in each section of the page, in the following order.
   - **Metrics overview** shows a summary of sent, delivered, opened, unique clicks, failed, and bounced emails.
   - **Deliverability and engagement trends** shows a line chart of the metrics over time. For more information, see [Reviewing deliverability and engagement trends](#en-metrics-trends).
   - **Deliverability insights** shows a table of individual email records. For more information, see [Reviewing deliverability insights](#en-metrics-insights).
   - **Failure distribution by reason** and **Bounce distribution by reason** show why emails failed or bounced. 

Delivery metrics and email records are retained for 30 days. You can't view older data.
{: note}

## Setting the time interval and filters
{: #en-metrics-dashboard-settings}

By default, the dashboard shows data across all your domains and configurations. To change the content of the dashboard, use the **Dashboard settings** section. The settings apply to every section on the **Metrics** tab.

### Selecting the time interval
{: #en-metrics-time-interval}

1. In the **Dashboard settings** section, select an option from the **Select time interval** list.
2. To review specific dates, select **Custom range**, and then enter or select the **From** and **To** dates.

### Filtering the metrics
{: #en-filter-metrics}

1. In the **Dashboard settings** section, click **View filters**. 
2. Select a value for **Delivery method**. The filters that apply to the method that you select are shown.
3. Select or enter values for the filters that you want to use. For the available filters, see the following table.

   | Filter | Description | Delivery method |
   | ------ | ----------- | --------------- |
   | **Domain** | One or more domains that are used to send email. | All, API, SMTP |
   | **Email configuration name** | One or more API or SMTP configurations. \n Select a delivery method first to enable this filter. | All, API, SMTP |
   | **Email to address** | The email address of the recipient. | All, API, SMTP |
   | **Email from address** | The email address that the email was sent from. | All, API, SMTP |
   | **Email subject** | The subject of the email. | All, API, SMTP |
   | **Delivery method** | The method that was used to send the email: **All**, **API**, or **SMTP**. | All, API, SMTP |
   | **Topic name** | One or more topics that the email notification was published to. | API |
   | **Source name** | One or more sources that the email notification was sent from. | API |
   | **Template name** | One or more email templates. | API |
   | **Notification ID** | The unique identifier that is assigned to each notification event. This identifier is available only if the store notifications option is enabled on the source. | API |
   | **SMTP user name** | One or more SMTP users. | SMTP |
   {: caption="Metrics filters" caption-side="bottom"}

   The default **Delivery method** depends on how your domains are used. If your domains are used only for API email, the default is **API**. If they are used only for SMTP, the default is **SMTP**. If they are used for both, the default is **All**.

## Reviewing deliverability and engagement trends
{: #en-metrics-trends}

The **Deliverability and engagement trends** section shows a line chart with one line for each metric: sent, delivered, opened, unique clicks, failed, and bounced. The x-axis shows the dates in the selected time interval. The y-axis scales to the largest count in that interval. When the delivery method is **All**, the legend shows **Opened (API only)**. When the delivery method is **SMTP**, the chart doesn't include opens.

1. To see exact values, hover over a point on a line.
2. To focus on one metric, click its name in the legend. The other metrics are hidden. To show all metrics again, select them all in the legend.
3. To compare a metric with the others, hover over its name in the legend. 
4. To work with the chart, use the icons in the chart toolbar.
   - **Show as table** shows the chart data in a table.
   - **Full screen** expands the chart.
   - **Export** downloads the chart. For more information, see [Downloading metrics](#en-download-metrics).
5. If you select **Last 30 days** as the time interval, use the view switcher in the chart header to show one data point for each day (**Daily view**) or for each week (**Weekly view**).

## Reviewing deliverability insights
{: #en-metrics-insights}

The **Deliverability insights** section shows a table of the individual email records for the selected time interval and filters. The table has the following columns. You can sort every column.

Email address
:   The email address of the recipient.

Subject
:   The subject of the email.

Status
:   The latest status of the email: **Sent**, **Delivered**, **Opened**, **Failed**, or **Bounced**. The **Opened** status is available only for API email.

Reason
:   The cause of the failure or bounce. The cell is empty if the status is **Sent**, **Delivered**, or **Opened**.

Timestamp
:   The time of the last status that was retrieved for the email.


If no records match the time interval and filters, the table shows an empty state.

To see more information about an email, expand its row. The expanded row has the following sections.

History
:   The status changes of the email, with the time of each change. A status that hasn't happened yet is shown as "Not delivered yet" or "Not opened yet". For failed and bounced emails, the reason is shown under the status.

Email details
:   The **Domain**, **Email configuration name**, **Sender name**, **Mail from address**, and **Delivery method** of the email. For API email, the details also include **Topic name**, **Source name**, **Template name**, and **Notification ID**. For SMTP email, the details include **SMTP user name** and **IP address**. To see a description of **Topic name**, **Source name**, or **Notification ID**, hover over its information icon.

Tracked links
:   The links in the email that are tracked for unique clicks. For each link, the section shows the **URL**, the **Status** (**Clicked** or **Not clicked**), and the **Timestamp** of the click. This section is shown only if link tracking is set up.



## Downloading metrics
{: #en-download-metrics}

To download a chart to your local system, complete the following steps.

1. In the toolbar of the chart, click **Export**.
2. Select the format that you want to export to, such as **CSV**, **PNG**, or **JPG**.
