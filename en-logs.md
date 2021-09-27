---

copyright:
  years: 2019, 2021
lastupdated: "2021-09-27"

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

## Enabling platform logs from the {{site.data.keyword.en_short}} dashboard
{: #en-logs-service}

placeholder for content in pipeline.

## Enabling platform logs from the Logging dashboard
{: #en-logs}

To configure a logging instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![menu icon](../../icons/icon_hamburger.svg) &gt; **Observability** to access the *Observability* dashboard.

3. Click **Logging**, then click **Options** > **Edit Platform**.

4. Select a [region](/docs/log-analysis?topic=log-analysis-regions).

5. Choose which logging instance will receive logs from enabled services on that location. [Learn more about the services that are enabled to send logs to {{site.data.keyword.la_full_notm}}.](/docs/log-analysis?topic=log-analysis-cloud_services)

6. Click **Select**.

The main *Observability* page opens.

## Viewing logs
{: #en-logs-view}

To enable an instance that is receiving {{site.data.keyword.en_short}} action logs, you need to configure the Platform Service Logs in the logging service.
{{site.data.keyword.en_short}} sends the action logs to the Log Analysis service in the same region as the {{site.data.keyword.en_short}} namespace. Actions logs of a {{site.data.keyword.en_short}} namespace in `us-south` are sent to a logging instance in `us-south`.


### Launching the LogDNA web UI from the {{site.data.keyword.en_short}} dashboard

place holder for steps

## Pre-defined fields per log type
{: #en-logs-fields}

Each log record has:
- LogSourceCRN : CRN of the customer's instance
- saveServiceCopy: whether IBM's instance has access to it
- messageId
- messages
- resolutionUrl
- documentURL


| Type of log     | InstanceId  | SourceId | NotificationId | Description | 
|-----------------|-------------|----------|----------------|------------- | 
| New incoming notification| 57dd1fef-e4fb-4479-ba1f-648319b88927| c6fd66fd-c75b-4bc4-87a1--5aa917435173:api| 3ac4259c-b1dd-4101-b62f-4914191a7194 | indicates that a notification was triggered| 
{: caption="Table 1. Types of logs" caption-side="top"}
{: #en-logs-table-1}
{: tab-title="Incoming notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Type of log     | InstanceId | SourceId | NotificationId | Description | 
|-----------------|------------|----------|----------------|--------------| 
| New SMTP-IBM Notification ingested | 493e4a05-2b70-46cd-a27e-7057141951e9|2b094423-fd19-4b95-8bb1-5731e71b9f9a:api| c1dcb2a8-d218-413c-a10f-be5a64c620f4| After evaluation incoming notification is ingested into the system| 
| New SMS-IBM Notification Ingested| 4493e4a05-2b70-46cd-a27e-7057141951e9| 2b094423-fd19-4b95-8bb1-5731e71b9f9a:api|1ec35fd9-f7b5-496a-86e7-2170b9ae68b4|
| New WEBHOOK Notification Ingested|493e4a05-2b70-46cd-a27e-7057141951e9 | 2b094423-fd19-4b95-8bb1-5731e71b9f9a:api|1c1dcb2a8-d218-413c-a10f-be5a64c620f4|                             
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Ingested notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Type of log     | InstanceId | SourceId | NotificationId |  Description |
|-----------------|------------|----------|----------------|-------------- |
| New email notification status | <InstanceID_here> |<Source_CRN_HERE> | <NOTIFICATION_ID>| Total 5 emails were attempted | 
| New email notification status | <InstanceID_here>| <Source_CRN_HERE> |<NOTIFICATION_ID>| Failed to deliver emails to `test@gmail.com`|                            
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Email notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Type of log     | InstanceId | SourceId | NotificationId |  Description |
|-----------------|------------|----------|----------------|-------------- |
| New SMS notification status | <InstanceID_here> |<Source_CRN_HERE> | <NOTIFICATION_ID>|Total 3 SMS units were sent. Failed to deliver SMS to 3 numbers |                           
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="SMS notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Type of log     | InstanceId | SourceId | NotificationId |  Description |
|-----------------|------------|----------|----------------|-------------- |
| Webhook notification status | <InstanceID_here> |<Source_CRN_HERE> | <NOTIFICATION_ID>|Webhook failed: {"webhook_id": "12323213", "status_code": 400, "status_message": "400 Bad Request https://webhook.site/dba0967b-0115-45d0-845c-e226bdf19555",   "date_sent": "2021-09-24T04:48:10.707Z"} |
| Webhook notification status | <InstanceID_here> |<Source_CRN_HERE> | <NOTIFICATION_ID>|Webhook success: {"webhook_id": "12323213", "status_code": 200, "status_message": "OK",   "date_sent": "2021-09-24T04:48:10.707Z"} |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Webhook notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}


## Analyzing logs for {{site.data.keyword.en_short}}

placeholder
