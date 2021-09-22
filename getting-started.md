---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-20"

keywords:

subcollection:

content-type: tutorial
services:
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.en_short}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="10m"}

{{site.data.keyword.en_full}} is a centralized alerts management service that notifies and alerts you to events occurring in your {{site.data.keyword.Bluemix_notm}} account. You can, in turn send a filtered notification to a set of your users.
You can create subscriptions to associate destinations to topics and write rules to filter specific notifications to the topic.
In this tutorial, we'll take you through the steps to get started.
{: shortdesc}

## Pricing plans

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

The basic steps that get you started:

1. [Create an {{site.data.keyword.en_short}} service instance](/docs/event-notifications?topic=event-notifications-en-create-en-instance)
1. [Create a topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic)
1. [Define rules for a topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic#en-topic-rules)
1. [Select a destination](/docs/event-notifications?topic=event-notifications-en-create-en-destination)
1. [Create a subscription by associating a destination with a topic](/docs/event-notifications?topic=event-notifications-en-create-en-subscription)
