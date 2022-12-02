---

copyright:
  years:  2022
lastupdated: "2022-11-28"

keywords: event notifications, event notification, notifications, managing encryption, byok, kyok, integrations protect, hpcs

subcollection: event-notifications

---
{{site.data.keyword.attribute-definition-list}}

# Managing encryption
{: #en-managing-encryption}

By default, customer data in {{site.data.keyword.en_short}} are encrypted at-rest using a randomly generated key. Although this default encryption model provides at-rest security, you might need a higher level of control. For these use cases, {{site.data.keyword.en_short}} supports customer-managed encryption with the following IBM Cloud® Key Management Services:

- {{site.data.keyword.keymanagementservicefull}} (Bring Your Own Key - BYOK) helps you provision encrypted keys for apps across {{site.data.keyword.cloud_notm}} services. As you manage the lifecycle of your keys, you can benefit from knowing that your keys are secured by FIPS 140-2 Level 3 certified cloud-based hardware security modules (HSMs) that protect against the theft of information. You can find out more about using {{site.data.keyword.keymanagementserviceshort}} in the [Getting Started tutorial](/docs/key-protect?topic=key-protect-getting-started-tutorial){: external}.
- {{site.data.keyword.hscrypto}} (Keep Your Own Key - KYOK) is a single-tenant, dedicated HSM that is controlled by you. The service is built on FIPS 140-2 Level 4-certified hardware, the highest offered by any cloud provider in the industry. You can find out more about using {{site.data.keyword.hscrypto}} in the [Getting Started tutorial](/docs/hs-crypto?topic=hs-crypto-get-started){: external}.

These services allow the use of a customer-provided key to control encryption. By disabling or deleting this key, you can prevent any further access to the data stored by the service, because it is no longer possible to decrypt it.
{: shortdesc}

Consider using customer-managed keys if you require the following features:

- Encryption of data at-rest controlled by your own key.
- Explicit control of the lifecycle of data stored at rest.
{: #considerations_keys notoc}

Customer-managed keys is available on the Standard plan only.
{: note}

Deletion of the customer-managed key is non-recoverable and will result in the loss of any data stored in your {{site.data.keyword.en_short}} instance.
{: important}

## What is not covered by customer-managed encryption
{: #en-encryption-what}

If customer-managed encryption feature is selected, the user should be aware that **only** customer data is covered by this encryption. {{site.data.keyword.en_short}} encrypts at-rest other data related to the use of the service.

You are not recommended to use confidential information in client metadata.
{: important}

## How customer-managed encryption works
{: #en-encryption-how}

{{site.data.keyword.en_short}} uses a concept called envelope encryption to implement customer-managed keys.

Envelope encryption is the practice of encrypting one encryption key with another encryption key. The key used to encrypt the actual data is known as a data encryption key (DEK). The DEK itself is never stored, but instead is wrapped by a second key known as the key encryption key (KEK) to create a wrapped DEK.

To decrypt data, the wrapped DEK must first be unwrapped to get the DEK. This process is possible only by accessing the KEK, which in this case is your root key stored in either [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-about){: external} or [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-overview){: external}.

You own the KEK, which you create as a root key in the {{site.data.keyword.hscrypto}} or {{site.data.keyword.keymanagementserviceshort}} service. The {{site.data.keyword.en_short}} service never sees the root (KEK) key. Its storage, management, and use to wrap and unwrap the DEK is performed entirely within the key management service. If you disable or delete the key, the data can no longer be decrypted.

## Enabling a customer-managed key for {{site.data.keyword.en_short}}
{: #en-enabling-encryption}

Complete the following steps to provision your {{site.data.keyword.en_short}} instance to use a customer-managed key:

1. Provision an instance of [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-provision){: external} or [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-provision){: external}.

1. Create an authorization policy to allow the {{site.data.keyword.en_short}} service to access the key management service instance as a Reader. For more information, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth){: external}.

1. Create or import a root key into your key management service instance.

1. Retrieve the Cloud Resource Name (CRN) of the key using the **View CRN** option in the key management service instance GUI.

1. Provision an instance of [{{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-en-create-en-instance). This feature is supported on the Standard plan only.

## Using a customer-managed key
{: #en-using-encryption}

After a customer-managed key is enabled, the cluster operates as normal, but with the following additional capabilities:

### Preventing access to data
{: #en-preventing-access}

To temporarily prevent access, you can disable your root key. As a consequence, {{site.data.keyword.en_short}} can no longer access the data because it can no longer access the key.

To remove access permanently, you can delete the key. However, you must take extreme caution because this operation is non-recoverable. You will lose access to any data stored in your {{site.data.keyword.en_short}} instance. There is no way to recover this data.

In both cases, the {{site.data.keyword.en_short}} instance shuts down and no longer accepts or processes connections. An activity tracker event is generated to report the action. For more information, see [{{site.data.keyword.en_short}} events](/docs/event-notifications?topic=event-notifications-en-at_events).

The authorization should be left in place between your {{site.data.keyword.en_short}} and the key management service instance at all times. While removing this authorization prevents {{site.data.keyword.en_short}} from future access to your data, already in-use data will continue to be available for a period of time.
{: note}

You are charged for your instance of {{site.data.keyword.en_short}} until you deprovision it using the {{site.data.keyword.cloud_notm}} console or CLI. These charges are still applied even if you chose to prevent access to your data.
{: important}

### Restoring access to data
{: #restoring_access}

Access can be restored only if the key was not deleted. To restore access, re-enable your root key. After a short period of initialization, your {{site.data.keyword.en_short}} instance is restarted and starts accepting connections again. All data is retained, subject to the normal retention limits configured in your instance.

An activity tracker event is generated to report the action. For more information, see [{{site.data.keyword.cloudaccesstrailshort}} events](/docs/event-notifications?topic=event-notifications-en-at_events).

### Rotating the key
{: #rotating_key}

{{site.data.keyword.keymanagementserviceshort}} and {{site.data.keyword.hscrypto}} support the rotation of root keys, either on demand or on a schedule. When this occurs, {{site.data.keyword.en_short}} adopts the new key by rewrapping the DEK as described in [how customer-managed encryption works](#en-encryption-how).

An activity tracker event is generated to report the action. For more information, see [{{site.data.keyword.cloudaccesstrailshort}} events](/docs/event-notifications?topic=event-notifications-en-at_events).

## Disabling customer-managed encryption
{: #stop_customer_encryption}

After enabling customer-managed encryption, it is not possible to disable it. Instead, you must delete the service instance and create a new instance.
