---

copyright:
  years: 2020, 2022
lastupdated: "2022-11-18"

keywords: event-notifications, event notification, getting help and support

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Getting help and support
{: #en-getting-help-and-support}

{{site.data.keyword.en_full}} provides troubleshooting information to isolate and resolve problems, and also offers support. If you cannot resolve your issue with the troubleshooting guide, open an IBM support case.
{: shortdesc}

By default, account users don't have access to create, update, search, or view cases. The account owner must provide users access by assigning an {{site.data.keyword.iamlong}} (IAM) access policy. For more information, see [Assigning user access for working with support cases](/docs/get-support?topic=get-support-access#access){: external}.
{: tip}

## Creating a cloud support case
{: #en-cloud-support-case}

For more information, see [Using the Support Center](/docs/get-support?topic=get-support-using-avatar){: external}.

### Creating a support case for a UI issue
{: #ac-ui-support-case}

Collecting the following information can help a faster support case resolution for UI issues

- Provide error codes and reference IDs.
- Save the full URL of the console when the problem occurred, for example: `https://cloud.ibm.com/event-notifications/provision/ac`
- Include the steps to reproduce the issue, along with your inputs and expected outputs.
- Note the approximate time that the error occurred.
- Provide the code version and error details:
   1. Right-click on the console page and select the `Inspect` or `Inspect Element` option.
   1. Scroll to the end of the output and copy any errors or stack traces.
- Provide the network response:
   1. While you inspect the page, click the `Network` tab.
   1. Refresh the page and reproduce the problem.
   1. Starting at the end of the list, click each request and view the `Preview` tab. If the request has an "errors" node, expand that node to show the full error.
   1. Click the `Response` tab and include the full response string and the URL that generated the response.

### Creating a support case for non-UI issues
{: #en-non-ui-support-case}

Collect the following information to get a faster support case resolution for non-UI issues:

- guid
- sourceName
- region of the instance
- topicName (if the issue is related to a topic)
- channelName (if the issue is related to a channel)
- subscriptionName (if the issue is related to subscriptions)
- notification_id (if the issue is related to sending notification)
- Error message received
- Status of notification shown in LogDNA (in the case of notification sent but not received)
