---

copyright:
  years:  2022
lastupdated: "2022-11-28"

keywords: event notifications, event notification, notifications, integrations, key protect, key management, hyper protect, hpcs

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Integrations
{: #en-integrations}

Integrations in {{site.data.keyword.en_short}} represent list of other {{site.data.keyword.cloud_notm}} services that are connected to your {{site.data.keyword.en_short}} instance. You can encrypt the data that you store in {{site.data.keyword.cloud_notm}} databases by using encryption keys that you can control.
{: shortdesc}

You can use either one of the following options:
- Bring Your Own Key (BYOK) through {{site.data.keyword.keymanagementservicelong_notm}}, and use one of your own keys to encrypt your databases and backups.
- Hyper Protect Crypto Services (HPCS) - {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}, a dedicated key management service, and Hardware Security Module (HSM) that provides you with the Keep Your Own Key capability for cloud data encryption with exclusive control of your encryption keys.

BYOK and KYOK capabilities are supported only for {{site.data.keyword.en_short}} Standard plan.
{: important}

For more information, see [Managing encryption](/docs/event-notifications?topic=event-notifications-en-managing-encryption).

## Integrating with a Key management service
{: #en-int-key-management}

You can create and bring keys that are created by using {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.hscrypto}}. To get started, you need [{{site.data.keyword.keymanagementserviceshort}}](https://cloud.ibm.com/catalog/key-protect){: external} or [{{site.data.keyword.hscrypto}}](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services) provisioned on your {{site.data.keyword.cloud_notm}} account. For more information, see [provisioning a key protect instance](https://cloud.ibm.com/docs/key-protect?topic=key-protect-provision){: external} or see [provisioning a {{site.data.keyword.hscrypto}} instance](/docs/hs-crypto?topic=hs-crypto-get-started){: external}.

1. From your {{site.data.keyword.en_short}} service instance dashboard, click **Integrations**. By default, a Key Protect entry is listed, that can be edited to configure the **Key Management** option of your choice, connecting to your {{site.data.keyword.en_short}} instance.

1. From Overflow menu of the default entry, click **Edit**. This displays the **Key Management** side panel.

1. Select **Key Protect** or **Hyper Protect Crypto Services** from the **Service** drop-down list, as per your requirement.

1. For the **Instance**, select one of these options:
   - **Create a new instance** - to create a new instance of the selected service. This will take you to the respective provisioning page of the service selected.
   - **Choose existing instance** - select this option if you already have a {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.hscrypto}} instance. Select the **Service** instance and **Root key** from the drop-down list.

1. Click **Save** to apply the changes.

The updated **Key Management** information is listed in the **Integrations** dashboard.
