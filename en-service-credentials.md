---

copyright:
  years: 2020, 2021
lastupdated: "2021-01-12"

keywords: app-configuration, app configuration, service credentials, authentication

subcollection: app-configuration

---

{:codeblock: .codeblock}
{:external: target="_blank" .external}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:tip: .tip}

# Authenticating with service credentials
{: #ac-service-credentials}

You can generate a new set of credentials for cases where you want to manually connect an app or external consumer to an {{site.data.keyword.cloud_notm}} service. Credentials are provided in JSON format. The JSON snippet lists credentials, such as the API key and secret, as well as connection information for the service.
{: shortdesc}

Services that are managed by {{site.data.keyword.iamlong}} (IAM) can generate a resource key, also known as a credential. Credentials are service-specific and vary based on how each service defines the credentials they need to generate. A credential might contain a user name, password, host name, port, and a URL.

Click **Service credentials** to view the existing credentials with the **Key name** and **Date created** or create a new one.

For more information on adding and viewing a service credential, see [here](/docs/account?topic=account-service_credentials){: external}.

