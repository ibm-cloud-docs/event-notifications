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

# Event notification relationship model
{: #en-relation}

Cardinality principles and relationships that govern event notification flow from source to destination.
{: shortdesc}

![Event notification flow](images/en-overview1.png "Event notifications flow"){: caption="Figure 1. {{site.data.keyword.en_short}} relationship model" caption-side="bottom"}

## Event notification flow
{: #en-flow}

When an event occurs in a registered source, the source sends an event notification to the {{site.data.keyword.en_short}} service.  Based on the filters or conditions that are defined on the source, this incoming notification is targeted to one or several topics. The notification is delivered to all destinations, which are subscribed to the targeted topics. 

## Event notification format
{: #en-format}

A notification sent to the Event Notifications service must conform to the [CNCF](https://www.cncf.io/) [CloudEvents](https://cloudevents.io/) format.  


## More about filters
{: #en-more-filter}

A filter is a conditional statement, which connects a source to a topic.  Filters are written to route notifications of interest to a particular topic.  All notifications that pass through the filters into a topic are then routed to the topic subscribers.  Filtering is absent between topic and destination.

To simplify filtering, a source might include **event categories** in their notifications. Event categories are standard filter keys with hierarchy; Event Category -> Event Type -> Severity.  Event categories simplify filtering because they appear as dropdown selection boxes when you are creating topics and filters in the {{site.data.keyword.en_short}} UI. For more advance filtering, use [JSONPath](https://jsonpath.com/) in the <uicontrol>Custom Filter</uicontrol> field. More on JSONPath [here](https://restfulapi.net/json-jsonpath/).
