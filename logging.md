---

copyright:
  years: 2018, 2024
lastupdated: "2024-09-05"

keywords: event notifications cloud logs, event notifications logging, event notifications external logs

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# Logging for {{site.data.keyword.en_short}}
{: #logging-old}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.en_short}}, generate platform logs that you can use to investigate abnormal activity and critical actions in your account, and troubleshoot problems.
{: shortdesc}

You can use {{site.data.keyword.logs_routing_full_notm}}, a platform service, to route platform logs in your account to a destination of your choice by configuring a tenant that defines where platform logs are sent. For more information, see [About Logs Routing](/docs/logs-router?topic=logs-router-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on platform logs that are generated in your account and routed by {{site.data.keyword.logs_routing_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

As of 28 March 2024, the {{site.data.keyword.la_full_notm}} service is deprecated and will no longer be supported as of 30 March 2025. Customers will need to migrate to {{site.data.keyword.logs_full_notm}} before 30 March 2025. During the migration period, customers can use {{site.data.keyword.la_full_notm}} along with {{site.data.keyword.logs_full_notm}}. Logging is the same for both services. For information about migrating from {{site.data.keyword.la_full_notm}} to {{site.data.keyword.logs_full_notm}} and running the services in parallel, see [migration planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).
{: important}

## Locations where platform logs are generated
{: #log-locations}



| Field                  | Type                 |
|------------------------|----------------------|
| Dallas (`us-south`)    | [Yes]{: tag-green}   |
| Sydney (`au-syd`)      | [Yes]{: tag-green}   |
| Frankfurt (`eu-de`)    | [Yes]{: tag-green}   |
| Madrid (`eu-es`)       | [Yes]{: tag-green}   |
| London (`eu-gb`)       | [Yes]{: tag-green}   |

### Locations where logs are sent to {{site.data.keyword.la_full_notm}}
{: #la-legacy-locations}



{{site.data.keyword.en_short}} sends platform logs to {{site.data.keyword.la_full_notm}} in the regions indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Americas locations" caption-side="top"}
{: #la-table-1}
{: tab-title="Americas"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Asia Pacific locations" caption-side="top"}
{: #la-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where platform logs are sent in Europe locations" caption-side="top"}
{: #la-table-3}
{: tab-title="Europe"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

## Locations where logs are sent by {{site.data.keyword.logs_routing_full_notm}}
{: #lr-locations}



{{site.data.keyword.en_short}} sends logs by {{site.data.keyword.logs_routing_full_notm}} in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Americas locations" caption-side="top"}
{: #la-table-1}
{: tab-title="Americas"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Asia Pacific locations" caption-side="top"}
{: #la-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where platform logs are sent in Europe locations" caption-side="top"}
{: #la-table-3}
{: tab-title="Europe"}
{: tab-group="la"}
{: class="simple-tab-table"}
{: row-headers}

## Enabling logging
{: #log-enable}

Platform logs are logs that are exposed by logging-enabled services and the platform in {{site.data.keyword.cloud_notm}}.

- Platform logs are regional.

   You can monitor logs from enabled services on the {{site.data.keyword.cloud_notm}} in the region where the service is available.

- You can configure one instance only of the {{site.data.keyword.la_short}} service per region to collect platform logs in that location.

   You can have multiple {{site.data.keyword.la_short}} instances in a location. However, only one instance in a location (region) can be configured to receive logs from [enabled services](/docs/log-analysis?topic=log-analysis-cloud_services) in that {{site.data.keyword.cloud_notm}} location.

- To configure a {{site.data.keyword.la_short}} instance, you must set on the `platform logs` configuration setting. Also, you must have the platform role `editor` or higher for the {{site.data.keyword.la_short}} service in your account.

   To enable platform logs, see:

   - [Configuring platform logs through the Observability dashboard](/docs/log-analysis?topic=log-analysis-config_svc_logs&interface=ui)

   - [Configuring platform logs from the command line](/docs/log-analysis?topic=log-analysis-config_svc_logs&interface=cli)

For more information about platform logs, see [Configuring IBM Cloud platform logs](/docs/log-analysis?topic=log-analysis-config_svc_logs).

## Viewing logs
{: #logging_view-old}

If a {{site.data.keyword.la_short}} instance in a region is already enabled to collect platform logs, logs from the {{site.data.keyword.en_short}} service in that region are collected automatically and available for analysis through this instance.

To view and analyze platform logs for an {{site.data.keyword.en_short}} instance, check that the {{site.data.keyword.la_short}} instance is provisioned in the same region where the {{site.data.keyword.en_short}} instance that you want to monitor is available.
{: note}

To start the {{site.data.keyword.la_short}} web UI to view logs, see [Navigating to the web UI](/docs/log-analysis?topic=log-analysis-launch).



### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}



For more information about launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

## Fields per log type
{: #logging_fields-old}

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
| `sourceID`        | Required   | CRN of the {{site.data.keyword.cloud_notm}} service that sends the notification through the {{site.data.keyword.en_short}} service. |
| `notificationID`  | Optional   | ID of the notification that is sent to a destination. |
| `destinationID`   | Optional   | ID of the destination for which the status is being reported. |
| `level`           | Required   | Type of log. Valid values are `INFO`, `WARN`, `ERROR` |
{: caption="Log record fields" caption-side="top"}


## Log messages
{: #log_messages}

The following table lists the message IDs that are generated by the {{site.data.keyword.en_short}} service:

| Message ID | Log type    | Description |
|------------|-------------|-------------|
| `event-notifications.00001I` | `INFO` | `A notification event from source <sourceID> has been received.` CRN is used for IBM Cloud services. SourceID can be an IBM Cloud service or a human, for example|
| `event-notifications.00002I` | `INFO` | `The notification ID <NOTIFICATION-ID> has been assigned to the event that is originated from source <sourceID>.` |
| `event-notifications.00003I` | `INFO` | `A notification event with ID <NOTIFICATION-ID> is published through the following topic IDs: [<LIST-OF-TOPIC-IDS>]` |
| `event-notifications.00004I` | `INFO` | `A notification request with ID <NOTIFICATION-ID> is processed by the following subscribers: [<LIST-OF-SUBSCRIPTIONS>]` |
| `event-notifications.00006I` | `INFO` | `No devices found for platform: push_chrome` Valid platforms are [push_chrome, push_firefox, push_android, push_ios, push_safari] |
| `event-notifications.00007I` | `INFO` | `An SMS is dispatched to the following numbers: [<LIST-OF-TELEPHONE-NUMBERS].` |
| `event-notifications.00008I` | `INFO` | `An email is sent to each of the following destinataries: [<LIST-OF-EMAIL-ADDRESSES>]` |
| `event-notifications.00009I` | `INFO` | `The Webhook is successfully served. Response from the Webhook API: OK with the status code: 200` |
| `event-notifications.00010I` | `INFO` | `A notification event with ID <NOTIFICATION_ID is sent to the following subscriptions.<LIST-OF_SUBSCRIPTIONS>`
| `event-notifications.00011I` | `INFO` | `A notification event with ID <NOTIFICATION_ID is sent to the following destinations.<LIST-OF_DESTINATIONS>`
| `event-notifications.00012I` | `INFO` | `Notification processed successfully for total: 1 devices and platform push_chrome`
| `event-notifications.00013I` | `INFO` | `Notification dispatched successfully to total devices <COUNT> and platform push_android`. |
| `event-notifications.00014I` | `INFO` | `The Slack destination is successfully served. Response from the Slack API: OK with the status code: 200`. |
| `event-notifications.00015I` | `INFO` | `The notification is delievered to the deviceID:<DEVICE_ID> on the platform: <PLATFORM_NAME> and the destination ID:<DESTINATION_ID>`. |
| `event-notifications.00015I` | `INFO` | `The user has opened the notification on the deviceID:<DEVICE_ID> and the platform: <PLATFORM_NAME> and the destination ID:<DESTINATION_ID>.`|
| `event-notifications.00016I` | `INFO` | `The Microsoft Teams destination is successfully served. Response from the Microsoft Teams API: OK with the status code: 200`|
| `event-notifications.00017I` | `INFO` | `The IBM Cloud functions destination is successfully served. Response from the IBM Cloud functions API: OK with the status code: 200`|
| `event-notifications.00018I` | `INFO` | `The Pager Duty destination is successfully served. Response from the Pager Duty API: OK with the status code: 200`|
| `event-notifications.00019I` | `INFO` | `The Code Engine destination is successfully served. Response from the Code Engine API: OK with the status code: 200`|
| `event-notifications.00020I` | `INFO` | `The Service Now destination is successfully served. Response from the Service Now API: OK with the status code: 200`|
| `event-notifications.00021I` | `INFO` | `The Cloud Object Storage is successfully served. Response from the Cloud Object Storage API: OK with the status code: 200`|
| `event-notifications.00022I` | `INFO` | `An email of size 1048 bytes is sent to the following recepients: <masked-email-id>, from the sender: <masked-sender-email-id>`|
| `event-notifications.00023I` | `INFO` | `An email of size 1048 bytes is deferred to each of the following : <masked-email-id>, from the sender: <masked-sender-email-id>`|
| `event-notifications.00001W` | `WARN` | `A notification event from source<Source_ID> is rejected because no topic is configured for the source. . The topic to filter the event is missing.` |
| `event-notifications.00002W` | `WARN` | `A notification event from the source <Source_ID> is invalid as it is not filtered by any topic.` |
| `event-notifications.00003W` | `WARN` | `A notification request with ID <NOTIFICATION-ID>, that is processed by the following subscribers: [<LIST-OF-SUBSCRIPTIONS>], is forbidden for the destination type: smtp_ibm/sms` |
| `event-notifications.00004W` | `WARN` | `A notification with ID <NOTIFICATION_ID> is not dispatched as it has no subscribers.`|
| `event-notifications.00005W` | `WARN` | `Webhook returned with an error response: Not Found with the status code: 404`|
| `event-notifications.00006W` | `WARN` | `Slack returned with an error response: <error_message> with the status code: 404`|
| `event-notifications.00007W` | `WARN` | `Microsoft teams API returned with an error response: Not Found with the status code: 401`|
| `event-notifications.00008W` | `WARN` | `The SMS is not delivered because it is unsubscribed by: [<SMS_NUMBERS>]`|
| `event-notifications.00009W` | `WARN` | `IBM Cloud functions API returned with an error response: Not Found with the status code: 401`|
| `event-notifications.00010W` | `WARN` | `Pager Duty API returned with an error response: Not Found with the status code: 401`|
| `event-notifications.00011W` | `WARN` | `Code Engine functions API returned with an error response: Not Found with the status code: 401`|
| `event-notifications.00012W` | `WARN` | `Service Now API returned with an error response: Not Found with the status code: 401`|
| `event-notifications.00013W` | `WARN` | `An email of size 1xxx bytes is bounced, Please check the authentacity of the emails: [g*a*g*n*1*3@in.ibm.com], from the sender: t*s*<*o*e*l*@xyz.com>host xyz.pphosted.com[] said: 550 5.1.1 User Unknown (in reply to DATA command`|
| `event-notifications.00001E` | `ERROR` | `Notifications failed to dispatch to the following invalid devices [<DEVICE_IDS>] and platform push_android.` |
| `event-notifications.00002E` | `ERROR` | `Webhook returned with an error response:<Error response> Unauthorised with the status code:404`|
| `event-notifications.00003E` | `ERROR` | `Notification dispatch failed due to the authentication error for device id <device_id> and platform <platform_name>`.|
| `event-notifications.00004E` | `ERROR` | `Slack returned with an error response: <error_message> with the status code: 401`|
| `event-notifications.00005E` | `ERROR` | `Notification dispatch failed due to the <'BadDeviceToken'> error for device id <device_id> and platform <platform_name>.`|
| `event-notifications.00006E` | `ERROR` | `Microsoft teams API returned with an error response: Unauthorised with the status code: 401`|
| `event-notifications.00007E` | `ERROR` | `IBM Cloud functions API returned with an error response: Unauthorised with the status code: 401`|
| `event-notifications.00008E` | `ERROR` | `Pager Duty API returned with an error response: Unauthorised with the status code: 401`|
| `event-notifications.00009E` | `ERROR` | `Code Engine API returned with an error response: Unauthorised with the status code: 401`|
| `event-notifications.00010E` | `ERROR` | `Service Now API returned with an error response: Unauthorised with the status code: 401`|
{: caption="Additional information about message IDs" caption-side="top"}


 -->

### List logs generated by a service
{: #logging_analyze_1-old}

If you want to view all the logs that are being generated for a particular source, get the `sourceID` from the {{site.data.keyword.en_short}} service dashboard and use the following query in {{site.data.keyword.la_short}}:

```bash
sourceID:<source_crn>
```
{: codeblock}

### List logs for a notification request
{: #logging_analyze_2-old}

If you know the notification ID that is generated for a request from a service or source to the {{site.data.keyword.en_short}} service, use the following query in {{site.data.keyword.la_short}} to list all logs for that particular notification ID:

```bash
notificationID:<notification Id>
```
{: codeblock}
