---

copyright:
  years: 2020, 2021
lastupdated: "2021-07-26"

keywords: event-notifications, event notifications, about event notifications

subcollection: event-notifications

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}


# Event notifications concepts
{: #en-overview}

![Overview](images/en-overview.png "Overview diagram"){: caption="Figure 1. Event notifications overview" caption-side="bottom"}

## What notification problems are being solved for whom?
{: #en-description}

### Challenges for Cloud Developers
{: #en-challenges-clouddev}
Event-driven programming on IBM cloud
        (a) IBM Cloud has no native FS- and FedRamp-compliant service that specializes in discrete event routing.
        (b) Few IBM Cloud services emit events externally for developers to react.
Connect to a variety of channels.
Coordinate events across channels.
Event logic distributed over multiple components making it difficult to troubleshoot and maintain.

### Challenges for App Operators
{: #en-challenges-appopp}
Route app infrastructure events to human (A2P) channels.
Set up event-based automation and logging in a consistent way.
Route events based on context (e.g. origin, status, label, etc).

### Challenges for Internal IBM Cloud service teams
{: #en-challenges-internal}
Currently must implement event logic inside individual services which results in duplicate and disparate effort.
Must implement bespoke internal services for communicating with IBM Cloud customers. 
Lack of central event routing leaves teams to build numerous service-to-service integrations
