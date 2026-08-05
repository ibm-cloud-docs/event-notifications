---

copyright:
  years: 2022, 2023
lastupdated: "2023-10-10"

keywords: event-notifications, event notifications, about event notifications, destinations, ms teams, Microsoft Teams

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Microsoft Teams
{: #en-destinations-msteams}

Microsoft&trade; Teams is an enterprise collaboration and communication platform. When you select Microsoft Teams as a service destination, any subscribed notification about an event can be sent as a message to a Microsoft Teams channel.
{: shortdesc}

## Create an incoming webhook URL
{: #en-create-an-incoming-webhook-url}

To post a Microsoft Teams notification, you need to create an incoming webhook URL. To create the incoming webhook URL, follow the steps in [Add an incoming webhook](https://learn.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook){: external}.

## Configuring a Microsoft Teams destination
{: #en-msteams-configure}

You can configure a Microsoft Teams destination in the **Destinations** tab. As part of the configuration, enter the Microsoft Teams Incoming Webhook URL.

## Create an {{site.data.keyword.en_short}} topic
{: #en-msteams-create-topic}

Click **Topics** in the {{site.data.keyword.en_short}} instance and click **Create**. Enter the topic and filter details in the **Topic details** and **Event filters** steps, then click **Create topic**.

## Configuring a Microsoft Teams subscription
{: #en-msteams-configure-sub}

Proceed to the **Subscriptions** step. Click **Create**, enter the subscription details in the **Create subscription** dialog, and click **Create subscription** to associate the Microsoft Teams destination to this topic.

## How do Microsoft Teams notification from {{site.data.keyword.en_short}} looks
{: #en-how-do-msteams-notification-from-en-looks}

{{site.data.keyword.en_short}} generates Microsoft Teams notifications from the incoming payload. The template that {{site.data.keyword.en_short}} uses to send to Microsoft Teams looks like the following example:

```sh
{
   "type": "message",
   "attachments": [
      {
         "contentType": "application/vnd.microsoft.card.adaptive",
         "content": {
            "type": "AdaptiveCard",
            "body": [
               {
                  "items": [
                     {
                        "size": "large",
                        "text": "{{event.ibmendefaultshort}}",
                        "type": "TextBlock"
                     }
                  ],
                  "type": "Container"
               },
               {
                  "text": "{{event.ibmendefaultlong}}",
                  "type": "TextBlock",
                  "weight": "Bolder",
                  "wrap": true
               },
               {
                  "actions": [
                     {
                        "targetElements": [
                           "stacktrace"
                        ],
                        "title": "Show Data",
                        "type": "Action.ToggleVisibility"
                     }
                  ],
                  "type": "ActionSet"
               },
               {
                  "id": "stacktrace",
                  "isVisible": false,
                  "items": [
                     {
                        "fontType": "monospace",
                        "isSubtle": true,
                        "size": "Small",
                        "text": "{{event.data}}",
                        "type": "TextBlock",
                        "weight": "Bolder",
                        "wrap": true
                     }
                  ],
                  "type": "Container"
               }
            ],
            "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
            "version": "1.4"
         }
      }
   ]
}
```

Where:

- `ibmendefaultshort` is the default short payload provided in the incoming payload.
- `ibmendefaultlong` is the default long payload provided in the incoming payload.
- `data` is the data JSON provided in the incoming payload and is formatted as JSON in the Microsoft Teams notification.

## Testing a Microsoft&trade; Teams destination configuration
{: #en-msteams-test-destination}

You can test a Microsoft&trade; Teams destination in the options menu next to the destination. You can test whether the provided configuration is correct with a single click.

For more information on testing a destination, see [Testing Destinations](/docs/event-notifications?topic=event-notifications-en-test-destination).


## Microsoft Teams retry policy
{: #en-msteams-retry}

When publishing a Microsoft Teams notification, issues such as network errors and application glitches can cause the requests to fail. {{site.data.keyword.en_short}} automatically retries failed requests to provide resiliency.

For detailed information about retry behavior, including retry attempts, delays, and timeout values, see [Retry policy for destinations](/docs/event-notifications?topic=event-notifications-en-destination#en-destination-retry-policy).
