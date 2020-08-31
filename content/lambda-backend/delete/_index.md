+++
title = "Delete route"
weight = 5
pre = "<b>4.5 </b>"
+++

1. From the gallery tab, let's say the user uploaded accidentally an embarrasing photo. He wants to erase it easily from the frontend rather than going to the bucket and deleting it from there. Well that what delete is for. Delete is a simple call to the backend, with the filename. The function scans through the bucket for both the image and json, deleting them once found.

```python
def doDelete(event):
    # get the second item on the URL, the item we want to remove from S3
    key = event['path'].split("/")[2]
    s3.delete_object( Bucket=bucket_name, Key=key )
    s3.delete_object( Bucket=bucket_name, Key=key + '.json' )
    return json.dumps({'Message': 'Success'})
```

**What's happened?**

In the event path with be the filename. To get the key we are splitting this line and then using that key on the next two lines to delete the image and the json of results attached to that image.

We then give back a success message to say the deletion was a success.