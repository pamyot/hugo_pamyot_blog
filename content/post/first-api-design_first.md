+++
Categories = []
Tags = []
date = "2016-03-12T07:23:45-04:00"
title = "API-Step 1 Design first"

+++

To build my first API, I will use a design first approach.

## Why design first ?

My background as a software architect leads me naturally to opt for a design first approach.

I googled a little bit to confirm that the design first approach still applies in an Agile and API world (we never know) :
 
*  Excellent presentation from [Jason Harmon](http://www.infoq.com/presentations/api-design-first) or similar on [slideshare](http://fr.slideshare.net/JasonHarmon1)
*  [API Evangelist](http://apievangelist.com/2014/08/11/what-is-an-api-first-strategy-adding-some-dimensions-to-this-new-question/)
*  [apigee](http://apigee.com/about/blog/developer/design-first-approach-building-apis-swagger) 

## Use case

The use case that will be used for the first API will be based on a flash word learning technic that is used for [kids with dyslexia](http://homeschoolingwithdyslexia.com/how-to-teach-sight-words-dyslexia/).
For the first API, I will only build an API that allows to do CRUD operation on a word list:

- Create, Update or Delete a word list.
- Get a word list.

I know the operations are rather basic for now, but I want to start small and I'll add more later.

## Tools

I'll use the [Swagger](http://swagger.io/) format to design the API and store it on [Swagger Hub](https://swaggerhub.com).

## Designing the API

The swagger editor is nice but it doesn't help in creating a valid YAML document.  To create my API, I add
to go to the [OPENAPI SPECIFICATION](http://swagger.io/specification/) reference page and I refered to
another example that a had written last year to test the swagger specification.

### Designing the entities

I started by defining my entities required for my API.

{{< gist pamyot 6b4d3f6b17ec1647c416 >}}

### Reusable parameters

I have the wordListID parameter that is used in a few places so I created a parameter for that.

{{< gist pamyot 3091576d6c1f70b96b6a >}}

### Create the required verbs

The final step was to create the verbs required to implement my API.

{{< gist pamyot 41fb243f2d16352848ef >}}

## The API

You can explore the complete [Words API](https://swaggerhub.com/api/pamyot/words/V0.1) on swaggerHub.

## Intuitive and easy

This first step was easy to do and I the swagger format helped me in designing a simple and clear API to be used.
 
## See also

- [My first API projet](/post/first-api-project/)  
