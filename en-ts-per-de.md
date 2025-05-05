---

copyright:
  years: 2019, 2024
lastupdated: "2024-10-08"

keywords: question about event notifications, permission, integrating, authorization, authorize

subcollection: event-notifications

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why don't I have permissions to integrate an {{site.data.keyword.en_short}} instance?
{: #troubleshoot-integrate}
{: troubleshoot}
{: support}

You are denied permission while integrating an {{site.data.keyword.en_short}} service instance with an IBM Cloud Service.
{: shortdesc}

You get a 'Permission denied' message, while integrating {{site.data.keyword.en_short}} service instance with IBM Cloud service.
{: tsSymptoms}

{{site.data.keyword.en_short}} integration APIs use Service to Service [authorization](/docs/account?topic=account-serviceauth&interface=ui){: external}.
{: tsCauses}

Grant authorization between the IBM Cloud Service (for example: Security and Compliance Center) and {{site.data.keyword.en_short}} service instance.
{: tsResolve}

Manage --> Access (IAM) --> Authorization --> Create

![Create authorization](images/en-ts-authorize.png "Authorize event notifications in SCC"){: caption="Grant authorization" caption-side="bottom"}
