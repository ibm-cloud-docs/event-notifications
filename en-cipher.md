---

copyright:
  years: 2022
lastupdated: "2022-11-10"

keywords: event-notifications, event notifications, about event notifications, securing your data, tls cipher

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# TLS cipher support
{: #en-cipher-support}

{{site.data.keyword.en_short}} API endpoints support the following TLS versions. Additionally, {{site.data.keyword.en_short}} API end points allows only the following cipher suites:
{: shortdesc}

## TLS 1.2 cipher suites
{: #en-tls12-cipher-suites}

- `ECDHE-ECDSA-AES256-GCM-SHA384`
- `ECDHE-ECDSA-CHACHA20-POLY1305-OLD`
- `ECDHE-ECDSA-CHACHA20-POLY1305`

## TLS 1.3 cipher suites
{: #en-tls13-cipher-suites}

- `TLS_AES_128_GCM_SHA256`
- `TLS_CHACHA20_POLY1305_SHA256`
- `TLS_AES_256_GCM_SHA384`
