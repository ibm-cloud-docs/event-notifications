---

copyright:
  years: 2025
lastupdated: "2025-05-02"

keywords: event-notifications, event notifications, about event notifications, templates, slack

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Event Streams Notification Template
{: #en-event-streams-notification-template}

{{site.data.keyword.messagehub}} is a message bus that is built by using Apache Kafka.In Event Streams, applications can send data by creating messages and sending to a topic. To receive messages, the application subscribes to a topic and can choose to receive all the messages of the topic or share the messages between them. 
{: shortdesc}

For more information on the Event Streams destination, see [here](/docs/event-notifications?topic=event-notifications-en-destinations-event-streams).

## Constructing an {{site.data.keyword.messagehub}} notification template
{: #en-construct-event-streams-template}

Construct the template block. Make sure the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.

Handlebars is a templating language that allows for dynamic content generation within templates.Handlebars can be used to customize notification messages using template variables and conditional logic.

If the UI is used to create the template , Handlebars is used to create the payload for the body of the template. If API/CLI is used to create the template the payload must be encoded to the Base64 format. Refer the sample template for [UI](#ui-event-streams-template) or [AI/CLI](#api-cli-event-streams-template).

### UI Event Streams notification template example
{: #ui-event-streams-template}

```handlebars
{
  {{#equal data.alert_definition.severity "Critical"}}
		"severity": 1,
	{{/equal}}
  {{#equal data.alert_definition.severity "Info"}}
		"severity": 2,
	{{/equal}}
  {{#equal data.alert_definition.severity "Error"}}
		"severity": 2,
	{{/equal}}
  "console": "toc",
  "version": "1.0",
  "crn": {
    "version": "v1",
    "ctype": "public",
    "cname": "bluemix",
    "resource_type": "object",
    "resource": "event-notifications",
    "service_name": "event-notifications"
    },
  "alert_id": "{{data.alert_definition.id}}",
  "tribe_name": "Mobile",
  "disable_pager": "false",
  "source": "{{source}}",
  "tip_msg_type": "create.notice",
  "situation": "{{ibmendefaultshort}}",
  "customer_impacting": "false",
  "runbook_toc_enabled": "false",
  "short_description": "{{ibmendefaultshort}}",
  "product_ready_compliance": "true",
  "long_description": "{{data.alert_definition.description}}",
  "timestamp": "{{time}}",
  "alert_ui_url": "{{data.links.view_alert}}",
  "runbook_url": "{{data.alert_definition.meta_labels.runbook}}"
}
```


### API or CLI Event Streams notification template example
{: #api-cli-event-streams-template}

```json
    {
	"name": "Template for ",
	"params": {
		"body": "ewogIHt7I2VxdWFsIGRhdGEuYWxlcnRfZGVmaW5pdGlvbi5zZXZlcml0eSAiQ3JpdGljYWwifX0KCQkic2V2ZXJpdHkiOiAxLAoJe3svZXF1YWx9fQogIHt7I2VxdWFsIGRhdGEuYWxlcnRfZGVmaW5pdGlvbi5zZXZlcml0eSAiSW5mbyJ9fQoJCSJzZXZlcml0eSI6IDIsCgl7ey9lcXVhbH19CiAge3sjZXF1YWwgZGF0YS5hbGVydF9kZWZpbml0aW9uLnNldmVyaXR5ICJFcnJvciJ9fQoJCSJzZXZlcml0eSI6IDIsCgl7ey9lcXVhbH19CiAgImNvbnNvbGUiOiAidG9jIiwKICAidmVyc2lvbiI6ICIxLjAiLAogICJjcm4iOiB7CiAgICAgICJ2ZXJzaW9uIjogInYxIiwKICAgICJjdHlwZSI6ICJwdWJsaWMiLAogICAgImNuYW1lIjogImJsdWVtaXgiLAogICAgInJlc291cmNlX3R5cGUiOiAib2JqZWN0IiwKICAgICJyZXNvdXJjZSI6ICJldmVudC1ub3RpZmljYXRpb25zIiwKICAgICJzZXJ2aWNlX25hbWUiOiAiZXZlbnQtbm90aWZpY2F0aW9ucyIKICAgIH0sCiAgImFsZXJ0X2lkIjogInt7ZGF0YS5hbGVydF9kZWZpbml0aW9uLmlkfX0iLAogICJ0cmliZV9uYW1lIjogIk1vYmlsZSIsCiAgImRpc2FibGVfcGFnZXIiOiAiZmFsc2UiLAogICJzb3VyY2UiOiAie3tzb3VyY2V9fSIsCiAgInRpcF9tc2dfdHlwZSI6ICJjcmVhdGUubm90aWNlIiwKICAic2l0dWF0aW9uIjogInt7aWJtZW5kZWZhdWx0c2hvcnR9fSIsCiAgImN1c3RvbWVyX2ltcGFjdGluZyI6ICJmYWxzZSIsCiAgInJ1bmJvb2tfdG9jX2VuYWJsZWQiOiAiZmFsc2UiLAogICJzaG9ydF9kZXNjcmlwdGlvbiI6ICJ7e2libWVuZGVmYXVsdHNob3J0fX0iLAogICJwcm9kdWN0X3JlYWR5X2NvbXBsaWFuY2UiOiAidHJ1ZSIsCiAgImxvbmdfZGVzY3JpcHRpb24iOiAie3tkYXRhLmFsZXJ0X2RlZmluaXRpb24uZGVzY3JpcHRpb259fSIsCiAgInRpbWVzdGFtcCI6ICJ7e3RpbWV9fSIsCiAgImFsZXJ0X3VpX3VybCI6ICJ7e2RhdGEubGlua3Mudmlld19hbGVydH19IiwKICAicnVuYm9va191cmwiOiAie3tkYXRhLmFsZXJ0X2RlZmluaXRpb24ubWV0YV9sYWJlbHMucnVuYm9va319Igp9"
	},
	"type": "eventstreams.notification"
    }
```
