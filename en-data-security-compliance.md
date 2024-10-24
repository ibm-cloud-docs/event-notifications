---

copyright:
  years: 2022
lastupdated: "2022-11-18"

keywords: event-notifications, event notifications, about event notifications, data security, compliance, data security and compliance, ciphers

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Data security and compliance
{: #en-data-security-and-compliance}

{{site.data.keyword.en_short}} service has data security strategies in place to meet your compliance needs and ensure that your data remains secure and protected in the cloud.
{: shortdesc}

## Security readiness
{: #en-security-readiness}

{{site.data.keyword.en_short}} ensures security readiness by adhering to {{site.data.keyword.IBM_notm}} best practices for systems, networking, and secure engineering.

To learn more about security controls across {{site.data.keyword.cloud_notm}}, see [How do I know that my data is safe?](/docs/overview?topic=overview-security#security){: external}.
{: tip}

To learn more about how your data is secured in {{site.data.keyword.en_short}}, see [securing your data in {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-en-mng-data).

### Data encryption
{: #en-data-encryption}

{{site.data.keyword.en_short}} stores and encrypts details that are related to your destinations like email (sender, recipients, subject), or SMS (sender, recipient, details).

Access to {{site.data.keyword.en_short}} takes place over HTTPS and uses Transport Layer Security (TLS) to encrypt data in transit.

For more information on supported TLS ciphers, see [TLS cipher support](/docs/event-notifications?topic=event-notifications-en-cipher-support).

If you attempt to use a cipher that is not on this list, you may experience connectivity issues. Update your client to use one of the supported ciphers. If you are using `openssl`, you can use the command `openssl ciphers -v` at the command line (or, for some installations of `openssl`, use the `-s -v` options) to show a verbose list of what ciphers your client supports.
{: tip}

## Compliance readiness
{: #en-compliance-readiness}

{{site.data.keyword.en_short}} meets controls for global, industry, and regional compliance standards, including ISO
27001/27017/27018/27701, and others.

For a complete listing of {{site.data.keyword.cloud_notm}} compliance certifications, see [Compliance on the {{site.data.keyword.cloud_notm}}](https://ibm.com/cloud/compliance){: external}.
{: tip}

### ISO 27001, 27017, 27018, 27701
{: #en-iso}

{{site.data.keyword.en_short}} is ISO 27001, 27017, 27018, and 27701 certified. You can view compliance certifications by visiting [Compliance on the {{site.data.keyword.cloud_notm}}](https://ibm.com/cloud/compliance){: external}.
