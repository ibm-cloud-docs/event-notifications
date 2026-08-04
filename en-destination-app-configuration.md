---

copyright:
  years: 2026
lastupdated: "2026-08-04"

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

You can configure an {{site.data.keyword.appconfig_short}} destination in the **Destinations** tab.

### Before you begin
{: #en-config-prerequisites}

Before you begin, make sure that you have the following prerequisites in place:

- An {{site.data.keyword.appconfig_short}} instance with the environments and feature flags created. See [Creating an {{site.data.keyword.appconfig_short}} instance](/docs/app-configuration?topic=app-configuration-ac-create-an-instance) to learn the process of creating an {{site.data.keyword.appconfig_short}} instance.

- You need to create a [service-to-service authorization](/docs/event-notifications?topic=event-notifications-en-using-s2s-authorization&interface=ui) between {{site.data.keyword.en_short}} and {{site.data.keyword.appconfig_short}} service and assign the role of **Config Operator**.

### Configuration
{: #en-appconfig-steps-configure}

To configure {{site.data.keyword.appconfig_short}} as a destination, complete the following steps:

1. From your {{site.data.keyword.en_short}} instance, click **Destinations**.

1. Click **Create** to add a new destination.

1. Enter the following destination details in the **Create destination** dialog:
   - **Name**: Enter a name for your destination.
   - **Description**: Optionally, enter a description for your destination.
   - **Type**: Under **Destination**, select **{{site.data.keyword.appconfig_short}}**. Select the account that your {{site.data.keyword.appconfig_short}} instance is located in.
        - **This account**: If your {{site.data.keyword.appconfig_short}} instance is in the same account as your {{site.data.keyword.en_short}} instance, select **This account**. Select the **Instance name**, **Environments**, and **Feature Flag** to be toggled. All three fields must be populated to create the destination.
        - **Specific account**: If your {{site.data.keyword.appconfig_short}} instance and {{site.data.keyword.en_short}} instance are in different accounts, select **Specific account**. Provide a valid {{site.data.keyword.appconfig_short}} instance **CRN**, select the **Environments** and **Feature Flag** to be toggled. All three fields must be populated to create the destination.

1. Click **Create destination**.

1. Click **Topics** in the {{site.data.keyword.en_short}} instance and click **Create**. Enter the topic and filter details in the **Topic details** and **Event filters** steps, then click **Create topic**. See [Creating an {{site.data.keyword.en_short}} topic](/docs/event-notifications?topic=event-notifications-en-create-en-topic&interface=ui) for more information.

1. Proceed to the **Subscriptions** step. Click **Create** and enter the following subscription details in the **Create subscription** dialog:
    - **Subscription name**: Enter a name for the subscription.
    - **Destination type**: Select destination type.
    - **Destination**: Select destination.
    - **Attributes or Template**: When you create the {{site.data.keyword.appconfig_short}} subscription, either the attribute or template must be defined. These define the state of the feature flag when a notification is sent.
        - **Attributes**: You can enable or disable the feature flag when a notification is sent.
        - **Template**: Define the template under the **Templates** section of the left navigation pane. See [App Configuration Notification Template](/docs/event-notifications?topic=event-notifications-en-app-configuration-notification-template&interface=ui) for more information.

1. Click **Create subscription**.


## Testing {{site.data.keyword.appconfig_short}} destination configuration
{: #en-test-ac-destination}

You can test an {{site.data.keyword.appconfig_short}} destination in the options menu next to the destination. You can test whether the provided configuration is correct with a single click.

1. Click **Destinations** in the {{site.data.keyword.en_short}} instance.

1. On the destination you want to test, click the **Options** menu and select **Test Destination**.

1. Click the **Feature Flags** tab in your {{site.data.keyword.appconfig_short}} instance. If the destination is configured correctly, the feature flag is **enabled**, which indicates that your destination configuration is successful.


For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).

## {{site.data.keyword.appconfig_short}} retry policy
{: #en-appconfig-retry}

When sending notifications to {{site.data.keyword.appconfig_short}}, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
