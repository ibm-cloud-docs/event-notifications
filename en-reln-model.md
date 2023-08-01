---

copyright:
  years: 2020, 2022
lastupdated: "2022-10-26"

keywords: event-notifications, event notifications, about event notifications

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.en_short}} relationship model
{: #en-relation}

{{site.data.keyword.en_short}} includes sources, filters, topics, destinations, and subscriptions. The relationship between these elements is shown in Figure 1.
{: shortdesc}

![{{site.data.keyword.en_short}} flow](images/en_relationshipmodelv3.png "{{site.data.keyword.en_short}} flow"){: caption="Figure 1. {{site.data.keyword.en_short}} relationship model" caption-side="bottom"}

Events originate outside {{site.data.keyword.en_short}}, for example, from {{site.data.keyword.cloud_notm}} services. An 'event source' within {{site.data.keyword.en_short}} represents a connection between {{site.data.keyword.en_short}} and one of these event-producing services.

Topics have associated filters that determine which source events are published. Topics can have multiple sources, each with their own filter. Topics isolate events of interest from various sources and aggregate them into one entity.

Subscriptions tie topics to destinations. While a single topic or destination can be associated with multiple subscriptions, a subscription is one-to-one, meaning it ties one topic to one destination. For service-to-human channels, one subscription can contain multiple recipients. For example, a subscription to an email destination is not restricted to just one email address but instead has a recipient list that might hold many addresses.

## Event notification flow
{: #en-flow}

When an event occurs in a registered source, the source sends an event notification to the {{site.data.keyword.en_short}} service. Based on the filters or conditions that are defined on the source, this incoming notification is targeted to one or several topics. The notification is delivered to all destinations, which are subscribed to the targeted topics.

## Event notification format
{: #en-format}

A notification sent to the {{site.data.keyword.en_short}} service must conform to the [CNCF](https://www.cncf.io/) [CloudEvents](https://cloudevents.io/) format.

## More about filters
{: #en-more-filter}

A filter is a conditional statement, which connects a source to a topic. Filters are written to route notifications of interest to a particular topic. All notifications that pass through the filters into a topic are then routed to the topic subscribers. Filtering is absent between topic and destination.

To simplify filtering, a source might include **event categories** in their notifications. Event categories are standard filter keys with the following hierarchy: Event Category -> Event Type -> Severity. Event categories simplify filtering because they appear as dropdown selection boxes when you are creating topics and filters in the {{site.data.keyword.en_short}} UI. For more advance filtering, use [JSONPath](https://jsonpath.com/) in the `Custom Filter` field. For more on JSONPath, see [JSONPath Online Evaluator](https://restfulapi.net/json-jsonpath/).
