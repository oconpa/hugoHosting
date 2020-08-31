
+++
title = "Introduction"
weight = 1
pre = "<b>1. </b>"
+++

## What will we be building? 
We will be building a ML face detection gallery app!

**Demo**: http://facial-hosting.s3-website-ap-southeast-2.amazonaws.com/

![app-gif](/img/DEMO.gif)

### Key Features

There are five main components to this application
1. **Frontend**
   - A simple three paged web app made up of a home page, upload page and gallery.
   - Built using ***React***, a framework for front-end development, enhancing the process of building user interfaces and websites.
   
   >**NOTE**: As the focus of this workshop is AWS, we will be providing the majority of the frontend code (except the code required to *connect* this frontend to AWS).

2. **Lambda (Backend)**
   - The backbone to the website where all the logic for the sites happens. 
   - Its made of of five routes (each will be explained further in depth later in the workshop) providing functionality to the app.

3. **API Gateway**
   - API Gateway acts as the 'front door' to the backend.
   - It creates URL links that allow us to channel data to the lambda backend and return information back, if we need, to the frontend.
   
4. **S3**
   - S3 is amazons general storage space.
   - Similar to your computers file system, on s3 you can store any type of file.

5. **Rekognition**
   - The backbone to Amazon's machine learning.
   - Easily communicate with rekognition through the aws sdk seelcting from a range of ml models.

With a rising potential on what machine learning has to offer, AWS offers an easy plug-n-play module to integrate machine learning services very easily. Machine learning can help your applications stand out and deliver a more personlised experience for your users. 
