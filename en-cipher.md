---

copyright:
  years: 2022, 2026
lastupdated: "2026-09-02"

keywords: event-notifications, event notifications, about event notifications, securing your data, tls cipher

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Understanding support for TLS versions and cipher suites
{: #en-cipher-support}

## Which versions of TLS are supported by Event Notifications?
{: #en-tls-versions}

{{site.data.keyword.en_short}} API endpoints support the following TLS versions:
- `TLS 1.3`
- `TLS 1.2`

## Which cipher suites are allowed by Event Notifications?
{: #en-cipher-allowed}

{{site.data.keyword.en_short}} API end points allows only the following cipher suites:
{: shortdesc}

- `ECDHE-ECDSA-AES256-GCM-SHA384`
- `ECDHE-RSA-AES256-GCM-SHA384`
- `ECDHE-ECDSA-AES128-GCM-SHA256`
- `ECDHE-RSA-AES128-GCM-SHA256`
