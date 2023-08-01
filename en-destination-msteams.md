---

copyright:
  years: 2022
lastupdated: "2022-10-26"

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

To post a Microsoft Teams notification, you need to create an incoming webhook URL. To create the incoming webhook URL, follow the steps mentioned [here](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook){: external}.

## Configuring a Microsoft Teams destination
{: #en-msteams-configure}

You can configure a Microsoft Teams destination in the `Destinations` tab. As part of the configuration, enter the Microsoft Teams Incoming Webhook URL.

## Configuring an Microsoft Teams subscription
{: #en-msteams-configure-sub}

Create a subscription to associate the Microsoft Teams destination to a topic.

## How do Microsoft Teams notification from {{site.data.keyword.en_short}} looks
{: #en-how-do-msteams-notification-from-en-looks}

Event notification generates Microsoft Teams notifications from incoming payload. The template event notification use to send to Microsoft Teams looks like following -

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

Here -

*ibmendefaultshort* is the default short payload provided in the incoming payload.
*ibmendefaultlong* is tbe default long payload provided in the incoming payload.
*data* is the data JSON provided in the incoming payload and will be formated as json in the Microsoft Teams notification.

## Microsoft Teams retry policy
{: #en-msteams-retry}

When publishing an Microsoft Teams notification, issues such as network errors and application glitches can cause the requests to fail. A retry is used to provide resiliency to external requests. Attempt to retry the requests in such situations by using the following values:

- Limit = 60 seconds: total time that the service retries.
- Step = 5 seconds: after each failure, the service waits 5 seconds before retrying. This delay prevents bombarding of the external services (webhook).

In addition, the following timeout conditions cause the Microsoft Teams call to fail:

- A connection timeout of 10 seconds
- A response timeout of 60 seconds

If a call to the Microsoft Teams webhook URL fails even after retry attempts, the notification is lost.
{: note}
