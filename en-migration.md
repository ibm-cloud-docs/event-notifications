---

copyright:
  years: 2022
lastupdated: "2022-03-25"

keywords: event-notifications, event notifications migration, notifications, destinations, push, migration

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Migrate your apps from {{site.data.keyword.mobilepushfull}} service to {{site.data.keyword.en_full}}
{: #en-migrate-apps}

You can migrate your mobile apps from the deprecated IBM Cloud Push Notifications service to {{site.data.keyword.en_short}} to continue to use Push. 
{: shortdesc}

## Introduction
{: #en-migrate-intro}

{{site.data.keyword.en_short}} is a routing service that tells you about critical events that occur in your {{site.data.keyword.Bluemix_notm}} account. You can filter and route {{site.data.keyword.en_full}} from {{site.data.keyword.Bluemix_notm}} services like Monitoring, Security and Compliance Center, and Secrets Manager to communication channels like email, SMS, push notifications, and webhooks.

This guide outlines the steps to migrate your mobile apps and the backend to integrate with the {{site.data.keyword.en_short}} service.

Take the following steps to migrate your mobile apps:

* Create and configure an instance of {{site.data.keyword.en_full}}
* Modify your Android or iOS mobile app to work with the {{site.data.keyword.en_short}} service 
* Modify your backend to integrate with the new API of the {{site.data.keyword.en_short}} service 
* Release the new version of the mobile app 

## Create and configure an instance of the {{site.data.keyword.en_short}} service
{: #en-migrate-create}
{: step}

Create an instance of the {{site.data.keyword.en_short}} service. This procedure does not use any advanced capabilities of the {{site.data.keyword.en_short}} service. Within the service, you create an API source, a topic, a subscription, and a destination as outlined in figure 1. 
For a more detailed explanation of the concepts of {{site.data.keyword.en_short}}, see [Getting started with {{site.data.keyword.en_full}}](/docs/event-notifications?topic=event-notifications-getting-started).

![Push capability in {{site.data.keyword.en_short}}](images/en-how-push-en.png "Push capability in {{site.data.keyword.en_short}}"){: caption="Figure 1. Push capability in {{site.data.keyword.en_short}}" caption-side="bottom"}

### Create a source
{: #en-migrate-create-source}

Create an API source. This source represents the backend from which you send the notifications. 


### Create a topic
{: #en-migrate-create-topic}

Create a topic where all the events from the backend flow into. However, this topic does not do any filtering, define a filter that sends all events from the source to this topic.

### Create a destination
{: #en-migrate-create-destination}

Create a destination of the required type. 

### Create a subscription
{: #en-migrate-create-subscription}

Create a subscription from the topic to the destination.

### Create service credentials
{: #en-migrate-create-credentials}

Create a set of credentials with the role of “Device Manager”.

## Modify an Android mobile application
{: #en-migrate-modify-android}
{: step}


Modify the mobile app source code to use the new {{site.data.keyword.en_short}} SDKs. You replace the existing {{site.data.keyword.mobilepushshort}} service SDK with the {{site.data.keyword.en_short}} FCM SDK.

### Create an Android destination
{: #en-migrate-create-android-destination}

Create a destination of type `Android Push Notification` (FCM) for the Android app. Provide the Sender ID and Server Key from your Google console. 

![Create Android destination](images/en-migration-android.png "Create Android destination"){: caption="Figure 2. Create Android destination" caption-side="bottom"}

### Modify your project in Firebase console
{: #en-migrate-modify-project-firebase}

The package name for the {{site.data.keyword.mobilepushshort}} SDK was `com.ibm.mobilefirstplatform.clientsdk.android.push`. The new Event Notification SDK has the package `com.ibm.cloud.eventnotifications.destination.android`. Update your project in Firebase Console with the new package, then download and replace the new `google-services.jsonfile` in your Android project.

1. Go to the [Firebase Console](https://console.firebase.google.com)

   ![Firebase console](images/en-migration-firebase-console.png "Firebase console"){: caption="Figure 3. Firebase Console" caption-side="bottom"}

1. Select the project that you are using for {{site.data.keyword.mobilepushshort}}. 

   ![Select project](images/en-migration-firebase-project.png "Select project"){: caption="Figure 4. Select project" caption-side="bottom"}

1. In the navigation panel, select the **Settings** icon next to the **Project Overview** and select **Settings > Project settings**. Scroll down to locate **Your apps**.

   ![Project setting](images/en-migration-firebase-setting.png "Project setting"){: caption="Figure 5. Project setting" caption-side="bottom"}

1. Find an app with package name `com.ibm.mobilefirstplatform.clientsdk.android.push` and click **Remove this app**. 

1. Click **Add app > Choose Android**

1. Enter `com.ibm.cloud.eventnotifications.destination.android` as the package name and click **Register App**. 

   ![Register app](images/en-migration-firebase-addapp.png "Project setting"){: caption="Figure 6. Register app" caption-side="bottom"}

1. Download `google-services.json`. You use this file later when you modify the app.


### Edit the Android app
{: #en-migrate-edit-andriod-app}

1. Add the Firebase `google-services.json` in the app module.

1. Change the Module’s `build.gradlefile`to include the new SDKs.

   ![Modify build](images/en-migration-firebase-gradle.png "Modify build"){: caption="Figure 7. Modify build" caption-side="bottom"}

1. Open `AndroidManifest.xml` and change the following elements:

   - Change the `<service>` section to refer to the new service

   ![Modify manifest](images/en-migration-firebase-manifest.png "Modify manifest"){: caption="Figure 8. Modify manifest" caption-side="bottom"}

   - Change the `<activity>` section to point to the new class

   ![Modify activity](images/en-migration-firebase-activity.png "Modify activity"){: caption="Figure 9. Modify activity" caption-side="bottom"}

1. Change the import statements in the code. The new package name is `com.ibm.cloud.eventnotifications.destination.android.*`. Replace the old push import as shown:

   ![Modify import](images/en-migration-firebase-import.png "Modify import"){: caption="Figure 10. Modify import" caption-side="bottom"}

1. Initialize the new SDK  

   ![Initialize SDK](images/en-migration-firebase-sdk.png "Initialize SDK"){: caption="Figure 11. Initialize SDK" caption-side="bottom"}

   There are additional fields like `destinationID` and `apikey` in the new `initialize()` method.

   For more information, on getting the `apikey` for client SDK see [Managing service access](/docs/event-notifications?topic=event-notifications-service-access-management). 

1. The callback class in the new SDK has changes. Make these changes in the listener.

   ![Change listener](images/en-migration-firebase-sdk1.png "Change listener"){: caption="Figure 12. Change listener" caption-side="bottom"}

1. Make changes to the device registration step.

   - If you are registering without `userID`

   ![Register without id](images/en-migration-firebase-registerwoutid.png "Register without id"){: caption="Figure 13. Register without id" caption-side="bottom"}

   - If you are using `registerDeviceWithUserId`

   ![Register with id](images/en-migration-firebase-withid.png "Register with id"){: caption="Figure 14. Register with id" caption-side="bottom"}

1. Make changes to the unregister API call.

   ![Change unregister API](images/en-migration-firebase-unregister.png "Modify unregister API"){: caption="Figure 15. Modify unregister API" caption-side="bottom"}

1. Optionally, if you are using tags

   - Change the tag subscriptions as follows:

   ![Modify tag subscriptions](images/en-migration-firebase-tag.png "Modify tag subscriptions"){: caption="Figure 16. Modify tag subscriptions" caption-side="bottom"}

   - Changes to get all the tag subscription for the device

   ![Modify get all tag](images/en-migration-firebase-tag1.png "Modify get all tag"){: caption="Figure 17. Modify get all tag" caption-side="bottom"}

   - Make changes to tag unsubscribe

   ![Modify tag unsubscribe](images/en-migration-firebase-tagunsubscribe.png "Modify tag unsubscribe"){: caption="Figure 18. Modify tag unsubscribe" caption-side="bottom"}

1. Optionally, if you are using Notification options, make the following changes:

   - Initializing the class

   ![Initialize class](images/en-migration-firebase-initialize.png "Initialize class"){: caption="Figure 19. Initialize class" caption-side="bottom"}

   - Changes to Notification button

   ![Modify notification button](images/en-migration-firebase-button.png "Modify notification button"){: caption="Figure 20. Modify notification button" caption-side="bottom"}

   - Changes to Notification category 

   ![Modify category](images/en-migration-firebase-category.png "Modify category"){: caption="Figure 21. Modify category" caption-side="bottom"}

1. Changes to the Notification actions listener

   ![Modify action listener](images/en-migration-firebase-actlistener.png "Modify action listener"){: caption="Figure 22. Modify action listener" caption-side="bottom"}

Your Android mobile app is ready to work with your new instance of {{site.data.keyword.en_full}}.

## Modify an iOS mobile application
{: #en-migrate-modify-ios}
{: step}

Modify the mobile app source code to use the new {{site.data.keyword.en_short}} SDKs. You will replace the existing {{site.data.keyword.mobilepushshort}} service SDK with the {{site.data.keyword.en_short}} FCM SDK.

### Create an iOS destination
{: #en-migrate-create-ios-destination}

Create a destination of type Apple Push Notification (APNs) for the iOS app. Provide the P12 or P8 and their configurations.

![Create iOS destination](images/en-migration-apns.png "Create iOS destination"){: caption="Figure 23. Create iOS destination" caption-side="bottom"}

### Edit the iOS application
{: #en-migrate-edit-ios-app}

Follow these steps to migrate from BMPush to ENPushDestination:

1. Change the import statement

   ![Change import](images/en-migration-apns-import.png "Change import"){: caption="Figure 24. Change import" caption-side="bottom"}

1. Replace SDK Initialization code

   ![Replace SDK initialize](images/en-migration-apns-initialize.png "Replace SDK initialize"){: caption="Figure 25. Replace SDK initialize" caption-side="bottom"}

   There are extra fields like `destinationID` and `apikey` in new `initialize()` method. For more information, on getting the `apikey` for client SDK see [Managing service access](/docs/event-notifications?topic=event-notifications-service-access-management). 

1. Change the device registration step

   - If you are registering without `userID`

   ![Register withoutid](images/en-migration-apns-woutuid.png "Register withoutid"){: caption="Figure 26. Register withoutid" caption-side="bottom"}

   - If you are using user ID for registration

   ![Register withid](images/en-migration-apns-withuid.png "Register withid"){: caption="Figure 27. Register with id" caption-side="bottom"}

1. Change the unregister API call

   ![Change unregister](images/en-migration-apns-unregeg.png "Change unregister"){: caption="Figure 28. Change unregister" caption-side="bottom"}


1. Optionally, if you are using tags:

   - Change the tag subscriptions as follows:

   ![Change tag subscription](images/en-migration-apns-tagsubscribe.png "Change tag subscription"){: caption="Figure 29. Change tag subscription" caption-side="bottom"}

   - Changes to the get all tag subscription for the device

   ![Change get all](images/en-migration-apns-tagall.png "Change get all"){: caption="Figure 30. Change get all" caption-side="bottom"}

   - Changes to the tag unsubscribe

   ![Change tag unsubscribe](images/en-migration-apns-modifytag.png "Change tag unsubscribe"){: caption="Figure 31. Change tag unsubscribe" caption-side="bottom"}

1. Optionally, if you are using **Notification options**, make the following changes:

   - Initialize the class

   ![Class initialization](images/en-migration-apns-classinit.png "Class initialization"){: caption="Figure 32. Class initialization" caption-side="bottom"}

   - Change the Notification button

   ![Change notification button](images/en-migration-apns-button.png "Change notification button"){: caption="Figure 33. Change notification button" caption-side="bottom"}

   - Change the Notification category

   ![Change notification category](images/en-migration-apns-category.png "Change notification category"){: caption="Figure 34. Change notification category" caption-side="bottom"}

Your iOS mobile app is ready to work with your new instance of {{site.data.keyword.en_full}}.

## Modify the back end
{: #en-migrate-modify-backend}
{: step}

This section contains the steps that you perform in the back end. The send notification API is changed and therefore all the SDKs change also. 

### If you are using the `Node.js` SDK 
{: #en-migrate-using-nodejs}

Migrate the existing Node SDK to the new {{site.data.keyword.en_full}} SDK. Follow this link for the new Node Admin SDK documentation. 

1. Changes to importing the SDK

   ![Import SDK](images/en-migration-importsdk.png "MImport SDK"){: caption="Figure 35. Import SDK" caption-side="bottom"}


1. Changes to initializing the SDK

    ![Initialize SDK](images/en-migration-initializesdk.png "Initialize SDK"){: caption="Figure 36. Initialize SDK" caption-side="bottom"}


1. Changes to creating notification targets

   ![Create targets](images/en-migration-targets.png "Create targets"){: caption="Figure 37. Create targets" caption-side="bottom"}

1. Changes to the FCM style payload

   ![Change FCM Style](images/en-migration-fcmstyle.png "Change FCM Style"){: caption="Figure 38. Change FCM Style" caption-side="bottom"}

1. Changes to FCM message body

   ![Change FCM message body](images/en-migration-messagebody.png "Change FCM message body"){: caption="Figure 39. Change FCM message body" caption-side="bottom"}

1. Changes to Send notification method

   ![Change send method](images/en-migration-sendmethod.png "Change send method"){: caption="Figure 40. Change send method" caption-side="bottom"}


### If you are using REST API
{: #en-migrate-using-restapi}

This section contains the details about the modifications that are required for Send Notifications API. The new API has extra parameters in the request body. The required parameters for Android push notifications are as follows:

![Modification to REST API1](images/en-migration-restapi1.png "Modification to REST API1t"){: caption="Figure 41. Modification to REST API1" caption-side="bottom"}

For a detailed description of the event attributes, see the {{site.data.keyword.en_full}} event attribute definition.

![Modification to REST API2](images/en-migration-restapi2.png "Modification to REST API2"){: caption="Figure 42. Modification to REST API2" caption-side="bottom"}

* `target` field is replaced by `ibmenpushto`
* `message` field is removed. The `alert`, `url` fields are part of the `ibmenfcmbody`
* `settings->gcm` is replaced by `ibmenfcmbody`

The `ibmenpushto` fields can take four values same as `target` of push API

1. tags –array of tag names
1. user_ids –array of user ids 
1. fcm_devices –array of device Ids
1. platforms –the target device platform 

The `ibmenfcmbody` field contains every field in the **settings-> gcmfield** of  service, but with the following changes:

1. All fields are in snake case instead of camel case. For example, `interactiveCategory` is `interactive_category`. 
1. Channels and channel groups {{site.data.keyword.mobilepushshort}}are not supported. 

## Migrate the data from {{site.data.keyword.mobilepushshort}} service to {{site.data.keyword.en_full}} service
{: #en-migrate-final}
{: step}

You can use the [push-en-migration-tool](https://github.com/Event-Notifications/push-en-migration-tool) to migrate the devices and tag subscriptions data from {{site.data.keyword.mobilepushshort}} service to the {{site.data.keyword.en_full}} service.

## Release a new version of the app
{: #en-migrate-release-app}
{: step}

After the integration is complete, release the new version of the app. In the new version, ask the user's permission to send a notification and register the device again. In the overlapping window when the user population is migrating from the old version of the app to the new version, the notifications might have to be sent to the existing {{site.data.keyword.mobilepushshort}} environment and the new {{site.data.keyword.en_full}} environment.
