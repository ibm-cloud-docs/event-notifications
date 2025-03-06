---

copyright:
   years: 2025
lastupdated: "2025-03-04"

keywords: event-notifications, event notifications, about event notifications, cloud logs, pagerduty

subcollection: event-notifications

content-type: tutorial
account-plan: standard
completion-time: 30m

---

{{site.data.keyword.attribute-definition-list}}


# Integrating {{site.data.keyword.logs_full_notm}} alerts with {{site.data.keyword.en_short}} and raising PagerDuty alerts
{: #tutorial-en-icl-pd-integration}
{: toc-content-type="tutorial"}
{: toc-completion-time="30m"}


This tutorial shows you how to integrate {{site.data.keyword.logs_full_notm}} alerts with {{site.data.keyword.en_short}} and send PagerDuty Alerts.

{{site.data.keyword.logs_full_notm}} is used to visualize and alert on events that are generated in your account. When an event of interest takes place in your {{site.data.keyword.logs_full_notm}} instance, it communicates with a connected {{site.data.keyword.en_short}} instance to raise an alert to the [PagerDuty destination](/docs/event-notifications?topic=event-notifications-en-destinations-pagerduty).

This tutorial shows you how to configure the following flow:

1. Creating a {{site.data.keyword.logs_full_notm}} and an {{site.data.keyword.en_short}} instance.

1. Connecting an instance of {{site.data.keyword.logs_full_notm}} with an {{site.data.keyword.en_short}} instance.

1. Configuring {{site.data.keyword.logs_full_notm}} to send out notifications to PagerDuty as a destination.

1. Configuring an alert in {{site.data.keyword.logs_full_notm}}.

1. Raising a PagerDuty alert when an alert is open in {{site.data.keyword.logs_full_notm}} and automatically resolving it in PagerDuty when the alert is closed {{site.data.keyword.logs_full_notm}}.

## Before you begin 
{: #en-integration-prereqs}

You need an {{site.data.keyword.cloud}} account. If you don't have an account, then [Create an {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration/).

## Create an {{site.data.keyword.en_short}} service instance
{: #en-create-en-instance}
{: step}

1. Login to your [{{site.data.keyword.cloud}}](https://cloud.ibm.com){: external} account.

1. In the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog#services), search **Event notifications > Event notifications**.

1. Select a **Location** from the list of supported locations and select a pricing plan. To know more about the pricing plans, refer [here](/docs/event-notifications?topic=event-notifications-getting-started#en-decide-pricing-plans).

1. Enter a service name.

1. Select a resource group.

1. Accept the license agreement terms and click **Create**.

## Create an {{site.data.keyword.logs_full_notm}} service instance
{: #en-create-icl-instance}
{: step}

1. In the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog#services), search **Cloud Logs > Cloud Logs**.

1. Select a **Location** from the list of supported locations and select a pricing plan.

1. Enter a service name.

1. Select a resource group.

1. Accept the license agreement terms and click **Create**.

## Authorize the connection between the {{site.data.keyword.logs_full_notm}} service instance and the {{site.data.keyword.en_short}} service instance
{: #en-authorize-connection}
{: step}

1. Select **Manage > Access(IAM)** from the upper right on your Dashboard. 

1. Under Authorizations, click **Create**.

1. Select the source account, Cloud Logs as the source service and the specific instance of Cloud Logs that needs access. 

1. Next, select Event notifications as the target service, the service instance of {{site.data.keyword.en_short}} that needs source access and assign the viewer, reader, and event source manager roles to the source that it can use to interact with the target. 

1. Click **Review**. Review all the assignments.

1. Select **Authorize**.

## Enabling access in the instances and testing the connection
{: #en-enabling-access}
{: step}

1. Navigate to the cloud logs instance that was selected as the source in the connection that was previously established by clicking ![Hamburger icon](images/icon_hamburger.svg) > Resource List > Logging and Monitoring > **Your Cloud Logs instance**. 

1. In your {{site.data.keyword.logs_full_notm}} instance, select **Dashboard**. Now, in your dashboard, click ![Hamburger icon](images/icon_hamburger.svg) and select **Integrations > Outbound Integrations**. 

1. Select **Add** under {{site.data.keyword.en_short}}.

1. Click **Add New**. Since the authorization policy has been created, select next. 

1. Name your integration, select the {{site.data.keyword.en_short}} instance that was used for authorizing and set your endpoint type to **Public**. Click **Save**.

1. Before moving to the **Test** step, we need to verify whether a connection has been established between the {{site.data.keyword.en_short}} instance and the {{site.data.keyword.logs_full_notm}} instance.

1. Navigate to your **{{site.data.keyword.en_short}} instance** by clicking ![Hamburger icon](images/icon_hamburger.svg) > Resource List > Developer Tools > **Your Event notifications instance**. 

1. Under **Sources** in your {{site.data.keyword.en_short}} instance, you should see your {{site.data.keyword.logs_full_notm}} instance as a source of the form **IBM Cloud Logs - GUID of your Cloud Logs Instance**. 

1. Go to **topics** and click **Create**. Name your topic, and select your Cloud Logs instance as the Source. To learn more about creating a topic and providing filters that can be used in your instance, see [Creating an Event notifications topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic). Click **Create**. 

1. Navigate to **Destinations** and click Create. Name your destination and select destination type as **PagerDuty**. Provide the API key and Routing key, then click Add. See here for process to generate the [API Key](https://support.pagerduty.com/main/docs/api-access-keys) and [Routing key](https://support.pagerduty.com/main/docs/services-and-integrations#generate-a-new-integration-key).

1. Create a template for your PagerDuty alert by navigating to Templates > Create. Name your template, select the template type as PagerDuty notification, and provide your template. 

    **Example Template:**

    ```json
    {
    "payload": {
        "summary": "{{ data.alert_definition.name}}",
        "timestamp": "{{time}}",
        {{#equal data.alert_definition.severity "Critical"}}
        "severity": "critical",
        {{/equal}}
        {{#equal data.alert_definition.severity "High"}}
        "severity": "error",
        {{/equal}}
        {{#equal data.alert_definition.severity "Info"}}
        "severity": "info",
        {{/equal}}
        {{#equal data.alert_definition.severity "Warning"}}
        "severity": "warning",
        {{/equal}}
        "source": "{{ source }}"
    },
    "dedup_key": "{{ data.alert_definition.id }}",
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

    To learn more about the fields that can be used to construct the template block, see [here](https://developer.pagerduty.com/api-reference/368ae3d938c9e-send-an-event-to-pager-duty).

1. To create a Subscription, navigate to **Subscriptions > Create**. Name your subscription, select the topic, the PagerDuty destination, and the template that were previously created. Click **Create**. 

## Creating an {{site.data.keyword.logs_full_notm}} alert 
{: #en-icl-alert}

1. Navigate to your {{site.data.keyword.logs_full_notm}} instance and click **Dashboard**. 

1. Click ![Hamburger icon](images/icon_hamburger.svg) > **Alerts** > **Alert Management**.

1. Create a New Alert. 

1. Provide the Alert Name and Severity. Select the wanted alert type and provide the query to filter the logs, along with the severity and conditions for the alert to be raised. 

1. Set the time period and schedule for the alert notifications and specify the notification content. 

1. Verify the alert and click create. 

## Verifying that the connection was successfully established
{: #en-verification}

1. Navigate to your {{site.data.keyword.logs_full_notm}} **Dashboard** and click Test. If the connection was successfully established, you receive a PagerDuty alert. 

1. You can set the time period and frequency of the Alert notifications in the next step and select alerts to attach to the webhook. 

1. Select **Done**.


The process of integration is completed. You should start receiving PagerDuty alerts according to the criteria that were set when unusual activity is observed. 
