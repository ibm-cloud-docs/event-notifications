---

copyright:
  years: 2021, 2025
lastupdated: "2025-03-19"

keywords: event notifications CLI plug-in, CLI reference, en cli reference, event notifications cli reference, event notifications, command line reference

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_short}} CLI
{: #event-notifications-cli}

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides extra capabilities for service offerings. {{site.data.keyword.cloud_notm}} CLI supports a plug-in framework to extend its capability. You can install the {{site.data.keyword.en_short}} CLI plug-in from the {{site.data.keyword.cloud_notm}} plug-in repository. With the {{site.data.keyword.en_short}} service CLI plug-in, you can easily manage {{site.data.keyword.en_short}} service instances by using the CLI commands available.
{: shortdesc}

## Prerequisites
{: #en-cli-prereq}

- An {{site.data.keyword.cloud_notm}} account. If you do not have an account, click [here](https://cloud.ibm.com/) to create one.
- An instance of [{{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}}](https://cloud.ibm.com/catalog/services/event-notifications) service.
- [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli) package on your local system.

When you log in to the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started){: external}, you're notified when updates are available. Be sure to keep your CLI up-to-date so that you can use the commands and flags that are available for the {{site.data.keyword.en_short}} CLI plug-in.
{: tip}

[IBM Cloud Quick Reference card](https://cloud.ibm.com/media/docs/downloads/IBM%20Cloud%20CLI%20quick%20reference.pdf).


**Note** The CLI Plugin versions from 0.0.5 to 1.0.0 is deprecated.
{: note}

## Install the {{site.data.keyword.en_short}} CLI
{: #en-cli-install}

Install the {{site.data.keyword.en_short}} CLI plug-in by using the `plugin install` command.

```sh
ibmcloud plugin install en
```
{: pre}

## {{site.data.keyword.en_short}} CLI commands
{: #en-cli-commands}

### ibmcloud event-notifications init
{: #en-cli-init-command}

Set the instance that you'll we working on by using the following command:

```sh
ibmcloud event-notifications init [--instance-id INSTANCE-ID]
```
{: pre}

#### Command options
{: #en-cli-init-options}

`--instance-id` (string)
:  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications environment variables set
{: #en-cli-environment-variables}

Sets the region that you'll be working on. The default endpoint region is Dallas. For other regions, change the endpoint by using the export command to set the variable, for example, use the following command for Sydney:
export IBMCLOUD_EN_ENDPOINT=<https://au-syd.event-notifications.cloud.ibm.com/event-notifications>

- export **IBMCLOUD_EN_ENDPOINT** variable to set the {{site.data.keyword.en_short}} region public endpoint.

   - **Dallas:** `https://us-south.event-notifications.cloud.ibm.com/event-notifications`
   - **London:** `https://eu-gb.event-notifications.cloud.ibm.com/event-notifications`
   - **Sydney:** `https://au-syd.event-notifications.cloud.ibm.com/event-notifications`
   - **Frankfurt:** `https://eu-de.event-notifications.cloud.ibm.com/event-notifications`
   - **Madrid:** `https://eu-es.event-notifications.cloud.ibm.com/event-notifications`
   - **Osaka:** `https://jp-osa.event-notifications.cloud.ibm.com/event-notifications`
   - **Tokyo:** `https://jp-tok.event-notifications.cloud.ibm.com/event-notifications`
   - **Toronto:** `https://ca-tor.event-notifications.cloud.ibm.com/event-notifications`

- export **IBMCLOUD_EN_ENDPOINT** variable to set the {{site.data.keyword.en_short}} region private endpoint.

   - **Dallas:** `https://private.us-south.event-notifications.cloud.ibm.com/event-notifications`
   - **London:** `https://private.eu-gb.event-notifications.cloud.ibm.com/event-notifications`
   - **Sydney:** `https://private.au-syd.event-notifications.cloud.ibm.com/event-notifications`
   - **Frankfurt:** `https://private.eu-de.event-notifications.cloud.ibm.com/event-notifications`
   - **Madrid:** `https://private.eu-es.event-notifications.cloud.ibm.com/event-notifications`
   - **Osaka:** `https://private.jp-osa.event-notifications.cloud.ibm.com/event-notifications`
   - **Tokyo:** `https://private.jp-tok.event-notifications.cloud.ibm.com/event-notifications`
   - **Toronto:** `https://private.ca-tor.event-notifications.cloud.ibm.com/event-notifications`

- export **EVENT_NOTIFICATIONS_API_KEY** variable to set the {{site.data.keyword.en_short}} instance `apikey`.

### ibmcloud event-notifications show
{: #en-cli-show-command}

Check your configuration.

The command shows the initialized Event Notifications instance GUID.

```sh
ibmcloud event-notifications show
```
{: pre}

## Sources
{: #en-cli-source}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} source.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications source --help
```
{: pre}

### ibmcloud event-notifications source create
{: #en-cli-source-create-command}

- **Action:** Create `Source`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications source create --instance-id INSTANCE-ID --name NAME --description DESCRIPTION [--enabled ENABLED]
   ```
   {: pre}

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications sources-create --instance-id INSTANCE-ID --name NAME --description DESCRIPTION [--enabled ENABLED]
   ```
   {: pre}

- **Parameters to provide:**

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `--name NAME` (int64)
   :  The name to be provided for API source.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `1` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--description DESCRIPTION` (string)
   :  The description for source.

      The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--enabled ENABLED` (Boolean)
   :  The Boolean flag to enable or disable the source.

      The value is set to true to enable the source and false to disable the source.

### ibmcloud event-notifications source update
{: #en-cli-source-update-command}

- **Action:** Update `Source`.
   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications source update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--enabled ENABLED]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications source-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--enabled ENABLED]
   ```
   {: pre}

- **Parameters to provide:**

   `--instance-id` (string)
   :  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `--name` (int64)
   :  API Source name.

      The default value is ``. The maximum length is `255` characters. The minimum length is `1` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--description` (int64)
   :  API Source Description

      The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--enabled` (Boolean)
   :  Search string for filtering results.

      The value is set to true to enable the source and false to disable the source.

   `--id` (string)
   :  Unique identifier for Source. Required.

      The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

### ibmcloud event-notifications source list
{: #en-cli-source-list-command}

- **Action:** List all `Source`.
   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications source list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications sources [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--limit LIMIT` (int64)
   :  The page limit for paginated results.

      The maximum value is `100`. The minimum value is `1`.

   `--offset OFFSET` (int64)
   :  The offset for paginated results.

      The minimum value is `0`.

   `--search SEARCH` (string)
   :  The search string for filtering results.

      The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]`
   :  Activate to force resource deletion (to bypass the confirmation prompt).

### ibmcloud event-notifications source get
{: #en-cli-source-get-command}

- **Action:** Get specific `Source`.
   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications source get --id ID [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications source --id ID [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for source. Required.

      The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

   `--offset OFFSET`
   :  The offset for paginated results.

   `--search SEARCH`
   :  The search string for filtering results.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]`
   :  Activate to force resource deletion (to bypass the confirmation prompt).

### ibmcloud event-notifications source delete
{: #en-cli-source-delete-command}

- **Action:** Delete specific `Source`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications source delete --instance-id INSTANCE-ID --id ID
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications source-delete  --instance-id INSTANCE-ID --id ID
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for source. Required.

      The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]`
   :  Activate to force resource deletion (to bypass the confirmation prompt).

## Destinations
{: #en-cli-destination}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} destination.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications destination --help
```
{: pre}

### ibmcloud event-notifications destination create
{: #en-cli-destination-create}

- **Action:** Create a destination.
   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications destination create --name NAME --type TYPE [--description DESCRIPTION] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--config CONFIG] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications destination-create --instance-id INSTANCE-ID --name NAME --type TYPE [--description DESCRIPTION] [--collect-failed-events COLLECT-FAILED-EVENTS] [--config CONFIG] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--icon16x16 ICON16X16] [--icon16x16-content-type ICON16X16-CONTENT-TYPE] [--icon16x162x ICON16X162X] [--icon16x162x-content-type ICON16X162X-CONTENT-TYPE] [--icon32x32 ICON32X32] [--icon32x32-content-type ICON32X32-CONTENT-TYPE] [--icon32x322x ICON32X322X] [--icon32x322x-content-type ICON32X322X-CONTENT-TYPE] [--icon128x128 ICON128X128] [--icon128x128-content-type ICON128X128-CONTENT-TYPE] [--icon128x1282x ICON128X1282X] [--icon128x1282x-content-type ICON128X1282X-CONTENT-TYPE]
   ```
   {: pre}

- **Parameters to provide:**

   `--instance-id` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `--name NAME` (string)
   :  The name of the destination. Required.

      The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `--type TYPE` (string)
   :  The type of the destination. The options available are webhook, push_android, push_ios,push_chrome,push_firefox,push_huawei,push_safari,ibmce,  ibmcos,msteams,pagerduty,servicenow,slack,smtp_custom,sms_custom, event_streams. Required.

      Allowable values are: `webhook`, `push_android`, `push_ios`,`push_chrome`,`push_firefox`,`push_huawei`,`push_safari`,`ibmce`,  `ibmcos`,`msteams`,`pagerduty`,`servicenow`,`slack`,`smtp_custom`,`sms_custom`,event_streams. The minimum length is `1` character.

   `--collect-failed-events` (bool)
   :   Whether to collect the failed event in Cloud Object Storage bucket.

    The default value is `false`.

   `--description DESCRIPTION` (string)
   :  The description of the destination.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `--certificate CERTIFICATE` (string)
   :  The certificate file path to be provided. The allowed file type is p8 and p12 certificate. Provide file location to pass the certificate.

   `--certificate-content-type CERTIFICATE-CONTENT-TYPE` (string)
   :  The certificate content type to be set in the case of iOS destination. The default value is ``. The available options are: p8 or p12.

   `--config CONFIG` ([`DestinationConfig` examples](#en-cli-destination-config-example-schema))
   :  The configuration needed to set the destination-specific parameters.

      `--icon16x16` (io.ReadCloser)
   :   Safari icon 16x16.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon16x16-content-type` (string)
   :   The content type of Icon16x16.

   `--icon16x162x` (io.ReadCloser)
   :   Safari icon 16x16@2x.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon16x162x-content-type` (string)
   :   The content type of Icon16x162x.

   `--icon32x32` (io.ReadCloser)
   :   Safari icon 32x32.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon32x32-content-type` (string)
   :   The content type of Icon32x32.

   `--icon32x322x` (io.ReadCloser)
   :   Safari icon 32x32@2x.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon32x322x-content-type` (string)
   :   The content type of Icon32x322x.

   `--icon128x128` (io.ReadCloser)
   :   Safari icon 128x128.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon128x128-content-type` (string)
   :   The content type of Icon128x128.

   `--icon128x1282x` (io.ReadCloser)
   :   Safari icon 128x128@2x.

      The maximum length is `5000` characters. The minimum length is `1` character.

   `--icon128x1282x-content-type` (string)
   :   The content type of Icon128x1282x.

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

   Note: The Event Notifications Destination Cloud Functions has been deprecated and no longer supported in category of destinations.

- **Examples:**
{: #en-cli-destination-config-example-schema}

   - The following example shows format of the `DestinationConfig` object for iOS destination(push_ios) with P8 certificate. Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*:

      ```json
      {
         "params" : {
            "cert_type" : "p8",
            "is_sandbox" : true,
            "key_id": "production",
            "team_id": "1234",
            "bundle_id": "test1",
            "pre_prod" : "true" // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```


   - The following example shows format of the `DestinationConfig` object for iOS destination(push_ios) with P12 certificate. Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*.

      ```json
      {
         "params" : {
            "cert_type" : "p12",
            "is_sandbox" : true,
            "password": "apnspasswordvalue",
            "pre_prod" : "true" true // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```

   - The following example shows the format of the `DestinationConfig` object for Chrome destination(push_chrome). Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*.

      ```json
      {
         "params" : {
            "api_key": "chromeapikey",
            "website_url" : "https://testwebsite.com",
            "pre_prod" : "true" true // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for Firefox destination(push_firefox). Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*.

      ```json
      {
         "params" : {
            "website_url" : "https://testwebsite.com",
            "pre_prod" : "true" // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for Slack destination(slack) with type as incoming_webhook.

      ```json
      {
         "params" : {
            "type" : "incoming_webhook",
            "url" : "https://hooks.slack.com/services/G0gyhsush/TYodsjhs/GHTbfidsimkk"
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for Slack destination(slack) with type as direct_message.

      ```json
      {
         "params" : {
            "type" : "direct_message",
            "token" : "vhdwvecwefwefewivcweivcwiwiciwcvwicwec"
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for Safari destination(push_safari). Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*.

      ```json
      {
         "params": {
            "cert_type":"p12",
            "certificate_name":"Users/Testuser/Documents/safari.p12",
            "password":"safarinew",
            "url_format_string":"https://test.com",
            "website_name":"testwebsite",
            "website_push_id":"test",
            "website_url":"https://test.com",
            "pre_prod" : "true" // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for MS Teams(msteams) destination.

      ```json
      {
         "params" : {
            "url" : "https://xyz.webhook.office.com"
         }
      }
      ```

   - The following example shows format of the `DestinationConfig` object for PagerDuty(pagerduty) destination.

      ```json
      {
         "params" : {
            "routing_key" : "routingkeytoconnecttoPD",
            "api_key" : "cffunctionnamespaceserviceidapikey"
         }
      }
      ```


   - The following example shows the format of the `DestinationConfig` object for Webhook(webhook).
   
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

   - The following example shows the format of the `DestinationConfig` object for Android(push_android) destination.

      ```json
      {
         "params" : {
            "project_id" : "6232305230320",
            "private_key" : "36e21epfweort823or8rt832pr8p2r832pr82pr382r8f",
            "client_email" : "testuser.123@gmail.com",
            "pre_prod" : true // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```


   - The following example shows the format of the `DestinationConfig` object for ServiceNow(servicenow) destination.

      ```json
      {
         "params" : {
            "client_id" : "359705ceddd100eyfewyyw1f0f9e1c96",
            "client_secret": "testsecrets",
            "username": "testuser",
            "password": "user_password",
            "instance_name": "testinstancenje"
         }
      }
      ```

   - The following example shows the format of the `DestinationConfig` object for Code Engine(ibmce) destination.

      code engine destination type: application

      ```json
      {
         "params" : {
            "type" : "application",
            "url" : "https://codeengine.test.com",
            "verb" : "get",
            "custom_headers" : { },
            "sensitive_headers" : [ "exampleString" ]
         }
      }
      ```

      code engine destination type: job

      ```json
      {
         "params" : {
            "type" : "job",
            "job_name" : "custom-job",
            "project_crn" : "crn:v1:bluemix:public:codeengine:us-south:a/e7e5820aeccb40efb78fd69a7858ef23:xxxxxxxxxxxxxx::"
            
         }
      }
      ```


   - The following example shows the format of the `DestinationConfig` object for {{site.data.keyword.cos_full_notm}}(ibmcos) destination.

      ```json
      {
         "params" : {
            "bucket_name" : "cos-destination-en-bucket",
            "instance_id" : "42e13636e-0548-41a0-a178-e95be28464773",
            "endpoint" : "https://s3.us-west.cloud-object-storage.appdomain.cloud"
         }
      }
      ```


   - The following example shows the format of the `DestinationConfig` object for Huawei(push_huawei) destination.

      ```json
      {
         "params" : {
            "client_id" : "359705ceddd100eyfew",
            "client_secret": "testsecrets",
            "pre_prod" : true // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
         }
      }
      ```  

   - The following example shows the format of the `DestinationConfig` object for Custom Email(smtp_custom) destination.

      Process To do the Custom Domain Configuration and Verification: <https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-destinations-custom-email#en-destinations-custom-email-verify>

      ```json
      {
         "params" : {
            "domain": "mailx.com"
         }
      }
      ```  

       - The following example shows the format of the `DestinationConfig` object for {{site.data.keyword.messagehub}}(event_streams) destination.

      ```json
      {
         "params" : {
           "crn": "crn:v1:bluemix:public:messagehub:us-south:a/9f007405a9fe4a5d9345fa8c13357373:a292db6e-af78-4c0b-b3db-7d6794b637g::",
           "endpoint": "https://n6627w6t7dgeh2cfgd.svc09.us-south.eventstreams.cloud.ibm.com",
           "topic": "demo_topic"
         }
      }
      ```

   Note: The Custom SMS Destination does not require any Destination Config To be set up.

### ibmcloud event-notifications destination list
{: #en-cli-destination-list-command}

- **Action:** List all `Destination`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications destination list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications destinations [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--limit LIMIT` (int64)
   :  The page limit for paginated results.

      The maximum value is `100`. The minimum value is `1`.

   `--offset OFFSET` (int64)
   :  The offset for paginated results.

      The minimum value is `0`.

   `--search SEARCH` (string)
   :  The search string for filtering results.

      The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

   `--instance-id` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications destination get
{: #en-cli-destination-get-command}

- **Action:** Get specific `Destination`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications destination get --id ID [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications destination --id ID [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  The unique identifier for destination. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications destination update
{: #en-cli-destination-update-command}

- **Action:** Update existing `Destination`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications destination update --id ID [--name NAME] [--description DESCRIPTION] [--certificate CERTIFICATE] [--config CONFIG] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications destination-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--collect-failed-events COLLECT-FAILED-EVENTS] [--config CONFIG] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--icon16x16 ICON16X16] [--icon16x16-content-type ICON16X16-CONTENT-TYPE] [--icon16x162x ICON16X162X] [--icon16x162x-content-type ICON16X162X-CONTENT-TYPE] [--icon32x32 ICON32X32] [--icon32x32-content-type ICON32X32-CONTENT-TYPE] [--icon32x322x ICON32X322X] [--icon32x322x-content-type ICON32X322X-CONTENT-TYPE] [--icon128x128 ICON128X128] [--icon128x128-content-type ICON128X128-CONTENT-TYPE] [--icon128x1282x ICON128X1282X] [--icon128x1282x-content-type ICON128X1282X-CONTENT-TYPE]
   ```
   {: pre}

- **Parameters to provide:**

   `--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Destination. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:   Destination name.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--description` (string)
:   Destination description.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--collect-failed-events` (bool)
:   Whether to collect the failed event in Cloud Object Storage bucket.

    The default value is `false`.

`--config` ([`DestinationConfig`](#en-cli-destination-config-example-schema))
:   Payload describing a destination configuration.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--config=@path/to/file.json`.

`--certificate` (io.ReadCloser)
:   Certificate for APNS.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--certificate-content-type` (string)
:   The content type of Certificate.

`--icon16x16` (io.ReadCloser)
:   Safari icon 16x16.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x16-content-type` (string)
:   The content type of Icon16x16.

`--icon16x162x` (io.ReadCloser)
:   Safari icon 16x16@2x.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x162x-content-type` (string)
:   The content type of Icon16x162x.

`--icon32x32` (io.ReadCloser)
:   Safari icon 32x32.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x32-content-type` (string)
:   The content type of Icon32x32.

`--icon32x322x` (io.ReadCloser)
:   Safari icon 32x32@2x.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x322x-content-type` (string)
:   The content type of Icon32x322x.

`--icon128x128` (io.ReadCloser)
:   Safari icon 128x128.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x128-content-type` (string)
:   The content type of Icon128x128.

`--icon128x1282x` (io.ReadCloser)
:   Safari icon 128x128@2x.

    The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x1282x-content-type` (string)
:   The content type of Icon128x1282x.

### ibmcloud event-notifications destination delete
{: #en-cli-destination-delete-command}

- **Action:** Delete existing `Destination`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications destination delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications destination-delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  The unique identifier for destination. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]` (Boolean)
   :  Activate to force resource deletion (to bypass the confirmation prompt).
{: pre}

### `ibmcloud event-notifications enabled-countries`
{: #event-notifications-cli-enabled-countries-command}

Get enabled country details of SMS destination.

```sh
ibmcloud event-notifications enabled-countries --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-enabled-countries-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Destination. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

#### Example
{: #event-notifications-enabled-countries-examples}

```sh
ibmcloud event-notifications enabled-countries \
    --instance-id=exampleString \
    --id=exampleString
```
{: pre}

### `ibmcloud event-notifications test-destination`
{: #event-notifications-cli-test-destination-command}

Test a Destination.

```sh
ibmcloud event-notifications test-destination --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-test-destination-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Destination. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

#### Example
{: #event-notifications-test-destination-examples}

```sh
ibmcloud event-notifications test-destination \
    --instance-id=exampleString \
    --id=exampleString
```
{: pre}

### `ibmcloud event-notifications verify-destination-update`
{: #event-notifications-cli-verify-destination-update-command}

Verify SPF and DKIM records of custom domain.

```sh
ibmcloud event-notifications verify-destination-update --instance-id INSTANCE-ID --id ID --type TYPE
```

#### Command options
{: #event-notifications-verify-destination-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Destination. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:   Verification type. Required.

    The maximum length is `20` characters. The minimum length is `1` character. The value must match regular expression `/[a-z]/`.

#### Example
{: #event-notifications-verify-destination-update-examples}

```sh
ibmcloud event-notifications verify-destination-update \
    --instance-id exampleString \
    --id exampleString \
    --type exampleString
```
{: pre}

## Topics
{: #en-cli-topic}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} topic.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications topic --help
```
{: pre}

### ibmcloud event-notifications topic create
{: #en-cli-topic-create-command}

- **Action:** Create new `Topic`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications topic create --name NAME [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications topic-create --name NAME [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--name NAME` (string)
   :  Name of the topic. Required.

      The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--description DESCRIPTION` (string)
   :  Description of the topic.

      The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--sources SOURCES]` ([TopicCreateSourcesItem[]](#en-cli-topic-example-schema))
   :  The list of sources.

- **Example:**
{: #en-cli-topic-example-schema}
  
   - The following example shows the format of the `TopicCreateSourcesItem[]` object for the Periodic Timer source.

      ```json
       [
          {
             "id" : "exampleString",
             "rules" : [
                {
                   "enabled" : true,
                   "event_schedule_filter": {
                      "starts_at": "2024-12-23T12:00:00.000Z",
                      "ends_at": "2024-12-23T20:00:00.000Z",
                      "expression": "* * * * *"
                      }
                }
             ]
          }
       ]
      ```

   - The following example shows the format of the `TopicCreateSourcesItem[]` object.

      ```json
      [
         {
            "id" : "exampleString",
            "rules" : [
               {
                  "enabled" : true,
                  "event_type_filter" : "$.*",
                  "notification_filter" : "exampleString"
               }
            ]
         }
      ]
      ```

   - The following example shows the format of the `TopicUpdateSourcesItem[]` object.

      ```json
      [
         {
            "id" : "exampleString",
            "rules" : [
               {
                  "enabled" : true,
                  "event_type_filter" : "exampleString",
                  "notification_filter" : "exampleString",
                  "rule_id" : "exampleString"
               }
            ]
         }
      ]
      ```

### ibmcloud event-notifications topic list
{: #en-cli-topic-list-command}

- **Action:** List all `Topic`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications topic list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications topics [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--limit LIMIT` (int64)
   :  The page limit for paginated results.

      The maximum value is `100`. The minimum value is `1`.

   `--offset OFFSET` (int64)
   :  The offset for paginated results.

      The minimum value is `0`.

   `--search SEARCH` (string)
   :  The search string for filtering results.

      The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications topic get
{: #en-cli-topic-get-command}

- **Action:** Get specific `Topic`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications topic get --id ID [--include INCLUDE] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications topic --id ID [--include INCLUDE] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for topic. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--include INCLUDE` (string)
   :  Include sub topics.

      The default value is ``. The maximum length is `20` characters. The minimum length is `0` characters. The value must match regular expression `/[a-z]/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications topic update
{: #en-cli-topic-update-command}

- **Action:** Update existing `Topic`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications topic update --id ID [--name NAME] [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications topic-replace --id ID [--name NAME] [--description DESCRIPTION] [--sources SOURCES] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--instance-id` (string)
   :  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `--id` (string)
   :  Unique identifier for topic. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--name` (string)
   :  Name of the topic.

      The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--description` (string)
   :  Description of the topic.

      The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

   `--sources` ([TopicUpdateSourcesItem[]](#en-cli-topic-example-schema))
   :  List of sources.

### ibmcloud event-notifications topic delete
{: #en-cli-topic-delete-command}

- **Action:** Delete existing `Topic`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications topic delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications topic-delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for topic. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]` (Boolean)
   :  Activate to force resource deletion (to bypass the confirmation prompt).

## Subscriptions
{: #en-cli-subscription}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} subscription.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications subscription --help
```
{: pre}

### ibmcloud event-notifications subscription create
{: #en-cli-subscription-create-command}

- **Action:** Create new `Subscription`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications subscription create [--name NAME] [--description DESCRIPTION] [--destination-id DESTINATION-ID] [--topic-id TOPIC-ID] [--attributes ATTRIBUTES] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications subscription-create --instance-id INSTANCE-ID --name NAME --destination-id DESTINATION-ID --topic-id TOPIC-ID [--description DESCRIPTION] [--attributes ATTRIBUTES] 
   ```
   {: pre}

- **Parameters to provide:**

   `--name NAME` (string)
   :  The name to be set for subscription.

      The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `--instance-id INSTANCE-ID` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `--description DESCRIPTION` (string)
   :  The description to be set for subscription.

      The default value is ``. The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `--destination-id DESTINATION-ID` (string)
   :  The destination ID to be set for subscription.

      The maximum length is `150` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--topic-id TOPIC-ID` (string)
   :  The topic ID to be set for subscription.

      The maximum length is `150` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--attributes ATTRIBUTES` ([SubscriptionCreateAttributes](#en-cli-subscription-example-schema))
   :  The attributes to be set for subscription.

- **Examples:**
{: #en-cli-subscription-example-schema}

   - The following example shows the format of the `SubscriptionCreateAttributes` object for webhook.

      ```json
      {
         "signing_enabled" : true,
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13"
      }
      ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for SMS.

      ```json
      {
         "invited" :["+1xxxxxxxxxx", "+1xxxxxxxxxx"]
      }
      ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for IBM Email.

      ```json
      {
         "invited" :["entest@gmail.com"],
         "add_notification_payload": true,
         "reply_to_mail": "en@ibm.com",
         "reply_to_name": "EYS ORG",
         "from_name":"ABC ORG"
      }
      ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for Slack Destination type as incoming_webhook.

      ```json
      {
         "attachment_color" : "#FF0000",
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
      }
      ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for Slack Destination type as direct_message.

   ```json
   {
      "channels" : [{ "id": "GHIUIFJHGGH"},{"id": "TSFDIDFOFNF"}],
      "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
   }
   ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for ServiceNow.

      ```json
      {
         "assigned_to" : "serviceuser@gmail.com",
         "assignment_group" : "incidentgroup"
      }
      ```

   - The following example shows the format of the `SubscriptionCreateAttributes` object for Custom Email.

      ```json
      {
         "invited" :["entest@gmail.com"],
         "add_notification_payload": true,
         "reply_to_mail": "en@ibm.com",
         "reply_to_name": "EYS ORG",
         "from_name":"ABC ORG",
         "from_email":"Testuser@mailx.com",
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724afc58b13",
         "template_id_invitation": "f1ef32fb-b7dd-4405-xxxx-7b6719cee8aa"
      }
      ```
      - The following example shows the format of the `SubscriptionCreateAttributes` object for Pagerduty/Event Streams.

      ```json
      {
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724afc58b13",
      }
      ```

### ibmcloud event-notifications subscription list
{: #en-cli-subscription-list-command}

- **Action:** List all `Subscription`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications subscription list [--offset OFFSET] [--limit LIMIT] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```

    [From version 1.0.0]

   ```sh
   ibmcloud event-notifications subscriptions [--offset OFFSET] [--limit LIMIT] [--search SEARCH] [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--limit LIMIT` (int64)
   :  The page limit for paginated results.

      The maximum value is `100`. The minimum value is `1`.

   `--offset OFFSET` (int64)
   :  The offset for paginated results.

      The minimum value is `0`.

   `--search SEARCH` (string)
   :  The search string for filtering results.

      The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

   `[--instance-id INSTANCE-ID]`  (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.      

### ibmcloud event-notifications subscription get
{: #en-cli-subscription-get-command}

- **Action:** Get specific `Subscription`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications subscription get --id ID [--instance-id INSTANCE-ID]
   ```

    [From version 1.0.0]

   ```sh
   ibmcloud event-notifications subscription --id ID [--instance-id INSTANCE-ID]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for subscription. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications subscription delete
{: #en-cli-subscription-delete-command}

- **Action:** Delete existing `Subscription`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications subscription delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications subscription-delete --id ID [--instance-id INSTANCE-ID] [--force]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for subscription. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--force]` (Boolean)
   :  Activate to force resource deletion (to bypass the confirmation prompt).

### ibmcloud event-notifications subscription update
{: #en-cli-subscription-update-command}

- **Action:** Update existing `Subscription`.

   [Supported till version 0.2.0]

   ```sh
   ibmcloud event-notifications subscription update --id ID [--name NAME] [--description DESCRIPTION] [--attributes ATTRIBUTES] [--instance-id INSTANCE-ID]
   ```

   [From version 1.0.0]

   ```sh
   ibmcloud event-notifications subscription-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--attributes ATTRIBUTES]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for subscription. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--name NAME]` (string)
   :  The updated description to be set for subscription.

      The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

   `[--instance-id INSTANCE-ID]` (string)
   :  The Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

   `[--description DESCRIPTION]` (string)
   :  The updated description to be set for subscription.

      The default value is ``. The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

   `[-attributes ATTRIBUTES]` ([SubscriptionUpdateAttributes](#en-cli-subscription-update-example-schema))
   :  The attributes to be set for subscription

- **Examples:**
{: #en-cli-subscription-update-example-schema}

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for Webhook.

      ```json
      {
         "signing_enabled": true
      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for IBM SMS.

      ```json
      {
         "invited": {
            "add": ["+8xxxxxxxxxx"],
            "remove": ["+1xxxxxxxxxx", "+91xxxxxxxxxx"]
         },
         "subscribed": {
            "remove": ["+1xxxxxxxxxx", "+91xxxxxxxxxx"]
         },
         "unsubscribed": {
            "remove": ["+1xxxxxxxxxx", "+91xxxxxxxxxx"]
         }
      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for IBM Email.

      ```json
      {
         "invited": {
            "add": ["example1@gmail.com"],
            "remove": []
         },
         "subscribed": {
            "remove": ["example2@gmail.com"]
         },
         "unsubscribed": {
            "remove": ["example3@gmail.com"]
         },
         "reply_to_mail": "example@ibm.com",
         "reply_to_name": "USA news",
         "from_name": "IBM",
         "add_notification_payload": true
      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for Custom Email.

      ```json
      {
         "invited": {
            "add": ["example1@gmail.com"],
            "remove": []
         },
         "subscribed": {
            "remove": ["example2@gmail.com"]
         },
         "unsubscribed": {
            "remove": ["example3@gmail.com"]
         },
         "reply_to_mail": "example@ibm.com",
         "reply_to_name": "USA news",
         "from_name": "IBM",
         "from_email": "test@email.com",
         "add_notification_payload": true,
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724afc58b13",
         "template_id_invitation": "f1ef32fb-b7dd-4405-xxxx-7b6719cee8aa"
      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for Slack for type as `incoming_webhook`.

      ```json
      {
         "attachment_color" : "#FF0000",
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",

      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for Slack for type as `direct_message`.

      ```json
      {
         "channels": [{"id": "D01CFDTYBH", "operation": "add"}, {"id": "D01GHUTYBH", "operation": "remove"}],
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
      }
      ```

   - The following example shows the format of the `SubscriptionUpdateAttributes` object for Service Now.

      ```json
      {
         "assigned_to" : "serviceuser@gmail.com",
         "assignment_group" : "incidentgroup"
      }
      ```

      - The following example shows the format of the `SubscriptionUpdateAttributes` object for Pagerduty/Event Streams.

      ```json
      {
         "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
      }
      ```

### ibmcloud event-notifications tag subscription create
{: #en-cli-tag-subscription-create-command}

- **Action:** Create `Tag-Subscription`.

    [From version 1.0.0]

   ```sh
   ibmcloud event-notifications tags-subscription-create --instance-id INSTANCE-ID --id ID --device-id DEVICE-ID --tag-name TAG-NAME
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for Destination. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--tag-name TAG-NAME` (string)
   :  The offset for paginated results.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `----device-id DEVICE-ID` (string)
   :  Unique identifier of the device.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--instance-id INSTANCE-ID]`  (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

### ibmcloud event-notifications tag subscription delete
{: #en-cli-tag-subscription-delete-command}

- **Action:** Delete `Tag-Subscription`.

    [From version 1.0.0]

   ```sh
   ibmcloud event-notifications tags-subscription-delete --instance-id INSTANCE-ID --id ID --device-id DEVICE-ID --tag-name TAG-NAME
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Unique identifier for Destination. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--tag-name TAG-NAME` (string)
   :  The offset for paginated results.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `----device-id DEVICE-ID` (string)
   :  Unique identifier of the device.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `[--instance-id INSTANCE-ID]`  (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.  

### ibmcloud event-notifications tag subscription list
{: #en-cli-tag-subscription-list-command}

- **Action:** list `Tag-Subscriptions`.

    [From version 1.0.0]

   ```sh
   ibmcloud event-notifications tags-subscription --instance-id INSTANCE-ID --id ID [--device-id DEVICE-ID] [--user-id USER-ID] [--tag-name TAG-NAME] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
   ```
   {: pre}

- **Parameters to provide:**

   `--id ID` (string)
   :  Subscription Tag ID. Required.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `--tag-name TAG-NAME` (string)
   :  The offset for paginated results.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

   `----device-id DEVICE-ID` (string)
   :  Unique identifier of the device.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

   `----user-id USER-ID` (string)
   :  The user identifier for the device registration.

      The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.   

   `--limit LIMIT` (int64)
   :  The page limit for paginated results.

      The maximum value is `100`. The minimum value is `1`.

   `--offset OFFSET` (int64)
   :  The offset for paginated results.

      The minimum value is `0`.

   `--search SEARCH` (string)
   :  The search string for filtering results.

      The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.   

   `[--instance-id INSTANCE-ID]`  (string)
   :  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

      The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.             

## Integrations
{: #en-cli-integration}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} integration.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications Integration --help
```

### ibmcloud event-notifications integration Create
{: #en-cli-integration-create-command}

```sh
ibmcloud event-notifications integration-create --instance-id INSTANCE-ID --type TYPE --metadata METADATA
```

#### Command options
{: #en-cli-integration-options}

`--instance-id` (string)
:  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:  Type of the integration collect_failed_events.

   The maximum length is `50` characters. The minimum length is `1` characters. Allowed values are KMS and hs-crypto.

`--metadata` ([IntegrationCreateAttributes](#en-cli-integration-create-example-schema))
:  Integration schema for update

   Metadata required for integration.

### ibmcloud event-notifications integration replace
{: #en-cli-integration-update-command}

Replace `Integration`.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications Integration replace --instance-id INSTANCE-ID --id ID --type Type --metadata METADATA
```

[From version 1.0.0]

```sh
ibmcloud event-notifications integration-replace --instance-id INSTANCE-ID --id ID --type Type --metadata METADATA
```

- **Examples:**
{: #en-cli-integration-create-example-schema}

   - The following example shows the format of the `IntegrationCreateAttributes` object.

      ```json
      {
         "endpoint": "https://s3.us-west.cloud-object-storage.appdomain.cloud",
         "crn": "crn:v1:bluemix:public:cloud-object-storage:global:xxxxxxx6db359a81a1dde8f44bxxxxxx:xxxxxxxx-1d48-xxxx-xxxx-xxxxxxxxxxxx::",
         "bucket_name": "cloud-object-storage"
      }
      ```

#### Command options
{: #en-cli-integration-replace-options}

`--instance-id` (string)
:  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:  Type of the integration KMS/hs-crypto.

   The maximum length is `50` characters. The minimum length is `1` characters. Allowed values are KMS and hs-crypto.

`--metadata` ([IntegrationReplaceAttributes](#en-cli-integration-example-schema))
:  Integration schema for update

   Metadata required for integration.

`--id` (string)
:  Unique identifier for integration. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

- **Examples:**
{: #en-cli-integration-example-schema}

   - The following example shows the format of the `IntegrationReplaceAttributes` object.

      ```json
      {
         "endpoint" : "https://qa.us-south.kms.test.cloud.ibm.com",
         "crn" : "crn of key protect/hpcs instance",
         "root_key_id" : "root key id"
      }
      ```

### ibmcloud event-notifications integration list
{: #en-cli-integration-list-command}

List all `Integrations`.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications Integration list [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
```

[From version 1.0.0]

```sh
ibmcloud event-notifications integrations [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--instance-id INSTANCE-ID]
```

#### Command options
{: #event-notifications-Integration-list-cli-options}

`--instance-id` (string)
:  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:  Page limit for paginated results.

   The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:  offset for paginated results.

   The minimum value is `0`.

`--search` (string)
:  Search string for filtering results.

   The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

### ibmcloud event-notifications Integration get
{: #en-cli-integration-get-command}

Get specific `Integration`.

[Supported till version 0.2.0]

```sh
ibmcloud event-notifications Integration get --id ID [--instance-id INSTANCE-ID]
```

[From version 1.0.0]

```sh
ibmcloud event-notifications integration --id ID [--instance-id INSTANCE-ID]
```

#### Command options
{: #en-cli-integration-get-options}

`--instance-id` (string)
:  Unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  Unique identifier for integration. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

## Templates
{: #event-notifications-templates-cli}

IBM Cloud Event Notifications Templates.

### `ibmcloud event-notifications template-create`
{: #event-notifications-cli-template-create-command}

Create a new Template.

```sh
ibmcloud event-notifications template-create --instance-id INSTANCE-ID --name NAME --type TYPE [--params PARAMS] [--description DESCRIPTION]
```

#### Command options
{: #event-notifications-template-create-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:   The Message Template. Required.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--type` (string)
:   The type of template. Required.

    The maximum length is `24` characters. The minimum length is `22` characters. The value must match regular expression `/^(smtp_custom.notification|smtp_custom.invitation)$/`.

`--params` ([`TemplateConfig`](#event-notifications-template-create-examples))
:   Payload describing a template configuration. This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--params=@path/to/file.json`.

`--description` (string)
:   The Template description.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--params-body` (string)
:   Template body. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `20000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--params-subject` (string)
:   The template subject. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `1000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

#### Examples
{: #event-notifications-template-create-examples}

- The following example shows the format of the `TemplateConfig` object for Email. The supported type is `smtp_custom.notification|smtp_custom.invitation`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type smtp_custom.notification \
    --params '{"body": "exampleString", "subject": "exampleString"}' \
    --description exampleString
```

- The following example shows the format of the `TemplateConfig` object for Slack. The supported type is `slack.notification`.

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type slack.notification \
    --params '{"body": "ewoJImJsb2NrcyI6IFsKCQl7CgkJCSJ0eXBlIjogInNlY3Rpb24iLAoJCQkidGV4dCI6IHsKCQkJCSJ0eXBlIjogIm1ya2R3biIsCgkJCQkidGV4dCI6ICJOZXcgUGFpZCBUaW1lIE9mZiByZXF1ZXN0IGZyb20gPGV4YW1wbGUuY29tfEZyZWQgRW5yaXF1ZXo+XG5cbjxodHRwczovL2V4YW1wbGUuY29tfFZpZXcgcmVxdWVzdD4iCgkJCX0KCQl9CgldCn0="}' \
    --description exampleString
```

- The following example shows the format of the `TemplateConfig` object for Webhook. The supported type is `webhook.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type webhook.notification \
    --params '{"body": "ewoJImJsb2NrcyI6IFsKCQl7CgkJCSJ0eXBlIjogInNlY3Rpb24iLAoJCQkidGV4dCI6IHsKCQkJCSJ0eXBlIjogIm1ya2R3biIsCgkJCQkidGV4dCI6ICJOZXcgUGFpZCBUaW1lIE9mZiByZXF1ZXN0IGZyb20gPGV4YW1wbGUuY29tfEZyZWQgRW5yaXF1ZXo+XG5cbjxodHRwczovL2V4YW1wbGUuY29tfFZpZXcgcmVxdWVzdD4iCgkJCX0KCQl9CgldCn0="}' \
    --description exampleString
```
- The following example shows the format of the `TemplateConfig` object for Pagerduty. The supported type is `pagerduty.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type pagerduty.notification \
    --params '{"body": "ewogICJwYXlsb2FkIjogewogICAgInN1bW1hcnkiOiAie3sgZGF0YS5hbGVydF9kZWZpbml0aW9uLm5hbWV9fSIsCiAgICAidGltZXN0YW1wIjogInt7dGltZX19IiwKICAgICJzZXZlcml0eSI6ICJpbmZvIiwKICAgICJzb3VyY2UiOiAie3sgc291cmNlIH19IgogIH0sCiAgImRlZHVwX2tleSI6ICJ7eyBpZCB9fSIsCiAge3sjZXF1YWwgZGF0YS5zdGF0dXMgInRyaWdnZXJlZCJ9fQogICJldmVudF9hY3Rpb24iOiAidHJpZ2dlciIKICAge3svZXF1YWx9fQoKICB7eyNlcXVhbCBkYXRhLnN0YXR1cyAicmVzb2x2ZWQifX0KICAiZXZlbnRfYWN0aW9uIjogInJlc29sdmUiCiAge3svZXF1YWx9fQoKICAge3sjZXF1YWwgZGF0YS5zdGF0dXMgImFja25vd2xlZGdlZCJ9fQogICAiZXZlbnRfYWN0aW9uIjogImFja25vd2xlZGdlIgogICB7ey9lcXVhbH19Cn0="}' \
    --description exampleString
```

- The following example shows the format of the `TemplateConfig` object for Event Streams. The supported type is `event_streams.notification`
=======

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type pagerduty.notification \
    --params '{"body": "ewogICJwYXlsb2FkIjogewogICAgInN1bW1hcnkiOiAie3sgZGF0YS5hbGVydF9kZWZpbml0aW9uLm5hbWV9fSIsCiAgICAidGltZXN0YW1wIjogInt7dGltZX19IiwKICAgICJzZXZlcml0eSI6ICJpbmZvIiwKICAgICJzb3VyY2UiOiAie3sgc291cmNlIH19IgogIH0sCiAgImRlZHVwX2tleSI6ICJ7eyBpZCB9fSIsCiAge3sjZXF1YWwgZGF0YS5zdGF0dXMgInRyaWdnZXJlZCJ9fQogICJldmVudF9hY3Rpb24iOiAidHJpZ2dlciIKICAge3svZXF1YWx9fQoKICB7eyNlcXVhbCBkYXRhLnN0YXR1cyAicmVzb2x2ZWQifX0KICAiZXZlbnRfYWN0aW9uIjogInJlc29sdmUiCiAge3svZXF1YWx9fQoKICAge3sjZXF1YWwgZGF0YS5zdGF0dXMgImFja25vd2xlZGdlZCJ9fQogICAiZXZlbnRfYWN0aW9uIjogImFja25vd2xlZGdlIgogICB7ey9lcXVhbH19Cn0="}' \
    --description exampleString
```

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type event_streams.notification \
    --params '{"body": "eyJuYW1lIjoie3tkYXRhLm5hbWV9fSIifQ=="}' \
    --description exampleString
```
{: pre}

### `ibmcloud event-notifications templates`
{: #event-notifications-cli-templates-command}

List all Templates.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud event-notifications templates --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```

#### Command options
{: #event-notifications-templates-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:   Page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   offset for paginated results.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Search string for filtering results.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for templates.

#### Example
{: #event-notifications-templates-examples}

```sh
ibmcloud event-notifications templates \
    --instance-id exampleString \
    --limit 10 \
    --offset 0 \
    --search exampleString
```
{: pre}

### `ibmcloud event-notifications template`
{: #event-notifications-cli-template-command}

Get details of a Template.

```sh
ibmcloud event-notifications template --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-template-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-template-examples}

```sh
ibmcloud event-notifications template \
    --instance-id exampleString \
    --id exampleString
```
{: pre}

### `ibmcloud event-notifications template-replace`
{: #event-notifications-cli-template-update-command}

Update details of a Template.

```sh
ibmcloud event-notifications template-replace --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--type TYPE] [--params PARAMS]
```

#### Command options
{: #event-notifications-template-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--name` (string)
:   Template name.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--description` (string)
:   Template description.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--type` (string)
:   The type of template.

    The maximum length is `24` characters. The minimum length is `22` characters. The value must match regular expression `/^(smtp_custom.notification|smtp_custom.invitation)$/`.

`--params` ([`TemplateConfig`](#event-notifications-template-update-examples))
:   Payload describing a template configuration. This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--params=@path/to/file.json`.

`--params-body` (string)
:   Template body. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `20000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--params-subject` (string)
:   The template subject. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `1000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

#### Examples
{: #event-notifications-template-replace-examples}

```sh
ibmcloud event-notifications template-update \
    --instance-id exampleString \
    --id exampleString \
    --name exampleString \
    --description exampleString \
    --type exampleString \
    --params '{"body": "exampleString", "subject": "exampleString"}'
```
{: pre}

Alternatively, granular options are available for the sub-fields of JSON string options:

```sh
ibmcloud event-notifications template-update \
    --instance-id exampleString \
    --id exampleString \
    --name exampleString \
    --description exampleString \
    --type exampleString \
    --params-body exampleString \
    --params-subject exampleString
```
{: pre}

### `ibmcloud event-notifications template-delete`
{: #event-notifications-cli-template-delete-command}

Delete a Template.

```sh
ibmcloud event-notifications template-delete --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-template-delete-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for Template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-template-delete-examples}

```sh
ibmcloud event-notifications template-delete \
    --instance-id exampleString \
    --id exampleString
```
{: pre}

## SMTP Configurations
{: #event-notifications-s-mtp-configurations-cli}

IBM Cloud Event Notifications SMTP Configurations.

### `ibmcloud event-notifications smtp-configuration-create`
{: #event-notifications-cli-smtp-configuration-create-command}

Create a new SMTP Configuration.

```sh
ibmcloud event-notifications smtp-configuration-create --instance-id INSTANCE-ID --name NAME --domain DOMAIN [--description DESCRIPTION]
```

#### Command options
{: #event-notifications-smtp-configuration-create-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:   The name of SMTP configuration. Required.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--domain` (string)
:   Domain Name. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--description` (string)
:   The description of SMTP configuration.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

#### Example
{: #event-notifications-smtp-configuration-create-examples}

```sh
ibmcloud event-notifications smtp-configuration-create \
    --instance-id=exampleString \
    --name=exampleString \
    --domain=exampleString \
    --description=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-configurations`
{: #event-notifications-cli-smtp-configurations-command}

List all SMTP Configurations.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud event-notifications smtp-configurations --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```

#### Command options
{: #event-notifications-smtp-configurations-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:   Page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   offset for paginated results.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Search string for filtering results.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for smtp-configurations.

#### Example
{: #event-notifications-smtp-configurations-examples}

```sh
ibmcloud event-notifications smtp-configurations \
    --instance-id=exampleString \
    --limit=10 \
    --offset=0 \
    --search=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-user-create`
{: #event-notifications-cli-smtp-user-create-command}

Create a new SMTP User.

```sh
ibmcloud event-notifications smtp-user-create --instance-id INSTANCE-ID --id ID [--description DESCRIPTION]
```

#### Command options
{: #event-notifications-smtp-user-create-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--description` (string)
:   The description of SMTP configuration.

    The maximum length is `250` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

#### Example
{: #event-notifications-smtp-user-create-examples}

```sh
ibmcloud event-notifications smtp-user-create \
    --instance-id=exampleString \
    --id=exampleString \
    --description=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-users`
{: #event-notifications-cli-smtp-users-command}

List all SMTP users.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud event-notifications smtp-users --instance-id INSTANCE-ID --id ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```

#### Command options
{: #event-notifications-smtp-users-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--limit` (int64)
:   Page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   offset for paginated results.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Search string for filtering results.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for smtp-users.

#### Example
{: #event-notifications-smtp-users-examples}

```sh
ibmcloud event-notifications smtp-users \
    --instance-id=exampleString \
    --id=exampleString \
    --limit=10 \
    --offset=0 \
    --search=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-configuration`
{: #event-notifications-cli-smtp-configuration-command}

Get details of a SMTP Configuration.

```sh
ibmcloud event-notifications smtp-configuration --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example

{: #event-notifications-smtp-configuration-examples}

```sh
ibmcloud event-notifications smtp-configuration \
    --instance-id=exampleString \
    --id=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-configuration-update`
{: #event-notifications-cli-smtp-configuration-update-command}

Update details of SMTP.

```sh
ibmcloud event-notifications smtp-configuration-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION]
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--name` (string)
:   SMTP name.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--description` (string)
:   SMTP description.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

#### Example
{: #event-notifications-smtp-configuration-update-examples}

```sh
ibmcloud event-notifications smtp-configuration-update \
    --instance-id=exampleString \
    --id=exampleString \
    --name=exampleString \
    --description=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-configuration-delete`
{: #event-notifications-cli-smtp-configuration-delete-command}

Delete a SMTP Configuration.

```sh
ibmcloud event-notifications smtp-configuration-delete --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-smtp-configuration-delete-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-smtp-configuration-delete-examples}

```sh
ibmcloud event-notifications smtp-configuration-delete \
    --instance-id=exampleString \
    --id=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-user`
{: #event-notifications-cli-smtp-user-command}

Get details of a SMTP User.

```sh
ibmcloud event-notifications smtp-user --instance-id INSTANCE-ID --id ID --user-id USER-ID
```

#### Command options
{: #event-notifications-smtp-user-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--user-id` (string)
:   UserID. Required.

    The maximum length is `256` characters. The minimum length is `5` characters. The value must match regular expression `/.*/`.

#### Example
{: #event-notifications-smtp-user-examples}

```sh
ibmcloud event-notifications smtp-user \
    --instance-id=exampleString \
    --id=exampleString \
    --user-id=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-user-update`
{: #event-notifications-cli-smtp-user-update-command}

Update details of SMTP User.

```sh
ibmcloud event-notifications smtp-user-update --instance-id INSTANCE-ID --id ID --user-id USER-ID [--description DESCRIPTION]
```

#### Command options
{: #event-notifications-smtp-user-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--user-id` (string)
:   UserID. Required.

    The maximum length is `256` characters. The minimum length is `5` characters. The value must match regular expression `/.*/`.

`--description` (string)
:   SMTP user description.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

#### Example
{: #event-notifications-smtp-user-update-examples}

```sh
ibmcloud event-notifications smtp-user-update \
    --instance-id=exampleString \
    --id=exampleString \
    --user-id=exampleString \
    --description=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-user-delete`
{: #event-notifications-cli-smtp-user-delete-command}

Delete a SMTP user.

```sh
ibmcloud event-notifications smtp-user-delete --instance-id INSTANCE-ID --id ID --user-id USER-ID
```

#### Command options
{: #event-notifications-smtp-user-delete-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--user-id` (string)
:   UserID. Required.

    The maximum length is `256` characters. The minimum length is `5` characters. The value must match regular expression `/.*/`.

#### Example
{: #event-notifications-smtp-user-delete-examples}

```sh
ibmcloud event-notifications smtp-user-delete \
    --instance-id=exampleString \
    --id=exampleString \
    --user-id=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-allowed-ips`
{: #event-notifications-cli-smtp-allowed-ips-command}

Get details of a SMTP allowed IPs.

```sh
ibmcloud event-notifications smtp-allowed-ips --instance-id INSTANCE-ID --id ID
```

#### Command options
{: #event-notifications-smtp-allowed-ips-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-smtp-allowed-ips-examples}

```sh
ibmcloud event-notifications smtp-allowed-ips \
    --instance-id=exampleString \
    --id=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-allowed-ips-update`
{: #event-notifications-cli-smtp-allowed-ips-update-command}

Note: The support for legacy allowlisting has been deprecated. The support has been enabled via Context-based-restrictions. For detailed information, please refer here: <https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-smtp-configurations#en-smtp-configurations-cbr>

{: pre}

### `ibmcloud event-notifications verify-smtp-update`
{: #event-notifications-cli-verify-smtp-update-command}

Verify SPF and DKIM records of SMTP.

```sh
ibmcloud event-notifications verify-smtp-update --instance-id INSTANCE-ID --id ID --type TYPE
```

#### Command options
{: #event-notifications-verify-smtp-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--type` (string)
:   SMTP Verification type. Required.

    The maximum length is `20` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

#### Example
{: #event-notifications-verify-smtp-update-examples}

```sh
ibmcloud event-notifications verify-smtp-update \
    --instance-id=exampleString \
    --id=exampleString \
    --type=exampleString
```

{: pre}

## Metrics
{: #event-notifications-metrics-cli}

### `ibmcloud event-notifications metrics`
{: #event-notifications-cli-metrics-command}

Get metrics.

```sh
ibmcloud event-notifications metrics --instance-id INSTANCE-ID --destination-type DESTINATION-TYPE --gte GTE --lte LTE [--id ID] [--email-to EMAIL-TO] [--notification-id NOTIFICATION-ID] [--subject SUBJECT]
```

#### Command options
{: #event-notifications-metrics-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--destination-type` (string)
:   Destination type. Allowed values are [smtp_custom]. Required.

    Allowable values are: `smtp_custom`.

`--gte` (string)
:   GTE (greater than equal), start timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--lte` (string)
:   LTE (less than equal), end timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--id` (string)
:   Unique identifier for Source.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--email-to` (string)
:   Receiver email id.

    The maximum length is `256` characters. The minimum length is `0` characters. The value must match regular expression `/[A-Za-z0-9\\._%+\\-]+@[A-Za-z0-9\\.\\-]+\\.[A-Za-z]{2,}/`.

`--notification-id` (string)
:   Notification Id.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--subject` (string)
:   Email subject.

    The maximum length is `256` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

#### Example
{: #event-notifications-metrics-examples}

```sh
ibmcloud event-notifications metrics \
    --instance-id=exampleString \
    --destination-type=smtp_custom \
    --gte=exampleString \
    --lte=exampleString \
    --id=exampleString \
    --email-to=exampleString \
    --notification-id=exampleString \
    --subject=exampleString
```
{: pre}

## Send Notifications
{: #event-notifications-send-notifications-cli}

This document describes the payload details for sending events using the API sources in Event Notifications. API sources can be used to send events from your backend applications. Event Notifications supports two modes to make HTTP calls. This is adhering to the CloudEvents specification. These modes are Binary Mode and Structured mode. More details here - <https://github.com/cloudevents/spec>. In the Binary Content Mode, the value of the event data is placed into the HTTP request, or response, body as-is, with the datacontenttype attribute value declaring its media type in the HTTP Content-Type header; all other event attributes are mapped to HTTP headers. All the attribute names are prefixed with ce- and added to the header (except for the data and datacontenttype). When mandatory attributes of CloudEvents (specversion, id, type, and source) are passed as part of headers the request is treated as binary mode. Structured Mode. In the Structured Content Mode, event metadata attributes and event data are placed into the HTTP request body. For structured mode, set the Content-Type header to application/cloudevents+json. Mandatory attributes of CloudEvents (specversion, id, type, and source) are required to be part of the request body. In addition, id data is provided as datacontenttype which is mandatory. We only support datacontenttype as \"application/json\".

### `ibmcloud event-notifications send-notifications`
{: #event-notifications-cli-send-notifications-command}

Send Notifications body from the instance. For more information about Event Notifications payload, see [here](/docs/event-notifications?topic=event-notifications-en-spec-payload).

```sh
ibmcloud event-notifications send-notifications --instance-id INSTANCE-ID [--body BODY]
```

#### Command options
{: #event-notifications-send-notifications-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--body` ([`NotificationCreate`](#cli-notification-create-example-schema))
:   Payload describing a notification create request.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--body=@path/to/file.json`.

### NotificationCreate
{: #cli-notification-create-example-schema}

The following example shows the format of the NotificationCreate object.

```json

{
  "specversion" : "1.0",
  "time" : "2019-01-01T12:00:00.000Z",
  "id" : "exampleString",
  "source" : "exampleString",
  "type" : "exampleString",
  "ibmenseverity" : "exampleString",
  "ibmensourceid" : "exampleString",
  "ibmendefaultshort" : "exampleString",
  "ibmendefaultlong" : "exampleString",
  "ibmensubject" : "exampleString",
  "ibmentemplates" : "[\"886f8f4c-8605-47hb-85a1-8682b9377468483\"]",
  "ibmenmailto" : "exampleString",
  "ibmenslackto": "[\"sgjhgsjaS\",\"agjhgsjaS\"]",
  "ibmensmsto" : "exampleString",
  "ibmenmms": {"content": "VBORw0KGgoAAAANSUhEUgAAAFoAAAA4CAYAAAB9lO","content_type": "image/png"},
  "ibmenhtmlbody" : "exampleString",
  "subject" : "exampleString",
  "data" : {
    "anyKey" : "anyValue"
  },
  "datacontenttype" : "application/json",
  "ibmenpushto" : "{
    \"fcm_devices\" : [ \"exampleString\" ],
    \"apns_devices\" : [ \"exampleString\" ],
    \"huawei_devices\" : [ \"exampleString\" ],
    \"safari_devices\" : [ \"exampleString\" ],
    \"chrome_devices\" : [ \"exampleString\" ],
    \"firefox_devices\" : [ \"exampleString\" ],
    \"user_ids\" : [ \"exampleString\" ],
    \"tags\" : [ \"exampleString\" ],
    \"platforms\" : [ \"push_android\" ]
  }",
  "ibmenfcmbody" : "{ }",
  "ibmenapnsbody" : "{ }",
  "ibmenapnsheaders" : "{ }",
  "ibmenchromebody" : "{ }",
  "ibmenchromeheaders" : "{ }",
  "ibmenfirefoxbody" : "{ }",
  "ibmenfirefoxheaders" : "{ }",
  "ibmenhuaweibody" : "{ }",
  "ibmensafaribody" : "{ }"
}
```
{: codeblock}

#### Example
{: #event-notifications-send-notifications-examples}

```sh
ibmcloud event-notifications send-notifications \
    --instance-id=exampleString \
    --body='{"specversion": "1.0", "time": "2019-01-01T12:00:00.000Z", "id": "exampleString", "source": "exampleString", "type": "exampleString", "ibmenseverity": "exampleString", "ibmensourceid": "exampleString", "ibmendefaultshort": "exampleString", "ibmendefaultlong": "exampleString", "ibmensubject": "exampleString", "ibmentemplates": [\"template-id\"], "ibmenmailto": "exampleString","ibmenslackto": "[\"sgjhgsjaS\",\"agjhgsjaS\"]", "ibmensmsto": "exampleString","ibmenmms": "{\"content\": \"VBORw0KGgoAAAANSUhEUgAAAFoAAAA4CAYAAAB9lO\",\"content_type\": \"image/png\"}", "ibmenhtmlbody": "exampleString", "subject": "exampleString", "data": {"anyKey": "anyValue"}, "datacontenttype": "application/json", "ibmenpushto": "{\"fcm_devices\": [\"exampleString\"], \"apns_devices\": [\"exampleString\"], \"huawei_devices\": [\"exampleString\"], \"safari_devices\": [\"exampleString\"], \"chrome_devices\": [\"exampleString\"], \"firefox_devices\": [\"exampleString\"], \"user_ids\": [\"exampleString\"], \"tags\": [\"exampleString\"], \"platforms\": [\"push_android\"]}", "ibmenfcmbody": "{}", "ibmenapnsbody": "{}", "ibmenapnsheaders": "{}", "ibmenchromebody": "{}", "ibmenchromeheaders": "{}", "ibmenfirefoxbody": "{}", "ibmenfirefoxheaders": "{}", "ibmenhuaweibody": "{}", "ibmensafaribody": "{}"}'
```
{: pre}

#### Additional properties that can be configured for the iOS notification
{: #en-cli-send-notifications-command-addprops-ios}

|  Property  |  Property type  |  Description  |
|-------------|-------------|-------------|
| `badge` | integer | The number to display as the badge of the application icon. |
| `interactive_category` | string | The category identifier to be used for the interactive push notifications. |
| `ios_action_key` | string |The title for the Action key. |
| `payload` | JSON object | Custom JSON payload that is sent as part of the notification message. |
| `sound` | string | The name of the sound file in the application bundle. The sound of this file is played as an alert. |
| `title_loc_key` | string | The key to a title string in the Localizable.strings file for the current localization. The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the titleLocArgs array. |
| `loc_key` | string | A key to an alert-message string in a Localizabl.strings file for the current localization (which is set by the user's language preference). The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the locArgs array. |
| `launch_image` | string | The file name of an image file in the app bundle, with or without the file name extension. The image is used as the launch image when users tap the action button or move the action slider. |
| `title_loc_args` | string | Variable string values to appear in place of the format specifiers in title-loc-key. |
| `loc_args` | string | Variable string values to appear in place of the format specifiers in locKey. | title string The title of Rich Push notifications (Supported only on iOS 10 and above).|
| `title` | string | The title of Rich Push notifications (Supported only on iOS 10 and above). |
| `subtitle` | string | The subtitle of the Rich notifications (Supported only on iOS 10 and above). |
| `body` | string | The body for IOS notifications. |
| `attachment_url` | string | The link to the iOS notifications media (video, audio, GIF, images - Supported only on iOS 10 and above). |
| `type` | string | Allowable values: DEFAULT, MIXED, SILENT. |
| `apns_collapse_id` | string | Multiple notifications with the same collapse identifier are displayed to the user as a single notification. |
| `apns_thread_id` | string | An app-specific identifier for grouping related notifications. This value corresponds to the threadIdentifier property in the UNNotificationContent object. |
| `apns_group_summary_arg` | string | The string the notification adds to the category’s summary format string. |
| `apns_group_summary_arg_count` | integer | The number of items the notification adds to the category’s summary format string. |
{: caption="iOS platform settings" caption-side="bottom"}

#### Additional properties that can be configured for the FCM notification
{: #en-cli-send-notifications-command-addprops-fcm}

|  Property  |  Property type  |  Description  |
|-------------|-------------|-------------|
| `icon` | string | Specify the name of the icon to be displayed for the notification. Make sure that the icon is already packaged with the client application. |
| `delay_while_idle` | Boolean | When set to true, this parameter indicates that the message should not be sent until the device becomes active. |
| `sync` | Boolean | Device group messaging makes it possible for every app instance in a group to reflect the latest messaging state. |
| `visibility` | string | private or public - Visibility of this notification, which affects how and when the notifications are revealed on a secure locked screen. |
| `redact` | string | Content that is specified shows up on a secure locked screen on the device when visibility is set to Private. |
| `payload` | JSON object | Custom JSON payload that is sent as part of the notification message.|
| `priority` | string | A string value that indicates the priority of this notification. Allowed values are 'max', 'high', 'default', 'low' and 'min'. High/Max priority notifications along with 'sound' field might be used for Heads up notification in Android 5.0 or higher.sampleval='low'. |
| `sound` | string| The sound file (on device) that will be attempted to play when the notification arrives on the device. |
| `time_to_live` | integer | Specifies how long (in seconds) the message should be kept in GCM storage if the device is offline.
| `lights` |  | Sets the notification LED color on receiving push notification. |
| `ledArgb` | string | The color of the LED. The hardware does its best approximation. |
| `ledOnMs` | integer | The time in milliseconds for the LED to be on while it's flashing. The hardware does its best approximation. |
| `ledOffMs` | string | The time in milliseconds for the LED to be off while it's flashing. The hardware does its best approximation. |
| `android_title` | string | The title of Rich Push notifications. |
| `group_id` | string | Set this notification to be part of a group of notifications sharing the same key. Grouped notifications might display in a cluster or stack on devices that support such rendering. |
| `style` |  | Options to specify for Android expandable notifications. The types of expandable notifications are picture_notification, bigtext_notification, inbox_notification. |
| `type` | string | Specifies the type of expandable notifications. The possible values are bigtext_notification, picture_notification, inbox_notification.|
| `title` | string | Specifies the title of the notification. The title is displayed when the notification is expanded. Title must be specified for all three expandable notifications. |
| `type` | string | Allowed values: DEFAULT, SILENT. |
| `alert` | string | The alert value of Notification. |
{: caption="Android platform settings" caption-side="bottom"}

## CLI version history
{: #en-cli-version-history}

Find a summary of changes for each version of {{site.data.keyword.en_short}} plug-in. Keep your CLI up to date so that you can use all of the available commands and their options.
{: shortdesc}

The CLI Plugin versions from 0.0.5 to 1.0.0 is deprecated.
{: note}

| Version | Release date | Changes |
|------------|--------------|---------|
| 1.0.1 | 17 July 2023 | Support for Huawei Destination and New CLI Support. |
| 1.1.0 | 5 October 2023 | Support for Custom Email. |
| 1.2.0 | 9 October 2023 | Support for Email Templates. |
| 1.3.0 | 1 December 2023 | {{site.data.keyword.cos_full_notm}} integration supported. |
| 1.4.0 | 14 March 2024 | Code engine destination configuration support for job and application. |
| 1.5.0 | 10 May 2024 | Support for SMTP Configuration and Slack Templates. |
| 1.6.0 | 1 August 2024 | CF destination deprecated and MMS supported. |
| 1.7.0 | 9 August 2024 | Support for metrics and removed support for SMTP allowed IPs from SMTP configuration.|
| 1.8.0 | 9 September 2024 | Support for Slack DM destination. |
| 1.9.0 | 11 October 2024 | Support for Webhook templates. |
| 1.10.0 | 4 November 2024 | Removed support for Cloud Functions |
| 1.11.0 | 7 January 2025 | Support for Periodic Timer |
| 1.12.0 | 27 February 2025 | Support for Pagerduty template |
| 1.13.0 | 6 March 2025 | Support for {{site.data.keyword.messagehub}} destination, subscription and Templates
{: caption="Changes in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} CLI" caption-side="bottom"}
