# What is purpose of this repo :
* Describes the creation of the an api in swagger hub and then deploy to AWS with a lambda function completing the simple science. Has links to Microsoft, Google and AWS respectfully.  

# Develop the api first
* This is a collaboration, between the business and the IT execution arm that will complete the work.  The API is a contract that will be established and become the layer of abstraction so that the client can move forward with there work while the implementation is being completed.
* What are the methods that you are exposing to your clients ?
* What is the input format for the model (json, xml, etc.) ?
* What is the security model for the api, could use identity access management, api keys or many other items.
* Follow some of the api leading practices - many resources, this is one example from microsoft : [microsoft leading practices][ms2]

# Author the api through example.
* copy the [Simple scoring api][api] from the Git repository into an [api_Editor], for the purpose of this excercise i will use [Swagger hub][sh1] 

* now that you have copied into swagger hub you can see there are two actions (Post to scores and Get ping of service) . these are two simple services that allow you to excercise some simple science.  
* if you click on the Post /scores; you can try it out without any further work.  

```sh
$ Click "Try it out".
$ this brings up the expected inputs to the service endpoints for Posting a score.
$ this method is looking for a json packet that has some information about the person to be scored.
$ if you click on model in the method you will see the below image.
```
[![model](https://github.com/eddeuser2017/commercialize_api/blob/master/personToScore.png)]

```sh
$ Click "Edit Value" within the body of the PersontoScore.
$ this brings up the example json the api provided.
$ Then Click "Execute" see the below image.
```
[![execute](https://github.com/eddeuser2017/commercialize_api/blob/master/personJsonExecute.png)]

```sh
$ Once the service executes you will see what the service would execute as 
$ a curl command and the requested URL.  
$ this is ultimately a preview of what your customers will see when calling your service.
$ if you click on model in the method you will see the below image.
$ based on the input a Code will be emited, see list of http codes below

```
[![response](https://github.com/eddeuser2017/commercialize_api/blob/master/scorePerson_response.png)]

[HTTP ERROR CODES][http]


* An example of the api that is hosted in this repository is located in my swagger hub at [commercialize api][soa1]


# How do i deploy my newly created API ?
There are some changes that need to be made from swagger hub so you can copy into the cloud hosting provider of API management suite. 
* first thing to understand is that the OpenAPI standards that different cloud providers are using needs to be accounted for.
* For a guide on the differences between the structures of the versions see [api_visualguide][openapi]
* in the two API's i largely took some of the formatting that is out of the box for swagger and removed; such as mocking, examples, schemas etc.
* Created a working example of the API that works in AWS see [api_cloud]




# AWS specific information 
* Follow the [AWS][aws1] directions by copying the following [api_cloud] source code that you completed in the swagger hub and paste into AWS gateway.

```sh
$ go to the aws console. you will see the following image : 
```
[![aws1](https://github.com/eddeuser2017/commercialize_api/blob/master/aws-apicreation1.png)]

```sh
$ Click ok, as they have already loaded the pet example for you.
$ Select "Import from Swagger"
$ This allows us to select the swagger file or just copy the api_cloud file from the repository into this box.
```
[![aws2](https://github.com/eddeuser2017/commercialize_api/blob/master/aws-apicreation2.png)]

```sh
$ Click import which now brings up your methods
$ Click on /Scores POST method and Select "Integration type = Mock"
$ this integration type will allow us to test that it will work appropriately prior to introducing the lamda function.
$ Click "Save"
```
* once you have completed the integration type and saved the settings you will see the test harness amazon uses.

[![aws3](https://github.com/eddeuser2017/commercialize_api/blob/master/aws-apicreation3.png)]

```sh
$ Click on "Test"
$ Navigate to the "Request Body"
$ Paste the following JSON packet into the field
$ Dont forget to remove the dollar signs "$" or it wont work
$ {
$   "id": "d290f1ee-6c54-4b01-90e6-d701748f0851",
$   "gender": "m",
$   "conditions": {
$     "code": [
$       [
$         8745002,
$         89003005,
$         427038005
$       ]
$     ]
$   }
$ }
$ Click on "Test"
```
* As you can see, the execution excercised the API with the expected inputs and sent the body of the request for processing.   We will ultimately move this to our NodeJS, Python or other Lamda function.

* Now it is time to integrate the real science into the API
* click on "Integration Request" which is currently set at Type = "Mock"
* We now want to actually implement the function.
* TODO: could put in specific step by step instructions to help learning; here is an AWS you will have to get some basic setup completed prior to doing this section, see [AWS Deployment][aws_deployment] section which really will help you get the roles, users, deployments and stage setup prior to using the lambda.
* To help out, i have created a cloud formation template - [simple science cloud formation template][cloudformationmodified]; based on the good work  [Cloud Formation template starter][cloudformation] that will do all this work for you.  

# MICROSOFT specific information 
* Follow the [Microsoft][ms1] directions by copying the following [api_cloud] source code that you completed in the swagger hub and paste into AWS gateway.


# GOOGLE specific information 
* Follow the [Google][gg1] directions by copying the following [api_cloud] source code that you completed in the swagger hub and paste into AWS gateway.




License
----

MIT


   [sh1]: <https://swagger.io/tools/swaggerhub/>
   [ms1]: <https://azure.microsoft.com/en-us/services/api-management/>
   [ms2]: <https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design>
   [gg1]: <https://cloud.google.com/apigee-api-management/>
   [aws1]: <https://docs.aws.amazon.com/apigateway/latest/developerguide/integrating-api-with-aws-services-lambda.html>
   [soa1]:<https://app.swaggerhub.com/apis/edeuser/CommercializationAPI_SOA/1.0.0>
   [cloudformation]: <https://gist.github.com/magnetikonline/c314952045eee8e8375b82bc7ec68e88>
   [cloudformationmodified]: <https://github.com/eddeuser2017/commercialize_api/blob/master/dsstack.yaml>
   
   [simple scoring api]: <https://github.com/eddeuser2017/commercialize_api/blob/master/simplescoringapi>
   [api_cloud]: <https://github.com/eddeuser2017/commercialize_api/blob/master/api_cloud>
   [scorePerson]: <https://github.com/eddeuser2017/commercialize_api/blob/master/scorePerson>
   [http]: <https://en.wikipedia.org/wiki/List_of_HTTP_status_codes>
   [api_Editor]: <https://github.com/OAI/OpenAPI-Specification/blob/master/IMPLEMENTATIONS.md#implementations>
   [openapi]: <https://blog.readme.io/an-example-filled-guide-to-swagger-3-2/>
   
   [aws_deployment]: <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-deployments.html>
   
