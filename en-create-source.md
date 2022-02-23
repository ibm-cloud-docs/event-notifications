---

copyright:
  years: 2015, 2022
lastupdated: "2022-02-07"

keywords: event notifications, event-notifications, source, tutorials

subcollection: event-notifications

content-type: tutorial
account-plan: lite
completion-time: 15m

---

{{site.data.keyword.attribute-definition-list}}

# Add an {{site.data.keyword.en_short}} source
{: #en-add-source}
{: toc-content-type="tutorial"}
{: toc-completion-time="15m"}

Add an {{site.data.keyword.en_short}} source. Various services produce events that can be consumed by {{site.data.keyword.en_short}}. You can add these services as 'sources' within your {{site.data.keyword.en_short}} instance. When a source is added, you can filter the events from it by using topics, and then subscribe destinations to the topics.
{: shortdesc}

## Types of sources
{: #en-add-source-types}

Two types of sources are supported for {{site.data.keyword.en_short}}: IBM-managed sources and generic API sources. 

With IBM-managed sources, events emit from managed services on {{site.data.keyword.Bluemix_notm}}. For example, {{site.data.keyword.Bluemix_notm}} Monitoring, {{site.data.keyword.Bluemix_notm}} Security and Compliance Center, and {{site.data.keyword.Bluemix_notm}} Secrets Manager can all be added to {{site.data.keyword.en_short}} IBM-managed sources. 

To see the current list of {{site.data.keyword.Bluemix_notm}} services available as {{site.data.keyword.en_short}} sources, go to the `Sources` section of your {{site.data.keyword.en_short}} dashboard, click `Add`, and select `IBM Managed Services`.

With generic API sources, events emanate from services or applications that are not managed by IBM. For example, if you create your own application that sends events to {{site.data.keyword.en_short}}, your application can be added as an API source. 

API sources cannot route notifications to the {{site.data.keyword.Bluemix_notm}} email service and {{site.data.keyword.Bluemix_notm}} SMS service because these services deliver content that is generated exclusively from {{site.data.keyword.Bluemix_notm}} managed services.
{: note}

The connection protocols differ between source types, so the procedure for adding is different as described in the following sections.

## Add an IBM-managed source
{: #en-add-source-IBM-managed}
{: step}

Verify that the managed service is available as a source for {{site.data.keyword.en_short}}

- Go to the `Sources` section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select `IBM Managed Service`.
- Confirm that the managed service of interest is shown.

## Create a service authorization
{: #en-create-service-auth}
{: step}

Create a service-to-service authorization between your managed service and {{site.data.keyword.en_short}}

- From the {{site.data.keyword.Bluemix_notm}} console, select `Manage` >> `Access(IAM)` >> `Authorizations`.
- The Authorizations view contains dropdowns for `Source service` and `Target service`. Select your managed service as the source, and {{site.data.keyword.en_short}} as the target.
- Set the service access level to `Event Source Manager`.

## Find your instance of the managed service
{: #en-find-mg-serv-inst}
{: step}

- Find your existing service instances in your [account resource list](https://cloud.ibm.com/resources).
- Select the instance of interest and open its dashboard.

If you don't have an existing instance, create one from the [{{site.data.keyword.Bluemix_notm}} catalog](https://cloud.ibm.com/catalog).
{: tip}

## Configure your managed service instance to connect to {{site.data.keyword.en_short}}
{: #en-config-mgt-serv-inst}
{: step}

Follow the documentation for the selected service to configure the connection to {{site.data.keyword.en_short}}.

## Add a generic API source
{: #en-add-source-generic-API}
{: step}

API Sources can not be used to send notifications to out of the box destinations like email and SMS. {: note }

- Go to the `Sources` section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select `API Source`.
- Type a name and an optional description and click `Add`.
- Because you are connecting from your own application or service, follow the instructions in the [{{site.data.keyword.en_short}} API documentation](https://cloud.ibm.com/apidocs/event-notifications/event-notifications?code=node) or in the SDK documentation for your programming language to configure the connection.
