---

copyright:
  years: 2020, 2021
lastupdated: "2021-03-29"

keywords: app-configuration, app configuration, about app configuration

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

# What is {{site.data.keyword.appconfig_short}}?
{: #ac-about}

{{site.data.keyword.appconfig_notm}} is a centralized feature management and configuration service for use with web and mobile applications, microservices, and distributed environments.
{:shortdesc}

Instrument your applications with {{site.data.keyword.appconfig_short}} SDKs, and use the {{site.data.keyword.appconfig_short}} dashboard or {{site.data.keyword.appconfig_short}} administrator API to define features flags, which are organized into collections and targeted to segments. Change feature flag states in the cloud to activate or deactivate features in your application or environment, often without restarting. You can also manage the properties for distributed applications centrally.

- **App Owners** - Roll out features by segment and independent from code deployments.
- **Developers** - Reduce source code branch complexity and troublesome merges by including untested or unfinished features behind a feature flag in your master branch.
- **Testers** - Test new features in production and be assured of a smooth transition. Use flags to activate untested features only for testers and QA personnel until it's time to release.

## Features
{: #ac-features}

Key features of {{site.data.keyword.appconfig_short}}

- **Centralized configuration** - Configure multiple, distributed resources from a central location. Use collections to organize your flags by app or resource.
- **Dark Launch** - Includes features that are not ready for launch into your deployments, and activate them when they are ready.
- **Segmented Feature Rollout** - Activate features for different segments at different times, or vary features by segment.
- **Feature Rollback** - Instantly roll back problematic features by toggling feature flags in the {{site.data.keyword.appconfig_short}} cloud dashboard.
