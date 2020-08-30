+++
title = "Getting App Info"
weight = 4
pre = "<b>4.1 </b>"
+++

Now that we understand what an API is, how our backend is configured, and the basics of sending data between our frontend and backend, let's implement a simple workflow.

![simple-example](/img/simple-example.png)

**Scenario:** As a user, I want to get basic info about the application from the backend. 

Based on the above diagram, there are 3 things we have to do:
1. Create the API Gateway with the path `/info`.
2. Create the Lambda function called `infoFunction` that returns this information, and connect this to the API. 
3. Send a request to the API Gateway from our web application, and receive the info from the backend. 

**Let's try this in our application**

Run the following command:
```bash
amplify api add
```
**You will now be asked a series of questions by Amplify:**

1. Create the API Gateway with the path `/info`

   ```bash
   ? Please select from one of the below mentioned services: REST
   ? Provide a friendly name for your resource to be used as a label for this category in the project: mainAPI
   ? Provide a path (e.g., /book/{isbn}): /info
   ```

2. Create the Lambda function called `infoFunction`, and connect this to the API. 

   ```bash
   ? Choose a Lambda source: Create a new Lambda function
   ? Provide a friendly name for your resource to be used as a label for this category in the project: infoFunction
   ? Provide the AWS Lambda function name: infoFunction
   ? Choose the runtime that you want to use: NodeJS
   ? Choose the function template that you want to use: Serverless ExpressJS function (Integration with API Gateway)
   ? Do you want to access other resources in this project from your Lambda function? No
   ? Do you want to invoke this function on a recurring schedule? No
   ? Do you want to configure Lambda layers for this function? No
   ? Do you want to edit the local lambda function now? No
   Successfully added resource infoFunction locally.

   ? Restrict API access Yes
   ? Who should have access? Authenticated users only
   ? What kind of access do you want for Authenticated users? read
   ? Do you want to add another path? No
   ```
   
   You have just created a Lambda function called `infoFunction` that runs on a `NodeJS` environment (javascript language).
   
3. Edit the `infoFunction` Lambda function so it returns info about the application
   
   Open the file `amplify/backend/function/infoFunction/src/app.js`, and inspect the file. You will notice that Amplify has already created `GET`, `POST`, `PUT` and `DELETE` methods for the `info` resource. However, we are only concerned with the `GET` method of this resource. Look for this code block:
   
   ```javascript
   app.get('/info', function(req, res) {
     // Add your code here
     res.json({success: 'get call succeed!', url: req.url});
   });
   ```

   Replace that code with the following code. 
   
   ```javascript
   app.get('/info', function(req, res) {
     res.json({
      "message": "I created this application during the CCA x CISSA x AWS workshop event!"
     });
   });
   ```
   
   Save the file.
   
   You just edited the data that is being sent back from the backend. Now, if you send a GET request to '/info', you will receive the following payload in your      frontend:
   
   ```json
   {
     "message": "I created this application during the CCA x CISSA x AWS workshop event!"
   }
   ```
   
4. Push the function to the cloud by running the following command:
   ```bash
   amplify push
   ```
   
   While you are waiting, think about what you just did. You set up an API, a Lambda function, edited the Lambda function, and just pushed it to the cloud. 
   
   After the process is finished, let's see how this looks in the Amazon Console.
  
   1. Open the AWS console: https://console.aws.amazon.com/console/home
   2. Search up 'Lambda' in the main catalog search bar, and click the first option.
   3. Click on `infoFunction-dev`, and view the code of the function by scrolling down to `Function Code`. This is the Lambda function that you just pushed up to       the cloud. 
   4. Click on `Services` at the top, and search for `API Gateway`, and click on `mainAPI`. This is the API Gateway you just pushed to the Cloud. Notice the 'info' resource that you have just created. 
   

5. Connect our Web Application to the API Gateway to get the about info. 

   Open the file `src/api/db.js` - this file is responsible for retrieving and sending data to our API. 
   
   To connect to the API, we need to import a module provided by Amplify. This module allows us to easily communicate with the API. Add this to the top of your file:
   
   ```bash
   import { API } from 'aws-amplify';
   ```
   
   ### getAboutInfo() Function
   The function `getAboutInfo` is used to get the application info. To configure this function to send a request to our API Gateway, replace it with the following code:
   
   ```javascript
   export async function getAboutInfo() {
       const data = await API.get('mainAPI', '/info', {})
       return data.message
   }
   ```
   
   **Code Breakdown**
   - Uses API (the Amplify module that you imported) to send a `GET` request to `/info` in the `mainAPI` API that you configured. 
   - In doing this, the API gateway will call the `infoFunction` Lambda function that you previously created.
   - `infoFunction` will return a message back to the API, which will in turn send it back to our web application. 
   
4. Preview updated application.

   Congrats! Your web app now sends a request to the API gateway, and should receive the info that is returned by the Lambda. Open the browser tab where your app is being previewed, and you should see the info populated at the top of your application!
   