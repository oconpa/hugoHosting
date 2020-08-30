+++
title = "Create the Lambda function"
weight = 2
pre = "<b>5.2 </b>"
+++

For the Lambda function we are creating, we will use a **function template** provided by Amplify specifically for database interactions.
    
It is called the `CRUD function for DynamoDB (Integration with API Gateway)`, where `CRUD` stands for **Create, Read, Update and Delete**. This means that it has pre-built functions for creating, reading, updating and deleting items within the database. 

![crud-template](/img/CRUDTemplate.png)

1. Create the Lambda function called `databaseFunction` to interact with the DynamoDB Table, and hook it up to the API. 
    
    Firstly, let's add a new path to our API gateway. As all of the paths for `databaseFunction` begin with `/items`, we only need to add one more path to our `mainAPI` API.
    
    ```bash
    amplify api update
    
    ? Please select from one of the below mentioned services: REST
    ? Please select the REST API you would want to update mainAPI
    ? What would you like to do: Add another path
    ? Provide a path (e.g., /book/{isbn}): /items
    ```
    
    Secondly, let's setup the `databaseFunction` Lambda function that uses the CRUD template.
    
    ```bash
    ? Choose a Lambda source: Create a new Lambda function
    ? Provide a friendly name for your resource to be used as a label for this category in the project: databaseFunction
    ? Provide the AWS Lambda function name: databaseFunction
    ? Choose the runtime that you want to use: NodeJS
    ? Choose the function template that you want to use: CRUD function for DynamoDB (Integration with API Gateway)
    ? Choose a DynamoDB data source option: Use DynamoDB table configured in the current Amplify project
    ? Choose from one of the already configured DynamoDB tables: items
    ? Do you want to access other resources in this project from your Lambda function? No
    ? Do you want to invoke this function on a recurring schedule? No
    ? Do you want to configure Lambda layers for this function? No
    ? Do you want to edit the local lambda function now? No
    
    ? Restrict API access Yes
    ? Who should have access? Authenticated users only
    ? What kind of access do you want for Authenticated users? create, read, update, delete
    ? Do you want to add another path? No
    ```
    
    Open the file `amplify/backend/function/databaseFunction/src/app.js`, and inspect the file. Scrolling through it, you should notice the CRUD paths that have been automatically generated (same as the diagram). 
    
    Push the Lambda function and the API Gateway with the updated path to the cloud by running the following command:
    ```bash
    amplify push
    ```

2.  View the Lambda function in the AWS console

    In the AWS console, search for Lambda or [click this](https://ap-southeast-2.console.aws.amazon.com/lambda/home?region=ap-southeast-2).
  
    Search for the function `databaseFunction-dev`. This is the function you just pushed up to AWS.