---

copyright:
   years: 2026
lastupdated: "2026-06-30"

keywords: event-notifications, event notifications, pagerduty, on call manager, ocm, migration, icl, cloud logs

subcollection: event-notifications

content-type: tutorial
account-plan: standard
completion-time: 30m

---

{{site.data.keyword.attribute-definition-list}}


# Migrating from PagerDuty to On Call Manager with {{site.data.keyword.en_short}}
{: #tutorial-en-pd-ocm-migration}
{: toc-content-type="tutorial"}
{: toc-completion-time="30m"}


This tutorial shows you how to migrate your PagerDuty alerting setup to IBM On Call Manager (OCM) using {{site.data.keyword.en_full_notm}}.
{: shortdesc}

IBM On Call Manager can receive events from various monitoring sources, either on-premises or in the cloud. By integrating OCM with {{site.data.keyword.en_short}}, you can route notifications from IBM Cloud services to your OCM instance for centralized incident management.

The migration process differs based on your source type:

- If your source is {{site.data.keyword.logs_full_notm}} (ICL), you'll create an ICL Integration on OCM to receive alerts directly from Cloud Logs.
- For other IBM Cloud sources (such as Secrets Manager or IBM Cloud Monitoring), you'll create an Outbound Integration on OCM and configure {{site.data.keyword.en_short}} to route notifications through a webhook destination.

## Before you begin 
{: #en-pd-ocm-migration-prereqs}

- You need an IBM On Call Manager account. If you don't have an account, then [Create an On Call Manager account](https://oncallmanager.ibm.com/cemui/onboard-users).
- You need an {{site.data.keyword.cloud}} account. If you don't have an account, then [Create an {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com).
- Verify that you have an existing {{site.data.keyword.en_short}} service instance or create a new one.

## Migrating {{site.data.keyword.logs_full_notm}} source to OCM
{: #en-pd-ocm-migration-icl}

Follow these steps when your source is {{site.data.keyword.logs_full_notm}} (ICL).

### Create an ICL Integration on On Call Manager
{: #en-create-icl-integration}
{: step}

1. Log in to your [On Call Manager](https://oncallmanager.ibm.com){: external} account.

1. Click **Administration** > **Integrations**.

1. Click **New Integration**.

1. Locate the **IBM Cloud Logs** tile and click **Configure**.

1. Enter a name for the integration (for example, "Cloud Logs Production Alerts").

1. Click **Copy** ![Copy](/images/copy.svg) to copy the generated webhook URL to the clipboard. Save this URL for use in the next step.

1. Click **Save** to complete the integration setup.

### Create a webhook destination in {{site.data.keyword.en_short}}
{: #en-create-webhook-destination-icl}
{: step}

1. Navigate to your {{site.data.keyword.en_short}} instance by clicking ![Hamburger icon](images/icon_hamburger.svg) > **Resource List** > **Developer Tools** > **Your Event Notifications instance**.

1. Go to the **Destinations** section of the {{site.data.keyword.en_short}} dashboard.

1. Click **Add**.

1. Enter a name for the destination (for example, "OCM Webhook - Cloud Logs").

1. Provide an optional description.

1. Select the destination type as **Webhook**.

1. Paste the webhook URL that you copied from On Call Manager in the previous step.

1. Select the HTTP verb as **POST**.

1. (Optional) Add any required authorization headers if your OCM instance requires authentication.

1. Click **Add**.

### Create a subscription
{: #en-create-subscription-icl}
{: step}

1. In the **Topics** section of the {{site.data.keyword.en_short}} dashboard, select the topic that is configured for your {{site.data.keyword.logs_full_notm}} source.

1. In the topic details page, click **Subscriptions** and then click **Create**.

1. Enter a name for the subscription (for example, "Cloud Logs to OCM").

1. Provide an optional description.

1. Select the OCM webhook destination you created earlier.

1. Click **Create**.

Your {{site.data.keyword.logs_full_notm}} alerts are now configured to route to On Call Manager through {{site.data.keyword.en_short}}.

## Migrating other IBM Cloud sources to OCM
{: #en-pd-ocm-migration-other}

Follow these steps for sources other than {{site.data.keyword.logs_full_notm}}, such as Secrets Manager, IBM Cloud Monitoring, or API sources.

### Create an Outbound Integration on On Call Manager
{: #en-create-outbound-integration}
{: step}

1. Log in to your [On Call Manager](https://oncallmanager.ibm.com){: external} account.

1. Click **Administration** > **Integrations**.

1. Click **New Integration**.

1. Locate the **Webhook** tile and click **Configure**.

1. Enter a name for the integration (for example, "IBM Cloud Services Webhook").

1. Click **Copy** ![Copy](/images/copy.svg) to copy the generated webhook URL to the clipboard. Save this URL for use in the next step.

1. Click **Save** to complete the integration setup.

### Create a webhook destination in {{site.data.keyword.en_short}}
{: #en-create-webhook-destination-other}
{: step}

1. Navigate to your {{site.data.keyword.en_short}} instance by clicking ![Hamburger icon](images/icon_hamburger.svg) > **Resource List** > **Developer Tools** > **Your Event Notifications instance**.

1. Go to the **Destinations** section of the {{site.data.keyword.en_short}} dashboard.

1. Click **Add**.

1. Enter a name for the destination (for example, "OCM Webhook - General").

1. Provide an optional description.

1. Select the destination type as **Webhook**.

1. Paste the webhook URL that you copied from On Call Manager in the previous step.

1. Select the HTTP verb as **POST**.

1. (Optional) Add any required authorization headers if your OCM instance requires authentication.

1. Click **Add**.

### Create or use a template for your source
{: #en-create-template-other}
{: step}

Templates are required for non-ICL sources to format the notification payload correctly for On Call Manager. You can either copy your existing webhook template and modify it for OCM, or create a new one.

To create a new webhook template:

1. Go to the **Templates** section of the {{site.data.keyword.en_short}} dashboard.

1. Click **Create**.

1. Enter a name for the template (for example, "OCM Webhook Template - Secrets Manager").

1. Provide an optional description.

1. Select the template type as **Webhook Notification**.

1. Enter the template body based on your source type. You can reference your existing PagerDuty template or use the following examples for common sources:

   **Secrets Manager source:**

   ```handlebars
   {
       "severity": "{{#if (equal severity "low")}}Minor{{else if(equal severity "high")}}Critical{{else if (equal severity "medium")}}Warning{{else}}Information{{/if}}",
       "source": "{{source}}",
       "summary": "{{ibmendefaultlong}}",
       "eventtype": "{{data.event_type}}",
       "resolution": false
   }
   ```

   **IBM Cloud Monitoring source:**

   ```handlebars
   {
       "severity": "{{#if (equal severity "LOW")}}Minor{{else if(equal severity "HIGH")}}Critical{{else if (equal severity "MEDIUM")}}Warning{{else}}Information{{/if}}",
       "source": "{{source}}",
       "summary": "{{data.alert.body}}",
       "resolution": {{#if (contains subject "Triggered")}}false{{else}}true{{/if}},
       "eventtype": "{{#if (contains subject "Triggered")}}Trigger{{else}}Resolved{{/if}}"
   }
   ```

   For more information about template syntax and available variables, see [Webhook notification templates](/docs/event-notifications?topic=event-notifications-en-webhook-notifications-template).

1. Click **Add**.

### Create a subscription with the template
{: #en-create-subscription-other}
{: step}

1. In the **Topics** section of the {{site.data.keyword.en_short}} dashboard, select the topic that is configured for your source (for example, Secrets Manager or IBM Cloud Monitoring).

1. In the topic details page, click **Subscriptions** and then click **Create**.

1. Enter a name for the subscription (for example, "Secrets Manager to OCM").

1. Provide an optional description.

1. Select the OCM webhook destination you created earlier.

1. Select the webhook template you created or modified for OCM.

1. Click **Create**.

Your IBM Cloud service alerts are now configured to route to On Call Manager through {{site.data.keyword.en_short}}.

## Verify the integration
{: #en-verify-integration}
{: step}

To verify that your migration was successful:

1. Go to the **Destinations** section of the {{site.data.keyword.en_short}} dashboard.

1. Locate your OCM webhook destination.

1. Click the overflow menu ![Overflow menu](/images/overflow-menu.svg) for the destination.

1. Click **Test destination**.

1. You should receive a test notification in your On Call Manager instance.

1. Verify that the notification appears correctly in OCM with the expected format and severity.

## Next steps
{: #en-pd-ocm-migration-next-steps}

After completing the migration:

- Review and adjust your notification templates to match your team's requirements.
- Configure escalation policies in On Call Manager to route alerts to the appropriate on-call personnel.
- Set up notification rules in OCM to control how and when team members are notified.
- Monitor the integration for a few days to ensure all alerts are being received correctly.
- Once verified, you can decommission your PagerDuty integration.

For more information about {{site.data.keyword.en_short}} templates and customization, see:
- [Webhook notification templates](/docs/event-notifications?topic=event-notifications-en-webhook-notifications-template)
- [Creating templates](/docs/event-notifications?topic=event-notifications-en-create-template)
- [Mapping notification payload](/docs/event-notifications?topic=event-notifications-en-map-notification-payload)

