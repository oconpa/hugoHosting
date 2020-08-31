
+++
title = "Connecting our App"
weight = 6
pre = "<b>6. </b>"
+++

Awesome we're now ready to start connecting up our service with the backend. We've set up all our infrastructure to handle our needs, all that's left is connecting. So, let's get started with the first connection. This step will show you how to connect the upload page up and test it.

1. Navigate back to your cloud 9. On line 37 of frontend/src/Components/Dropzone.js you will substitute **REPLACE ME** with the **Invoke URL** you copied from API Gateway. 

2. Great work, you've now finished your first page of features for your ML website. To test whether the functionality works we will try upload an image from the website. To do this we will need to kick off a local version of the site with the following code.

*Only run this if the process running in your terminal has stopped, it should still be running from before.*

```shell
npm run start
```

3. Make sure you **Save** after editing files on cloud9.

4. After the app has compiled successfully, click **Tools** in the toolbar up top, click **Preview** and finally click **Preview Running Application**. 
   Open the preview in another tab by clicking the arrow / box button on the right of the search bar.

![ReactExpand](/img/ReactExpand.png)

5. In the app, you will need to navigate to the upload page by opening up the left drawer menu. Once on the page, try uploading an image using the upload interface; preferably a facial image, to test whether your /upload and /detect routes work. Make sure to click **Scan**.

6. If you've correctly followed the previous steps and all goes well, the site should save your image to the s3 with a json of detections and render the results, if there is at least one facial detection on the site.

**Note:** *The results should return in a few seconds, if you're waiting for a while check to make sure the invoke link you copied is correct or that your lambda code is formatted correctly (python is whitespace sensitive).*
