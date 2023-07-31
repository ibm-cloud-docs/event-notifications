---

copyright:
  years: 2021, 2023
lastupdated: "2023-07-19"

keywords: event-notifications, event notifications, about event notifications, destinations, email

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

## Using an {{site.data.keyword.cloud_notm}} email service with custom domain
{: #en-destinations-custom-email}

This capability is available only for selected users. If you would like to leverage this capability, please contact support.
{: tip}

### Configuring a webhook destination
{: #en-destinations-custom-email-webhook}

You can configure a custom email destination in the Destinations tab. As part of the configuration, enter the domain name to be used for sending emails.

### Custom domain name verification
{: #en-destinations-custom-email-verify}

After you create the destination with your domain name, make sure its validated for the right ownership. This will prevent misuse of your domain and to keep away from bad actors.
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

### Using a Custom email destination
{: #en-destinations-custom-email-use}

To use the email service destination, add it to a subscription along with the email addresses of interest. Within a single subscription, you can add up to 100 email recipients. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, Event Notifications immediately routes the event notification to your email recipients.

If you add an individual to the recipient list who does not want to receive email notifications, the recipient can opt out by clicking a link in the footer of the email. You can track recipients who opt into the Event Notifications dashboard.

By adding email addresses, you represent on behalf of yourself and your company that you inform the individuals, to whom the added emails pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

After a subscription is created, the list of users in the Invited tab automatically receives initial message with information that they are invited to subscribe to the list, which is the "Opt-in" message.

Opt-in message contains user or account who invited the recipient, the name of the subscription, the purpose of the notifications, the frequency of expected notifications, a way to accept or reject the invitation, and expiration time for the invitation.

The Event Notifications are only sent to the opted-in recipients.

You can either resend the invitation or remove the recipient from the Invited list. In the Invited tab, click and select the three vertical dots (overflow menu) and select Resend invitation for the recipient email address, to whom you need to resend the invitation. For deleting a user from the invited list, in the Invited tab, click the three vertical dots (overflow menu) and select Delete for the recipient email address, to whom you need to remove from the Invited list. For adding back a recipient after opted-out or not responded within the stipulated time that is mentioned in the invite email, you need to send a mail to the Reply to email address mentioned in the initial invite mail.

### Templates

Event Notifications offers users the flexibility of utilizing custom email destinations along with templates. Users have the option to provide HTML templates containing a payload. When sending notifications, the service integrates these templates seamlessly, replacing template variables with corresponding variables from the payload. This allows for dynamic and personalized email content for recipients.

In cases where a custom template is not available, the system automatically defaults to the "ibmenhtmlbody" template. If the "ibmenhtmlbody" template is also unavailable, the system gracefully fallbacks to the "ibmendefaultlong" template, ensuring a smooth and consistent user experience. This robust template selection mechanism guarantees that notifications are always dispatched with relevant and appealing content, maximizing their impact and effectiveness.

Example - 

Here in a snippet you can send template with following body (It has to be minimal without any \n) with a variable which will be present in payload.

```
<html>
  <body>
    {{event.custom_variable_from_payload}} 
  </body> 
</html>
```


