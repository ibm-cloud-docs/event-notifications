---

copyright:
  years: 2025
lastupdated: "2025-03-25"

keywords: event-notifications, event notifications, about event notifications, templates, pagerduty

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# PagerDuty Notification Template
{: #en-pagerduty-notification-template}

PagerDuty helps organizations with the insight to proactively manage events that may impact customers across their IT environment. When you select PagerDuty as service destination, any subscribed notification about an event can be sent as an **alert** to PagerDuty channels.
{: shortdesc}

For more information about the PagerDuty destination, see [here](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty).

## How to create a PagerDuty Notification Template
{: #en-create-pager-duty-template}

Construct the template block. Make sure the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.
To learn more about the fields that can be used to construct the template block, see [here](https://developer.pagerduty.com/api-reference/368ae3d938c9e-send-an-event-to-pager-duty)

### PagerDuty notification template example
{: #pd-template}

```json
{
  "payload": {
    "summary": "{{ data.alert_definition.name}}",
    "timestamp": "{{time}}",
    "severity": "info",
    "source": "{{ source }}"
  },
  "dedup_key": "{{ id }}",
  {{#equal data.status "triggered"}}
  "event_action": "trigger"
   {{/equal}}

  {{#equal data.status "resolved"}}
  "event_action": "resolve"
  {{/equal}}

   {{#equal data.status "acknowledged"}}
   "event_action": "acknowledge"
   {{/equal}}
}
```
