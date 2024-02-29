---

copyright:
  years: 2023
lastupdated: "2023-10-10"

keywords: event-notifications, event notifications, about event notifications, destinations, code engine

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Code Engine
{: #en-destinations-codeengine}

{{site.data.keyword.codeenginefull}} is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeengineshort}} represents a service destination, where an incoming notification can be consumed programmatically. For example, an incoming notification about an event can trigger a {{site.data.keyword.codeengineshort}} destination to a backend microservice to act based on the content of the incoming notification.
{: shortdesc}

## Configuring a {{site.data.keyword.codeengineshort}} destination
{: #en-codeengine-configure}

Before you configure {{site.data.keyword.codeengineshort}} as a destination for `run type` Job, make sure that you have a {{site.data.keyword.codeengineshort}} project [created and job configured](https://cloud.ibm.com/codeengine/projects) in the same account as your {{site.data.keyword.en_short}} instance.
{: note}

In case of `run type` Job, if you are using {{site.data.keyword.en_short}} CLI or API to configure {{site.data.keyword.codeengineshort}} job as a destination, ensure that you have enabled authorization to grant access between services. For more information, see [Using authorizations to grant access between services](#en-using-s2s-auth1).
{: important}

To configure a {{site.data.keyword.codeengineshort}} destination, do the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add new destination.

1. In the **Add a destination** side panel, provide the following details.

  - **Name** - Enter a name for your destination.
  - **Description** - Optionally, enter a description for your destination.
  - **Type** - Under **Destination**, for the **Type**, select **{{site.data.keyword.codeengineshort}}** from the list as your destination type.
  - **Run Type** - Select one of the run type **{{site.data.keyword.codeengineshort}}** job or **{{site.data.keyword.codeengineshort}}** application.
  
  If selected run type is job then provide the following details:
  - **Project name** - Select the {{site.data.keyword.codeengineshort}} project name from the list, if you already have a {{site.data.keyword.codeengineshort}} project. Otherwise, click the **Create new project** link, to create an {{site.data.keyword.codeengineshort}} project.

      When you select a {{site.data.keyword.codeengineshort}} project, the authorization between the services will be created internally between the two service instances, if the authorization between the services doesn't exist.
      {: note}
  - **Job name** - Select the job name from the list.

  If selected run type is application then provide the following details:
  - **URL** - Enter **{{site.data.keyword.codeengineshort}}** application secured URL (only HTTPS).
  - **Verb** - Select the Verb to be called (GET or POST).
  - **Headers** - Optionally, enter a list of headers to be passed to **{{site.data.keyword.codeengineshort}}** application.

4. Click **Add**.

## Using authorizations to grant access between services
{: #en-using-s2s-auth1}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to create or remove an authorization that grants one service access to another service.


### Creating an authorization in the console
{: #en-using-s2s-console}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**, and select **Authorizations**.

1. Click **Create**.

1. Select a source account.
   * If the source service that needs access to the target service is in this account, select **This account**.

1. Select a **Source service** as **Event Notifications**.

1. Specify whether you want the authorization to be for all resources or Resources based on selected attributes. If you have chosen Resources based on selected attributes, then specify the **Add attributes**: only source resource group or only source service instance.

1. Select a **Target service** as **{{site.data.keyword.codeengineshort}}**.

1. For the target service, specify whether you want the authorization to be for all projects, only to a specific project in the account, or projects only in a certain resource group.

1. Select both the roles (Viewer and Writer) to assign access to the source service that accesses the target service.

   If you have selected only one of these two roles (Reader or Writer) during the service to service authorization, you may endup with not able to tirgger a job or configure destination. You will get an error for service to service authorization failure in these cases. Make sure to recreate an authorization between the services with both the roles selected.
{: important}

1. Click **Authorize**.

### Creating an authorization by using the CLI
{: #en-create-auth-cli1}

To authorize a source service to access a target service, run the `ibmcloud iam authorization-policy-create` command.

For more information about all of the parameters that are available for this command, see [ibmcloud iam authorization-policy-create](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_authorization_policy_create).

### Accessing event payload in {{site.data.keyword.codeengineshort}} job
{: #en-codeengine-access-event-payload}

The event payload has been transmitted to {{site.data.keyword.codeengineshort}} job using an environment variable, which can be retrieved by utilizing the `ibmendata` environment variable.

## Testing a {{site.data.keyword.codeengineshort}} destination configuration
{: #en-codeengine-test-destination}

You can test a {{site.data.keyword.codeengineshort}} destination in the options menu provided againts the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

For more information on testing a destination, see [here](/docs/event-notifications?topic=event-notifications-en-test-destination).

## {{site.data.keyword.codeengineshort}} retry policy
{: #en-codengine-retry}

When calling {{site.data.keyword.codeengineshort}}, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services ({{site.data.keyword.codeengineshort}}).

In addition, the following timeout conditions cause the {{site.data.keyword.codeengineshort}} call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the URL fails even after retry attempts, the notification is lost.
{: note}
