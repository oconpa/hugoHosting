
+++
title = "Create an S3 with CORS"
weight = 3
chapter = true
pre = "<b>3. </b>"
+++

# Creating a bucket with CORS

For this section we are going to create our storage unit for the images the user uploads. Each image will be saved a unique id so that we don't overlap with a corresponding json file of detection results to be used later on.

1. Provision an s3 bucket
2. Enable CORS put under CORS configuration