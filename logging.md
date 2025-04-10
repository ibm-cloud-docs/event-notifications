---

copyright:
  years: 2018, 2025
lastupdated: "2025-04-10"

keywords: event notifications cloud logs, event notifications logging, event notifications external logs

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Logging for {{site.data.keyword.en_short}}
{: #logging}

{{site.data.keyword.cloud}} services, such as {{site.data.keyword.en_short}}, generate platform logs that you can use to investigate abnormal activity and critical actions in your account, and troubleshoot problems.
{: shortdesc}

You can use {{site.data.keyword.logs_routing_full_notm}}, a platform service, to route platform logs in your account to a destination of your choice by configuring a tenant that defines where platform logs are sent. For more information, see [About Logs Routing](/docs/logs-router?topic=logs-router-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on platform logs that are generated in your account and routed by {{site.data.keyword.logs_routing_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

As of 28 March 2024, the {{site.data.keyword.la_full_notm}} service is deprecated and will no longer be supported as of 30 March 2025. Customers will need to migrate to {{site.data.keyword.logs_full_notm}} before 30 March 2025. During the migration period, customers can use {{site.data.keyword.la_full_notm}} along with {{site.data.keyword.logs_full_notm}}. Logging is the same for both services. For information about migrating from {{site.data.keyword.la_full_notm}} to {{site.data.keyword.logs_full_notm}} and running the services in parallel, see [migration planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).
{: important}

## Locations where platform logs are generated
{: #log-locations}

| Region                  | Supported                 |
|------------------------|----------------------|
| Dallas (`us-south`)    | [Yes]{: tag-green}   |
| Sydney (`au-syd`)      | [Yes]{: tag-green}   |
| Frankfurt (`eu-de`)    | [Yes]{: tag-green}   |
| Madrid (`eu-es`)       | [Yes]{: tag-green}   |
| London (`eu-gb`)       | [Yes]{: tag-green}   |
| Toronto (`ca-tor`)     | [Yes]{: tag-green}   |
| Tokyo (`jp-tok`)       | [Yes]{: tag-green}   |
| Osaka (`jp-osa`)       | [Yes]{: tag-green}   |
{: caption="Locations where platform logs are generated" caption-side="top"}



### Locations where logs are sent to {{site.data.keyword.logs_full_notm}}
{: #logs-locations}

{{site.data.keyword.en_short}} sends platform logs to {{site.data.keyword.logs_full_notm}} in the regions indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Americas locations" caption-side="top"}
{: #logs-table-1}
{: tab-title="Americas"}
{: tab-group="logs"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Asia Pacific locations" caption-side="top"}
{: #logs-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="logs"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where platform logs are sent in Europe locations" caption-side="top"}
{: #logs-table-3}
{: tab-title="Europe"}
{: tab-group="logs"}
{: class="simple-tab-table"}
{: row-headers}

## Locations where logs are sent by {{site.data.keyword.logs_routing_full_notm}}
{: #lr-locations}

{{site.data.keyword.en_short}} sends logs by {{site.data.keyword.logs_routing_full_notm}} in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`)  | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|-------------------------|-------------------|----------------------|
| [Yes]{: tag-green} | [No]{: tag-red} | [Yes]{: tag-green} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Americas locations" caption-side="top"}
{: #lr-table-1}
{: tab-title="Americas"}
{: tab-group="lr"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)    | Sydney (`au-syd`) |  Osaka (`jp-osa`) | Chennai (`in-che`) |
|---------------------|------------------|------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red} |
{: caption="Regions where platform logs are sent in Asia Pacific locations" caption-side="top"}
{: #lr-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="lr"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`)  | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------------------------------------------------|---------------------|------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where platform logs are sent in Europe locations" caption-side="top"}
{: #lr-table-3}
{: tab-title="Europe"}
{: tab-group="lr"}
{: class="simple-tab-table"}
{: row-headers}

## Enabling logging
{: #log-enable}

Platform logs are logs that are exposed by logging-enabled services and the platform in {{site.data.keyword.cloud_notm}}. You can configure {{site.data.keyword.cloud_notm}} logs instance to receive the logs sent by service. See [{{site.data.keyword.logs_full_notm}}](/docs/cloud-logs?topic=cloud-logs-getting-started) for more information.

## Viewing logs
{: #logging_view-old}

To view and analyze platform logs for an {{site.data.keyword.en_short}} instance, check that the {{site.data.keyword.logs_routing_full_notm}} instance is provisioned and target is set for the same region where the {{site.data.keyword.en_short}} instance that you want to monitor is available.
{: note}

To start the {{site.data.keyword.logs_routing_full_notm}} web UI to view logs, see [Navigating to the web UI](/docs/cloud-logs?topic=cloud-logs-instance-launch).

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}

For more information about launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

## Fields per log type
{: #logging_fields-old}

See the following table for the list of fields that are included in each log record:

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

For information about fields included in every platform log, see [Fields for platform logs](/docs/logs-router?topic=logs-router-about-platform-logs#platform_reqd)

## Log messages
{: #log_messages}

The following table lists the message IDs that are generated by {{site.data.keyword.en_short}}:

| Message ID | Log type    | Description |
|------------|-------------|-------------|
| `event-notifications.00001I` | `INFO` | This message provides information that a notification event from a source has been received.CRN is used for IBM Cloud services. SourceID can be an IBM Cloud service or a human, for example |
| `event-notifications.00002I` | `INFO` | This message provides information that a notification ID has been assigned to the event that originated from a source. |
| `event-notifications.00003I` | `INFO` | This message provides information that a notification event is published through a list of topic IDs. |
| `event-notifications.00004I` | `INFO` | This message provides information that a notification request is process by a list of subscribers. |
| `event-notifications.00006I` | `INFO` | This message provides information about the devices available for a valid platform. Valid platforms are [push_chrome, push_firefox, push_android, push_ios, push_safari] |
| `event-notifications.00007I` | `INFO` | This message provides information that an SMS is dispatched to a list of telephone numbers. |
| `event-notifications.00008I` | `INFO` | This message provides information that an email is sent to a specified list of addresses. |
| `event-notifications.00009I` | `INFO` | This message provides information that the webhook has been successfully served and reflects the response with the status code as 200 from the webhook API. |
| `event-notifications.00010I` | `INFO` | This message provides information that a notification event is sent to a specified list of subscriptions. |
| `event-notifications.00011I` | `INFO` | This message provides information that a notification event is sent to a specified list of destinations. |
| `event-notifications.00012I` | `INFO` | This message provides information about the number of devices and platforms for which a notification has been processed successfully. |
| `event-notifications.00013I` | `INFO` | This message provides information about the number of devices and platforms for which a notification has been dispatched successfully. |
| `event-notifications.00014I` | `INFO` | This message provides information that the slack destination has been successfully served and reflects the response with the status code as 200 from the slack API. |
| `event-notifications.00015I` | `INFO` | This message provides information that a notification is delivered to a device on a platform with a corresponding destination ,device and platform ID. |
| `event-notifications.00015I` | `INFO` | This message provides information about the device,platform and destination ID where the user has opened the notification. |
| `event-notifications.00016I` | `INFO` | This message provides information that the Microsoft Teams destination has been succesfully served and reflects the response with the status code as 200 from the Microsoft Teams API. |
| `event-notifications.00018I` | `INFO` | This message provides information that the Pager Duty destination has been succesfully served and reflects the response with the status code as 200 from the Pager Duty API. |
| `event-notifications.00019I` | `INFO` | This message provides information that the Code Engine destination has been successfully served and reflects the response with the status code as 200 from the Code Engine API. |
| `event-notifications.00020I` | `INFO` | This message provides information that a notification has been succesfully served to the Service Now destination has been served and reflects the response with the status code as 200 from the Service Now API. |
| `event-notifications.00021I` | `INFO` | This message provides information that the {{site.data.keyword.cos_full_notm}} has been succesfully served and reflects the response from the {{site.data.keyword.cos_full_notm}} API. |
| `event-notifications.00022I` | `INFO` | This message provides information about an email of a specific size has been sent to a specified list of recipients from the sender. |
| `event-notifications.00023I` | `INFO` | This message provides information about an email of a specific size has been deferred to a specified list of recipients from the sender. |
| `event-notifications.00001W` | `WARN` | This message provides a warning that a notification event from a source has been rejected because no topic is configured for the source. The topic that is required to filter the event is missing. |
| `event-notifications.00002W` | `WARN` | This message provides a warning that a notification event from a source is invalid as it is not filtered by any topic. |
| `event-notifications.00003W` | `WARN` | This message provides a warning that a notification request processed by a specified list of subscribers is forbidden for a destination type. |
| `event-notifications.00004W` | `WARN` | This message provides a warning that a notification has not been dispatched as it has no subscribers. |
| `event-notifications.00005W` | `WARN` | This message provides a warning that the webhook API has returned an erroneous response with the status code 404. |
| `event-notifications.00006W` | `WARN` | This message provides a warning that the slack API has returned an erroneous response with the status code 404. |
| `event-notifications.00007W` | `WARN` | This message provides a warning that the Microsoft Teams API has returned an erroneous response with the status code 401. |
| `event-notifications.00008W` | `WARN` | This message provides a warning that the SMS is not delivered because it is unsubscribed by the SMS numbers. |
| `event-notifications.00010W` | `WARN` | This message provides a warning that the Pager Duty API has returned an erroneous response with the status code 401. |
| `event-notifications.00011W` | `WARN` | This message provides a warning that the Code Engine API has returned an erroneous response with the status code 401. |
| `event-notifications.00012W` | `WARN` | This message provides a warning that the Service Now API has returned an erroneous response with the status code 401. |
| `event-notifications.00013W` | `WARN` | This message provides a warning that an email of a specific size has bounced and the authenticity of the email has to be checked. |
| `event-notifications.00001E` | `ERROR` | This error message indicates that the notifications failed to dispatch to invalid devices. |
| `event-notifications.00002E` | `ERROR` | This error message indicates that the webhook API returned an erroneous response with the status code 404. |
| `event-notifications.00003E` | `ERROR` | This error message indicates that the notifications failed to dispatch due to authentication error for device and platform . |
| `event-notifications.00004E` | `ERROR` | This error message indicates that the Slack API returned an erroneous response with the status code 401.|
| `event-notifications.00005E` | `ERROR` | This error message indicates that the notifications failed to dispatch due to the `BadDeviceToken` error for a device and platform. |
| `event-notifications.00006E` | `ERROR` | This error message indicates that the Microsoft Teams API returned an erroneous response with the status code 401. |
| `event-notifications.00008E` | `ERROR` | This error message indicates that the Pager Duty API returned an erroneous response with the status code 401. |
| `event-notifications.00009E` | `ERROR` | This error message indicates that the Code Engine API returned an erroneous response with the status code 401. |
| `event-notifications.00010E` | `ERROR` | This error message indicates that the Service Now API returned an erroneous response with the status code 401. |
{: caption="Additional information about message IDs" caption-side="top"}

### List logs generated by a service
{: #logging_analyze_1-old}

If you want to view all the logs that are being generated for a particular instance, select the `guid` of {{site.data.keyword.en_short}} instance from left panel under subsystems and search the source in serach bar.

### List logs for a notification request
{: #logging_analyze_2-old}

If you know the notification ID that is generated for a request from a service or source to the {{site.data.keyword.en_short}} service, use the following query in {{site.data.keyword.logs_full_notm}} to list all logs for that particular notification ID:

```
<notification Id>
```
