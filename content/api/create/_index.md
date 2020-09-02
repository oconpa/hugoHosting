+++
title = "Create the API"
weight = 1
pre = "<b>5.1 </b>"
+++

1. There will be a number of gateways to which we can choose from. We will be creating a REST API, so select "REST API" (**Note**: There are two version of REST API, don't choose the REST API private option), Click **Build**. 

![Create REST](/img/restapi-1.png)

*If you have never used API Gateway before when you click build, make sure on the next screen in the "Create new API" section you have **New API** selected rather than **example API**. Must match the below image.*

2. We will be creating a new REST API, give your API a name, "rekognition" will work for this example.  Then click **Create API**

![Create REST](/img/restapi-2.png)

3. Click **Actions** and select **Create Resource**

![Create resource](/img/creatresource-1.png)

4. Select the check box **Configure as proxy resource**. We want every request to be passed directly to the lambda function created, application code will take care of the http method. Click **Create Resource**

*Do not name your resource, by checking the box the naming should automatically be populate with proxy*

![Create resource](/img/creatresource-2.png)

5. In the lambda function text field, type in the name of the lambda function we created, **facial-detect**, and click save, when requested to confirm permission click **OK** we are allowing this API Gateway to invoke the lambda function.

![Create resource](/img/creatresource-3.png)

