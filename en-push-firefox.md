---

copyright:
  years: 2022, 2024
lastupdated: "2024-10-17"

keywords: event-notifications, event notifications, about event notifications, destinations, push

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Creating and sending push notifications to Firefox web by using {{site.data.keyword.en_short}}
{: #en-push-firefox}

Create an {{site.data.keyword.en_short}} service, add a push destination for Firefox, and send messages to Firefox web devices.
{: shortdesc}

## What is {{site.data.keyword.en_short}}?
{: #en-what-is-ff}

{{site.data.keyword.en_short}} is an event notification routing service that notifies you of critical events that occur in your {{site.data.keyword.cloud_notm}} account or triggers automated actions by using webhooks. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like {{site.data.keyword.prf_hubshort}}, to email, SMS, push notifications, and webhooks.

## How do clients use Firefox web push notifications?
{: #en-how-clients-send-ff}

The following diagram shows you how clients use Firefox web Push Notifications.

![How clients use push notifications](images/en-how-send-mozilla.svg "How clients use push notifications"){: caption="How clients use push notifications" caption-side="bottom"}

## Objectives
{: #en-objectives-ff}

This tutorial shows you how to send push notifications as follows:

* Create a website with {{site.data.keyword.en_short}}.
* Get Firefox web credentials.
* Download the SDK and complete the notifications setup.
* Configure and send Firefox web Push Notifications to a browser.

## Create an {{site.data.keyword.en_short}} service instance
{: #en-create-event-ff}
{: step}

* Log in to your [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/).
* In the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog#services), search `Event Notifications > Event Notifications`.
* Select a `Region` from the list of supported regions and select a `pricing plan`.
* Provide a `Service name`.
* Select a `resource group`.
* Accept the licensing agreements and terms by clicking the checkbox.
* Click `Create`.

## Add a generic API source
{: #en-add-gen-api-ff}
{: step}

Take the following steps:

* Go to the `Sources` section of the {{site.data.keyword.en_short}} dashboard.
* Click `Add` and select an API Source.
* Type a name and an optional description and click `Add`.

## Create an {{site.data.keyword.en_short}} destination
{: #en-create-dest-ff}
{: step}

Click `Destinations` in the {{site.data.keyword.en_short}} console and add the following destination details:

* `Name`: add a name for the Destination.
* `Description`: add an optional description for the destination.
* `Type`: select `Firefox Push Notifications` type from the dropdown list.
* Select a destination plan: Pre-production destination or Production destination.
   - `Pre-production destination` - select this destination as low-cost push destination, for your development and test environments.
   - `Production destination` - utilize the full capability of this destination. Unlimited devices and outbound messages allowed.
* Provide the URL of your website.
* Click **Add**.
* Once Firefox destination is created. Edit the created destination to get `public vapId key` required for web sdk.

![Destination Edit](images/en-push-firefox-destination-edit.png "Destination Edit"){: caption="Receive notifications" caption-side="bottom"}

![Destination](images/en-push-firefox-destination.png "Destination"){: caption="Receive notifications" caption-side="bottom"}

## Create an {{site.data.keyword.en_short}} topic
{: #en-create-topic-ff}
{: step}

Select `Topics` in the {{site.data.keyword.en_short}} console and click `Create`. Enter the following topic details:
* `Name`: enter a name for the topic.
* `Description`: add an optional description for the topic.
* `Source`: select a source from the dropdown list.
* `Event type`: select event type from the dropdown list.
* `Event sub type`: select event sub type from the event sub type dropdown list.
* `Severity`: select severity from the severity dropdown list.
* `Advanced conditions`: write your own custom conditions, which must follow [jsonpath specifications](https://www.rfc-editor.org/rfc/rfc9535.html). Jsonpath expressions can be validated at [jsonpath.com](https://jsonpath.com) or [extendsclass.com](https://extendsclass.com/jsonpath-tester.html).

## Create an {{site.data.keyword.en_short}} subscription
{: #en-create-sub-ff}
{: step}

Click `Subscriptions` in the {{site.data.keyword.en_short}} console. Enter the following subscription details:

* `Click` Create to display subscription wizard.
* Complete the following subscription details:
   * `Subscription name`: name of the subscription.
   * `Subscription description`: add an optional description.
* Under the `Subscribe to a topic` section, select a topic from the drop-down list and select a destination from the destination drop-down list.
* `Destination type`: select type under `Destination` and click `Add`.

## Set up {{site.data.keyword.en_short}} Firefox web SDK
{: #en-setup-firefox-sdk}
{: step}

The Firefox web SDK enables Firefox websites to receive push notifications. Complete the following steps to install {{site.data.keyword.en_short}} Firefox web SDK, initialize the SDK, and register for notifications for your website.

* To include the SDK in your project, add the `ENPushSDK.js`,`ENPushServiceWorker.js` and `manifest_Website.json` files to your project root folder.

* Edit the manifest_Website.json file.

   ```js
   {
      "name": "YOUR_WEBSITE_NAME"
   }
   ```
   {: codeblock}

* Change the `manifest_Website.json` file name to `manifest.json`.

* Include the `manifest.json` in the `<head>` tag of your html file.

   ```html
   <link rel="manifest" href="https://github.com/IBM/event-notifications-destination-webpush-sdk/blob/main/manifest_Website.json">
   ```
   {: codeblock}

* Include {{site.data.keyword.cloud_notm}} web push SDK to the script.

   ```html
   <script src="https://github.com/IBM/event-notifications-destination-webpush-sdk/blob/main/ENPushSDK.js" async></script>
   ```
   {: codeblock}

* Complete the following steps to enable the website to initialize the SDK.

   ```js
   var enPush = new ENPush()

   function callback(response) {
      alert(response.response)
   }

   var initParams = {
      "instanceGUID": "<instance_guid>",
      "apikey": "<instance_apikey>",
      "region": "<region>",
      "deviceId": "<YOUR_DEVICE_ID>",
      "firefoxDestinationId": "<firefox_destination_id>",
      "firefoxApplicationServerKey": "<Firefox_VapId_public_key>"
   }

   enPush.initialize(initParams, callback)
   ```
   {: codeblock}

   * `region`: Region of the {{site.data.keyword.en_short}} instance. eg; `us-south`,`eu-gb`, `au-syd`, `eu-de` and `eu-es`.

   * `deviceId`: Optional `deviceId` for device registration.

* To register for notifications, se the `register()` or `registerWithUserId()` API to register the device with {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}} service. Choose either of the following options:

   * Register without `UserId`:

      ```js
      enPush.register(function(response) {
         alert(response.response)
      })
      ```
      {: codeblock}

   * Register with `UserId`. For `userId` based notification, the register method will accept one more parameter - `userId`.

      ```js
      bmsPush.registerWithUserId("UserId",function(response) {
         alert(response.response)
      })
      ```
      {: codeblock}

      `UserId` is the user identifier value with which you want to register devices in the push service instance.

* The `subscribe` API subscribes the device for a tag. After the device is subscribed to a particular tag, the device can receive notifications that are sent for that tag. Add the following code snippet to your web application to subscribe to a list of tags.

   ```js
   enPush.subscribe(tagName, function(response) {
      alert(response.response)
   })
   ```
   {: codeblock}

* When the setup is complete, run your application and register for push notifications.

## Send notifications to the Firefox device
{: #en-send-notifications-ff}
{: step}

Use the [Send Notification API](/apidocs/event-notifications) to send the push notification for the Firefox device. You can use the [Node](https://github.com/IBM/event-notifications-node-admin-sdk#send-notifications){: external} or [Go](https://github.com/IBM/event-notifications-go-admin-sdk#send-notifications){: external} admin SDK instead of calling the API directly.

![Receive notifications](images/en-receive-push-firefox.png "Receive notifications"){: caption="Receive notifications" caption-side="bottom"}
