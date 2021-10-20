---

copyright:
  years: 2020, 2021
lastupdated: "2021-10-20"

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

FAQs for {{site.data.keyword.en_short}} provides answers to common operations issues.
{: shortdesc}

## Why are messages reported as delivered but not received by the end-user
{: #faq-en-message}
{: faq}
Sometimes messages will be reported as delivered but are not received by the end user because:

- They have been rejected by the telecom operator. If the same message is repeated over a span of time, messages will be classified as SPAM message by the operator.
If you face this, please consider adding any TransactionID/ReferenceID to the message body. This classifies the SMS as transactional, and is not blocked by the operator.
-  The user opted out. If user has opted out from messaging by sending out text like `Opt Out/Stop/Exit`, messages will not reach that user and the status report will state accordingly. User can send an `Opt in` message to the same source, to re-start receiving messages.

