---

copyright:
  years: 2023, 2026
lastupdated: "2026-10-01"

keywords: event notifications, event notification, notifications, email, custom domain, best practices

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Email best practices
{: #en-email-bestpractices}

{{site.data.keyword.en_short}} is a powerful tool for sending event-related emails to your customers. Establishing reliable email delivery involves two phases: security configuration (domain verification with SPF, DKIM, and DMARC) and building a strong sending reputation as you scale your email volume. This topic provides guidelines and recommendations to help you get the most from the service while avoiding common pitfalls.
{: shortdesc}

## Before you send
{: #en-email-before-send}

### Use a custom email domain
{: #en-email-use-custom-email}

- Using a custom email domain for sending {{site.data.keyword.en_short}} is highly recommended. This establishes trust and brand recognition, reducing the likelihood of your emails being flagged as spam.

### Authentication and verification
{: #en-email-authverification}

- Implement DomainKeys Identified Mail (DKIM), Sender Policy Framework (SPF), and Domain-based Message Authentication, Reporting, and Conformance (DMARC) to authenticate your emails. Here's what you need to know about them:

  - **DomainKeys Identified Mail (DKIM)**: DKIM is an email authentication method that adds a digital signature to your outgoing emails. This signature is generated using a private key that only you have access to. The recipient's email service provider can then verify the signature using the public key stored in your DNS records. This verification ensures that the email hasn't been tampered with in transit and that it genuinely comes from your domain. Implementing DKIM helps prevent email spoofing and phishing, which can improve email deliverability.

  - **Sender Policy Framework (SPF)**: SPF is another email authentication method that helps prevent email spoofing. SPF specifies which IP addresses or domains are authorized to send email on behalf of your domain. By setting up SPF records in your DNS, you inform receiving email servers which sources are legitimate senders for your domain. This ensures that only authorized servers can send emails claiming to be from your domain.

  - **Domain-based Message Authentication, Reporting, and Conformance (DMARC)**: DMARC is an email authentication and reporting protocol that builds upon SPF and DKIM. It allows you to set policies that define how email providers should handle emails that fail authentication checks. DMARC helps prevent domain spoofing and phishing attacks by providing clear instructions to email receivers on how to handle messages that claim to be from your domain. DMARC also offers reporting features, giving you insights into how your email domain is used and whether unauthorized sources are attempting to send emails on your behalf.

With the implementation of DMARC in addition to DKIM and SPF, your email messages are more secure, and you have better control over how emails claiming to be from your domain are treated by email service providers, enhancing your email deliverability and security.

### Shared IP addresses
{: #en-email-sharedip}

{{site.data.keyword.en_short}} uses the following shared IPs to send emails.
```
52.118.150.126
158.176.0.148
158.177.13.167
149.81.215.46
52.118.254.206
52.118.98.90
```
- **How Shared IP Address Works**:
    - In this service, a single IP address is designated for sending emails on behalf of multiple domains. This shared IP address is authenticated using SPF, which allows it to be used to send emails to all users of the {{site.data.keyword.en_short}} service.

 - **Consequences**:
    - Unfortunately, due to the shared IP address, the entire IP reputation is affected by one user's actions, due to which, another user's legitimate events may also be blocked or flagged as spam by the email service providers, despite their adherence to the best practices.
    - If the shared IP's reputation is adversely impacted, it is more difficult for all users to deliver emails effectively.

Thus, it is important to maintain a responsible and ethical approach to email communication, as the actions of one user on a shared IP address can impact the deliverability of all users. Regular monitoring, education, and adherence to email best practices are crucial to prevent such issues.

## As you scale
{: #en-email-as-you-scale}

IP and domain reputation indicate how receiving email providers perceive the trustworthiness of your email sending infrastructure and domain. Maintaining a good reputation is important for reliable email delivery and helps reduce the likelihood of messages being throttled, rejected, or delivered to spam folders.

### Sending volume and warm-up
{: #en-email-warmup}

Maintain a consistent and predictable sending volume in the initial phases. Avoid sudden, unexplained spikes in traffic, particularly when warming up a new IP or domain. Gradually increase volume when scaling your email traffic to allow receiving providers to establish a reputation for the IP and the sending domain.

During warm-up:

- Start with low volume and recipients who are known to be active and engaged.
- Increase volume gradually rather than making large jumps.
- Maintain a consistent sending pattern.

#### Suggested sending volumes during initial days after onboarding to {{site.data.keyword.en_short}}
{: #en-email-warmup-table}

| Day | Suggested volume |
|-----|-----------------|
| 1 | 50 |
| 2 | 100 |
| 3 | 500 |
| 4 | 1,000 |
| 5 | 2,000 |
| 6 | 4,000 |
| 7 | 8,000 |
| 8 | 16,000 |
| 9 | 25,000 |
| 10 | 35,000 |
| 11 | 50,000 |
| 12 | 75,000 |
| 13 | 100,000 |
| 14 | 150,000 |
| 15 | 200,000 |
| 16 | 275,000 |
| 17 | 375,000 |
| 18 | 500,000 |
| 19 | 650,000 |
| 20 | 825,000 |
| 21 | 1,000,000 |

### Bounce rates
{: #en-email-bouncerates}

Maintain a low bounce rate (ideally under 2%) by sending only to valid and active recipients. Remove or suppress email addresses that generate permanent (hard) bounces, handle transient (soft) bounces appropriately, and avoid repeatedly sending to invalid or non-existent recipient addresses.

### Spam complaints
{: #en-email-spamcomplaints}

Recipients marking your email as spam will significantly lower your IP and domain reputation with mailbox providers. Keep spam complaint rates strictly below 0.1%.

To minimize spam complaints:
- Send relevant and expected emails only to recipients who have explicitly consented to receive them.
- Ensure the sender identity is clear and consistent in the email header and subject line.
- Promptly honor all unsubscribe and opt-out requests.
- If you are using {{site.data.keyword.en_short}} managed opt-in ([Managing subscriptions](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out)), monitor your opt-out rates. If you manage subscriptions independently, ensure an easily accessible and functional unsubscribe link is included in every non-transactional email.

### Recipient engagement
{: #en-email-engagement}

Positive engagement from recipients such as opening emails, clicking links, moving messages out of spam, or adding sender addresses to address books signals to mailbox providers that your content is legitimate and wanted. Conversely, persistent lack of engagement harms sender reputation.

### Monitor and prevent spam
{: #en-email-preventspam}

- The origin IP addresses could be added to a blocklist, resulting in the emails being marked as spam, if the email service is not used responsibly:
  - Educate team on the importance of email etiquette.
  - Implement rate limits on email sends to avoid sending a high volume of emails in a short period.
  - Regularly monitor email sending activity for any signs of abuse.

### Opt-in subscription
{: #en-email-Opt-in}

- Use a double opt-in process for subscribers, ensuring that they have explicitly requested to receive your {{site.data.keyword.en_short}}. This reduces the likelihood of sending emails to uninterested recipients.

### Email frequency
{: #en-email-frequency}

- Maintain a reasonable email frequency. Sending too many emails in a short timeframe can result in recipients marking your emails as spam.

## Content and ongoing hygiene
{: #en-email-content-hygiene}

### Content and payload checks
{: #en-email-payloadcheck}

- Be mindful of the content you send in your emails. Avoid common spam triggers, such as excessive use of capital letters, misleading subject lines, and poor grammar.
- Prevent sending the same email multiple times to the same recipient, as this can be flagged as spam.

It's important to note that the IBM {{site.data.keyword.en_short}} Service does not perform payload validation or check personal data within the email content. Therefore, it is your responsibility to ensure that the content of your emails complies with privacy regulations and best practices, especially if you are dealing with sensitive or personal information.

### Handling emails in spam or junk folders
{: #en-email-spamhandling}

It's important for users to understand that despite following best practices, some legitimate emails might still end up in their spam or junk folders. This can occur for various reasons, such as user preferences or the occasional marking of emails as spam by other recipients.

- **User Action**:
  - Users should periodically check their spam or junk folders. If they find a legitimate email in these folders, they should take the following actions:
    - **Mark as "Not Spam"**: By marking an email as "Not Spam" or "Not Junk," users inform the email service provider that the message is not unwanted. This action signals that the sender is legitimate, and future emails from the same sender should be delivered to the inbox.
    - **Move to Inbox**: Users can also move legitimate emails from the spam/junk folder to their inbox. This helps train the email service provider to recognize these messages as wanted and trusted.

- **Educate Recipients**:
  - If you are a sender of {{site.data.keyword.en_short}}, consider educating your recipients about the importance of checking their spam or junk folders for legitimate emails. Encourage them to mark your emails as "Not Spam" to ensure they receive important notifications.

Understanding and actively managing emails in spam folders is essential to ensure the successful delivery of important {{site.data.keyword.en_short}}, even in cases where some recipients may mistakenly classify them as spam. It's a collaborative effort between senders and recipients to maintain an effective email communication channel.
