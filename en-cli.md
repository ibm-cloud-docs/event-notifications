---

copyright:
  years: 2021, 2022
lastupdated: "2022-02-28"

subcollection: event-notifications-cli-plugin
keywords: event notifications CLI, event notifications command line, event notifications terminal, event notifications shell, Event Notifications, en

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# {{site.data.keyword.en_short}} CLI plug-in for Event Notifications service
{: #CLI_Event_Notifications}

Use the {{site.data.keyword.Bluemix_notm}} command-line interface (CLI) to interact  {{site.data.keyword.en_short}} IBM Cloud service

## Prerequisites
To use the {{site.data.keyword.Bluemix_notm}} CLI, download and install the following packages on your local system.


- The [{{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cloud-cli-install-ibmcloud-cli)

## Install the {{site.data.keyword.en_short}} CLI

Install the plug-in by using the `plugin install` command.

```sh
ibmcloud plugin install en
```
{: pre}

### ibmcloud event-notifications init
{: #event-notifications-cli-init-command}

Set instance you'll we working on.

```sh
ibmcloud event-notifications init [--instance-id INSTANCE-ID]
```
{: pre}

#### Command options
{: #event-notifications-init-cli-options}

--instance-id (string)
:   Unique identifier for IBM Cloud Event Notifications instance.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.


### ibmcloud event-notifications show
{: #event-notifications-cli-show-command}

Check your configuration.

```sh
ibmcloud event-notifications show
```
{: pre}


#### Command options
{: #event-notifications-show-cli-options}

## Destination
{: #event-notifications-destination-cli}

Operate on IBM Cloud Event Notifications Destination.

```sh
ibmcloud event-notifications destination --help
```
{: pre}

### ibmcloud event-notifications destination create
* **Action:** Create a new Destination

```sh 
ibmcloud event-notifications destination create --name NAME --type TYPE [--description DESCRIPTION] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--config CONFIG] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
* The name of the Destination.
   * Flag: `--name NAME`
* The type of the Destination The options available are webhook, push_android, push_ios.
   * Flag: `--type TYPE`
* The Description of the destination .
   * Flag: `--description DESCRIPTION`   
* The Certificate file path to be provided.
   * Flag: `--certificate CERTIFICATE`     
* The Certificate Content type to be set in case of IOS destination. The available options are p8/p12
   * Flag: `--certificate-content-type CERTIFICATE-CONTENT-TYPE`    
* The Configuration needed to set the destination specific parameters.
   * Flag: `--config CONFIG` 
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `--instance-id `      

    The `--config` flag json structure for Webhook Destination.
    ```json
    {
     "params" : {
     "url" : "exampleString",
     "verb" : "get",
     "custom_headers" : { },
     "sensitive_headers" : [ "exampleString" ]
     }
    }
    ```    
    The following example shows the format of the DestinationConfig object for IOS destination with P8 certificate.

    ```json
    {
    "params" : {
      "cert_type" : "p8",
      "is_sandbox" : true,
      "key_id": "production",
      "team_id": "1234",
      "bundle_id":"test1"
    }
   }
    ```  

   The following example shows the format of the DestinationConfig object for IOS destination with P8 certificate.

   ``` json
   {
    "params" : {
    "cert_type" : "p12",
    "is_sandbox" : true,
    "password": "apnspasswordvalue"
   }
  }
  ```
### ibmcloud event-notifications destination list
{: #event-notifications-cli-destination-list-command}

List all `Destination`.

```sh 
ibmcloud event-notifications destination list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
* The Page limit for paginated results.
   * Flag: `--limit LIMIT`
* The offset for paginated results.
   * Flag: `--offset OFFSET`
* The Search string for filtering results.
   * Flag: `--search SEARCH`   
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `--instance-id ` 


### ibmcloud event-notifications destination get
{: #event-notifications-cli-destination-get-command}

Get specific `Destination`.


* **Usage:** `ibmcloud event-notifications destination get --id ID [--instance-id INSTANCE-ID]`


* **Parameters to provide:**
* The Unique identifier for Destination. Required.
   * Flag: `--id ID`
* The offset for paginated results.
   * Flag: `[--instance-id INSTANCE-ID]`


### ibmcloud event-notifications destination update
{: #event-notifications-cli-destination-update-command}

Update existing `Destination`.

```sh 
ibmcloud event-notifications destination update --id ID [--name NAME] [--description DESCRIPTION] [--certificate CERTIFICATE] [--config CONFIG] [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Destination. Required.
   * Flag: `--id`
* The  Destination name to be updated.
   * Flag: `--name NAME`
* The Description of the destination .
   * Flag: `--description DESCRIPTION`  
* The Certificate file path to be provided.
   * Flag: `--certificate CERTIFICATE`    
* The Configuration needed to set the destination specific parameters.
   * Flag: `--config CONFIG` 
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `--instance-id `   


### ibmcloud event-notifications destination delete
{: #event-notifications-cli-destination-delete-command}

Delete existing `Destination`.

```sh 
ibmcloud event-notifications destination delete --id ID [--instance-id INSTANCE-ID] [--force]
```
{: pre}

* **Parameters to provide:**
* The Unique identifier for Destination. Required.
   * Flag: `--id ID`
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* Activate to force resource deletion (to bypass the confirmation prompt).
   * Flag: `[--force]`   



### ibmcloud event-notifications source list
{: #event-notifications-cli-source-list-command}

List all `Source`.

```sh 
ibmcloud event-notifications source list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
* The Page limit for paginated results.
   * Flag: `--limit LIMIT`
* The offset for paginated results.
   * Flag: `--offset OFFSET`
* The Search string for filtering results.
   * Flag: `--search SEARCH`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* Activate to force resource deletion (to bypass the confirmation prompt).
   * Flag: `[--force]`  


### ibmcloud event-notifications source get
{: #event-notifications-cli-source-get-command}

Get specific `Source`.

```sh
ibmcloud event-notifications source get --id ID [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Source. Required.
   * Flag: `--id ID`
* The offset for paginated results.
   * Flag: `--offset OFFSET`
* The Search string for filtering results.
   * Flag: `--search SEARCH`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* Activate to force resource deletion (to bypass the confirmation prompt).
   * Flag: `[--force]`

## Topic
{: #event-notifications-topic-cli}

Operate on IBM Cloud Event Notifications Topic.

```sh
ibmcloud event-notifications topic --help
```
{: pre}


### ibmcloud event-notifications topic create
{: #event-notifications-cli-topic-create-command}

Create new `Topic`.

```sh
ibmcloud event-notifications topic create --name NAME [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* Name of the topic. Required.
   * Flag: `--name NAME`
* Description of the topic.
   * Flag: `--description DESCRIPTION` 
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* The  List of sources.
   * Flag: `[--sources SOURCES]`   

```json
[ {
  "id" : "exampleString",
  "rules" : [ {
    "enabled" : true,
    "event_type_filter" : "$.*",
    "notification_filter" : "exampleString"
  } ]
} ]
```

### ibmcloud event-notifications topic list
{: #event-notifications-cli-topic-list-command}

List all `Topic`.

```sh
ibmcloud event-notifications topic list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
* The Page limit for paginated results.
   * Flag: `--limit LIMIT`
* The offset for paginated results.
   * Flag: `--offset OFFSET`
* The Search string for filtering results.
   * Flag: `--search SEARCH`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`

### ibmcloud event-notifications topic get
{: #event-notifications-cli-topic-get-command}

Get specific `Topic`.

```sh
ibmcloud event-notifications topic get --id ID [--include INCLUDE] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
* Unique identifier for Topic. Required.
   * Flag: `--id ID`
* Include sub topics..
   * Flag: `--include INCLUDE` 
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`


### ibmcloud event-notifications topic update
{: #event-notifications-cli-topic-update-command}

Update existing `Topic`.

```sh
ibmcloud event-notifications topic update --id ID [--name NAME] [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Topic. Required.
   * Flag: `--id ID`
*  The Name of the topic to update.
   * Flag: `[--name NAME]` 
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* The Description to update for Topic
   * Flag: `[--description --description DESCRIPTION ]`   
* TheList of sources for topic
   * Flag: `[--sources SOURCES]`   


```json
[ {
  "id" : "exampleString",
  "rules" : [ {
    "enabled" : true,
    "event_type_filter" : "exampleString",
    "notification_filter" : "exampleString",
    "rule_id" : "exampleString"
  } ]
} ]
```

### ibmcloud event-notifications topic delete
{: #event-notifications-cli-topic-delete-command}

Delete existing `Topic`.

```sh
ibmcloud event-notifications topic delete --id ID [--instance-id INSTANCE-ID] [--force]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Topic. Required.
   * Flag: `--id ID`
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* Activate to force resource deletion (to bypass the confirmation prompt).
   * Flag: `[--force]`   


## Subscription
{: #event-notifications-subscription-cli}

Operate on IBM Cloud Event Notifications Subscription.

```sh
ibmcloud event-notifications subscription --help
```
{: pre}

### ibmcloud event-notifications subscription create
{: #event-notifications-cli-subscription-create-command}

Create new `Subscription`.

```sh
ibmcloud event-notifications subscription create [--name NAME] [--description DESCRIPTION] [--destination-id DESTINATION-ID] [--topic-id TOPIC-ID] [--attributes ATTRIBUTES] [--instance-id INSTANCE-ID]
```
{: pre}


* **Parameters to provide:**
*  The name to be set for Subscription.
   * Flag: `--name NAME`
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* The description to be set for Subscription.
   * Flag: `[--description DESCRIPTION]`  
* The Destination ID to be set for subscription.
   * Flag: `[--destination-id DESTINATION-ID]`   
* The Topic ID to be set for subscription.
   * Flag: `[--topic-id TOPIC-ID]`  
* The attributes to be set for subscription
   * Flag: `[-attributes ATTRIBUTES]`     

Syntax in case of webhook subscription to be created   

```json
{
  "add_notification_payload" : true,
  "signing_enabled" : true
}
```    
Syntax in case of sms subscription to be created   

```json
{
    "to" :["+19667895490", "+19845678321"]
}
```    
Syntax in case of email subscription to be created   

```json
{
    "to" :["entest@gmail.com"],
    "add_notification_payload": true,
    "reply_to_mail": "en@ibm.com",
    "reply_to_name": "EYS ORG",
    "from_name":"ABC ORG"
    }
```      


### ibmcloud event-notifications subscription list
{: #event-notifications-cli-subscription-list-command}

List all `Subscription`.

```sh
ibmcloud event-notifications subscription list [--offset OFFSET] [--limit LIMIT] [--search SEARCH] [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* The Page limit for paginated results.
   * Flag: `--limit LIMIT`
* The offset for paginated results.
   * Flag: `--offset OFFSET`
* The Search string for filtering results.
   * Flag: `--search SEARCH`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`


### ibmcloud event-notifications subscription get
{: #event-notifications-cli-subscription-get-command}

Get specific `Subscription`.

```sh
ibmcloud event-notifications subscription get --id ID [--instance-id INSTANCE-ID]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Subscription. Required.
   * Flag: `--id ID`
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`


### ibmcloud event-notifications subscription delete
{: #event-notifications-cli-subscription-delete-command}

Delete existing `Subscription`.

```sh
ibmcloud event-notifications subscription delete --id ID [--instance-id INSTANCE-ID] [--force]
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Subscription. Required.
   * Flag: `--id ID`
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* Activate to force resource deletion (to bypass the confirmation prompt).
   * Flag: `[--force]`  


### ibmcloud event-notifications subscription update
{: #event-notifications-cli-subscription-update-command}

Update existing `Subscription`.

```sh
ibmcloud event-notifications subscription update --id ID [--name NAME] [--description DESCRIPTION] [--attributes ATTRIBUTES] [--instance-id INSTANCE-ID] 
```
{: pre}

* **Parameters to provide:**
*  Unique identifier for Subscription. Required.
   * Flag: `--id ID`
* The updated description to be set for Subscription.
   * Flag: `[--name NAME]`   
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
* The updated description to be set for Subscription.
   * Flag: `[--description DESCRIPTION]`  
* The attributes to be set for subscription
   * Flag: `[-attributes ATTRIBUTES]`     

## Send Notifications
### ibmcloud event-notifications Send Notifications
{: #event-notifications-cli-send-notifications-command}


```sh
send-notifications --instance-id INSTANCE-ID --subject SUBJECT --severity SEVERITY --id ID --source SOURCE --en-source-id EN-SOURCE-ID --type TYPE --time TIME [--data DATA] [--push-to PUSH-TO] [--message-fcm-body MESSAGE-FCM-BODY] [--message-apns-headers MESSAGE-APNS-HEADERS] [--message-apns-body MESSAGE-APNS-BODY] [--datacontenttype DATACONTENTTYPE] [--specversion SPECVERSION] 
```
{: pre}

* **Parameters to provide:**
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`
*  The Subject for Notification
   * Flag: `--subject SUBJECT`
* The level of severity for notification. Required.
   * Flag: `[--severity SEVERITY]`   
* The source description.
   * Flag: `[--source SOURCE]`  
* The source ID to be set for Notification source. Required
   * Flag: `[--en-source-id]`
* The type of notification. Required
   * Flag: `[--type TYPE]`  
* The Timestamp to be set for notification. Required
   * Flag: `[--time TIME]` 
* The Timestamp to be set for notification. Required
   * Flag: `[--time TIME]` 
* The datacontent type for notification. Required
   * Flag: `[--datacontenttype DATACONTENTTYPE]`         
* The spec version value.Default value to be used is 1.0
   * Flag: `[--specversion SPECVERSION]`  
* PThe Device data information to send data in case of Registered Devices/ Usersids/ Platforms.
   * Flag: `[--push-to PUSH-TO]`
* FCM message body to send notification to FCM devices.
   * Flag: `[--message-fcm-body MESSAGE-FCM-BODY]` 
* The Custom APNS headers information can be set using this option.
   * Flag: `[--message-apns-headers MESSAGE-APNS-HEADERS]`     
* The apns meaage body can be set using this option.
   * Flag: `[--message-apns-body MESSAGE-APNS-BODY]`            

The following example shows the format of data payload for sending notifications.

```json
{"data": {
            "createTimestamp": 1557282940339,
            "severity": "LOW",
            "shortDescription": "examplestring"
          }
}
```

The following example shows the format of FCM message body to send notification to FCM devices.        

```json
{"message":{
    "data":{
        "alert": "examlestring", "delay_while_idle":true,"time_to_live":2,"collapse_key":"testCollapseKey","notification":{"title":"Match update","body":"Arsenal goal in added time, score is now 3-0"},"data":{"alert":"Notification alert message","url":"https","payload":{"mydevicearra":["cc75e4a6-edd8-3bec-a7c3-dfca6572a03b"]}}
        }
}

```

The following example shows the format of apns headers.   

```json
{
    "test": "test header",
    "new": "newmesaage"
}
```
The following example shows the format of APNS message body to send notification to FCM devices.        

```json
{"data":{"alert":"alert","url":"https","badge":9,"sound":"bingbong.aiff","payload":"{\\\"fcm_devices\\\": [\\\"cc75e4a6-edd8-3bec-a7c3-dfca6572a03b\\\"]}","type":"DEFAULT","subtitle":"dummy","title":"dummy1","body":"body","ios_action_key":"key","interactive_category":"interactiveCategory","title_loc_key":"titleLocKey","loc_key":"GAME_PLAY_REQUEST_FORMAT","launch_image":"image.png","title_loc_args":["Shelly","Rick"],"loc_args":["Shelly","Rick"],"attachment_url":"some url","apns_collapse_id":"12","apns_thread_id":"1","apns_group_summary_arg":"apnsGroupSummaryArg","apns_group_summary_arg_count":1}}
```

The following example shows the target device configuration example.

```json
{"fcm_devices": ["deviceidstring"],"user_ids": ["useridstring"], "platform": ["G"]}
```

<dd>Additional properties that can be configured for the IOS notification.
<p>
<table>
  <caption>Table 1. Settings specific to iOS platform.</caption>
  <tr>
    <th>Property</th>
    <th>Property type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>badge</td>
    <td>integer</td>
    <td>The number to display as the badge of the application icon.</td>
  </tr>
  <tr>
    <td>interactive_category</td>
    <td>string</td>
    <td>The category identifier to be used for the interactive push notifications.</td>
  </tr>
  <tr>
    <td>ios_action_key</td>
    <td>string</td>
    <td>The title for the Action key.</td>
  </tr>
  <tr>
    <td>payload</td>
    <td>JSON object</td>
    <td>Custom JSON payload that will be sent as part of the notification message.</td>
  </tr>
  <tr>
    <td>sound</td>
    <td>string</td>
    <td>The name of the sound file in the application bundle. The sound of this file is played as an alert.</td>
  </tr>
  <tr>
    <td>title_loc_key</td>
    <td>string</td>
    <td>The key to a title string in the Localizable.strings file for the current localization. The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the titleLocArgs array.</td>
  </tr>
  <tr>
    <td>loc_key</td>
    <td>string</td>
    <td>A key to an alert-message string in a Localizabl.strings file for the current localization (which is set by the user's language preference). The key string can be formatted with %@ and %n$@ specifiers to  take the variables specified in the locArgs array.</td>
  </tr>
  <tr>
    <td>launch_image</td>
    <td>string</td>
    <td>The filename of an image file in the app bundle, with or without the filename extension. The image is used as the launch image when users tap the action button or move the action slider.</td>
  </tr>
  <tr>
    <td>title_loc_args</td>
    <td>string[]</td>
    <td>Variable string values to appear in place of the format specifiers in title-loc-key.</td>
  </tr>
  <tr>
    <td>loc_args</td>
    <td>string[]</td>
    <td>Variable string values to appear in place of the format specifiers in locKey.</td>
  </tr>
  <tr>
    <td>title</td>
    <td>string</td>
    <td>The title of Rich Push notifications (Supported only on iOS 10 and above).</td>
  </tr>
  <tr>
    <td>subtitle</td>
    <td>string</td>
    <td>The subtitle of the Rich Notifications (Supported only on iOS 10 and above).</td>
  </tr>
  <tr>
    <td>body</td>
    <td>string</td>
    <td>The body for IOS notifications.</td>
  </tr>
  <tr>
    <td>attachment_url</td>
    <td>string</td>
    <td>The link to the iOS notifications media (video, audio, GIF, images - Supported only on iOS 10 and above).</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Allowable values: DEFAULT, MIXED, SILENT.</td>
  </tr>
  <tr>
    <td>apns_collapse_id</td>
    <td>string</td>
    <td>Multiple notifications with the same collapse identifier are displayed to the user as a single notification.</td>
  </tr>
  <tr>
    <td>apns_thread_id</td>
    <td>string</td>
    <td>An app-specific identifier for grouping related notifications. This value corresponds to the threadIdentifier property in the UNNotificationContent object.</td>
  </tr>
  <tr>
    <td><nobr>apns_group_summary_arg</nobr></td>
    <td>string</td>
    <td>The string the notification adds to the category’s summary format string.</td>
  </tr>
  <tr>
    <td><nobr>apns_group_summary_arg_count</nobr></td>
    <td>integer</td>
    <td>The number of items the notification adds to the category’s summary format string.</td>
  </tr>
</table>
</p>

<dd>Additional properties that can be configured for the FCM notification.
<p>
<table>
  <caption>Table 2. Settings specific to Android platform.</caption>
  <tr>
    <th>Property</th>
    <th>Property type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>icon</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>Specify the name of the icon to be displayed for the notification. Make sure that the icon is already packaged with the client application.</td>
  </tr>
  <tr>
    <td>delay_while_idle</td>
    <td>&nbsp;</td>
    <td>boolean</td>
    <td>When this parameter is set to true, it indicates that the message should not be sent until the device becomes active.</td>
  </tr>
  <tr>
    <td>sync</td>
    <td>&nbsp;</td>
    <td>boolean</td>
    <td>Device group messaging makes it possible for every app instance in a group to reflect the latest messaging state.</td>
  </tr>
  <tr>
    <td>visibility</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>private/public - Visibility of this notification, which affects how and when the notifications are revealed on a secure locked screen.</td>
  </tr>
  <tr>
    <td>redact</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>Content that is specified will show up on a secure locked screen on the device when visibility is set to Private.</td>
  </tr>
  <tr>
    <td>payload</td>
    <td>&nbsp;</td>
    <td>JSON object</td>
    <td>Custom JSON payload that will be sent as part of the notification message.</td>
  </tr>
  <tr>
    <td>priority</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>A string value that indicates the priority of this notification. Allowed values are 'max', 'high', 'default', 'low' and 'min'. High/Max priority notifications along with 'sound' field might be used for Heads up notification in Android 5.0 or higher.sampleval='low'.</td>
  </tr>
  <tr>
    <td>sound</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>The sound file (on device) that will be attempted to play when the notification arrives on the device.</td>
  </tr>
  <tr>
    <td>time_to_live</td>
    <td>&nbsp;</td>
    <td>integer</td>
    <td>This parameter specifies how long (in seconds) the message should be kept in GCM storage if the device is offline.</td>
  </tr>
  <tr>
    <td>lights</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>Allows setting the notification LED color on receiving push notification.</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>ledArgb</td>
    <td>string</td>
    <td>The color of the led. The hardware will do its best approximation.</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>ledOnMs</td>
    <td>integer</td>
    <td>The number of milliseconds for the LED to be on while it's flashing. The hardware will do its best approximation.</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>ledOffMs</td>
    <td>string</td>
    <td>The number of milliseconds for the LED to be off while it's flashing. The hardware will do its best approximation.</td>
  </tr>
  <tr>
    <td>android_title</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>The title of Rich Push notifications.</td>
  </tr>
  <tr>
    <td>group_id</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>Set this notification to be part of a group of notifications sharing the same key. Grouped notifications might display in a cluster or stack on devices that support such rendering.</td>
  </tr>
  <tr>
    <td>style</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>Options to specify for Android expandable notifications. The types of expandable notifications are picture_notification, bigtext_notification, inbox_notification.</td>
  </tr>
  <tr>
    <td>type</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>Specifies the type of expandable notifications. The possible values are bigtext_notification, picture_notification, inbox_notification.</td>
  </tr>
  <tr>
    <td>title</td>
     <td>&nbsp;</td>
    <td>string</td>
    <td>Specifies the title of the notification. The title is displayed when the notification is expanded. Title must be specified for all three expandable notifications.</td>
  </tr>
  <tr>
    <td>type</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>Allowable values: DEFAULT, SILENT.</td>
  </tr>
   <tr>    
    <td>alert</td>
    <td>&nbsp;</td>
    <td>string</td>
    <td>The alert Vlaue of Notification</td>
  </tr>
</table>
</p>
