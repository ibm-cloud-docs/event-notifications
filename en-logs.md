---

copyright:
  years: 2019, 2022
lastupdated: "2022-04-29"

keywords: event notifications logDNA, event notifications logging, event notifications external logs

subcollection: event-notifications

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
{: #logging}

You can view and analyze {{site.data.keyword.en_short}} logs by using the {{site.data.keyword.la_full}} service and enabling platform logs in each region where you operate in {{site.data.keyword.cloud_notm}}. {{site.data.keyword.la_full_notm}} adds log management capabilities to your {{site.data.keyword.cloud}} architecture. 
{: shortdesc}

Use the [{{site.data.keyword.at_full_notm}} service](/docs/activity-tracker) to audit and track how users and applications interact with the {{site.data.keyword.en_short}} service. 
{: tip}


## Platform logs
{: #logging_ov}

Platform logs are logs that are exposed by logging-enabled services and the platform in {{site.data.keyword.cloud_notm}}. 

- Platform logs are regional. 

    You can monitor logs from enabled services on the {{site.data.keyword.cloud_notm}} in the region where the service is available. 

- You can configure one instance only of the {{site.data.keyword.la_short}} service per region to collect platform logs in that location. 

    You can have multiple {{site.data.keyword.la_short}} instances in a location. However, only one instance in a location (region) can be configured to receive logs from [enabled services](/docs/log-analysis?topic=log-analysis-cloud_services) in that {{site.data.keyword.cloud_notm}} location.

- To configure a {{site.data.keyword.la_short}} instance, you must set on the `platform logs` configuration setting. Also, you must have the platform role `editor` or higher for the {{site.data.keyword.la_short}} service in your account.

    To enable platform logs, see:

    - [Configuring platform logs through the Observability dashboard](/docs/log-analysis?topic=log-analysis-config_svc_logs#config_svc_logs_ui)

    - [Configuring platform logs from the command line](/docs/log-analysis?topic=log-analysis-config_svc_logs#platform_logs_enabling_cli)


For more information about platform logs, see [Configuring IBM Cloud platform logs](/docs/log-analysis?topic=log-analysis-config_svc_logs).

## Locations
{: #logging_locations}

The following table outlines the locations where you can view and analyze {{site.data.keyword.en_short}} logs:

| Locations in Americas | Platform logs available |
|-----------------------|---------------------------------|
| `Dallas (us-south)`   | ![Checkmark icon](../icons/checkmark-icon.svg "checkmark") |
{: caption="Table 1. The automatic collection of {{site.data.keyword.registryshort_notm}} service metrics in Americas locations" caption-side="bottom"}

| Locations in Asia Pacific | Platform logs available |
|---------------------------|---------------------------------|
| `Sydney (au-syd)`         | ![Checkmark icon](../icons/checkmark-icon.svg "checkmark") |
{: caption="Table 2. The automatic collection of {{site.data.keyword.registryshort_notm}} service metrics in Asia Pacific locations" caption-side="bottom"}

| Locations in Europe | Platform logs available |
|---------------------|---------------------------------|
| `Frankfurt (eu-de)` | ![Checkmark icon](../icons/checkmark-icon.svg "checkmark") |
| `London (eu-gb)`    | ![Checkmark icon](../icons/checkmark-icon.svg "checkmark") |
{: caption="Table 3. The automatic collection of {{site.data.keyword.registryshort_notm}} service metrics in Europe locations" caption-side="bottom"}


## Viewing logs
{: #logging_view}

If a {{site.data.keyword.la_short}} instance in a region is already enabled to collect platform logs, logs from the {{site.data.keyword.en_short}} service in that region are collected automatically and available for analysis through this instance.

To view and analyze platform logs for an {{site.data.keyword.en_short}} instance, check that the {{site.data.keyword.la_short}} instance is provisioned in the same region where the {{site.data.keyword.en_short}} instance that you want to monitor is available.
{: note}

To start the {{site.data.keyword.la_short}} web UI to view logs, see [Navigating to the web UI](/docs/log-analysis?topic=log-analysis-launch).

## Fields per log type
{: #logging_fields}

Table 4 outlines the fields that are included in each log record:

| Field             | Type       | Description             |
|-------------------|------------|-------------------------|
| `logSourceCRN`    | Required   | Defines the account where the log is published. |
| `saveServiceCopy` | Required   | Defines whether IBM saves a copy of the record for operational purposes. |
| `resourceGroupId` | Required   | Defines the resource group that is associated with the {{site.data.keyword.en_short}} instance. |
| `message`         | Required   | Description of the log that is generated. 
| `msg_timestamp`   | Required   | UTC timestamp of the message.
| `messageID`       | Required   | ID of the log that is generated. |
| `resolution`      | Optional   | Guidance on how to proceed if you receive this log record. |
| `documentsURL`    | Optional   | More information on how to proceed if you receive this log record. |
| `sourceID`        | Required   | CRN of the {{site.data.keyword.cloud_notm}} service that sends the notification through the {{site.data.keyword.en_short} service. |
| `notificationID`  | Optional   | ID of the notification that is sent to a destination. |
| `level`           | Required   | Type of log. Valid values are `INFO`, `WARN`, `ERROR` | 
{: caption="Table 4. Log record fields" caption-side="top"}


## Log messages
{: #logging_msgs}

The following table lists the message IDs that are generated by the {{site.data.keyword.en_short}} service:

| Message ID | Log type    | Description |
|------------|-------------|-------------|
| `event-notifications.00001I` | `INFO` | `A notification event from source <sourceID> has been received.` CRN is used for IBM Cloud services. SourceID can be an IBM Cloud service or a human, for example|
| `event-notifications.00002I` | `INFO` | `The notification ID <NOTIFICATION-ID> has been assigned to the event that is originated from source <sourceID>.` |
| `event-notifications.00003I` | `INFO` | `A notification event with ID <NOTIFICATION-ID> is published through the following topic IDs: [<LIST-OF-TOPIC-IDS>]` |
| `event-notifications.00004I` | `INFO` | `A notification request with ID <NOTIFICATION-ID> is processed by the following subscribers: [<LIST-OF-SUBSCRIPTIONS>]` |
| `event-notifications.00006I` | `INFO` | `No devices found for platform: push_chrome` Valid platforms are [push_chrome, push_firefox, push_android, push_ios] |
| `event-notifications.00007I` | `INFO` | `An SMS is dispatched to the following numbers: [<LIST-OF-TELEPHONE-NUMBERS].` |
| `event-notifications.00008I` | `INFO` | `An email is sent to each of the following destinataries: [<LIST-OF-EMAIL-ADDRESSES>]` |
| `event-notifications.00009I` | `INFO` | `A webhook is successfully served. Response from the webhook: OK with the status code: 200` |
| `event-notifications.00010I` | `INFO` | `A notification event with ID <NOTIFICATION_ID is sent to the following subscriptions.<LIST-OF_SUBSCRIPTIONS>` 
| `event-notifications.00011I` | `INFO` | `A notification event with ID <NOTIFICATION_ID is sent to the following destinations.<LIST-OF_DESTINATIONS>` 
| `event-notifications.00012I` | `INFO` | `Notification processed successfully for total: 1 devices and platform push_chrome` 
| `event-notifications.00013I` | `INFO` | `Notification dispatched successfully to total devices <COUNT> and platform push_android`. 
| `event-notifications.00001W` | `WARN` | `A notification event from source<Source_ID> is rejected because no topic is configured for the source. . The topic to filter the event is missing.` |
| `event-notifications.00002W` | `WARN` | `A notification event from the source <Source_ID> is invalid as it is not filtered by any topic.` |
| `event-notifications.00003W` | `WARN` | `A notification request with ID <NOTIFICATION-ID>, that is processed by the following subscribers: [<LIST-OF-SUBSCRIPTIONS>], is forbidden for the destination type: smtp_ibm/sms` |
| `event-notifications.00004W` | `WARN` | `A notification with ID <NOTIFICATION_ID> is not dispatched as it has no subscribers.`|
| `event-notifications.00005W` | `WARN` | `Webhook returned with an error response: Not Found with the status code: 404`|
| `event-notifications.00001E` | `ERROR` | `Notifications failed to dispatch to the following invalid devices [<DEVICE_IDS>] and platform push_android.` |
| `event-notifications.00002E` | `ERROR` | `Webhook returned with an error response:<Error response> Unauthorised with the status code:401`|
{: caption="Table 5. Message IDs" caption-side="top"}


## Analyzing logs
{: #logging_analyze}


### List logs generated by a service
{: #logging_analyze_1}

If you want to view all the logs thar are being generated for a particular source, get the `sourceID` from the {{site.data.keyword.en_short}} service dashboard and use the following query in {{site.data.keyword.la_short}}:
 
```sh
sourceID:<source_crn>
```
{: codeblock}


### List logs for a notification request
{: #logging_analyze_2}


If you know the notification ID that is generated for a request from a service or source to the {{site.data.keyword.en_short}} service, use the following query in {{site.data.keyword.la_short}} to list all logs for that particular notification ID:

```sh
notificationID:<notification Id>
```
{: codeblock}


