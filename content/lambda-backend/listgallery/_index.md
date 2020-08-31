+++
title = "Listgallery route"
weight = 4
pre = "<b>4.4 </b>"
+++

Listgallery will be used as a pull mechanism, to pull and display the existing images on the s3. This will allow the user to display a collection of images where anyone using the site can rapidly perform detections on previously uploaded images.

1. Similar to the last step copy the below code into your skeleton, replacing the skeleton function exactly so that it matches below.

```python
def doListGallery(event):
    response = s3.list_objects_v2(Bucket=bucket_name)

    for s3itemIndex in range(len(response['Contents'])-1, -1, -1):
        if 'LastModified' in response['Contents'][s3itemIndex]:
            del response['Contents'][s3itemIndex]['LastModified']
        if response['Contents'][s3itemIndex]['Key'][-5:] == '.json':
            response['Contents'].pop(s3itemIndex)

    photoList = []
    for j in response['Contents']:
        link = s3.generate_presigned_url(
                    'get_object',
                    Params={
                        'Bucket': bucket_name,
                        'Key': j['Key'],
                    },
                    ExpiresIn=expiration)
        photoList.append({'src': link, 'thumbnail': link})

    return json.dumps(photoList)
```

**What's happened?**

What we are doing here is pulling the content of the bucket with s3.list_objects_v2. After we pull, we have to filter out all the json files as these won't be needed.
