---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-11"

keywords: data encryption in Event Notifications, data storage for Event Notifications, bring your own keys for Event Notifications, BYOK for Event Notifications, key management for Event Notifications, key encryption for Event Notifications, personal data in Event Notifications, data deletion for Event Notifications, data in Event Notifications, data security in Event Notifications, KYOK for Event Notifications

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.en_short}}
{: #en-mng-data}

To ensure that you can securely manage your data when you use {{site.data.keyword.en_full}}, you must know exactly what data is stored and encrypted and you must know how to delete any stored data.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.en_short}}
{: #en-data-storage}

{{site.data.keyword.en_short}} stores and encrypts details that are related to your destinations like email (sender, recipients, subject), or SMS (sender, recipient, details). As a multi-tenant service, every tenant has a designated encryption key and user data in each tenant is encrypted with only that tenant's key. This tenant key is protected by using {{site.data.keyword.en_short}} managed Key Protect. {{site.data.keyword.en_short}} ensures that private information is encrypted before it is stored.

You can add a higher level of encryption control to your data at rest (when it is stored) by enabling integration with a Key Management Service (KMS). The data that you store in {{site.data.keyword.cloud_notm}} is encrypted at rest by using envelope encryption. If you need to control the encryption keys, you can integrate Key Protect or Hyper Protect Crypto Services. This process is commonly referred to as Bring Your Own Key (BYOK). With Key Protect and Hyper Protect Crypto Services, you can create, import, and manage encryption keys. You can assign access policies to the keys, assign users or service IDs to the keys, or give the key access only to a specific service.

For more information, see [Managing encryption](/docs/event-notifications?topic=event-notifications-en-managing-encryption).

## Protecting your sensitive data in {{site.data.keyword.en_short}}
{: #en-data-sensitive}

The data that you store in the {{site.data.keyword.en_short}} instance is encrypted at rest by using a randomly generated key, which is in turn protected by Key Protect, managed by {{site.data.keyword.en_short}} service.

## Deleting your data in {{site.data.keyword.en_short}}
{: #en-data-delete}

The {{site.data.keyword.en_short}} data retention policy describes how long your data is stored after you delete the service. As in {{site.data.keyword.cloud_notm}} data retention policy you can [restore](/docs/account?topic=account-resource-reclamation&interface=cli#restore-resource-cli) a resource within 7 days after you delete it.

### Commands to delete data
{: #en-data-delete-cmd}

1. Log in to your {{site.data.keyword.cloud_notm}} account by using {{site.data.keyword.cloud_notm}} CLI from terminal.
1. `ibmcloud resource reclamations` lists your deleted instance along with the reclamation ID for it.
1. Use `ibmcloud resource reclamation-delete <reclamation_id_for_instance>` to permanently delete data that is related to a deleted instance.
1. If an instance is not restored, all related data is automatically deleted after the data retention period.

### Deleting {{site.data.keyword.en_short}} instances
{: #en-delete}

If you no longer need an instance of {{site.data.keyword.en_short}}, you can delete the service instance by using {{site.data.keyword.cloud_notm}} CLI. You can also choose to delete your service instance by using the console. Any data that is stored related to that instance is also deleted.

### Restoring deleted data for {{site.data.keyword.en_short}}
{: #en-data-restore}

To restore a deleted instance or to delete the instance permanently, you can use Resource Reclamations. For more information about resource reclamation, see [Using Resource Reclamations](/docs/account?topic=account-resource-reclamation).

## Data security and compliance
{: #en-data-security-and-compliance1}

{{site.data.keyword.en_short}} service has data security strategies in place to meet your compliance needs and ensure that your data remains secure and protected in the cloud.

### Security readiness
{: #en-security-readiness1}

{{site.data.keyword.en_short}} ensures security readiness by adhering to {{site.data.keyword.IBM_notm}} best practices for systems, networking, and secure engineering.

To learn more about security controls across {{site.data.keyword.cloud_notm}}, see [How do I know that my data is safe?](/docs/overview?topic=overview-security#security){: external}.
{: tip}

To learn more about how your data is secured in {{site.data.keyword.en_short}}, see [securing your data in {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-en-mng-data).

#### Data encryption
{: #en-data-encryption1}

{{site.data.keyword.en_short}} stores and encrypts details that are related to your destinations like email (sender, recipients, subject), or SMS (sender, recipient, details).

Access to {{site.data.keyword.en_short}} takes place over HTTPS and uses Transport Layer Security (TLS) to encrypt data in transit.

For more information on supported TLS ciphers, see [TLS cipher support](/docs/event-notifications?topic=event-notifications-en-cipher-support).

If you attempt to use a cipher that is not on this list, you may experience connectivity issues. Update your client to use one of the supported ciphers. If you are using `openssl`, you can use the command `openssl ciphers -v` at the command line (or, for some installations of `openssl`, use the `-s -v` options) to show a verbose list of what ciphers your client supports.
{: tip}

### Compliance readiness
{: #en-compliance-readiness1}

{{site.data.keyword.en_short}} meets controls for global, industry, and regional compliance standards, including ISO
27001/27017/27018/27701, and others.

For a complete listing of {{site.data.keyword.cloud_notm}} compliance certifications, see [Compliance on the {{site.data.keyword.cloud_notm}}](https://ibm.com/cloud/compliance){: external}.
{: tip}

#### ISO 27001, 27017, 27018, 27701
{: #en-iso1}

{{site.data.keyword.en_short}} is ISO 27001, 27017, 27018, and 27701 certified. You can view compliance certifications by visiting [Compliance on the {{site.data.keyword.cloud_notm}}](https://ibm.com/cloud/compliance){: external}.
