+++
title = "Creating the lambda"
weight = 1
pre = "<b>4.1 </b>"
+++

Let's create our lambda and give it the appropriate permissions.

1. From the aws console, search up **Lambda** in the search bar, and click on the first option. If you can't find it click [here](https://ap-southeast-2.console.aws.amazon.com/lambda/home?region=ap-southeast-2#/functions)

2. Click **Create function**

3. On the create function page:

<pre>
- Name your function <b>facial-detect</b>
- Set your runtime to <b>Python 3.8</b>
</pre>

4. Click **Create function**

![Lambda Image](/img/lambdaCreate.png)

5. Once created and inside the lambda, click into the **Permissions** tab (located at the top of the lambda). Under **Execution role** (the first section under the new tab) will be a role name, Click it.

6. In the newly opened window click on the blue button **Attach policies**. Using the search bar, search for the following policies, checking the boxes once you've found them.

```
- AmazonS3FullAccess
- AmazonRekognitionFullAccess
```

7. Once both policies have been checked, click **Attach policy**

***Make Note***

Before we put in the code let's just take a step back and understand what we just did. In steps 1-4 we created our lambda. But in 5, 6 and 7, we actually gave it the permissions to use other services. AWS's model of permissions is to grant rather than strip. This means that when you first create your lambda, the permissions that lambda has is very minimal and so what we did was grant it permission to s3 and rekognition through Identity Access Management. IAM is the central hub for all thing’s permissions, it where we are allowing our lambda to use other services.
