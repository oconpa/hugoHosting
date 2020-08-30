
+++
title = "Publishing our App"
weight = 6
pre = "<b>6. </b>"
+++

We've finished our application! However, one problem - our application is still running locally on our Cloud9 instance. 
The last step is to host our frontend website on the cloud, so it can be accessed ANYWHERE and ANYTIME, as long as you have an internet connection. 

To do this, run the following command, and follow the guided instructions

```bash
amplify hosting add

? Select the plugin module to execute: Hosting with Amplify Console
? Choose a type: Manual Deployment
```

Lastly, run the final command to publish your application

```bash
amplify publish
```

Congrats, you have just published your application! The console should output a **link** that you can click on to access your published website. You can access this website ANYWHERE - on your phone, laptop, iPad. You can send the link to your friends and get them to make an account!