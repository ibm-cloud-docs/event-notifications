---

copyright:
  years: 2020, 2025
lastupdated: "2025-05-30"

keywords: event-notifications, event notifications, about event notifications, destinations, webhook

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Webhooks
{: #en-destinations-webhook}

A webhook represents a service destination, where an incoming notification can be consumed programmatically. For example, an incoming notification about an event can trigger a webhook destination to a backend microservice to act based on the content of the incoming notification.
{: shortdesc}

## Configuring a webhook destination
{: #en-webhook-configure}

You can configure a webhook destination in the `Destinations` tab. As part of the configuration, enter the webhook URL, and the REST API verb to be called when the webhook is called. You can also enter authorization headers to the destination webhook. Create a subscription to associate the webhook destination to a topic.

## Supported HTTP Verbs
{: #en-supported-verbs}

{{site.data.keyword.en_short}} webhooks support the http verbs GET, POST, PUT, and PATCH.

- GET : Retrieves a representation of the specified resource.
- POST : Creates a new resource.
- PUT : Replaces the entire resource with the provided data.
- PATCH : Applies partial modifications to a resource.

## Webhook signing
{: #en-webhook-sign}

To identify that the incoming notification is coming from {{site.data.keyword.en_full_notm}}, you can enable webhook signing. If signing is enabled, a public key can be downloaded, and used to decrypt the incoming notification content.

## Allowlisting IP addresses
{: #en-allowlisting}

You can allowlist the ranges of IP addresses to restrict access to your servers that receive webhooks. For more information, see [webhook IP addresses](/docs/support?topic=support-webhook-ips).

Regardless of the location of the Event Notifications Service instance, to help ensure uninterrupted webhook traffic that you should add the IP ranges of all regions to your allowlist.

## Webhook retry policy
{: #en-webhook-retry}

When calling a webhook, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency to external requests.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).


## Testing a webhook destination configuration
{: #en-webhook-test-destination}

You can test a webhook destination in the options menu that is provided against the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).
