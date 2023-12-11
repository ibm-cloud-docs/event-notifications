---

copyright:
  years:  2023
lastupdated: "2023-12-07"

keywords: event notifications, event notification, notifications, email, custom domain, best practices

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# Email Best Practices
{: #en-email-bestpractices}

IBM {{site.data.keyword.en_short}} is a powerful tool for sending event-related emails to your customers. To ensure the smooth and reliable operation of the service, it is essential to follow best practices for email communication. In this documentation, we will provide guidelines and recommendations to help you make the most of the service while avoiding common pitfalls.

## Use a Custom Email Domain
{: #en-email-use-custom-email}

- Using a custom email domain for sending {{site.data.keyword.en_short}} is highly recommended. This establishes trust and brand recognition, reducing the likelihood of your emails being flagged as spam.

## Monitor and Prevent Spam
{: #en-email-preventspam}

- The origin IP addresses could be blacklisted resulting in the emails being marked as spam, if the email service is not used responsibly:
  - Educate team on the importance of email etiquette.
  - Implement rate limits on email sends to avoid sending a high volume of emails in a short period.
  - Regularly monitor email sending activity for any signs of abuse.
  
## Shared IP Addresses
{: #en-email-sharedip}

{{site.data.keyword.en_short}} uses the following  Shared IPs to send Emails.
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
    - Unfortunately, due to the shared IP address, the entire IP reputation is affected by one user's actions, due to which, another user's legitimate event notifications may also be blocked or flagged as spam by the email service providers, despite their adherence to the best practices.
    - If the shared IP's reputation is adversely impacted, it will be challenging for both the users to deliver emails effectively.

Thus, it is important to maintain a responsible and ethical approach to email communication, as the actions of one user on a shared IP address can impact the deliverability of all users. Regular monitoring, education, and adherence to email best practices are crucial to prevent such issues.

## Authentication and Verification
{: #en-email-authverification}

- Implement DomainKeys Identified Mail (DKIM), Sender Policy Framework (SPF), and Domain-based Message Authentication, Reporting, and Conformance (DMARC) to authenticate your emails. Here's what you need to know about them:
  
  - **DomainKeys Identified Mail (DKIM)**: DKIM is an email authentication method that adds a digital signature to your outgoing emails. This signature is generated using a private key that only you have access to. The recipient's email service provider can then verify the signature using the public key stored in your DNS records. This verification ensures that the email hasn't been tampered with in transit and that it genuinely comes from your domain. Implementing DKIM helps prevent email spoofing and phishing, which can improve email deliverability.

  - **Sender Policy Framework (SPF)**: SPF is another email authentication method that helps prevent email spoofing. SPF specifies which IP addresses or domains are authorized to send email on behalf of your domain. By setting up SPF records in your DNS, you inform receiving email servers which sources are legitimate senders for your domain. This ensures that only authorized servers can send emails claiming to be from your domain.
  
  - **Domain-based Message Authentication, Reporting, and Conformance (DMARC)**: DMARC is an email authentication and reporting protocol that builds upon SPF and DKIM. It allows you to set policies that define how email providers should handle emails that fail authentication checks. DMARC helps prevent domain spoofing and phishing attacks by providing clear instructions to email receivers on how to handle messages that claim to be from your domain. DMARC also offers reporting features, giving you insights into how your email domain is used and whether unauthorized sources are attempting to send emails on your behalf.
  
With the implementation of DMARC in addition to DKIM and SPF, your email messages will be more secure, and you'll have better control over how emails claiming to be from your domain are treated by email service providers, enhancing your email deliverability and security.

## Handling Emails in Spam/Junk Folders
{: #en-email-spamhandling}
 
It's important for users to understand that despite following best practices, some legitimate emails might still end up in their spam or junk folders. This can occur for various reasons, such as user preferences or the occasional marking of emails as spam by other recipients.

  - **User Action**:
    - Users should periodically check their spam or junk folders. If they find a legitimate email in these folders, they should take the following actions:
      - **Mark as "Not Spam"**: By marking an email as "Not Spam" or "Not Junk," users inform the email service provider that the message is not unwanted. This action signals that the sender is legitimate, and future emails from the same sender should be delivered to the inbox.
      - **Move to Inbox**: Users can also move legitimate emails from the spam/junk folder to their inbox. This helps train the email service provider to recognize these messages as wanted and trusted.

  - **Educate Recipients**:
    - If you are a sender of {{site.data.keyword.en_short}}, consider educating your recipients about the importance of checking their spam or junk folders for legitimate emails. Encourage them to mark your emails as "Not Spam" to ensure they receive important notifications.
Understanding and actively managing emails in spam folders is essential to ensure the successful delivery of important {{site.data.keyword.en_short}}, even in cases where some recipients may mistakenly classify them as spam. It's a collaborative effort between senders and recipients to maintain an effective email communication channel.

## Content and Payload Checks
{: #en-email-payloadcheck}

- Be mindful of the content you send in your emails. Avoid common spam triggers, such as excessive use of capital letters, misleading subject lines, and poor grammar.
- Prevent sending the same email multiple times to the same recipient, as this can be flagged as spam.

It's important to note that the IBM {{site.data.keyword.en_short}} Service does not perform payload validation or check personal data within the email content. Therefore, it is your responsibility to ensure that the content of your emails complies with privacy regulations and best practices, especially if you are dealing with sensitive or personal information.

## Additional Recommendations
{: #en-email-recommendations}

### Opt-In Subscription
{: #en-email-Opt-in}

- Use a double opt-in process for subscribers, ensuring that they have explicitly requested to receive your {{site.data.keyword.en_short}}. This reduces the likelihood of sending emails to uninterested recipients.

### Email Frequency
{: #en-email-frequency}

- Maintain a reasonable email frequency. Sending too many emails in a short timeframe can result in recipients marking your emails as spam.

## Conclusion
{: #en-email-conclusion}

IBM {{site.data.keyword.en_short}} service provides a valuable platform for reaching your customers and users with important event-related emails. By following these email best practices and additional recommendations, you can improve the deliverability of your emails, maintain a positive sender reputation, and provide a better experience for your recipients. Remember that email communication should be respectful and valuable to your audience to build trust and engagement.
