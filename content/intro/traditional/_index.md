
+++
title = "Web App Architecture"
weight = 1
pre = "<b>1.1 </b>"
+++

![architecture](/img/Arch.png)

The architecture above should give you a high overview view of the ML app's architecture. Each service is inter-related to the next, coming together in harmony to deliver the application. 

1. **Frontend**: The frontend is served from cloud9, symbolised as the cloud with a nine above. 
2. **API Gateway**: Channel's the requests made by the react app to the backend lambda. 
3. **Backend**: As seen above the backend lambda works with s3 and rekognition through various routes.
4. **Storage**: Stores application data.
5. **Rekognition**: Tool used for all detections. 

A few things to note:
- The above solution is not quite a serverless application as we are hosting from our cloud9. You can easily make this a serverless solution by pushing to an s3 bucket and hosting from there.
- The main benefit in developing on cloud9 is that you don't have to authenticate with AWS, as you are developing from within the VPC, hence no auth needed.