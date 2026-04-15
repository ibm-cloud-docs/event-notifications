---

copyright:
  years: 2026
lastupdated: "2026-04-15"

keywords: about payload of notifications, store notifications, view notification, notification payloads, troubleshooting

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Viewing payloads of notifications
{: #en-view-notification-payloads}

You can view the payloads of incoming notifications in {{site.data.keyword.en_full_notm}} to validate notification payload formats, set up filters, and troubleshoot issues without routing notifications to external webhooks.
{: shortdesc}

The ability to view notification payloads allows you to inspect the format and content of notifications sent to your {{site.data.keyword.en_short}} instance. By examining the payload data, you can identify available fields, understand data formats, and verify that notifications contain the expected information. This capability is particularly valuable when setting up topic filters to route notifications based on specific field values, and when troubleshooting notification delivery issues to diagnose why notifications may not be reaching their intended destinations.

## Enabling notification storage
{: #en-view-notification-payloads-enable}

By default, {{site.data.keyword.en_short}} does not store incoming notification payloads. You must explicitly enable the **Store Notifications** option for each source to begin storing notifications. When you enable **Store Notifications** for a source, {{site.data.keyword.en_short}} begins storing incoming notifications from that source. Only notifications that arrive after you enable this option are stored. The **Notifications** column displays the number of notification payloads available for that source.

**Store Notifications** is not supported for periodic timer sources.
{: note}

To start storing notifications, you must enable the **Store Notifications** for the source you want to monitor.

To enable notifications storage:

1. In the {{site.data.keyword.cloud_notm}} console, go to your {{site.data.keyword.en_short}} instance.
2. In the navigation menu, click **Sources**.
3. Locate the source for which you want to store notifications.
4. In the **Store Notifications** column, click the toggle to enable notification storage for that source.

After you enable the **Store Notifications**, {{site.data.keyword.en_short}} begins storing all incoming notification payloads for that source. Notification payloads retain for 7 days and are automatically purged after this period. {{site.data.keyword.en_short}} stores a maximum of 100 notification payloads per instance. When this limit reaches, older notification payloads are automatically deleted to make room for new notification payloads.
{: important}

## Viewing stored notifications
{: #en-view-notification-payloads-view}

After you enable the **Store Notifications**, you can view stored notification payloads for the source. Only notifications received after enabling this option are available for viewing.

A side panel opens on the right side of the screen when you click the **Notifications** count, displaying the stored notification payloads for the selected source.

The **Source Events** side panel contains the following sections:

**Source details**
:   The top section displays information about the selected source:
    - **Source name**: The name of the source
    - **Source ID**: The unique identifier of the source
    - **Source type**: The type of source (for example, api, resource-lifecycle-events)

**Search**
:   A search field allows you to filter notification payloads by entering search criteria. The search filters notification payloads based on notification ID, timestamp, notification description (`ibmendefaultshort` parameter from the payload).

**List of notification payloads**
:   The main section displays a paginated list of stored notification payloads with the following columns:
    - **Notification ID**: The unique identifier of the notification payload
    - **Description**: A brief description of the notification payload
    - **Timestamp**: The date and time when the notification payload was received

### Viewing notification details
{: #en-view-notification-payloads-details}

To view the complete notification payload:

1. In the list of notification payloads within the side panel, locate the notification you want to inspect.
1. Click the expand button on the notification row to view the payload.
1. You can view the notification payload now in JSON format.

You can copy the JSON payload by clicking the copy icon in the upper right corner of the payload display.

## Disabling notification storage
{: #en-view-notification-payloads-disable}

When you no longer need to view notification payloads, you can disable the **Store Notifications** toggle to stop storing notifications.

To disable notification storage, in the **Store Notifications** column, click the toggle to disable notification storage for that source.

When you disable the **Store Notifications**, {{site.data.keyword.en_short}} stops storing new notification payloads for that source. Existing stored notification payloads retain until 7 days or until the total notification payloads reach the count 100 and older notifications are automatically deleted.
{: note}
