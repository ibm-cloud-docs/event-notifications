---

copyright:
  years: 2025
lastupdated: "2025-03-13"

keywords: event notifications, event-notifications, map event notifications to destinations
subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Map Event notification payloads to destination fields
{: #en-map-notificationpayload-destination-params}

Event notification payloads include a set of default parameters that are consistently mapped across all destinations.
However, to align with specific properties of the destination, you must incorporate additional parameters into the payload.
You can simultaneously send event notifications to individuals, your application, and your automation suite.

You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.compliance_short}}, {{site.data.keyword.secrets-manager_short}}, {{site.data.keyword.cloud_notm}} Projects, and Toolchain to communication channels like email, SMS, push notifications, Huawei Cloud Push, webhook, slack, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

To understand more about the event notification payload [see](/docs/event-notifications?topic=event-notifications-en-spec-payload#en-ce-mandatory-attributes).

Events can be utilized to trigger proactive alerts and can also be derived from logs for metric collection or debugging purposes.
To ensure that notifications are informative and useful to the recipient, it's crucial to construct a comprehensive notification payload.
A typical alert or log payload generally follows this structure.

```json
{
   "data": {
      "alert_definition": {
         "alert_type": "StandardMoreThanAlertEvent",
         "condition": {
            "MoreThan": {
               "condition_threshold": 1,
               "condition_timeframe": 1
            }
         },
         "description": "",
         "id": "<alert_id>",
         "meta_labels": {
                "env": "prod"
            },
         "name": "<alert_name>",
         "query_statement": "_exists_:level",
         "severity": "ERROR"
      },
      "latest_event_timestamp": 0000000000000,
      "links": {
         "edit_alert": "https://dashboard.eu-gb.logs.cloud.ibm.com/<instance_id>/#/alerts/<alert_id>",
         "view_alert": "https://dashboard.eu-gb.logs.cloud.ibm.com/<instance_id>/#/insights?id=c9fe7539-e901-4745-b3ad-29ca0ae987a0"
      },
      "log_example": {"msg":"Test Log"},
      "log_example_truncated": true,
      "meta_labels_truncated": false,
      "status": "triggered"
   },
   "datacontenttype": "application/json",
   "ibmendefaultlong": "Triggered: 2024-01-01T00:00:00Z",
   "ibmendefaultshort": "ERROR - new_groupBy",
   "ibmenseverity": "info",
   "ibmensourceid": "crn:v1:bluemix:public:logs:<region>:a/<account_id>:<instance_id>::",
   "id": "997355d5-4542-47fd-9868-84cf5df71e1b_c9fe7539-e901-4745-b3ad-29ca0ae987a0",
   "notification_id": "923873c0-2b42-4d4c-a9a0-c69339b16717",
   "source": "crn:v1:bluemix:public:logs:<region>:a/<account_id>:<instance_id>::",
   "specversion": "1.0",
   "time": "2024-01-01T00:00:00.000000Z",
   "type": "com.ibm.cloud.logs.<event_type>:<event_subtype>"
}
```
The preceding structure is a typical example of a payload that is used by {{site.data.keyword.logs_full_notm}} to be fanned out to multiple destinations. To understand this usage more, [see](/docs/cloud-logs?topic=cloud-logs-event-payload).

The **data** key here has alert definition values. They are alert ID, name, alert type, desciption, and security. It also has a log example key. These values can be used at the destination endpoint once the event is consumed and transformed. You can use templates for most of the destinations to help to frame or transform the event payload into a meaningful message.

To help you to develop a notification payload to send to any of the destinations, understand the following mapping.

## Map notification payload to default email destination
{: #en-map-notificationpayload-destination-deEmail}

For default emails, users cannot modify the email template and it is dedicated to the events sourced from IBM Cloud sources only.
Also, API sources cannot send notifications to IBM Cloud email destination.
These emails originate from no-reply@cloud.ibm.com or eventnotifications@cloud.ibm.com, while you can add your own reply-to address
{: important}

**ibmendefaultshort** maps to the subject of the email.
**ibmendefaultlong** maps to email body.

## Map notification payload to default SMS destination
{: #en-map-notificationpayload-destination-deSMS}

**ibmendefaultshort** is a part of the subject of SMS.
**ibmendefaultlong** is a part of the SMS body.


## Map notification payload to custom email destination
{: #en-map-notificationpayload-destination-cuEmail}

Use email Template to personalize the messages transformed from events. Also email templates are supported for Custom Domain email destination. You can use any of the keys that are defined under the **data** key as an input to the template.
To understand more about email templates, [see](/docs/event-notifications?topic=event-notifications-en-email-templates).

**ibmendefaultshort** maps to the subject of the email.
In cases where a custom template is not available, the system automatically defaults to the **ibmenhtmlbody** template. If the **ibmenhtmlbody** template is also unavailable, the system gracefully fallbacks to the **ibmendefaultlong**, ensuring a smooth and consistent user experience.

## Map notification payload to custom SMS destination
{: #en-map-notificationpayload-destination-cuSMS}

**ibmensmstext** is a part of the SMS body. If not specified, the SMS body constitutes of **ibmendefaultlong**.
**ibmensmsto** has a list of destination numbers. If not specified, the events route to the phone numbers in the recipient list defined in the SMS destination.
**ibmenmms** maps to the MMS body if you use Multimedia Messaging Service (MMS). 

# Map notification payload to Webhooks destination
{: #en-map-notificationpayload-destination-webHook}

Use the Webhook notification Template to transform event notifications to be consumed programmatically.
The keys that are defined as part of a **data** block maps to specific properties in the template block. To understand more about the Webhook notification Template, [see](/docs/event-notifications?topic=event-notifications-en-webhook-notifications-template).

## Map notification payload to Slack destination
{: #en-map-notificationpayload-destination-slack}

Use Slack Template to transform event notification to Slack.
The keys that are defined as part of a **data** block maps to specific properties in the template block. To understand more about the Slack Template, [see](/docs/event-notifications?topic=event-notifications-en-slack-notification-template).

If a template is not defined, the system gracefully fallbacks to the **ibmendefaultlong** for the body of the message.


## Map notification payload to Microsoft&reg; Teams destination
{: #en-map-notificationpayload-destination-teams}

To post a Microsoft Teams notification, you need to create an incoming webhook URL. To understand more about the Microsoft Teams notification, (see)[/docs/event-notifications?topic=event-notifications-en-destinations-msteams].

**ibmendefaultshort** maps to the default short payload.
**ibmendefaultlong** maps to the default long payload.
**data** block maps to data JSON which is formatted as JSON in the Microsoft Teams notification.

## Map notification payload to ServiceNow destination
{: #en-map-notificationpayload-destination-SNow}

The event notification payload keys are mapped to destination fields of ServiceNow fields.
**ibmendefaultshort** maps to **short_description** field.
**description** maps to **data** or **ibmendefaultlong** if **data** is not specified.
**ibmenseverity** maps to **impact** field.
**urgency** and **priority** to the respective fields of ServiceNow fields.


## Map notification payload to PagerDuty destination
{: #en-map-notificationpayload-destination-pagerDuty}

Use PagerDuty Template to transform event notification to PagerDuty.
The keys that are defined as part of a **data** block maps to specific properties in the template block. To understand more about the PagerDuty Template, [see](/docs/event-notifications?topic=event-notifications-en-pagerduty-notification-template).

If a template is not defined, the event notification payload keys are mapped to the destination fields of PagerDuty.
**ibmendefaultlong** maps to the **payload.summary** field.
**critical** maps to **payload.severity** field.
**time** maps to the **payload.timestamp** field.
**data** maps to the **payload.custom_details** field.
**source** maps to **payload.source** field.

## Map notification payload to Push Android destination
{: #en-map-notificationpayload-destination-pushAndroid}

**ibmenfcmbody** maps to the body of the messase sent to the FCM server.
**ibmenfcmbody** is used only if **ibmenpushto** has a targeted Android device, otherwise it is ignored.
If **ibmenfcmbody** is not specified, **ibmendefaultlong** is used as the notification body.

## Map notification payload to Push IOS destination
{: #en-map-notificationpayload-destination-pushIOS}

**ibmenapnsbody** maps to the body of the messase sent to the APNs server.
**ibmenapnsbody** is used only if **ibmenpushto** has a targeted an IoS device, otherwise it is ignored.
If **ibmenapnsbody** is not specified, **ibmendefaultlong** is used as the notification body.


## Map notification payload to Push Chrome destination
{: #en-map-notificationpayload-destination-pushChrome}

**ibmenchromebody** maps to the body of the messase sent to a web server.
**ibmenchromebody** is used only if **ibmenpushto** has a targeted an Chrome device, otherwise it is ignored.
If **ibmenchromebody** is not specified, **ibmendefaultlong** is used as the notification body.

## Map notification payload to Push Firefox destination
{: #en-map-notificationpayload-destination-pushFirefox}

**ibmenfirefoxbody** maps to the body of the message sent to a web server.
**ibmenfirefoxbody** is used only if **ibmenpushto** has a targeted an Firefox device, otherwise it is ignored.
If **ibmenfirefoxbody** is not specified, **ibmendefaultlong** is used as the notification body.

## Map notification payload to Push Safari destination
{: #en-map-notificationpayload-destination-pushSafari}

**ibmensafaribody** maps to the body of the message sent to the web server.
**ibmensafaribody** is used only if **ibmenpushto** has a targeted a Safari device, otherwise it is ignored.
If **ibmensafaribody** is not specified, **ibmendefaultlong** is used as the notification body.

## Map notification payload to Push Huawei destination
{: #en-map-notificationpayload-destination-pushHuawei}

**ibmenhuaweibody** maps to the body of the message sent to the web server.
**ibmenhuaweibody** is used only if **ibmenpushto** has a targeted a Huawei device, otherwise it is ignored.
If **ibmensafaribody** is not specified, **ibmendefaultlong** is used as the notification body.


