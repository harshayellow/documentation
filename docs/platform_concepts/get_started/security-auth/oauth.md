---
title: Single sign-on with OAuth & SAML for Cloud Platform
sidebar_label: SSO with OAuth & SAML
---

## Overview

### OAuth

OAuth is an authentication protocol that supports Single Sign-On (SSO) and streamlines user access across various applications within an organization. SSO with OAuth enables your users to access the Yellow.ai platform using their existing application login credentials, eliminating the need to re-enter them. This approach enhances security by enabling secure third-party access to user data without exposing login details, providing a seamless and efficient authentication process.

**Benefits of signing in through OAuth:**

* Eliminates the need for direct sharing of login credentials, enhancing security.
* You can control and limit third-party access to your data.
* Proves adaptable to various scenarios in large-scale systems.

### SAML

SAML (Security Assertion Markup Language) is an open standard for enabling single sign-on (SSO) across applications and services. It allows users to authenticate once with an Identity Provider (IDP) and gain access to multiple service providers without repeated logins. This improves user experience and enhances security on the Yellow.ai platform by centralizing authentication.

**Benefits of SAML Authentication:**

* Reduces the risk of phishing attacks and password vulnerabilities by eliminating the need for multiple passwords.
* Enables users to log in once and access multiple applications without interruption.
* Simplifies and centralizes user management by delegating authentication to a trusted IDP.

### SSO Workflow

![image](https://imgur.com/1ufEPQS.png)

### Basic Terminology

| Term | Description |
| :------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Resource owner** | The organization that wants to log in to Yellow.ai. |
| **Client** | Yellow.ai |
| **Authorization server** | The server issuing the access token, in this case, your application. |
| **Resource server** | The application that accepts the access token and must verify its validity. |
| **Redirect URI** | This URL is where the Authorization Server sends the user back after granting permission to the Yellow.ai client. |
| **Response type** | The type of information the Client (Yellow.ai) expects to receive. For this case, the Response Type will be "code" indicating an Authorization Code. |
| **Grant type** | Refers to the way an OAuth application gets the access token. In this case, the authorization code flow will be used. |
| **Scope** | Granular permissions the Client (Yellow.ai) wants, such as access to data or to perform actions. For this case, `openid`, `profile`, and `email` are required scopes. |
| **Consent** | The Authorization Server verifies with the Resource Owner (user) whether they want to give the Client (Yellow.ai) permission. |
| **Client ID** | A unique identifier for the client application, provided by the Authorization Server to the Client (Yellow.ai). |
| **Client secret** | A secret key used for authentication, provided by the Authorization Server to the Client (Yellow.ai). |
| **Authorization code** | A short-lived temporary code the Client (Yellow.ai) gives the Authorization Server in exchange for an Access Token (valid for one-time use with a maximum lifetime of 10 minutes). |
| **Access token** | The key used by the Client (Yellow.ai) to communicate with the Resource Server. Similar to a badge or key card, it grants permission to request data or perform actions with the Resource Server on behalf of the Client (Yellow.ai). |
| **OAuth application** | The entity created by the Authorization Server containing details (such as Client ID, Client Secret, Redirect URL, etc.) corresponding to a specific OAuth client. |

## Configure OAuth Sign-in

To configure OAuth, follow the steps below:

### Step 1: Set up OAuth in IDP

To set up OAuth, you need to create an OAuth application on your Authorization Server. Here are the steps:

#### Create an OAuth Application

1.  Log in to your Authorization Server.
2.  Click on the "Applications" or "OAuth Applications" tab.
3.  Click on the "Create Application" or "New Application" button.
4.  Fill in the required information, such as:
    * Application name
    * Application description
    * Redirect URI (the URL where the user will be redirected after authorization)
    * Client ID (a unique identifier for your application)
    * Client secret (a secret key used for authentication)
5.  Choose the authorization flow that you want to use (e.g., authorization code flow).
6.  Choose the scopes that you want to request (e.g., `openid`, `profile`, `email`).
7.  Click on the "Create" or "Save" button to create the application.

#### Configure the OAuth Application

1.  Note down the Client ID and Client secret. You will need these values to configure OAuth in your Yellow.ai application.
2.  Configure the Redirect URI to point to the URL where you want the user to be redirected after authorization.
3.  Configure the scopes to request the necessary permissions from the user.
4.  Whitelist the following redirect URLs on your IDP's OAuth app:
    * `https://cloud.yellow.ai/api/sso/oauth/handle-redirect`
    * `https://app.yellow.ai/api/sso/oauth/handle-redirect`

#### Example Configuration

Here is an example of how you might configure the OAuth application:

| Field | Value |
| :-------------------- | :------------------------------------ |
| Application name | My Yellow.ai Application |
| Application description | This is my Yellow.ai application |
| Redirect URI | `https://my-yellow-ai-app.com/callback` |
| Client ID | `client-id-123456` |
| Client secret | `client-secret-123456` |
| Authorization flow | Authorization code flow |
| Scopes | `openid`, `profile`, `email` |

Steps to **retrieve details** from a few **common identity providers** are outlined below:

| Identity provider | Values required to set up SSO for Yellow.ai | Step-by-step guide |
| :---------------- | :------------------------------------------ | :----------------- |
| **Okta** | Okta domain <br/> Client ID <br/> Client Secret | [Click here](https://developer.okta.com/docs/guides/implement-oauth-for-okta/main/#create-an-oauth-2-0-app-in-okta) |
| **Red Hat** | Realm <br/> Client ID | [Click here](https://access.redhat.com/documentation/en-us/red_hat_single_sign-on/7.0/html/server_administration_guide/clients#oidc_clients) |
| **Google** | Client ID <br/> Client Secret | [Click here](https://support.google.com/cloud/answer/6158849?hl=en) <br/> <br/> **Note**: Select **`openid`**, **`userinfo.email`**, and **`userinfo.profile`** under scopes on the [Create Consent Screen](https://console.cloud.google.com/apis/credentials/consent?pli=1). |
| **Microsoft Azure AD** | Client ID <br/> Client Secret <br/> Tenant ID <br/> Tenant Domain | <details> <summary>**Click here**</summary><div> 1. Sign in to Azure AD. Click on **App Services** and select **Manage Azure Active Directory**. <br/> <br/> 2. In the left navigation, go to **App registrations** and click **New registration**. <br/> <br/> 3. On the registration page, provide application details. Choose **web** as the Redirect URI and input the redirect URLs. <br/> <br/> 4. Click **Register**. Azure AD will assign a unique Application ID (Client ID) to your application. Copy the Application ID and Directory ID (Tenant ID). <br/> <br/> 5. Navigate to **Certificates & Secrets**, click **New Client Secret**. Enter a description, set expiration, and click **Add**. This will be your Client Secret key. </div> </details> |
| **SAML integration** | IDP Name <br/> IDP description <br/> IDP login URL <br/> Entity ID <br/> Email domain <br/> IDP Certificate (in Certificates) | |

Watch this video on how to configure your identity provider (**Microsoft Azure AD**) and fetch details for Yellow.ai SSO configuration:

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/VmhHpo5FeYI?si=CmNdYqjbtM2NJ38E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></center>

:::note
If your identity provider isn't configured in Yellow.ai for SSO, share OAuth details directly with [Yellow.ai's support team](mailto:support@yellow.ai).
:::

#### Configure Okta for SAML Integration with Yellow.ai

To enable Single Sign-On (SSO) using Okta, follow the steps below to configure your Okta application with the appropriate SAML settings required by Yellow.ai.

##### Prerequisites

* Admin access to your Okta dashboard
* SAML configuration details provided by Yellow.ai, including:
    * **Single Sign-On (SSO) URL**
    * **Relay State** (optional)

#### Step 1: Access the Okta Admin Console

1.  Sign in to your Okta Admin Console.
2.  From the left sidebar, navigate to **Applications**.

#### Step 2: Create or Select an App

##### If no app is configured yet:

1.  Click **Create App Integration**.
2.  Choose **SAML 2.0** as the sign-in method.
3.  Click **Next**.

##### If an app is already available:

* Select the existing application you want to configure for Yellow.ai.

#### Step 3: Configure SAML Settings

##### When creating an app

1.  Enter a recognizable **App Name** (e.g., *Yellow.ai Integration*).
2.  Upload an optional logo if needed, then click **Next**.
3.  In **Single sign-on URL**, enter the URL provided by Yellow.ai (`https://cloud.yellow.ai/api/sso/oauth/handle-redirect`).
4.  **Check** the option:
    **✔ Use this for Recipient URL and Destination URL**
5.  In **Default Relay State**, paste the value provided by Yellow.ai (if available).

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/editsaml.png)

6.  In **Attribute statements**, add *Firstname* and *Email* attributes.

    ![](https://i.ibb.co/35jGCd3h/image-13.png)

##### When updating an existing app

If your Okta app is already set up:

1.  Go to **Applications** and select the relevant app.
2.  Under the **General** tab, click **Edit** and update the **Single sign-on URL** with the Yellow.ai URL.
3.  Navigate to the **Sign On** tab and click **Edit**.
4.  Replace the **Default Relay State** with the value shared by Yellow.ai.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/okta.png)

#### Step 4: Save the changes in Okta.

---

### Step 2: Share OAuth Setup Details

Once you have set up your IDP, share the following details (fetched from your identity provider) with our support team at [support@yellow.ai](mailto:support@yellow.ai):

| Field | Description |
| :---------------- | :--------------------------------------------------------------------------------------------------------- |
| **Email** | Your email address associated with the platform. |
| **API Version** | The version of the OAuth API being used. Ensures compatibility between the platform and the OAuth service. |
| **Scope** | The extent of access requested. Specifies resources or actions the application seeks permission to access. |
| **Domain** | The domain name configured for OAuth, used to identify and access the platform. |
| **Client ID** | A unique identifier assigned by the OAuth provider to recognize and authorize the application. |
| **Tenant ID** | Identifies the instance or organization within the OAuth provider, relevant for multi-tenant systems. |
| **Auth URL** | URL where users are redirected for authentication and authorization. |
| **Token URL** | URL where the platform obtains the OAuth access token after user authentication. |
| **Token scope** | Defines the level of access the access token has. |
| **User Info URL** | URL to retrieve additional information about the authenticated user. |
| **Client Secret** | A secret known only to the application and the OAuth provider for authentication during token requests. |

After verifying your details, SSO will be enabled for your domain by the Yellow.ai team.

### Step 3: Sign in Using OAuth

1.  Log in to `cloud.yellow.ai`.
2.  Enter the domain name configured for OAuth by the Yellow.ai support team. Click the **Sign with OAuth** button.
    ![image](https://imgur.com/OJSsVu6.png)
3.  You will be redirected to the third-party tool, where you can log in using its credentials to access the Yellow.ai platform.
    ![image](https://imgur.com/aUpX9WM.png)

### Step 4: Create Your Bot

Once OAuth is enabled, [create a bot](https://docs.yellow.ai/docs/platform_concepts/get_started/createfirstbot). In the URL, locate and copy the `botId` (separate for live/production). This `botId` is required for providing access and assigning roles.

![image](https://imgur.com/TDLTqpA.png)

---

## Role-based Access Through OAuth

The Yellow.ai platform supports various user roles, such as developer, agent, and admin. You can configure different roles within your OAuth app and assign users to each role as per your requirement.

To enable role-based access for your OAuth setup, follow these steps:

> **Prerequisite:** Configure OAuth sign-in and fetch your bot ID.

### Step 1: Add User Roles in IDP

Add roles in your respective identity provider app. The following are the **supported user roles** on the Yellow.ai platform:

* **Admin** (Bot admin)
* **Agent** (Inbox agent)
* **Developer** (Developer)
* **InsightsUser** (Insights user)
* **EchoAdmin** (Inbox admin)
* **Approver**
* **Tester**
* **Database** (Database viewer)
* **EngagementAdmin** (Engage admin)
* **EngagementUser** (Engage viewer)

:::note
The **Super admin** role is automatically created and assigned to the primary email address of the bot when the bot is created. It cannot be assigned through role mapping or the Yellow.ai UI.
Learn more about other user roles [here](https://docs.yellow.ai/docs/platform_concepts/get_started/add-bot-collaborators#user-roles-and-access).
:::

**Syntax to add user roles in the identity provider app**: `botId.{role}`
> **Example**: `x1599503999999.admin`

**Syntax to provide table and read/write access to database users:**

* **For App and Cloud (legacy tables)**: `botId.database.{tableName}.{accessType}`
* **For Cloud (v2 tables)**: `botId.database.{tableName}:v2.{accessType}`

:::info
`accessType` can have one of the following values:
* `read` for viewing the respective `tableName`. Ex: `x1599503999999.database.feedback.read`, `x1599503999999.database.users.write`
* `write` for performing editing operations on the respective `tableName`. Ex: `x1599503999999.database.users:v2.read`, `x1599503999999.database.feedback:v2.write`
:::

### Step 2: Assign Users to Roles in IDP

Once the roles are added to your IDP, you can assign users to each role. Steps to add user roles differ for each identity provider; follow the steps mentioned by the provider itself. For example, [this guide is for Microsoft Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps).

The following video demonstrates how to assign users to a user role in Microsoft Azure AD.

<iframe width="560" height="315" src="https://www.youtube.com/embed/yBu2HbQDuJA?si=qZJ2RP-t1QbevrNp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

:::note
If your identity provider isn't configured in Yellow.ai for SSO, share OAuth details directly with [Yellow.ai's support team](mailto:support@yellow.ai).
:::

### Step 3: Share User Role Details with Yellow.ai

Share the following information with the support team at `support@yellow.ai`:

* **OAuth details** if the identity provider is not configured in Yellow.ai for SSO.
* **Roles or groups** created in user details (retrievable on Yellow.ai platform through the `/userinfo` endpoint). Also, share the **key** associated with passing role values. Refer to the legend below for the correct role attribute based on your identity provider:

| Identity Provider Type | Role Attribute |
| :--------------------- | :------------- |
| Azure Active Directory | Roles |
| Okta | Groups |
| Auth0 | As configured on the identity provider (dynamic value) |
| Ping Identity | As configured on the identity provider (dynamic value) |

#### Testing What User Details Are Retrieved from Your OAuth Using the `/userinfo` Endpoint

To know what user details are retrieved by the SSO, make an API request to the GET `/userinfo` API.

The JSON response includes the following data: `email`, `roleAttribute`, and `given_name`. If a user is assigned to multiple roles across various AI agents, you will observe the list of role attributes along with their associated bots presented as an array within the `roleAttribute` field, as demonstrated in the following response.

```json
{
  "email": "something@domain.com",
  "family_name": "Steve",
  "given_name": "Smith",
  "roleAttribute": ["x1597777777777.admin", "x1597777777777.agent", "x1607777777777.admin", "x1607777777777.developer"]
}
````

:::note
Once OAuth role mapping is enabled, the role update UI (Settings \> Access control) on the Yellow.ai platform will be disabled. Roles can only be updated from the identity provider, and users will be assigned updated roles at the time of login.
:::

```
