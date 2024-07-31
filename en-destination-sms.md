---

copyright:
  years: 2020, 2023
lastupdated: "2024-07-29"

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
|"+93"(Afghanistan) | 3.14706 units | 0.050825019 USD
|"+355"(Albania) | 4.31478 units | 0.069683697 USD
|"+213"(Algeria) | 4.14087 units | 0.0668750505 USD
|"+1684"(American Samoa) | 9.77 units | 0.1577855 USD
|"+376"(Andorra) | 0.72879 units | 0.0117699585 USD
|"+244"(Angola) | 1.86339 units | 0.0300937485 USD
|"+1264"(Anguilla) | 2.48452 units | 0.040124998 USD
|"+1268"(Antigua and Barbuda) | 2.2692 units | 0.03664758 USD
|"+54"(Argentina) | 3.02283 units | 0.0488187045 USD
|"+374"(Armenia) | 4.34791 units | 0.0702187465 USD
|"+297"(Aruba) | 2.48452 units | 0.040124998 USD
|"+247"(Ascension Island) | 7.32 units | 0.118218 USD
|"+61"(Australia) | 2.48452 units | 0.040124998 USD
|"+43"(Austria) | 3.87585 units | 0.0625949775 USD
|"+994"(Azerbaijan) | 4.22368 units | 0.068212432 USD
|"+1242"(Bahamas) | 1.15944 units | 0.018724956 USD
|"+973"(Bahrain) | 1.08491 units | 0.0175212965 USD
|"+880"(Bangladesh) | 2.79923 units | 0.0452075645 USD
|"+1246"(Barbados) | 2.48452 units | 0.040124998 USD
|"+375"(Belarus) | 3.42864 units | 0.055372536 USD
|"+32"(Belgium) | 4.96904 units | 0.080249996 USD
|"+501"(Belize) | 0.68738 units | 0.011101187 USD
|"+229"(Benin) | 3.02283 units | 0.0488187045 USD
|"+1441"(Bermuda) | 1.73088 units | 0.027953712 USD
|"+975"(Bhutan) | 1.86339 units | 0.0300937485 USD
|"+591"(Bolivia) | 2.79923 units | 0.0452075645 USD
|"+387"(Bosnia and Herzegovina) | 3.59427 units | 0.0580474605 USD
|"+267"(Botswana) | 1.86339 units | 0.0300937485 USD
|"+55"(Brazil) | 3.42036 units | 0.055238814 USD
|"+673"(Brunei) | 1.19 units | 0.0192185 USD
|"+359"(Bulgaria) | 3.76819 units | 0.0608562685 USD
|"+226"(Burkina Faso) | 1.73088 units | 0.027953712 USD
|"+257"(Burundi) | 4.34791 units | 0.0702187465 USD
|"+855"(Cambodia) | 0.81161 units | 0.0131075015 USD
|"+237"(Cameroon) | 3.77647 units | 0.0609899905 USD
|"+1"(Canada) | 0.29814 units | 0.004814961 USD
|"+238"(Cape Verde) | 3.66881 units | 0.0592512815 USD
|"+1345"(Cayman Islands) | 2.15325 units | 0.0347749875 USD
|"+236"(Central African Republic) | 0.82817 units | 0.0133749455 USD
|"+235"(Chad) | 1.39961 units | 0.0226037015 USD
|"+56"(Chile) | 2.71641 units | 0.0438700215 USD
|"+86"(China) | 3.10565 units | 0.0501562475 USD
|"+57"(Colombia) | 3.76819 units | 0.0608562685 USD
|"+269"(Comoros) | 0.69567 units | 0.0112350705 USD
|"+682"(Cook Islands) | 1.30023 units | 0.0209987145 USD
|"+506"(Costa Rica) | 2.37686 units | 0.038386289 USD
|"+385"(Croatia) | 2.40998 units | 0.038921177 USD
|"+53"(Cuba) | 2.111847 units | 0.03410632905 USD
|"+5999"(Curacao) | 2.15325 units | 0.0347749875 USD
|"+357"(Cyprus) | 3.00627 units | 0.0485512605 USD
|"+420"(Czechia) | 2.48452 units | 0.040124998 USD
|"+243"(Democratic Republic of the Congo) | 2.48452 units | 0.040124998 USD
|"+45"(Denmark) | 1.02693 units | 0.0165849195 USD
|"+253"(Djibouti) | 5.2589 units | 0.084931235 USD
|"+1767"(Dominica) | 2.15325 units | 0.0347749875 USD
|"+1809"(Dominican Republic) | 3.60255 units | 0.0581811825 USD
|"+670"(East Timor) | 4.31478 units | 0.069683697 USD
|"+593"(Ecuador) | 3.69365 units | 0.0596524475 USD
|"+20"(Egypt) | 4.18 units | 0.067507 USD
|"+503"(El Salvador) | 2.02074 units | 0.032634951 USD
|"+291"(Eritrea) | 6.59 units | 0.1064285 USD
|"+372"(Estonia) | 4.2154 units | 0.06807871 USD
|"+268"(Eswatini) | 0.57 units | 0.0092055 USD
|"+251"(Ethiopia) | 6.15 units | 0.0993225 USD
|"+500"(Falkland Islands) | 3.66 units | 0.059109 USD
|"+298"(Faroe Islands) | 0.81161 units | 0.0131075015 USD
|"+679"(Fiji) | 2.48452 units | 0.040124998 USD
|"+358"(Finland) | 4.10774 units | 0.066340001 USD
|"+33"(France) | 2.79923 units | 0.0452075645 USD
|"+594"(French Guiana) | 7.64404 units | 0.123451246 USD
|"+689"(French Polynesia) | 8.53019 units | 0.1377625685 USD
|"+995"(Georgia) | 1.24226 units | 0.020062499 USD
|"+49"(Germany) | 3.42036 units | 0.055238814 USD
|"+350"(Gibraltar) | 0.68738 units | 0.011101187 USD
|"+30"(Greece) | 3.10565 units | 0.0501562475 USD
|"+299"(Greenland) | 0.68738 units | 0.011101187 USD
|"+1473"(Grenada) | 2.48452 units | 0.040124998 USD
|"+590"(Guadeloupe) | 4.96904 units | 0.080249996 USD
|"+1671"(Guam) | 0.87786 units | 0.014177439 USD
|"+502"(Guatemala) | 2.48452 units | 0.040124998 USD
|"+592"(Guyana) | 2.65015 units | 0.0427999225 USD
|"+509"(Haiti) | 1.4493 units | 0.023406195 USD
|"+504"(Honduras) | 2.16153 units | 0.0349087095 USD
|"+852"(Hong Kong) | 2.1781 units | 0.035176315 USD
|"+36"(Hungary) | 3.90898 units | 0.063130027 USD
|"+354"(Iceland) | 1.40789 units | 0.0227374235 USD
|"+91"(India) | 0.4969 units | 0.008024935 USD
|"+62"(Indonesia) | 1.7226 units | 0.02781999 USD
|"+98"(Iran) | 7.46 units | 0.120479 USD
|"+353"(Ireland) | 3.03111 units | 0.0489524265 USD
|"+972"(Israel) | 3.9 units | 0.062985 USD
|"+39"(Italy) | 3.47833 units | 0.0561750295 USD
|"+1876"(Jamaica) | 2.48452 units | 0.040124998 USD
|"+81"(Japan) | 2.75 units | 0.0444125 USD
|"+962"(Jordan) | 1.1 units | 0.017765 USD
|"+7"(Kazakhstan) | 1.9048 units | 0.03076252 USD
|"+254"(Kenya) | 12.69 units | 0.2049435 USD
|"+686"(Kiribati) | 1.34164 units | 0.021667486 USD
|"+383"(Kosovo) | 4.18 units | 0.067507 USD
|"+965"(Kuwait) | 2.12 units | 0.034238 USD
|"+996"(Kyrgyzstan) | 1.98762 units | 0.032100063 USD
|"+856"(Laos) | 1.95449 units | 0.0315650135 USD
|"+371"(Latvia) | 2.89861 units | 0.0468125515 USD
|"+961"(Lebanon) | 1.69 units | 0.0272935 USD
|"+266"(Lesotho) | 3.85 units | 0.0621775 USD
|"+218"(Libya) | 11.08 units | 0.178942 USD
|"+423"(Liechtenstein) | 1.50728 units | 0.024342572 USD
|"+370"(Lithuania) | 0.78676 units | 0.012706174 USD
|"+352"(Luxembourg) | 0.79505 units | 0.0128400575 USD
|"+853"(Macau) | 1.62322 units | 0.026215003 USD
|"+389"(Macedonia) | 0.87786 units | 0.014177439 USD
|"+60"(Malaysia) | 1.83026 units | 0.029558699 USD
|"+960"(Maldives) | 0.64598 units | 0.010432577 USD
|"+356"(Malta) | 1.55697 units | 0.0251450655 USD
|"+692"(Marshall Islands) | 10.99 units | 0.1774885 USD
|"+596"(Martinique) | 5.78065 units | 0.0933574975 USD
|"+222"(Mauritania) | 4.34791 units | 0.0702187465 USD
|"+230"(Mauritius) | 1.14 units | 0.018411 USD
|"+262"(Mayotte) | 9.52 units | 0.153748 USD
|"+52"(Mexico) | 2.1781 units | 0.035176315 USD
|"+691"(Micronesia) | 4.97 units | 0.0802655 USD
|"+373"(Moldova) | 2.65844 units | 0.042933806 USD
|"+377"(Monaco) | 4.72059 units | 0.0762375285 USD
|"+976"(Mongolia) | 1.15944 units | 0.018724956 USD
|"+382"(Montenegro) | 0.81161 units | 0.0131075015 USD
|"+1644"(Montserrat) | 1.15944 units | 0.018724956 USD
|"+212"(Morocco) | 2.98 units | 0.048127 USD
|"+95"(Myanmar) | 5.36656 units | 0.086669944 USD
|"+264"(Namibia) | 1.76 units | 0.028424 USD
|"+674"(Nauru) | 10.41 units | 0.1681215 USD
|"+977"(Nepal) | 2.16153 units | 0.0349087095 USD
|"+31"(Netherlands) | 4.09946 units | 0.066206279 USD
|"+687"(New Caledonia) | 7.45356 units | 0.120374994 USD
|"+64"(New Zealand) | 4.15743 units | 0.0671424945 USD
|"+505"(Nicaragua) | 2.9483 units | 0.047615045 USD
|"+234"(Nigeria) | 9.36 units | 0.151164 USD
|"+850"(North Korea) | 0.42 units | 0.006783 USD
|"+1670"(Northern Mariana Islands) | 0.78 units | 0.012597 USD
|"+47"(Norway) | 2.80751 units | 0.0453412865 USD
|"+968"(Oman) | 2.94 units | 0.047481 USD
|"+92"(Pakistan) | 0.74536 units | 0.012037564 USD
|"+680"(Palau) | 4.3065 units | 0.069549975 USD
|"+507"(Panama) | 3.42036 units | 0.055238814 USD
|"+675"(Papua New Guinea) | 2.38514 units | 0.038520011 USD
|"+595"(Paraguay) | 0.87786 units | 0.014177439 USD
|"+51"(Peru) | 2.48452 units | 0.040124998 USD
|"+63"(Philippines) | 1.59009 units | 0.0256799535 USD
|"+48"(Poland) | 2.11184 units | 0.034106216 USD
|"+351"(Portugal) | 2.79923 units | 0.0452075645 USD
|"+1787"(Puerto Rico) | 0.4969 units | 0.008024935 USD
|"+974"(Qatar) | 2.39 units | 0.0385985 USD
|"+262"(Réunion Island) | 7.42 units | 0.119833 USD
|"+40"(Romania) | 3.66881 units | 0.0592512815 USD
|"+7"(Russia) | 1.60666 units | 0.025947559 USD
|"+250"(Rwanda) | 1.53 units | 0.0247095 USD
|"+290"(Saint Helena) | 7.32 units | 0.118218 USD
|(Saint Lucia) | 0.57972 units | 0.009362478 USD
|"+508"(Saint Pierre and Miquelon) | 4.14087 units | 0.0668750505 USD
|"+1784"(Saint Vincent and The Grenadines) | 0.28986 units | 0.004681239 USD
|"+685"(Samoa) | 1.86339 units | 0.0300937485 USD
|"+378"(San Marino) | 3.89241 units | 0.0628624215 USD
|"+966"(Saudi Arabia) | 1.85 units | 0.0298775 USD
|"+381"(Serbia) | 1.1346 units | 0.01832379 USD
|"+65"(Singapore) | 1.49071 units | 0.0240749665 USD
|"+421"(Slovakia) | 3.72678 units | 0.060187497 USD
|"+386"(Slovenia) | 1.32508 units | 0.021400042 USD
|(Solomon Islands) | 3.9918 units | 0.06446757 USD
|"+27"(South Africa) | 1.78 units | 0.028747 USD
|"+82"(South Korea) | 1.73916 units | 0.028087434 USD
|"+34"(Spain) | 3.72678 units | 0.060187497 USD
|"+94"(Sri Lanka) | 1.86339 units | 0.0300937485 USD
|"+249"(Sudan) | 8.26 units | 0.133399 USD
|"+597"(Suriname) | 0.99381 units | 0.0160500315 USD
|"+46"(Sweden) | 2.50937 units | 0.0405263255 USD
|"+41"(Switzerland) | 3.02283 units | 0.0488187045 USD
|"+963"(Syria) | 12.28 units | 0.198322 USD
|"+886"(Taiwan) | 2.22779 units | 0.0359788085 USD
|"+255"(Tanzania) | 2.09 units | 0.0337535 USD
|"+66"(Thailand) | 1.24226 units | 0.020062499 USD
|"+1868"(Trinidad and Tobago) | 1.71432 units | 0.027686268 USD
|"+90"(Turkey) | 1.16 units | 0.018734 USD
|"+993"(Turkmenistan) | 4.34791 units | 0.0702187465 USD
|"+1649"(Turks and Caicos Islands) | 2.31889 units | 0.0374500735 USD
|"+688"(Tuvalu) | 0.42 units | 0.006783 USD
|"+256"(Uganda) | 7.56 units | 0.122094 USD
|"+380"(Ukraine) | 3.859296 units | 0.0623276304 USD
|"+971"(United Arab Emirates) | 1.1 units | 0.017765 USD
|"+44"(United Kingdom) | 1.80542 units | 0.029157533 USD
|"+1"(United States) | 0.29814 units | 0.004814961 USD
|"+598"(Uruguay) | 4.96904 units | 0.080249996 USD
|"+998"(Uzbekistan) | 3.10565 units | 0.0501562475 USD
|"+678"(Vanuatu) | 2.65015 units | 0.0427999225 USD
|"+58"(Venezuela) | 2.03731 units | 0.0329025565 USD
|"+84"(Vietnam) | 4.08289 units | 0.0659386735 USD
|"+1340"(Virgin Islands, US) | 2.39 units | 0.0385985 USD
|"+681"(Wallis and Futuna) | 7.84 units | 0.126616 USD
|"+967"(Yemen) | 2.65 units | 0.0427975 USD
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
