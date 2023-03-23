---

copyright:
  years: 2023
lastupdated: "2023-03-24"

keywords: event-notifications, event notifications, about event notifications, destinations, code engine

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Code Engine
{: #en-destinations-codeengine}

{{site.data.keyword.codeenginefull}} is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeengineshort}} represents a service destination, where an incoming notification can be consumed programmatically. For example, an incoming notification about an event can trigger a {{site.data.keyword.codeengineshort}} destination to a backend microservice to act based on the content of the incoming notification.
{: shortdesc}

## Configuring a {{site.data.keyword.codeengineshort}} destination
{: #en-codeengine-configure}

You can configure a {{site.data.keyword.cloud_notm}} {{site.data.keyword.codeengineshort}} destination in the `Destinations` tab. As part of the configuration, enter the secured URL (only HTTPS), and select the Verb to be called (GET or POST). You can also enter authorization headers to the destination {{site.data.keyword.codeengineshort}}. Create a subscription to associate the {{site.data.keyword.codeengineshort}} destination to a topic.

## {{site.data.keyword.codeengineshort}} signing
{: #en-codeengine-sign}

To identify that the incoming notification is coming from {{site.data.keyword.en_full_notm}}, you can enable {{site.data.keyword.codeengineshort}} signing. If signing is enabled, a public key can be downloaded, and used to decrypt the incoming notification content.

## {{site.data.keyword.codeengineshort}} retry policy
{: #en-codengine-retry}

When calling {{site.data.keyword.codeengineshort}}, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services ({{site.data.keyword.codeengineshort}}).

In addition, the following timeout conditions cause the {{site.data.keyword.codeengineshort}} call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the URL fails even after retry attempts, the notification is lost.
{: note}
