# Searching data

###### Searching Data Intro

<!-- <article id="searching-data"> -->

## Searching Data

We did some great stuff with basic HTTP methods, like create, update, and delete JSON documents. We also learned how to retrieve documents with filter, sort, and pagination. What if we need more powerful queries with our documents? In WeDeploy you can do a text search, handle user misspellings, and show the number of documents by category with your data, and much more.

First take a look at the text search. It's a simple, yet very powerful way to filter our results by a text query. Using the movie database we created before, let's search for a Star Wars movie by the episode title, like "Revenge of the Sith". We are not interested if the letter is in upper or lower case, since we are using English connectors like "of" and "the". We want something flexible enough that it will also work for texts like "The revenge of the Sith", or "Sith's revenge". Our match operator is flexible enough for both.

  ```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .get(Filter.match('title', "Sith's revenge"));
  ```

The result of the match operator query is the following entry:

  ```js
[{"id":"star_wars_iii","title":"Star Wars: Episode III - Revenge of the Sith","year":2005,"rating":7.7}]
  ```

We can also use simple text operators in our match:

  ```js
// we can run this
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .get(Filter.match('title', '(jedi | force) -return'));

// or this
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .get(Filter.match('title', 'awake*'));

// or even this
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .get(Filter.match('title', 'wakens~'));
  ```

Any search in the previous example results in the following match:

  ```js
[{"id":"star_wars_vii","title":"Star Wars: Episode VII - The Force Awakens","year":2015}]
  ```

What we did with * can also be done with the prefix operator Filter.prefix('title', 'awake'). The fuzziness we added to 'wakens' using ~, can also be done explicitly with the fuzzy operator Filter.fuzzy('title', 'wakens').

So far we are still just filtering data with filters. We can do so much more than that! If we use 'query search' instead of 'filter' to send those filters to the server, we can also get information about how relevant a document is to a given search, and order our results by this criteria. Let us introduce this with a new filter that allows us to query movies with a title similar to a given text:

  ```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .search(Filter.similar('title', 'The attack an awaken Jedi uses to strike a Sith is pure force!'))
  .get();
  ```

We receive not only the documents that match the filter, but also search metadata:

  ```js
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

Notice that the score of the star_wars_vii document is bigger than the other matches, indicating its title is more similar to the given filter than the others. The documents in the result are now ordered by the relevance of the document, expressed as a number in the scores metadata, rather than the document's ID. Now we can show not only filtered results, but also order our results by relevance!

Want more? Well, let's make things even easier for the user! Adding one entry to the search query, we can automatically highlight the words that matched our query, showing not only how relevant the document is to the search, but also where it matches our criteria. We can do this with small changes in our previous search, using the following code:

  ```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .search(Filter.similar('title', 'The attack an awakened Jedi uses to strike a Sith is pure force!'))
  .highlight('title')
  .get();
  ```

As you can see in the code below, our keywords are highlighted in the results:

  ```js
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

The third search feature is also quite simple, but can be applied to generate meaningful statistical information about our data. What if we need to compare the average rating the first three movies received, with the last three movies? We can do that with aggregations, using the following code:

  ```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
   .filter(Filter.lt('year', 1990))
   .aggregate('Old Movies', 'rating', 'avg')
   .count()
   .get();
  ```

The count we added to the query informed the server thatwe are not interested in the documents themselves, but rather the number of matches and search metadata. The result, in this case, will be the following data:

  ```js
{
  "total": 3,
  "queryTime": 13,
  "aggregations": {
    "Old Movies": 8.633333333333333
  }
}
  ```

Cool, right? Simply run another query for the newest movies, and then you'll have the data you need to compare them. There are some additional operators that you might find useful: min, max, sum, histogram, and even a generic stats that returns several statistics over the field. Take a look at the example below to see results using the additional operators:

  ```js
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

The last search feature we will cover here needs a little setup before we put our documents in the data store, but it's not as complicated as it sounds. First, let's cover some basics on the datatypes we support. As previously noted, we offer a JSON storage (we support all JSON types), with the restriction that arrays must be of elements of the same type. Once we put a new document in a collection, we can automatically derive the datatype of the added fields, and bind the fields to that datatype. So, if we try to run the following request:

  ```js
WeDeploy
  .url('http://data.datademo.wedeploy.me/places/my_place/foo')
  .put("bar");
  ```

And then run the following request:

  ```js
WeDeploy
  .url('http://data.datademo.wedeploy.me/places/my_place/foo')
  .put({ someObject: true });
  ```

We will receive an error:

  ```js
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

The error was triggered because we could not convert the given data to the data type bounded to that field. We can do simple conversions, such as between numbers and strings. However, whenever we fail, we will inform you something is wrong.

To access those datatypes, request the root of your service with a "GET", and you'll receive something like the following result:

  ```js
WeDeploy
  .url('http://data.datademo.wedeploy.me/')
  .get()
  .then(function(response) {
    console.log( response.body() );
  });
  ```

  ```js
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

Notice that in order to read and write your service's root path you need to map it with an API endpoint and data flag active.
If we want to inform the server of the data type of a collection field before it receives its first document, we can POST/PATCH the data root with the mapping information:

  ```js
WeDeploy
  .url('http://data.datademo.wedeploy.me/')
  .post({
     "places": {
       "location": "geo_point"
     }
  });
  ```

We can never update an already mapped field, but we can map new fields in an existing collection, as we did in the request above. When we manually map our collection, we can use some extra datatypes that are not mapped dynamically: date, geo_point, and geo_shape. We will focus on geo_point for this next feature.

So, we mapped a field called location, in the collection places, as representing a geolocation point. This means we can operate, filter, and aggregate the places we put in that collection, using geo filters over this field! Let's try something simple: find cinemas close to London's Waterloo Station. To run the search criteria, we'll use the following code:

  ```js
WeDeploy.url('http://data.datademo.wedeploy.me/places')
   .filter(Filter.any('category', 'cinema'))
   .filter(Filter.distance('location', '51.5031653,-0.1123051', '1mi'))
   .get();
   ```

Our result is the following matches:

  ```js
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

## Next Steps

Now that you have learned how to retrieve data, you can interact with [real-time feeds](/docs/data/real-time-feeds.html).
