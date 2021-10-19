---

copyright:
  years: 2020, 2021
lastupdated: "2021-11-29"

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


# {{site.data.keyword.en_short}} terms and use cases
{: #en-overview}



## Event
{: #en-event}
An occurrence of something of interest that is associated with {{site.data.keyword.Bluemix_notm}} platform or services and apps that run on it.  

## Event notification
{: #en-eventn}
A digitized message that is triggered when an event has occurred. Event notifications come in to the {{site.data.keyword.en_short}} service from event sources. Sometimes "event notification" is shortened to "event" or "notification" in the context of the {{site.data.keyword.en_short}} service.

## Event source
{: #en-source}

A service or application on {{site.data.keyword.Bluemix_notm}} that emits event notifications and publishes them to a topic within the {{site.data.keyword.en_short}} service. A source is a registered entity in an {{site.data.keyword.en_short}} service instance. Several services on {{site.data.keyword.Bluemix_notm}} are integrated to send notifications to {{site.data.keyword.en_short}}.
Examples include {{site.data.keyword.compliance_long}}, IBM Monitoring, and {{site.data.keyword.secrets-manager_full_notm}}. A source can publish to multiple topics. In other contexts sources can also be identified as producers or publishers.

## Filter
{: #en-filters}

A mechanism for selectively passing event notifications from a source into a topic.  A topic has an independent filter for each source connected to it. 

### Condition
{: #en-conditions}

One of many criteria used for filtering. {{site.data.keyword.en_short}} whose attributes match a condition are passed through to a topic. {{site.data.keyword.en_short}} whose attributes do not match a condition are dropped.

## Ingested event notification
{: #en-ingested}

- An event notification that is evaluated by a filter.  Ingested events is a primary billing metric. The price for ingested events is the same for all sources. If no filter is defined for a given source, none of the events from that source are ingested. 

- If a filter is defined for a given source but no event notifications are passed through, the number of notifications which bounced are still considered "ingested" because they were analyzed by a filter. 

## Topic
{: #en-topics}

- A landing place for filtered events. Topics hold a set of incoming event notifications of interest.  Each source is connected to a topic through a user-defined filter. Notifications that pass into a topic are pushed to all subscribed destinations. A topic can connect to multiple sources. 

-  Event notifications that end up in a topic are routed to destinations. A topic can be connected to multiple sources. Although topics are innately coupled to sources (via filters), they are not innately coupled to destinations. That coupling happens through subscriptions.

## Destination
{: #en-destinations}

A delivery target for event notifications.  In other contexts, destinations may be known as channels, sinks, consumers, or subscribers.

- Human destination: A device, server, or application presents notifications for human consumption.  Examples of human destinations are email servers, SMS text providers, and push notification services. 

   Specific email addresses, phone numbers, and device IDs may be part of a subscription to a destination, but they are not part of the destination itself.
   {:note: .note}
- Service destinations: A cloud service or an application where notifications are consumed programmatically. A webhook to a backend microservice is an example of a service destination.

### Service-to-service 
{: #en-destinations-s2s}

A way to describe a notification that travels from a cloud service to a service destination. In other contexts, service-to-service may be known as app-to-app.

### Service-to-human
{: #en-destinations-s2h}

A way to describe a notification that travels from a cloud service to a human destination.  In other contexts, service-to-human may be known as app-to-person.

## Subscription
{: #en-subscriptions}

An association of one topic to one destination.  If a destination requires additional information to operate correctly (e.g. email addresses for an email destination), then that information is included in the subscription.

## Subscriber
{: #en-subscriber}

An entity that is targeted by a subscription. For webhooks, the webhook host is the subscriber. For human destinations, email addresses and phone numbers (or the people who own them) are subscribers.

One subscription can only have one destination, but it may have many subscribers within that destination. 
{:note: .note}

## Outbound digital message
{: #en-outbound}

An event notification send from the Event Notifications service to a subscriber. Outbound digital messages is a primary billing metric for the {{site.data.keyword.en_short}} service. The price for outbound digital messages varies by destination (e.g. outbound digital messages to SMS are priced differently than outbound digital messages to email).In most cases a dispatch (attempt to deliver) is considered an outbound digital message, regardless of whether or not the delivery was successfully.

## Digital message origin
{: #en-outbound-origin}

The originating phone number or origin ID for a text message, and the originating domain or IP address for email.  In most countries the sender is obligated by law to be transparent about the origin of a digital message. If you select the IBM SMS Service or IBM Email Service as a destination for your subscriptions, the text messages the end user will receive will have an origin owned by IBM.   

## SMS message
{: #en-sms}

A text message in **Simple Messaging Service** format.

### SMS message segment
{: #en-sms-segemnt}

A group of 160 characters within an SMS text message.  A single message may contain many segments. Each message segment counts as one outbound digital message for billing purposes.

### SMS unit
{: #en-sms-unit}

A pricing unit for SMS text messages.

### Preventing spam
{: #en-sms-spam}

