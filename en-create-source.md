---

copyright:
  years: 2015, 2020, 2022
lastupdated: "2022-02-01"

keywords: event notifications, event-notifications, source, tutorials

subcollection: event-notifications

content-type: tutorial
services:
account-plan: lite
completion-time: 15m

---

{{site.data.keyword.attribute-definition-list}}

# Add an {{site.data.keyword.en_short}} source
{: #en-add-source}

Various services produce events that can be consumed by {{site.data.keyword.en_short}}.  You can add these services as 'sources' within your {{site.data.keyword.en_short}} instance.  After a source is added, you can filter the events from it by using topics, and then subscribe destinations to the topics.  This tutorial describes how to add a source.
{: shortdesc}

## Types of sources
{: #en-add-source-types}

There are two types of sources for {{site.data.keyword.en_short}}:  IBM-managed sources and generic API sources.  

With IBM-managed sources, events emit from managed services on {{site.data.keyword.Bluemix_notm}}.  For example, {{site.data.keyword.Bluemix_notm}} Monitoring, {{site.data.keyword.Bluemix_notm}} Security and Compliance Center, and {{site.data.keyword.Bluemix_notm}} Secrets Manager can all be added to {{site.data.keyword.en_short}} IBM-managed sources.  To see the current list {{site.data.keyword.Bluemix_notm}} services available as {{site.data.keyword.en_short}} sources, visit the Sources section of your {{site.data.keyword.en_short}} dashboard, click the 'Add' button, an select 'IBM Managed Services'.

With generic API sources, events emanate from services or applications not managed by IBM. For example, if you create your own application that sends events to {{site.data.keyword.en_short}}, your application can be added as an API source.  

API sources cannot route notifications to the {{site.data.keyword.Bluemix_notm}} Email service and {{site.data.keyword.Bluemix_notm}} SMS service because these services are meant to deliver content generated exclusively from {{site.data.keyword.Bluemix_notm}} managed services.
{: note}

The connection protocols differ between source types, so the procedure for adding is different as described below.

## Add an IBM-managed source
{: #en-add-source-IBM-managed}

Verify the managed service is available as a source for {{site.data.keyword.en_short}}
{: step}

- Visit the Sources section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select IBM Managed Service.
- Confirm the managed service of interest is shown.

Create a service-to-service authorization between your managed service and {{site.data.keyword.en_short}}
{: step}

- From the top bar of the {{site.data.keyword.Bluemix_notm}} console, select Manage >> Access(IAM) >> Authorizations
- In the Authorizations view you will see dropdowns for Source service and Target service.  Select your managed service as the source, and {{site.data.keyword.en_short}} as the target.
- Set the service access level to Event Source Manager.

Find your instance of the managed service
{: step}

- Find your existing service instances in your [account resource list](https://cloud.ibm.com/resources).
- Select the instance of interest and open its dashboard.

If you don't have an existing instance, create one from the [{{site.data.keyword.Bluemix_notm}} catalog](https://cloud.ibm.com/catalog).
{: tip}

Configure your managed service instance to connect to {{site.data.keyword.en_short}}
{: step}

- Follow the documentation for the selected service to configure the connection to {{site.data.keyword.en_short}}.

## Add a generic API source
{: #en-add-source-generic-API}

- Visit the Sources section of the {{site.data.keyword.en_short}} dashboard.
- Click `Add` and select API Source.
- Type a name and description (optional) and click `Add`.
- Since you will be connecting from your own application or service, follow the instructions in the [{{site.data.keyword.en_short}} API documenation](https://cloud.ibm.com/apidocs/event-notifications/event-notifications?code=node) or in the SDK documentation for your programming language to configure the connection.
