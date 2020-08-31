+++
title = "Upload route"
weight = 2
pre = "<b>4.2 </b>"
+++

The upload route is used to open a temporary tunnel to the s3 from the frontend for just enough time to upload an image. Think of this as toll road for example. In the old days when travelling on toll roads you would come to a checkpoint. In order to pass the checkpoint, you would pay a specified fee, which in turn would allow you to pass and continue your journey.

![Backend](/img/presigned.png)

Well let's take that example and apply it to what we are doing. In order to open up a tunnel between the front and backend we first hit the upload route. The lambda will then return what's called a presigned URL. This URL is special in that it allows you to perform a put to the s3 for a short period of time. In the toll road example this is the receipt you receive in order to pass the checkpoint. This receipt is special in that it will allow you to pass the checkpoint for a short period of time before becoming invalid and a new one must be purchased.

To upload the image, we are using this returned URL attaching our image to it and ultimately sending an image to our s3.

1. After attaching the policy, in the previous step, go back to your lambda (it should already be open in your browser on another tab) and under the **Configuration** tab in the **function code** section (scroll down on the lambda until you see a suitable place to paste code), paste:

```python
import boto3
from botocore.client import Config
import json

rekognition = boto3.client('rekognition')
s3 = boto3.client('s3', 
    endpoint_url=f'https://s3.ap-southeast-2.amazonaws.com', 
    config=Config(s3={'addressing_style': 'virtual'})
    )
bucket_name = "facial-detection-REPLACEME"
expiration = 120

def lambda_handler(event, context):
    print(event)
    path = event['path'].split("/")[1]
    body = ''
    if (path == 'upload'):
        body = doUpload(event)
    elif (path == 'detect'):
        body = doFacialDetection(event)
    elif (path == 'delete'):
        body = doDelete(event)
    elif (path == 'listgallery'):
        body = doListGallery(event)
    elif (path == 'charts'):
        body = doChart(event)
    
    return {
            'statusCode': 200,
            'headers': {
                "access-control-allow-origin": "*",
                "access-control-allow-methods": "*"
            },
            'body': body
    }
    

# Upload method
def doUpload(event):
    response = s3.generate_presigned_url(
        'put_object',
        Params={
            'Bucket': bucket_name,
            'Key': event['queryStringParameters']['fileName'],
            'ContentType': 'image/*'
        },
        ExpiresIn=expiration)
        
    body = json.dumps(response)
    return body

# Pass a s3 item reference to 
def doFacialDetection(event):
    return json.dumps('Not Done yet')

# Pull Images
def doListGallery(event):
    return json.dumps('Not Done yet')

# Get Charts
def doChart(event):
    return json.dumps('Not Done yet')
    
# Delete Method
def doDelete(event):
    return json.dumps('Not Done yet')
```

2. On line 6 you will need to replace **REPLACEME** with your full name so that bucket_name matches the bucket you created earlier on. E.g. if you named your bucket facial-detection-johnsmith, then line 6 would look like

```python
bucket_name = "facial-detection-johnsmith"
```

*It's critical that this matches exactly that name of your bucket (case sensitive)*

3. Click **Save**

**What's happening?**

Let's now recap on what we are doing in the code. As you can see above, we set up the skeleton for each of our individual routes, however, only gave the proper functionality for upload. 

If you look closely in the upload function you can see s3.generate_presigned_url. What is happening here is a call using an SDK to the AWS S3 service. An SDK is a library you can import to easily talk to AWS service, we will do it again in detect with the rekognition service. You can see that at the very top the code imports boto3, the library to talk to AWS, and it specifies the resource connection on line 6.

Using the AWS SDK, in the upload function, we are calling s3 to generate our presigned URL to temporarily allow a put_object of image type to our bucket. Once that link is retrieved, we simply return it to the user to be used.
