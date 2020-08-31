
+++
title = "Deleting Images"
weight = 2
pre = "<b>7.2 </b>"
+++

#### Connect delete to React Frontend

The delete feature will allow user from the webpage to delete and remove images from the s3 bucket.

1. Make sure you have the default **Invoke URL** copied into your clipboard from API Gateway, then goto your cloud 9.

2. In frontend/src/Components/ImageGridList.js, on line 43 substitute **REPLACE ME** with the invoke URL.

3. Test the app. To test the delete feature goto the gallery page. If you select one of the images, there should be an option to delete. If successful, when you select the button after the page has refreshed the image should now be gone.
