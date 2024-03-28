---

copyright:
  years: 2020, 2023
lastupdated: "2024-03-27"

keywords: event-notifications, event notifications, about event notifications, destinations, sms

subcollection: event-notifications

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} SMS service
{: #en-destinations-sms}

{{site.data.keyword.en_short}} provides a built-in SMS service for sending transactional and informational event notification text messages to recipients who need to be aware of events that happen within your {{site.data.keyword.cloud_notm}} account.
{: shortdesc}

The text messages originate from IBM-owned phone numbers or alphanumeric sender IDs. Except for test messages, the content cannot be modified within {{site.data.keyword.en_short}}.

![SMS state-diagram](images/en-sms-state-diagram.png "SMS state diagram"){: caption="Figure 1. SMS state diagram" caption-side="bottom"}

## Adding an SMS destination
{: #en-destinations-sms-add}

{{site.data.keyword.cloud_notm}} SMS service is a destination that provided by default and ready for immediate use. When a new instance is created, you see an entry `{{site.data.keyword.cloud_notm}} SMS service` in the destination tab. The SMS destination is pre-configured and is ready to use.

## Using an {{site.data.keyword.cloud_notm}} SMS service destination
{: #en-destinations-sms-use}

`{{site.data.keyword.cloud_notm}} SMS service` as the destination type is only supported for US and Canada numbers.
{: important}

To use the SMS service destination, add it to a subscription along with the phone numbers of the recipients. Within a single subscription, you can add up to 3 phone numbers for lite plan and 100 phone numbers for standard plan. The subscription also needs a topic to filter events of interest from your sources. When an event lands in the topic, {{site.data.keyword.en_short}} immediately routes the event notification to your SMS recipients.

When you select `{{site.data.keyword.cloud_notm}} SMS service` as the destination type, you can add up to 3 phone numbers for lite plan and 100 phone numbers for standard plan, to the recipient list. To comply with the regulatory standards, you may need to get a consent (opt-in) from the SMS recipients to receive SMSs from each of the {{site.data.keyword.en_short}} subscriptions.

### Create a subscription with IBM SMS service as destination
{: #en-create-subscription-sms-destination}

1. From the {{site.data.keyword.en_short}} dashboard, click **Subscriptions** in the navigation menu.

1. Click `Create +` to display **Create a Subscription** side panel.

1. Complete the following subscription details:
   - `Name`: name of the subscription.
   - `Description`: add an optional description for this subscription

1. Select a `Topic` from the list.

1. Select `{{site.data.keyword.cloud_notm}} SMS service` as **Destination** from the list.

1. The **Recipients** section displays three tabs:
   - *Invited* - displays the list of phone numbers added to the subscription. Enter the phone numbers that need to receive SMS notifications and need to be part of the subscription.
   - *Active* - displays the list of phone numbers added to the subscription and confirmed by the user to receive SMS notifications.
   - *Unsubscribed* - displays the list of phone numbers added to the subscription and refused by the user not to receive SMS notifications.

   Add the user's phone numbers with a *+ and country code*, who needs to receive SMS messages as part of this subscription, with comma (,) as separator between the numbers.

1. Click **Create**. The recipient automatically receives initial message that they have been invited to subscribe to the topic. This is the `opt-in` message.

The Opt-in message contains:
- invitee name or account
- name of the subscription
- name of the topic
- a link that will take you to a web page. The web page contains information that the recipient is subscribed to receive SMS notifications to a topic and a **Confirm** button. When the recipient click the **Confirm** button, then the recipient's number is moved from *Invited* tab to *Active* tab. A confirmation message also displaying that the recipient has accepted to receive SMS notifications. The confirmation message also contains a link to **Unsubscribe**, which on clicking moves to recipient's number to the *Unsubscribed* tab.
- an expiration time for the opt-in message.

{{site.data.keyword.en_short}} are routed only to opted-in recipients. To stop receiving the notifications, recipient can click the **Unsubscribe** link in the message. Once unsubscribed, the recipients will not receive any notifications on the topic they have unsubscribed. To restart the subscription, the recipient need to contact {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to subscription.

In some cases, the carrier service allows keywords like `START` and `STOP` for receiving notifications and to stop notifications.

When a recipient doesn't wants to receive any SMS notification, they can opt out by sending a response `STOP`, which immediately disables sending notifications to the recipient. However, the phone number is moved to **Unsubscribed** tab only on the next attempt to send an SMS to the same number.

To add a recipient number back to active list, take the following steps:

1. Recipient needs to send `START` message back to the number from which SMS was received.
1. After sending `START` message, the recipient can contact their {{site.data.keyword.IBM_notm}} {{site.data.keyword.en_short}} service administrator to add the number back to subscription.

By adding phone numbers, you represent on behalf of yourself and your company that you have properly informed the individuals, to whom the added phone numbers pertain, of their addition to this recipient list and purpose thereof, and have the required consents to do so.
{: note}

## SMS segment
{: #en-destinations-sms-segment}

SMS segments are character batches (of length 160 characters) of an SMS message, used by carriers to measure the message size.

If a message contains less than 160 characters, then it is considered as one SMS segment. If a message contains over 160 characters, for example, of 200 characters, then it is considered as 2 segments, first segment has 160 character and the second segment has 40 characters.

## SMS charges
{: #en-destinations-sms-charge}

Because SMS delivery rates vary widely with location, SMS text messages are charged in terms of `SMS Units`. An SMS unit is a fixed unit of cost. Therefore, the number of units that are consumed by a message varies based on the destination country, and {{site.data.keyword.en_short}} service charges vary. Table 1 shows the current SMS Units by country.

| Supported Country Code        | SMS Units | Price In USD |
|-------------------------------|-----------|------------------|
| +1684 (American Samoa) | 9.77 units | 0.1577855 USD
| +376 (Andorra) | 0.64 units | 0.010336 USD
| +54 (Argentina) | 2.67 units | 0.0431205 USD
| +247 (Ascension Island) | 7.32 units | 0.118218 USD
| +43 (Austria) | 3.43 units | 0.0553945 USD
| +994 (Azerbaijan) | 3.74 units | 0.060401 USD
| +1242 (Bahamas) | 1.03 units | 0.0166345 USD
| +973 (Bahrain) | 0.96 units | 0.015504 USD
| +880 (Bangladesh) | 6.33 units | 0.1022295 USD
| +375 (Belarus) | 3.03 units | 0.0489345 USD
| +32 (Belgium) | 4.39 units | 0.0708985 USD
| +229 (Benin) | 2.67 units | 0.0431205 USD
| +1441 (Bermuda) | 2.01 units | 0.0324615 USD
| +975 (Bhutan) | 1.65 units | 0.0266475 USD
| +591 (Bolivia) | 2.48 units | 0.040052 USD
| +387 (Bosnia and Herzegovina) | 3.18 units | 0.051357 USD
| +267 (Botswana) | 1.65 units | 0.0266475 USD
| +55 (Brazil) | 3.03 units | 0.0489345 USD
| +673 (Brunei) | 1.19 units | 0.0192185 USD
| +359 (Bulgaria) | 3.33 units | 0.0537795 USD
| +855 (Cambodia) | 6.89 units | 0.1112735 USD
| +1 (Canada) | 0.97 units | 0.0156655 USD
| +238 (Cape Verde) | 3.24 units | 0.052326 USD
| +56 (Chile) | 2.4 units | 0.03876 USD
| +86 (China) | 2.75 units | 0.0444125 USD
| +57 (Colombia) | 3.3 units | 0.053295 USD
| +682 (Cook Islands) | 1.15 units | 0.0185725 USD
| +506 (Costa Rica) | 2.1 units | 0.033915 USD
| +385 (Croatia) | 2.13 units | 0.0343995 USD
| +53 (Cuba) | 1.87 units | 0.0302005 USD
| +5999 (Curacao) | 10.25 units | 0.1655375 USD
| +357 (Cyprus) | 2.66 units | 0.042959 USD
| +420 (Czechia) | 2.2 units | 0.03553 USD
| +45 (Denmark) | 0.91 units | 0.0146965 USD
| +1809 (Dominican Republic) | 3.19 units | 0.0515185 USD
| +593 (Ecuador) | 3.59 units | 0.0579785 USD
| +20 (Egypt) | 4.18 units | 0.067507 USD
| +291 (Eritrea) | 6.59 units | 0.1064285 USD
| +372 (Estonia) | 3.73 units | 0.0602395 USD
| +268 (Eswatini) | 0.57 units | 0.0092055 USD
| +251 (Ethiopia) | 6.15 units | 0.0993225 USD
| +500 (Falkland Islands) | 3.66 units | 0.059109 USD
| +298 (Faroe Islands) | 0.72 units | 0.011628 USD
| +679 (Fiji) | 2.2 units | 0.03553 USD
| +358 (Finland) | 3.63 units | 0.0586245 USD
| +33 (France) | 2.48 units | 0.040052 USD
| +594 (French Guiana) | 6.76 units | 0.109174 USD
| +689 (French Polynesia) | 7.54 units | 0.121771 USD
| +995 (Georgia) | 1.1 units | 0.017765 USD
| +49 (Germany) | 6.52 units | 0.105298 USD
| +350 (Gibraltar) | 0.61 units | 0.0098515 USD
| +30 (Greece) | 2.75 units | 0.0444125 USD
| +299 (Greenland) | 0.61 units | 0.0098515 USD
| +590 (Guadeloupe) | 4.39 units | 0.0708985 USD
| +1671 (Guam) | 0.78 units | 0.012597 USD
| +502 (Guatemala) | 2.2 units | 0.03553 USD
| +504 (Honduras) | 1.91 units | 0.0308465 USD
| +852 (Hong Kong) | 1.93 units | 0.0311695 USD
| +36 (Hungary) | 3.46 units | 0.055879 USD
| +354 (Iceland) | 1.25 units | 0.0201875 USD
| +91 (India) | 3.34 units | 0.053941 USD
| +62 (Indonesia) | 25.02 units | 0.404073 USD
| +98 (Iran) | 7.46 units | 0.120479 USD
| +353 (Ireland) | 2.68 units | 0.043282 USD
| +972 (Israel) | 3.9 units | 0.062985 USD
| +39 (Italy) | 3.08 units | 0.049742 USD
| +81 (Japan) | 2.75 units | 0.0444125 USD
| +962 (Jordan) | 1.1 units | 0.017765 USD
| +7 (Kazakhstan) | 10.5 units | 0.169575 USD
| +254 (Kenya) | 12.69 units | 0.2049435 USD
| +686 (Kiribati) | 1.19 units | 0.0192185 USD
| +383 (Kosovo) | 4.18 units | 0.067507 USD
| +965 (Kuwait) | 2.12 units | 0.034238 USD
| +996 (Kyrgyzstan) | 1.76 units | 0.028424 USD
| +856 (Laos) | 1.73 units | 0.0279395 USD
| +371 (Latvia) | 2.56 units | 0.041344 USD
| +961 (Lebanon) | 1.69 units | 0.0272935 USD
| +266 (Lesotho) | 3.85 units | 0.0621775 USD
| +218 (Libya) | 11.08 units | 0.178942 USD
| +423 (Liechtenstein) | 1.33 units | 0.0214795 USD
| +370 (Lithuania) | 0.7 units | 0.011305 USD
| +352 (Luxembourg) | 0.7 units | 0.011305 USD
| +853 (Macau) | 1.44 units | 0.023256 USD
| +60 (Malaysia) | 2.48 units | 0.040052 USD
| +356 (Malta) | 1.38 units | 0.022287 USD
| +692 (Marshall Islands) | 10.99 units | 0.1774885 USD
| +596 (Martinique) | 8.85 units | 0.1429275 USD
| +230 (Mauritius) | 1.14 units | 0.018411 USD
| +262 (Mayotte) | 9.52 units | 0.153748 USD
| +52 (Mexico) | 1.93 units | 0.0311695 USD
| +691 (Micronesia) | 4.97 units | 0.0802655 USD
| +373 (Moldova) | 2.35 units | 0.0379525 USD
| +976 (Mongolia) | 1.03 units | 0.0166345 USD
| +212 (Morocco) | 2.98 units | 0.048127 USD
| +95 (Myanmar) | 4.75 units | 0.0767125 USD
| +264 (Namibia) | 1.76 units | 0.028424 USD
| +674 (Nauru) | 10.41 units | 0.1681215 USD
| +977 (Nepal) | 1.91 units | 0.0308465 USD
| +31 (Netherlands) | 3.63 units | 0.0586245 USD
| +687 (New Caledonia) | 6.59 units | 0.1064285 USD
| +64 (New Zealand) | 3.68 units | 0.059432 USD
| +505 (Nicaragua) | 2.61 units | 0.0421515 USD
| +234 (Nigeria) | 9.36 units | 0.151164 USD
| +850 (North Korea) | 0.42 units | 0.006783 USD
| +1670 (Northern Mariana Islands) | 0.78 units | 0.012597 USD
| +47 (Norway) | 2.48 units | 0.040052 USD
| +968 (Oman) | 2.94 units | 0.047481 USD
| +92 (Pakistan) | 5.39 units | 0.0870485 USD
| +507 (Panama) | 3.03 units | 0.0489345 USD
| +595 (Paraguay) | 0.78 units | 0.012597 USD
| +51 (Peru) | 2.2 units | 0.03553 USD
| +63 (Philippines) | 1.65 units | 0.0266475 USD
| +48 (Poland) | 2.64 units | 0.042636 USD
| +351 (Portugal) | 2.48 units | 0.040052 USD
| +1787 (Puerto Rico) | 0.44 units | 0.007106 USD
| +974 (Qatar) | 2.39 units | 0.0385985 USD
| +262 (Réunion Island) | 7.42 units | 0.119833 USD
| +40 (Romania) | 3.24 units | 0.052326 USD
| +7 (Russia) | 35.34 units | 0.570741 USD
| +250 (Rwanda) | 1.53 units | 0.0247095 USD
| +290 (Saint Helena) | 7.32 units | 0.118218 USD
| +508 (Saint Pierre and Miquelon) | 3.66 units | 0.059109 USD
| +378 (San Marino) | 3.44 units | 0.055556 USD
| +966 (Saudi Arabia) | 1.85 units | 0.0298775 USD
| +381 (Serbia) | 1 units | 0.01615 USD
| +65 (Singapore) | 1.32 units | 0.021318 USD
| +421 (Slovakia) | 3.3 units | 0.053295 USD
| +386 (Slovenia) | 1.17 units | 0.0188955 USD
| +27 (South Africa) | 1.78 units | 0.028747 USD
| +82 (South Korea) | 1.54 units | 0.024871 USD
| +34 (Spain) | 3.3 units | 0.053295 USD
| +94 (Sri Lanka) | 4.78 units | 0.077197 USD
| +249 (Sudan) | 8.26 units | 0.133399 USD
| +597 (Suriname) | 0.88 units | 0.014212 USD
| +46 (Sweden) | 2.22 units | 0.035853 USD
| +41 (Switzerland) | 2.67 units | 0.0431205 USD
| +963 (Syria) | 12.28 units | 0.198322 USD
| +886 (Taiwan) | 1.97 units | 0.0318155 USD
| +255 (Tanzania) | 2.09 units | 0.0337535 USD
| +66 (Thailand) | 1.1 units | 0.017765 USD
| +1868 (Trinidad and Tobago) | 1.52 units | 0.024548 USD
| +90 (Turkey) | 1.16 units | 0.018734 USD
| +993 (Turkmenistan) | 3.85 units | 0.0621775 USD
| +688 (Tuvalu) | 0.42 units | 0.006783 USD
| +256 (Uganda) | 7.56 units | 0.122094 USD
| +380 (Ukraine) | 9.56 units | 0.154394 USD
| +971 (United Arab Emirates) | 1.1 units | 0.017765 USD
| +44 (United Kingdom) | 1.6 units | 0.02584 USD
| +1 (United States) | 0.61 units | 0.0098515 USD
| +598 (Uruguay) | 4.39 units | 0.0708985 USD
| +998 (Uzbekistan) | 13.71 units | 0.2214165 USD
| +58 (Venezuela) | 1.8 units | 0.02907 USD
| +84 (Vietnam) | 3.61 units | 0.0583015 USD
| +1340 (Virgin Islands, US) | 2.39 units | 0.0385985 USD
| +681 (Wallis and Futuna) | 7.84 units | 0.126616 USD
| +967 (Yemen) | 2.65 units | 0.0427975 USD
{: caption="Table 1. Destination country, unit per segment and price per segment" caption-side="bottom"}

## Calculating SMS Units and Price
{: #en-destinations-sms-charge-calculations}

If a notification is longer (notifications greater than 160 characters) might be split into multiple segments. Each segment is considered a message, as is each recipient phone number. For example, if an incoming notification is split into three SMS segments and the message is sent to five subscribed phone numbers

### Total SMS Units

The total number of SMS units consumed for the notification is calculated as follows:

```
Total SMS units = (Number of Segments) x (Number of phone numbers) x (SMS Unit for the country)
```

In this example, with five subscribed phone numbers - two in the United States, two in Mexico, and one in France - the total number of SMS units would be:

```
SMS units for United States is: 3 x 2 x 0.61 = 3.66
SMS units for Mexico is: 3 x 2 x 1.93 = 11.58
SMS units for France is: 3 x 1 x 2.48 = 7.44
```
Total SMS units = 22.68

### Total SMS Price

The total cost of SMS messages sent is calculated as follows:

```
Total SMS price = (Number of Segments) x (Number of phone numbers) x (Price In USD for the country)
```

In this example, the total cost of SMS messages sent would be:

```
SMS price for United States is: 3 x 2 x 0.0098515 = 0.059109 USD
SMS price for Mexico is: 3 x 2 x 0.0311695 = 0.187017 USD
SMS price for France is: 3 x 1 x 0.040052 = 0.120156 USD
```

Total SMS price = 0.366282 USD

### Alternative Calculation

Alternatively, the total cost of SMS messages sent can be calculated using:

```
Total SMS Price = Total SMS units x 0.01615 ($0.01615 USD/Outbound Digital Message SMS Unit)
```

Total SMS price = 22.68 x 0.01615 = 0.366282 USD

### Charging for Successfully Sent Messages

Regardless of whether the message was successfully delivered to the local device, you are charged for messages that are successfully sent by the {{site.data.keyword.cloud_notm}} SMS service to the local SMS provider. Therefore, it is essential to verify your phone number list carefully to prevent unnecessary charges


For personalized numbers or if you're looking for higher volume and price negotiations, you can find more details [here](/docs/event-notifications?topic=event-notifications-en-destinations-sms-custom).
{: note}

You can monitor your SMS usage by setting up a monitoring dashboard through the `Actions` menu in the {{site.data.keyword.en_short}} dashboard. See [Monitor {{site.data.keyword.en_short}} service metrics with {{site.data.keyword.monitoringfull_notm}}](/docs/event-notifications?topic=event-notifications-en-monitoring) for details.
