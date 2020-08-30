
+++
title = "Running the Web App"
weight = 2
pre = "<b>2.2 </b>"
+++

___

1. Clone the current repository to your Cloud9 IDE
   
   ```bash
   git clone -b frontendOnly https://github.com/josephtey/AWSAmplifyWorkshop.git
   ```
   
2. Move into the cloned directory, and install all required packages. 

   ```bash
   cd AWSAmplifyWorkshop
   npm install
   ```
   
3. Install the Amplify CLI and initialise the project (as an Amplify app)
   ```bash
   npm install -g @aws-amplify/cli
   ```

4. Initialise the project as an Amplify application

   ```bash
   amplify init
   
   ? Enter a name for the project: AWSAmplifyWorkshop
   ? Enter a name for the environment: dev
   ? Choose your default editor: None
   ? Choose the type of app that youre building: javascript
   
   Please tell us about your project
   ? What javascript framework are you using: react
   ? Source Directory Path: src
   ? Distribution Directory Path: build
   ? Build Command:  npm run-script build
   ? Start Command: npm run-script start
   
   AWS access credentials can not be found.
   ? Setup new user (Y/n) Yes
   
   Press Enter (you dont need to click the link for this one)
   
   Specify the AWS Region
   ? region:  ap-southeast-2
   Specify the username of the new IAM user:
   ? user name:  amplify-workshop
   Complete the user creation using the AWS console
   
   Click on the link that is provided
   ```
   
   You will get a link to configure your Identity Access Management user.\
   Click on it, keep clicking 'Next' and leave everything default until you reach 'Create User'.\
   Click 'Download .csv' to save your User Credentials.
   
   Go back to your Cloud9.\
   Your `accessKeyId` and `secretAccessKey` will be in the CSV file that you just downloaded.
   
   ```bash
   ? accessKeyId: ********************
   ? secretAccessKey:  ****************************************
   ? region:  ap-southeast-2
   ? Profile Name:  default
   
   Successfully set up the new user.
   For more information on AWS Profiles, see: https://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html
   
   ? Do you want to use an AWS profile? Yes
   ? Please choose the profile you want to use: default
   ```
   After this step, some deployment resources are created in AWS including an S3 bucket (for deployment) and IAM roles.

5. Connect your React web app to Amplify.

   On sidebar in the Cloud9 interface, expand the AWSAmplifyWorkshop folder and open the file `src/index.js`. Add the following code **after the import statements**:
   
   ```javascript
   import config from './aws-exports'
   import Amplify from 'aws-amplify'
   Amplify.configure(config)
   ```
   Save the file.

6. Run the React application locally
   ```bash
   npm start
   ```
   
7. Preview your Web Application
   
   After the app has compiled successfully, click 'Tools' in the toolbar up top, click 'Preview' and finally click 'Preview Running Application'. 
   Open the preview in another tab by clicking the arrow / box button on the right of the search bar. 

**You should see a basic Shopping List app in your browser! However, there is currently no functionality. Let's use AWS to fix this.**