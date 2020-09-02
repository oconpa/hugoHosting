
+++
title = "Setting up Lambda Backend"
weight = 4
pre = "<b>4. </b>"
+++

Now that we've got the storage unit set up, its time to set up our backend which to talk to the bucket. In the coming slides we will no only push content to the bucket, but also pull it to populate our website.

For the backend we are going to set up 5 routes each playing a crucial role in the app.

![Backend](/img/Backend.png)

1. **/upload**

The upload route is designed to serve back a presigned URL to which will open a temporary tunnel for the user to upload his image. (Explained more in 4.2)

2. **/detect**

Detect is where the real magic happens. This route is responsible for finding the image in the S3 bucket, performing an ML analysis, saving the results as a .json in the s3 and returning the results.

3. **/listgallery**

Called whenever the gallery tab is loaded, this route pulls all the images currently in the s3 to display in as an image gallery to the user.

4. **/delete**

Gives the user the ability to delete images from the user interface. User calls this route by clicking onto an image in the gallery and clicking the respective delete button above of the image.

5. **/charts**

Charts currently has configurations for both smile analysis and age categorisation. Based on the images in the gallery, this route will pull detection data from the jsons in the s3 and place them in an array to be used on the frontend charts.

**In the next few steps we will focus on building the lambda function section by section to get an understanding of the code we are putting in.**

