+++
title = "Enabling CORS"
weight = 2
pre = "<b>3.2 </b>"
+++

1. Click on the bucket you just created, clicking on the **Permission** tab from within the bucket. You should then see four sub options, go to **CORS configuration** and paste the following code:

```html
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
<CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>PUT</AllowedMethod>
    <AllowedHeader>*</AllowedHeader>
</CORSRule>
</CORSConfiguration>
```

2. Click **Save**

![CORS Image](/img/CORS.png)

**Hang on a second! What's CORS?**

**Cross-origin resource sharing**, CORS, is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served. Think of it as a **firewall or blockade**. When you create and expose your API, you don't want some random website accessing the API you built specifically for your site. With CORS you can specify the specific sites you want to have access to your API securely, and blocking any unauthorised sites.

What we've done on the bucket is allow webpages to perform actions on our bucket, in this case, allowing those with the presigned URL to **PUT** objects into the bucket.
   
**And that's it, you've now set up a suitable space to save both your images and detections of those images to be later used in the app. Now let's look at the backend.** 