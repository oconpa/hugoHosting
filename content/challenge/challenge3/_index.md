
+++
title = "Gallery Detection"
weight = 3
pre = "<b>7.3 </b>"
+++

#### Connect gallery detection to React Frontend

The gallery detection feature will allow user from the gallery to perform detections on previous image by pressing the tick icon on the top left of each image.

1. Make sure you have the default **Invoke URL** copied into your clipboard from API Gateway, then goto your cloud 9.

2. In frontend/src/Components/ImageGridList.js, on line 59 substitute **REPLACE ME** with the invoke URL.

3. Test the app. To test the gallery detection goto the gallery page. On the top left of each image should be a tick icon. If you click it, if all things go well you should get back detection for the image.
