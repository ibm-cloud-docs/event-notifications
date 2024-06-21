---

copyright:
  years: 2022
lastupdated: "2022-11-18"

keywords: event-notifications, event notifications, about event notifications, data security, compliance, data security and compliance, ciphers

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:preview: .preview}

# Monitoring {{site.data.keyword.en_full}} metrics
{: #en-manage-monitor-metrics}

After you set up your {{site.data.keyword.en_full_notm}} service
instance, you can manage monitoring metrics by using this feature.
{: shortdesc}

## Metrics settings
{: #en-manage-metrics-policy}

Metrics for {{site.data.keyword.en_short}} service instances is
a policy that allows you to receive the notfication metrics for your
{{site.data.keyword.en_short}} instance. When you enable this
policy, {{site.data.keyword.en_short}} can be used to track your notifications metrics in real-time.

Enabling {{site.data.keyword.en_short}} metrics is currently only available
Custom Email Domains.
{: preview}

Before you enable operational metrics for your
{{site.data.keyword.en_short}} instance, keep in mind the
following considerations:

- **Enable your {{site.data.keyword.cloud_notm}} Monitoring for your {{site.data.keyword.en_full_notm}} instance.**
    You need to [provision {{site.data.keyword.cloud_notm}} Monitoring](https://cloud.ibm.com/catalog/services/ibm-cloud-monitoring?callback=/observe/monitoring/create) instance on your {{site.data.keyword.IBM}} account.

- **When you enable metrics for your {{site.data.keyword.en_full_notm}} instance, metrics are only reported after the time that the policy is enabled.**
    Once your metrics policy is enabled, you can then customize and monitor your metrics.

- **Ensure you have the required level of access to view the metrics.**
    To view the metrics, you need the [**Operator** platform role or higher]({[link]}-access-management). You must also have access to the credentials that are needed to access your resource configurations.

### Set up metrics for your {{site.data.keyword.keymanagementserviceshort}} instance with the Console
{: #enable-metrics-instance-policy-ui}

After creating a {{site.data.keyword.en_short}} instance, complete the following steps to enable the metrics:

1. [Log in to the {{site.data.keyword.cloud_notm}} console](/login/){: external}.

1. Go to **Menu** &gt; **Resource List** to view a list of your resources.

1. From your {{site.data.keyword.cloud_notm}} resource list, select your
    provisioned instance of {{site.data.keyword.en_short}}.
    Otherwise, you can [create a new {{site.data.keyword.en_short}} service instance](/docs/event-notifications?topic=event-notifications-en-create-en-instance).

1. Click `Metrics` in the {{site.data.keyword.en_short}} console.

## Understanding the dashboard
{: #understand-dashboard}

As you evaluate your resources, the results are returned via the service UI in graphical and detailed formats.

![A visual representation of the service dashboard. The concepts are fully explained in the surrounding text.](images/dashboard.svg){: caption="Figure 2. Example dashboard" caption-side="bottom"}

When you visit the dashboard, there are three graphical representations of data that has been aggregated from your scans. You see the:

Success rate
:   The rate at which your configurations pass the evaluation that is conducted. **Note:** The number of evaluations conducted does not always match the number of billable evaluations, as there is no charge for assessments evaluated as unable to perform. Be sure to look for the billable evaluations in each scan result if you need to estimate your cost.

Total controls
:   The total number of controls that have been evaluated in the past 30 days.

Total evaluations
:   The total number of evaluations that have been run in the past 30 days. An evaluation is the check of one resource against one assessment.
