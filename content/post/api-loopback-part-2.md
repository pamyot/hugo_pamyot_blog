+++
date = "2016-03-25T15:12:22-04:00"
title = "API-Step 2 - Loopback implementation (part 2) - Connecting to a MongoDB database"

+++

In this post, I will connect the generated API (see [Part 1](/post/api-loopback-part-1)) to my
local MongoDB database and correct some errors that I've done on my swagger definition.

## Fixing the swagger API definition

In my [V0.1](https://swaggerhub.com/api/pamyot/words/V0.1) `WordList` definition, the `id` field was defined as a `String` : 
```
WordList:
  type: "object"
  properties:
    id:
      type: "string"
      title: "Word list ID"
    words:
      type: "array"
      title: "Words"
      items:
        $ref: "#/definitions/Word"
```

This won't work as the `id` field is expected to be an `integer` field.  The new [V0.2](https://swaggerhub.com/api/pamyot/words/V0.2) 
definition looks like this : 
```
WordList:
  type: object
  properties:
    id:
      type: integer
      format: int64
      title: Word list ID
    words:
      type: array
      title: Words
      items:
        $ref: '#/definitions/Word'
```
I also removed some `paths` entries that are no longer required but didn't find a way to remove them all
without having SwaggerHub reporting en error.

## Swagger generator

Since I modified my model, I ran the swagger generator again (after deleting the previous model).  The
generator ended with an error but it still worked : 

{{% fluid_img "/img/api-loopback/api-swagger-generator-v0.2.png" %}}


## Adding the MongoDB datasource

The next step is to configure the datasource to my local MongoDB database (installation is not shown here).
Instead of running the generator, you can manually configure the database in the **datasources.json** file : 

```
  "learn": {
    "host": "127.0.0.1",
    "port": 27017,
    "database": "learn_db",
    "password": "",
    "name": "learn",
    "user": "",
    "connector": "mongodb"
  }
```

## Connecting the model to the datasource

The step is really is easy, I only had to change to configuration in the **model-config.json** file : 

```
  "WordList": {
    "dataSource": "learn",
    "public": true
  }
```

## Testing my API

It's now time to test my new API and see if it works.  I will do this using the built-in 
API explorer : 

```
http://localhost:3000/explorer/#/
```

I will add a new WordList.  Leaving the `id` field empty will let MongoDB generate a new `objectID` :
```
curl -X POST --header "Content-Type: application/json" --header "Accept: application/json" -d "{
  \"words\": [
    \"requin\",
    \"poisson\"
  ]
}" "http://localhost:3000/api/WordLists"
```

The response body : 
```
{
  "id": "56f58cc02dd5c18421bf03e5",
  "words": [
    "requin",
    "poisson"
  ]
}
```

I did a check on the mongoDB command line : 
```
C:\dev\learn>mongo
MongoDB shell version: 3.2.0
connecting to: test
> use learn_db
switched to db learn_db
> db.WordList.find()
{ "_id" : ObjectId("56f58cc02dd5c18421bf03e5"), "words" : [ "requin", "poisson" ] }
>
```

## Next step

I found the exercise really easy to do and didn't have to write much code to do this.  The next 
step will be to add some security to this API.
