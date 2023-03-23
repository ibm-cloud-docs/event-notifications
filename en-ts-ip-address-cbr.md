---

copyright:
  years: 2023
lastupdated: "2023-03-24"

keywords: event-notifications, event notifications, about event notifications, troubleshooting, faqs, Frequently Asked Questions, question, can't create IAM credentials, can't regenerate IAM credentials, IAM credentials not working, IP address restrictions enabled, IP address not allowed

subcollection: event-notifications

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why am I blocked from ordering a public certificate or generating IAM credentials?
{: #en-ip-address-not-allowed}
{: troubleshoot}
{: support}

When you try to use {{site.data.keyword.en_short}} to order public certificates or generate IAM credentials, but the service is unable to complete the action.
{: shortdesc}

You're working in an {{site.data.keyword.cloud_notm}} account that has [IP address access restrictions](/docs/account?topic=account-ips). When you try to use a feature in {{site.data.keyword.en_short}} that requires a user-provided {{site.data.keyword.cloud_notm}} API key, for example, when you generate IAM credentials, you encounter an error similar to the following examples:
{: tsSymptoms}

```json
IAM credentials couldn't be regenerated because IP address restrictions are enabled for the account. Update the IP address settings in your account to include IP addresses for Secrets Manager and try again.
```
{: screen}

```json
Cloud Internet Services (CIS) couldn't be reached because IP address restrictions are enabled for the account. Update the IP address settings in your account to include IP addresses for Secrets Manager and try again.
```
{: screen}

These errors can occur when {{site.data.keyword.en_short}} attempts to log in to the target account with the configured API key in order to complete the request. However, the service is unable to do so because the account allows access to specific IP addresses only. To allow the account to accept requests from {{site.data.keyword.en_short}}, you must specify an allowlist of IP addresses, along with your own IP address.
{: tsCauses}

To resolve the issue, ensure that the IP address restriction settings in the account are updated to allow the IP addresses that correspond with the region in which your {{site.data.keyword.en_short}} is located.
{: tsResolve}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage > Access (IAM)**, and select **Settings**.
2. From the Account restrictions section, edit the **IP address access** setting.
3. In the Allowed IP addresses field, include the allowlist of IP addresses that you defined based on the locations where access requests originate. For more information, see [Managing access with context-based restrictions](/docs/event-notifications?topic=event-notifications-en-access-control-cbr).
