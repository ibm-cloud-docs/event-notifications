---

copyright:
  years: 2015, 2024
lastupdated: "2024-11-28"

keywords: event notifications, event-notifications, tutorials

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# Creating an {{site.data.keyword.en_short}} topic
{: #en-create-en-topic}

You can send notifications or alerts to multiple destination types, for example, email, SMS, and others that are subscribed to a particular topic. Configure topics as needed and {{site.data.keyword.en_short}} handles the routing and delivering of alerts reliably to the correct destinations.
{: shortdesc}

## Creating a topic
{: #en-create-topic}

1. Select **Topics** in the {{site.data.keyword.en_short}} console.

1. Click **Create**, and enter the following topic details:
   - **Name**: enter a name for the topic.
   - **Description**: add an optional description for the topic.
   - **Source**: select a source from the list. Sources are of 3 types:

      - {{site.data.keyword.IBM_notm}} Source
      - API Source
      - Periodic Timer Source

   
1. If your chosen source is an **{{site.data.keyword.IBM_notm}} Source**: 

   Add the following rules to your topic:

      - **Event type**: select event type from the list.
      - **Event subtype**: select event sub type from the event sub type list.
      - **Severity**: select severity from the severity list.
      - **Advanced conditions**: create your own custom conditions, which must follow [JSONpath specifications](https://goessner.net/articles/JsonPath/). The correctly written rule extracts the appropriate data from the incoming request payload. {{site.data.keyword.en_short}} supports conditional operators `>=, <=, ==, >, <, !=, =~` and logical operators `||, &&` for JSONPath evaluation. You can validate your JSONPath [here](https://jsonpath.com/). If you want to add advanced conditions for event type, subtype, and severity, see the following [example](/docs/event-notifications?topic=event-notifications-en-create-en-topic#create-topic-example). Similarly, you can add advanced conditions for the other available [payload fields](https://{DomainName}/apidocs/event-notifications#send-notifications-request).

      The "=~" operator is a powerful tool that helps you search for patterns in strings by using regular expressions.
      {: note}

### Example:
{: #create-topic-example}

   ```JSON
      {
      "data": {
         "details": [
            {
               "id": 1,
               "name": "Bob",
               "gender": "male",
               "age": 30,
               "country": "China"
            },
            {
               "id": 2,
               "name": "Alice",
               "gender": "female",
               "age": 25,
               "country": "India"
            },
            {
               "id": 3,
               "name": "Charlie",
               "gender": "male",
               "age": 35,
               "country": "USA"
            }
         ],
         "location": "London",
         "company": "IBM",
         "region": "london",
         "event_type": "secret_about_to_expire ",
         "event_sub_type": "in_60_days ",
         "severity" : "MEDIUM"
      }
      }
   ```

   Based on the previous JSON input, the following valid JSONPaths can be constructed:

   ```bash
         1. $.data.event_sub_type == "in_60_days"
            Output: True

         2. $.data.event_type == "secret_about_to_expire"
            Output: True

         3. $.data.severity == "MEDIUM"
            Output: True

         4. $.data.details[1].age >= 25
            Output: True

         5. $.data.details[0].name == "Bob"
            Output: True

         6. $.data.details[2].name != "unknown"
            Output: True

         7. $.data.details[0].name == "Bob" || $.data.location == "New york"
            Output: True
            
         8. $.data.details[1].age > 20 && $.data.company == "IBM"
            Output: True

         9. $.data.details[0].age <= 30  || $.data.details[1].id >= 3
            Output: True

         10. $.data.details[2].id < 4
            Output: True

         11. $.data.location == "London"
            Output: True
         
         12. $.data.region =~ "dallas|london|sydney"
            Output: True 

         13. $.data.details[?(@.country == "India")].name == "Alice"
            Output: True 
   ```
      

If your chosen source is an **API source**, then you can add the "Advanced Conditions" rule to your topic.
{: note}

If your chosen source is a **Periodic Timer Source**, then refer [here](/docs/event-notifications?topic=event-notifications-en-cron-periodic-timer) for steps to set rules for your topic. 

Step 2 created a topic, step 3 provisioned optional custom rules for the topic.
{: note}

1. Click **Add a condition**.

    If you do not select any rules, a default rule is added, which means all notifications route to the topic by default.
    {: note}

1. Click **Create** in the topic wizard.
