+++
date = "2016-03-22T10:28:24-04:00"
title = "API-Step 2 - Starting the loopback implementation (part 1)"

+++

Now that my [design](/post/first-api-design_first/) as been done with the swagger format, I'll start the coding with [LoopBack](http://loopback.io/).

## Apigee-127

Before deciding to use loopback, my first attempt was with [Apigee-127](https://github.com/apigee-127/a127-documentation/wiki/What-is-Apigee-127).  The framework
was easy to use until I realized that while the [API Gateway](http://microservices.io/patterns/apigateway.html) is written using
pure node.js code, the [favorite choice](https://github.com/apigee-127/a127-documentation/wiki/Quick-Start:-Download-and-Start-Usergrid) of implementation is 
the [apache usergrid](http://usergrid.apache.org/) BaaS Framework.  

Since apache usergrid is writting in Java EE stack and not a pure node.js implementation I have to eliminate it.

## Feathers 2.0

After that, I tried the [feathers 2.0](https://www.gitbook.com/book/feathersjs/feathers-docs/details) framework.  Very
modular, the framework is writting using pure node.js code. After searching a little bit on the internet and 
the slack channel for the framework, I didn't find any hooks that can bridge the swagger 2.0 yaml format 
to the service implementation.   The people working to build this framework were very kind in answering my questions.

I found it difficult to find examples and to write a complete working API with it.  I'm not a node expert too so I stopped my
exploration for now but I promise to go back and give it a try later.

## Loopback

The loopback framework is well documented and as a lot of examples available, easier to start with than Apigee-127 and 
Feathers 2.0 so I started with this one (on my third try).

### Creating the application

Creating the application was easy :

{{% fluid_img "/img/api-loopback/api_create_app.png" %}}

### Generating a model based on my swagger definition

The built-in [Swagger generator](https://docs.strongloop.com/display/public/LB/Swagger+generator) makes it easy to do the job.

I've made a local copy of my swagger definition in the `api` directory of my project with the name `words-swagger.yaml` and generated the model : 

{{% fluid_img "/img/api-loopback/api-swagger-generator.png" %}}

### Running the project

The included generator as a little bug in the version that I used :  

{{% fluid_img "/img/api-loopback/api-generator-error.png" %}}

The same bug appeared at a few places that I fixed easily.

### The generated API

 My swagger definition included a model and a list of API that I created to have some basics CRUD operations on my model. I
 didn't realize when I used the `swagger-generator` that it had the capacity to automatically generate the CRUD operations so I 
 ended up with two sets of API.
 
 The **swagger_v1** API :
 
{{% fluid_img "/img/api-loopback/api-swagger-v1.png" %}}
 
 The **WordList** API :
 
{{% fluid_img "/img/api-loopback/api-wordlist.png" %}}
 
## My first learning

I've learned an interesting feature about the loopback framework and the swagger format.  Since we have the ability to 
define a model, there is not added value in defining the API for some basics CRUD operations.

I will modify my swagger format to reflect that and continue on my API project.
 
## See also

- [Learn GitHub project](https://github.com/pamyot/learn)
- [My first API projet](/post/first-api-project/)  
- [API-Step 1 Design first](/post/first-api-design_first/)  
 

