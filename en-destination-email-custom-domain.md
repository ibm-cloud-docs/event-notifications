---
copyright:
  years: 2021, 2024
lastupdated: "2024-01-31"

keywords: event-notifications, event notifications, about event notifications, destinations, email,  sandbox, testing

subcollection: event-notifications
---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} Email Service with Custom domain
{: #en-destinations-custom-email}


You can configure a custom email destination in the Destinations tab. As part of the configuration, enter the domain name to be used for sending emails. When you create a custom email destination, you can choose between sandbox mode for testing or production mode with your own verified domain.

Custom email destination is not supported by Lite Plan. To know more about the plans and destinations available, refer [here](/docs/event-notifications?topic=event-notifications-getting-started).
{: note}

## Choosing between Sandbox and Production mode
{: #en-destinations-custom-email-modes}

When you create a custom email destination, you can select one of the following modes:

Sandbox mode
:   Use an {{site.data.keyword.en_short}}-provided domain for immediate testing without domain verification.

Production mode
:   Use your own domain with full control over email sending. Production mode requires domain verification through SPF and DKIM records.

## Sandbox environment for testing
{: #en-destinations-custom-email-sandbox}

Sandbox mode allows you to test your email notification configuration quickly without setting up and verifying your own domain. {{site.data.keyword.en_short}} automatically maps an {{site.data.keyword.en_short}}-owned domain to your destination, enabling you to start sending test notifications immediately.

### Sandbox mode restrictions
{: #en-destinations-custom-email-sandbox-restrictions}

The following restrictions apply in sandbox mode:

Instance limit
:   You can create only one custom email destination with sandbox mode enabled per {{site.data.keyword.en_short}} instance.

Subscription flow requirement
:   Sandbox destinations must use the {{site.data.keyword.en_short}} managed email opt-in capability. Customer-managed opt-in is not available in sandbox mode.

Recipient limit
:   You can invite up to 10 recipients to subscribe to notifications from a sandbox destination.

Rate limiting
:   You can send up to 3000 notifications per {{site.data.keyword.en_short}} instance.

### Using Sandbox mode
{: #en-destinations-custom-email-sandbox-use}

To use Sandbox mode:

1. In the {{site.data.keyword.en_short}} dashboard, go to **Destinations**.
2. Click **Add a destination**.
3. Select **Custom Email** as the destination type.
4. Select the **Sandbox environment (recommended for testing)** checkbox.
5. Complete the destination details and click **Create**.

After you create the sandbox destination, {{site.data.keyword.en_short}} automatically maps an {{site.data.keyword.en_short}} domain to your destination. You can then:

1. Create a subscription for the sandbox destination.
2. {{site.data.keyword.en_short}} provides a default sender email address for your subscription.
3. Add email addresses to invite users (up to 10 recipients).
4. You can start sending notifications.

### Transitioning from sandbox to production
{: #en-destinations-custom-email-sandbox-to-production}

After you complete testing in sandbox mode and are ready to send notifications to a larger audience, you can transition your existing sandbox destination to production mode by updating the domain.

Updating the domain transitions you out of the sandbox environment. You must reconfigure and verify your own domain and update the subscription details in the subscriptions section.
{: important}

To transition from sandbox to production:

1. In the {{site.data.keyword.en_short}} dashboard, go to **Destinations**.
2. Locate your sandbox custom email destination in the destinations list.
3. Click the overflow menu (three vertical dots) for the destination.
4. Select **Update domain**.
6. In the **Domain name** field, enter your domain name. Review your changes before saving. Updates will require DNS changes depending on your configuration.
8. Click **Save** to update the domain.
9. Complete the domain verification process by configuring SPF and DKIM records. For more information, see [Custom domain name verification](#en-destinations-custom-email-verify).
10. Update your subscriptions to reflect the new domain configuration:
    - Navigate to the **Subscriptions** section.
    - Update the sender email address and other subscription details as needed.


After the transition is complete, your destination operates in production mode with your verified domain, and Sandbox restrictions no longer apply.

## Custom domain name verification
{: #en-destinations-custom-email-verify}

After you create the destination with your domain name, make sure its validated for ownership. This will prevent misuse of your domain and to keep away from bad actors.
To verify your custom domain name, follow these steps:

1. Select the configure overflow menu for the destination you want to verify.
2. Create Sender Policy Framework (SPF), which is used to authenticate the sender of an email. SPF specifies the mail servers that are allowed to send email for your domain.
    * Open your DNS hosting provider for the domain name configured
    * Create a new TXT record with your domain name registerer with the name and value provided in the configure screen for SPF
3. Create DomainKeys Identified Mail (DKIM), which allows an organization to take responsibility for transmitting a message by signing it. DKIM allows the receiver to check the email that claimed to have come from a specific domain, is authorized by the owner of that domain.
    * Open your DNS hosting provider for the domain name configured
    * Create a new TXT record with your domain name registerer with the name and value provided in the configure screen for DKIM
4. Save the TXT records.
5. In the destination verify screen, click on Verify buttons for both SPF and DKIM.

Some of the common verification issues could be
a. Make sure the domain name is spelled correctly
b. The DNS record for the domain is not updated correctly. Verify if the SPF/DKIM values are copied correctly.
c. The DNS propagation may take up to 72 hours to be updated across the internet.
{: note}

## Using a Custom email destination
{: #en-destinations-custom-email-use}

To use the email service destination, add it to a subscription along with the email addresses of interest. For a single subscription, you can add up to 10,000 email addresses with the {{site.data.keyword.en_short}} managed email Opt-in capability. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your email recipients.

Custom domain emails are sent from regional email infrastructure based on your {{site.data.keyword.en_short}} instance location. Instances in Dallas, Toronto, Tokyo, Osaka, Sydney, London, Sao Paulo, Montreal, Chennai, and Washington DC send emails from the Dallas region. Instances in Frankfurt and Madrid send emails from the Frankfurt region.

If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who opt into the {{site.data.keyword.en_short}} dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you inform the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

After a subscription is created, the list of users in the Invited tab automatically receives initial message with information that they are invited to subscribe to the list, which is the "Opt-in" message.

Opt-in message contains user or account who invited the recipient, the name of the subscription, the purpose of the notifications, the frequency of expected notifications, a way to accept or reject the invitation, and expiration time for the invitation.

The {{site.data.keyword.en_short}} are only sent to the opted-in recipients.

You can either resend the invitation or remove the recipient from the Invited list. In the Invited tab, click and select the three vertical dots (overflow menu) and select Resend invitation for the recipient email address, to whom you need to resend the invitation. For deleting a user from the invited list, in the Invited tab, click the three vertical dots (overflow menu) and select Delete for the recipient email address, to whom you need to remove from the Invited list. For adding back a recipient after opted-out or not responded within the stipulated time that is mentioned in the invite email, you need to send a mail to the Reply to email address mentioned in the initial invite mail.

## Opting out of Event Notifications managed opt-in capability
{: #en-destination-email-custom-domain-opt-out-desc}

{{site.data.keyword.en_short}} provides users with the flexibility to bypass the traditional subscription flow by offering an opt-out capability. With this feature, users can conveniently send notifications by specifying the desired email addresses and templates through the send notifications payload, streamlining the process and enhancing user control over communication preferences. By default opting out functionality is not enabled for the security purposes and to prevent fraud, detection as well as it helps protect users's reputation as a sender. More information about it and to get it enabled follow [this section](/docs/event-notifications?topic=event-notifications-en-destinations-custom-domain-opt-out).

## Email Templates
{: #en-destinations-custom-email-templates}

{{site.data.keyword.en_short}} offers users the flexibility of utilizing custom email destinations along with templates. Users have the option to provide HTML templates containing a payload. When sending notifications, the service integrates these templates seamlessly, replacing template variables with corresponding variables from the payload. This allows for dynamic and personalized email content for recipients.

In cases where a custom template is not available, the system automatically defaults to the "ibmenhtmlbody" template. If the "ibmenhtmlbody" template is also unavailable, the system gracefully fallbacks to the "ibmendefaultlong" template, ensuring a smooth and consistent user experience. This robust template selection mechanism guarantees that notifications are always dispatched with relevant and appealing content, maximizing their impact and effectiveness.

In the following example snippet, you can find a template with a minimal body that should not contain any line breaks (\n). The template includes a variable that will be replaced with its value in the email.

```html
<html>
  <body>
    {{event.custom_variable_from_payload}}
  </body>
</html>
```

For more information on how to create custom templates, follow [these steps](/docs/event-notifications?topic=event-notifications-en-create-en-template).

## Tracking Email Status
{: #en-destinations-custom-email-tracking-status}

This capability allows users to monitor the delivery status of emails sent through a Custom Email destination, ensuring transparency and enhancing the overall user experience. For more information, follow [these steps](/docs/event-notifications?topic=event-notifications-en-destination-email-custom-domain-status).
