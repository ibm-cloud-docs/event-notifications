---

copyright:
  years: 2022
lastupdated: "2022-05-10"

keywords: event-notifications, event notifications migration, notifications, destinations, specification

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_full}} payload
{: #en-spec-payload}

This document outlies the {{site.data.keyword.en_short}} notification specification
{: shortdesc}

## Introduction
{: #en-spec-payloadintro}

This document describes the payload details for sending events using the API sources in EN. API sources can be used to send events from your backend applications. 
You can use this to send Push notifications from business backends.

Events from API sources cannot be routed to IBM Email and IBM SMS destinations. 
{: note}

`METHOD: POST`
`URL: /event-notifications/v1/apps/{instanceID}/notifications`
`Header: Authorization: Bearer <IAM token>`

The Events adhere to Cloud Event standard. You can find more information about Cloud Events here. 

## Modes of transport 
{{site.data.keyword.en_short}} supports two modes to make HTTP calls. This is adhering to the CoudEvents specification. More details here.

Event Notifications supports the following two modes from the CloudEvents specification:

### Binary Mode

In the binarycontent mode, the value of the event `data` is placed into the HTTP request, or response, body as-is, with the `datacontenttype` attribute 
value declaring its media type in the HTTP `Content-Typeheader`; all other event attributes are mapped to HTTP headers.

All the attribute names are prefixed with `ce-` and added to the header (except for the `data` and `datacontenttype` )

Binary Mode is recommended way to send notifications
{: note}

### Structured Mode
In the structuredcontent mode, event metadata attributes and event data are placed into the HTTP request body. 
For structured mode set the `Content-Typeheader` to `application/cloudevents+json`

## Attributes

### CE Mandatory Attributes

The following attributes are mandatory for the event request to be accepted.

### id (String)

A unique identifier that identifies each event. `source+id` must be unique.
The backend should be able to uniquely track this id in logs and other records. Send unique ID for each send notification. Same ID can be sent in 
case of failure of send notification. 
`source+id` will be logged in IBM Cloud Logging service. Using this combination IBM customers will be able to trace the event movement from one system to 
another and will aid in debugging and tracing.

e.g: 
`id: qwer-1234-1qsd-po94`
Binary mode header
`ce-id: qwer-1234-1qsd-po94`

### source (URI-reference)

This is the identifier of the event producer. A way to uniquely identify the source of the event. For IBM Cloud services this is the crn 
of the service instance producing the events.  For API sources this can be something the event producer backend can uniquely identify itself with.

e.g.: 
`source: com.mybank.customerbanking.accountmanagement`
Binary mode header
`ce-source: com.mybank.customerbanking.accountmanagement`

### specversion (string) 

This is the version of CloudEvents specification that {{site.data.keyword.en_short}} currently supports. This value must be set to “1.0”
e.g.: 
`specversion:1.0`
Binary mode header
`ce-specversion:1.0`

### type (string) 

This describes the type of event.  It is of the form `<event-type-name>:<sub-type>` This type is defined by the producer.  
The event type name has to be prefixed with the reverse DNS names so the event type is uniquely identified. The same event type can be produced 
by 2 different sources. It is highly recommended to use hyphen `-` as a separator instead of `_`

e.g. 1:
`type:com.acmebank.password:expiring-in-15-days`
Type: `com.acmebank.password`
Sub type: `expiring-in-15-days`

Binary mode header
`ce-type:com.acmebank.password:expiring-in-15-days`

e.g. 2:
`type:com.acmebank.password-changed`
Type: `com.acmebank.password-changed`
Sub type: N/A

Binary mode header
`ce-type:com.acmebank.password-changed`

## CE optional attributes

Following attributes are optional but highly recommended to take full advantage of {{site.data.keyword.en_short}}

### time (timestamp) 

UTC time stamp when the event occurred. Must be in the RFC 3339 format.

E.g.:
`time: 2022-02-10T10:51:37+00:00`

Binary mode header
`ce-time: 2022-02-10T10:51:37+00:00`

### subject (String) 

This is the subject of the event in the event producer (source). So, this can be the account ID of the password that’s about to expire 

e.g:
`subject:ajay@accts.acmebank.com`

Binary mode header
`ce-subject:ajay@accts.acmebank.com`

### datacontenttype

Defines the MIME type of the data content. Currently only “application/json” is supported.

e.g:
`datacontenttype: application/json`

Binary mode header 
`Content-Type:application/json`

### data

The payload of the event.  This can contain information that can be passed along to destinations like webhooks. Make sure that you are not sending any 
sensitive information. This has to be a valid JSON object

e.g:
`data: { “lastchanged-days”: “74”, “reason”:”time-based”}`

Binary mode – this is part of the HTTP body N/A

## {{site.data.keyword.en_short}} extension mandatory attributes

These are mandatory attributes for every event sent to EN

### ibmensourceid (string): 
This is the ID of the source created in EN. This is available in the EN UI in the “Sources” section

e.g: 
`ibmensourceid: 121313123:api`
Binary mode header
`ce-ibmensourceid: 121313123:api`

## {{site.data.keyword.en_short}} extension optional attributes

These are optional attributes

### ibmenseverity(String) 

Some sources can have the concept of an Event severity. Hence a handy way is provided to specify a severity of the event. 
e.g:
`ibmenseverity:LOW`
Binary mode header
`ce-ibmenseverity:LOW`

### ibmendefaultshort(String) 
This message will be used in case the event is routed to a destination that needs a human readable text, but a destination specific attribute is not specified.
e.g.: if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultshort` will be used as the notification title 
(android_title).

e.g.:
`ibmendefaultshort: “Change password”`
Binary mode header
`ce-ibmendefaultshort: “Change password”`

### ibmendefaultlong(String) 

This message will be used in case the eventis routed to a destination that needs a human readable text, but a destination specific attribute is not specified. 
E.g.: if `ibmenfcmbody` is not specified and the event is routed to Android FCM type destination, `ibmendefaultlong` will be used as the notification body (alert).

e.g.:
`ibmendefaultlong: “Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password.”`
Binary mode header
`ce-ibmendefaultlong: “Password will expire in 10 Days. Pleaselog in to the Bank home page and click on Change Password link to change your password.”`

### ibmenfcmbody(string/json)

This attribute is needed if you want to send push notification to an Android device. This is the body that you want to send to FCM server, this has to be 
JSON in string format. For more info regarding FCM body please follow this documentation - https://firebase.google.com/docs/cloud-messaging/concept-options.
For backward compatibility for existing Push notification customers, the previous unified data format is still supported but is deprecated. 

e.g.: Deprecated Push Notification service compatible format:
`“ibmenfcmbody": "{\"en_data\":{\"alert\":\" Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password. \", \"android_title\":\"Change Password\"}}"`
Binary mode header
`ce-ibmenfcmbody: "{\"en_data\":{\"alert\":\" Password will expire in 10 Days. Please log in to the Bank home page and click on Change Password link to change your password. \", \"android_title\":\"Change Password\"}}"`

### ibmenapnsbody(string/json)

This attribute is needed if you want to send push notification to an IOS device. This is the body that you want to send to APNs server, this has to be JSON 
in string format. For more info regarding APNs body please follow this documentation - https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html

For backward compatibility for existing Push notification customers, the previous unified data format is still supported but is deprecated. 

e.g.: Deprecated Push Notification service compatible format:
`“ibmenapnsbody": "{\"en_data\":{\"alert\":\"alert\",\"url\":\"https\",\"badge\":9,\"sound\":\"bingbong.aiff\",\"payload\":{\"myaarray\":[\"cc75e4a6-edd8-3bec-a7c3-dfca6572a03b\"]},\"type\":\"DEFAULT\",\"subtitle\":\"dummy\",\"title\":\"dummy1\",\"body\":\"body\",\"ios_action_key\":\"key\",\"interactive_category\":\"interactiveCategory\",\"title_loc_key\":\"titleLocKey\",\"loc_key\":\"GAME_PLAY_REQUEST_FORMAT\",\"launch_image\":\"image.png\",\"title_loc_args\":[\"Shelly\",\"Rick\"],\"loc_args\":[\"Shelly\",\"Rick\"],\"attachment_url\":\"some url\",\"apns_collapse_id\":\"12\",\"apns_thread_id\":\"1\",\"apns_group_summary_arg\":\"apnsGroupSummaryArg\",\"apns_group_summary_arg_count\":1}}"`
Binary mode header
`ce-ibmenapnsbody: "{\"en_data\":{\"alert\":\"alert\",\"url\":\"https\",\"badge\":9,\"sound\":\"bingbong.aiff\",\"payload\":{\"myaarray\":[\"cc75e4a6-edd8-3bec-a7c3-dfca6572a03b\"]},\"type\":\"DEFAULT\",\"subtitle\":\"dummy\",\"title\":\"dummy1\",\"body\":\"body\",\"ios_action_key\":\"key\",\"interactive_category\":\"interactiveCategory\",\"title_loc_key\":\"titleLocKey\",\"loc_key\":\"GAME_PLAY_REQUEST_FORMAT\",\"launch_image\":\"image.png\",\"title_loc_args\":[\"Shelly\",\"Rick\"],\"loc_args\":[\"Shelly\",\"Rick\"],\"attachment_url\":\"some url\",\"apns_collapse_id\":\"12\",\"apns_thread_id\":\"1\",\"apns_group_summary_arg\":\"apnsGroupSummaryArg\",\"apns_group_summary_arg_count\":1}}"`

### ibmenpushto(string/json)

This attribute is mandatory for successful delivery from an Android FCM or APNS destination

This contains details about the destination where you want to send push notification. This field is also string format of JSON and further contains following field 
- `user_id` – Useridto be associated with the device. where you want to target your notification 
- `tag` – This is used to send notifications on registered tags
- `platform` - For FCM we can target all registered device by giving platform as “G”
- `fcm_devices` – Unique identifier of the FCM device where you want to target your notification
- `apns_devices` - Unique identifier of the APNS device where you want to target your notification

e.g.:
`ibmenpushto: "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"]}"`
`ibmenpushto: "{\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"`

Multiple destination can be targeted using following methods 

`ibmenpushto: "{\"fcm_devices\": [\"9c75975a-37d0-3898-905d-3b5ee0d7c172\",\"C9CACDF5-6EBF-49E1-AD60-E25BA23E954C\"],\"apns_devices\": [\"1c75972a-37d0-3898-905d-3b5ee0d7c172\",\"M9CACDF5-1EBF-49E1-AD60-E25BA23E954C\"]}"`

`ibmenpushto: "{\"user_id\": [\" ajay@accts.acmebank.com \",\" ankit@accts.acmebank.com \"]}"Binary mode headerce-ibmenpushto: "{\"user_id\": [\"ajay@accts.acmebank.com\",\"ankit@accts.acmebank.com\"]}"`


