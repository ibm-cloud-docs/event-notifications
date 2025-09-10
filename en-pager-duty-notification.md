---

copyright:
  years: 2025
lastupdated: "2025-09-10"

keywords: event-notifications, event notifications, about event notifications, templates, pagerduty

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# PagerDuty Notification Template
{: #en-pagerduty-notification-template}

PagerDuty helps organizations with the insight to proactively manage events that impact customers across their IT environment. When you select PagerDuty as the service destination, any subscribed notification about an event can be sent as an alert to PagerDuty channels.
{: shortdesc}

For more information about the PagerDuty destination, see [PagerDuty](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty).

## How to create a PagerDuty Notification Template
{: #en-create-pager-duty-template}

Construct the template block. Make sure that the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.
To learn more about the fields that can be used to construct the template block, see [Send an event to PagerDuty](https://developer.pagerduty.com/api-reference/368ae3d938c9e-send-an-event-to-pager-duty)

If the UI is used to create the template, Handlebars is used to create the payload for the body of the template. If API/CLI is used to create the template, then the payload must be encoded to the Base64 format. Refer the sample template for [UI](#ui-pd-template) or [AI/CLI](#api-cli-pd-template).



### UI PagerDuty notification template example
{: #ui-pd-template}

```handlebars
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

}
```

To learn more about Handlebars integration and the various helpers offered, see [Handlebars Integration](/docs/event-notifications?topic=event-notifications-en-create-en-template&interface=ui#handlebars-integration).
{: note}

### API or CLI PagerDuty notification template example
{: #api-cli-pd-template}

```json
    {
	"name": "Template for TIP",
	"params": {
		"body": "YGBganNvbgp7CiAgInBheWxvYWQiOiB7CiAgICAic3VtbWFyeSI6ICJ7eyBkYXRhLmFsZXJ0X2RlZmluaXRpb24ubmFtZX19IiwKICAgICJ0aW1lc3RhbXAiOiAie3t0aW1lfX0iLAogICAgInNldmVyaXR5IjogImluZm8iLAogICAgInNvdXJjZSI6ICJ7eyBzb3VyY2UgfX0iCiAgfSwKICAiZGVkdXBfa2V5IjogInt7IGlkIH19IiwKICB7eyNlcXVhbCBkYXRhLnN0YXR1cyAidHJpZ2dlcmVkIn19CiAgImV2ZW50X2FjdGlvbiI6ICJ0cmlnZ2VyIgogICB7ey9lcXVhbH19CgogIHt7I2VxdWFsIGRhdGEuc3RhdHVzICJyZXNvbHZlZCJ9fQogICJldmVudF9hY3Rpb24iOiAicmVzb2x2ZSIKICB7ey9lcXVhbH19CgogICB7eyNlcXVhbCBkYXRhLnN0YXR1cyAiYWNrbm93bGVkZ2VkIn19CiAgICJldmVudF9hY3Rpb24iOiAiYWNrbm93bGVkZ2UiCiAgIHt7L2VxdWFsfX0KfQpgYGA="
	},
	"type": "pagerduty.notification"
    }
 ```
