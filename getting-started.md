---

copyright:
  years: 2020, 2021
lastupdated: "2021-09-16"

keywords: event-notifications, event notification, getting started, getting started with event notifications

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:step: data-tutorial-type='step'}

# Getting started with {{site.data.keyword.en_short}}
{: #getting-started}

 {{site.data.keyword.en_full}} is a centralized alerts management service that notifies and alerts you to events occurring in your {{site.data.keyword.Bluemix_notm}} account. You can, in turn send a filtered notification to a set of your users, via notification destination of choice. These users need not be {{site.data.keyword.Bluemix_notm}} users. Instrument your applications with {{site.data.keyword.en_short}} SDKs, and use the {{site.data.keyword.en_short}} dashboard or {{site.data.keyword.en_short}} administrator API to create topics and destinations.
You can create subscriptions to associate destinations to topics and write rules to filter the specific notifications to the topic.
{: shortdesc}

#### Pricing plans

Currently, two pricing plans are on offer: **Lite**, and **Standard**

You need an {{site.data.keyword.cloud}} account. If you don't have an account, create one [here](https://cloud.ibm.com/registration/). Log in to your {{site.data.keyword.cloud}} account.
{: note }

Refer to {{site.data.keyword.en_short}} service [terms](/docs/event-notifications?topic=event-notifications-en-overview)

## Filtering capability
{: #en-getting-started-filtering}

{{site.data.keyword.en_full}} can restrict notifications to events of your choice and also route notifications for specific events to specific destinations.


Destinations that are currently supported include:

- Email
Uses {{site.data.keyword.Bluemix_notm}} provided email service to send emails to your recipients.
- SMS
Uses {{site.data.keyword.Bluemix_notm}} provided SMS function to send text notifications to your recipients.
- Webhooks
Send events from supported {{site.data.keyword.Bluemix_notm}} Services to Webhook destinations of your choice.

## Create an {{site.data.keyword.en_short}} service instance
{: #en-create-an-en-instance}

The basic steps that get you started:

### Log in to your {{site.data.keyword.Bluemix_notm}} account
{: #en-log-in}
{: step}

In the {{site.data.keyword.Bluemix_notm}} [catalog](https://test.cloud.ibm.com/catalog#services), search and select [{{site.data.keyword.en_short}}](https://test.cloud.ibm.com/catalog/services/event-notifications). The service configuration screen opens.

![Event Notifications configuration](images/en-select.png "Configuration screen"){: caption="Figure 1. Configuration screen" caption-side="bottom"}

### Select a region
{: #en-select}
{: step}

Currently, Dallas (us-south), London (eu-gb), and Sydney (au-syd) region is supported.

### Select a pricing plan
{: #en-pricing}
{: step}

Currently, only Lite and Standard pricing plans are defined. With the Lite plan, you get unlimited ingested events, 1 topic, and 100 outbound digital messages of any type per month.
With the Standard plan, you are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it, the incoming events are dropped and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

### Add a service name
{: #en-configure}
{: step}

Configure your resource with a service name, or use the preset name.

### Select a resource group
{: #en-resource}
{: step}

The resource group selection helps how you want resources to be organized in your account. The resource group that you select cannot be changed after the service instance is created.

### Define tags
{: #en-tags}
{: step}

Optionally, define Tags that are required to identify this service instance.

### Create the {{site.data.keyword.en_short}} service instance
{: #en-create}
{: step}

Click Create. A new service instance is created and the {{site.data.keyword.en_short}} console displayed.

![Event Notifications console](images/en-console.png "Console"){: caption="Figure 2. {{site.data.keyword.en_short}} console" caption-side="bottom"}






