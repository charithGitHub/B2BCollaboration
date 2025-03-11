# ASP.NET Core Web App with Azure Entra ID B2B Authentication

This project demonstrates how to integrate and configure **Azure Entra ID B2B** authentication in an **ASP.NET Core Web Application**.

## 🚀 Features

- Authenticate users using Azure Entra ID B2B (formerly Azure AD B2B)
- Secure API endpoints with OpenID Connect & Microsoft Identity Web
- Protect application routes using authentication middleware
- Supports external B2B guest users

## 🛠 Prerequisites

- .NET 6 or later
- An **Azure Entra ID** tenant
- A registered **Azure Entra ID application**
- Visual Studio or VS Code

---

## 📌 Register the Application in Azure Entra ID

1. **Sign in** to [Microsoft Entra Admin Center](https://entra.microsoft.com).
2. Navigate to **Azure Active Directory** → **App registrations**.
3. Click **New registration**.
4. Configure the app:
   - **Name:** `MyAspNetCoreApp`
   - **Supported account types:** `Accounts in this organizational directory only` (or **Multitenant** if needed).
   - **Redirect URI:** `https://localhost:5001/signin-oidc`
5. Click **Register** and copy the **Client ID** & **Tenant ID**.

### 🔐 Configure Authentication

6. Go to **Authentication** → Add platform → **Web**.
7. Set **Redirect URI** to `https://localhost:5001/signin-oidc`.
8. Enable **ID tokens** under Implicit grant.
9. Click **Save**.

### 🔑 Create Client Secret

10. Go to **Certificates & secrets** → **New client secret**.
11. Copy the secret value **(store it securely)**.


## 📂 Step 2: Configure ASP.NET Core Web App

### 🛠 Install Dependencies

Run the following commands in the terminal:

```sh
dotnet add package Microsoft.AspNetCore.Authentication.OpenIdConnect
dotnet add package Microsoft.Identity.Web
dotnet add package Microsoft.Identity.Web.UI
```

### ⚙ Configure `appsettings.json`

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "YOUR_TENANT_ID",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientSecret": "YOUR_CLIENT_SECRET",
    "CallbackPath": "/signin-oidc"
  }
}
```



