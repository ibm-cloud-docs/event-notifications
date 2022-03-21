---

copyright:
  years: 2019, 2021
lastupdated: "2021-10-18"

keywords: event notifications logDNA , event notifications logging, event notifications external logs

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

### Common fields in the log records
|Log field|Description|
|---------|-----------|
|`logSourceCRN`| The CRN of the Event Notifications service instance for which the platform logs are ingested
|`resourceGroupID` | The CRN of the resource group in which the event notification instance is created
|`messageId` | Unique identifier of the message in the log
|`message` | Summary of the log record.
|`sourceID`| The CRN of the source from which the event is ingested


### Platform logs for events received
Event notifications service ingests a log when the event is received from a configured source.

Example log:

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.78081I","level":"INFO","message":"An event is received from the source: crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f::","notificationID":"","sourceID":"crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f::","resolution":null,"documentUrl":null}
```

|Log field|Description|
|---------|-----------|
|`notificationID`| Since the event is not yet ingesed the notificationID is not generated
| `level` | INFO
|`message`| An event is received from the source:`<source_CRN>`

### Platform logs for events ingested
Event is ingested as it is filtered by atleast one condition specified in the topics.
Example log

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.94326I","level":"INFO","message":"An event from the source: crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f:: has been ingested into topic and got assigned a unique notification_id: 4da9f2d5-d69a-48b8-b17d-c8d4e990f01b","notificationID":"4da9f2d5-d69a-48b8-b17d-c8d4e990f01b","sourceID":"crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f::","resolution":null,"documentUrl":null}
```
|Log field|Description|
|---------|-----------|
|`notificationID`| A unique ID is generated to identify the notification.
| `level` | INFO|
| `message`| An event from the source <source_crn> has been ingested into topic and got assigned a unique notificationID

If there is no topic configured for the source, notification ID is not generated and the event is not ingested.

Example log:

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:us-south:a/4a74f2c31f554afc88156b73a1d577c6:307c3955-fe0a-44de-b92b-3fa133815aac::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:86125079d24a4a70af67902e3c4f96c2","saveServiceCopy":true,"messageId":"event-notifications.20774W","level":"WARN","message":"An event is not ingested as no topic is configured for the source: crn:v1:bluemix:public:sysdig-monitor:us-south:a/4a74f2c31f554afc88156b73a1d577c6:c38cce22-e939-432b-be61-3aee6d501b97::","notificationID":"","sourceID":"crn:v1:bluemix:public:sysdig-monitor:us-south:a/4a74f2c31f554afc88156b73a1d577c6:c38cce22-e939-432b-be61-3aee6d501b97::","resolution":"Configure a topic for the source","documentUrl":"https://cloud.ibm.com/docs/event-notifications"}
```

|Log field|Description|
|---------|-----------|
|`message`|An event is not ingested as no topic is configured
| `level` | WARN
| `resoulution`| Configure a topic for the source


### Platform logs for topics filtered

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.55084I","level":"INFO","message":"The event is forwarded to these topics: [\"31b8e69b-aea1-43a8-8756-adac70679b5e\"]","notificationID":"4da9f2d5-d69a-48b8-b17d-c8d4e990f01b","sourceID":"crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f::","resolution":null,"documentUrl":null}
```


|Log field|Description|
|---------|-----------|
|`message`|The event is forwarded to these topics:[<topic_names>]
| `level` | INFO


### Platform logs for subscriptions

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.36037I","level":"INFO","message":"The notification is sent to the subscriptions: [\"a9035e6b-078c-4793-a600-909bfe460d42\"]","notificationID":"4da9f2d5-d69a-48b8-b17d-c8d4e990f01b","sourceID":"crn:v1:bluemix:public:sysdig-monitor:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:e67bf03a-dad4-4613-b186-b24604f1f40f::","resolution":null,"documentUrl":null}
```

|Log field|Description|
|---------|-----------|
|`message`|The event is forwarded to these subscriptions:[<subscription_names>]
| `level` | INFO

Error message for Non IBM Sources

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.52383W","level":"WARN","message":"The notification is not forwarded to subscriptions [\"66a707d2-dd47-41c2-b5ff-d7ce1c2c993d\",\"eea2e12d-b4f9-400a-af57-f7daeabd2e05\",\"f475a70f-77e9-4947-aef3-7d1db1122ab4\"] as it is forbidden for destination type: smtp_ibm","notificationID":"299b75de-342e-44eb-b524-a83b3093a44b","sourceID":"b0fb9b50-c5ed-468a-9ba9-0ff3b9f33afd:api","resolution":"Non IBM sources cannot be sent to out of the box destinations. ","documentUrl":"https://cloud.ibm.com/docs/event-notifications"}
```
|Log field|Description|
|---------|-----------|
|`message`|The notification is not forwarded to subscriptions <subscription_names> as it is forbidden for destination type: smtp_ibm
| `level` | WARN
|`resolution`|Non IBM sources cannot be sent to out of the box destinations

### Platform logs for  Push Notifications destinations

Logs for processing and number of devices

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.62977I","level":"INFO","message":"Processing notification for total devices: 1","notificationID":"5abbeefa-4748-4e63-872d-a3aec751e7af","sourceID":"b0fb9b50-c5ed-468a-9ba9-0ff3b9f33afd:api","resolution":"","documentUrl":""}
```
|Log field|Description|
|---------|-----------|
|`message`|Processing notification for total devices: <num_of_devices>
| `level` | INFO


Processing and platorm details for push destinations

```sh
{"logSourceCRN":"crn:v1:bluemix:public:event-notifications:au-syd:a/4a74f2c31f554afc88156b73a1d577c6:9a7e1000-44d7-46a1-b27f-4088134be4b6::","resourceGroupID":"crn:v1:bluemix:public:resource-controller::a/4a74f2c31f554afc88156b73a1d577c6::resource-group:ff5e9e21e6944306ae79d60f6da7fd69","saveServiceCopy":true,"messageId":"event-notifications.85844I","level":"INFO","message":"Notification processed successfully for devices: 1 and platform: G","notificationID":"5abbeefa-4748-4e63-872d-a3aec751e7af","sourceID":"b0fb9b50-c5ed-468a-9ba9-0ff3b9f33afd:api","resolution":null,"documentUrl":null}
```
|Log field|Description|
|---------|-----------|
|`message`|"Notification processed successfully for devices: 1 and platform: G
| `level` | INFO


### Platform logs for SMS Status

Example Log

```sh
{"logSourceCRN":"crn:v1:staging:public:event-notifications-dev:us-south:a/8c226dc8c8bfb9bc3431515a1618726b:829ed8cd-593d-4f5f-a355-7bcee7bad144::","resourceGroupID":"crn:v1:staging:public:resource-controller::a/8c226dc8c8bfb9bc3431515a1618726b::resource-group:4f15679623607b855b1a27a67f15f1c2","saveServiceCopy":true,"messageId":"event-notifications-dev.23854I","level":"INFO","message":"SMS dispatched to the numbers: [+12099216581]","notificationID":"37c15417-2109-44d3-8cfd-5411642454a8","sourceID":"da091186-2f22-43aa-b16b-81e9ab20ac6c:api","resolution":null,"documentUrl":null}
```

|Log field|Description|
|---------|-----------|
|`message`|"SMS dispatched to the numbers: <phone_numbers>
| `level` | INFO


### Platform logs for Email Status

Example Log

```sh
{"logSourceCRN":"crn:v1:staging:public:event-notifications-dev:us-south:a/8c226dc8c8bfb9bc3431515a1618726b:829ed8cd-593d-4f5f-a355-7bcee7bad144::","resourceGroupID":"crn:v1:staging:public:resource-controller::a/8c226dc8c8bfb9bc3431515a1618726b::resource-group:4f15679623607b855b1a27a67f15f1c2","saveServiceCopy":true,"messageId":"event-notifications-dev.55923I","level":"INFO","message":"Emails are sent to the IDs: [geetmanghnani@gmail.com]","notificationID":"7bf54fd4-aec1-4314-9c4a-dea1f2815229","sourceID":"da091186-2f22-43aa-b16b-81e9ab20ac6c:api","resolution":null,"documentUrl":null}
```

|Log field|Description|
|---------|-----------|
|`message`|Emails are sent to the IDs <EmailIDs>
| `level` | INFO

### Platform logs for Webhook Status

Example Log for webhook successfully served

```sh
{"logSourceCRN":"crn:v1:staging:public:event-notifications-dev:us-south:a/8c226dc8c8bfb9bc3431515a1618726b:829ed8cd-593d-4f5f-a355-7bcee7bad144::","resourceGroupID":"crn:v1:staging:public:resource-controller::a/8c226dc8c8bfb9bc3431515a1618726b::resource-group:4f15679623607b855b1a27a67f15f1c2","saveServiceCopy":true,"messageId":"event-notifications-dev.24705I","level":"INFO","message":"Webhook is successfully served, Response from the webhook: OK with the status code: 200","notificationID":"06245691-ee87-4ae7-a043-950d1309c345","sourceID":"da091186-2f22-43aa-b16b-81e9ab20ac6c:api","resolution":null,"documentUrl":null}
``` 


|Log field|Description|
|---------|-----------|
|`message`|Webhook is successfully served, Response from the webhook: OK with the status code: 200
| `level` | INFO

Example Log for webhook with error response

```sh
{"logSourceCRN":"crn:v1:staging:public:event-notifications-dev:us-south:a/8c226dc8c8bfb9bc3431515a1618726b:829ed8cd-593d-4f5f-a355-7bcee7bad144::","resourceGroupID":"crn:v1:staging:public:resource-controller::a/8c226dc8c8bfb9bc3431515a1618726b::resource-group:4f15679623607b855b1a27a67f15f1c2","saveServiceCopy":true,"messageId":"event-notifications-dev.45447W","level":"WARN","message":"Webhook returned with an error response: 500 Internal Server Error https://webhook.site/320eb9d0-14d0-449c-847d-e8fc261d28f6 with the status code: 500","notificationID":"7475dca4-c6b7-4c5f-9e71-84a4b9da0648","sourceID":"da091186-2f22-43aa-b16b-81e9ab20ac6c:api","resolution":"Check the configured URL for the webhook as well as the headers provided.","documentUrl":"https://cloud.ibm.com/docs/event-notifications"}
```
|Log field|Description|
|---------|-----------|
|`message`|"Webhook returned with an error response: 500 Internal Server Error https://webhook.site/320eb9d0-14d0-449c-847d-e8fc261d28f6 with the status code: 500
| `level` | WARN



## Analyzing Logs for IBM Cloud Event Notifications

For analyzing logs for your IBM Cloud Event Notifications, the following indexes can be useful

 - logSourceCRN
 - sourceID
 - notificationID
 - level


If you want to list all the logs coming from a particular source, Get the source ID from the Event Notifications service dashboard and query in the IBM Cloud Log Analysis dashboard

```sh
sourceID: <source_crn>
```

If you know the notification ID of the event ingested in the Event notification service, you can list all the external logs for that particular notification ID

```sh
notificationID: <notification Id>
```


