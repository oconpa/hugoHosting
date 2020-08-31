
+++
title = "Gallery View"
weight = 1
pre = "<b>7.1 </b>"
+++

#### Connect listgallery to React Frontend

This route will pull the existing images from your s3 to populate your gallery page. It pulls and serves them up for the users to view.

1. Make sure you have the default **Invoke URL** copied into your clipboard from API Gateway, then go to your cloud 9.

2. In frontend/src/Components/ImageGridList.js, on line 33 substitute **REPLACE ME** with the invoke URL

3. Test the app. To test the listgallery feature go to the gallery page. If successful, the images you uploaded via the upload page should now be rendering on the gallery page.
