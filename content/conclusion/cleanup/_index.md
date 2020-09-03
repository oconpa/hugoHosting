
+++
title = "Cleaning up"
weight = 8
pre = "<b>8.1 </b>"
+++

If you leave AWS resources running for long periods of time, you may get charged. You should clean up all of your AWS resources at the end of this workshop to avoid this!

---

### Deleting API Gateway

1. In the search bar of your AWS console search up API Gateway and go to the first link. Or click [here](https://ap-southeast-2.console.aws.amazon.com/apigateway/home?region=ap-southeast-2#/)
2. Find and select **rekognition**
3. Select **Actions**, then **Delete**

### Deleting the Lambda

1. In the search bar of your AWS console search up Lambda and go to the first link. Or click [here](https://ap-southeast-2.console.aws.amazon.com/lambda/home?region=ap-southeast-2#/functions)
2. Find and select **facial-detect**
3. Select **Actions**, then **Delete**

### Deleting the S3

1. In the search bar of your AWS console search up S3 and go to the first link. Or click [here](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-2#)
2. Find and select facial-detection-**Replace with your full name**
3. Select **Delete**

### Deleting the Cloud9 Workspace

1. In the search bar of your AWS console search up cloud9 and go to the first link. Or click [here](https://ap-southeast-2.console.aws.amazon.com/cloud9/home?region=ap-southeast-2#)
2. Select the environment named **MLWorkshop** and click **Delete**
3. Type the phrase ‘Delete’ into the confirmation box and click **Delete**
