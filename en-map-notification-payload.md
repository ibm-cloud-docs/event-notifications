---

copyright:
  years: 2025
lastupdated: "2025-03-26"

keywords: event notifications, event-notifications, map event notifications to destinations
subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Transforming messages with notification payloads for destinations
{: #en-map-notificationpayload-destination-params}

Event notification payloads include a set of default parameters that are consistently mapped across all destinations.
However, to align with specific properties of the destination, you must incorporate extra parameters into the payload.
You can simultaneously send event notifications to individuals, your application, and your automation suite.

You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.compliance_short}}, {{site.data.keyword.secrets-manager_short}}, {{site.data.keyword.cloud_notm}} Projects, and Toolchain to communication channels like email, SMS, push notifications, Huawei Cloud Push, webhook, slack, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

To understand more about the event notification payload, see [Event Notifications payload](/docs/event-notifications?topic=event-notifications-en-spec-payload).

Events can be used to trigger proactive alerts and can also be derived from logs for metric collection or debugging purposes.
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
The preceding structure is a typical example of a payload that is used by {{site.data.keyword.logs_full_notm}} to be fanned out to multiple destinations. To understand this usage more, see the [Event payload that is sent from IBM Cloud Logs to IBM Cloud Event Notifications](/docs/cloud-logs?topic=cloud-logs-event-payload).

The `data` key here has alert definition values. They are alert ID, name, alert type, description, and security. It also has a log example key. These values can be used at the destination endpoint when the event is consumed and transformed. You can use templates for most of the destinations to help to frame or transform the event payload into a meaningful message.

Map the notification payload properties to transform the messages to the following destinations.

## Default email
{: #en-map-notificationpayload-destination-deEmail}

For default emails, users cannot modify the email template and it is dedicated to the events sourced from IBM Cloud sources only.
Also, API sources cannot send notifications to IBM Cloud email destination.
These emails originate from `no-reply@cloud.ibm.com` or `eventnotifications@cloud.ibm.com`, while you can add your own reply-to address.
{: important}

`ibmendefaultshort` maps to the subject of the email.
`ibmendefaultlong` maps to email body.

## Default SMS
{: #en-map-notificationpayload-destination-deSMS}

`ibmendefaultlong` is a part of the SMS body.

## Custom email
{: #en-map-notificationpayload-destination-cuEmail}

Use an email Template to personalize the messages transformed from events. Also, email templates are supported for Custom Domain email destination. You can use any of the keys that are defined under the `data` key as an input to the template.
To understand more about email templates, see [Email Templates](/docs/event-notifications?topic=event-notifications-en-email-templates).

`ibmendefaultshort` maps to the subject of the email.
In cases where a custom template is not available, the system automatically defaults to the `ibmenhtmlbody` template. If the `ibmenhtmlbody` template is also not available, the system gracefully fallbacks to the `ibmendefaultlong`, ensuring a smooth and consistent user experience.

You can opt out from the conventional subscription process, and specify the preferred email addresses and templates in the notifications payload. To know more about the opt-out capability, see [Custom Domain email Opt-out functions](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out).

If you have enabled the opt-out feature and completed the opt-out questionnaire,
1. `ibmenmailto` key gets preference, even if subscribed email list is already present under connected subscription.
1. `ibmentemplates` key gets preference, even if a Notification Template is attached to the subscription.

## Custom SMS
{: #en-map-notificationpayload-destination-cuSMS}

`ibmensmstext` is a part of the SMS body. If not specified, the SMS body constitutes of `ibmendefaultlong`.
`ibmensmsto` has a list of destination numbers. If not specified, the events route to the phone numbers in the recipient list defined in the SMS destination.
`ibmenmms` maps to the MMS body if you use Multimedia Messaging Service (MMS).

## Webhooks
{: #en-map-notificationpayload-destination-webHook}

Use the Webhook notification Template to transform event notifications to be consumed programmatically.
The keys that are defined as part of a `data` block maps to specific properties in the template block. To understand more about the Webhook notification Template, see [Webhooks](/docs/event-notifications?topic=event-notifications-en-webhook-notifications-template).

## Slack
{: #en-map-notificationpayload-destination-slack}

Use Slack Template to transform event notification to Slack.
The keys that are defined as part of a `data` block maps to specific properties in the template block. To understand more about the Slack Template, see [Slack](/docs/event-notifications?topic=event-notifications-en-slack-notification-template).

If a template is not defined, the system gracefully fallbacks to the `ibmendefaultlong` for the body of the message.


## Microsoft&reg; Teams
{: #en-map-notificationpayload-destination-teams}

To post a Microsoft Teams notification, you need to create an incoming webhook URL. To understand more about the Microsoft Teams notification, see [Microsoft Teams](/docs/event-notifications?topic=event-notifications-en-destinations-msteams).

`ibmendefaultshort` maps to the default short payload.
`ibmendefaultlong` maps to the default long payload.
`data` block maps to data JSON that is formatted as JSON in the Microsoft Teams notification.

## ServiceNow
{: #en-map-notificationpayload-destination-SNow}

The event notification payload keys are mapped to destination fields of ServiceNow fields.
`ibmendefaultshort` maps to `short_description` field.
`description` maps to `data` or `ibmendefaultlong` if `data` is not specified.
`ibmenseverity` maps to `impact` field.
`urgency` and `priority` to the respective fields of ServiceNow fields.


## PagerDuty
{: #en-map-notificationpayload-destination-pagerDuty}

Use PagerDuty Template to transform event notification to PagerDuty.
The keys that are defined as part of a `data` block maps to specific properties in the template block. To understand more about the PagerDuty Template, see [PagerDuty Template](/docs/event-notifications?topic=event-notifications-en-pagerduty-notification-template).

If a template is not defined, the event notification payload keys are mapped to the destination fields of PagerDuty.
`ibmendefaultlong` maps to the `payload.summary` field.
`critical` maps to `payload.severity` field.
`time` maps to the `payload.timestamp` field.
`data` maps to the `payload.custom_details` field.
`source` maps to `payload.source` field.

## Push Android
{: #en-map-notificationpayload-destination-pushAndroid}

`ibmenfcmbody` maps to the body of the message that is sent to the Firebase Cloud Messaging (FCM) server.
`ibmenfcmbody` is used only if `ibmenpushto` targets Android device/s enlisted in `fcm_devices` or has a targeted platform `push_android` enlisted in `platforms`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmenfcmbody` is not specified, `ibmendefaultlong` is used as the notification body.

## Push iOs
{: #en-map-notificationpayload-destination-pushIOS}

`ibmenapnsbody` maps to the body of the message that is sent to the Apple Push Notification server (APNs).
`ibmenapnsbody` is used only if `ibmenpushto` targets iOs device/s enlisted in `apns_devices` or has a targeted platform `push_ios`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmenapnsbody` is not specified, `ibmendefaultlong` is used as the notification body.


## Push Chrome
{: #en-map-notificationpayload-destination-pushChrome}

`ibmenchromebody` maps to the body of the message that is sent to a Firebase Cloud Messaging (FCM) server.
`ibmenchromebody` is used only if `ibmenpushto` targets Chrome device/s enlisted in `chrome_devices` or has a targeted platform `push_chrome`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmenchromebody` is not specified, `ibmendefaultlong` is used as the notification body.

## Push Firefox
{: #en-map-notificationpayload-destination-pushFirefox}

`ibmenfirefoxbody` maps to the body of the message that is sent to a Firefox Push server.
`ibmenfirefoxbody` is used only if `ibmenpushto` targets Firefox device/s enlisted in `firefox_devices` or has a targeted platform `push_firefox`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmenfirefoxbody` is not specified, `ibmendefaultlong` is used as the notification body.

## Push Safari
{: #en-map-notificationpayload-destination-pushSafari}

`ibmensafaribody` maps to the body of the message that is sent to the Apple Push Notification Server (APNs).
`ibmensafaribody` is used only if `ibmenpushto` targets Safari device/s enlisted in `safari_devices` or has a targeted platform `push_safari`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmensafaribody` is not specified, `ibmendefaultlong` is used as the notification body.

## Push Huawei
{: #en-map-notificationpayload-destination-pushHuawei}

`ibmenhuaweibody` maps to the body of the message that is sent to the Huawei Push Kit Server.
`ibmenhuaweibody` is used only if `ibmenpushto` targets Huawei device/s enlisted in `huawei_devices` or has a targeted platform `push_huawei`. Also, `user_ids` and `tags` are also used to target user IDs and push tags enlisted in `ibmenpushto`.
If `ibmenhuaweibody` is not specified, `ibmendefaultlong` is used as the notification body.

## {{site.data.keyword.codeengineshort}}
{: #en-map-notificationpayload-destination-codeengine}

{{site.data.keyword.codeengineshort}} consumes event notification payloads programmatically. Depending on the type of consumer, web-apps, micro-services, event driven functions, or a batch job, the structure of `data` and type of `datacontenttype` varies.

## {{site.data.keyword.cos_full_notm}}
{: #en-map-notificationpayload-destination-cos}

{{site.data.keyword.cos_full_notm}} consumes event notification payloads programmatically. Depending on the type of storage requirement, the structure of `data` and type of `datacontenttype` varies.

## {{site.data.keyword.messagehub}}
{: #en-map-notificationpayload-destination-eventstreams}

{{site.data.keyword.messagehub}} consumes event notification as a message to be read once, as {{site.data.keyword.messagehub}} is a Kafka managed message bus. Depending on the type of message you want to send, the structure of `data` and type of `datacontenttype` varies.
