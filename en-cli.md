---

copyright:
  years: 2021, 2026
lastupdated: "2026-09-21"

keywords: event notifications CLI plug-in, CLI reference, en cli reference, event notifications cli reference, event notifications, command line reference

subcollection: event-notifications

content-type: cli-docs

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_short}} CLI reference
{: #event-notifications-cli}

To work with {{site.data.keyword.en_short}} by using the command-line interface (CLI) you can install the {{site.data.keyword.en_short}} CLI plug-in from the {{site.data.keyword.cloud_notm}} plug-in repository. The plug-in is designed to extend the capabilities that are offered by the {{site.data.keyword.cloud_notm}} CLI.
{: shortdesc}

## Prerequisites
{: #en-cli-prereq}

- An [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/).
- An instance of [{{site.data.keyword.en_short}}](https://cloud.ibm.com/catalog/services/event-notifications).
- The [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli) installed on your local system. For help working with the {{site.data.keyword.cloud_notm}} CLI, checkout the [reference card](https://cloud.ibm.com/media/docs/downloads/IBM%20Cloud%20CLI%20quick%20reference.pdf).

You are notified when you log into the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started){: external} when updates are available. Be sure to keep your CLI up-to-date so that you have access to any new commands and flags that are available for the {{site.data.keyword.en_short}} CLI plug-in.
{: tip}


## Install the {{site.data.keyword.en_short}} CLI
{: #en-cli-install}

Install the {{site.data.keyword.en_short}} CLI plug-in by using the `plugin install` command.

```sh
ibmcloud plugin install event-notifications
```
{: pre}

Versions of the plugin before 1.15.2 are deprecated.
{: note}

## {{site.data.keyword.en_short}} CLI commands
{: #en-cli-commands}

The `init` command is deprecated and will be removed in a future release.
{: note}

### `ibmcloud event-notifications en-list`
{: #en-cli-list-command}

Lists the instances in the set target region. You can retrieve your instance GUID from the listed instances.

```sh
ibmcloud event-notifications en-list
```
{: pre}

#### Example
{: #en-cli-list-example}

```sh
ibmcloud event-notifications en-list
```
{: pre}

## Set a target region
{: #en-cli-region}

Set the region in which you want to work by using the `ibmcloud target` command.

```sh
ibmcloud target -r REGION
```
{: pre}

Alternatively, you can export a regional endpoint via the variable `IBMCLOUD_EN_ENDPOINT` as shown in the following example.

```sh
export IBMCLOUD_EN_ENDPOINT= https://au-syd.event-notifications.cloud.ibm.com/event-notifications
```
{: codeblock}

To set the regional endpoint as either public or private, see the following options:

- Available public endpoints:

   - **Dallas:** `https://us-south.event-notifications.cloud.ibm.com/event-notifications`
   - **London:** `https://eu-gb.event-notifications.cloud.ibm.com/event-notifications`
   - **Sydney:** `https://au-syd.event-notifications.cloud.ibm.com/event-notifications`
   - **Frankfurt:** `https://eu-de.event-notifications.cloud.ibm.com/event-notifications`
   - **Madrid:** `https://eu-es.event-notifications.cloud.ibm.com/event-notifications`
   - **Osaka:** `https://jp-osa.event-notifications.cloud.ibm.com/event-notifications`
   - **Tokyo:** `https://jp-tok.event-notifications.cloud.ibm.com/event-notifications`
   - **Toronto:** `https://ca-tor.event-notifications.cloud.ibm.com/event-notifications`
   - **Sao Paulo:** `https://br-sao.event-notifications.cloud.ibm.com/event-notifications`
   - **Montreal:** `https://ca-mon.event-notifications.cloud.ibm.com/event-notifications`
   - **Washington DC:** `https://us-east.event-notifications.cloud.ibm.com/event-notifications`
   - **Chennai:** `https://in-che.event-notifications.cloud.ibm.com/event-notifications`
   - **Mumbai:** `https://in-mum.event-notifications.cloud.ibm.com/event-notifications`

- Available private endpoints:

   - **Dallas:** `https://private.us-south.event-notifications.cloud.ibm.com/event-notifications`
   - **London:** `https://private.eu-gb.event-notifications.cloud.ibm.com/event-notifications`
   - **Sydney:** `https://private.au-syd.event-notifications.cloud.ibm.com/event-notifications`
   - **Frankfurt:** `https://private.eu-de.event-notifications.cloud.ibm.com/event-notifications`
   - **Madrid:** `https://private.eu-es.event-notifications.cloud.ibm.com/event-notifications`
   - **Osaka:** `https://private.jp-osa.event-notifications.cloud.ibm.com/event-notifications`
   - **Tokyo:** `https://private.jp-tok.event-notifications.cloud.ibm.com/event-notifications`
   - **Toronto:** `https://private.ca-tor.event-notifications.cloud.ibm.com/event-notifications`
   - **Sao Paulo:** `https://private.br-sao.event-notifications.cloud.ibm.com/event-notifications`
   - **Montreal:** `https://private.ca-mon.event-notifications.cloud.ibm.com/event-notifications`
   - **Washington DC:** `https://private.us-east.event-notifications.cloud.ibm.com/event-notifications`
   - **Chennai:** `https://private.in-che.event-notifications.cloud.ibm.com/event-notifications`
   - **Mumbai:** `https://private.in-mum.event-notifications.cloud.ibm.com/event-notifications`

You can also export the **EVENT_NOTIFICATIONS_API_KEY** variable to configure the API key  or the service credentials API key for your {{site.data.keyword.en_short}} instance.

## Sources
{: #en-cli-source}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} source.

### `ibmcloud event-notifications source-create`
{: #en-cli-source-create-command}

Create a source that configures a service to produce events that {{site.data.keyword.en_short}} can consume. You must provide the ID of the {{site.data.keyword.en_short}} instance for which you configure the source. For more information about source types and registering them with {{site.data.keyword.en_short}}, see [Adding an Event Notifications source](/docs/event-notifications?topic=event-notifications-en-add-source).

The CLI currently supports creating API sources only.
{: note}


```sh
ibmcloud event-notifications source-create --instance-id INSTANCE-ID --name NAME [--description DESCRIPTION] --enabled ENABLED [--store-notifications STORE-NOTIFICATIONS]
```
{: pre}

Both `source-create` and `sources-create` are supported. Use `source-create` for consistency with other commands.
{: note}


#### Command options
{: #command-options-source-create}

`--instance-id` (string)
:  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name NAME` (string)
:  The name to be provided for API source. Required.

   The default value is ` `. The maximum length is `255` characters. The minimum length is `1` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.


`--description` (string)
:  The description of the API source.

   The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--enabled` (boolean)
:  Enable or disable the source. Required. Set to `true` to enable the source.

`--store-notifications` (boolean)
:  Store notifications. Set to `true` to store notifications so you can view the payload of incoming events for troubleshooting purposes.


#### Example
{: #example-source-create}

```sh
ibmcloud event-notifications source-create \
   --instance-id=exampleString \
   --name=exampleString \
   --description=exampleString \
   --enabled=true \
   --store-notifications=false
```
{: pre}

### `ibmcloud event-notifications source-update`
{: #en-cli-source-update-command}

Update source parameters by using the source ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the source is configured.


```sh
ibmcloud event-notifications source-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--enabled ENABLED] [--store-notifications STORE-NOTIFICATIONS]
```
{: pre}

#### Command options
{: #command-options-source-update}


`--instance-id` (string)
:  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier of the source. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--name` (string)
:  The updated name for the API source.

   The default value is ` `. The maximum length is `255` characters. The minimum length is `1` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--description` (string)
:  The updated description for the API source.

   The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--enabled` (boolean)
:  Enable or disable the source.

   The value is set to true to enable the source and false to disable the source.

`--store-notifications` (boolean)
:  Store notifications. You can view the payload of incoming events for troubleshooting purposes.

   The default value is `false`.

#### Example
{: #example-source-update}

```sh
ibmcloud event-notifications source-update \
   --instance-id=exampleString \
   --id=exampleString \
   --name=exampleString \
   --description=exampleString \
   --enabled=true \
   --store-notifications=false
```
{: pre}

### `ibmcloud event-notifications sources`
{: #en-cli-source-list-command}

List all of the sources in a specified instance.

```sh
ibmcloud event-notifications sources --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--all-pages]
```
{: pre}

#### Command options
{: #command-options-sources}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:  The page limit for paginated results.

   The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:  The offset for paginated results.

   The minimum value is `0`.

`--search` (string)
:  The search string for filtering results.

   The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the source collection.


#### Example
{: #example-sources}

```sh
ibmcloud event-notifications sources \
  --instance-id=exampleString \
  --limit=10 \
  --offset=0 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications source`
{: #en-cli-source-get-command}

Get the details of a specific source.

```sh
ibmcloud event-notifications source --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #command-options-source}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the source. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

#### Example
{: #example-source}

```sh
ibmcloud event-notifications source \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications source-delete`
{: #en-cli-source-delete-command}

Delete a source.

```sh
ibmcloud event-notifications source-delete  --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #command-options-source-delete}

`--id` (string)
:  Unique identifier for source. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--instance-id` (string)
:  The unique identifier for {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--force`
:  Bypass the confirmation prompt and force the deletion of the resource.

#### Example
{: #example-source-delete}

```sh
ibmcloud event-notifications source-delete \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

## Destinations
{: #en-cli-destination}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} destination.

### `ibmcloud event-notifications destination-create`
{: #en-cli-destination-create}

Create a destination to serve as a delivery target for a notification. A destination can be configured to deliver notifications to a human user or to an automated service.

```sh
ibmcloud event-notifications destination-create --instance-id INSTANCE-ID --name NAME --type TYPE [--description DESCRIPTION] [--collect-failed-events COLLECT-FAILED-EVENTS] [--config CONFIG] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--icon16x16 ICON16X16] [--icon16x16-content-type ICON16X16-CONTENT-TYPE] [--icon16x162x ICON16X162X] [--icon16x162x-content-type ICON16X162X-CONTENT-TYPE] [--icon32x32 ICON32X32] [--icon32x32-content-type ICON32X32-CONTENT-TYPE] [--icon32x322x ICON32X322X] [--icon32x322x-content-type ICON32X322X-CONTENT-TYPE] [--icon128x128 ICON128X128] [--icon128x128-content-type ICON128X128-CONTENT-TYPE] [--icon128x1282x ICON128X1282X] [--icon128x1282x-content-type ICON128X1282X-CONTENT-TYPE]
```
{: pre}

#### Command options
{: #command-options-destination-create}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:  The name of the destination. Required.

   The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--type` (string)
:  The type of the destination. Destinations for human users: `smtp_ibm`, `sms_ibm`, `smtp_custom`, `sms_custom`, `event_streams`, `msteams`, `pagerduty`, `push_android`, `push_chrome`, `push_firefox`, `push_huawei`, `push_ios`, `push_safari`, `servicenow`, `slack`. Destinations for services: `ibmce`, `ibmcos`, `webhook`. Required.

   The minimum length is `1` character.

`--description` (string)
:  The description of the destination.

   The default value is ` `. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--collect-failed-events` (boolean)
:  Set to `true` to collect failed events in a Cloud Object Storage bucket. To collect failed events, enable Cloud Object Storage integration for this instance. The default value is `false`.

`--config` ([`DestinationConfig` examples](#en-cli-destination-config-example-schema))
:  The configuration for the destination. If you create a destination without `--config`, the destination is created but does not function until you configure it.

`--certificate` (string)
:  The certificate file path for APNs or iOS push destinations. Accepts p8 and p12 certificate files.

`--certificate-content-type` (string)
:  The content type of the certificate for iOS destinations. Allowed values are `p8` and `p12`.

`--icon16x16` (string)
:  The file path for the Safari icon 16x16. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x16-content-type` (string)
:  The content type of the Safari icon 16x16.

`--icon16x162x` (string)
:  The file path for the Safari icon 16x16@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x162x-content-type` (string)
:  The content type of the Safari icon 16x16@2x.

`--icon32x32` (string)
:  The file path for the Safari icon 32x32. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x32-content-type` (string)
:  The content type of the Safari icon 32x32.

`--icon32x322x` (string)
:  The file path for the Safari icon 32x32@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x322x-content-type` (string)
:  The content type of the Safari icon 32x32@2x.

`--icon128x128` (string)
:  The file path for the Safari icon 128x128. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x128-content-type` (string)
:  The content type of the Safari icon 128x128.

`--icon128x1282x` (string)
:  The file path for the Safari icon 128x128@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x1282x-content-type` (string)
:  The content type of the Safari icon 128x128@2x.

Cloud Functions is no longer supported as a destination.
{: deprecated}

#### Examples
{: #en-cli-destination-config-example-schema}

```sh
ibmcloud event-notifications destination-create \
  --instance-id=exampleString \
  --name=exampleString \
  --type=webhook \
  --description=exampleString \
  --collect-failed-events=false \
  --config='{"params": {"domain": "exampleString", "dkim": {"public_key": "exampleString", "selector": "exampleString", "verification": "exampleString"}, "spf": {"txt_name": "exampleString", "txt_value": "exampleString", "verification": "exampleString"}}}' \
  --certificate=tempdir/test-file.txt \
  --certificate-content-type=exampleString \
  --icon16x16=tempdir/test-file.txt \
  --icon16x16-content-type=exampleString \
  --icon16x162x=tempdir/test-file.txt \
  --icon16x162x-content-type=exampleString \
  --icon32x32=tempdir/test-file.txt \
  --icon32x32-content-type=exampleString \
  --icon32x322x=tempdir/test-file.txt \
  --icon32x322x-content-type=exampleString \
  --icon128x128=tempdir/test-file.txt \
  --icon128x128-content-type=exampleString \
  --icon128x1282x=tempdir/test-file.txt \
  --icon128x1282x-content-type=exampleString
```
{: pre}

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
   {: pre}


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
   {: pre}

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
   {: pre}

- The following example shows format of the `DestinationConfig` object for Firefox destination(push_firefox). Set `pre_prod` Boolean parameter to *true* to configure destination as pre-production destination else set the value as *false*.

   ```json
   {
      "params" : {
         "website_url" : "https://testwebsite.com",
         "pre_prod" : "true" // Set to true in case of configuring Destination as pre-prod Destination (pre_prod destination can only be configured for Standard plan)
      }
   }
   ```
   {: pre}

- The following example shows format of the `DestinationConfig` object for Slack destination(slack) with type as incoming_webhook.

   ```json
   {
      "params" : {
         "type" : "incoming_webhook",
         "url" : "https://hooks.slack.com/services/G0gyhsush/TYodsjhs/GHTbfidsimkk"
      }
   }
   ```
   {: pre}

- The following example shows format of the `DestinationConfig` object for Slack destination(slack) with type as direct_message.

   ```json
   {
      "params" : {
         "type" : "direct_message",
         "token" : "vhdwvecwefwefewivcweivcwiwiciwcvwicwec"
      }
   }
   ```
   {: pre}

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
   {: pre}

- The following example shows format of the `DestinationConfig` object for MS Teams(msteams) destination.

   ```json
   {
      "params" : {
         "url" : "https://xyz.webhook.office.com"
      }
   }
   ```
   {: pre}

- The following example shows format of the `DestinationConfig` object for PagerDuty(pagerduty) destination.

   It is recommended to use only the Routing key while creating the destination. The API key is deprecated and will not available for use in the future.
   {: attention}

   ```json
   {
      "params" : {
         "routing_key" : "routingkeytoconnecttoPD",
         "api_key" : "cffunctionnamespaceserviceidapikey"
      }
   }
   ```
   {: pre}


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
   {: pre}

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
   {: pre}


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
   {: pre}

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
   {: pre}

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
   {: pre}


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
   {: pre}


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
   {: pre}

- The following example shows the format of the `DestinationConfig` object for Custom Email(smtp_custom) destination. In case of Custom Email Sandbox(smtp_custom_sandbox) destination, Destination Configuration params are not required.

   Process To do the Custom Domain Configuration and Verification: https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-destinations-custom-email#en-destinations-custom-email-verify

   ```json
   {
      "params" : {
         "domain": "mailx.com"
      }
   }
   ```
   {: pre}

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
   {: pre}

- The following example shows the format of the `DestinationConfig` object for {{site.data.keyword.appconfig_short}}(app_configuration) destination.

   ```json
   {
      "params" : {
         "type": "features",
         "crn": "crn:v1:bluemix:public:apprapp:us-south:a/4a74f2c31f554afc88156b73a1d577c6:dbxxxx93-0xxa-4xx5-axcf-c2faxxxd::",
         "environment_id": "stage",
         "feature_id": "test"
      }
   }
   ```
   {: pre}

   A custom SMS destination can be created without `DestinationConfig`, but it will not function until the required personalized numbers are explicitly requested and configured. To request personalized numbers, see [Custom SMS personalized numbers](/docs/event-notifications?topic=event-notifications-en-destinations-sms-custom#en-destinations-sms-custom-numbers).
   {: note}

### `ibmcloud event-notifications destinations`
{: #en-cli-destinations-command}

List all destinations for an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications destinations --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--all-pages]
```
{: pre}

#### Command options
{: #command-options-destinations}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:  The page limit for paginated results.

   The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:  The offset for paginated results.

   The minimum value is `0`.

`--search` (string)
:  The search string for filtering results.

   The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the destination collection.

#### Example
{: #en-cli-destinations-example}

```sh
ibmcloud event-notifications destinations \
  --instance-id=exampleString \
  --limit=10 \
  --offset=0 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications destination`
{: #en-cli-destination-command}

Get the details of a destination by using its ID.

```sh
ibmcloud event-notifications destination --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #command-options-destination}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the destination. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

#### Example
{: #en-cli-destination-example}

```sh
ibmcloud event-notifications destination \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications destination-update`
{: #en-cli-destination-update-command}

Update destination parameters by using the destination ID.

```sh
ibmcloud event-notifications destination-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--collect-failed-events COLLECT-FAILED-EVENTS] [--config CONFIG] [--certificate CERTIFICATE] [--certificate-content-type CERTIFICATE-CONTENT-TYPE] [--icon16x16 ICON16X16] [--icon16x16-content-type ICON16X16-CONTENT-TYPE] [--icon16x162x ICON16X162X] [--icon16x162x-content-type ICON16X162X-CONTENT-TYPE] [--icon32x32 ICON32X32] [--icon32x32-content-type ICON32X32-CONTENT-TYPE] [--icon32x322x ICON32X322X] [--icon32x322x-content-type ICON32X322X-CONTENT-TYPE] [--icon128x128 ICON128X128] [--icon128x128-content-type ICON128X128-CONTENT-TYPE] [--icon128x1282x ICON128X1282X] [--icon128x1282x-content-type ICON128X1282X-CONTENT-TYPE]
```
{: pre}

#### Command options
{: #command-options-destination-update}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the destination. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:  The updated name of the destination.

   The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--description` (string)
:  The updated description of the destination.

   The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--collect-failed-events` (boolean)
:  Set to `true` to collect failed events in a Cloud Object Storage bucket. The default value is `false`.

`--config` ([`DestinationConfig`](#en-cli-destination-config-example-schema))
:  The updated configuration for the destination.

   Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--config=@path/to/file.json`.

`--certificate` (string)
:  The certificate file path for APNs or iOS push destinations. Accepts p8 and p12 certificate files.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--certificate-content-type` (string)
:  The content type of the certificate for iOS destinations. Allowed values are `p8` and `p12`.

`--icon16x16` (string)
:  The file path for the Safari icon 16x16. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x16-content-type` (string)
:  The content type of the Safari icon 16x16.

`--icon16x162x` (string)
:  The file path for the Safari icon 16x16@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon16x162x-content-type` (string)
:  The content type of the Safari icon 16x16@2x.

`--icon32x32` (string)
:  The file path for the Safari icon 32x32. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x32-content-type` (string)
:  The content type of the Safari icon 32x32.

`--icon32x322x` (string)
:  The file path for the Safari icon 32x32@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon32x322x-content-type` (string)
:  The content type of the Safari icon 32x32@2x.

`--icon128x128` (string)
:  The file path for the Safari icon 128x128. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x128-content-type` (string)
:  The content type of the Safari icon 128x128.

`--icon128x1282x` (string)
:  The file path for the Safari icon 128x128@2x. For `push_safari` destinations.

   The maximum length is `5000` characters. The minimum length is `1` character.

`--icon128x1282x-content-type` (string)
:  The content type of the Safari icon 128x128@2x.

#### Example
{: #en-cli-destination-update-example}

```sh
ibmcloud event-notifications destination-update \
  --instance-id=exampleString \
  --id=exampleString \
  --name=exampleString \
  --description=exampleString \
  --collect-failed-events=false \
  --config='{"params": {"domain": "exampleString", "dkim": {"public_key": "exampleString", "selector": "exampleString", "verification": "exampleString"}, "spf": {"txt_name": "exampleString", "txt_value": "exampleString", "verification": "exampleString"}}}' \
  --certificate=tempdir/test-file.txt \
  --certificate-content-type=exampleString \
  --icon16x16=tempdir/test-file.txt \
  --icon16x16-content-type=exampleString \
  --icon16x162x=tempdir/test-file.txt \
  --icon16x162x-content-type=exampleString \
  --icon32x32=tempdir/test-file.txt \
  --icon32x32-content-type=exampleString \
  --icon32x322x=tempdir/test-file.txt \
  --icon32x322x-content-type=exampleString \
  --icon128x128=tempdir/test-file.txt \
  --icon128x128-content-type=exampleString \
  --icon128x1282x=tempdir/test-file.txt \
  --icon128x1282x-content-type=exampleString
```
{: pre}

### `ibmcloud event-notifications destination-delete`
{: #en-cli-destination-delete-command}

Delete a destination by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the destination is configured.

```sh
ibmcloud event-notifications destination-delete --instance-id INSTANCE-ID --id ID [--force]
```
{: pre}

#### Command options
{: #command-options-destination-delete}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the destination. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--force` (boolean)
:  Force the command to run.

#### Example
{: #en-cli-destination-delete-example}

```sh
ibmcloud event-notifications destination-delete \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications enabled-countries`
{: #event-notifications-cli-enabled-countries-command}

Get the enabled country details of an SMS destination by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the destination is configured.

```sh
ibmcloud event-notifications enabled-countries --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-enabled-countries-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the SMS destination. Required.

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

Test a destination configuration by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the destination is configured. For the list of supported destinations, see [Testing a destination](/docs/event-notifications?topic=event-notifications-en-test-destination).

```sh
ibmcloud event-notifications test-destination --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-test-destination-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the destination. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

#### Example
{: #event-notifications-test-destination-examples}

```sh
ibmcloud event-notifications test-destination \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications sandbox-destination-update`
{: #event-notifications-cli-sandbox-destination-update-command}

Upgrade a sandbox email destination to production with a custom domain.

```sh
ibmcloud event-notifications sandbox-destination-update --instance-id INSTANCE-ID --id ID --domain DOMAIN
```
{: pre}

#### Command options
{: #event-notifications-sandbox-destination-update-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   The unique identifier for the destination. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--domain` (string)
:   The email domain. Required.

    The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

#### Example
{: #event-notifications-sandbox-destination-update-examples}

```sh
ibmcloud event-notifications sandbox-destination-update \
    --instance-id=exampleString \
    --id=exampleString \
    --domain=exampleString
```
{: pre}

### `ibmcloud event-notifications verify-destination-update`
{: #event-notifications-cli-verify-destination-update-command}

Verify the SPF and DKIM records of a custom domain.

```sh
ibmcloud event-notifications verify-destination-update --instance-id INSTANCE-ID --id ID --type TYPE
```
{: pre}

#### Command options
{: #event-notifications-verify-destination-update-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the destination. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:  The verification type for a custom domain email destination. Allowed values are `spf` and `dkim`. Required.

   The maximum length is `20` characters. The minimum length is `1` character. The value must match regular expression `/[a-z]/`.

#### Example
{: #event-notifications-verify-destination-update-examples}

```sh
ibmcloud event-notifications verify-destination-update \
  --instance-id=exampleString \
  --id=exampleString \
  --type=exampleString
```
{: pre}

## Topics
{: #en-cli-topic}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} topic.

### `ibmcloud event-notifications topic-create`
{: #en-cli-topic-create-command}

Create a topic to receive events from sources and deliver notifications to subscribed destinations. A topic can connect to multiple sources. To create a topic, you must provide the ID of the {{site.data.keyword.en_short}} instance.

For more information, see [Creating a topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic).

```sh
ibmcloud event-notifications topic-create --instance-id INSTANCE-ID --name NAME [--description DESCRIPTION] [--sources SOURCES]
```
{: pre}

#### Command options
{: #command-options-topic-create}

`--instance-id INSTANCE-ID` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name NAME` (string)
:  The name of the topic. Required.

   The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--description DESCRIPTION` (string)
:  The description of the topic.

   The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--sources SOURCES` ([TopicCreateSourcesItem[]](#en-cli-topic-example-schema))
:  The source and filter configuration to associate with the topic. See [source configuration examples](#en-cli-topic-example-schema).

#### Example
{: #en-cli-topic-example-schema}

```sh
ibmcloud event-notifications topic-create \
  --instance-id=exampleString \
  --name=exampleString \
  --description=exampleString \
  --sources='[{"id": "e7c3b3ee-78d9-4e02-95c3-c001a05e6ea5:api", "rules": [{"enabled": true, "event_type_filter": "$.notification_event_info.event_type == \'cert_manager\'", "notification_filter": "$.notification.findings[0].severity == \'MODERATE\'"}]}]'
```
{: pre}

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
               "event_type_filter": "$.notification_event_info.event_type == \'cert_manager\'",
               "notification_filter" : "$.notification.findings[0].severity == \'MODERATE\'",
               "rule_id" : "exampleString"
            }
         ]
      }
   ]
   ```

### `ibmcloud event-notifications topics`
{: #en-cli-topics-command}

List all topics that are created for an {{site.data.keyword.en_short}} instance. You must provide the ID of the instance.

```sh
ibmcloud event-notifications topics --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--all-pages]
```
{: pre}

#### Command options
{: #command-options-topics}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:  The page limit for paginated results.

   The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:  The offset for paginated results.

   The minimum value is `0`.

`--search` (string)
:  The search string for filtering results.

   The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the topic collection.

#### Example
{: #en-cli-topics-example}

```sh
ibmcloud event-notifications topics \
  --instance-id=exampleString \
  --limit=10 \
  --offset=0 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications topic`
{: #en-cli-topic-command}

Get the details of a topic by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the topic is configured.

```sh
ibmcloud event-notifications topic --instance-id INSTANCE-ID --id ID [--include INCLUDE]
```
{: pre}

#### Command options
{: #command-options-topic}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the topic. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--include` (string)
:  Include subtopics.

   The default value is ``. The maximum length is `20` characters. The minimum length is `0` characters. The value must match regular expression `/[a-z]/`.

#### Example
{: #en-cli-topic-example}

```sh
ibmcloud event-notifications topic \
  --instance-id=exampleString \
  --id=exampleString \
  --include=exampleString
```
{: pre}

### `ibmcloud event-notifications topic-update`
{: #en-cli-topic-update-command}

Update the details of a topic by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the topic is configured.


```sh
ibmcloud event-notifications topic-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--sources SOURCES]
```
{: pre}

You can use `topic-replace` as an alias for `topic-update`. The `topic-replace` command is deprecated and will be removed in a future release.
{: note}


#### Command options
{: #command-options-topic-update}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the topic. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--name` (string)
:  The updated name of the topic.

   The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--description` (string)
:  The updated description of the topic.

   The default value is ``. The maximum length is `255` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*()]*/`.

`--sources` ([TopicUpdateSourcesItem[]](#en-cli-topic-example-schema))
:  The updated source details and filters. See [source configuration examples](#en-cli-topic-example-schema).

This option adds only new sources. Sources that are already attached to the topic cannot be replaced or updated. To modify source filters, remove the source from the topic and add it again with the new filter configuration.
{: important}

#### Example
{: #en-cli-topic-update-example}

```sh
ibmcloud event-notifications topic-update \
  --instance-id=exampleString \
  --id=exampleString \
  --name=exampleString \
  --description=exampleString \
  --sources='[{"id": "e7c3b3ee-78d9-4e02-95c3-c001a05e6ea5:api", "rules": [{"enabled": true, "event_type_filter": "$.notification_event_info.event_type == \'cert_manager\'", "notification_filter": "$.notification.findings[0].severity == \'MODERATE\'"}]}]'
```
{: pre}

### `ibmcloud event-notifications topic-delete`
{: #en-cli-topic-delete-command}

Delete a topic by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the topic is configured.

```sh
ibmcloud event-notifications topic-delete --instance-id INSTANCE-ID --id ID [--force]
```
{: pre}

#### Command options
{: #command-options-topic-delete}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the topic. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--force` (boolean)
:  Force the command to run.

#### Example
{: #en-cli-topic-delete-example}

```sh
ibmcloud event-notifications topic-delete \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

## Subscriptions
{: #en-cli-subscription}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} subscription.

### `ibmcloud event-notifications subscription-create`
{: #en-cli-subscription-create-command}

Create a subscription that links a destination to a topic for event delivery. A destination can subscribe to topics, and multiple destinations can subscribe to the same topic. To create a subscription, you must provide the ID of the {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications subscription-create --instance-id INSTANCE-ID --name NAME --destination-id DESTINATION-ID --topic-id TOPIC-ID [--description DESCRIPTION] [--attributes ATTRIBUTES]
```
{: pre}

#### Command options
{: #command-options-subscription-create}

`--name` (string)
:  The name of the subscription. Required.

   The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--description` (string)
:  The description of the subscription.

   The default value is ``. The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--destination-id` (string)
:  The destination ID to link to the topic. Required.

   The maximum length is `150` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--topic-id` (string)
:  The topic ID for the subscription. Required.

   The maximum length is `150` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--attributes` ([SubscriptionCreateAttributes](#en-cli-subscription-example-schema))
:  The attributes that are required to create the subscription. See [attribute examples](#en-cli-subscription-example-schema).

#### Examples
{: #en-cli-subscription-example-schema}

```sh
ibmcloud event-notifications subscription-create \
  --instance-id=exampleString \
  --name=exampleString \
  --destination-id=exampleString \
  --topic-id=exampleString \
  --description=exampleString \
  --attributes='{"invited": ["exampleString"]}'
```
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for webhook.

```json
{
   "signing_enabled" : true,
   "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13"
}
```
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for SMS.

```json
{
   "invited" :["+1xxxxxxxxxx", "+1xxxxxxxxxx"]
}
```
{: pre}

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
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for Slack Destination type as incoming_webhook.

```json
{
   "attachment_color" : "#FF0000",
   "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
}
```
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for Slack Destination type as direct_message.

```json
{
"channels" : [{ "id": "GHIUIFJHGGH"},{"id": "TSFDIDFOFNF"}],
"template_id_notification": "a59f6e38-7a48-xxxx-b665-3724axx58b13",
}
```
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for ServiceNow.

```json
{
   "assigned_to" : "serviceuser@gmail.com",
   "assignment_group" : "incidentgroup"
}
```
{: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for Custom Email.

   ```json
   {
      "invited" :["entest@gmail.com"],
      "add_notification_payload": true,
      "reply_to_mail": "en@ibm.com",
      "reply_to_name": "EYS ORG",
   }
   ```
   {: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for Custom Email Sandbox.

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
   {: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for Pagerduty/Event Streams.

   ```json
   {
      "template_id_notification": "a59f6e38-7a48-xxxx-b665-3724afc58b13",
   }
   ```
   {: pre}

- The following example shows the format of the `SubscriptionCreateAttributes` object for App Configuration. When creating or updating a subscription for an **App Configuration** destination, the `attributes` object has a specific rule:

   - You must include **either** `feature_flag_enabled` **or** `template_id_notification`
   - You **cannot** include both properties together

   This ensures that a subscription is created for the correct use case — either **feature flag evaluation** or **notification templating**, but not both at once.

   ```json
   {
      "template_id_notification": "e40843c8-xxxx-4717-xxxx-f923f2786a34",
   }
   ```
   {: pre}

   ```json
   {
      "feature_flag_enabled": false,
   }
   ```
   {: pre}

### `ibmcloud event-notifications subscriptions`
{: #en-cli-subscriptions-command}

List all subscriptions that are configured for an {{site.data.keyword.en_short}} instance. You must provide the ID of the instance.

```sh
ibmcloud event-notifications subscriptions --instance-id INSTANCE-ID [--offset OFFSET] [--limit LIMIT] [--search SEARCH] [--all-pages]
```
{: pre}

#### Command options
{: #command-options-subscriptions}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--offset` (int64)
:  The offset for paginated results.

   The minimum value is `0`.

`--limit` (int64)
:  The page limit for paginated results.

   The maximum value is `100`. The minimum value is `1`.

`--search` (string)
:  The search string for filtering results.

   The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the subscription collection.

#### Example
{: #en-cli-subscriptions-example}

```sh
ibmcloud event-notifications subscriptions \
  --instance-id=exampleString \
  --offset=0 \
  --limit=10 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications subscription`
{: #en-cli-subscription-command}

Get the details of a subscription by using its ID. You must provide the ID of the {{site.data.keyword.en_short}} instance for which the subscription is configured.

```sh
ibmcloud event-notifications subscription --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #command-options-subscription}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the subscription. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #en-cli-subscription-example}

```sh
ibmcloud event-notifications subscription \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications subscription-delete`
{: #en-cli-subscription-delete-command}

Delete a subscription by using its ID. You must provide the ID of the {{site.data.keyword.en_short}} instance for which the subscription is configured.

```sh
ibmcloud event-notifications subscription-delete --instance-id INSTANCE-ID --id ID [--force]
```
{: pre}

#### Command options
{: #command-options-subscription-delete}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the subscription. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--force` (boolean)
:  Force the command to run.

#### Example
{: #en-cli-subscription-delete-example}

```sh
ibmcloud event-notifications subscription-delete \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications subscription-update`
{: #en-cli-subscription-update-command}

Update the parameters of a subscription by using its ID. You must provide the ID of the {{site.data.keyword.en_short}} instance for which the subscription is configured.

```sh
ibmcloud event-notifications subscription-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--attributes ATTRIBUTES]
```
{: pre}

#### Command options
{: #command-options-subscription-update}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the subscription. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--name` (string)
:  The updated name of the subscription.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--description` (string)
:  The updated description of the subscription.

   The default value is ``. The maximum length is `100` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--attributes` ([SubscriptionUpdateAttributes](#en-cli-subscription-update-example-schema))
:  The updated attributes. See [attribute examples](#en-cli-subscription-update-example-schema).

#### Examples
{: #en-cli-subscription-update-example-schema}

```sh
ibmcloud event-notifications subscription-update \
  --instance-id=exampleString \
  --id=exampleString \
  --name=exampleString \
  --description=exampleString \
  --attributes='{"invited": {"add": ["exampleString"], "remove": ["exampleString"]}, "subscribed": {"remove": ["exampleString"]}, "unsubscribed": {"remove": ["exampleString"]}}'
```
{: pre}

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

- The following example shows the format of the `SubscriptionUpdateAttributes` object for Custom Email Sandbox.

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

   - The following example shows the format of the `SubscriptionCreateAttributes` object for App Configuration. When creating or updating a subscription for an **App Configuration** destination, the `attributes` object has a specific rule:
      - You must include **either** `feature_flag_enabled` **or** `template_id_notification`
      - You **cannot** include both properties together

      This ensures that a subscription is created for the correct use case — either **feature flag evaluation** or **notification templating**, but not both at once.

   ```json
   {
      "template_id_notification": "e40843c8-xxxx-4717-xxxx-f923f2786a34",
   }
   ```
   ```json
   {
      "feature_flag_enabled": false,
   }
   ```

## Integrations
{: #en-cli-integration}

Operate on {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} integration.

### `ibmcloud event-notifications integration-create`
{: #en-cli-integration-create-command}

Create an integration that connects {{site.data.keyword.en_short}} with {{site.data.keyword.cloud_notm}} Object Storage.

```sh
ibmcloud event-notifications integration-create --instance-id INSTANCE-ID --type TYPE --metadata METADATA
```
{: pre}

#### Command options
{: #en-cli-integration-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:  The type of integration. The supported type is `collect_failed_events`. Required.

   The maximum length is `50` characters. The minimum length is `1` characters. Allowed value is collect_failed_events.

`--metadata` (string)
:  The integration metadata that is required to create the integration. See the [example](#en-cli-integration-create-example-schema) for help formatting. Required.

#### Examples
{: #en-cli-integration-create-example-schema}

```sh
ibmcloud event-notifications integration-create \
  --instance-id=exampleString \
  --type=collect_failed_events \
  --metadata='{"endpoint": "exampleString", "crn": "exampleString", "bucket_name": "exampleString"}'
```
{: pre}

The following example shows the format of the `IntegrationCreateAttributes` object.

```json
{
   "endpoint": "https://s3.us-west.cloud-object-storage.appdomain.cloud",
   "crn": "crn:v1:bluemix:public:cloud-object-storage:global:xxxxxxx6db359a81a1dde8f44bxxxxxx:xxxxxxxx-1d48-xxxx-xxxx-xxxxxxxxxxxx::",
   "bucket_name": "cloud-object-storage"
}
```
{: pre}

### `ibmcloud event-notifications integration-update`
{: #en-cli-integration-update-command}

Update an existing integration by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the integration is configured.

```sh
ibmcloud event-notifications integration-update --instance-id INSTANCE-ID --id ID --type TYPE --metadata METADATA
```
{: pre}

At this time, you can also use `integration-replace` to update your integration. But, the `integration-replace` command is deprecated and will be removed in a future release.
{: note}


#### Command options
{: #en-cli-integration-replace-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--type` (string)
:  The integration type. Allowed values are `kms`, `hs-crypto`, and `collect_failed_events`. Required.

   The maximum length is `50` characters. The minimum length is `1` characters.

`--metadata` (string)
:  The integration metadata that is required to update the integration. See the [example](#en-cli-integration-example-schema) for help formatting. Required.

`--id` (string)
:  The unique identifier for the integration. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

#### Examples
{: #en-cli-integration-example-schema}

```sh
ibmcloud event-notifications integration-update \
  --instance-id=exampleString \
  --id=exampleString \
  --type=exampleString \
  --metadata='{"endpoint": "exampleString", "crn": "exampleString", "root_key_id": "exampleString", "bucket_name": "exampleString"}'
```
{: pre}

The following example shows the format of the `IntegrationReplaceAttributes` object for Key Protect.

```json
{
   "endpoint" : "https://qa.us-south.kms.cloud.ibm.com",
   "crn" : "crn of key protect",
   "root_key_id" : "root key id"
}
```
{: pre}

### `ibmcloud event-notifications integrations`
{: #en-cli-integrations-command}

List the integrations that are created for an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications integrations --instance-id INSTANCE-ID [--offset OFFSET] [--limit LIMIT] [--search SEARCH] [--all-pages]
```
{: pre}

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

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the integration collection.

#### Example
{: #example-integrations}

```sh
ibmcloud event-notifications integrations \
  --instance-id=exampleString \
  --offset=0 \
  --limit=10 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications integration`
{: #en-cli-integration-command}

Get the details of an integration by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the integration is configured.

```sh
ibmcloud event-notifications integration --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #en-cli-integration-get-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the integration. Required.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

#### Example
{: #example-integration}

```sh
ibmcloud event-notifications integration \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}


## Templates
{: #event-notifications-templates-cli}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} templates.

### `ibmcloud event-notifications template-create`
{: #event-notifications-cli-template-create-command}

Create a template for invitations and notifications. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which you configure the template.

```sh
ibmcloud event-notifications template-create --instance-id INSTANCE-ID --name NAME --type TYPE --params PARAMS [--description DESCRIPTION]
```
{: pre}

#### Command options
{: #event-notifications-template-create-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:   The name of the template. Required.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--type` (string)
:   The template type. Supported types are `smtp_custom.invitation`, `smtp_custom.notification`, `webhook.notification`, `slack.notification`, `pagerduty.notification`, and `event_streams.notification`. Required.

    The maximum length is `24` characters. The minimum length is `22` characters. The value must match regular expression `/^(smtp_custom.notification|smtp_custom.invitation)$/`.

`--params` ([`TemplateConfig`](#event-notifications-template-create-examples))
:   The template parameters for the notification. Required. See [template parameters](#event-notifications-template-create-examples).

    This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--params=@path/to/file.json`.

`--description` (string)
:   The template description.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--params-body` (string)
:   Template body. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `20000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--params-subject` (string)
:   The template subject. This option provides a value for a sub-field of the JSON option 'params'. It is mutually exclusive with that option.

    The maximum length is `1000` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

#### Examples
{: #event-notifications-template-create-examples}

- The following example shows the format of the `TemplateConfig` object for email. The supported types are `smtp_custom.notification` and `smtp_custom.invitation`.

```sh
ibmcloud event-notifications template-create \
  --instance-id=exampleString \
  --name=exampleString \
  --type=exampleString \
  --params='{"body": "exampleString", "subject": "exampleString"}' \
  --description=exampleString
```
{: pre}

- The following example shows the format of the `TemplateConfig` object for Slack. The supported type is `slack.notification`.

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type slack.notification \
    --params '{"body": "ewoJImJsb2NrcyI6IFsKCQl7CgkJCSJ0eXBlIjogInNlY3Rpb24iLAoJCQkidGV4dCI6IHsKCQkJCSJ0eXBlIjogIm1ya2R3biIsCgkJCQkidGV4dCI6ICJOZXcgUGFpZCBUaW1lIE9mZiByZXF1ZXN0IGZyb20gPGV4YW1wbGUuY29tfEZyZWQgRW5yaXF1ZXo+XG5cbjxodHRwczovL2V4YW1wbGUuY29tfFZpZXcgcmVxdWVzdD4iCgkJCX0KCQl9CgldCn0="}' \
    --description exampleString
```
{: pre}

- The following example shows the format of the `TemplateConfig` object for Webhook. The supported type is `webhook.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type webhook.notification \
    --params '{"body": "ewoJImJsb2NrcyI6IFsKCQl7CgkJCSJ0eXBlIjogInNlY3Rpb24iLAoJCQkidGV4dCI6IHsKCQkJCSJ0eXBlIjogIm1ya2R3biIsCgkJCQkidGV4dCI6ICJOZXcgUGFpZCBUaW1lIE9mZiByZXF1ZXN0IGZyb20gPGV4YW1wbGUuY29tfEZyZWQgRW5yaXF1ZXo+XG5cbjxodHRwczovL2V4YW1wbGUuY29tfFZpZXcgcmVxdWVzdD4iCgkJCX0KCQl9CgldCn0="}' \
    --description exampleString
```
{: pre}


- The following example shows the format of the `TemplateConfig` object for Pagerduty. The supported type is `pagerduty.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type pagerduty.notification \
    --params '{"body": "ewogICJwYXlsb2FkIjogewogICAgInN1bW1hcnkiOiAie3sgZGF0YS5hbGVydF9kZWZpbml0aW9uLm5hbWV9fSIsCiAgICAidGltZXN0YW1wIjogInt7dGltZX19IiwKICAgICJzZXZlcml0eSI6ICJpbmZvIiwKICAgICJzb3VyY2UiOiAie3sgc291cmNlIH19IgogIH0sCiAgImRlZHVwX2tleSI6ICJ7eyBpZCB9fSIsCiAge3sjZXF1YWwgZGF0YS5zdGF0dXMgInRyaWdnZXJlZCJ9fQogICJldmVudF9hY3Rpb24iOiAidHJpZ2dlciIKICAge3svZXF1YWx9fQoKICB7eyNlcXVhbCBkYXRhLnN0YXR1cyAicmVzb2x2ZWQifX0KICAiZXZlbnRfYWN0aW9uIjogInJlc29sdmUiCiAge3svZXF1YWx9fQoKICAge3sjZXF1YWwgZGF0YS5zdGF0dXMgImFja25vd2xlZGdlZCJ9fQogICAiZXZlbnRfYWN0aW9uIjogImFja25vd2xlZGdlIgogICB7ey9lcXVhbH19Cn0="}' \
    --description exampleString
```
{: pre}

- The following example shows the format of the `TemplateConfig` object for Event Streams. The supported type is `event_streams.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type event_streams.notification \
    --params '{"body": "eyJuYW1lIjoie3tkYXRhLm5hbWV9fSIifQ=="}' \
    --description exampleString
```
{: pre}

- The following example shows the format of the `TemplateConfig` object for Code Engine Job. The supported type is `ibmcejob.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type ibmcejob.notification\
    --params '{"body": "ewogInJ1bl9lbnZfdmFyaWFibGVzIjogWwogICB7ICJuYW1lIjogInJlZ2lvbiIsICJ2YWx1ZSI6ICJ7e2RhdGEucmVnaW9ufX0iLCJ0eXBlIjogImxpdGVyYWwifSwKeyJuYW1lIjoiVkFSMSIsInR5cGUiOiJsaXRlcmFsIiwidmFsdWUiOiJ7e2RhdGEudmFyMX19In0sCnsibmFtZSI6IlZBUjIiLCJ0eXBlIjoibGl0ZXJhbCIsInZhbHVlIjoie3tkYXRhLnZhcjJ9fSJ9Cl0KfQ=="}' \
    --description exampleString
```

- The following example shows the format of the `TemplateConfig` object for Code Engine Application/Function. The supported type is `ibmceapp.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type ibmceapp.notification\
    --params '{"body": "ewogICJ2YXIxIjogInt7ZGF0YS52YXIxfX0iLAogICJ2YXIyIjogInt7ZGF0YS52YXIyfX0iCn0="}' \
    --description exampleString
```

- The following example shows the format of the `TemplateConfig` object for App Configuration. The supported type is `app_configuration.notification`

```sh
ibmcloud event-notifications template-create \
    --instance-id exampleString \
    --name exampleString \
    --type app_configuration.notification\
    --params '{"body": "eyJlbmFibGVkIjogZmFsc2V9Cg=="}' \
    --description exampleString
```
{: pre}

### `ibmcloud event-notifications templates`
{: #event-notifications-cli-templates-command}

List all user-defined templates that are created for an {{site.data.keyword.en_short}} instance. You must provide the ID of the instance.

If you do not set the `--all-pages` option, the command retrieves only one page of the collection.
{: note}

```sh
ibmcloud event-notifications templates --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```
{: pre}

#### Command options
{: #event-notifications-templates-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:   The page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The offset for paginated results.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   The search string for filtering results.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:   Invoke multiple requests to display all pages of the template collection.

#### Example
{: #event-notifications-templates-examples}

```sh
ibmcloud event-notifications templates \
  --instance-id=exampleString \
  --limit=10 \
  --offset=0 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications template`
{: #event-notifications-cli-template-command}

Get the details of a template by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the template is configured.

```sh
ibmcloud event-notifications template --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-template-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--id` (string)
:   The unique identifier for the template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-template-examples}

```sh
ibmcloud event-notifications template \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications template-update`
{: #event-notifications-cli-template-update-command}

Update the details of an existing template that is created under an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications template-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION] [--params PARAMS]
```
{: pre}

You can use `template-update` instead of `template-replace`. Both commands are currently supported, but `template-replace` will be deprecated in a future release.
{: note}

#### Command options
{: #event-notifications-template-update-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   The unique identifier for the template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--name` (string)
:   The updated template name.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--description` (string)
:   The updated template description.

    The maximum length is `255` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--params` ([`TemplateConfig`](#event-notifications-template-examples))
:   The updated template parameters. See [template parameters](#event-notifications-template-examples).

    This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--params=@path/to/file.json`.

#### Examples
{: #event-notifications-template-replace-examples}

```sh
ibmcloud event-notifications template-replace \
  --instance-id=exampleString \
  --id=exampleString \
  --name=exampleString \
  --description=exampleString \
  --params='{"body": "exampleString", "subject": "exampleString"}'
```
{: pre}

### `ibmcloud event-notifications template-delete`
{: #event-notifications-cli-template-delete-command}

Delete a template by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the template is configured.

```sh
ibmcloud event-notifications template-delete --instance-id INSTANCE-ID --id ID [--force]
```
{: pre}

#### Command options
{: #event-notifications-template-delete-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `256` characters. The minimum length is `10` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   The unique identifier for the template. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`-f, --force` (boolean)
:   Force the command to run.

#### Example
{: #event-notifications-template-delete-examples}

```sh
ibmcloud event-notifications template-delete \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

### `ibmcloud event-notifications pre-defined-templates`
{: #event-notifications-cli-pre-defined-templates-command}

List predefined templates for an {{site.data.keyword.en_short}} instance.

If you do not set the `--all-pages` option, the command retrieves only one page of the collection.
{: note}

```sh
ibmcloud event-notifications pre-defined-templates --instance-id INSTANCE-ID [--source SOURCE] [--type TYPE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```
{: pre}

#### Command options
{: #event-notifications-pre-defined-templates-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--source` (string)
:   The source type for the predefined template. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--type` (string)
:   The template type for the predefined template, based on the destination. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--limit` (int64)
:   The page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The offset for paginated results.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   The search string for filtering results.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:   Invoke multiple requests to display all pages of the predefined-template collection.

#### Example
{: #event-notifications-pre-defined-templates-examples}

```sh
ibmcloud event-notifications pre-defined-templates \
  --instance-id=exampleString \
  --source=exampleString \
  --type=exampleString \
  --limit=10 \
  --offset=0 \
  --search=exampleString
```
{: pre}

### `ibmcloud event-notifications pre-defined-template`
{: #event-notifications-cli-pre-defined-template-command}

Get the details of a predefined template by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the predefined template is configured.

```sh
ibmcloud event-notifications pre-defined-template --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-pre-defined-template-cli-options}

`--instance-id` (string)
:   The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

`--id` (string)
:   The unique identifier for the predefined template. Required.

#### Example
{: #event-notifications-pre-defined-template-examples}

```sh
ibmcloud event-notifications pre-defined-template \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}


## SMTP Configurations
{: #event-notifications-smtp-configurations-cli}

IBM Cloud Event Notifications SMTP Configurations.

### `ibmcloud event-notifications smtp-configuration-create`
{: #event-notifications-cli-smtp-configuration-create-command}

Create an SMTP configuration for mail delivery. For more information, see [SMTP configurations](/docs/event-notifications?topic=event-notifications-en-smtp-configurations).

```sh
ibmcloud event-notifications smtp-configuration-create --instance-id INSTANCE-ID --name NAME --domain DOMAIN [--description DESCRIPTION]
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-create-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--name` (string)
:  The name of the SMTP configuration. Required.

   The maximum length is `250` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--domain` (string)
:  The domain name for the SMTP configuration. Required.

   The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/.*/`.

`--description` (string)
:  The description of the SMTP configuration.

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

List all SMTP configurations for an {{site.data.keyword.en_short}} instance.

If you do not set the `--all-pages` option, the command retrieves only one page of the collection.
{: note}

```sh
ibmcloud event-notifications smtp-configurations --instance-id INSTANCE-ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH] [--all-pages]
```
{: pre}

#### Command options
{: #event-notifications-smtp-configurations-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--limit` (int64)
:  The page limit for paginated results.

   The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:  The offset for paginated results.

   The default value is `0`. The minimum value is `0`.

`--search` (string)
:  The search string for filtering results.

   The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9]/`.

`--all-pages` (boolean)
:  Invoke multiple requests to display all pages of the SMTP configuration collection.

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

Create an SMTP user for an SMTP configuration. You must provide the ID of the SMTP configuration and the ID of the {{site.data.keyword.en_short}} instance.

SMTP credentials are displayed only once. Copy and store them securely, as they cannot be retrieved later.
{: important}

```sh
ibmcloud event-notifications smtp-user-create --instance-id INSTANCE-ID --id ID [--description DESCRIPTION] [--username-to-clone USERNAME-TO-CLONE]
```
{: pre}

#### Command options
{: #event-notifications-smtp-user-create-cli-options}

`--instance-id` (string)
:  The unique identifier for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} instance. Required.

   The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:  The unique identifier for the SMTP configuration. Required.

   The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--description` (string)
:  The description of the SMTP user.

   The maximum length is `250` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z 0-9-_\/.?:'";,+=!#@$%^&*() ]*/`.

`--username-to-clone` (string)
:  The username of the SMTP user to clone.

   The maximum length is `20` characters. The minimum length is `1` character. The value must match regular expression `/^[a-z0-9]{18}\\d{2}$/`.

#### Example
{: #event-notifications-smtp-user-create-examples}

```sh
ibmcloud event-notifications smtp-user-create \
  --instance-id=exampleString \
  --id=exampleString \
  --description=exampleString \
  --username-to-clone=exampleString
```
{: pre}

### `ibmcloud event-notifications smtp-users`
{: #event-notifications-cli-smtp-users-command}

List all SMTP users for an SMTP configuration.

If the `--all-pages` option is not set, the command retrieves only a single page of the collection.
{: note}

```sh
ibmcloud event-notifications smtp-users --instance-id INSTANCE-ID --id ID [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```
{: pre}

#### Command options
{: #event-notifications-smtp-users-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

`--all-pages` (boolean)
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

Get details of an SMTP configuration for an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications smtp-configuration --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Update an SMTP configuration by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the SMTP configuration is configured.

```sh
ibmcloud event-notifications smtp-configuration-update --instance-id INSTANCE-ID --id ID [--name NAME] [--description DESCRIPTION]
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Delete an SMTP configuration by using its ID. You must also provide the ID of the {{site.data.keyword.en_short}} instance for which the SMTP configuration is configured.

```sh
ibmcloud event-notifications smtp-configuration-delete --instance-id INSTANCE-ID --id ID [--force]
```
{: pre}

#### Command options
{: #event-notifications-smtp-configuration-delete-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Get details of an SMTP user by using the user ID and SMTP configuration ID.

```sh
ibmcloud event-notifications smtp-user --instance-id INSTANCE-ID --id ID --user-id USER-ID
```
{: pre}

#### Command options
{: #event-notifications-smtp-user-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Update an SMTP user by using the user ID and SMTP configuration ID.

```sh
ibmcloud event-notifications smtp-user-update --instance-id INSTANCE-ID --id ID --user-id USER-ID [--description DESCRIPTION]
```
{: pre}

#### Command options
{: #event-notifications-smtp-user-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Delete an SMTP user by using the user ID and SMTP configuration ID.

```sh
ibmcloud event-notifications smtp-user-delete --instance-id INSTANCE-ID --id ID --user-id USER-ID [--force]
```
{: pre}

#### Command options
{: #event-notifications-smtp-user-delete-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Get all allowed IP addresses for an SMTP configuration.

```sh
ibmcloud event-notifications smtp-allowed-ips --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-smtp-allowed-ips-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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

Support for legacy allowlisting has been deprecated. Allowlisting is now enabled through Context-based restrictions. For more information, see [SMTP configurations](https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-en-smtp-configurations#en-smtp-configurations-cbr){: external}.
{: note}

### `ibmcloud event-notifications verify-smtp-update`
{: #event-notifications-cli-verify-smtp-update-command}

Verify SMTP configuration domain for spf, skim and en_authorization.

```sh
ibmcloud event-notifications verify-smtp-update --instance-id INSTANCE-ID --id ID --type TYPE
```

#### Command options
{: #event-notifications-verify-smtp-update-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--id` (string)
:   Unique identifier for SMTP. Required.

    The maximum length is `32` characters. The minimum length is `32` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--type` (string)
:   SMTP verification type. Allowed values are `spf`, `dkim`, and `en_authorization`. Required.

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

Retrieve metrics for an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications metrics --instance-id INSTANCE-ID --gte GTE --lte LTE [--smtp-config-id SMTP-CONFIG-ID] [--destination-type DESTINATION-TYPE] [--destination-id DESTINATION-ID] [--subscription-id SUBSCRIPTION-ID] [--source-id SOURCE-ID] [--email-to EMAIL-TO] [--notification-id NOTIFICATION-ID] [--subject SUBJECT]
```

#### Command options
{: #event-notifications-metrics-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

`--gte` (string)
:   GTE (greater than equal), start timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--lte` (string)
:   LTE (less than equal), end timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--smtp-config-id` (string)
:   SMTP configuration ID. Required when querying metrics for SMTP interface destinations.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--destination-type` (string)
:   Destination type for which metrics are requested. Supported value: smtp_custom. Required when querying metrics for custom email destinations.

    Allowable values are: `smtp_custom`.

`--destination-id` (string)
:   Unique identifier for Destination.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--subscription-id` (string)
:   Unique identifier for Subscription.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--source-id` (string)
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
  --destination-id=exampleString \
  --subscription-id=exampleString \
  --source-id=exampleString \
  --email-to=exampleString \
  --notification-id=exampleString \
  --subject=exampleString
```
{: pre}

### `ibmcloud event-notifications bounce-metrics`
{: #event-notifications-cli-bounce-metrics-command}

Retrieve bounce metrics for an {{site.data.keyword.en_short}} instance.

```sh
ibmcloud event-notifications bounce-metrics --instance-id INSTANCE-ID --gte GTE --lte LTE [--smtp-config-id SMTP-CONFIG-ID] [--destination-type DESTINATION-TYPE] [--destination-id DESTINATION-ID] [--subscription-id SUBSCRIPTION-ID] [--source-id SOURCE-ID] [--email-to EMAIL-TO] [--notification-id NOTIFICATION-ID] [--subject SUBJECT] [--limit LIMIT] [--offset OFFSET]
```
{: pre}


#### Command options
{: #event-notifications-bounce-metrics-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--gte` (string)
:   Greater than equal (GTE) start timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--lte` (string)
:   Less than equal (LTE) start timestamp in UTC. Required.

    The maximum length is `28` characters. The minimum length is `1` character. The value must match regular expression `/[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}T[0-9]{1,2}:[0-9]{1,2}:[0-9]{1,2}Z/`.

`--smtp-config-id` (string)
:   SMTP configuration ID. Required when querying metrics for SMTP interface destinations.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--destination-type` (string)
:   Destination type for which metrics are requested. Supported value: smtp_custom. Required when querying metrics for custom email destinations.

    Allowable values are: `smtp_custom`.

`--destination-id` (string)
:   Unique identifier for Destination.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--subscription-id` (string)
:   Unique identifier for Subscription.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--source-id` (string)
:   Unique identifier for Source.

    The maximum length is `100` characters. The minimum length is `1` character. The value must match regular expression `/[a-zA-Z0-9-:_]*/`.

`--email-to` (string)
:   Receiver email ID.

    The maximum length is `256` characters. The minimum length is `0` characters. The value must match regular expression `/[A-Za-z0-9\\._%+\\-]+@[A-Za-z0-9\\.\\-]+\\.[A-Za-z]{2,}/`.

`--notification-id` (string)
:   Notification ID.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--subject` (string)
:   Email subject.

    The maximum length is `256` characters. The minimum length is `0` characters. The value must match regular expression `/[a-zA-Z0-9]/`.

`--limit` (int64)
:   Page limit for paginated results.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   offset for paginated results.

    The default value is `0`. The minimum value is `0`.

#### Example
{: #event-notifications-bounce-metrics-examples}

```sh
ibmcloud event-notifications bounce-metrics \
  --instance-id=exampleString \
  --destination-type=smtp_custom \
  --gte=exampleString \
  --lte=exampleString \
  --destination-id=exampleString \
  --subscription-id=exampleString \
  --source-id=exampleString \
  --email-to=exampleString \
  --notification-id=exampleString \
  --subject=exampleString \
  --limit=10 \
  --offset=0
```
{: pre}

## Get Notifications Status
{: #event-notifications-get-notifications-status-cli}

### `ibmcloud event-notifications notifications-status`
{: #event-notifications-cli-notifications-status-command}

Get the notification status for a webhook destination test notification.

```sh
ibmcloud event-notifications notifications-status --instance-id INSTANCE-ID --id ID
```
{: pre}

#### Command options
{: #event-notifications-notifications-status-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

`--id` (string)
:   The notification ID returned when testing a webhook destination. This ID is specific to test notifications sent to webhook destinations. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}/`.

#### Example
{: #event-notifications-notifications-status-examples}

```sh
ibmcloud event-notifications notifications-status \
  --instance-id=exampleString \
  --id=exampleString
```
{: pre}

## Send Notifications
{: #event-notifications-send-notifications-cli}

Send events from your backend applications by using API sources. {{site.data.keyword.en_short}} supports two [CloudEvents](https://github.com/cloudevents/spec){: external} content modes:

- **Binary mode** — The event data is placed in the HTTP request body as-is, with the `datacontenttype` attribute declaring its media type in the `Content-Type` header. All other attributes are mapped to HTTP headers prefixed with `ce-`. Requests are treated as binary mode when the mandatory CloudEvents attributes (`specversion`, `id`, `type`, and `source`) are passed as headers.
- **Structured mode** — Event metadata and event data are placed in the HTTP request body. Set the `Content-Type` header to `application/cloudevents+json`. The mandatory attributes (`specversion`, `id`, `type`, and `source`) must be in the request body. The `datacontenttype` field is required and must be set to `application/json`.

### `ibmcloud event-notifications send-notifications`
{: #event-notifications-cli-send-notifications-command}

Send a notification from an instance of the service. For more information about the notification payload, see [the docs](/docs/event-notifications?topic=event-notifications-en-spec-payload).

```sh
ibmcloud event-notifications send-notifications --instance-id INSTANCE-ID [--body BODY]
```
{: pre}

#### Command options
{: #event-notifications-send-notifications-cli-options}

`--instance-id` (string)
:   Unique identifier for IBM Cloud Event Notifications instance. Required.

    The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]/`.

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
  "ibmenmarkdownn": "This is a *italic* message.\n- Item 1\n- Item 2\n**bold text** with more text data\n~~strike through~~\n1. order 1\n2. order 2\n```fenced code block```\n> block code\n`code`\n[Click here](https://example.com) for more info."
  "ibmenhtmlbody" : "exampleString",
  "subject" : "exampleString",
   "attachments": [
    {
      "content": "VGhpcyBpcyBhIHRlc3QgZG9jdW1lbnQK",
      "filename": "test.txt",
      "content_type": "text/plain",
      "disposition": "attachment"
    }
  ],
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

**With required parameters:**

```sh
ibmcloud event-notifications send-notifications \
  --instance-id=exampleString \
  --body='{"specversion": "1.0", "time": "2019-01-01T12:00:00.000Z", "type": "*", "id": "exampleString", "source": "exampleString", "ibmensourceid": "exampleString", "ibmendefaultshort": "short message", "ibmendefaultlong": "long message", "data": {"name": "exampleString"}, "datacontenttype": "application/json"}'
```
{: pre}

**With all parameters:**

```sh
ibmcloud event-notifications send-notifications \
  --instance-id=exampleString \
  --body='{"specversion": "1.0", "time": "2019-01-01T12:00:00.000Z", "id": "exampleString", "source": "exampleString", "type": "exampleString", "ibmenseverity": "exampleString", "ibmensourceid": "exampleString", "ibmendefaultshort": "exampleString", "ibmendefaultlong": "exampleString", "ibmensubject": "exampleString", "ibmentemplates": [\"template-id\"], "ibmenmailto": "exampleString","ibmenslackto": "[\"sgjhgsjaS\",\"agjhgsjaS\"]", "ibmensmsto": "exampleString","ibmenmms": "{\"content\": \"VBORw0KGgoAAAANSUhEUgAAAFoAAAA4CAYAAAB9lO\",\"content_type\": \"image/png\"}", "ibmenhtmlbody": "exampleString", "subject": "exampleString", "data": {"anyKey": "anyValue"}, "datacontenttype": "application/json", "ibmenpushto": "{\"fcm_devices\": [\"exampleString\"], \"apns_devices\": [\"exampleString\"], \"huawei_devices\": [\"exampleString\"], \"safari_devices\": [\"exampleString\"], \"chrome_devices\": [\"exampleString\"], \"firefox_devices\": [\"exampleString\"], \"user_ids\": [\"exampleString\"], \"tags\": [\"exampleString\"], \"platforms\": [\"push_android\"]}", "ibmenfcmbody": "{}", "ibmenapnsbody": "{}", "ibmenapnsheaders": "{}", "ibmenchromebody": "{}", "ibmenchromeheaders": "{}", "ibmenfirefoxbody": "{}", "ibmenfirefoxheaders": "{}", "ibmenhuaweibody": "{}", "ibmensafaribody": "{}"}'
```
{: pre}

#### Additional properties that can be configured for the iOS notification
{: #en-cli-send-notifications-command-addprops-ios}

| Property | Property type | Description |
|---|---|---|
| `badge` | integer | The number to display as the badge of the application icon. |
| `interactive_category` | string | The category identifier to be used for the interactive push notifications. |
| `ios_action_key` | string |The title for the Action key. |
| `payload` | JSON object | Custom JSON payload that is sent as part of the notification message. |
| `sound` | string | The name of the sound file in the application bundle. The sound of this file is played as an alert. |
| `title_loc_key` | string | The key to a title string in the Localizable.strings file for the current localization. The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the titleLocArgs array. |
| `loc_key` | string | A key to an alert-message string in a Localizabl.strings file for the current localization (which is set by the user's language preference). The key string can be formatted with %@ and %n$@ specifiers to take the variables specified in the locArgs array. |
| `launch_image` | string | The file name of an image file in the app bundle, with or without the file name extension. The image is used as the launch image when users tap the action button or move the action slider. |
| `title_loc_args` | string | Variable string values to appear in place of the format specifiers in title-loc-key. |
| `loc_args` | string | Variable string values to appear in place of the format specifiers in locKey. |
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

| Property | Property type | Description |
|---|---|---|
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


## Sample scripts
{: #en-scripts}

You can use the following scripts to help with development.

### Sample script for {{site.data.keyword.en_short}} provisioning using CLI
{: #en-provisioning-script}

The [provision_event_notification.sh](https://github.com/IBM/event-notifications/blob/main/samples/provision_event_notifications.sh){: external} script automates the provisioning and configuration of an {{site.data.keyword.en_short}} instance.


### Sample script for platform notifications integration using CLI
{: #en-platform-notifications-script}

The [en-platform-notification-src-and-email-dest.sh](https://github.com/IBM/event-notifications/blob/main/samples/en-platform-notification-src-and-email-dest.sh){: external} script integrates Platform Notifications with {{site.data.keyword.en_short}} and routes notifications to IBM Inbuilt Email or Custom Domain Sandbox.


### Sample script for {{site.data.keyword.logs_full_notm}} integration using CLI
{: #en-icl-script}

The [en-icl-src-and-email-dest.sh](https://github.com/IBM/event-notifications/blob/main/samples/en-icl-src-and-email-dest.sh){: external} script integrates {{site.data.keyword.logs_full_notm}} with {{site.data.keyword.en_short}} and routes notifications to IBM Inbuilt Email or Custom Domain Sandbox .

This script assumes that the {{site.data.keyword.logs_full_notm}} instance and {{site.data.keyword.en_short}} instance are in the same account.
{: note}
