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

![CORS Image](/img/cors.png)
   
**That's it, you've now set up a suitable space to save both your images and detections of those images to be later used in the app. Now let's look at the backend.** 