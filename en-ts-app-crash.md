---

copyright:
  years: 2022
lastupdated: "2022-07-15"

keywords: question about event notifications, permission, integrating, authorization, authorize

subcollection: event-notifications

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why my application crashes when registering a device on Android 6.0?
{: #troubleshoot-app-crash}
{: troubleshoot}
{: support} 

Your application crashes when you tried to register a device on Android version 6.0.
{: shortdesc}

Application crashes during device registration. 
{: tsSymptoms}

This is due to Android version 6.0 and is specific to this version alone..
{: tsCauses}

Updated your app's `build.gradle` file with the following code:
{: tsResolve}

```groovy
dependencies {
	........
	implementation('com.google.guava:guava') {
		version { strictly '29.0-android' }
	}
	........
}
```
{: codeblock}

