
+++
title = "Gallery View"
weight = 1
pre = "<b>7.1 </b>"
+++

#### Connect listgallery to React Frontend

This route will pull the existing images from your S3 to populate your gallery page. It pulls and serves them up for the users to view.

1. Make sure you have the default **Invoke URL** copied into your clipboard from API Gateway, as you will need it in this challenge.

2. In `frontend/src/Components/ImageGridList.js`, you need to paste your **Invoke URL** in the appropriate place, so that when the user loads the gallery page, all the images in the bucket are there. See if you can figure it out.

3. Test the app. To test the listgallery feature go to the gallery page. If successful, the images you uploaded via the upload page should now be rendering on the gallery page.
