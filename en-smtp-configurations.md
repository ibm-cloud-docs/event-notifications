---
copyright:
  years: 2021, 2024
lastupdated: "2024-05-01"

keywords: event-notifications, event notifications, about event notifications, destinations, email, smtp

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} Event Notifications SMTP Interface
{: #en-smtp-configurations}

IBM Cloud Event Notifications supports SMTP, which is the most common email protocol on the internet. You can send email using variety of clients, softwares or programming languages which supports SMTP by connecting to the IBM Cloud Event Notifications SMTP interface. This document explains how you can setup SMTP configuration, get user credentials and allowlist IPs to send emails.

## Domain name verification
{: #en-smtp-configurations-verify}

After creating a SMTP configuration in an IBM Cloud Event Notifications instance, to get the required parameters to send email via SMTP Interface, you need to perform three types of verifications under `Verify` tab under `⋮`:

1. Create Sender Policy Framework (SPF), which is used to authenticate the sender of an email. SPF specifies the mail servers that are allowed to send email for your domain.
    * Open your DNS hosting provider for the domain name configured
    * Create a new TXT record with your domain name registerer with the name and value provided in the configure screen for SPF
2. Create DomainKeys Identified Mail (DKIM), which allows an organization to take responsibility for transmitting a message by signing it. DKIM allows the receiver to check the email that claimed to have come from a specific domain, is authorized by the owner of that domain.
    * Open your DNS hosting provider for the domain name configured
    * Create a new TXT record with your domain name registerer with the name and value provided in the configure screen for DKIM
3. For the enhanced security we do manual verification about the SMTP interface requirement using following questionnaire:

    ```text
    1. Will the nature of the email content be Marketing or Transactional?

    2. What is your website's URL?

    3. Explain how you plan to use IBM Cloud Event Notifications to send email. To help us process your request, you should answer the following questions:

    a. What is your strategy for creating or obtaining your email subscriber list?

    b. What is your approach to managing bounced emails and handling recipient complaints?

    c. What methods do you have in place for recipients to unsubscribe from your email communications?

    d. How did you determine the sending rate or quota specified in your request?

    e. Are you regularly cleaning your email list to remove invalid or outdated email addresses?

    4. Indicate the email addresses where you wish to receive account-related communications. You can provide a list of up to four email addresses, separated by commas.

    5. In the Event Notifications subscription, you are asked to provide a Reply-To field. Confirm that this is a valid email-id with a mailbox.

    6. Include a statement affirming your commitment to sending emails only to individuals who have explicitly requested them, and verify that you have established a procedure for managing bounce and complaint notifications.

    7. Provide the reason to use your own procedure to invite or subscribe email ids instead of using the Event Notifications provided  invitation or subscription flow.

    8. Whether you have a manual or automated process in place for handling unsubscribes, it's important to provide an "unsubscribe" link in the email payload you send. When recipients decide not to receive further emails, they can simply click on the 'unsubscribe' link and remove their email address from your mailing list. Add a statement that you agree to have an “unsubscribe” link in the email payload that you send.

    9. If you send the html content in the notification payload, do you have a process to validate this content is well formatted? Ill formatted HTML content may descrese the server reputation.
    ```
    {: codeblock}

    While many questions are self-explanatory, we've provided explanations for a few to ensure clarity.
    * Provide Nature of email as **`Marketing` or `Transactional`**
        * Marketing email - These emails are distributed to a broad audience. They are targeted list of prospects or customers containing marketing and promotional content such as to make a purchase, download information, etc.
        * Transactional email - These emails are individualized for each recipient, typically triggered by specific user actions like making a website purchase or requesting a password reset, etc.
    * **Website URL** is required to gain a clearer understanding of the type of content you intend to send.
    * A valid **Reply-To** email id is required to receive rejected or bounced emails' information.
    * Requirement of **Well Formatted** Email content is required to prevent emails classified as Spam at the receivers end. Email which are not well formatted (i.e not html) can result in Email Service Providers to classify the mails as spam.

    Upon filling out answers to the aforementioned questions, users have 2 methods to request for the enablement of SMTP interface Event Notifications verification:

    1. Via Support Ticket:
        1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon > **Support center**.
        1. From the Contact support section, click **Create a case**.
        1. Select under `Category`, `Topic` as Event Notifications and `Subtopic` as Others
        1. Under `Subject` add **Requesting for the Opt Out feature for the Custom Domain Email destination**
        1. In the 'Description' section firstly provide IBM Cloud Event Notifications instance id, region in which instance is created, and a DKIM Name which is in the format of `{{uuid}}._domainkey.{{domain}}`
        1. Later, please include responses to the aforementioned questionnaire.
        1. Add **Attachments** if you want to provide more evidences supporting your answers
        1. Add required email Ids in the **Watchlist** section. And to know more about other options while creating a support case refer [here](https://{DomainName}/docs/get-support?topic=get-support-open-case){: external}.

    2. Via opening a new issue in the IBM Cloud Event Notifications [Adopters repository](https://github.ibm.com/Notification-Hub/adopters/issues)
        1. Open a new Issue named as `SMTP Configuration Event Notifications Verification`
        2. In the description provide IBM Cloud Event Notifications instance id, region in which instance is created, and a DKIM Name which is in the format of `{{uuid}}._domainkey.{{domain}}`
        3. Later, please include responses to the aforementioned questionnaire.
        4. Add **Attachments** if you want to provide more evidences supporting your answers

Some of the common verification issues could be:

1. Make sure the domain name is spelled correctly
2. The DNS record for the domain is not updated correctly. Verify if the SPF/DKIM values are copied correctly.
3. The DNS propagation may take up to 72 hours to be updated across the internet in some rare cases.

It's worth mentioning that we do periodic checks on the SPF and DKIM TXT records of the domain provided, it is advisable to keep the records inserted in the DNS even after verifying once. If the SPF or DKIM fails in the periodic check we will stop sending emails.
{: note}

Upon successfully completing all three verification methods, `Setiings` option will be enabled under `⋮`.

## Requirements to send email over SMTP Interface
{: #en-smtp-configurations-requirements}

After successful verification of a SMTP configuration in an IBM Cloud Event Notifications instance, to send email using SMTP Interface you need following parameters:

1. The SMTP endpoint address. A list of IBM Cloud Event Notifications SMTP endpoints is mentioned below:

    | Event Notifications Instance Region | SMTP Endpoint                                   |
    |-------------------------------------|-------------------------------------------------|
    | us-south (Dallas)                   | smtp.us-south.event-notifications.cloud.ibm.com |
    | au-syd (Sydney)                     | smtp.us-south.event-notifications.cloud.ibm.com |
    | eu-gb (London)                      | smtp.us-south.event-notifications.cloud.ibm.com |
    | eu-de (Frankfurt)                   | smtp.eu-de.event-notifications.cloud.ibm.com    |
    | eu-es (Madrid)                      | smtp.eu-de.event-notifications.cloud.ibm.com    |
    | eu-fr2 (France dMZR)                | smtp.eu-fr2.event-notifications.cloud.ibm.com   |
    {: caption="Table 1. IBM Cloud Event Notifications SMTP endpoints" caption-side="bottom"}

    Based on the above table it can be depicted as instances created in the London and Sydney also connects to the Dallas SMTP endpoint and instances created in the Madrid also conencts to the Frankfurt SMTP endpoint.
    {: note}

2. The SMTP interface port number. As of now, we are supporting port 587.

3. An SMTP username and password. Usernames and passwords are unique across the SMTP configurations, and passwords are encrypted using single-way hashing. A maximum of 5 users can be created in a single SMTP configuration. We are currently supporting `Login` and `Plain` authentication methods from the SMTP protocol.

4. Client software or program can communicate strictly using Transport Layer Security (TLS).

5. Valid IP addresses or subnets can be provided from which the client is connecting to the SMTP interface.

6. When you access IBM Cloud Event Notifications through the SMTP interface, your SMTP client application assembles the message, so the information you need to provide depends on the application that you're using. At a minimum, the SMTP exchange between a client and a server requires the following:
   * A source address: The source address should be from the domain which you have provided while configuration; otherwise, the sender address will get rejected.
   * A destination address: The destination address can be any valid email address or set of email addresses.
   * Message data: Make sure the message data should be spam content-free, clean, and sensible.

## Using SMTP interface for sending emails
{: #en-smtp-configurations-send-emails}

1. Configure SMTP-enabled software such as ServiceNow, Jira, blogging platforms, RSS aggregators, list management software, and workflow systems using the provided SMTP endpoint, port, and valid username-password credentials.
2. To send an email using the SMTP interface, you can use an SMTP-enabled programming language, email server, or application. Make sure to complete all the required steps mentioned above. You need the correct SMTP endpoint, port, and credentials to connect to the IBM Cloud Event Notifications SMTP interface.
3. If you currently administer your own email server, you can use the IBM Cloud SMTP endpoint, port, and credentials to send all your outgoing email through Event Notifications SMTP configuration. There is no need to modify your existing email clients and applications.
4. To interact with the IBM Cloud Event Notifications SMTP interface using the command line, follow the example below:

    ```sh
    openssl s_client -starttls smtp -connect {{smtp_endpoint}}:587
    ...
    ...
    ...
    auth login
    334 VXNlcm5hbWU6
    dXNlcm5hbWU=
    334 UGFzc3dvcmQ6
    cGFzc3dvcmQ=
    235 2.7.0 Authentication successful
    mail from: mailer@example.com
    250 2.1.0 Ok
    rcpt to: recipient@test.com
    250 2.1.5 Ok
    data
    354 End data with <CR><LF>.<CR><LF>
    from: Mailer <mailer@example.com>
    to: Recipient <recipent@test.com>
    Subject: IBM Cloud Event Notifications SMTP interface
    Get the all events securely from IBM EN SMTP Interface
    .
    ```
    {: codeblock}



## Tracking Email Status
{: #en-destinations-smtp-configurations-tracking-status}

* After sending emails from any of the above methods, you will receive a Queue ID which will be benficial for debugging purposes.
* This capability allows users to monitor the delivery status of emails sent through a Custom Email destination, ensuring transparency and enhancing the overall user experience. For more information, follow [these steps](/docs/event-notifications?topic=event-notifications-en-destination-email-custom-domain-status).
