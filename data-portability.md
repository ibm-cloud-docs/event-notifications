---

copyright:
  years: 2024
lastupdated: "2024-11-13"

keywords:

subcollection: schematics

---

{{site.data.keyword.attribute-definition-list}}

# Understanding data portability for {{site.data.keyword.en_full_notm}}
{: #data-portability}

Data portability involves a set of tools and procedures that enable customers to export the digital artifacts that are needed to implement similar workload and data processing on different service providers or on-premises software. It includes procedures for copying and storing the service customer content, including the related configuration that is used by the service to store and process the data, on the customer's own location.
{: shortdesc}

## Responsibilities
{: #data-portability-responsibilities}

{{site.data.keyword.cloud_notm}} services provide interfaces and instructions to guide the customer to copy and store the service customer content, including the related configuration, on their own selected location.
{: shortdesc}

The customer is responsible for the use of the exported data and configuration for data portability to other infrastructures, which includes:

- The planning and execution for setting up alternative infrastructure on different cloud providers or on-premises software that provide similar capabilities to the {{site.data.keyword.IBM_notm}} services.
- The planning and execution for the porting of the required application code on the alternative infrastructure, including the adaptation of customer's application code, deployment automation.
- The conversion of the exported data and configuration to the format that is required by the alternative infrastructure and adapted applications.

For more information about your responsibilities for {{site.data.keyword.en_full}}, see [Shared responsibilities for {{site.data.keyword.en_full}}](/docs/event-notifications?topic=event-notifications-en-responsibilities).

## Data export procedures
{: #data-portability-procedures}

{{site.data.keyword.en_full_notm}} provides the mechanisms to export your content that is uploaded, stored, and processed when you use the service.

For each data set that you need to export, use `GET` calls to get a copy of the data. And use the corresponding `PUT / POST API` to populate the new instance at the place where the data is copied.

|Entity   | Endpoint | Description |
|---------|--------|-----------|
| sources | `/v1/instances/{instance_id}/sources` | Your platform sources |
| topics | `/v1/instances/{instance_id}/topics` | All registered topics |
| destinations | `/v1/instances/{instance_id}/destinations` | All registered destinations |
| subscriptions | `/v1/instances/{instance_id}/subscriptions` | All the subscriptions |
| metrics | `/v1/instances/{instance_id}/metrics` | All the metrics |
| templates | `/v1/instances/{instance_id}/templates` | All the templates |
| SMTP configurations| `/v1/instances/{instance_id}/smtp/config` | All the smtp configurations|
| integrations | `/v1/instances/{instance_id}/integrations` | All the integrations|
{: caption="Example API endpoints" caption-side="top"}

For more information about all available APIs for exporting data, see [API documentation](https://cloud.ibm.com/apidocs/event-notifications).

/metrics does not have have a POST/PUT api as they are the metrics of usage of the service.
{: note}

## Exported data formats
{: #data-portability-data-formats}

{{site.data.keyword.en_full_notm}} resources export the data via Service APIs in JSON format. The schema of the exported data is described in the {{site.data.keyword.en_full_notm}} service [API documentation](https://cloud.ibm.com/apidocs/event-notifications).

## Data ownership
{: #data-portability-ownership}

All exported data is classified as customer content and is therefore applied to them full customer ownership and licensing rights, as stated in [{{site.data.keyword.cloud_notm}} Service Agreement](https://www.ibm.com/support/customer/csol/terms/?id=Z126-6304_WS&cc=in&lc=en){: external}.
