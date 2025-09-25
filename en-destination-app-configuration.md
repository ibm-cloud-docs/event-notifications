---

copyright:
  years: 2025
lastupdated: "2025-09-25"

keywords: event-notifications, event notifications, about event notifications, destinations,app configuration, app config

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.appconfig_notm}}
{: #en-destination-app-configuration}

{{site.data.keyword.appconfig_short}} is a centralized feature management and configuration service for use with web and mobile applications, microservices, and distributed environments. You can define feature flags, which are organized into collections and targeted to segments. Change feature flag states in the cloud to activate or deactivate features in your application or environment, often without restarting.
{: shortdesc}

The {{site.data.keyword.appconfig_short}} destination helps you toggle the feature flags by leveraging various {{site.data.keyword.en_short}} capabilities. For example, you can use the Periodic Timer source that is provided by {{site.data.keyword.en_short}} to schedule the toggling of feature flags.


## Configuring an {{site.data.keyword.appconfig_short}} destination
{: #en-appconfig-configure}

You can configure an {{site.data.keyword.appconfig_short}} destination in the `Destinations` tab.

### Before you begin
{: #en-config-prerequisites}

Before you begin, make sure that you have the following prerequisites in place:

- An {{site.data.keyword.appconfig_short}} instance with the environments and feature flags created. See [Creating an {{site.data.keyword.appconfig_short}} instance](/docs/app-configuration?topic=app-configuration-ac-create-an-instance) to learn the process of creating an {{site.data.keyword.appconfig_short}} instance.

- You need to create a [service-to-service authorization](/docs/event-notifications?topic=event-notifications-en-using-s2s-authorization&interface=ui) between {{site.data.keyword.en_short}} and {{site.data.keyword.appconfig_short}} service and assign the role of **Config Operator**.

### Configuration
{: #en-appconfig-steps-configure}

To configure {{site.data.keyword.appconfig_short}} as a destination, perform the following steps:

1. From your {{site.data.keyword.en_short}} instance dashboard, click **Destinations**.

1. Click **Add +** to add a new destination.

1. In the **Add a destination** side panel, provide the following details.
   - **Name** - Enter a name for your destination.
   - **Description** - Optionally, enter a description for your destination.
   - **Type** - Under **Destination** > **Type**, select {{site.data.keyword.appconfig_short}}. Select the account that your {{site.data.keyword.appconfig_short}} instance is located in.
        - **This account** - If your {{site.data.keyword.appconfig_short}} instance is located in the same account as your {{site.data.keyword.en_short}} instance, select **This account**. Select the **Instance name**, **Environments** and **Feature Flag** to be toggled. All 3 fields must be populated to create the instance.
        - **Specific account** - If your {{site.data.keyword.appconfig_short}} instance and {{site.data.keyword.en_short}} instance are in different accounts, select **Specific account**. Provide a valid {{site.data.keyword.appconfig_short}} instance **CRN, select the **Environments** and **Feature Flag** to be toggled. All 3 fields must be populated to create the instance.

1. Click **Add**.

1. Create a topic with a source of your choice. See [Creating an {{site.data.keyword.en_short}} topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic&interface=ui) to learn the process of creating a topic.

1. To create a subscription, navigate to the **Subscriptions** dashboard from the left navigation pane and click **Create**. 
    - Provide the **Name**, an optional **Description**, and select the **Topic** and **Destination** created previously.
    - You can choose to send the notification based on **Attributes** or on a **Template**. While creating the {{site.data.keyword.appconfig_short}} subscription, either the attribute or template must be defined. These define the state of the feature flag while sending a notification.
        - **Attributes** - If you choose to send the notification based on attributes, you can choose to enable the feature flag or disable it when a notification is sent.
        - **Template** - If you choose to send the notification based on a template, you need to define the template under the **Templates** section of the left navigation pane. See [App Configuration Notification Template](/docs/event-notifications?topic=event-notifications-en-appconfig-notification-template&interface=ui) to learn the process of creating a template to send notifications to {{site.data.keyword.appconfig_short}}.

1. Click **Create**.


## Testing {{site.data.keyword.appconfig_short}} destination configuration
{: #en-test-ac-destination}

You can test an {{site.data.keyword.appconfig_short}} destination in the options menu that is provided against the destination. You can effortlessly test a destination, whether the provided configuration is correct or not with a single click.

1. Navigate to the **Destinations** tab on the left navigation pane of your {{site.data.keyword.en_short}} instance.

1. On the destination you want to test, click the overflow menu ![Overflow Menu](/images/overflow-menu.svg) and select **Test Destination**.

1. Navigate to the **Feature Flags** tab in your {{site.data.keyword.appconfig_short}} instance and if the destination is configured correctly the feature flag should be **enabled**. This indicates that your destination configuration is successful.


For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).
