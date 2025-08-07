---

copyright:
  years: 2025
lastupdated: "2025-08-07"

keywords: event-notifications, event notifications, about event notifications, vpe, virtual private endpoints, virtual private endpoint gateways

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# Virtual Private Endpoint
{: #en-vpe}


Virtual Private Endpoints (VPE) for VPC enables you to connect to {{site.data.keyword.en_short}} and other supported {{site.data.keyword.cloud}} services from your VPC network by using the IP addresses of your choosing, allocated from a subnet within your VPC.

You can create an endpoint gateway for an {{site.data.keyword.cloud_notm}} service, third-party service or an application that you want to access on your private VPC network. You can either the console, CLI, API, or Terraform. 
{: shortdesc}


## Before you begin
{: #en-vpe-prereqs}

Before creating an endpoint gateway, ensure that you review [Planning for virtual private endpoint gateways](/docs/vpc?topic=vpc-planning-considerations) and have the following prerequisites:

- A VPC
- A subnet in at least one availability zone if you intend on binding an IP address at the same time you provision the endpoint gateway.
- An instance of the {{site.data.keyword.en_short}}
- Appropriate [IAM permissions](/docs/vpc?topic=vpc-vpe-iam) to create an endpoint gateway, create or bind a reserved IP, and view or list Event Notifications.
- Verification that the service you are configuring is enabled for VPE.

## Steps to provision a Virtual Private Endpoint Gateway by using console
{: #en-steps-vpe-gateway-ui}{: ui}

1. Login to your {{site.data.keyword.cloud_notm}} account.

1. On the [IBM Cloud Console](https://cloud.ibm.com), click the **Menu** icon ![Menu](images/icon_hamburger.svg) and navigate to **[Infrastructure](https://cloud.ibm.com/infrastructure/overview)** > **Network** > **Virtual Private Endpoint Gateways**.

1. On the console, click **Create**.


1. On the details page provide the **Geography**, **Region**, **Name** for your gateway, **Resource Group**, and select the **VPC** where you need the VPE IP address. To learn more about the fields, see [Viewing details of an endpoint gateway](/docs/vpc?topic=vpc-vpe-viewing-details-of-an-endpoint-gateway&interface=ui).

1. The security groups are used to tighten the security rules for inbound traffic toward your endpoint gateways. Select the checkbox for the security groups you want to attach to your gateway.
 
1. Select **{{site.data.keyword.en_short}}** under the **Request connection to a service** section.

1. Select the region and choose an endpoint.

1. In the **Reserved IP** section, select the option **Select one for me**. 

1. Review the order summary, then click **Create virtual private endpoint gateway**. The endpoint gateway is requested for use.

To learn more about the different fields, see [Ordering Endpoint Gateway](/docs/vpc?topic=vpc-ordering-endpoint-gateway&interface=ui).

## Steps to provision a Virtual Private Endpoint Gateway by using CLI
{: #en-steps-vpe-gateway-cli}{: cli}

1. Setup your [CLI environment](/docs/vpc?topic=vpc-set-up-environment&interface=cli).

1. List the IBM Cloud service instances that are qualified to be set as endpoint gateway targets:
    ```sh
    ibmcloud is endpoint-gateway-targets
    ```
    {: pre}

1. Create an endpoint gateway by running the following commands:

    ```sh
    ibmcloud is endpoint-gateway-create \
    --vpc VPC_ID \
    --target TARGET [--name NAME] [(--reserved-ip-id RESERVED_IP_ID1 --reserved-ip-id RESERVED_IP_ID2 ...) \
    | (--new-reserved-ip NEW_RESERVED_IP1 --new-reserved-ip NEW_RESERVED_IP2 ...)] \
    [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] \
    [--json]
   ```
   {: codeblock}

   Where:

   -   `--vpc`
      :   Indicates the ID of the VPC.

   -   `--target`
      :   Indicates the name or CRN of the {{site.data.keyword.en_short}} instance.

1. Create an endpoint gateway by attaching the target type for a private path service:

   ```sh
   ibmcloud is endpoint-gateway-create (--target-type private_path_service_gateway | provider_cloud_service | provider_infrastructure_service) --target TARGET [--vpc VPC] [--name NAME] [--rip RIP --subnet SUBNET | (--new-reserved-ip NEW_RESERVED_IP1 --new-reserved-ip NEW_RESERVED_IP2 ...)] [--sg SG] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name  RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
   ```
   {: codeblock}

   Where:

   `--target-type`:
   :   Indicates the type of target for this endpoint gateway, and one of the following: `private_path_service_gateway`, `provider_cloud_service`, or `provider_infrastructure_service`.

   `--vpc`:
   :   Indicates ID or name of the VPC.

   `--target`:
   :   Indicates the name of the provider infrastructure service or the CRN of the {{site.data.keyword.en_short}} instance. You can use the command `ibmcloud is endpoint-gateway-targets` to list the provider cloud and infrastructure services that are qualified to be set as the endpoint gateway target.

   `--name`:
   :   Indicates the new name of the endpoint gateway.

   `--reserved-ip-id`:
   :   Indicates the ID of the reserved IP to be bound to the endpoint gateway.

   `--new-reserved-ip`:
   :   Indicates the new reserved IP configuration in JSON format or a JSON file `RESERVED_IP_JSON|@RESERVED_IP_JSON_FILE`.

   `--security-group`:
   :   Indicates the ID of the security group.

    If you do not specify `-security-group`, the VPC default security group is bound to the endpoint gateway.
    {: note}

   `--resource-group-id`:
   :   Indicates the ID of the resource group. This option is mutually exclusive with `--resource-group-name`.

   `--resource-group-name`:
   :   Indicates the name of the resource group. This option is mutually exclusive with `--resource-group-id`.

   `--output`:
   :   Indicates the output format. Only JSON is supported.

   `-q, --quiet`:
   :   Suppresses verbose output.


## Steps to provision a Virtual Private Endpoint Gateway by using API
{: #en-steps-vpe-gateway-api}{: api}

1. Setup your [API environment](/docs/vpc?topic=vpc-set-up-environment&interface=api)

1. Store the following values in variables to be used in the API command:

   * **ResourceGroupId** - First, get your resource group and then populate the variable:

      ```sh
      export ResourceGroupId=<your_resourcegroup_id>
      ```
      {: pre}

   * **VpcId** - Use the `list vpc` command (with the preceding variables) and then populate the variable based on the provided ID:

      ```sh
      export VpcId=<your_VPC_id>
      ```
      {: pre}

   * **TargetCrn** - The name or CRN of the {{site.data.keyword.en_short}} instance where you want to set the endpoint gateway. You can use the command `ibmcloud is endpoint-gateway-targets` to list the IBM Cloud service instances that are qualified to be set as endpoint gateway targets.

      ```sh
      export TargetCrn=<CRN of a target service>
      ```
      {: pre}

   * `SubnetID` (Optional) - The subnet ID.

      ```sh
      export SubnetID=<your_subnet_id>
      ```
      {: pre}

1. When all variables are initiated, do one of the following:

   * Create an endpoint gateway for the specific VPC:

      ```sh
      curl -X POST -sH "Authorization:${iam_token}" \
      "$vpc_api_endpoint/v1/endpoint_gateways?version=$api_version&generation=2" \
      -d {
      "name": endpoint-gateway-1",
      "vpc": {"id":"'$VpcId'"},
      "target": {
      "crn": "$TargetCrn",
      "resource_type": "provider_cloud_service"
      },
      "security_groups": [
      {"id": "'$sg'"}
      ]
      }'
      ```
      {: codeblock}

      When creating an endpoint gateway to connect to a private path service, make sure '"resource type" = "private_path_service_gateway"'.
      {: note}

      After you create an endpoint gateway for your {{site.data.keyword.en_short}} instance and assign a reserved IP address, you must bind the IP addresses from your VPC network to the endpoint gateway. See [Binding and unbinding a reserved IP address](/docs/vpc?topic=vpc-bind-unbind-reserved-ip) for details. These bound IP addresses become the VPE to access the service that is mapped to the endpoint gateway.
      {: important}

   * Create an endpoint gateway with an associated reserved IP address:

      ```sh
      curl -X POST -sH "Authorization:${iam_token}" \
      "$vpc_api_endpoint/v1/endpoint_gateways?version=$api_version&generation=2" \
      -d {
      "name": endpoint-gateway-1",
      "vpc": {"id":"'$VpcId'"},
      "target": {
      "crn": "$TargetCrn",
      "resource_type": "provider_cloud_service"
      },
      "security_groups": [
      {"id": "'$sg'"}
      ],
      "ips": [
      {"subnet": { "id": "$SubnetId" } }
      ],
      }'
      ```
      {: codeblock}

      When creating an endpoint gateway to connect to a private path service, make sure that '"resource type" is set to `private_path_service_gateway`.
      {: note}

## Steps to provision a Virtual Private Endpoint Gateway by using Terraform
{: #en-steps-vpe-gateway-terraform}{: terraform}

1. Download the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in. For more information, see [Getting started with Terraform](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).

1. The following example creates a VPE gateway by using terraform

```hcl
resource "ibm_is_virtual_endpoint_gateway" "en_vpe_dal" {
  name = "en-test-gateway-dallas"
  target {
    crn           = <crn of your event notifications instance >
    resource_type = "provider_cloud_service"
  }
  vpc            = <vpc id of your vpc>
}
```

To find the different SMTP endpoints, see [Endpoints](/docs/event-notifications?topic=event-notifications-en-smtp-configurations#en-smtp-configurations-requirements). Find the VPC ID in your VPC instance, see [Creating and Configuring a VPC](/docs/vpc?topic=vpc-getting-started&interface=terraform#create-and-configure-vpc) to learn the process of creating a VPC.
