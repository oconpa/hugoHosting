+++
title = "Connect to Web App"
weight = 3
pre = "<b>5.3 </b>"
+++

1. Setting up our file to talk to the API. 

   Currently, when we click 'Add' in our application, nothing happens. Let's change this.
   
   Open the file `src/api/db.js` - the file responsible for all the calls to the API from the frontend. 
   
   Since we need to connect to the API, we need the API module from the Amplify library - this is already imported. We also need to get the **username** of the currently authenticated user, so we also need to import the Auth module. To do this, add the import after the API module:
   
   Replace:
   ```javascript
   import { API } from 'aws-amplify';
   ```
   with
   ```javascript
   import { API, Auth } from 'aws-amplify';
   ```
   
   **This file has three empty functions: `getUserItems`, `getItem`, and `deleteItem`.** Let's add functionality to these functions.
   
2. ### getUserItems() Function
   This function is to fetch all the items of a specific user. Replace the function with the following code:

   ```javascript
   export async function getUserItems() {
       const userData = await Auth.currentAuthenticatedUser()
       const data = await API.get('mainAPI', '/items/' + userData.username, {})

       return data
   }
   ```
   
   **Code Breakdown**
   - Line 1: Gets the details of the currently authenticated user. We use this to get the logged-in user's username. 
   - Line 2: Sends a `GET` request to the `mainAPI` API you configured, with the resource `/items`, and returning only the data of the current user. 
   
3. ### addItem() Function
   This function is to add an item that a user created. Replace the function with the following code:
   ```javascript
   export async function addItem(itemName) {
       const userData = await Auth.currentAuthenticatedUser()

       const response = await API.post('mainAPI', '/items', {
           body: {
               timestamp: new Date().getTime(),
               user: userData.username,
               itemName
           }
       })

       return response
   }
   ```
   
   **Code Breakdown**
   - Sends a `POST` request to the `mainAPI` API you configured, with the resource `/items`. A `body` payload is also sent to the API, where we specify the data of  the new item we are creating. 
   
   
4. ### deleteItem() Function
   This function is to delete an item from a user's account. Replace the function with the following code:
   ```javascript
   export async function deleteItem(timestamp) {
       const userData = await Auth.currentAuthenticatedUser()
       const response = await API.del('mainAPI', '/items/object/' + userData.username + '/' + timestamp, {})

       return response
   }
   ```
   
   **Code Breakdown**
   - Sends a `DELETE` request to the `mainAPI` API you configured, with the resource `/items`. We specify the username and timestamp, as the combination of both will uniquely identify an item. 
   
5. Save the file, and push the changes to the cloud. 

   ```bash
   amplify push
   ```

5. Congrats! You have successfully setup a Dynamo DB Table, and hooked it up to your web application. 
   Open the browser tab where your app is being previewed, and you should be able to get, create and delete items!