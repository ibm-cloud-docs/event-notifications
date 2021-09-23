---

copyright:
  years: 2020, 2021
lastupdated: "2021-08-18"

keywords: event-notifications, event notifications, about event notifications

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


#  {{site.data.keyword.en_short}} terms
{: #en-overview}

This document lists the standard terms and their definitions that are used in the {{site.data.keyword.en_short}} services.

<!-- ![Overview](images/en-overview.png "Overview diagram"){: caption="Figure 1.{{site.data.keyword.en_short}} overview" caption-side="bottom"} -->

## Source
{: #en-source}

 {{site.data.keyword.en_short}} originate from sources. A source is a registered entity in an {{site.data.keyword.en_short}} service instance that publishes notifications. In the current release, sources are limited to those entities categorized as IBM Source.

### IBM Source
An IBM Source is a source in {{site.data.keyword.en_short}} where notifications are published from an {{site.data.keyword.Bluemix_notm}} service. Several services on {{site.data.keyword.Bluemix_notm}} are integrated to sent notifications to {{site.data.keyword.en_short}}. Examples include {{site.data.keyword.compliance_short}}, {{site.data.keyword.prf_hubshort}}, and {{site.data.keyword.secrets-manager_short}}.  

**Service to Service Authorization** is used to enable an IBM Service to publish notifications to the {{site.data.keyword.en_short}} service. A customer who is interested in notifications from an IBM service must authorize such a source service to publish to an instance of the {{site.data.keyword.en_short}} service.      

## Topic
{: #en-topics}

A logical entity, which connects one or more sources to destinations, a topic logically groups multiple sources based on pre-defined filters, and targets notifications from such a group to multiple destinations.
Topics help decouple sources and destinations. A source for a notification does not need to be aware of all the destinations that it targets to.

## Filter
{: #en-filters}

A filter is a conditional statement, which connects a source to a topic. Filters are written to route notifications of interest to a particular topic. Notifications passing the conditional statement of the filter continues through the {{site.data.keyword.en_short}} system and be delivered to all the destinations that are subscribed to the same topic.

   - More details on [JSONPath](https://jsonpath.com/) and [JSON with JSONPath](https://restfulapi.net/json-jsonpath/)

   Multiple sources can route to a topic by defining a filter for each such source - topic connection.
   A source can also route to multiple topics.



## Destination
{: #en-destinations}

Destinations represent locations to which notifications are to be delivered. Destinations can be categorized as human or an app.
   - Examples of human destinations include SMS, email, Push Notifications, and Slack
   - Examples of Application or Service destinations include Webhooks, Event Streams(Kafka), Elastic Search

{{site.data.keyword.en_short}} supports the following destinations:
   - Email: Email is a pre-defined destination, with SendGrid as the email provider. All emails from {{site.data.keyword.en_short}} service are sent from a fixed IBM email-id.
   - SMS: SMS is a pre-defined destination. An IBM-owned number and Twilio the service platform is used to support text messaging.
   - Webhooks: Customers can use webhook destinations to process notifications from the {{site.data.keyword.en_short}} service. Customers can also write their own custom applications to receive notifications from {{site.data.keyword.en_short}} service. Such an application is defined as a webhook destination.
   Webhook signing: {{site.data.keyword.en_short}} provides an option for users to authenticate the notification payload. This option enables the webhook to validate that the incoming notification is from a trusted source - that is, {{site.data.keyword.en_short}} service.

## Subscription
{: #en-subscriptions}

Destinations subscribe to topics. Multiple destinations can subscribe to a single topic.
An email subscription is a list of all emails IDs, and an SMS subscription is a list of all phone numbers that a notification is routed to. A webhook subscription links a webhook destination to a topic.


## Notification
{: #en-notifications}

Whenever an event occurs in a registered source, a notification is sent to the {{site.data.keyword.en_short}} service. Based on the filters or conditions that are defined on such a registered source, this incoming notification is targeted to one or several topics. The notification is then delivered to all destinations subscribed to these targeted topics. A notification sent to {{site.data.keyword.en_short}} must be of a pre-defined format, as defined here. (link)

## Event Category
{: #en-categories}

When a source is registered into {{site.data.keyword.en_short}}, one can additionally (and optimally) define an Event Category for the source, which identifies notifications from a particular source that might be of interest. Event Category hierarchy reads in the order, Event Category, Event Type, and Severity.
The benefit of defining event categories is that the {{site.data.keyword.en_short}} UI displays these categories in the <wintitle>topics </wintitle> page where filters are created. The customer can easily select common categories from such a dropdown, while advanced filters can be handwritten in JSONPath format.
