+++
title = "Connecting to App"
weight = 2
pre = "<b>3.2 </b>"
+++

1. Add a login and signup page to our Web Application (while we are waiting for the service to be provisioned).
   
   Open the file `src/index.js`, and import the Authenticator module by adding the following code **after the rest of your imports**. This module includes the UI components for our login and sign up page:
   
   ```javascript
   import { AmplifyAuthenticator } from '@aws-amplify/ui-react';
   ```
   
   In the same file, surround the `<App />` tag with the `<AmplifyAuthenticator>` tag. 
   Essentially, replace `<App />` with the following code:
   
   ```javascript
    <AmplifyAuthenticator>
      <App />
    </AmplifyAuthenticator>
    ```
    
   Any content you surround `<AmplifyAuthenticator>` with will require authentication / users to log-in. As such, when users try to access the application, they will be redirected to a login page if they are unauthenticated. 
   
2. Add a log out button.
   
   Open the file `src/components/NavBar.js`, as the log-out button is located in the Navigation Bar. 
   
   We need to import an authentication module that will allow us to perform tasks related to authentication, including sign-out. Add this to the top of your code:
   
   ```javascript
   import { Auth } from 'aws-amplify';
   ```
   
   Look for the Log out button, and replace the 'onClick' function with the following code:
   ```javascript
   onClick={async ()=>{
       await Auth.signOut();
   }}
   ```
    
3. Preview updated application.
   
   If Amplify is finished pushing the authentication service to the cloud, open the tab where your application is being previewed. You should now see a login screen! Follow the on-screen instructions to make an account, verify your email, and then login. 
   
   Let's see what you just did in the Amazon Console.
  
   1. Open the AWS console: https://console.aws.amazon.com/console/home
   2. Search up 'Cognito' in the main catalog search bar, and click the first option.
   3. Click 'Manage user pools'.
   4. Click your Amplify project.
   5. Click 'Users and Groups' under 'General Settings'. 
   
   You should see the account you just made.
   
**Congrats! You have just set up an Authentication service, and connected it to your web application.** 