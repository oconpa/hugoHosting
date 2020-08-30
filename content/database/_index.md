+++
title = "Connecting to a Database"
weight = 5
pre = "<b>5. </b>"
+++

AWS Amplify uses AWS DynamoDB as its database service - a serverless, NoSQL database solution that supports key-value and document data structures. 

### How will we design our database?
![database-design](/img/tableDesign.png)

The above diagram is the design for our applications' database. Columns include:

1. `user`: Each user should have their own items. This column would allow us to display only the items relevant to a specific user. 
2. `timestamp`: Tracks the exact time in which items are created. This column allows us to sort the table by creation time. 
3. `itemName`: The name of the item being created. 

DynamoDB tables require a **primary key** to uniquely identify each item in the table. A **primary key** can be a single column, OR, a combination that includes a partition key and a sort key. For our table:

1. **Partition Key** is `user`. This allows us to **partition** our queries based on the `user` column, so we can display items relevant to only the logged-in user. 
2. **Sort Key** is `timestamp`. This allows us to **sort** our table based on creation time. 

### How do we implement this?

![database-flow](/img/database-flow.png)

**There are three steps to implement this:** 

1. Create the database.
2. Create a new Lambda function (`databaseFunction`) specifically for interact with our database. 
3. Update the API with new paths, and connect it to our Web App.