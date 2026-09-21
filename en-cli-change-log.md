---

copyright:
  years: 2024, 2026
lastupdated: "2026-09-21"

keywords: event-notifications, event notifications cli, en cli reference

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}


# {{site.data.keyword.en_short}} CLI change log
{: #cli-change-log}

In this change log, you can learn about the latest changes, improvements, and updates for the [{{site.data.keyword.en_short}} CLI plug-in](/docs/event-notifications?topic=event-notifications-event-notifications-cli) (`ibmcloud event-notifications`). The change log lists changes that have been made, ordered by the date they were released.
{: shortdesc}

To learn about general updates and improvements to the {{site.data.keyword.en_short}} service, see the [Release notes](/docs/event-notifications?topic=event-notifications-release-notes).


## Version 1.21.3
{: #1.21.3}

Version 1.21.3 was released on 6 August 2026. This release includes the following updates:
- CLI plug-in vulnerability fix.
- Usability and cosmetic improvements.

## Version 1.21.2
{: #1.21.2}

Version 1.21.2 was released on 29 June 2026. This release includes the following updates:
- Bug fix for SMTP metrics to support the SMTP Config ID flag.
- Destination type is now marked as optional for SMTP metrics.

## Version 1.21.1
{: #1.21.1}

Version 1.21.1 was released on 25 May 2026. This release includes the following updates:
- Deprecated the `init` and `show` commands.
- Added a command to list {{site.data.keyword.en_short}} instances.
- Fixed an issue where the {{site.data.keyword.en_short}} endpoint was not automatically set based on the target region.

## Version 1.21.0
{: #1.21.0}

Version 1.21.0 was released on 7 April 2026. This release includes the following updates:
- Added support for viewing sandbox email destinations.
- Added support for email attachments.
- Added source options support for payload debugging.

## Version 1.20.2
{: #1.20.2}

Version 1.20.2 was released on 18 February 2026. This release includes the following updates:
- CLI plug-in vulnerability fix patch update.

## Version 1.20.1
{: #1.20.1}

Version 1.20.1 was released on 19 January 2026. This release includes the following updates:
- Fixed private endpoint support metadata.
- Fixed an {{site.data.keyword.en_short}} plug-in installation issue in `private.cloud.ibm.com`.

## Version 1.20.0
{: #1.20.0}

Version 1.20.0 was released on 15 December 2025. This release includes the following updates:
- Added support for bounce metrics.

## Version 1.19.0
{: #1.19.0}

Version 1.19.0 was released on 30 October 2025. This release includes the following updates:
- Added support for cloning SMTP user credentials.

## Version 1.18.0
{: #1.18.0}

Version 1.18.0 was released on 25 September 2025. This release includes the following updates:
- Added support for App Configuration destination, subscription, and templates.

## Version 1.17.0
{: #1.17.0}

Version 1.17.0 was released on 4 September 2025. This release includes the following updates:
- Added support for the webhook destination test `notifications-status` command.

## Version 1.16.0
{: #1.16.0}

Version 1.16.0 was released on 1 August 2025. This release includes the following updates:
- Added support for Code Engine destinations.
- Added support for pre-defined templates.

## Version 1.15.0
{: #1.15.0}

Version 1.15.0 was released on 27 June 2025. This release includes the following updates:
- Added support for Markdown content in notifications.

## Version 1.14.0
{: #1.14.0}

Version 1.14.0 was released on 28 April 2025. This release includes the following updates:
- The `api_key` parameter for PagerDuty destinations is now optional.

## Version 1.13.0
{: #1.13.0}

Version 1.13.0 was released on 6 March 2025. This release includes the following updates:
- Added support for {{site.data.keyword.messagehub}} destinations, subscriptions, and templates.

## Version 1.12.0
{: #1.12.0}

Version 1.12.0 was released on 27 February 2025. This release includes the following updates:
- Added support for PagerDuty templates.

## Version 1.11.0
{: #1.11.0}

Version 1.11.0 was released on 7 January 2025. This release includes the following updates:
- Added support for the Periodic Timer source.

## Version 1.10.0
{: #1.10.0}

Version 1.10.0 was released on 4 November 2024. This release includes the following updates:
- Removed support for Cloud Functions destinations.

## Version 1.9.0
{: #1.9.0}

[Deprecated]{: tag-deprecated}

Version 1.9.0 was released on 11 October 2024. This release includes the following updates:
- Added support for webhook templates.

## Version 1.8.0
{: #1.8.0}

[Deprecated]{: tag-deprecated}

Version 1.8.0 was released on 9 September 2024. This release includes the following updates:
- Added support for Slack DM destinations.

## Version 1.7.0
{: #1.7.0}

[Deprecated]{: tag-deprecated}

Version 1.7.0 was released on 9 August 2024. This release includes the following updates:
- Added support for metrics.
- Removed support for SMTP allowed IPs from SMTP configuration.

## Version 1.6.0
{: #1.6.0}

[Deprecated]{: tag-deprecated}

Version 1.6.0 was released on 1 August 2024. This release includes the following updates:
- Cloud Functions destinations deprecated.
- Added support for MMS notifications.

## Version 1.5.0
{: #1.5.0}

[Deprecated]{: tag-deprecated}

Version 1.5.0 was released on 10 May 2024. This release includes the following updates:
- Added support for SMTP configuration.
- Added support for Slack templates.
