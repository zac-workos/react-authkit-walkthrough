# WorkOS AuthKit Example Application Setup Guide

## ✅ Prerequisite Setup

- **Create a WorkOS Account**  
  [https://dashboard.workos.com/signup](https://dashboard.workos.com/signup)

- **Create an Okta Dev Sandbox Account**  
  > 💡 You can use any identity provider. If your company has an internal IDP, feel free to use it here to model what customers would do to set up SSO/SCIM.
  - [https://developer.okta.com/signup/](https://developer.okta.com/signup/)
  - Ensure you have at least one user in your Okta tenant for testing SSO  
    _(Avoid using public email domains like Gmail/Yahoo. Use a company domain if possible.)_

- **Clone the WorkOS React Quickstart App**  
  [https://github.com/zac-workos/react-authkit-walkthrough](https://github.com/zac-workos/react-authkit-walkthrough)
  ```bash
  npm i
  npm run dev
  ```
  Make sure the app builds and starts properly.

## 🛠️ Dashboard Setup

- **Dashboard Config**
  - Add this redirect URI to your WorkOS dashboard:  
    `http://localhost:5173`
    
   > ![Screenshot 2025-02-25 at 3 17 41 PM](https://github.com/user-attachments/assets/68ba4bb3-7585-4fc7-83f1-b80d6657a9bf)
  - Go to the **Authentication** page → Click **Configure CORS**  
  - Add `http://localhost:5173` to allowed origins and click "Save".


      > ![Screenshot 2025-02-25 at 3 18 52 PM](https://github.com/user-attachments/assets/50706fa3-c301-4c17-8c70-d363471976ad)


  - Navigate to **API Keys** and copy your *Client ID*

    > ![Screenshot 2025-02-25 at 3 22 07 PM](https://github.com/user-attachments/assets/88020b66-2bf0-4c90-b071-d7f0267bf35b)

   - Rename `.env.local.example` to `.env.local`
   - Paste your Client ID into the `.env.local` file

      > ![Screenshot 2025-02-25 at 3 22 59 PM](https://github.com/user-attachments/assets/5dbcc1cb-9b93-4a34-94a7-e8138931c339)


  - Go to the **Organizations** tab and create an organization

      > ![image (2)](https://github.com/user-attachments/assets/4e97f991-9d6f-4221-b028-b3e70d41b9ac)

   - Add a domain (use your Okta dev sandbox domain)
   - Make sure to create a user under this domain in Okta (admin role is fine)

- **Configure Organization Domain Policy**

   > ![image (4)](https://github.com/user-attachments/assets/20cce009-a30a-484e-807d-28578e973ff0)

  - Adjust authentication policies for your org/domain as needed
  - Enable SSO once the connection is available
  - Enable/disable additional authentication methods via the **Authentication** tab

- **Set Up Okta (or other IDP) SSO**
  - Go to your organization in WorkOS
  - Click **Invite Admin**
    - Select features (just SSO for this lab)
  - Click **Next** → **Copy Setup Link**  
    > This is what customers would use to configure SSO/SCIM with your app
    ![Screenshot 2025-02-25 at 3 24 24 PM](https://github.com/user-attachments/assets/09aa7156-8963-4475-b605-1c7be27fbfa0)


  - Paste the link in your browser to begin the SSO setup
     > ![Screenshot 2025-02-25 at 3 24 49 PM](https://github.com/user-attachments/assets/87254806-d8fe-4ebd-b3bb-2e6a084cdf05)


- **Brand Authkit**
  - Navigate to the **Branding** tab in the WorkOS Dashboard
  - Customize the login widget (logos, colors, etc.)
  - Optionally enable the split panel and add your own HTML/CSS
     > ![Screenshot 2025-02-25 at 3 25 43 PM](https://github.com/user-attachments/assets/f410e675-e102-418f-86c9-0c58fb38d9e4)


- **Test the Login Flow**
  - Test SSO by using an email address from your Okta domain
  - Test other login methods (email/password, social logins, etc.)
