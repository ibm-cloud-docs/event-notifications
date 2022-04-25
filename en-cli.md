---

copyright:
  years: 2021, 2022
lastupdated: "2022-04-22"

subcollection: event-notifications-cli-plugin
keywords: event notifications CLI, event notifications command line, event notifications terminal, event notifications shell, Event Notifications, en

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_short}} CLI plug-in for Event Notifications service
{: #CLI_Event_Notifications}

Use the {{site.data.keyword.Bluemix_notm}} command-line interface (CLI) to interact  {{site.data.keyword.en_short}} IBM Cloud service

## Prerequisites
{: #CLI_Event_Notifications_prereq}

To use the {{site.data.keyword.Bluemix_notm}} CLI, download and install the following packages on your local system.


- The [{{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cloud-cli-install-ibmcloud-cli)

## Install the {{site.data.keyword.en_short}} CLI
{: #CLI_Event_Notifications_inst}

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

### ibmcloud event-notifications environment variables set
{: #CLI_Event_Notifications_envvar}

export **IBMCLOUD_EN_ENDPOINT** variable to set the EN region endpoint

**Dallas:** https://us-south.event-notifications.cloud.ibm.com/event-notifications
**London:** https://eu-gb.event-notifications.cloud.ibm.com/event-notifications
**Sydney:** https://au-syd.event-notifications.cloud.ibm.com/event-notifications
**Frankfurt:** https://eu-de.event-notifications.cloud.ibm.com/event-notifications

export **EVENT_NOTIFICATIONS_API_KEY** variable to set the Event Notifications instance apikey.

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
{: #CLI_Event_Notifications_createdest}

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
   * Flag: `--instance-id`
   
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

```json
   {
    "params" : {
    "cert_type" : "p12",
    "is_sandbox" : true,
    "password": "apnspasswordvalue"
   }
  }
  ```

  The following example shows the format of the DestinationConfig object for Chrome destination.

   ``` json
   {
    "api_key": "chromeapikey",
    "website_url" : "https://testwebsite.com",
    
   }
  }
  ```

  The following example shows the format of the DestinationConfig object for Firefox destination.

   ``` json
   {
    "website_url" : "https://testwebsite.com",
    
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
   * Flag: `--instance-id` 


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
   * Flag: `--instance-id`   


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

### ibmcloud event-notifications source create
{: #event-notifications-cli-source-create-command}

Create `Source`.

```sh 
ibmcloud event-notifications source create --instance-id INSTANCE-ID --name NAME --description DESCRIPTION [--enabled ENABLED]
```
{: pre}


* **Parameters to provide:**
* The name to be provided for API source
   * Flag: `--name NAME`
* The description for source.
   * Flag: `--description DESCRIPTION`
* The boolean flag to enable or disable the source
   * Flag: `--enabled ENABLED`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`

### ibmcloud event-notifications source update
{: #event-notifications-cli-source-update-command}

Update `Source`.

```sh 
ibmcloud event-notifications source update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--enabled ENABLED]
```
{: pre}


* **Parameters to provide:**
* The name to be provided for API source
   * Flag: `--name NAME`
* Unique identifier for Source. Required.
   * Flag: `--id ID`   
* The description for source.
   * Flag: `--description DESCRIPTION`
* The boolean flag to enable or disable the source
   * Flag: `--enabled ENABLED`      
* The Unique identifier for IBM Cloud Event Notifications instance.
   * Flag: `[--instance-id INSTANCE-ID]`   

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

### ibmcloud event-notifications source delete
{: #event-notifications-cli-source-delete-command}

Delete specific `Source`.

```sh
ibmcloud event-notifications source delete --instance-id INSTANCE-ID --id ID
```
{: pre}

* **Parameters to provide:**
* Unique identifier for Source. Required.
   * Flag: `--id ID`
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
{: #CLI_Event_Notifications_sendnots}

### ibmcloud event-notifications Send Notifications
{: #event-notifications-cli-send-notifications-command}

Use below command to send notifications in cli version 0.0.7.

```sh
ibmcloud event-notifications send-notifications --instance-id INSTANCE-ID --subject SUBJECT --severity SEVERITY --id ID --source SOURCE --en-source-id EN-SOURCE-ID --type TYPE --time TIME [--data DATA] [--push-to PUSH-TO] [--message-fcm-body MESSAGE-FCM-BODY] [--message-apns-headers MESSAGE-APNS-HEADERS] [--message-apns-body MESSAGE-APNS-BODY] [--datacontenttype DATACONTENTTYPE] [--specversion SPECVERSION] 
```
{: pre}

Use below command to send notifications in cli version 0.0.8.

send-notifications --instance-id INSTANCE-ID [--body BODY] [--ce-ibmenseverity CE-IBMENSEVERITY] [--ce-ibmendefaultshort CE-IBMENDEFAULTSHORT] [--ce-ibmendefaultlong CE-IBMENDEFAULTLONG] [--ce-ibmenfcmbody CE-IBMENFCMBODY] [--ce-ibmenapnsbody CE-IBMENAPNSBODY] [--ce-ibmenpushto CE-IBMENPUSHTO] [--ce-ibmenapnsheaders CE-IBMENAPNSHEADERS] [--ce-ibmenchromebody CE-IBMENCHROMEBODY] [--ce-ibmenfirefoxbody CE-IBMENFIREFOXBODY] [--ce-ibmenchromeheaders CE-IBMENCHROMEHEADERS] [--ce-ibmenfirefoxheaders CE-IBMENFIREFOXHEADERS] [--ce-ibmensourceid CE-IBMENSOURCEID] [--ce-id CE-ID] [--ce-source CE-SOURCE] [--ce-type CE-TYPE] [--ce-specversion CE-SPECVERSION] [--ce-time CE-TIME]

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

* The body payload to be provided for notification. 
   * Flag: `[--body BODY]` 
* The short text for notification to send
   * Flag: `[--ce-ibmendefaultshort]`
* The long text for notification top send.
   * Flag: `[--ce-ibmendefaultlong CE-IBMENDEFAULTLONG]`   
* The level of severity for notification. Required.
   * Flag: `[--ce-ibmenseverity CE-IBMENSEVERITY]`   
* The source description.
   * Flag: `[--ce-source CE-SOURCE]`  
* The source ID to be set for Notification source. Required
   * Flag: `[--ce-ibmensourceid CE-IBMENSOURCEID]`
* The type of notification. Required
   * Flag: `[--ce-type CE-TYPE]`  
* The Timestamp to be set for notification. Required
   * Flag: `[--time TIME]`        
* The spec version value.Default value to be used is 1.0
   * Flag: `[--ce-specversion CE-SPECVERSION]`  
* PThe Device data information to send data in case of Registered Devices/ Usersids/ Platforms.
   * Flag: `[--ce-ibmenpushto CE-IBMENPUSHTO]`
* FCM message body to send notification to FCM devices.
   * Flag: `[--ce-ibmenfcmbody CE-IBMENFCMBODY]` 
* Chrome message body to send notification to FCM devices.
   * Flag: `[--ce-ibmenchromebody CE-IBMENCHROMEBODY]`
* Firefox message body to send notification to FCM devices.
   * Flag: `[--ce-ibmenfirefoxbody CE-IBMENFIREFOXBODY]`      
* The Custom APNS headers information can be set using this option.
   * Flag: `[--ce-ibmenapnsheaders CE-IBMENAPNSHEADERS]` 
* The Custom Chrome headers information can be set using this option.
   * Flag: `[--ce-ibmenchromeheaders CE-IBMENCHROMEHEADERS]` 
* The Custom Firefox information can be set using this option.
   * Flag: `[--ce-ibmenfirefoxheaders CE-IBMENFIREFOXHEADERS]`         
* The apns meaage body can be set using this option.
   * Flag: `[--ce-ibmenapnsbody CE-IBMENAPNSBODY]`              

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

The following example shows the format of Chrome message body to send notification to FCM devices.        

```json
{"title":"Hello Chrome", "en_data":{"alert":"Hello Chrome Notification","title":"Chrome New Title","iconUrl":"https://","timeToLive":100,"payload":{"key":"value"}}}

```
The following example shows the format of Firefox message body to send notification to FCM devices.        

```json

'{"title":"Hello Firefox", "en_data":{"alert":"Hello firefox Notification","title":"firefox New Title","iconUrl":"https://","timeToLive":100,"payload":{"key":"value"}}}'

```

The following example shows the format of apns/chrome/fireox custom headers.   

```json
{
    "test": "test header",
    "new": "newmessage"
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

#### Additional properties that can be configured for the IOS notification
{: #event-notifications-cli-send-notifications-command-addprops}

|  Property  |  Property type  |  Description  |
|-------------|-------------|-------------|
|  badge | integer | The number to display as the badge of the application icon. |
| interactive_category | string | The category identifier to be used for the interactive push notifications. |
| ios_action_key | string |The title for the Action key.| 
| payload | JSON object | Custom JSON payload that is sent as part of the notification message.|
| sound | string | The name of the sound file in the application bundle. The sound of this file is played as an alert. |
| title_loc_key | string | The key to a title string in the Localizable.strings file for the current localization. The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the titleLocArgs array. |
| loc_key | string | A key to an alert-message string in a Localizabl.strings file for the current localization (which is set by the user's language preference). The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the locArgs array. |
| launch_image | string | The filename of an image file in the app bundle, with or without the filename extension. The image is used as the launch image when users tap the action button or move the action slider. |
| title_loc_args | string | Variable string values to appear in place of the format specifiers in title-loc-key. |
| loc_args | string | Variable string values to appear in place of the format specifiers in locKey. | title string The title of Rich Push notifications (Supported only on iOS 10 and above).|
| title | string | The title of Rich Push notifications (Supported only on iOS 10 and above). |
| subtitle | string | The subtitle of the Rich Notifications (Supported only on iOS 10 and above). |
| body | string | The body for IOS notifications. |
| attachment_url | string | The link to the iOS notifications media (video, audio, GIF, images - Supported only on iOS 10 and above). |
| type | string | Allowable values: DEFAULT, MIXED, SILENT. |
| apns_collapse_id | string | Multiple notifications with the same collapse identifier are displayed to the user as a single notification. |
| apns_thread_id | string | An app-specific identifier for grouping related notifications. This value corresponds to the threadIdentifier property in the UNNotificationContent object. |
| apns_group_summary_arg | string | The string the notification adds to the category’s summary format string. |
| apns_group_summary_arg_count | integer | The number of items the notification adds to the category’s summary format string. |
{: caption="Table 1. iOS platform settings " caption-side="bottom"}

#### Additional properties that can be configured for the FCM notification
{: #event-notifications-cli-send-notifications-command-fcm}

|  Property  |  Property type  |  Description  |
|-------------|-------------|-------------|
| icon | string | Specify the name of the icon to be displayed for the notification. Make sure that the icon is already packaged with the client application. |
| delay_while_idle | boolean | When set to true, this parameter indicates that the message should not be sent until the device becomes active. |
| sync | boolean | Device group messaging makes it possible for every app instance in a group to reflect the latest messaging state. |
| visibility | string | private/public - Visibility of this notification, which affects how and when the notifications are revealed on a secure locked screen. |
| redact | string | Content that is specified shows up on a secure locked screen on the device when visibility is set to Private. |
| payload | JSON object | Custom JSON payload that is sent as part of the notification message.|
|priority | string | A string value that indicates the priority of this notification. Allowed values are 'max', 'high', 'default', 'low' and 'min'. High/Max priority notifications along with 'sound' field might be used for Heads up notification in Android 5.0 or higher.sampleval='low'. |
| sound | string| The sound file (on device) that will be attempted to play when the notification arrives on the device. |
| time_to_live | integer | Specifies how long (in seconds) the message should be kept in GCM storage if the device is offline.
| lights |  | Sets the notification LED color on receiving push notification. |
| ledArgb | string | The color of the LED. The hardware does its best approximation. |
| ledOnMs | integer | The time in milliseconds for the LED to be on while it's flashing. The hardware does its best approximation. |
| ledOffMs | string | The time in milliseconds for the LED to be off while it's flashing. The hardware does its best approximation. |
| android_title | string | The title of Rich Push notifications. |
| group_id | string | Set this notification to be part of a group of notifications sharing the same key. Grouped notifications might display in a cluster or stack on devices that support such rendering. |
| style |  | Options to specify for Android expandable notifications. The types of expandable notifications are picture_notification, bigtext_notification, inbox_notification. |
| type | string | Specifies the type of expandable notifications. The possible values are bigtext_notification, picture_notification, inbox_notification.| 
| title | string | Specifies the title of the notification. The title is displayed when the notification is expanded. Title must be specified for all three expandable notifications. |
| type | string | Allowed values: DEFAULT, SILENT. |
| alert | string | The alert value of Notification. |
{: caption="Table 2. Android platform settings " caption-side="bottom"}
