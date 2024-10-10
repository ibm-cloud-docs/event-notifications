---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-07"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite, standard
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} service instance
{: #en-create-en-instance}

Take the steps that get you started by creating an {{site.data.keyword.en_short}} service instance.
{: shortdesc}

1. Log in to your {{site.data.keyword.cloud_notm}} account
1. In the {{site.data.keyword.cloud_notm}} [catalog](/catalog#services), search and select [{{site.data.keyword.en_short}}](/catalog/services/event-notifications). The service configuration screen opens.
1. Select a `Location`. Currently, Dallas (us-south), London (eu-gb), Sydney (au-syd), Frankfurt (eu-de) and Madrid (eu-es) locations are supported.
1. Select a pricing plan. Currently, only `Lite` and `Standard` pricing plans are defined as follows:
   * `Lite` plan: This plan gives you unlimited ingested events, 10 topics, two filters per topic, five destinations, 20 outbound emails, 20 outbound SMSes, 20 outbound webhooks, and 1000 notifications per push destination. Ten subscriptions are allowed, and a subscription can have a maximum of three email recipients.
   * `Standard` plan: You are charged for ingested events and for outbound digital messages. An ingested event is one that is received and filtered. If a source is connected but no filters are defined for it (in other words, the source is not associated with any topic), the incoming events are dropped, and you are not charged. Outbound digital messages come in various types, and each type is priced separately.

   You can use **Pre-production destination**, as low-cost push destination, for your development and test environments. This feature is only available for `Standard` pricing plan.
   {: note}

1. Configure your resource with a `Service name`, or use the preset name.
1. Select a resource group. The resource group selection organizes your resources in your account. The resource group that you select cannot be changed after the service instance is created.
1. Define optional tags that identify this service instance.
1. Create the {{site.data.keyword.en_short}} service instance. Accept the licensing agreements and terms by clicking the checkbox.
1. Click `Create`. A new service instance is created and the {{site.data.keyword.en_short}} console is displayed.
