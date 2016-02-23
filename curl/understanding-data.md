# Understanding Data with cURL

###### Launchpad provides a JSON document store with search and realtime capabilities. Read and write operations are translated into a RESTful API. The Launchpad client also helps you to easily create complex queries in Java, JavaScript, or Swift, and search your data in realtime. Yes, you can listen for query in realtime, with no need of extra server-side code.

<!-- <article id="1-write-section"> -->

## 1. Write

Writing new data is as simple as sending a JSON.

```bash
curl -X "POST" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"title\":\"Star Wars IV\",\"year\":1977,\"rating\":8.7}"
```

This operation will return the newly created document, with the following generated ID:

```json
{
  "title": "Star Wars",
  "id":" 115992383516607958",
  "year": 1977,
  "rating": 8.7
}
```

The URL we just created stored a new document in our `app`'s `service`, inside the _collection_ `movies`. More information on how to setup this datastore URL can be seen in the section [Building APIs](http://liferay.io/docs/curl/building-apis.html). For now, we only need to know that within the path where the data is mounted, the URL will be interpreted as a key that points to a stored resource like the one below:

```text
/collectionName/documentId/documentProperty/documentInnerProperty
```

For example, to reference the newly created _Star Wars_ rating, we can use the path:

```text
/movies/115992383516607958/rating
```

From this point, update and delete operations can be performed at any level of the resource. For example, we can update the existing document by adding a new field:

```bash
curl -X "PATCH" "http://liferay.io/app/service/movies/115992383516607958" \
     --data-urlencode "stars=Mark Hamill" \
     --data-urlencode "stars=Harrison Ford" \
     --data-urlencode "stars=Carrie Fisher"
```

Note in the example above the data was sent as request form attributes. The response is the modified document:

```json
{
  "title": "Star Wars",
  "id": "115992383516607958",
  "year": 1977,
  "rating": 8.7,
  "stars": ["Mark Hamill", "Harrison Ford", "Carrie Fisher"]
}
```

To create a document with a custom ID, or override an existing one, we can use the PUT method at the document level. The following example creates a new entry with the custom ID `star_wars_v`:

```bash
curl -X "PUT" "http://liferay.io/app/service/movies/star_wars_v" \
     --header "Content-Type: application/json" \
     --data "{\"title\":\"Star Wars: Episode V - The Empire Strikes Back\",\"year\":1980,\"rating\":8.8}"
```

To override an existing entry you would just specify the existing ID.

To delete a field, document, or the entire collection, we just use the DELETE method:

```bash
curl -X "DELETE" "http://liferay.io/app/service/movies/star_wars_v/title"
curl -X "DELETE" "http://liferay.io/app/service/movies/star_wars_v"
curl -X "DELETE" "http://liferay.io/app/service/movies"
```

<!-- </article> -->

<!-- <article id="2-read-section"> -->

## 2. Read

Reading data from our storage takes only 3 lines of code.

```bash
curl -X "GET" "http://liferay.io/app/service/movies/star_wars_v"
```

The response body is the stored JSON document:

```json
{
  "id": "star_wars_v",
  "title": "Star Wars: Episode V - The Empire Strikes Back",
  "year": 1980,
  "rating": 8.8
}
```

We can also get any field value using the full path:

```bash
curl -X "GET" "http://liferay.io/app/service/movies/star_wars_v/title"
```

The full path returns the raw content in the response body:

```text
Star Wars: Episode V - The Empire Strikes Back
```

Requesting the entire `movies` collection using `curl -X "GET" "http://liferay.io/app/service/movies"` results in the first `10` documents stored:

```json
[
  {"id":"star_wars_i", "title":"Star Wars: Episode I - The Phantom Menace", "year":1999, "rating":6.5},
  {"id":"star_wars_ii", "title":"Star Wars: Episode II - Attack of the Clones", "year":2002, "rating":6.7},
  {"id":"star_wars_iii", "title":"Star Wars: Episode III - Revenge of the Sith", "year":2005, "rating":7.7},
  {"id":"star_wars_iv", "title":"Star Wars: Episode IV - A New Hope", "year":1977, "rating":8.7},
  {"id":"star_wars_v", "title":"Star Wars: Episode V - The Empire Strikes Back", "year":1980, "rating":8.8},
  {"id":"star_wars_vi", "title":"Star Wars: Episode VI - Return of the Jedi", "year":1983, "rating":8.4},
  {"id":"star_wars_vii", "title":"Star Wars: Episode VII - The Force Awakens", "year":2015}
]
```

The result is ordered by the document `id`, as we can see in the list above. We can select the order we want the results to be in, by passing a sort parameter, using the following code:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"sort\":{\"rating\":\"desc\"}}"
```

As expected, the result would be the following list:

```json
[
  {"id":"star_wars_v","title":"Star Wars: Episode V - The Empire Strikes Back","year":1980,"rating":8.8},
  {"id":"star_wars_iv","title":"Star Wars: Episode IV - A New Hope","year":1977,"rating":8.7},
  {"id":"star_wars_vi","title":"Star Wars: Episode VI - Return of the Jedi","year":1983,"rating":8.4},
  {"id":"star_wars_iii","title":"Star Wars: Episode III - Revenge of the Sith","year":2005,"rating":7.7},
  {"id":"star_wars_ii","title":"Star Wars: Episode II - Attack of the Clones","year":2002,"rating":6.7},
  {"id":"star_wars_i","title":"Star Wars: Episode I - The Phantom Menace","year":1999,"rating":6.5},
  {"id":"star_wars_vii","title":"Star Wars: Episode VII - The Force Awakens","year":2015}
]
```

Notice that Episode VII has no rating, as it was not released yet, thus it's sorted as the last document.

In addition to sorting the results, we can also apply filters using the following code:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":[ \
               {\"year\":{\"operator\":\"<\",\"value\":2000}}, \
               {\"rating\":{\"operator\":\">\",\"value\":8.5}} \
            ]}"
```

The result of the filters just used is the following entries:

```json
[
  {"id":"star_wars_iv","title":"Star Wars: Episode IV - A New Hope","year":1977,"rating":8.7},
  {"id":"star_wars_v","title":"Star Wars: Episode V - The Empire Strikes Back","year":1980,"rating":8.8}
]
```

We can also paginate the result using the `limit` and `offset` properties. Combining all the tools we've learned so far, we can run a detailed query on our data:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{\"year\":{\"operator\":\">\",\"value\":2000}}, \
              \"sort\":{\"rating\":\"asc\"}, \
              \"limit\":2, \
              \"offset\":1}"
```

Notice that filtering by the year we only get episodes I, II, III and VII. Applying the rating sort will give us this same order. We also limited the result to show only 2 documents, and skipped the first one. The final result is the following entries:

```json
[
  {"id":"star_wars_ii","title":"Star Wars: Episode II - Attack of the Clones","year":2002,"rating":6.7},
  {"id":"star_wars_iii","title":"Star Wars: Episode III - Revenge of the Sith","year":2005,"rating":7.7}
]
```

We support all basic SQL-like operators (`=`, `!=`, `>`, `>=`, `<`, `<=`, `~`), as well as `any` and `none` to filter elements in a list. We also give support for search operators, which we will see in more details in the section [Search Data](#3-search).

<!-- </article> -->

<!-- <article id="3-search-section"> -->

## 3. Search

Well, we did some great stuff with basic HTTP methods, like create, update, and delete JSON documents. We also learned how to retrieve documents with filter, sort, and pagination. What if we need to do more powerful queries with our documents? Well, in Launchpad you can do a text search, handle user misspellings, show the number of documents by category with your data, and much more.

First take a look at the text search. Its a simple, yet very powerful way to filter our results by a text query. Using the movie database we created before, let's search for a Star Wars movie by the episode title, like `"Revenge of the Sith"`. We are not interested if the letter is in upper or lower case, since we are using English connectors like `"of"` and `"the"`. We want something flexible enough it will also work for texts like "The revenge of the Sith", or "Sith's revenge". Our `match` operator is just what we need to run the search.

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{\"title\":{\"operator\":\"match\",\"value\":\"Sith's Revenge\"}}}"
```

The result of the `match` operator query is the following entry:

```json
[{"id":"star_wars_iii","title":"Star Wars: Episode III - Revenge of the Sith","year":2005,"rating":7.7}]
```

We can also use simple text operators in our match:

```bash
# we can run this
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{ \
                \"title\":{ \
                   \"operator\":\"match\", \
                   \"value\":\"(jedi | force) -return\"}}}"

# or this
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{ \
                \"title\":{ \
                   \"operator\":\"match\", \
                   \"value\":\"awake*\"}}}"

# or even this
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{ \
                \"title\":{ \
                   \"operator\":\"match\", \
                   \"value\":\"wakens~\"}}}"
```

Any search in the previous example results in the following match:

```json
[{"id":"star_wars_vii","title":"Star Wars: Episode VII - The Force Awakens","year":2015}]
```

What we did with `*` can also be done with the `prefix` operator `Filter.prefix('title', 'awake')`. The fuzziness we added to `wakens` using `~`, can also be done explicitly with the `fuzzy` operator `Filter.fuzzy('title', 'wakens')`.

So far we are still just filtering data with filters. We can do so much more than that! If we use query search instead of filter to send those filters to the server, we can also get information about how relevant a document is to a given search, and order our results by this criteria. Let us introduce this with a new filter that allows us to query movies with a title similar to a given text:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{ \
                \"title\":{ \
                   \"operator\":\"similar\", \
                   \"value\":\"The attack an awakened Jedi uses to strike a Sith is pure force!\"}}}"
```

We receive not only the documents that match the filter, but also search metadata:

```json
{
  "total": 5,
  "documents": [
    {
      "title": "Star Wars: Episode VII - The Force Awakens",
      "id": "star_wars_vii"
    },
    {
      "title": "Star Wars: Episode V - The Empire Strikes Back",
      "id": "star_wars_v"
    },
    {
      "title": "Star Wars: Episode VI - Return of the Jedi",
      "id": "star_wars_vi"
    },
    {
      "title": "Star Wars: Episode III - Revenge of the Sith",
      "id": "star_wars_iii"
    },
    {
      "title": "Star Wars: Episode II - Attack of the Clones",
      "id": "staw_wars_ii"
    }
  ],
  "scores": {
    "star_wars_ii": 0.13102644681930542,
    "star_wars_iii": 0.13102644681930542,
    "star_wars_v": 0.13102644681930542,
    "star_wars_vi": 0.13102644681930542,
    "star_wars_vii": 0.5241057872772217
  },
  "queryTime": 1
}
```

Notice that the score of the `star_wars_vii` document is bigger than the other matches, indicating its title is more similar to the given filter than the others. The documents in the result are now ordered by the _relevance_ of the document, expressed as a number in the `scores` metadata, rather than the document's ID. Now we can show not only filtered results, but also order our results by relevance!

Want more? Well, let's make things even easier for the user! Adding one entry to the search query, we can automatically highlight the words that matched our query, showing not only how relevant the document is to the search, but also where it matches our criteria. We can do this with small changes in our previous search, using the following code:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{ \
                \"title\":{ \
                   \"operator\":\"similar\", \
                   \"value\":\"The attack an awakened Jedi uses to strike a Sith is pure force!\"}}, \
             \"highlight\":\"title\"}"
```

As you can see in the code below, our keywords are highlighted in the results:

```json
{
  "total": 5,
  "documents": [
    {
      "title": "Star Wars: Episode VII - The <em>Force</em> <em>Awakens</em>",
      "id": "star_wars_vii"
    },
    {
      "title": "Star Wars: Episode V - The Empire <em>Strikes</em> Back",
      "id": "star_wars_v"
    },
    {
      "title": "Star Wars: Episode VI - Return of the <em>Jedi</em>",
      "id": "star_wars_vi"
    },
    {
      "title": "Star Wars: Episode III - Revenge of the <em>Sith</em>",
      "id": "star_wars_iii"
    },
    {
      "title": "Star Wars: Episode II - <em>Attack</em> of the Clones",
      "id": "star_wars_ii"
    }
  ],
  "scores": {
    "star_wars_ii": 0.13102644681930542,
    "star_wars_iii": 0.13102644681930542,
    "star_wars_v": 0.13102644681930542,
    "star_wars_vi": 0.13102644681930542,
    "star_wars_vii": 0.5241057872772217
  },
  "queryTime": 1
}
```

The third search feature is also quite simple, but can be applied to generate meaningful statistical information about our data. What if we need to compare the average rating the first three movies received, with the last three movies? Well, we can do that with aggregations, using the following code:

```bash
curl -X "GET" "http://liferay.io/app/service/movies" \
     --header "Content-Type: application/json" \
     --data "{\"filter\":{\"year\":{\"operator\":\"<\",\"value\":1990}}, \
              \"aggregate\":{\"rating\":{\"name\":\"Old Movies\",\"operator\":\"avg\"}}, \
              \"type\":\"count\"}"
```

The `count` we added to the query informed the server we are not interested in the documents themselves, but rather the number of matches and search metadata. The result in this case will be the following data:

```json
{
  "total": 3,
  "queryTime": 13,
  "aggregations": {
    "Old Movies": 8.633333333333333
  }
}
```

Cool, right? Simply run another query for the newest movies, and then you'll have the data you need to compare them. There are some additional operators that you might find useful: `min`, `max`, `sum`, `histogram`, and even a generic `stats` that returns several statistics over the field. Take a look at the example below to see results using the additional operators:

```json
{
  "total": 3,
  "queryTime": 8,
  "aggregations": {
    "Old Movies": {
      "average": 8.633333333333333,
      "count": 3,
      "max": 8.8,
      "min": 8.4,
      "name": "Old Movies",
      "standardDeviation": null,
      "sum": 25.9,
      "sumOfSquares": null,
      "variance": null
    }
  }
}
```

The last search feature we will cover here needs a little setup before we put our documents in the datastore, but it's not as complicated as it sounds. First, let's cover some basics on the datatypes we support. As we said before, we offer a JSON storage, thus we support all JSON types, with the restriction that arrays must be of elements of the same type. Once we put a new document in a collection, we can automatically derive the datatype of the fields added, and bind the fields to that datatype. So, if we try to run the following request:

```bash
curl -X "PUT" "http://liferay.io/app/service/places/my_place/foo" \
     --data "bar"
```

And then run the following request afterwards:

```bash
curl -X "PUT" "http://liferay.io/app/service/places/my_place/foo" \
     --header "Content-Type: application/json" \
     --data "{\"key\":\"value\"}"
```

We will receive an error:

```json
{
  "code": 400,
  "message": "Bad Request",
  "errors": [
    {
      "reason": "invalidDocumentValue",
      "message": "Document cannot be saved. One or more document values could not be parsed to the correct type."
    }
  ]
}
```

The error was triggered because we could not convert the given data to the datatype bounded to that field. Of course, we can do simple conversions, for instance between numbers and strings, but whenever we fail, we will inform you something is wrong.

To access those datatypes, request the root of your service with a "GET", and you'll receive something like the following result:

```bash
curl -X "GET" "http://liferay.io/app/service"
```

```json
[
  {
    "movies": {
      "title": "string",
      "year": "long",
      "rating": "double"
    }
  },
  {
    "places": {
      "foo": "string"
    }
  }
]
```

> Notice to be able to read and write your `service`'s root path you need to map it with an *API endpoint* with data flag active.

If we want to inform the server of the datatype of a collection field before it receives its first document, we can POST/PATCH the data root with the mapping information:

```bash
curl -X "POST" "http://liferay.io/app/service" \
     --header "Content-Type: application/json" \
     --data "{\"places\":{\"location\":\"geo_point\"}}"
```

We can never update an already mapped field, but we can map new fields in an existing collection, as we did in the request above. When we manually map our collection, we can use some extra datatypes that are not mapped dynamically: `date`, `geo_point`, and `geo_shape`. We will focus on `geo_point` for this next feature.

So, we mapped a field called `location`, in the collection `places`, as representing a geolocation point. This means we can operate, filter, and aggregate the places we put in that collection, using geo filters over this field! Let's try something simple: find cinemas close to [London's Waterloo Station](https://www.google.com.br/maps/place/Waterloo+Station/@51.5031653,-0.1123051,17z/data=!3m1!4b1!4m2!3m1!1s0x487604b9c09f521d:0x1d0598197b5003ba?hl=en). To run the search criteria, we'll use the following code:

```bash
curl -X "GET" "http://liferay.io/app/service/places" \
    --header "Content-Type: application/json" \
    --data "{\"filter\":[ \
               {\"category\":{\"operator\":\"any\",\"value\":\"cinema\"}}, \
               {\"location\":{\"operator\":\"gd\",\"value\":{\"location\":\"51.5031653,-0.1123051\",\"max\":\"1mi\"}}}]}"
```

Our result is the following matches:

```json
[
  {
    "name": "BFI IMAX",
    "location": "51.5126928,-0.12052",
    "id": "116686224946770924",
    "category": [
      "cinema"
    ]
  },
  {
    "name": "Cinema Museum",
    "location": "51.501661,-0.1177734",
    "id": "116686224946770925",
    "category": [
      "cinema",
      "museum"
    ]
  },
  {
    "name": "Roxy Bar and Screen",
    "location": "51.5012603,-0.1146835",
    "id": "116686224946770926",
    "category": [
      "cinema",
      "bar",
      "restaurant"
    ]
  }
]
```

Now we can plug a map to our app, and let users see and filter places, with just a few lines of code.

<!-- </article> -->

<!-- <article id="4-watch-section"> -->

## 4. Watch

Unfortunately, you can't watch for realtime changes using cURL. Try using [Java](http://liferay.io/docs/java/understanding-data.html#4-watch) or [JavaScript](http://liferay.io/docs/js/understanding-data.html#4-watch) to accomplish that.

<!-- </article> -->

## 5. What's next?

Well, it's time to create your amazing app! We're really excited to see what you're going to build next. And remember, there are many features coming. Stay tuned!