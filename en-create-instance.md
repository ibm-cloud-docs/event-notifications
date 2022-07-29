---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-29"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Create an {{site.data.keyword.en_short}} service instance
{: #en-create-en-instance}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Take the steps that get you started by creating an {{site.data.keyword.en_short}} service instance.
{: shortdesc}

## Log in to your {{site.data.keyword.cloud_notm}} account
{: #en-log-in}
{: step}

In the {{site.data.keyword.cloud_notm}} [catalog](https://{DomainName}/catalog#services), search and select [{{site.data.keyword.en_short}}](https://{DomainName}/catalog/services/event-notifications). The service configuration screen opens.

## Select a location
{: #en-select}
{: step}

Select a `Location`. Currently, Dallas (us-south), London (eu-gb), Sydney (au-syd) and Frankfurt (eu-de) locations are supported.

## Select a pricing plan
{: #en-pricing}
{: step}

Currently, only `Lite` and `Standard` pricing plans are defined as follows:

* `Lite` plan: This plan gives you unlimited ingested events, 10 topics, two filters per topic, five destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks, and 1000 notifications per push destination. 10 subscriptions are allowed, and a subscription can have a maximum of three email recipients.

* `Standard` plan: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (in other words, the source is not associated with any topic), the incoming events are dropped, and you are not charged.  Outbound digital messages come in various types, and each type is priced separately.

   You can use **Pre-production destination**, as low-cost push destination, for your development and test environments. This feature is only available for `Standard` pricing plan.
   {: note}

## Add a service name
{: #en-configure}
{: step}

Configure your resource with a `Service name`, or use the preset name.

## Select a resource group
{: #en-resource}
{: step}

The resource group selection organizes your resources in your account. The resource group that you select cannot be changed after the service instance is created.

## Define tags
{: #en-tags}
{: step}

Define optional tags that identify this service instance.

## Create the {{site.data.keyword.en_short}} service instance
{: #en-create}
{: step}

Accept the licensing agreements and terms by clicking the checkbox.

Click `Create`. A new service instance is created and the {{site.data.keyword.en_short}} console is displayed.
