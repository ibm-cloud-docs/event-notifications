---

copyright:
  years: 2020, 2022
lastupdated: "2022-02-09"

keywords: event-notification, event notification, faqs, Frequently Asked Questions, question, billing, service

subcollection: event-notification

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:faq: data-hd-content-type='faq'}

# Operations FAQs for {{site.data.keyword.en_short}}
{: #en-faqs-operations}

FAQs for {{site.data.keyword.en_short}} provide answers to common operations issues.
{: shortdesc}

## Why are messages reported as delivered but not received by the user?
{: #faq-en-message}
{: faq}

Sometimes messages are reported as delivered but are not received by the user for the following reasons:

- They are rejected by the telecom operator. If the same message is repeated over a span of time, messages are classified as SPAM message by the operator.

A resolution is to add any TransactionID or ReferenceID to the message body. These IDs classify the SMS as transactional, and is not blocked by the operator.

- The user opts out. If the user opts out from messaging by sending opt-out text like `Opt Out`, `Stop` or `Exit`, then messages do not reach that user and the status report states that. The user can send an `Opt in` message to the same source to restart receiving messages.


