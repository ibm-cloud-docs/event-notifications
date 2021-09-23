---

copyright:
  years:  2017, 2021
lastupdated: "2021-08-12"

keywords: event notifications, event notification, notifications, service access, manage, user roles

subcollection: mobilepush

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:reactnative: .ph data-hd-programlang='React Native'}
{:csharp: .ph data-hd-programlang='csharp'}
{:ios: .ph data-hd-programlang='iOS'}
{:android: .ph data-hd-programlang='Android'}
{:cordova: .ph data-hd-programlang='Cordova'}
{:xml: .ph data-hd-programlang='xml'}

# Managing service access
{: #service-access-management}

With {{site.data.keyword.en_short}} and {{site.data.keyword.iamlong}}, IAM account owners can manage user access in your account.
{: shortdesc}

As an account owner, you can set policies within your account to create different levels of access for different users. For example, certain users can have **Read only** access to one instance, but **Write** access to another. You can decide who is allowed to create, update, and delete instances of {{site.data.keyword.en_short}}.

{{site.data.keyword.en_short}} service has adopted IAM and App secret is not generated for new instances. You must use the [API keys instead](https://cloud.ibm.com/docs/account?topic=account-manapikey).
{: note}

## User roles
{: #roles}

The scope of an access policy is based on an user's assigned role.

Policies enable access to be granted at different levels. Some of the options include:

- Access across all instances of the service in your account
- Access to an individual service instances in your account
- Access to a specific resource within an instance
- Access to all IAM-enabled services in your account

Platform management roles enable users to perform tasks on service resources at the platform level. For example, roles can be assigned to determine who can create or delete IDs, create instances, and bind instances to apps. The following table classifies actions as they are assigned to platform management roles.

| Platform role | Permissions | Example actions |
|---------------|---------------|---------------|
| Viewer | View {{site.data.keyword.en_short}} instances. |You can see a Cloud Directory user's data or the identity provider configuration. |
| Editor | View and bind {{site.data.keyword.en_short}} instances. | You can bind applications to an instance of {{site.data.keyword.en_short}}. |
| Operator | Create, delete, edit, suspend, resume, view, or bind {{site.data.keyword.en_short}} instances. | You can create or delete an {{site.data.keyword.en_short}} instance from the catalog. |
| Administrator | All management actions for all services in the account. | You can perform all operator actions and the ability to assign policies to other users. |
{: caption="Table 1. Platform management roles and permissions" caption-side="top"}

The following table details actions that are mapped to service access roles. Service access roles enable users to access {{site.data.keyword.en_short}} and also call the {{site.data.keyword.en_short}} API.

| Service role  | Permissions | Example actions |
|---------------|---------------|---------------|
| Reader | View {{site.data.keyword.en_short}} instance data | View details of the service instance such as sources, rules, topics, and channels |
| Writer | View and edit an {{site.data.keyword.en_short}} instance | <ul><li>Perform all Reader actions</li> <li>Edit the service instance data, such as sources, rules, topics, and channels</li></ul> |
| Channel Editor| View, create, and delete {{site.data.keyword.en_short}} subscriptions| View, create, update, and delete {{site.data.keyword.en_short}} subscriptions |
| Manager | View, edit, and delete data in an {{site.data.keyword.en_short}} instance |<ul><li>Perform all Writer actions</li> <li> Delete service instance data such as sources, rules, topics, channels</li></ul>|
| Service Configuration Reader| Read services configuration for Governance management | View services configurations |
| Event Source Manager | Source integration with{{site.data.keyword.en_short}} using service to service authorization | <ul><li>Perform service to service registration, of source</li><li>View, edit, and delete sources and events</li><li>Send notifications</li></ul> |
| {{site.data.keyword.en_short}} Publisher | Create notification and view notifications count | Send notifications and view notifications count |
{: caption="Table 2. Actions mapping to service access roles" caption-side="top"}

For more information about assigning user roles in the UI, see [Managing IAM access](/docs/account?topic=account-assign-access-resources).

## {{site.data.keyword.en_short}} access policies
{: #access}

Every user who accesses the {{site.data.keyword.en_short}} service in your account must be assigned an access policy with an IAM user role defined. That policy determines what actions the user can perform within the context of the service or instance you select.
{: shortdesc}

The actions are customized and defined by the {{site.data.keyword.Bluemix_notm}} service as operations that are permitted in the service. The actions are then mapped to IAM user roles. Some of the actions taken you can track with the {{site.data.keyword.cloudaccesstrailshort}} service. In the following table, the actions and required permissions for {{site.data.keyword.en_short}} are mapped.

| Service action | Display name| Role| Description|
|----------------|-------------|------------------|-----------------|
| `event-notifications.sources.create` | `POST /event-notifications/v1/instances/{instanceID}/sources`| Manager, Administrator, Event-Source-Manager |Create Source for Event Notifications instance  |
| `event-notifications.sources.read` | `GET /event-notifications/v1/instances/{instanceID}/sources/{sourceID}`| Manager, Administrator, Event-Source-Manager, Channel-Editor | Get Source for Event Notifications instance  |
| `event-notifications.sources.update` | `PUT /event-notifications/v1/instances/{instanceID}/sources/{sourceID}`| Manager, Administrator, Event-Source-Manager | Update Source for Event Notifications instance |
| `event-notifications.sources.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/sources/{sourceID}`| Manager, Administrator, Event-Source-Manager | Delete Source from Event Notifications instance |
| `event-notifications.sources.list` | `GET /event-notifications/v1/instances/{instanceID}/sources`| Manager, Administrator, Event-Source-Manager, Channel Editor | Get all sources of Event Notifications instance  |
| `event-notifications.topics.create` | `POST /event-notifications/v1/instances/{instanceID}/topics`| Manager, Writer, Administrator | Create Topic for Event Notifications instance |
| `event-notifications.topics.read` | `GET /event-notifications/v1/instances/{instanceID}/topics/{topicID}`| Manager, Reader, Writer, Administrator, Channel-Editor |Get Topic for Event Notifications instance |
| `event-notifications.topics.update`| `PUT /event-notifications/v1/instances/{instanceID}/topic/{topicID}`| Manager, Writer, Administrator |Update Topic for Event Notifications instance  |
| `event-notifications.topics.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/topic/{topicID}`| Manager, Administrator | Delete Topic from Event Notifications instance |
| `event-notifications.topics.list` | `GET /event-notifications/v1/instances/{instanceID}/topics`| Manager, Reader, Writer, Administrator, Channel-Editor | Get All topics for Event Notifications instance |
| `event-notifications.rules.create` | `POST /event-notifications/v1/instances/{instanceID}/rules`| Manager, Writer, Administrator | Create Rule for Event Notifications instance  |
| `event-notifications.rules.read` | `GET /event-notifications/v1/instances/{instanceID}/rules/{ruleID}`| Manager, Reader, Writer, Administrator, Channel-Editor | Get Rule for Event Notifications instance |
| `event-notifications.rules.update` | `PUT /event-notifications/v1/instances/{instanceID}/rules/{ruleID}`| Manager, Writer, Administrator | Update Rule for Event Notifications instance |
| `event-notifications.rules.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/rules/{ruleID}`| Manager, Administrator | Delete Rule from Event Notifications instance |
| `event-notifications.rules.list` | `GET /event-notifications/v1/instances/{instanceID}/rules`| Manager, Reader, Writer, Administrator, Channel-Editor |Get All Rules for Event Notifications instance  |
| `event-notifications.destinations.create` | `POST /event-notifications/v1/instances/{instanceID}/destinations`| Manager, Writer, Administrator | Create Destination for Event Notifications instance |
| `event-notifications.destinations.read` | `GET /event-notifications/v1/instances/{instanceID}/destinations/{destinationID}`| Manager, Reader, Writer, Administrator, Channel-Editor | Get Destination for Event Notifications instance |
| `event-notifications.destinations.update` | `PUT /event-notifications/v1/instances/{instanceID}/destinations/{destinationID}`| Manager, Writer, Administrator|Update Destination for Event Notifications instance  |
| `event-notifications.destinations.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/destinations/{destinationID}`| Manager, Administrator| Delete Destination from Event Notifications instance |
| `event-notifications.destinations.list` | `GET /event-notifications/v1/instances/{instanceID}/destinations`| Manager, Reader, Writer, Administrator, Channel-Editor | Get All Destinations for Event Notifications instance |
| `event-notifications.subscriptions.create` | `POST /event-notifications/v1/instances/{instanceID}/subscriptions`| Manager, Writer, Administrator, Channel-Editor | Create Subscription for Event Notifications instance |
| `event-notifications.subscriptions.read` | `GET /event-notifications/v1/instances/{instanceID}/subscriptions/{subscriptionID}`| Manager, Reader, Writer, Administrator, Channel-Editor |Get Subscription for Event Notifications instance  |
| `event-notifications.subscriptions.update` | `PUT /event-notifications/v1/instances/{instanceID}/subscriptions/{subscriptionID}`| Manager, Writer, Administrator, Channel-Editor | Update Subscription for Event Notifications instance |
| `event-notifications.subscriptions.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/subscriptions/{subscriptionID}`| Manager, Administrator, Channel-Editor| Delete Subscription from Event Notifications instance |
| `event-notifications.subscriptions.list` | `GET /event-notifications/v1/instances/{instanceID}/subscriptions`| Manager, Reader, Writer, Administrator, Channel-Editor | Get All Subscriptions for Event Notifications instance  |
| `event-notifications.notifications.post` | `POST /event-notifications/v1/instances/{{instance_id}}/notifications`| 	Manager, Writer, Administrator, Event-Source-Manager, Event-Notification-Publisher | Send Notification to Event Notifications instance  |
| `event-notifications.counts.get` | `GET /event-notifications/v1/instances/{instanceID}/counts`| Manager, Reader, Event-Source-Manager, Channel-Editor, Event-Notification-Publisher |Get All Notifications for Event Notifications instance  |
| `event-notifications.events.create` | `GET /event-notifications/v1/instances/{instanceID}/events/{eventID}?sourceID=*`| Manager, Administrator, Event-Source-Manager| Get Event for Event Notifications instance |
| `event-notifications.events.read` | `POST /event-notifications/v1/instances/{instanceID}/sources`| Manager, Administrator, Event-Source-Manager |   |
| `event-notifications.events.list` | `GET /event-notifications/v1/instances/{instanceID}/events?sourceID=*`| Manager, Administrator, Event-Source-Manager | Get All Events for Event Notifications instance  |
| `event-notifications.events.delete` | `DELETE /event-notifications/v1/instances/{instanceID}/events/{eventID}?sourceID=*`| Manager, Administrator, Event-Source-Manager | Delete Events from Event Notifications instance  |
{: caption="Table 3. Actions mapped to different roles" caption-side="top"}

## Working with API keys
{: #apikeys}

Upon creating service credentials, you might notice an `apiKey` is displayed instead of the `appSecret`.

To use any ReST APIs, you must generate the access token by using the following curl command:

### Parameters

```
  curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=G2c7oaUuOjul1RbmbjAeI7YwJSUCW_hmfif3GhLabYPE" \
  "https://iam.cloud.ibm.com/identity/token"
```
{: codeblock}

### Response

```
{
    "access_token": "eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTcwMTgzMDYwLWY3NWUtNGQ5Yy04NjY5LTA4NTNkYzc2NDQyMSIsImlkIjoiaWFtLVNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC03MDE4MzA2MC1mNzVlLTRkOWMtODY2OS0wODUzZGM3NjQ0MjEiLCJzdWIiOiJTZXJ2aWNlSWQtNzAxODMwNjAtZjc1ZS00ZDljLTg2NjktMDg1M2RjNzY0NDIxIiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6IjJmZDIwM2E1M2Q5MDI1ZDI4NTU5YjZhZDFhM2JhMTNjIn0sImlhdCI6MTUzNDc2MDIwNywiZXhwIjoxNTM0NzYzODA3LCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImltZnB1c2giLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.MSUIk3KvFKeidTa4Qf9Ydf-7_boRwPRyigRjBkF0KWT2AVxeQ7oDVOgSEvApzy1tKSoi4N-bAIDpsOkd-BYnYtZnAFJxn9IGSnHli4YXOabLnLIuXbvYJBqCeAWVZoTiqQO6H7ZY__8Nf1YlfGms-iV4FFRPVAq1bx_9BylY1t2gq6WhTWciSGhoq5CHr_bdbc3qK6NRHDzvOfqBP5hDRDo9WAVFSSqtMJNttGR1Dj92jM0o9yADWe32WoVXbxMDX7VZ-wEAbvIJIW1ZcQPPKG9rfW57XOthZSWSbE4MxrUkoHvrBiGqcJfm_yV_mZD_Ynbm4yDSW4q0HbHOB1K7mg",
    "refresh_token": "J1D6UZp3fEhxRdPCzhY4kvt7ojXIdUHjmO8x9pxGMgSZt0XpGd15F098WFKKUwp_v0pktQxdOZtcBGx3sL5THYUxU-PlkxELZ3gKX78dWf4P7lYDLDXR2x_n48fPIvRQoDD0ZJAKewO3o1IcegmNdf_InSgvu2M3Ra3FwlJPDN9mRH6-2e8pHnvq4e1rdY6pV0ufxweKc9dGqU-U7VU765BCg84kr8tkb9kpZnnPseDJ89gf5lhkZteKoNVkn-uiLUF0L-yv33tgtoDrdU5-FqaV00TUbLBoJEeTTnUD1fgIGB6SfphIImCQ0368gTU2emGBe3lzlQBnvkOXaMoBds3Nc2YL6px2LhqBWFd_ho68P4ahz1cbTn1rhqIjZMokeN88sreAKsRWhH7nVgBpfN3FS7OJBrVTx55j44vrZdH3vFJ-glLNb3FBwI6_6N_i2lVz7W-_W9xHW2CTYO7e3PYEZorQDBRZFIPImES6v7UV7YyaYG5ikktHHsOZsMzb6UYP-Kg1k2z_UTOumBkCDYxeV9GxukgSSK7Nckpysi5DJt4VgEnyxlbnfmWhtVeSzl8vjIBLJFE7oe7QDn3YyfCDP4QS4cIkTAvvpE5916pXk-rU9NLbIp6mmJw4PwY8__ao6CmCZJ4IDlr6GsDu4Ocn72yGgsNSwI-sq-dJyMuYG494CQ3MOooWsUjzhLTIHGsuHOkouMh07yR-v-D0dNrBeRmXM-JyF6BmtAS-rcivztjjbfJV3NNZcjC9RJvgf7OW5kp7dSRXMlohHu4tAxgVy16ON3Hm1TFnZt5jsaYLcwxuC6s2Qv7N4QEf2VIWLI5UWjbuj1IFi_Jq4RAkCCNgdvKo6RWaMbvZ8XL-3VKaDiJ60oy7wjGwZmWAWIFBZ1S3Br5waaT51T6mFV_s0VTu-68HhFpdIb1WFCXrU8DEcsamkUU7XRiTtBEIFNWQWnDDGMtn_vFGJCFygOd8CMsj",
    "token_type": "Bearer",
    "expires_in": 3600,
    "expiration": 1534763807,
    "scope": "ibm openid"
}
```

Upon generating the access token by using the preceding curl command, you might now operate the Rest APIs by passing the `Bearer <value of access_token>` in the Authorization header

For example,

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJraWQiOiIyMDE3MTAzMC0wMDowMDowMCIsImFsZyI6IlJTMjU2In0.eyJpYW1faWQiOiJpYW0tU2VydmljZUlkLTYxZDdhNzJkLWM3YzAtNGNlZS05Zjg0LWI2ZDc1NzgzMWM2NSIsImlkIjoiaWFtLVNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJyZWFsbWlkIjoiaWFtIiwiaWRlbnRpZmllciI6IlNlcnZpY2VJZC02MWQ3YTcyZC1jN2MwLTRjZWUtOWY4NC1iNmQ3NTc4MzFjNjUiLCJzdWIiOiJTZXJ2aWNlSWQtNjFkN2E3MmQtYzdjMC00Y2VlLTlmODQtYjZkNzU3ODMxYzY1Iiwic3ViX3R5cGUiOiJTZXJ2aWNlSWQiLCJhY2NvdW50Ijp7ImJzcyI6Ijk3MDg5MjkzNTg0OTg1NzBhYjYxMjUwNDk3ZjBmMDI2In0sImlhdCI6MTUzNTM2NTQ5MywiZXhwIjoxNTM1MzY5MDkzLCJpc3MiOiJodHRwczovL2lhbS5ibHVlbWl4Lm5ldC9pZGVudGl0eSIsImdyYW50X3R5cGUiOiJ1cm46aWJtOnBhcmFtczpvYXV0aDpncmFudC10eXBlOmFwaWtleSIsInNjb3BlIjoiaWJtIG9wZW5pZCIsImNsaWVudF9pZCI6ImRlZmF1bHQiLCJhY3IiOjEsImFtciI6WyJwd2QiXX0.ASKxD9Wrz5--OYVkPIsufKK9RNKKhJKuvRldm5mnGNv6PSH7sPBB6NiRG-SSGzEC0ZIei1WqtRE-0TRHwzSnIjXPb3yffBcvNtXuG9wT8GT8zsvxQ7bJk0ovge_0Xrrcym4cCTq2jO6ROWzOZ275wkH0h4fIzukbPv7YpT2Z-DdxIwHY_uALxqcCY83xODtMIs21PO6YwQ3KX4YfNEpKUminJpo45T8po4k049PODQKEK65YrqHYK1_voCJUu9xt9uVoGd-r962fhnbuxeEAe6di9KGVfOGfEdZFHgexoG__wXHa0Rmv9dCl-nNI4WMZfCTj8jgfEOhuZstpW7pW2g' --header 'Accept-Language: en-US' -d '{ \
   "message": { \
     "alert": "Notification alert message" \
   } \
 }' 'https://us-east.imfpush.cloud.ibm.com/imfpush/v1/apps/4809d407-85ff-4d11-ae4b-0fcdf8a833f1/messages'
```

For more information about IAM, see [IAM Access](https://cloud.ibm.com/docs/account?topic=account-userroles).
