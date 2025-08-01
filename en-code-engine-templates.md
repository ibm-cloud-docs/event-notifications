---

copyright:
  years: 2025
lastupdated: "2025-08-01"

keywords: event-notifications, event notifications, about event notifications, templates, code engine

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Code Engine Notification Template
{: #en-code-engine-notification-template}

{{site.data.keyword.codeenginefull_notm}} is a serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeengineshort}} represents a service destination, where an incoming notification can be consumed programmatically. For example, an incoming notification about an event can trigger a {{site.data.keyword.codeengineshort}} destination to a backend microservice to act based on the content of the incoming notification.
{: shortdesc}

For more information on the Code Engine destination, see [Code Engine](/docs/event-notifications?topic=event-notifications-en-destinations-codeengine&interface=ui).

## Constructing a {{site.data.keyword.codeengine_short}} notification template
{: #en-construct-code-engine-template}

Construct the template block. Make sure the template is a well-formed JSON that adheres to the Handlebars template syntax and semantics.

Handlebars is a templating language that allows for dynamic content generation within templates.Handlebars can be used to customize notification messages using template variables and conditional logic.


### {{site.data.keyword.codeengine_short}} notification template examples
{: #en-code-engine-template-example}


#### Template examples for {{site.data.keyword.codeengine_short}} Jobs
{: #en-code-engine-job-templates}

```json
{
 "run_env_variables": [
   { "name": "region", "value": "{{data.region}}","type": "literal"},
]
}
```
See [Create a Job Run](https://cloud.ibm.com/apidocs/codeengine/v2#create-job-run) to find more parameters that you can integrate into the template.

#### Template examples for {{site.data.keyword.codeengine_short}} Functions/Applications:
{: #en-code-engine-template-functions-applications-templates}

For function and application templates, you can define them as per your requirement.



