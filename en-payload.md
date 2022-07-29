---

copyright:
  years: 2022
lastupdated: "2022-07-05"

keywords: event-notifications, event notifications migration, notifications, destinations, specification

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_short}} payload
{: #en-spec-payload}

This document outlines the {{site.data.keyword.en_short}} specification.
{: shortdesc}

## Introduction
{: #en-spec-payloadintro}

This document describes the payload details for sending events using the API sources in EN. API sources can be used to send events from your backend applications. You can use this to send Push notifications from business backends.

Events from API sources cannot be routed to IBM Email and IBM SMS destinations.
{: important}

```sh
`METHOD: POST`
`URL: /event-notifications/v1/apps/{instanceID}/notifications`
`Header: Authorization: Bearer <IAM token>`
```

The Events adhere to Cloud Event standard. You can find more information about Cloud Events here. 

## Modes of transport 
{: #en-modes-of-transport}

{{site.data.keyword.en_short}} supports two modes to make HTTP calls. This is adhering to the CoudEvents specification. More details here.

Event Notifications supports the following two modes from the CloudEvents specification:

### Binary Mode
{: #en-binary-mode}

In the binarycontent mode, the value of the event `data` is placed into the HTTP request, or response, body as-is, with the `datacontenttype` attribute  value declaring its media type in the HTTP `Content-Typeheader`; all other event attributes are mapped to HTTP headers.

All the attribute names are prefixed with `ce-` and added to the header (except for the `data` and `datacontenttype`).

Binary Mode is recommended way to send notifications.
{: note}

### Structured Mode
{: #en-structured-mode}

In the structured content mode, event metadata attributes and event data are placed into the HTTP request body. For structured mode set the `Content-Typeheader` to `application/cloudevents+json`.

## Attributes
{: #en-attributes}

### CE Mandatory Attributes
{: #en-ce-mandatory-attributes}

The following attributes are mandatory for the event request to be accepted.

#### id (String)
{: #en-id-string}

A unique identifier that identifies each event. `source+id` must be unique. The backend should be able to uniquely track this id in logs and other records. Send unique ID for each send notification. Same ID can be sent in case of failure of send notification. 

`source+id` will be logged in IBM Cloud Logging service. Using this combination IBM customers will be able to trace the event movement from one system to another and will aid in debugging and tracing.

##### Example
{: #en-example1}

```JSON
id: qwer-1234-1qsd-po94
```

##### Binary mode header
{: #en-binary-mode-header}

```JSON
ce-id: qwer-1234-1qsd-po94
```

#### source (URI-reference)
{: #en-source-uri-reference}

This is the identifier of the event producer. A way to uniquely identify the source of the event. For IBM Cloud services this is the crn of the service instance producing the events. For API sources this can be something the event producer backend can uniquely identify itself with.

##### Example
{: #en-example2a}

```JSON
source: com.mybank.customerbanking.accountmanagement
```

##### Binary mode header
{: #en-binary-mode-header1}

```JSON
ce-source: com.mybank.customerbanking.accountmanagement
```

#### specversion (string) 
{: #en-specversion-string}

This is the version of CloudEvents specification that {{site.data.keyword.en_short}} currently supports. This value must be set to "1.0"

##### Example
{: #en-example3}

```JSON
specversion:1.0
```

##### Binary mode header
{: #en-binary-mode-header2}

```JSON
ce-specversion:1.0
```

#### type (string) 
{: #en-type-string}

This describes the type of event. It is of the form `<event-type-name>:<sub-type>`. This type is defined by the producer.
The event type name has to be prefixed with the reverse DNS names so the event type is uniquely identified. The same event type can be produced by 2 different sources. It is highly recommended to use hyphen `-` as a separator instead of `_`.

##### Example 1
{: #en-example4}

```sh
`type:com.acmebank.password:expiring-in-15-days`  
Type: `com.acmebank.password`  
Sub type: `expiring-in-15-days`  
```

##### Binary mode header
{: #en-binary-mode-header3}

```JSON
ce-type:com.acmebank.password:expiring-in-15-days`
```

##### Example 2
{: #en-example2}

```sh
`type:com.acmebank.password-changed`
Type: `com.acmebank.password-changed`
Sub type: N/A
```

##### Binary mode header (for Example 2)
{: #en-binary-mode-header4}

```JSON
`ce-type:com.acmebank.password-changed`
```

### CE optional attributes
{: #en-ce-optional-attributes}

Following attributes are optional but highly recommended to take full advantage of {{site.data.keyword.en_short}}.

#### time (timestamp)
{: #en-time-timestamp}

UTC time stamp when the event occurred. Must be in the RFC 3339 format.

##### Example
{: #en-example5}

```JSON
time: 2022-02-10T10:51:37+00:00
```

##### Binary mode header
{: #en-binary-mode-header5}

```JSON
ce-time: 2022-02-10T10:51:37+00:00
```

#### subject (String) 
{: #en-subject-string}

This is the subject of the event in the event producer (source). So, this can be the account ID of the password that’s about to expire.

##### Example
{: #en-example6}

```JSON
subject:ajay@accts.acmebank.com`
```

##### Binary mode header
{: #en-binary-mode-header6}

```sh
`ce-subject:ajay@accts.acmebank.com`  
```

#### datacontenttype
{: #en-datacontenttype}

Defines the MIME type of the data content. Currently only "application/json" is supported.

##### Example
{: #en-example7}

```sh
`datacontenttype: application/json`
```

##### Binary mode header
{: #en-binary-mode-header7}

```sh
`Content-Type:application/json`
```

#### data
{: #en-data}

The payload of the event. This can contain information that can be passed along to destinations like webhooks. Make sure that you are not sending any sensitive information. This has to be a valid JSON object.

##### Example
{: #en-example8}

```JSON
data: { "lastchanged-days": "74", "reason":"time-based"}
```

Binary mode – this is part of the HTTP body N/A.

### {{site.data.keyword.en_short}} extension mandatory attributes
{: #en-extension-mandatory-attributes}

These are mandatory attributes for every event sent to {{site.data.keyword.en_short}}.

#### ibmensourceid (string)
{: #en-ibmensourceid-string}

This is the ID of the source created in {{site.data.keyword.en_short}}. This is available in the {{site.data.keyword.en_short}} UI in the "Sources" section.

##### Example
{: #en-example9}

```JSON
ibmensourceid: 121313123:api
```

##### Binary mode header
{: #en-binary-mode-header8}

```JSON
ce-ibmensourceid: 121313123:api
```

### {{site.data.keyword.en_short}} extension optional attributes
{: #en-extension-optional-attributes}

These are optional attributes.

#### ibmenseverity(String) 
{: #en-ibmenseverify-string}

Some sources can have the concept of an Event severity. Hence a handy way is provided to specify a severity of the event. 

##### Example
{: #en-example10}

```JSON
ibmenseverity:LOW
```

##### Binary mode header
{: #en-binary-mode-header9}

```sh
`ce-ibmenseverity:LOW`
```

#### ibmendefaultshort(String) 
{: #en-ibmendefaultshort-string}

This message will be used in case the event is routed to a destination that needs a human readable text, but a destination specific attribute is not specified.

For example, if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultshort` will be used as the notification title (android_title).

##### Example
{: #en-example11}

```JSON
ibmendefaultshort: "Change password"
```

##### Binary mode header
{: #en-binary-mode-header10}

```JSON
ce-ibmendefaultshort: "Change password"
```

#### ibmendefaultlong(String)
{: #en-ibmendefaultlong-string}

This message will be used in case the event is routed to a destination that needs a human readable text, but a destination specific attribute is not specified.

For example, if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultlong` will be used as the notification body (alert).

##### Example
{: #en-example12}

```JSON
ibmendefaultlong: "Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password."
```

##### Binary mode header
{: #en-binary-mode-header11}

```JSON
ce-ibmendefaultlong: "Password will expire in 10 Days. Pleaselog in to the Bank home page and click on Change Password link to change your password."
```

#### ibmenfcmbody(string/json)
{: #en-ibmenfcmbody-string-json}

This attribute is needed if you want to send push notification to an Android device. This is the body that you want to send to FCM server, this has to be JSON in string format. For more info regarding FCM body please follow this documentation - https://firebase.google.com/docs/cloud-messaging/concept-options.

For backward compatibility for existing Push notification customers, the previous unified data format is still supported but is deprecated.

##### Example: Deprecated Push Notification service compatible format:
{: #en-example13}

```JSON
"ibmenfcmbody": "{\"en_data\":{\"alert\":\" Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password. \", \"android_title\":\"Change Password\"}}"
```

##### Binary mode header
{: #en-binary-mode-header12}

```JSON
ce-ibmenfcmbody: {"en_data":{"alert":" Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password. ", "android_title":"Change Password"}}
```

#### ibmenapnsbody(string/json)
{: #en-ibmenapnsbody-string-json}

This attribute is needed if you want to send push notification to an iOS device. This is the body that you want to send to APNs server, this has to be JSON in string format. For more info regarding APNs body please follow this documentation [here](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html){: external}.

For backward compatibility for existing Push notification customers, the previous unified data format is still supported but is deprecated.

##### Example: Deprecated Push Notification service compatible format:
{: #en-example14}

```JSON
"ibmenapnsbody": "{\"en_data\":{\"alert\":\"alert\",\"url\":\"https\",\"badge\":9,\"sound\":\"bingbong.aiff\",\"payload\":{\"myaarray\":[\"cc75e4a6-edd8-3bec-a7c3-dfca6572a03b\"]},\"type\":\"DEFAULT\",\"subtitle\":\"dummy\",\"title\":\"dummy1\",\"body\":\"body\",\"ios_action_key\":\"key\",\"interactive_category\":\"interactiveCategory\",\"title_loc_key\":\"titleLocKey\",\"loc_key\":\"GAME_PLAY_REQUEST_FORMAT\",\"launch_image\":\"image.png\",\"title_loc_args\":[\"Shelly\",\"Rick\"],\"loc_args\":[\"Shelly\",\"Rick\"],\"attachment_url\":\"some url\",\"apns_collapse_id\":\"12\",\"apns_thread_id\":\"1\",\"apns_group_summary_arg\":\"apnsGroupSummaryArg\",\"apns_group_summary_arg_count\":1}}"
```

##### Binary mode header
{: #en-binary-mode-header13}

```JSON
ce-ibmenapnsbody: {"en_data":{"alert":"alert","url":"https","badge":9,"sound":"bingbong.aiff","payload":{"myaarray":["cc75e4a6-edd8-3bec-a7c3-dfca6572a03b"]},"type":"DEFAULT","subtitle":"dummy","title":"dummy1","body":"body","ios_action_key":"key","interactive_category":"interactiveCategory","title_loc_key":"titleLocKey","loc_key":"GAME_PLAY_REQUEST_FORMAT","launch_image":"image.png","title_loc_args":["Shelly","Rick"],"loc_args":["Shelly","Rick"],"attachment_url":"some url","apns_collapse_id":"12","apns_thread_id":"1","apns_group_summary_arg":"apnsGroupSummaryArg","apns_group_summary_arg_count":1}}
```

To customise your APNs push notifications, you can provide APNs headers. Some of them are mandatory to deliver a notification if key is present. The required body as follows:

```JSON
"ibmenapnsheaders": "{\"apns-priority\":10, \"apns-collapse-id\": \"collapse\"}"
```

To get more details on APNs headers, you can check out [here](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/sending_notification_requests_to_apns/).

#### ibmenchromebody(string/json)
{: #en-ibmenchromebody-string-json}

This attribute is needed if you want to send push notification to a chrome device. This is the body that you want to send to web server, this has to be JSON in string format. For more info regarding chrome body please follow this documentation [here](https://developer.mozilla.org/en-US/docs/Web/API/Notification).

You can follow below example for quick start:

```JSON
"ibmenchromebody": "{\"title\":\"Hello Chrome\", \"options\": {}}"
```

##### Binary mode header
{: #en-binary-mode-header14}

```JSON
ce-ibmenchromebody: {"title":"Hello Chrome", "options": {}}
```

To customise your chrome push notifications, you can provide chrome headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenchromeheaders":"{\"TTL\":100}"
```

###### Binary mode header
{: #en-binary-mode-header15}

```JSON
ce-ibmenchromeheaders: "{"TTL":100}"
```

#### ibmenfirefoxbody(string/json)
{: #en-ibmenfirefoxbody-string-json}

This attribute is needed if you want to send push notification to a firefox device. This is the body that you want to send to web server, this has to be JSON in string format. For more info regarding Firefox body please follow this documentation [here](https://developer.mozilla.org/en-US/docs/Web/API/Notification).

You can follow below example for quick start:

```JSON
"ibmenfirefoxbody": "{\"title\":\"Hello Firefox\", \"options\": {}}"
```

##### Binary mode header
{: #en-binary-mode-header16}

```JSON
ce-ibmenfirefoxbody: {"title":"Hello Firefox", "options": {}}
```

To customise your chrome push notifications, you can provide firefox headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenfirefoxheaders": "{\"TTL\":100, \"Urgency\": \"low\" , \"Topic\": \"Test Firefox Notifications\"}",
```

###### Binary mode header
{: #en-binary-mode-header17}

```JSON
ce-ibmenfirefoxheaders: {"TTL":100, "Urgency": "low" , "Topic": "Test Firefox Notifications"}
```

```JSON
"ibmenapnsbody": "{\"en_data\":{\"alert\":\"alert\",\"url\":\"https\",\"badge\":9,\"sound\":\"bingbong.aiff\",\"payload\":{\"myaarray\":[\"cc75e4a6-edd8-3bec-a7c3-dfca6572a03b\"]},\"type\":\"DEFAULT\",\"subtitle\":\"dummy\",\"title\":\"dummy1\",\"body\":\"body\",\"ios_action_key\":\"key\",\"interactive_category\":\"interactiveCategory\",\"title_loc_key\":\"titleLocKey\",\"loc_key\":\"GAME_PLAY_REQUEST_FORMAT\",\"launch_image\":\"image.png\",\"title_loc_args\":[\"Shelly\",\"Rick\"],\"loc_args\":[\"Shelly\",\"Rick\"],\"attachment_url\":\"some url\",\"apns_collapse_id\":\"12\",\"apns_thread_id\":\"1\",\"apns_group_summary_arg\":\"apnsGroupSummaryArg\",\"apns_group_summary_arg_count\":1}}"
```

####### Binary mode header
{: #en-binary-mode-header18}

This contains details about the destination where you want to send push notification. This field is also string format of JSON and further contains following field

- `user_id` – Useridto be associated with the device. where you want to target your notification
- `tag` – This is used to send notifications on registered tags
- `platform` - For FCM we can target all registered device by giving platform as "G"
- `fcm_devices` – Unique identifier of the FCM device where you want to target your notification
- `apns_devices` - Unique identifier of the APNS device where you want to target your notification

##### Example
{: #en-example15}

```JSON
ibmenpushto: "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"]}"`
`ibmenpushto: "{\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"
```

Multiple destination can be targeted using following methods

```JSON
ibmenpushto: "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"],\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"
```

```JSON
ibmenpushto: "{\"user_id\": [\" ajay@accts.acmebank.com \",\" ankit@accts.acmebank.com \"]}"**Binary mode header**ce-ibmenpushto: "{\"user_id\": [\"ajay@accts.acmebank.com\",\"ankit@accts.acmebank.com\"]}"
```

```JSON
ce-ibmenapnsbody: {"en_data":{"alert":"alert","url":"https","badge":9,"sound":"bingbong.aiff","payload":{"myaarray":["cc75e4a6-edd8-3bec-a7c3-dfca6572a03b"]},"type":"DEFAULT","subtitle":"dummy","title":"dummy1","body":"body","ios_action_key":"key","interactive_category":"interactiveCategory","title_loc_key":"titleLocKey","loc_key":"GAME_PLAY_REQUEST_FORMAT","launch_image":"image.png","title_loc_args":["Shelly","Rick"],"loc_args":["Shelly","Rick"],"attachment_url":"some url","apns_collapse_id":"12","apns_thread_id":"1","apns_group_summary_arg":"apnsGroupSummaryArg","apns_group_summary_arg_count":1}}
```

To customise your APNs push notifications, you can provide APNs headers. Some of them are mandatory to deliver a notification if key is present. The required body as follows:

```JSON
"ibmenapnsheaders": "{\"apns-priority\":10, \"apns-collapse-id\": \"collapse\"}"
```

To get more details on APNs headers, you can check out [here](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/sending_notification_requests_to_apns/).

##### ibmenchromebody(string/json)
{: #en-ibmenchromebody-string-json1}

This attribute is needed if you want to send push notification to a chrome device. This is the body that you want to send to web server, this has to be JSON in string format. For more info regarding chrome body please follow this documentation [here](https://developer.mozilla.org/en-US/docs/Web/API/Notification).

You can follow below example for quick start:

```JSON
"ibmenchromebody": "{\"title\":\"Hello Chrome\", \"options\": {}}"
```

###### Binary mode header
{: #en-binary-mode-header19}

```JSON
ce-ibmenchromebody: {"title":"Hello Chrome", "options": {}}
```

To customise your chrome push notifications, you can provide chrome headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenchromeheaders":"{\"TTL\":100}"
```

####### Binary mode header
{: #en-binary-mode-header20}

```JSON
ce-ibmenchromeheaders: "{"TTL":100}"
```

##### ibmenfirefoxbody(string/json)
{: #en-ibmenfirefoxbody-string-json1}

This attribute is needed if you want to send push notification to a firefox device. This is the body that you want to send to web server, this has to be JSON in string format. For more info regarding Firefox body please follow this documentation [here](https://developer.mozilla.org/en-US/docs/Web/API/Notification).

You can follow below example for quick start:

```JSON
"ibmenfirefoxbody": "{\"title\":\"Hello Firefox\", \"options\": {}}"
```

###### Binary mode header
{: #en-binary-mode-header21}

```JSON
ce-ibmenfirefoxbody: {"title":"Hello Firefox", "options": {}}
```

To customise your chrome push notifications, you can provide firefox headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenfirefoxheaders": "{\"TTL\":100, \"Urgency\": \"low\" , \"Topic\": \"Test Firefox Notifications\"}",
```

####### Binary mode header
{: #en-binary-mode-header22}

```JSON
ce-ibmenfirefoxheaders: {"TTL":100, "Urgency": "low" , "Topic": "Test Firefox Notifications"}
```

##### ibmensafaribody(string/json)
{: #en-ibmensafaribody-string-json1}

This attribute is needed if you want to send push notification to a Safari device. This is the body that you want to send to web server, this has to be JSON in string format. For more info regarding Safari body please follow this documentation [here](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/NotificationProgrammingGuideForWebsites/PushNotifications/PushNotifications.html#//apple_ref/doc/uid/TP40013225-CH3-SW1).

You can follow below example for quick start:

```JSON
"ibmensafaribody": "{\"aps\":{\"alert\":{\"title\":\"Shipment Order 1832128321 Delevered\",\"body\":\"Shipment Order 1832128321 Delevered.\",\"action\":\"View\"},\"url-args\":[\"1832128321\"]}}"
```

###### Binary mode header
{: #en-binary-mode-header23}

```JSON
ce-ibmensafaribody: {"aps":{"alert":{"title":"Shipment Order 1832128321 Delevered","body":"Shipment Order 1832128321 Delevered.","action":"View"},"url-args":["1832128321"]}}
```

##### ibmenpushto(string/json)
{: #en-ibmenpushto-string-json}

This attribute is mandatory for successful delivery from an Android FCM or APNS destination

This contains details about the destination where you want to send push notification. This field is also string format of JSON and further contains following field

- `user_id` – Useridto be associated with the device. where you want to target your notification
- `tag` – This is used to send notifications on registered tags
- `platform` - We can target all registered device by platforms. 

Below are the corresponding platform values for each type of target.

- `FCM`: push_android
- `APNS`: push_ios 
- `Chrome`: push_chrome
- `Firefox`: push_firefox
- `Safari`: push_safari
- `fcm_devices` – Unique identifier of the FCM device where you want to target your notification
- `apns_devices` - Unique identifier of the APNS device where you want to target your notification
- `chrome_devices` - Unique identifier of the Chrome Web device where you want to target your notification
- `firefox_devices` - Unique identifier of the Firefox Web device where you want to target your notification
- `safari_devices` - Unique identifier of the Safari Web device where you want to target your notification

###### Example
{: #en-example16}

```JSON
"ibmenpushto": "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"]}"`
"ibmenpushto": "{\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"
"ibmenpushto": "{\"chrome_devices\": [\"2c75972a-37d0-3898-905d-3b5ee0d7c182\",\"N9CACDF5-1EBF-49E1-AD60-E25BA23E994D\"]}"
"ibmenpushto": "{\"firfox_devices\": [\"3c75972a-37d0-3898-905d-3b5ee0d7c182\",\"L9CACDF5-1EBF-49E1-AD60-E25BA23E994E\"]}"
"ibmenpushto": "{\"safari_devices\": [\"1175972a-37d0-3898-905d-3b5ee0d7c1D2\",\"Q9CACDF5-1EBF-49E1-AD60-E25BA23E994N\"]}"
```

Multiple destination can be targeted using following methods

```JSON
"ibmenpushto": "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"],\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"],\"chrome_devices\": [\"2c75972a-37d0-3898-905d-3b5ee0d7c182\",\"N9CACDF5-1EBF-49E1-AD60-E25BA23E994D\"],\"firefox_devices\": [\"3c75972a-37d0-3898-905d-3b5ee0d7c182\",\"L9CACDF5-1EBF-49E1-AD60-E25BA23E994E\"],\"safari_devices\": [\"1175972a-37d0-3898-905d-3b5ee0d7c1D2\",\"Q9CACDF5-1EBF-49E1-AD60-E25BA23E994N\"]}"
```

Targeting notifications to push user_ids.

```JSON
"ibmenpushto": "{\"user_ids\": [\"ajay@accts.acmebank.com\",\"ankit@accts.acmebank.com\"]}"
```

Targeting notifications to push tags.

```JSON
"ibmenpushto": "{\"tags\": [\"salesTeam\",\"TechTeam\"]}"
```

Targeting notifications to platforms.

```JSON
"ibmenpushto": "{\"platforms\":[\"push_android\",\"push_ios\"]]}"
```

Targeting notifications to specific platform.

```JSON
"ibmenpushto": "{\"platforms\":[\"push_android\"]}"
"ibmenpushto": "{\"platforms\":[\"push_ios\"]}"
"ibmenpushto": "{\"platforms\":[\"push_chrome\"]}"
"ibmenpushto": "{\"platforms\":[\"push_firefox\"]}"
"ibmenpushto": "{\"platforms\":[\"push_safari\"]}"
```

###### Binary mode header
{: #en-binary-mode-header24}

```JSON
ce-ibmenpushto: "{\"user_id\": [\"ajay@accts.acmebank.com\",\"ankit@accts.acmebank.com\"]}"
```
