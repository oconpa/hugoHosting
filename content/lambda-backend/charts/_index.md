+++
title = "Charts route"
weight = 6
pre = "<b>4.6 </b>"
+++

The final piece to the puzzle is the charts route. This route, at this current time, will return an array that will be used to populate the smile chart and age chart. This is just a demonstration of what can be done with the detection results of rekognition. Here we are summarising the age range and smile count of our gallery.

1. Copy the code below replacing our doChart function exactly.

```python
def doChart(event):
    if (event['body'] == 'age'):
        response = s3.list_objects_v2( Bucket=bucket_name)
        
        photoList = []
        # We are looping to get all json information on each image
        for item in response['Contents']:
            if (item['Key'][-5:] == '.json'):
                resp = s3.get_object(
                    Bucket=bucket_name,
                    Key=item['Key']
                )
                photoList.append(json.loads(resp['Body'].read().decode('utf-8')))
        
        chart = [0, 0, 0, 0, 0, 0]
        # We are looping through each face to pull average age
        for photo in photoList:
            if len(photo['FaceDetails']) != 0:
                for face in photo['FaceDetails']:
                    age = (face['AgeRange']['Low'] + face['AgeRange']['High'])/2
                    if age > 89:
                        chart[5] += 1
                    elif age > 69:
                        chart[4] += 1
                    elif age > 49:
                        chart[3] += 1
                    elif age > 39:
                        chart[2] += 1
                    elif age > 19:
                        chart[1] += 1
                    elif age >= 0:
                        chart[0] += 1

    elif (event['body'] == 'smile'):
        response = s3.list_objects_v2(
            Bucket=bucket_name
        )
        
        photoList = []
        # We are looping to get all json information on each image
        for item in response['Contents']:
            if (item['Key'][-5:] == '.json'):
                resp = s3.get_object(
                    Bucket=bucket_name,
                    Key=item['Key']
                )
                photoList.append(json.loads(resp['Body'].read().decode('utf-8')))
        
        chart = [0, 0]
        # We are looping through each face to see if it's a smile or not
        for photo in photoList:
            if len(photo['FaceDetails']) != 0:
                for face in photo['FaceDetails']:
                    if face['Smile']['Value']:
                        chart[0] += 1
                    else:
                        chart[1] += 1

    return json.dumps(chart)
```

2. Make sure to **Save** your lambda before proceeding.

**What's happened?**

Here you can see that we've split up the doChart function into an age case and a smile case. Let decipher one of them to gain an understanding of what we are doing. First, we pull a listing of the files currently in the bucket. We then loop through the file names looking to only grab the json files.

We then perform some data manipulation looping through the content pulling an age indicator and adding it, or adding a counter to smile, on whether the people are smiling or not.
