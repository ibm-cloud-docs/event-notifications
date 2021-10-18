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


| Log sample    |  SourceId  | Verbatim|
|---------------|------------|-------------|
| New incoming notification| c6fd66fd-c75b-4bc4-87a1--5aa917435173:api| Indicates that a notification was triggered| 
{: caption="Table 1. Types of logs" caption-side="top"}
{: #en-logs-table-1}
{: tab-title="Incoming notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample    |  SourceId | NotificationId | Verbatim |
|---------------|-----------|----------------|-------------|
| New ingested notification | 2b094423-fd19-4b95-8bb1-5731e71b9f9a:api| c1dcb2a8-d218-413c-a10f-be5a64c620f4| After evaluation incoming notification is ingested into the system|
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Ingested notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample  | SourceId | NotificationId | Verbatim |
|-------------|----------|----------------|--------------|
| New email notification status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Total 5 emails were sent |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Email notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample   | SourceId | NotificationId |  Verbatim| Resolution | Helpdocs|
|--------------|----------|----------------|--------------|---------------|------------|
| SMS notification status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Successfully sent SMS to 8 out of 10 phone numbers. Each message was segmented into 3 parts| N/A  |  N/A |
| SMS failed status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Failed to deliver to the following phone numbers: +91946******, +91976*****| Verify the phone numbers provided in the subscription are valid and from supported countries |  Link to our docs section   |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="SMS notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}

| Log sample   | SourceId | NotificationId |  Verbatim| Resolution | Helpdocs|
|--------------|----------|----------------|----------|------------| ------- |
| Webhook notification status (warning) | <Source_CRN_HERE> | <NOTIFICATION_ID>|Failed to send the notification to webhook with the status code : 400 and response : 400 Bad Request https://webhook.site/dba0967b-0115-45d0-845c-e226bdf19555 | Please check the configured URL for the webhook as well as the headers provided|  Link to our docs section  |
| Webhook notification status | <Source_CRN_HERE> | <NOTIFICATION_ID>| Successfully sent the notification to the Webhook | N/A |  N/A  |
{: caption="Table 1. Types of logs " caption-side="top"}
{: #en-logs-table-2}
{: tab-title="Webhook notifications"}
{: tab-group="External Logs"}
{: class="simple-tab-table"}
{: row-headers}


## Analyzing logs for {{site.data.keyword.en_short}}

placeholder
