---

copyright:
  years: 2025
lastupdated: "2025-11-03"

keywords: event-notifications, event notifications, about event notifications, topics, advanced filtering

subcollection: event-notifications

---

# Advanced Filtering using JSONPath
{: #en-advanced-filtering}

While creating topics you can add your own custom conditions, which must follow the [JSONpath specifications](https://goessner.net/articles/JsonPath/). JSONPath is a Java DSL for reading JSON documents. The correctly written rule extracts the appropriate data from the incoming request payload. {{site.data.keyword.en_short}} supports conditional operators `>=, <=, ==, >, <, !=, =~` and logical operators `||, &&` for JSONPath evaluation. You can validate your JSONPath [JSONPath Validator](https://jsonpath.com/). If you want to add advanced conditions for event type, subtype, and severity, see the following [example](/docs/event-notifications?topic=event-notifications-en-advanced-filtering&interface=ui#en-advanced-filtering-examples). Similarly, you can add advanced conditions for the other available [payload fields](https://{DomainName}/apidocs/event-notifications#send-notifications-request).

JSONPath expressions can use the dot–notation:
```bash
$.data.details[0].name
```

We only support regular expressions compatible with the [Go regexp package](https://pkg.go.dev/regexp).This package does not support lookbehind or negative lookahead assertions (e.g., `(?<!...)`, `(?!...)` are not supported).If you need to express a negative match, use a positive regular expression and apply the `not` operator provided by us to invert the result. See [Path Examples](/docs/event-notifications?topic=event-notifications-en-advanced-filtering&interface=ui#en-advanced-filtering-examples) to find an example of the usage of the `not` operator.
{: note}


## JSONPath Operators
{: #en-operators}

JSONPath provides a variety of operators to query JSON structures. Using these operators you can search elements, filter based on conditions and perform other data extraction tasks. The following operators are supported by {{site.data.keyword.en_short}}.

| Operator | Description |
|-------|--------|
| `$` | The root object/element. This starts all path expressions. |
| `@` | The current object/element |
| `. or []` | Child operator |
| `*` | Wildcard. All objects/elements regardless their names. |
| `..` | Recursive descent. |
| `[,]` | Union operator in JSONPath allows alternate names or array indices as a set. |
| `[start:end]` | Array slice operator |
| `?()` | Applies a filter expression. |
{: caption="JSONPath Operators" caption-side="bottom"}


## Filter Operators
{: #en-filters}

Filters are logical expressions used to filter arrays. The filters listed in the following table are supported by {{site.data.keyword.en_short}}.

| Operator | Description |
|-------|--------|
| `==` | left is equal to right |
| `!=` | left is not equal to right |
| `<` | left is less than right |
| `<=` | left is less than or equal to right |
| `>` | left is greater than right |
| `>=` | left is greater than or equal to right |
| `=~` | left matches regular expression [?(@.name =~ /foo.*?/i)] |
| `&&` | combine multiple conditions in a filter where all conditions must be true for an element to be selected. |
| `\|\|`| combine multiple conditions in a filter where at least one of the specified conditions must be true for an element to be selected. |
{: caption="Filter Operators" caption-side="bottom"}

## Path Examples
{: #en-advanced-filtering-examples}

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
        "event_type": "secret_about_to_expire",
        "event_sub_type": "in_60_days",
        "severity" : "MEDIUM"
    }
}
```

Based on the previous JSON input, the following valid JSONPaths can be constructed:


| JSONPath | Result |
|------|-----|
| `$.data.details[*].name` | The names of all people |
| `$.data.details[1].age` | The age of the second person |
| `$..gender` | All genders |
| `$..details[2]` | The third person |
| `$..details[-2]` | The second to last person |
| `$..details[0,1]` | The first two people |
| `$..details[:2]` | All people from index 0 (inclusive) until index 2 (exclusive) |
| `$..details[1:2]` | All people from index 1 (inclusive) until index 2 (exclusive) |
| `$..details[-2:]` | Last two people |
| `$..details[1:]` | All people from index 1 (inclusive) to last |
| `$..details[?(@.age)]` | All people with age |
| `$.data.details[?(@.age < 30)]` | All people with age less than 30 |
| `$..details[?(@.name =~ 'Bo*')]` | All people matching regex |
| `$..*` | Everything |
| `$.data.event_sub_type == "in_60_days"`| JSONPath to check if event_sub_type is equal to "in_60_days". |
| `$.data.event_type == "secret_about_to_expire"`| JSONPath to check if event_type is equal to "secret_about_to_expire". |
| `$.data.severity == "MEDIUM"`| JSONPath to check if severity is equal to "MEDIUM". |
| `$.data.details[1].age >= 25` | JSONPath to check if the age of the second person is equal to or greater than 25. |
| `$.data.details[0].name == "Bob"` | JSONPath to check if the name of the first person is Bob. |
| `$.data.details[2].name != "unknown"` | JSONPath to check if the name of the third person is not unknown. |
| `$.data.details[0].name == "Bob" \|\| $.data.location == "New york"` | JSONPath to check if the name of the first person is Bob **OR** if the location is New York.|
| `$.data.details[1].age > 20 && $.data.company == "IBM"` | JSONPath to check if the age of the second person is greater than 20 **AND** the company given is IBM.|
| `$.data.details[0].age <= 30 \|\| $.data.details[1].id >= 3` | JSONPath to check if the age of the first person is less than or equal to 30 **OR** the id of the second person is greater than or equal to 3.|
| `$.data.details[2].id < 4` | JSONPath to check if the id of the third person is less than 4. |
| `$.data.location == "London"` | JSONPath to check if the location provided is London. |
| `$.data.region =~ "dallas\|london\|sydney"` | JSONPath to check if region provided is one among Dallas, London and Sydney. |
| `$.data.details[?(@.country == "India")].name == "Alice"`| JSONPath to check if the person from India has the name Alice. |
| `not($.data.details[?(@.name =~ 'Ali*')])` | JSONPath to check if there is any person whose name does not start with `Ali`. |
{: caption="Valid JSONPaths" caption-side="bottom"}
