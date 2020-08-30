+++
title = "Create the Database"
weight = 1
pre = "<b>5.1 </b>"
+++

1. Create the Dynamo DB Table
   
   Run the following command, and follow the guided instructions
   ```javascript
     amplify storage add
    
     ? Please select from one of the below mentioned services: NoSQL Database

     Welcome to the NoSQL DynamoDB database wizard
     This wizard asks you a series of questions to help determine how to set up your NoSQL database table.

     ? Please provide a friendly name for your resource that will be used to label this category in the project: items
     ? Please provide table name: items

     You can now add columns to the table.

     ? What would you like to name this column: user
     ? Please choose the data type: string
     ? Would you like to add another column? Yes
     ? What would you like to name this column: timestamp
     ? Please choose the data type: number
     ? Would you like to add another column? Yes
     ? What would you like to name this column: itemName
     ? Please choose the data type: string
     ? Would you like to add another column? No

     ? Please choose partition key for the table: user
     ? Do you want to add a sort key to your table? Yes
     ? Please choose sort key for the table: timestamp

     ? Do you want to add global secondary indexes to your table? No
     ? Do you want to add a Lambda Trigger for your Table? No
    ```
    
    Push the DynamoDB Table to the cloud by running the following command:
   ```bash
   amplify push
   ```

2. View the database in the AWS console

   In the AWS console, search for DynamoDB or [click this](https://ap-southeast-2.console.aws.amazon.com/dynamodb/home?region=ap-southeast-2).
  
   Click on "tables" on the left then `items-dev`. This is the table you just pushed to the Cloud.
  
   You can click on the "Items" tab to see the data. Currently, it should be empty.  