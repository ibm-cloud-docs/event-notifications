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

# Monitoring metrics
{: #en-manage-monitor-metrics}

After you set up your {{site.data.keyword.keymanagementservicelong}} service
instance, you can manage monitoring metrics by using the service API.
{: shortdesc}

## Metrics settings
{: #en-manage-metrics-policy}

Metrics for {{site.data.keyword.keymanagementserviceshort}} service instances is
an extra policy that allows you to receive the operational metrics for your
{{site.data.keyword.keymanagementserviceshort}} instance. When you enable this
policy, {{site.data.keyword.mon_short}} can be used to monitor any operations
that are performed on the resources in your
{{site.data.keyword.keymanagementserviceshort}} instance.

Enabling {{site.data.keyword.en_short}} metrics is currently only available
Custom Email Domains.
{: preview}

Before you enable operational metrics for your
{{site.data.keyword.en_short}} instance, keep in mind the
following considerations:

- **When you enable metrics for your {{site.data.keyword.keymanagementserviceshort}} instance, metrics are only reported after the time that the policy is enabled.**
    Once your metrics policy is enabled, you will see operational metrics for all
    API requests that occur in your instance after the the policy is activated.
    You will not be able to view any metrics prior to the time that the policy is
    enabled.

- **You will need to provision a {{site.data.keyword.mon_short}} instance for your policy in order to see the metrics.**
    You will need to
    [provision a {{site.data.keyword.mon_short}} instance](/docs/monitoring?topic=monitoring-provision){: external}
    that is located in the same region as the
    {{site.data.keyword.keymanagementserviceshort}} instance that you would like
    to receive operational metrics for. Once you provision the
    {{site.data.keyword.mon_short}} instance, you will need to
    [enable platform metrics](/docs/key-protect?topic=key-protect-operational-metrics#configure-monitor).

### Enabling metrics for your {{site.data.keyword.keymanagementserviceshort}} instance with the Console
{: #enable-metrics-instance-policy-ui}

After creating a {{site.data.keyword.keymanagementserviceshort}} instance,
provisioning a {{site.data.keyword.mon_short}}, and enabling platform metrics,
complete the following steps to enable a metrics policy:

1. [Log in to the {{site.data.keyword.cloud_notm}} console](/login/){: external}.

2. Go to **Menu** &gt; **Resource List** to view a list of your resources.

3. From your {{site.data.keyword.cloud_notm}} resource list, select your
    provisioned instance of {{site.data.keyword.keymanagementserviceshort}}.

4. On the **Instance policies** page, click the **Enable** button
    in the metrics policy section.

### Enabling metrics for your {{site.data.keyword.keymanagementserviceshort}} instance with the API
{: #enable-metrics-instance-policy-api}
