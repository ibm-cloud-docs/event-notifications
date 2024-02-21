---

copyright:
  years: 2023, 2024
lastupdated: "2024-02-21"

keywords: event-notifications, event notifications, about event notifications, troubleshooting, faqs, Frequently Asked Questions, question, can't create IAM credentials, can't regenerate IAM credentials, IAM credentials not working, IP address restrictions enabled, IP address not allowed

subcollection: event-notifications

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why am I unable to perform an action when working with Event Notifications?
{: #en-ip-address-not-allowed}
{: troubleshoot}
{: support}

When you try to use {{site.data.keyword.en_short}} service instance you are unable to perform the action that you're attempting to complete.
{: shortdesc}

When you try to access any feature in {{site.data.keyword.en_short}} service instance either through the console or API or CLI, you may encounter an error similar to any of the following examples:
{: tsSymptoms}

```json
You do not have permission to perform this action. Contact your service Administrator.
```
{: screen}

or

```json
{
  "message": "Unauthorized"
}
```
{: screen}

This is due to the reason that you are trying to access the {{site.data.keyword.en_short}} service instance from a Network Zone which is outside of the defined Network zone in your account's Context-based restrictions settings.
{: tsCauses}

To resolve the issue, make sure that your Context-based restrictions settings in the account are updated to allow the IP addresses that correspond with your network in the Network Zone's Allowed IP addresses. As an administrator of your {{site.data.keyword.en_short}} service instance perform the following steps.
{: tsResolve}

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage > Context-based restrictions**.
1. Go to **Network zones** and then select the required Network Zone and select **Edit** from the overflow menu.
1. In the **Allowed IP addresses**, include the required IP addresses that you want to enable access to the {{site.data.keyword.en_short}} service instance.
1. Click **Update**.

For more information, see [Managing access with context-based restrictions](/docs/event-notifications?topic=event-notifications-en-access-control-cbr).
