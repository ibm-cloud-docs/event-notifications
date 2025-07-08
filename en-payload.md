---

copyright:
  years: 2022, 2024
lastupdated: "2024-04-18"

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

This document describes the payload details for sending events notifications by using the API sources in {{site.data.keyword.en_short}}. API sources can be used to send events from your backend applications. You can use this document to send Push notifications from business backends.

Events from API sources cannot be routed to {{site.data.keyword.IBM_notm}} email and {{site.data.keyword.IBM_notm}} SMS destinations.
{: important}

```sh
`METHOD: POST`
`URL: /event-notifications/v1/apps/{instanceID}/notifications`
`Header: Authorization: Bearer <IAM token>`
```

The Events adhere to Cloud Event standard. You can find more information about Cloud Events here.

## Modes of transport
{: #en-modes-of-transport}

{{site.data.keyword.en_short}} supports the following two modes to make HTTP calls. This is adhering to the Cloud Events specification.

### Binary Mode
{: #en-binary-mode}

In the binary content mode, the value of the event `data` is placed into the HTTP request, or response, body as-is. The `datacontenttype` attribute value declares its media type in the HTTP `Content-Type` header. All other event attributes are mapped to HTTP headers.

All the attribute names are prefixed with `ce-` and added to the header (except for the `data` and `datacontenttype`).

Binary Mode is the recommended way to send notifications.
{: note}

### Structured Mode
{: #en-structured-mode}

In the structured content mode, event metadata attributes and event data are placed into the HTTP request body. For structured mode set the `Content-Type` header to `application/cloudevents+json`.

## Attributes
{: #en-attributes}

### CE Mandatory Attributes
{: #en-ce-mandatory-attributes}

The following attributes are mandatory for the event request to be accepted.

#### ID (String)
{: #en-id-string}

A unique identifier that identifies each event. `source+id` must be unique. The backend shall be able to uniquely track this ID in logs and other records. Send a unique ID for each send notification. The same ID can be sent in case of failure of send notification.

`source+id` is logged in {{site.data.keyword.cloud_notm}} Logging service. Using these combination {{site.data.keyword.IBM_notm}} customers are able to trace the event movement from one system to another and aids in debugging and tracing.

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

This is the identifier of the event producer. A way to uniquely identify the source of the event. For {{site.data.keyword.cloud_notm}} services this is the crn of the service instance that produces the events. For API sources this can be something the event producer backend can uniquely identify itself with.

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

It is the version of the Cloud Events specification that {{site.data.keyword.en_short}} currently supports. This value must be set to "1.0".

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

The event type name must be prefixed with the reverse DNS names so the event type is uniquely identified. The same event type can be produced by two different sources. It is highly recommended to use hyphen `-` as a separator instead of `_`.

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

The following attributes are optional but highly recommended to take full advantage of {{site.data.keyword.en_short}}.

#### time (timestamp)
{: #en-time-timestamp}

UTC timestamp when the event occurred. Must be in the RFC 3339 format.

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

Defines the MIME type of the data content. Currently, only "application/json" is supported.

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

The payload of the event. This can contain information that can be passed along to destinations like webhooks. Make sure that you are not sending any sensitive information. This must be a valid JSON object.

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

This is the ID of the source that is created in {{site.data.keyword.en_short}}. This is available in the {{site.data.keyword.en_short}} UI in the "Sources" section.

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

This message is used in case the event that is routed to a destination that needs a human readable text, but a destination-specific attribute is not specified.

For example, if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultshort` is used as the notification title (android_title).

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

This message is used in case the event that is routed to a destination that needs a human readable text, but a destination-specific attribute is not specified.

For example, if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultlong` is used as the notification body (alert).

##### Example
{: #en-example12}

```JSON
ibmendefaultlong: "Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password."
```

##### Binary mode header
{: #en-binary-mode-header11}

```JSON
ce-ibmendefaultlong: "Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password."
```

#### ibmenfcmbody(string/json)
{: #en-ibmenfcmbody-string-json}

This attribute is needed if you want to send a push notification to an Android device. This is the body that you want to send to FCM (Firebase Cloud Messaging) server, this must be JSON in string format. For more information regarding the FCM body, see [REST Resource: projects.messages](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages){: external}.

For compatibility with an earlier version for existing Push notification customers, the previous unified data format is still supported but is deprecated.

##### Example: Sample notification payload:
{: #en-example13}

```JSON
"ibmenfcmbody": "{\"message\":{\"android\":{\"ttl\":\"86400s\",\"notification\":{\"click_action\":\"OPEN_ACTIVITY_1\"},\"data\":{\"id\":\"test_id\"}}}}"
```

##### Binary mode header
{: #en-binary-mode-header12}

```JSON
ce-ibmenfcmbody: {"message":{"android":{"ttl":"86400s","notification":{"click_action":"OPEN_ACTIVITY_1"},"data":{"id":"test_id"}}}}
```

#### ibmenapnsbody(string/json)
{: #en-ibmenapnsbody-string-json}

This attribute is needed if you want to send a push notification to an iOS device. This is the body that you want to send to the APNs (Apple Push Notification Service) server, this must be JSON in string format. For more information regarding APNs body, see [Creating the Remote Notification Payload](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html){: external}.

For compatibility with an earlier version for existing Push notification customers, the previous unified data format is still supported but is deprecated.

##### Sample notification payload:
{: #en-example14}

```JSON
"ibmenapnsbody": {"aps":{"alert":{"title":"Game Request","subtitle":"Five Card Draw","body":"Bob wants to play poker"},"category":"GAME_INVITATION"},"gameID":"12345678"}
```

To customize your APNs push notifications, you can provide APNs headers. Some of them are mandatory to deliver a notification if key is present. The required body as follows:

```JSON
"ibmenapnsheaders": "{\"apns-priority\":10, \"apns-collapse-id\": \"collapse\"}"
```

To get more details on APNs headers, see [Generating a remote notification](https://developer.apple.com/documentation/usernotifications/generating-a-remote-notification){: external}.

##### Binary mode header
{: #en-binary-mode-header13}

```JSON
ce-ibmenapnsbody: {"en_data":{"alert":"alert","url":"https","badge":9,"sound":"bingbong.aiff","payload":{"myaarray":["cc75e4a6-edd8-3bec-a7c3-dfca6572a03b"]},"type":"DEFAULT","subtitle":"dummy","title":"dummy1","body":"body","ios_action_key":"key","interactive_category":"interactiveCategory","title_loc_key":"titleLocKey","loc_key":"GAME_PLAY_REQUEST_FORMAT","launch_image":"image.png","title_loc_args":["Shelly","Rick"],"loc_args":["Shelly","Rick"],"attachment_url":"some url","apns_collapse_id":"12","apns_thread_id":"1","apns_group_summary_arg":"apnsGroupSummaryArg","apns_group_summary_arg_count":1}}
```


#### ibmenchromebody(string/json)
{: #en-ibmenchromebody-string-json}

This attribute is needed if you want to send a push notification to a chrome device. This is the body that you want to send to the FCM server, this must be JSON in string format. For more information regarding chrome body, see [Notification](https://developer.mozilla.org/en-US/docs/Web/API/Notification){: external}.

You can follow these examples for quick start:

```JSON
"ibmenchromebody": "{\"title\":\"Hello Chrome\", \"options\": {}}"
```
To customize your chrome push notifications, you can provide chrome headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenchromeheaders":"{\"TTL\":100}"
```

##### Binary mode header
{: #en-binary-mode-header14}

```JSON
ce-ibmenchromebody: {"title":"Hello Chrome", "options": {}}
```

```JSON
ce-ibmenchromeheaders: "{"TTL":100}"
```

#### ibmenfirefoxbody(string/json)
{: #en-ibmenfirefoxbody-string-json}

This attribute is needed if you want to send a push notification to a Firefox device. This is the body that you want to send to the Firefox Push server, this must be JSON in string format. For more information regarding the Firefox body, see [Notification](https://developer.mozilla.org/en-US/docs/Web/API/Notification).

You can follow these examples for quick start:

```JSON
"ibmenfirefoxbody": "{\"title\":\"Hello Firefox\", \"options\": {}}"
```

To customize your chrome push notifications, you can provide Firefox headers. Some of them are mandatory to deliver a notification if key is present. The example body as follows:

```JSON
"ibmenfirefoxheaders": "{\"TTL\":100, \"Urgency\": \"low\" , \"Topic\": \"Test Firefox Notifications\"}",
```

##### Binary mode header
{: #en-binary-mode-header16}

```JSON
ce-ibmenfirefoxbody: {"title":"Hello Firefox", "options": {}}
```

```JSON
ce-ibmenfirefoxheaders: {"TTL":100, "Urgency": "low" , "Topic": "Test Firefox Notifications"}
```

#### ibmensafaribody(string/json)
{: #en-ibmensafaribody-string-json1}

This attribute is needed if you want to send a push notification to a Safari device. This is the body that you want to send to Apple Push Notification Server, this must be JSON in string format. For more information regarding the Safari body, see [Configuring Safari Push Notifications](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/NotificationProgrammingGuideForWebsites/PushNotifications/PushNotifications.html#//apple_ref/doc/uid/TP40013225-CH3-SW1){: external}.

You can follow these examples for quick start:

```JSON
"ibmensafaribody": "{\"aps\":{\"alert\":{\"title\":\"Shipment Order 1832128321 Delevered\",\"body\":\"Shipment Order 1832128321 Delevered.\",\"action\":\"View\"},\"url-args\":[\"1832128321\"]}}"
```

##### Binary mode header
{: #en-binary-mode-header23}

```JSON
ce-ibmensafaribody: {"aps":{"alert":{"title":"Shipment Order 1832128321 Delevered","body":"Shipment Order 1832128321 Delevered.","action":"View"},"url-args":["1832128321"]}}
```

#### ibmenhuaweibody(string/json)
{: #en-ibmenhuaweibody-string-json}

This attribute is needed if you want to send a push notification to a Huawei device. This is the body that you want to send to the Huawei Push Kit server, this must be JSON in string format. For more information regarding the Huawei body, see, [Huawei Push Notification payload](https://developer.huawei.com/consumer/en/doc/HMSCore-References/https-send-api-0000001050986197#EN-US_TOPIC_0000001562768322__p1324218481619).

You can follow these example for quick start:

```JSON
"ibmenhuaweibody":"{\"message\":{\"android\":{\"notification\":{\"title\":\"New Message\",\"body\":\"Hello World\",\"click_action\":{\"type\":3}}}}}"
```

##### Binary mode header
{: #en-binary-mode-header24}

```JSON
ce-ibmenhuaweibody: {"aps":{"alert":{"title":"Shipment Order 1832128321 Delevered","body":"Shipment Order 1832128321 Delevered.","action":"View"},"url-args":["1832128321"]}}
```

#### ibmenpushto(string/json)
{: #en-ibmenpushto-string-json}

This attribute is mandatory for successful delivery to an Android, FCM, APNS or Huawei destination.

This contains details about the destination where you want to send a push notification. This field is also the string format of JSON and further contains the following field

- `user_id` – Userid to be associated with the device. where you want to target your notification
- `tag` – This is used to send notifications on registered tags
- `platform` - You can target all registered device by platforms.

Following are the corresponding platform values for each type of target.

- `FCM`: push_android
- `APNS`: push_ios
- `Chrome`: push_chrome
- `Firefox`: push_firefox
- `Safari`: push_safari
- `Huawei` : push_huawei
- `fcm_devices` – Unique identifier of the FCM device where you want to target your notification
- `apns_devices` - Unique identifier of the APNS device where you want to target your notification
- `chrome_devices` - Unique identifier of the Chrome Web device where you want to target your notification
- `firefox_devices` - Unique identifier of the Firefox Web device where you want to target your notification
- `safari_devices` - Unique identifier of the Safari Web device where you want to target your notification
- `huawei_devices` - Unique identifier of the Huawei Web device where you want to target your notification

##### Example
{: #en-example16}

```JSON
"ibmenpushto": "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"]}"`
"ibmenpushto": "{\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"
"ibmenpushto": "{\"chrome_devices\": [\"2c75972a-37d0-3898-905d-3b5ee0d7c182\",\"N9CACDF5-1EBF-49E1-AD60-E25BA23E994D\"]}"
"ibmenpushto": "{\"firefox_devices\": [\"3c75972a-37d0-3898-905d-3b5ee0d7c182\",\"L9CACDF5-1EBF-49E1-AD60-E25BA23E994E\"]}"
"ibmenpushto": "{\"safari_devices\": [\"1175972a-37d0-3898-905d-3b5ee0d7c1D2\",\"Q9CACDF5-1EBF-49E1-AD60-E25BA23E994N\"]}"
"ibmenpushto": "{\"huawei_devices\": [\"1175972a-37d0-3898-905d-3b5ee0d7c1D2\",\"Q9CACDF5-1EBF-49E1-AD60-E25BA23E994N\"]}"
```

Multiple destinations can be targeted by using following methods

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

Targeting notifications to a specific platform.

```JSON
"ibmenpushto": "{\"platforms\":[\"push_android\"]}"
"ibmenpushto": "{\"platforms\":[\"push_ios\"]}"
"ibmenpushto": "{\"platforms\":[\"push_chrome\"]}"
"ibmenpushto": "{\"platforms\":[\"push_firefox\"]}"
"ibmenpushto": "{\"platforms\":[\"push_safari\"]}"
"ibmenpushto": "{\"platforms\":[\"push_huawei\"]}"
```

##### Binary mode header
{: #en-binary-mode-header25}

```JSON
ce-ibmenpushto: "{\"user_id\": [\"ajay@accts.acmebank.com\",\"ankit@accts.acmebank.com\"]}"
```
