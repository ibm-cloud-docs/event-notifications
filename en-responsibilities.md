---

copyright:
  years: 2021
lastupdated: "2021-03-16"

keywords: app-configuration, app configuration, customer responsibilities, IBM responsibilities, terms and conditions, disaster recovery, toolchain backup

subcollection: app-configuration

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Understanding your responsibilities when using App Configuration
{: #ac-responsibilities}
{: help}
{: support}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.appconfig_notm}}. For a high-level view of the service types in {{site.data.keyword.cloud_notm}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.cloud_notm}} {{site.data.keyword.appconfig_notm}}. For the overall terms of use, see [{{site.data.keyword.cloud}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## Incident and operations management
{: #ac-incident-and-ops}

You and {{site.data.keyword.IBM_notm}} share responsibilities for the set up and maintenance of your {{site.data.keyword.appconfig_notm}} instance.

You are responsible for incident and operations management of your application and application data.

|Task     |{{site.data.keyword.IBM_notm}} Responsibilities |Your Responsibilities |
|-------------|-----------------------|-----------------------|
|Incidents |Provide notifications for planned maintenance, security bulletins, or unplanned outages. |Set preferences to receive emails about platform notifications, and monitor the {{site.data.keyword.cloud_notm}} status page for general announcements. |
{:caption="Table 1. Responsibilities for incident and operations" caption-side="top"}

## Change management
{: #ac-change-management}

You and {{site.data.keyword.IBM_notm}} share responsibilities for keeping {{site.data.keyword.appconfig_notm}} service components at the latest version.

You are responsible for change management of your application and application data.

|Task     |{{site.data.keyword.IBM_notm}} Responsibilities |Your Responsibilities |
|-------------|-----------------------|-----------------------|
|Applications |Provide infrastructure operating system (OS), version, and security updates. |Use the API, SDK, CLI, or console tools to apply the provided updates for the local entities (app code, CLI, and SDK). |
{:caption="Table 2. Responsibilities for change management" caption-side="top"}

## Identity and access management
{: #ac-identity-and-access-management}

You and {{site.data.keyword.IBM_notm}} share responsibilities for controlling access to your {{site.data.keyword.appconfig_notm}} instances and resources.

You are responsible for identity and access management to your application and application data.

|Task     |{{site.data.keyword.IBM_notm}} Responsibilities |Your Responsibilities |
|-------------|-----------------------|-----------------------|
|Applications |Provide the ability to restrict access to resources.	|Depending on your needs, restrict access to resources and service functionality by using Cloud IAM access policies. For more information, see [Managing user access](/docs/app-configuration?topic=app-configuration-ac-service-access-management). |
{:caption="Table 3. Responsibilities for identity and access management" caption-side="top"}

## Security and regulation compliance
{: #ac-sec-and-reg-compliance}

{{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.appconfig_notm}}. 

You are responsible for the security and compliance of your application and application data.

|Task     |{{site.data.keyword.IBM_notm}} Responsibilities |Your Responsibilities |
|-------------|-----------------------|-----------------------|
|Encryption |<ul><li>Automatically apply security patch updates for infrastructure.</li><li>Enable certain security settings, such as encrypted disks.</li><li>Disable certain insecure actions, such as not permitting users to SSH into the host.</li><li>Encrypt communication with TLS.</li><li>Continuously monitor {{site.data.keyword.appconfig_notm}} entities to detect vulnerability and security compliance issues.</li><li>Integrate {{site.data.keyword.appconfig_notm}} with {{site.data.keyword.IBM_notm}} {{site.data.keyword.iamshort}} (IAM).</li></ul> |Manage {{site.data.keyword.cloud_notm}} credentials, and keep credentials secure. |
{:caption="Table 4. Responsibilities for security and regulation compliance" caption-side="top"}

## Disaster recovery
{: #ac-disaster-recovery}

{{site.data.keyword.IBM_notm}} is responsible for the recovery of {{site.data.keyword.appconfig_notm}} components in case of disaster.

You are responsible for the recovery of the workloads that run {{site.data.keyword.appconfig_notm}} and your application and application data.

|Task     |{{site.data.keyword.IBM_notm}} Responsibilities |Your Responsibilities |
|-------------|-----------------------|-----------------------|
|Availability |<ul><li>Provide high availability capabilities, such as {{site.data.keyword.IBM_notm}}-owned infrastructure in multizone regions, to meet local access and low latency requirements for each supported region. </li><li>Run {{site.data.keyword.appconfig_notm}} deployments with three replicas in the same region for high availability.</li><li>Continuously monitor {{site.data.keyword.appconfig_notm}} infrastructure to ensure the reliability and availability of the service environment by site reliability engineers.</li><li>Maintain service availability across [worldwide regions](/docs/app-configuration?topic=app-configuration-ac-regions-endpoints#ac-regions) so that customers can deploy projects across zones and regions for higher DR tolerance.</li></ul> |<ul><li>Use the list of [available regions](/docs/app-configuration?topic=app-configuration-ac-regions-endpoints#ac-regions) to plan for and create new instances of the service to meet performance and availability requirements above and beyond the default provided by {{site.data.keyword.IBM_notm}}.</li><li>Set up additional {{site.data.keyword.appconfig_notm}} instances across zones and regions to increase disaster recovery tolerance above the default provided by {{site.data.keyword.IBM_notm}}.</li></ul>
{:caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}

