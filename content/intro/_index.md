
+++
title = "Introduction"
weight = 1
pre = "<b>1. </b>"
+++

## What will we be building? 
We will be building a smart Shopping List web application!

**Demo**: https://dev.d2jld5htjwnhsz.amplifyapp.com

![app-screenshot](/img/AppScreenshot.png)


### Key Features

There are five main components to this application
1. **Frontend**
   - A clean website user interface for our shopping list application
   - Built using *React*, a framework for front-end development, enhancing the process of building user interfaces and websites.
     **NOTE**: As the focus of this workshop is AWS, we will be providing the majority of the frontend code (except the code required to *connect* this frontend to AWS).

2. **Authentication**
   - Ability to log-in, sign up, forget password - all basic 'authentication' operations. 
   - Ability to log-in with external providers, such as Google, Microsoft, Facebook, etc. 
   - You must be authenticated to make requests to the backend
3. **API + Backend**
   - API Gateway that acts as the 'front door' to the backend
   - Backend comprised of independent, serverless 'Lambda' functions
4. **Database**
   - Fetch all the items associated to a user
   - Ability to create a new item
   - Ability to delete an existing item
5. **BONUS:** Integration with other services
   - Use AI to recognise objects in images
   - Allow users to add these recognised objects

These 5 components are the **basis** of almost **every** application. **AWS Amplify** makes creating and connecting all these components an extremely simple and streamlined process. With these 5 components, the possibilities are endless - you will have the skills to create a forum, a task tracker, a basic social media platform, and so much more. We hope that after this workshop, you will use these core components to build something greater!
