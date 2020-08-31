+++
title = "Detect route"
weight = 3
pre = "<b>4.3 </b>"
+++

Our detect route works in harmony with S3, in that it takes in the file location of your image in s3 to perform it's detection. 

![Backend](/img/rekog.png)

The first step to detect is to feed into rekognition the location of your file in the s3. Once located rekognition will pull facial detections, if any and save them to a same named file with a json extension, before returning the data to the user.

1. Now lets add our detection chunk of code to our function. On your lambda you will need to replace the current doFacialDetection function so that it matches exactly the code below.

```python
def doFacialDetection(event):
    response = rekognition.detect_faces(
        Image={
            'S3Object': {
                'Bucket': bucket_name,
                'Name': event['body'],
            }
        },
        Attributes=['ALL']
    )
    
    s3.put_object(
        Body=(bytes(json.dumps(response).encode('UTF-8'))),
        Bucket=bucket_name,
        Key=str(event['body']) + '.json',
    )
    return json.dumps(response)
```

**What's happened?**

The same way we connect to the s3 service using the boto3 sdk, we are doing for the rekognition service. You can find that initial connect at the very top of your code on line 5.

The first block of code where we call rekognition.detect_faces is to trigger the rekognition service to go make a detection on the file name being based through the event's body.

Once the results of that detection have been returned we push that content to the s3 as a json with s3.put_object before returning it to the user.