---

copyright:
  years: 2026
lastupdated: "2026-08-04"

keywords: about payload of notifications, store notifications, view notification, notification payloads, troubleshooting

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Viewing event payloads
{: #en-view-notification-payloads}

You can view the payloads of incoming events in {{site.data.keyword.en_full_notm}} to validate payload formats, set up filters, and troubleshoot issues without routing them to external webhooks.
{: shortdesc}

The ability to view event payloads allows you to inspect the format and content of events sent to your {{site.data.keyword.en_short}} instance. By examining the payload data, you can identify available fields, understand data formats, and verify that payloads contain the expected information. This capability is particularly valuable when setting up topic filters to route events based on specific field values, and when troubleshooting notification delivery issues to diagnose why these notifications may not be reaching their intended destinations.

## Enabling storage of event payloads
{: #en-view-notification-payloads-enable}

By default, {{site.data.keyword.en_short}} does not store incoming event payloads. You must explicitly enable **Capture events** for a source for {{site.data.keyword.en_short}} to begin storing event payloads from that source. Only event payloads that arrive after you enable this option are stored.

**Capture events** is not supported for periodic timer sources.
{: note}

To enable this storage:

1. Click **Sources** in your {{site.data.keyword.en_short}} instance.
1. Locate the source for which you want to store event payloads and enable **Capture events** for that source.

After you enable **Capture events**, {{site.data.keyword.en_short}} begins storing all incoming event payloads for that source. Event payloads are retained for 7 days and are automatically purged after this period. {{site.data.keyword.en_short}} stores a maximum of 100 event payloads per instance. When this limit is reached, older event payloads are automatically deleted to make room for new ones.
{: important}

## Viewing stored event payloads
{: #en-view-notification-payloads-view}

After you enable **Capture events**, you can view stored event payloads for the source. Only events received after you enable this option are available for viewing.

To view event payloads:

1. Select **View events** from the **Options** menu for the source for which you enabled storage of event payloads.

1. The **Source Events** dialog contains the following sections:

    **Source details**
    :   The top section displays **Source name**, **Source ID** and **Source type** of the selected source.

**Search**
:   A search field allows you to filter event payloads by entering search criteria. The search filters event payloads based on notification ID, timestamp, summary (`ibmendefaultshort` parameter from the payload).

**List of events payloads** displays **Notification ID**, **Summary** and **Timestamp** of each event payload. 

### Viewing event payload details
{: #en-view-notification-payloads-details}

To view the complete event payload:

1. In the list of event payloads on the **Source Events** dialog, locate the event payload you want to inspect.
1. Click the expand icon on the event payload row to view the payload.

You can copy the JSON payload by clicking the copy icon in the upper right corner of the payload display.

## Disabling storage of event payloads
{: #en-view-notification-payloads-disable}

When you no longer need to view event payloads, you can disable **Capture events** to stop storing event payloads.

When you disable **Capture events**, {{site.data.keyword.en_short}} stops storing new event payloads for that source. Existing stored event payloads are retained for 7 days or until the total count reaches 100, at which point older event payloads are automatically deleted.
{: note}
