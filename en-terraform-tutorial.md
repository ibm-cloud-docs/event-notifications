---

copyright:
  years: 2022, 2024
lastupdated: "2024-10-10"

keywords: event notifications, event-notifications, tutorials, terraform

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for {{site.data.keyword.en_short}}
{: #en-tera-workwith}

Use Terraform to configure files like `provider.tf` to declare {{site.data.keyword.en_short}} resources for deployment.
{: shortdesc}

## Before you begin
{: #en-prereqs}

Make sure that the following prerequisites are in place:

* Install Terraform. For more information, see [Download Terraform](https://developer.hashicorp.com/terraform/install){: external}.

* Either deploy Terraform to a specific folder or add it to your `PATH`.

* Check the Terraform version:

   ```bash
   terraform –version
   ```
   {: codeblock}

* You need an {{site.data.keyword.cloud_notm}} account. If you don't have an account, then create an {{site.data.keyword.cloud_notm}} account. For more information on how to create an account, see[Create an IBM Cloud account](https://cloud.ibm.com/registration/){: external}.

* Log in to your {{site.data.keyword.cloud_notm}} account.

## Working with Terraform in {{site.data.keyword.cloud_notm}}
{: #en-work-terraform-cloud}

To work with Terraform and the {{site.data.keyword.cloud_notm}}, a plug-in is required to extend the current functions. For more information on how to install and configure the {{site.data.keyword.cloud_notm}} plug-in, see [terraform-provider-ibm](https://github.com/IBM-Cloud/terraform-provider-ibm){: external}. 

The following instructions use Provider 1.38.2. For more information, see [{{site.data.keyword.cloud_notm}} Provider](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs){: external}.

1. Create a hidden directory from the home directory:

   ```bash
   mkdir $HOME/.terraform.d/plugins
   ```
   {: codeblock}

1. Download and move the plug-in to the directory that you created. For more information, see [terraform-provider-ibm](https://github.com/IBM-Cloud/terraform-provider-ibm/releases){: external}.

   ```bash
   mv $HOME/Downloads/terraform-provider-ibm_v1.38.2 $HOME/.terraform.d/plugins/
   ```
   {: codeblock}

1. Connect to your {{site.data.keyword.cloud_notm}} account with {{site.data.keyword.cloud_notm}} API Key.

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: external} and go to the **Managed** tile and select **Access(IAM)**, and then select **{{site.data.keyword.cloud_notm}} API Keys**.

1. Create an {{site.data.keyword.cloud_notm}} API Key and save the password.

## Deploying resources
{: #en-resources-deploy}

Create an {{site.data.keyword.en_short}} resource. For more information, see [Getting started with {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-getting-started).

## Building Infrastructure-as-Code
{: #en-infrastructure-as-code}

The `tf-template` directory contains the following Terraform configuration files:

### `provider.tf`
{: #en-provider-tf}

`provider.tf` creates the required providers.

```hcl
terraform {
   required_providers {
      ibm = {
         source = "IBM-Cloud/ibm"
         version = "1.38.2"
      }
   }
}
```
{: codeblock}

### `variables.tf`
{: #en-variables-tf}

`variables.tf` stores passwords or other values that are required for Terraform at run time.

```hcl
variable "instance_id" {
   type        = string
   default     = "235b109c-0a2c-438b-8758-1a4b9db044db"
   description = "Event Notifications service instanceId."
}

variable "destination_name" {
   type        = string
   default     = "Smart Home Android app"
   description = "Destination name."
}

variable "destination_description" {
   type        = string
   default     = "Smart House device status"
   description = "Description for the destination."
}

variable "webhook_type" {
   default     = "webhook"
   type        = string
   description = "Type of the destination"
}

variable "webhook_verb" {
   default     = "POST"
   type        = string
   description = "Type of verb fro the destination"
}

variable "webhook_URL" {
   type        = string
   description = "URL of the webhook"
   default     = "https://hello.demo.com/hello"
}
```
{: codeblock}

The remaining files declare the resources to be deployed.

### `instance.tf`
{: #en-instance-tf}

`instance.tf` provisions an {{site.data.keyword.en_short}} instance.

```hcl
resource "ibm_resource_instance" "terraform_demo" {
   plan     = "lite"
   location = "us-south"
   name     = "terraform_demo"
   service  = "event-notifications"
}
```
{: codeblock}

### `destinations.tf`
{: #en-destinations-tf}

`destinations.tf` uses {{site.data.keyword.en_short}} to create destinations.

```hcl
resource "ibm_en_destination" "destination1" {
   type          = var.webhook_type
   name          = var.destination_name
   description   = var.destination_description
   instance_guid = ibm_resource_instance.terraform_demo.guid
   config {
      params {
         url  = var.webhook_URL
         verb = var.webhook_verb
         custom_headers = {
           "authorization" = "secure"
         }
         sensitive_headers = ["authorization"]
      }
   }
}
```
{: codeblock}

### `topics.tf`
{: #en-topics-tf}

`topics.tf`uses {{site.data.keyword.en_short}} to create topics.

```hcl
resource "ibm_en_topic" "topic1" {
   instance_guid = ibm_resource_instance.terraform_demo.guid
   description   = "Check the status of front door"
   name          = "Front Door Status"
}
```
{: codeblock}

### `subscriptions.tf`
{: #en-subscriptions-tf}

`subscriptions.tf`uses {{site.data.keyword.en_short}} to create subscriptions.

```hcl
resource "ibm_en_subscription" "subscription1" {
   instance_guid  = ibm_resource_instance.terraform_demo.guid
   name           = "Android app Subscription"
   description    = "Subscribe to Android app"
   topic_id       = ibm_en_topic.topic1.topic_id
   destination_id = ibm_en_destination.destination1.destination_id
   attributes {
      add_notification_payload = true
      signing_enabled          = true
   }
}
```
{: codeblock}

## Running your Terraform
{: #en-execute-tf}

Before you run any Terraform scripts, learn the following Terraform commands:

### Terraform **init**
{: #en-init-tf}

The Terraform **init** command prepares the environment to make sure that the directory is configured properly:

```bash
bash-5.1# terraform init

Initializing the backend...

Initializing provider plugins...
- Reusing previous version of ibm-cloud/ibm from the dependency lock file
- Using previously-installed ibm-cloud/ibm v1.38.2

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```
{: codeblock}

### Terraform **plan**
{: #en-plan-tf}

The Terraform **plan** command compares the declared resources with the state file to print the resources to be created, altered, or deleted. This step shows you the impact of the `main.tf` file.

```bash
bash-5.1# terraform plan

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
   + create

Terraform will perform the following actions:

   # ibm_en_destination.destination1 will be created
   + resource "ibm_en_destination" "destination1" {
      + description        = "Smart House device status"
      + destination_id     = (known after apply)
      + id                 = (known after apply)
      + instance_guid      = (known after apply)
      + name               = "Smart Home Android app"
      + subscription_count = (known after apply)
      + subscription_names = (known after apply)
      + type               = "webhook"
      + updated_at         = (known after apply)

      + config {
         + params {
            + custom_headers    = {
               + "authorization" = "secure"
            }
            + sensitive_headers = [
               + "authorization",
            ]
            + url               = "https://hello.demo.com/hello"
            + verb              = "POST"
         }
      }
   }

  # ibm_en_subscription.subscription1 will be created
  + resource "ibm_en_subscription" "subscription1" {
      + description      = "Subscribe to Android app"
      + destination_id   = (known after apply)
      + destination_name = (known after apply)
      + destination_type = (known after apply)
      + from             = (known after apply)
      + id               = (known after apply)
      + instance_guid    = (known after apply)
      + name             = "Android app Subscription"
      + subscription_id  = (known after apply)
      + topic_id         = (known after apply)
      + topic_name       = (known after apply)
      + updated_at       = (known after apply)

      + attributes {
         + add_notification_payload = true
         + signing_enabled          = true
      }
   }

   # ibm_en_topic.topic1 will be created
   + resource "ibm_en_topic" "topic1" {
      + description        = "Check the status of front door"
      + id                 = (known after apply)
      + instance_guid      = (known after apply)
      + name               = "Front Door Status"
      + source_count       = (known after apply)
      + subscription_count = (known after apply)
      + subscriptions      = (known after apply)
      + topic_id           = (known after apply)
      + updated_at         = (known after apply)
   }

   # ibm_resource_instance.terraform_demo will be created
   + resource "ibm_resource_instance" "terraform_demo" {
      + account_id              = (known after apply)
      + allow_cleanup           = (known after apply)
      + created_at              = (known after apply)
      + created_by              = (known after apply)
      + crn                     = (known after apply)
      + dashboard_url           = (known after apply)
      + deleted_at              = (known after apply)
      + deleted_by              = (known after apply)
      + extensions              = (known after apply)
      + guid                    = (known after apply)
      + id                      = (known after apply)
      + last_operation          = (known after apply)
      + location                = "us-south"
      + locked                  = (known after apply)
      + name                    = "terraform_demo"
      + plan                    = "lite"
      + plan_history            = (known after apply)
      + resource_aliases_url    = (known after apply)
      + resource_bindings_url   = (known after apply)
      + resource_controller_url = (known after apply)
      + resource_crn            = (known after apply)
      + resource_group_crn      = (known after apply)
      + resource_group_id       = (known after apply)
      + resource_group_name     = (known after apply)
      + resource_id             = (known after apply)
      + resource_keys_url       = (known after apply)
      + resource_name           = (known after apply)
      + resource_plan_id        = (known after apply)
      + resource_status         = (known after apply)
      + restored_at             = (known after apply)
      + restored_by             = (known after apply)
      + scheduled_reclaim_at    = (known after apply)
      + scheduled_reclaim_by    = (known after apply)
      + service                 = "event-notifications"
      + service_endpoints       = (known after apply)
      + state                   = (known after apply)
      + status                  = (known after apply)
      + sub_type                = (known after apply)
      + tags                    = (known after apply)
      + target_crn              = (known after apply)
      + type                    = (known after apply)
      + update_at               = (known after apply)
      + update_by               = (known after apply)
   }
```
{: codeblock}

## Exporting an API key
{: #en-exportkey-tf}

Export your {{site.data.keyword.cloud_notm}} API Key before you run the **apply** command:

```bash
export IBMCLOUD_API_KEY={Your IBM Cloud API Key}
```
{: codeblock}

## Running Terraform **apply**
{: #en-apply-tf}

The Terraform **apply** command implements the changes that are declared during the **plan** step and deploys the resource to the {{site.data.keyword.cloud_notm}}.

```bash
bash-5.1# terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # ibm_en_destination.destination1 will be created
  + resource "ibm_en_destination" "destination1" {
      + description        = "Smart House device status"
      + destination_id     = (known after apply)
      + id                 = (known after apply)
      + instance_guid      = (known after apply)
      + name               = "Smart Home Android app"
      + subscription_count = (known after apply)
      + subscription_names = (known after apply)
      + type               = "webhook"
      + updated_at         = (known after apply)

      + config {
          + params {
              + custom_headers    = {
                  + "authorization" = "secure"
                }
              + sensitive_headers = [
                  + "authorization",
                ]
              + url               = "https://hello.demo.com/hello"
              + verb              = "POST"
            }
        }
    }

  # ibm_en_subscription.subscription1 will be created
  + resource "ibm_en_subscription" "subscription1" {
      + description      = "Subscribe to Android app"
      + destination_id   = (known after apply)
      + destination_name = (known after apply)
      + destination_type = (known after apply)
      + from             = (known after apply)
      + id               = (known after apply)
      + instance_guid    = (known after apply)
      + name             = "Android app Subscription"
      + subscription_id  = (known after apply)
      + topic_id         = (known after apply)
      + topic_name       = (known after apply)
      + updated_at       = (known after apply)

      + attributes {
          + add_notification_payload = true
          + signing_enabled          = true
        }
    }

  # ibm_en_topic.topic1 will be created
  + resource "ibm_en_topic" "topic1" {
      + description        = "Check the status of front door"
      + id                 = (known after apply)
      + instance_guid      = (known after apply)
      + name               = "Front Door Status"
      + source_count       = (known after apply)
      + subscription_count = (known after apply)
      + subscriptions      = (known after apply)
      + topic_id           = (known after apply)
      + updated_at         = (known after apply)
    }

  # ibm_resource_instance.terraform_demo will be created
  + resource "ibm_resource_instance" "terraform_demo" {
      + account_id              = (known after apply)
      + allow_cleanup           = (known after apply)
      + created_at              = (known after apply)
      + created_by              = (known after apply)
      + crn                     = (known after apply)
      + dashboard_url           = (known after apply)
      + deleted_at              = (known after apply)
      + deleted_by              = (known after apply)
      + extensions              = (known after apply)
      + guid                    = (known after apply)
      + id                      = (known after apply)
      + last_operation          = (known after apply)
      + location                = "us-south"
      + locked                  = (known after apply)
      + name                    = "terraform_demo"
      + plan                    = "standard"
      + plan_history            = (known after apply)
      + resource_aliases_url    = (known after apply)
      + resource_bindings_url   = (known after apply)
      + resource_controller_url = (known after apply)
      + resource_crn            = (known after apply)
      + resource_group_crn      = (known after apply)
      + resource_group_id       = (known after apply)
      + resource_group_name     = (known after apply)
      + resource_id             = (known after apply)
      + resource_keys_url       = (known after apply)
      + resource_name           = (known after apply)
      + resource_plan_id        = (known after apply)
      + resource_status         = (known after apply)
      + restored_at             = (known after apply)
      + restored_by             = (known after apply)
      + scheduled_reclaim_at    = (known after apply)
      + scheduled_reclaim_by    = (known after apply)
      + service                 = "event-notifications"
      + service_endpoints       = (known after apply)
      + state                   = (known after apply)
      + status                  = (known after apply)
      + sub_type                = (known after apply)
      + tags                    = (known after apply)
      + target_crn              = (known after apply)
      + type                    = (known after apply)
      + update_at               = (known after apply)
      + update_by               = (known after apply)
    }

Plan: 4 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

ibm_resource_instance.terraform_demo: Creating...
ibm_resource_instance.terraform_demo: Still creating... [10s elapsed]
ibm_resource_instance.terraform_demo: Still creating... [20s elapsed]
ibm_resource_instance.terraform_demo: Still creating... [30s elapsed]
ibm_resource_instance.terraform_demo: Still creating... [40s elapsed]
ibm_resource_instance.terraform_demo: Still creating... [50s elapsed]
ibm_resource_instance.terraform_demo: Creation complete after 52s [id=crn:v1:bluemix:public:event-notifications:us-south:a/4a74f2c31f554afc88156b73a1d577c6:24547d88-e455-548f-cb6e-ge921g6d3025::]
ibm_en_topic.topic1: Creating...
ibm_en_destination.destination1: Creating...
ibm_en_destination.destination1: Still creating... [10s elapsed]
ibm_en_topic.topic1: Still creating... [10s elapsed]
ibm_en_topic.topic1: Creation complete after 12s [id=24547d88-e455-548f-cb6e-ge921g6d3025/7960f1fe-7991-4993-ad0c-38f12c78b3c8]
ibm_en_destination.destination1: Creation complete after 13s [id=24547d88-e455-548f-cb6e-ge921g6d3025/878ce8e6-75f9-41e6-913f-6b42f6945588]
ibm_en_subscription.subscription1: Creating...
ibm_en_subscription.subscription1: Creation complete after 4s [id=24547d88-e455-548f-cb6e-ge921g6d3025/b2d88ff9-da10-412a-9f7a-19f509ea83fb]

Apply complete! Resources: 4 added, 0 changed, 0 destroyed..
```
{: codeblock}

## Validating resources
{: #en-validate-tf}

Validate resources within the {{site.data.keyword.cloud_notm}} by selecting the resource list in [resources](https://cloud.ibm.com/resources){: external}.

For more information on API and SDK references, tutorials, and FAQs, for {{site.data.keyword.cloud_notm}} products and services, see [Documentation](https://cloud.ibm.com/docs).
