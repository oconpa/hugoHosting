+++
title = "Provisioning Cognito"
weight = 1
pre = "<b>3.1 </b>"
+++


1. Add a new terminal in your Cloud 9 IDE by clicking `Window` and then `New Terminal`
   
   Change directory into your Amplify project. 
   ```bash
   cd AWSAmplifyWorkshop
   ```

2. Provision the Cognito authentication service.
    
   Run the following command, and follow the guided instructions:
   ```bash
   amplify auth add

   Do you want to use the default authentication and security configuration? Default configuration
   How do you want users to be able to sign in? Username
   Do you want to configure advanced settings?  No, I am done.
   ```    
    
   To push it to the Cloud, run the following command:

   ```bash
   amplify push
   ```
   
   You should see a 'status' section with 'auth' as a new component that you just created. Type 'Y' and hit enter to confirm this process.
   

**Amplify is now provisioning the authentication service (Cognito). You can move on to the next step (3.2) while you are waiting for this to finish.**
  