---

copyright:
  years: 2019, 2021
lastupdated: "2021-10-18"

keywords: event notifications logDNA , event notifications logging, event notifications external logs

subcollection: event notifications

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Logging for {{site.data.keyword.en_short}}
{: #en-logging}

Logging is automatically enabled in {{site.data.keyword.en_full}} to help you troubleshoot issues. You can also use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.en_short}} service. Finally, you can view logs in {{site.data.keyword.la_full_notm}}.
{: shortdesc}


## Enabling platform logs from the Logging dashboard
{: #en-logs}

To configure a logging instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![menu icon](../../icons/icon_hamburger.svg) &gt; **Observability** to access the *Observability* dashboard.

3. Click **Logging**, then click **Options** > **Edit Platform**.

4. Select a [region](/docs/log-analysis?topic=log-analysis-regions).

5. Choose which logging instance receives logs from enabled services on that location. [Learn more about the services that are enabled to send logs to {{site.data.keyword.la_full_notm}}.](/docs/log-analysis?topic=log-analysis-cloud_services)

6. Click **Select**.

The main *Observability* page opens.

## Viewing logs
{: #en-logs-view}

To enable an instance that is receiving {{site.data.keyword.en_short}} action logs, you need to configure the Platform Service Logs in the logging service.
{{site.data.keyword.en_short}} sends the action logs to the Log Analysis service in the same region as the {{site.data.keyword.en_short}} namespace. Actions logs of a {{site.data.keyword.en_short}} namespace in `us-south` are sent to a logging instance in `us-south`.


## Pre-defined fields per log type
{: #en-logs-fields}

Each log record has:
- LogSourceCRN: CRN of the customer's instance
- saveServiceCopy: whether IBM's instance has access to it
- messageID
- message
- resolution
- documentURL


| Log sample    |  SourceId  | Description|
|---------------|------------|-------------|
| An event was received from the source <Source_ID> to be filtered by the topics for possible ingestion| <Source_ID>| Indicates that a notification was triggered| 
{: caption="Table 1. Types of logs" caption-side="top"}
{: #en-logs-table-1}
{: tab-title="Incoming notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample    |  SourceId | NotificationId | Description|
|---------------|-----------|----------------|-------------|
|An event from the source <source_id> was ingested by the filter and is assigned a unique notification_id <notificaiton_id> to be dispatched to the destinations.| <Source_ID>| <Notificaiton_id>| Incoming notification is ingested into the system after evaluation|
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Ingested notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample  | SourceId | NotificationId | Verbatim |
|-------------|----------|----------------|--------------|
|New email notification status| <Source_CRN_HERE> | <NOTIFICATION_ID>| Total five emails were sent |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Email notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample   | SourceId | NotificationId |  Verbatim| Resolution | Help docs|
|--------------|----------|----------------|--------------|---------------|------------|
|SMS notification status| <Source_CRN_HERE> | <NOTIFICATION_ID>| Successfully sent SMS to 8 out of 10 phone numbers. Each message was segmented into three parts| N/A  |  N/A |
| SMS failed status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Failed to deliver to the following phone numbers: +91946******, +91976*****| Verify that the phone numbers that are provided in the subscription are valid and from supported countries |  tbd   |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="SMS notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample   | SourceId | NotificationId |  Verbatim| Resolution | Help docs|
|--------------|----------|----------------|----------|------------| ------- |
|Webhook notification status (warning)| <Source_CRN_HERE> | <NOTIFICATION_ID>|Failed to send notification to webhook with status code: 400 and response: 400 Bad Request https://webhook.site/dba0967b-0115-45d0-845c-e226bdf19555 | Check the configured URL for the webhook and the headers provided|  tbd |
|Webhook notification status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Successfully sent notification to the webhook | N/A |  N/A  |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Webhook notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}



