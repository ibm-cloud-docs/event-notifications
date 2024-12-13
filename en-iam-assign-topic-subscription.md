---

copyright:
  years: 2024
lastupdated: "2024-12-13"

keywords: event-notifications, event notifications, managing service access, iam, account, topics, subscriptions

subcollection: event-notifications

content-type: tutorial
account-plan: standard
completion-time: 15m

---
{{site.data.keyword.attribute-definition-list}}

# Assigning access to an individual topics and subscriptions
{: #en-assign-access-to-topics-subscriptions}
{: toc-content-type="tutorial"}
{: toc-completion-time="15m"}

This tutorial shows you how to assign access roles for Users against Topics and Subscriptions, by creating and modifying IAM access policies.
{: shortdesc}

## Before you begin
{: #topics-subscriptions-access-step-0}

If you are already managing instances of Event Notifications or IAM, you do not need to create more. However, as this tutorial will modify and configure the instance we are working with, make sure that any accounts or services are not being used in a production environment.

For this tutorial, you need:

- An {{site.data.keyword.cloud}} Platform account
- An instance of {{site.data.keyword.cloud_notm}} {{site.data.keyword.en_short}}
- To complete the steps to manage access to the service, you should be the owner of the {{site.data.keyword.en_short}} instance. In other words, your user ID needs **administrator platform permissions** to use the IAM service. You may have to contact or work with an account administrator.

## Grant Reader access to {{site.data.keyword.en_short}} instance
{: #topics-subscriptions-access-step-1}
{: step}

To enable access to a specific topic/subscription in an instance, the user must at least have **Reader** level privileges to the particular {{site.data.keyword.en_short}} instance.
{: note}

Only **Writer** access is available for a particular topic/subscription.
{: important}

1. Navigate to IAM by following the **Manage** drop-down menu, and selecting **Access (IAM)**. Follow the **Users** link in the navigation menu, and select the user requiring limited access.
2. Click on **Access** tab. Click on the **Assign access** button. Select the **Access policy** tile and select **{{site.data.keyword.en_short}}**.
3. Select the radio toggle next to **Specific resources**. Select **Service Instance** from the _Attribute type_ drop-down menu. Select the {{site.data.keyword.en_short}} instance which you want to assign access. ![Create a new policy](images/en-assign-access-instance.png){: caption="Figure 1: Selecting Event Notifications instance."}
4. In the _Roles and access_ section, select the role **Reader**. You'll also need the Platform **Viewer** role, if you don't already have it, in order to view the UI. ![Create a new policy](images/en-assign-reader-viewer.png){: caption="Figure 2: Selecting Roles for Event Notification instance."}
5. Click **Next** and include conditions if needed which is optional.
6. Click **Add**.

## Grant Writer access to specific Environment
{: #topics-subscriptions-access-step-2}
{: step}

We'll repeat the step 1, but this time we'll use **Topic ID/Subscription ID** resource attribute and select **Writer** role.

Only **Writer** access is available for a particular topic/subscription.
{: important}

In an access policy , we can have either topic ID **or** subscription ID. Both cannot be present in the same access policy. If you want an access policy for more than 1 topics/subscriptions , create separate access policies for each topic/subscription.
{: note}

1. Navigate to the Topics/Subscriptions section of your {{site.data.keyword.en_short}} instance and copy the Topic/Subscription ID.![Create a new policy](images/en-topic-id.png){: caption="Accessing Topic ID"} ![Create a new policy](images/en-subscription-id.png){: caption="Accessing Subscription ID"}
2. Click on the **Assign access** button. Select the **Access policy** tile and select **Event Notification**.
3. Select the radio toggle next to **Specific resources**. Select **Topic ID/Subscription ID** from the _Attribute type_ drop-down menu. Paste the Topic/Subscription ID that you had copied in step 1. ![Create a new policy](images/en-select-subscription.png){: caption="Selecting specific Topic/Subscription"}
4. In the _Roles and access_ section, select the role **Writer**. ![Create a new policy](images/en-access-writer.png){: caption="Selecting Roles for specific Topic/Subscription"}
5. Click **Next** and include conditions if needed which is optional.
6. Click **Add**.

## Review access policies
{: #topics-subscriptions-access-step-3}
{: step}

At this stage, you should have two access policies created as shown below. One access policy with **Reader & Viewer**, another with **Writer** role.

![Create a new policy](images/en-verify-access.png){: caption="Reviewing Access Policies"}

## Verify that it works
{: #topics-subscriptions-access-step-4}
{: step}

When this {{site.data.keyword.en_short}} instance is accessed by shared use with Writer role, user can only update topics or and subscriptions.

When shared user tries to perform any action such as toggle a feature flag, update a feature flag on other topics/subscriptions using API/CLI/Terrform, the action is denied with **403** status code as shown below.
{: note}

```javascript
{
  "status_code":403,
  "trace":"e7bed498-6a41-4af0-89dc-cc08c4dc0e45",
  "errors": [{"code":"authorization_error",
  "message":"Unfortunately you don't have a permission to access requested resource",
  "more_info":"https://test.cloud.ibm.com/apidocs/event-notifications#event-notifications-api-authentication" }]
}
```
{: codeblock}
