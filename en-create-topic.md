---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-07"

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
   - **Source**: select a source from the list.

    Step 1 created a topic, step 2 provisions optional custom rules for the topic.
    {: note}

1. Add the following rules to your topic:

   - **Event type**: select event type from the list.
   - **Event subtype**: select event sub type from the event sub type list.
   - **Severity**: select severity from the severity list.
   - **Advanced conditions**: create your own custom conditions, which must follow [JSONpath specifications](https://goessner.net/articles/JsonPath/). The correctly written rule will extract the appropriate data from the incoming request payload. {{site.data.keyword.en_short}} supports conditional operators >=,<=,==,>,<,!= and logical operators ||,&& for JSONPath evaluation. You can validate your JSONPath [here](https://jsonpath.com/).

      Example:

      ```JSON
               {
      "data": {
         "details": [
            {
               "id": 1,
               "name": "Bob",
               "gender": "male",
               "age": 30
            },
            {
               "id": 2,
               "name": "Alice",
               "gender": "female",
               "age": 25
            },
            {
               "id": 3,
               "name": "Charlie",
               "gender": "male",
               "age": 35
            }
         ],
         "location": "London",
         "company": "IBM"
      }
      }
      ```

      Based on the previous JSON input, the following valid JSONPaths can be constructed:

      ```bash
      1. $.data.details[1].age>=25
         Output: True

      2. $.data.details[0].name=="Bob"
         Output: True

      3. $.data.details[2].name!="unknown"
         Output: True

      4. $.data.details[0].name=="Bob" || $.data.location=="New york"
         Output: True
      5. $.data.details[1].age>20 && $.data.company=="IBM"
         Output: True

      6. $.data.details[0].age<=30  || $.data.details[1].id>=3
         Output: True

      7. $.data.details[2].id<4
         Output: True

      8. $.data.location=="London"
         Output: True
      ```
      {: codeblock}




1. Click **Add a condition**.

    If you do not select any rules, a default rule is added, which means all notifications route to the topic by default.
    {: note}

1. Click **Create** in the topic wizard.
