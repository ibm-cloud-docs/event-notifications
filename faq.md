---

copyright:
  years: 2020, 2021
lastupdated: "2021-05-24"

keywords: app-configuration, app configuration, faqs, Frequently Asked Questions, question, billing, service

subcollection: app-configuration

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{: note .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:faq: data-hd-content-type='faq'}

# FAQs for {{site.data.keyword.appconfig_short}} - usage and billing
{: #ac-faqs-usage}

FAQs for {{site.data.keyword.appconfig_short}} provides answers to common questions about {{site.data.keyword.appconfig_short}}.
{: shortdesc}

## How to create an {{site.data.keyword.appconfig_short}} instance?
{: #faq-ac-instance}
{: faq}

 1. Log in to your {{site.data.keyword.cloud_notm}} account.
 1. In the {{site.data.keyword.cloud_notm}} catalog, search *{{site.data.keyword.appconfig_short}}* and select **{{site.data.keyword.appconfig_short}}**. The service configuration screen opens.
 1. Select a <uicontrol>Region</uicontrol>.
 1. Select a <uicontrol>Pricing plan</uicontrol>.
 1. Configure your resource with <uicontrol>Service name</uicontrol>, or use the preset name.
 1. Select a <uicontrol>Resource group</uicontrol>.
 1. <step importance="optional"><cmd>Define </cmd> <uicontrol>Tags</uicontrol> that are needed to identify this service instance. If your tags are billing related, consider writing tags as key: value pairs to help group-related tags, such as costctr: 124.
 1. Click <uicontrol>Create</uicontrol>. A new service instance is created and the {{site.data.keyword.appconfig_short}} service console displayed.

## What pricing plans are available with {{site.data.keyword.appconfig_short}}?
{: #faq-ac-pricing}
{: faq}

 {{site.data.keyword.appconfig_short}} has three pricing plans:

| Plan  | Inclusions| Capabilities|Price|
| :-------------: |:-------------| :-----|:-----|
| Lite   | This plan is a free evaluation plan that includes 10 active entity IDs and 5,000 API calls.| Includes all {{site.data.keyword.appconfig_short}} capabilities for evaluation only. Not to be used for production.|Free|
| Standard      | The monthly instance price includes 1000 active entity IDs and 100,000 API calls. | This plan includes feature flags in addition to the property management capabilities.|<ul><li>$250.00 USD/Application instance</li><li>$0.01 USD/Active Entity ID</li><li>$10.00 USD/Hundred Thousand API Calls</li></ul>|
| Enterprise     | The monthly instance price includes 10,000 active entity IDs and 1,000,000 API calls. | This plan includes targeting to segments in addition to property management and feature flags that are found in the Standard plan. |<ul><li>$500.00 USD/Application instance</li><li>$0.01 USD/Active Entity ID</li><li>$10.00 USD/Hundred Thousand API Calls</li></ul>|

## What are the charges to use {{site.data.keyword.appconfig_short}}?
{: #faq-ac-charges}
{: faq}

The fundamental pricing metrics for {{site.data.keyword.appconfig_short}} are Application Instance, Active Entity ID, and API Call.  

**Application Instance**- An Application Instance is a uniquely named copy of {{site.data.keyword.appconfig_short}} created by you but managed by {{site.data.keyword.IBM_notm}}. Multiple instances of {{site.data.keyword.appconfig_short}} within a single environment are all considered separate application instances, as are individual {{site.data.keyword.appconfig_short}}instances in multiple environments (such as test, development, staging, or production). 

A single instance of {{site.data.keyword.appconfig_short}} can serve multiple environments, and in fact the service is designed to do so.{:note: .note}

**Active Entity ID**- An active entity ID is a unique identifier for each entity that interacts with the {{site.data.keyword.appconfig_short}} service. For example, an entity might be an instance of an app that runs on a mobile device, a microservice that runs on the cloud, or a component of infrastructure that runs that microservice. For any entity to interact with {{site.data.keyword.appconfig_short}}, it must provide a unique entity ID. This task is most easily accomplished by programming your app or microservice to send the Entity ID by using the {{site.data.keyword.appconfig_short}}SDK.

**API Call** - An API call is the invocation of the {{site.data.keyword.appconfig_short}} through a programmable interface.</br>
Exactly what constitutes an API call varies depending on the entity type (for example, a microservice or a mobile app). For server-side entities like microservices, when the state of a feature flag or property changes in the {{site.data.keyword.appconfig_short}}, a websocket connection notifies the SDK in the microservice that a state change occurred. The microservice then calls back into the {{site.data.keyword.appconfig_short}} to retrieve the update. This action is an API call.</br>
An API call also occurs on startup to the retrieve the initial configuration state. For client-side entities like mobile apps, websockets are not used. Instead, an API call fetches the current configuration state when a user opens the app, or brings it to the foreground. You can also programmatically call the {{site.data.keyword.appconfig_short}} to retrieve the most recent configuration state.

## How to view usage metrics for {{site.data.keyword.appconfig_short}}?
{: #faq-ac-metrics}
{: faq}

View basic historical {{site.data.keyword.appconfig_short}} usage metrics on the {{site.data.keyword.IBM_notm}} platform [Billing and Usage dashboard](https://cloud.ibm.com/billing/usage). If you need more sophisticated monitoring, create an {{site.data.keyword.monitoringlong_notm}} instance from the [Observability](https://cloud.ibm.com/observe) section of the {{site.data.keyword.Bluemix_notm}} console.

## How to predict {{site.data.keyword.appconfig_short}} cost?
{: #faq-ac-cost}
{: faq}

The simplest way to estimate cost for any {{site.data.keyword.Bluemix_notm}} managed service is to use the [{{site.data.keyword.Bluemix_notm}} Cost Estimator tool](https://cloud.ibm.com/docs/billing-usage?topic=billing-usage-cost).

</br>

Guidelines to help you predict cost in more detail: </br>

The **Application Instance** cost is a fixed monthly cost. If you delete an {{site.data.keyword.appconfig_short}} instance mid-month, the monthly Application Instance charge is pro-rated. To predict month instance cost, you must be aware of the number of {{site.data.keyword.appconfig_short}} instances you have and what pricing plan is assigned to each.</br>
See all your existing instances in the {{site.data.keyword.Bluemix_notm}} Console Resource List in the Services Section. Determine your plan either by clicking the Resource List row that contains your {{site.data.keyword.appconfig_short}}instance to reveal an information slide-out, or go to the instance dashboard and look in the Plan section.</br>  
Some {{site.data.keyword.appconfig_short}} pricing plans have a monthly Application Instance price and others do not. If the plan you select has an instance price, the price for the instance includes a set number of entity IDs and API calls that are included in the instance price. If you exceed the included allotment, your instance continues to operate normally but you accumulate an overage charge based on the published rate for entity IDs and API calls.</br></br>

The **Active Entity ID** cost is based on the number of unique entities that interact with your {{site.data.keyword.appconfig_short}} instance during the month. Entities self-identify when an API call is made, and each instance of your application provides a unique entity ID. You are not charged for entities that do not call {{site.data.keyword.appconfig_short}} during the month. If your pricing plan includes a free allotment of Active Entity IDs, then you are not charged until the allotment is exceeded.</br>
Active Entity ID cost can be difficult to predict so you need to closely monitor your historical activity. See [How to view usage metrics for {{site.data.keyword.appconfig_short}}?](/docs/app-configuration?topic=app-configuration-ac-faqs#faq-ac-metrics) Rely on your own domain knowledge, business metrics, and usage forecasts to predict Active Entity ID cost. </br></br>

The **API Call** cost is based on the number of API calls sent or received by {{site.data.keyword.appconfig_short}} during the month over all your entities combined. Check section - [What are the charges to use {{site.data.keyword.appconfig_short}}?](/docs/app-configuration?topic=app-configuration-ac-faqs#faq-ac-charges) to determine what constitutes an API call.</br>
If your pricing plan includes a free allotment of API calls, then you are not charged until the allotment is exceeded. Closely monitor your historical activity and check out [How to view usage metrics for {{site.data.keyword.appconfig_short}}?](/docs/app-configuration?topic=app-configuration-ac-faqs#faq-ac-metrics) Rely on your own domain knowledge, business metrics, and usage forecasts to predict cost. </br></br>

## Can you give some example pricing scenarios?
{: #faq-ac-sample}
{: faq}

### Pricing Scenario 1: Mobile App with Feature Flags
Assume you have a mobile app and you want feature flags and targeted segments to roll out features incrementally to different sets of users. Your historical metrics show 200,000 users but only about 50% are active in a month. An average active user opens the app or brings it to the foreground once every day. You expect to roll out a new feature twice per month.</br></br>
You need the {{site.data.keyword.appconfig_short}} Enterprise plan to support both feature flags and segmentation.</br> 
 {{site.data.keyword.appconfig_short}} Enterprise instances: 1 @ $500 per month </br>
 Active Entity IDs: 200,000 total app instances (users) * 50% active = 100,000</br>
 Included Active Entity IDs: 10,000</br>
 Net Active Entity IDs:  100,000 - 10,000 = 90,000 @ $0.01 per Active Entity ID = $900 </br></br>

 API Calls: 100,000 Active Entity IDs * 30 app invocations per month = 3,000,000</br> 
 Included API Calls: 1,000,000</br>
 Net API Calls: 3,000,000 - 1,000,000 = 2,000,000 @ $10/ 100,000 API Calls = $200 </br>
 TOTAL COST: $500 + $900 + $200 = $1600 per month </br></br>

### Pricing Scenario 2: Microservice with Feature Flags
Assume you have five backend microservices that support your mobile app. To fully test new microservice features, you want to dark launch them into production and target them only to testers. The mobile app is used worldwide, so you have the set of five microservices in each of 3 regions worldwide, and you want to test in your app in each region before going live. </br>
You are moving toward continuous delivery so on average you dark launch a new feature every 3 days (10 dark launches per month), and the feature undergoes a day or two of testing before being released (i.e. targeting removed). This results in 2 toggles per feature, one to activate the feature for testers, and one to remove targeting and activate for the general user population.</br>
You will need the {{site.data.keyword.appconfig_short}} Enterprise plan since both feature flags and segmentation are required.</br></br>     

{{site.data.keyword.appconfig_short}} Enterprise instances: 1 @ $500 per month </br>
Active Entity IDs: 5 entity IDs per region \* 3 regions = 15</br>
Included Active Entity IDs: 10,000 </br>
Net Active Entity IDs: 0 (all included) = $0 </br></br>
API Calls: 3 instances per region \* 3 regions \* (10 dark launches per month \* 2 toggles per release) = 180</br>
Included API Calls:  1,000,000</br>
Net API Calls:  0 (all included)  = $0</br></br>
TOTAL COST: $500 + $0 + $0 = $500 per month</br>

You might use the same instance of {{site.data.keyword.appconfig_short}} for both scenarios for a total cost of just over $1600 per month.
{: note .note}

## What are the capabilities, quotas, and limits for various aspects of the {{site.data.keyword.appconfig_short}} plans?
{: #faq-ac-capabilities}
{: faq}

|  | Lite| Standard|Enterprise|
| :-------------: |:-------------| :-----|:-----|
| Number of collaborators (team members) | No restriction| No restriction|No restriction|
| Max number of instances | 1 | No restriction|No restriction|
| Instance life| 30 days of inactivity | No restriction |No restriction|
| Base price for instance (monthly) | Free| $250|$500|
| Monthly active entity IDs included with instance | 10 | 1000|10,000|
| Monthly active entity ID overage price| Overage not allowed | $.01/MAE |$.01/MAE|
| Max monthly active entity IDs per instance| 10| Unlimited|Unlimited|
| API calls included with instance | 5,000 | 100,000|1,000,000|
| API call overage price| Overage not allowed | $.0001/API call |$.0001/API call|
| Max monthly API calls per instance| 5,000| Unlimited|Unlimited|
| Environments | 1 | 15|15|
| Collections| 1 | 20|Unlimited|
| Properties | 10 (properties + flags)| 1000|Unlimited|
| Property types |All | All|All|
| Max property size| 10 kB | 10 kB |10 kB|
| Max storage size (all properties) | 0.1 MB| 10 MB|10 MB|
| Flags | 10 (properties + flags) | 100|Unlimited|
| Attributes| Glean from response and custom attributes |  Glean from response and custom attributes  | Glean from response and custom attributes |
| Segments| 3| -|Unlimited|
| Segment definition rules per segment| 3 | -|25|
| Max targeting definition rules per instance| 3 | - |100|
| Targeting definition rules per feature| -| -|50|
| Delivery mode | Websocket (server)pull or get (client)|Websocket (server) pull or get(client)|Websocket(server)pull or get (client)|
| Role-based access| Env-level | Env-level|Env-level|
| Locations| London, Dallas, Sydney |  London, Dallas, Sydney | London, Dallas, Sydney |
| HA| Regional| Regional|Regional|
| Security| End-to-end encryption RBAC| End-to-end encryption RBAC|End-to-end encryption RBAC|
| Monitoring| IBM Cloud Monitoring| IBM Cloud Monitoring |IBM Cloud Monitoring|
| Audit| IBM Cloud Activity Tracker| IBM Cloud Activity Tracker|IBM Cloud Activity Tracker|
| Support | per your IBM Cloud support plan| per your IBM Cloud support plan|per your IBM Cloud support plan|
| Satellite integration and [Razee CRD](https://github.com/IBM/appconfiguration-razee)| - | -|Yes|

## How do I audit {{site.data.keyword.appconfig_short}} activity?
{: #faq-ac-audit}
{: faq}

If you need strict governance and accountability within your {{site.data.keyword.appconfig_short}} instance, create an instance of {{site.data.keyword.Bluemix_notm}} Activity Tracker from the [Observability]( https://cloud.ibm.com/observe) section of the {{site.data.keyword.Bluemix_notm}} console. Use that to record and audit {{site.data.keyword.appconfig_short}} activity.

## How do I archive {{site.data.keyword.appconfig_short}} activity data?
{: #faq-ac-archive}
{: faq}

If you would like to retain a long-term record of activity within your {{site.data.keyword.appconfig_short}} instance, either for audit purposes or for post-processing and data analysis, including application of machine learning models, create an instance of {{site.data.keyword.Bluemix_notm}} Activity Tracker from the [Observability]( https://cloud.ibm.com/observe) section of the {{site.data.keyword.Bluemix_notm}} console. Then archive events from an {{site.data.keyword.Bluemix_notm}} Activity Tracker instance into a bucket in an {{site.data.keyword.Bluemix_notm}} Object Storage (COS) instance. [Learn more](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-archiving )

## In what regions is {{site.data.keyword.appconfig_short}} available?
{: #faq-ac-regions}
{: faq}

To see a list of {{site.data.keyword.Bluemix_notm}} regions where you can provision instances of {{site.data.keyword.appconfig_short}}, see the [{{site.data.keyword.appconfig_short}} About](https://cloud.ibm.com/catalog/services/app-configuration#about ) page in the {{site.data.keyword.Bluemix_notm}} catalog.

## Is {{site.data.keyword.appconfig_short}} a highly available service?
{: #faq-ac-available}
{: faq}

Yes. {{site.data.keyword.appconfig_short}}is designed as a high availability service designed for enterprise workloads, and conforming to the [{{site.data.keyword.appconfig_short}} Service Description](https://www.ibm.com/support/customer/csol/terms/?id=i126-8986#detail-documentand) and the [{{site.data.keyword.Bluemix_notm}} Service Level Agreement]( https://cloud.ibm.com/docs/overview?topic=overview-slas) for availability. Within a single region, {{site.data.keyword.appconfig_short}} is deployed across a multi-zone cluster. 

## Is {{site.data.keyword.appconfig_short}} secure?
{: #faq-ac-security}
{: faq}
Yes. While {{site.data.keyword.appconfig_short}} is not designed as a vault for secrets (use {{site.data.keyword.secrets-manager_full_notm}} instead), the service itself adheres to strict security guidelines in the development process and in securing and protecting your data. The development process includes things like vulnerability scanning and remediation, periodic penetration testing, and frequent security reviews by world-class security experts. The data in {{site.data.keyword.appconfig_short}} is encrypted by default both in transit and at rest. (See the {{site.data.keyword.appconfig_short}} Data Processing and Protection data sheet to learn more). Additionally, you secure access to your own instances of {{site.data.keyword.appconfig_short}} by using {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). You can use {{site.data.keyword.Bluemix_notm}} Security and Compliance Center for ongoing security monitoring and alerts for your {{site.data.keyword.appconfig_short}} instances.
