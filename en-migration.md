---

copyright:
  years: 2022
lastupdated: "2022-03-16"

keywords: event-notifications, event notifications migration, notifications, destinations, push, migration

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Migrate your apps from IBM Push Notifications service to {{site.data.keyword.en_full}}

## Introduction
{{site.data.keyword.en_full}} is an event notification routing service that notifies you to critical events that occur in your IBM Cloud account or triggers
automated actions by using webhooks. You can filter and route event notifications from your IBM Cloud account to Email, SMS, Webhooks and Push Notifications. 
You can migrate your mobile apps from the deprecated IBM Cloud Push Notifications service to {{site.data.keyword.en_short}} to continue to use Push. 
This guide outlines the steps to migrate your mobile apps and the backend to integrate with the {{site.data.keyword.en_short}} service.

Broadly there are 5 steps needed
* Create and configure a new instance of {{site.data.keyword.en_full}}
* Modify your Mobile app to work with the {{site.data.keyword.en_short}} service 
* Modify your backend to integrate with the new API of {{site.data.keyword.en_short}} service 
* Release the new version of the mobile app 

## New Instance of the {{site.data.keyword.en_short}} service

First you have to create a new instance of the {{site.data.keyword.en_short}} service.  For the purpose of this exercise, we will not use any advanced capabilities of 
the {{site.data.keyword.en_short}} service. Within the service, you will create an API source, a Topic, a Subscription and a destination as per the following diagram. 
For a more detailed explanation of the concepts of {{site.data.keyword.en_short}} you can refer to the [documentation](https://cloud.ibm.com/docs/event-notifications)

![Push capability in Event notifications](images/en-how-push-en.png "Push capability in Event Notifications"){: caption="Figure 1. Push capability in Event Notifications" caption-side="bottom"}

## Create Source
Create an API Source. This Source will represent the backend from which you will be sending the notifications from.

## Create Topic
Create a Topic where all the events from the backend will flow into. We will not do any filtering but define a filter that will send all events from the Source to this Topic.

## Create Destination
Create a Destination of the required platform. We will discuss more about the destinations in the mobile platform specific sections below.

## Create Subscription
Create a subscription from the topic to the Destination.

## Create Service Credentials
Create a new set of credentials with the role of “Device Manager” 

## Modify Android Mobile applications
The mobile app source code has to be modified to use the new Event Notifications SDKs. We will be replacing the existing Push Notifications service SDK to Event notifications FCM SDK.

## Create Android Destination
For the Android app a new Destination of type Android Push Notification (FCM) will have to be created. Here provide the Sender ID and Server Keyfrom your Google console. 

![Create Android destination](images/en-migration-android.png "Create Android destination"){: caption="Figure 2. Create Android destination" caption-side="bottom"}


## Modify your project in Firebase console 
The package name for the Push Notifications SDK was “com.ibm.mobilefirstplatform.clientsdk.android.push” . The new Event Notification SDK has the package “com.ibm.cloud.eventnotifications.destination.android”. 
You need to update your project in Firebase Console with the new package and downloadand replace the newgoogle-services.jsonfile in your Android project.

* Visit the [Firebase Console](https://console.firebase.google.com)

![Firebase console](images/en-migration-firebase-console.png "Firebase console"){: caption="Figure 3. Firebase Console" caption-side="bottom"}

* Select the project that you are using for Push Notifications. 

![Select project](images/en-migration-firebase-project.png "Select project"){: caption="Figure 4. Select project" caption-side="bottom"}

* In the navigation pane, select the settings icon next to the Project Overviewand select Settings > Project settings. 
Scroll down to locate “Your apps

![Project setting](images/en-migration-firebase-setting.png "Project setting"){: caption="Figure 5. Project setting" caption-side="bottom"}

* You will find an app with package name “com.ibm.mobilefirstplatform.clientsdk.android.push”. 
Click “Remove this app”. 

* Click “Add app” -> Choose Android -> Provide “com.ibm.cloud.eventnotifications.destination.android” as the package name -> Register App

![Register app](images/en-migration-firebase-addapp.png "Project setting"){: caption="Figure 6. Register app" caption-side="bottom"}

* Download the “google-services.json”. This file will be used later while modifying the app.

## Edit the Android app

* Add the Firebase google-services.json in the app module. 
* Change the Module’s build.gradlefile to include the new SDKs

![Modify build](images/en-migration-firebase-gradle.png "Modify build"){: caption="Figure 7. Modify build" caption-side="bottom"}

* Open the AndroidManifest.xml and change the following
* Change the <service> section to refer to the new service

![Modify manifest](images/en-migration-firebase-manifest.png "Modify manifest"){: caption="Figure 8. Modify manifest" caption-side="bottom"}

* Change the <activity> section to point to the new class

![Modify activity](images/en-migration-firebase-activity.png "Modify activity"){: caption="Figure 9. Modify activity" caption-side="bottom"}


* Next step is to change the import statements in the code. The new package name is com.ibm.cloud.eventnotifications.destination.android.*. 
Replace the old push import as shown below,

![Modify import](images/en-migration-firebase-import.png "Modify import"){: caption="Figure 10. Modify import" caption-side="bottom"}

* Initialize the new SDK  

![Initialize SDK](images/en-migration-firebase-sdk.png "Initialize SDK"){: caption="Figure 11. Initialize SDK" caption-side="bottom"}

There are additional fields like destinationID and apikey in new initialize() method.
Visit this [link](https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-service-access-management)for obtaining the apikey for client SDK. 

* Callback class in the new SDK has changes. Make changes in the listener

![Change listener](images/en-migration-firebase-sdk1.png "Change listener"){: caption="Figure 12. Change listener" caption-side="bottom"}

* Make changes in the device registration step 
If you are registering without userID

![Register without id](images/en-migration-firebase-registerwoutid.png "Register without id"){: caption="Figure 13. Register without id" caption-side="bottom"}

* If you are using registerDeviceWithUserId

![Register with id](images/en-migration-firebase-withid.png "Register with id"){: caption="Figure 14. Register with id" caption-side="bottom"}

* Make changes to the unregister API call.

![Change unregister API](images/en-migration-firebase-unregister.png "Modify unregister API"){: caption="Figure 15. Modify unregister API" caption-side="bottom"}

* Optionally, if you are using Tags.
Make the flowing changes to tag subscriptions

![Modify tag subscriptions](images/en-migration-firebase-tag.png "Modify tag subscriptions"){: caption="Figure 16. Modify tag subscriptions" caption-side="bottom"}

Changes to get all the tag subscription for the device

![Modify get all tag](images/en-migration-firebase-tag1.png "Modify get all tag"){: caption="Figure 17. Modify get all tag" caption-side="bottom"}

Make changes to tag unsubscribe

![Modify tag unsubscribe](images/en-migration-firebase-tagunsubscribe.png "Modify tag unsubscribe"){: caption="Figure 18. Modify tag unsubscribe" caption-side="bottom"}

* Optionally - If you are using Notification options, follow these changes
Initializing the class

![Initialize class](images/en-migration-firebase-initialize.png "Initialize class"){: caption="Figure 19. Initialize class" caption-side="bottom"}

Changes to Notification Button

![Modify notification button](images/en-migration-firebase-button.png "Modify notification button"){: caption="Figure 20. Modify notification button" caption-side="bottom"}

Changes to Notification category 

![Modify category](images/en-migration-firebase-category.png "Modify category"){: caption="Figure 21. Modify category" caption-side="bottom"}

Changes to the Notification actions listener

![Modify action listener](images/en-migration-firebase-actlistener.png "Modify action listener"){: caption="Figure 22. Modify action listener" caption-side="bottom"}

Your mobile app is ready to work with your new instance of Event Notifications.

## Modify iOS Mobile apps
The mobile app source code has to be modified to use the new Event Notifications SDKs. We will be replacing the existing Push Notifications service SDK to Event notifications iOS SDK.

## Create iOS Destination
For the iOS app a new Destination of type Apple Push Notification (APNs) will have to be created. Here provide the P12 or P8 and their configurations.

![Create iOS destination](images/en-migration-apns.png "Create iOS destination"){: caption="Figure 23. Create iOS destination" caption-side="bottom"}

## Edit the iOS application
Follow the below steps to migrate from BMPush to ENPushDestination
* Change the import statement

![Change import](images/en-migration-apns-import.png "Change import"){: caption="Figure 24. Change import" caption-side="bottom"}

* Replace SDK Initialization code as follows

![Replace SDK initialize](images/en-migration-apns-initialize.png "Replace SDK initialize"){: caption="Figure 25. Replace SDK initialize" caption-side="bottom"}

There are additional fields like destinationID and apikey in new initialize() method.
Visit this [link](https://cloud.ibm.com/docs/event-notifications?topic=event-notifications-service-access-management) for obtaining the apikey for client SDK.

* Make changes in the device registration step 
If you are registering without userID

![Register withoutid](images/en-migration-apns-woutuid.png "Register withoutid"){: caption="Figure 26. Register withoutid" caption-side="bottom"}

If you are using user ID for registration

![Register withid](images/en-migration-apns-withuid.png "Register withid"){: caption="Figure 27. Register with id" caption-side="bottom"}

Make changes to the unregister API call
![Change unregister](images/en-migration-apns-unreg.png "Change unregister"){: caption="Figure 28. Change unregister" caption-side="bottom"}


Optionally – if you are using Tags
Make the flowing changes to tag subscriptions
![Change tag subscription](images/en-migration-apns-tagsubscribe.png "Change tag subscription"){: caption="Figure 29. Change tag subscription" caption-side="bottom"}


Changes to get all the tag subscription for the device
![Change get all](images/en-migration-apns-tagall.png "Change get all"){: caption="Figure 30. Change get all" caption-side="bottom"}


Make changes to tag unsubscribe
![Change tag unsubscribe](images/en-migration-apns-modifytag.png "Change tag unsubscribe"){: caption="Figure 31. Change tag unsubscribe" caption-side="bottom"}


* Optionally -If you are using Notification options, follow these changes
Initializing the class
![Class initialization](images/en-migration-apns-classinit.png "Class initialization"){: caption="Figure 32. Class initialization" caption-side="bottom"}


Changes to Notification Button
![Change notification button](images/en-migration-apns-button.png "Change notification button"){: caption="Figure 33. Change notification button" caption-side="bottom"}


Changes to Notification category
![Change notification category](images/en-migration-apns-category.png "Change notification category"){: caption="Figure 34. Change notification category" caption-side="bottom"}


Your mobile app is ready to work with your new instance of Event Notifications.

## Modify the backend
This section contains the steps required to be performed in the backend side.  The send notification API has changed and hence all the SDKs as well. 

## If you are using the Node.js SDK 
The existing Node SDK will have to be migrated to the new Event Notifications SDK. Follow this link for the new Node Admin SDK documentation. 
* Changes in importing the SDK
![Import SDK](images/en-migration-importsdk.png "MImport SDK"){: caption="Figure 35. Import SDK" caption-side="bottom"}


* Changes in initializing the SDK
![Initialize SDK](images/en-migration-initializesdk.png "Initialize SDK"){: caption="Figure 36. Initialize SDK" caption-side="bottom"}


* Changes in creating notification targets
![Create targets](images/en-migration-targets.png "Create targets"){: caption="Figure 37. Create targets" caption-side="bottom"}


* Changes in the FCM style payload
![Change FCM Style](images/en-migration-fcmstyle.png "Change FCM Style"){: caption="Figure 38. Change FCM Style" caption-side="bottom"}


* Changes in FCM message body
![Change FCM message body](images/en-migration-messagebody.png "Change FCM message body"){: caption="Figure 39. Change FCM message body" caption-side="bottom"}


* Changes in Send notification method
![Change send method](images/en-migration-sendmethod.png "Change send method"){: caption="Figure 40. Change send method" caption-side="bottom"}


## If you are using REST API
This section contains the details about the modifications required for Send Notifications API. In the new API we have additional parameters
in the request body. The required parameters for Android push notifications are as given below
![Modification to REST API1](images/en-migration-restapi1.png "Modification to REST API1t"){: caption="Figure 41. Modification to REST API1" caption-side="bottom"}


For a detailed description of the event attributes please see the EN event attribute definition.

![Modification to REST API2](images/en-migration-restapi2.png "Modification to REST API2"){: caption="Figure 42. Modification to REST API2" caption-side="bottom"}


* `target` field is replaced by `ibmenpushto`
* `message` field is removed. The alert, url fields are part of the `ibmenfcmbody`
* `settings->gcm` is replaced by `ibmenfcmbody`

The ibmenpushto fields can take four values same as `target` of push API
1. tags –array of tag names
2. user_ids –array of user ids. 
3. fcm_devices–array of device Ids.
4. platforms –the target device platform. 

The ibmenfcmbody field contains every field in the settings-> gcmfield of IBM Cloud Push notifications service, but with some changes, 
1. All fields are in snake case instead of camel case. For examples,interactiveCategorywill be interactive_category. 
2. We don’t support the channels and channel groups. 


## Migrate the data from Push Notifications service to IBM Cloud Event Notifications Service

You can use this [tool](https://github.com/Event-Notifications/push-en-migration-tool) to migrate the devices and tag subscriptions data from Push Notifications service to IBM Cloud Event Notifications service.

## Release new version of the app

After the integration is complete –the new version of the App will have to be released. In the new version ask the user permission to send notification and register the device again.In the overlapping window when the user population is migrating from the old version of the app to the new version, the notifications may have to be sent to the existing Push Notification environment as well as the new Event Notifications environment.





