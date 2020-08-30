
+++
title = "Challenge Time: Adding AI"
weight = 7
pre = "<b>7. </b>"
+++

Challenge time! We've just created a fullstack web application using AWS Amplify, implementing authentication, a database, an API, and a Lambda backend. However, AWS Amplify is a LOT more powerful, and has many more plug-and-play modules that you can incorporate in your application. For example:

![amplify-features](/img/amplifyFeatures.png)

For our challenge, let's try and incorporate the **predictions** module in our shopping list application. Specifically, we will build a feature that allows users to upload photos, before using AI object recognition to label ALL of the entities within the image, and allowing the user to add those 'labels' within their shopping list. Here is a demo of the finished product: 

![ml-feature](/img/MLFeature.gif)

A few pointers: 
- Your web application should DIRECTLY connect to Amplify's Prediction service in the file: `src/api/predictions.js`
- Read the documentation as to how you should implement this: https://docs.amplify.aws/lib/predictions/label-image/q/platform/js
- Good luck! 