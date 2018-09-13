# What is purpose of this repo :
* Describes the creation of the an api in swagger hub and then deploy to AWS with a lambda function completing the simple science. Has links to Microsoft, Google and AWS respectfully.  

# Develop the api first  
* What are the methods that you are exposing to your clients ?
* What is the input format for the model (json, xml, etc.) ?
* What is the security model for the api, could use identity access management, api keys or many other items.
* Follow some of the api leading practices - many resources, this is one example from microsoft : [microsoft leading practices][ms2]

# [Swagger hub][sh1] tool could be used to author the api, could use other methods.
* copy the [Simple scoring api][api] from the Git repository into the swagger hub or another online editor.
* now that you have copied into swagger hub you can see there are two actions (Post to scores and Get ping of service) . these are two simple services that allow you to excercise some simple science.  
* if you click on the Post /scores; you can try it out without any further work.  

```sh
$ Click "Try it out".
$ this brings up the expected inputs to the service endpoint.
$ this method is looking for a json packet that has some information about the person to be scored.
$ copy json here
```

* An example of the api that is hosted in this repository is located in my swagger hub at [commercialize api][soa1]; there are some changes that need to be made from swagger hub so you can copy into the cloud hosting provider of API management suite. created a working example of the API that works in AWS see [api_cloud]


# [AWS][aws1] specific information 
* Copy the api that you completed in the swagger hub and paste into AWS gateway.


# [Microsoft][ms1] specific information 
* Copy the api that you completed in the swagger hub and paste into Azure gateway.


# [Google][gg1] specific information 
* Copy the api that you completed in the swagger hub and paste into Apigee gateway.




License
----

MIT


   [sh1]: <https://swagger.io/tools/swaggerhub/>
   [ms1]: <https://azure.microsoft.com/en-us/services/api-management/>
   [ms2]: <https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design>
   [gg1]: <https://cloud.google.com/apigee-api-management/>
   [aws1]: <https://docs.aws.amazon.com/apigateway/latest/developerguide/integrating-api-with-aws-services-lambda.html>
   [soa1]:<https://app.swaggerhub.com/apis/edeuser/CommercializationAPI_SOA/1.0.0>
   
   [simple scoring api]: <https://github.com/eddeuser2017/commercialize_api/blob/master/simplescoringapi>
   [api_cloud]: <https://github.com/eddeuser2017/commercialize_api/blob/master/api_cloud>
   [scorePerson]: <https://github.com/eddeuser2017/commercialize_api/blob/master/scorePerson>
