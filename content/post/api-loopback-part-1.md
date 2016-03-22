+++
date = "2016-03-22T10:28:24-04:00"
draft = true
title = "First API - Starting the loopback implementation (part 1)"

+++

Now that my [design](/post/first-api-design_first/) as been done with the swagger format, I'll start the coding with [LoopBack](http://loopback.io/).

## Apigee-127

Before deciding to use loopback, my first attempt was with [Apigee-127](https://github.com/apigee-127/a127-documentation/wiki/What-is-Apigee-127).  The framework
was easy to use until I realized that the strengths with this framework was the [API Gateway](http://microservices.io/patterns/apigateway.html) that is implemented using
pure node.js code but their [favorite choice](https://github.com/apigee-127/a127-documentation/wiki/Quick-Start:-Download-and-Start-Usergrid) of implementation is 
the [apache usergrid](http://usergrid.apache.org/) BaaS Framework.  

Since apache usergrid is writting in Java EE stack and not a pure node.js implementation I have to eliminate it.

## Feathers 2.0

After that, I tried the [feathers 2.0](https://www.gitbook.com/book/feathersjs/feathers-docs/details) framework.  Very
modular, the framework is writting using pure node.js code. After searching a little bit on the internet and 
the slack channel for the framework, I didn't find any hooks that can bridge the swagger 2.0 yaml format 
to the service implementation.   The people working to build this framework were very kind in answering my questions.

I found it difficult to find examples and to write a complete working API with it.  I'm not a node expert too so I stop my
exploration for now but I promise to go back and give it a try later.

## Loopback

The loopback framework is well documented and as a lot of examples available, easier to start with than Apigee-127 and 
Feathers 2.0 so I start with this one (on my third try).

### Creating the application

I create the application following the simple steps