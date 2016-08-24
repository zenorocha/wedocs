# Saving data

###### To add new data to the WeDeploy Data,

<!-- <article id="insert-data"> -->

## Insert data

Writing new data is as simple as sending a JSON.

```js
WeDeploy
  .url('http://data.datademo.wedeploy.me/movies')
  .post({
    "title": "Star Wars IV",
    "year": 1977,
    "rating": 8.7
  })
  .then(function(clientResponse) {
    console.log(clientResponse.body())
  });
```

This operation will return the newly created document, with the following generated ID:

```js
{
  "title": "Star Wars",
  "id":" 115992383516607958",
  "year": 1977,
  "rating": 8.7
}
```
<!-- </article> -->

<!-- <article id="url-scope-structure"> -->

## URL Scope structure

The URL we just created stored a new document in our app's service inside the "movies" collection. More information on how to set up this datastore URL can be seen in the section Building APIs. For now, we only need to know that within the path where the data is mounted. The URL will be interpreted as a key that points to a stored resource like the one below:

```text
/collectionName/documentId/documentProperty/documentInnerProperty
```

For example, to reference the newly created Star Wars rating, we can use the path:

```text
http://data.datademo.wedeploy.me/movies/115992383516607958/rating
```

At this point, update and delete operations can be performed at any level of the resource. For example, we can update the existing document by adding a new field:

```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
   .path('115992383516607958')
   .form('stars', 'Mark Hamill')
   .form('stars', 'Harrison Ford')
   .form('stars', 'Carrie Fisher')
   .patch();
```

Note in the example above, the data was sent as request form attributes. The response is the modified document:

```js
{
  "title": "Star Wars",
  "id": "115992383516607958",
  "year": 1977,
  "rating": 8.7,
  "stars": ["Mark Hamill", "Harrison Ford", "Carrie Fisher"]
}
```

We can use the PUT method at the document level to create a document with a custom ID, or to override an existing one. The following example creates a new entry with the custom ID star_wars_v:

```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies')
  .path('star_wars_v')
  .put({
    "title":"Star Wars: Episode V - The Empire Strikes Back",
    "year":1980,
    "rating":8.8
  })
  .then(function() {
    console.log('Data saved');
  });
```

To override an existing entry you would just specify the existing ID.

To delete a field, document, or the entire collection, we use the DELETE method:

```js
WeDeploy.url('http://data.datademo.wedeploy.me/movies/star_wars_v/title').delete();
WeDeploy.url('http://data.datademo.wedeploy.me/movies/star_wars_v').delete();
WeDeploy.url('http://data.datademo.wedeploy.me/movies').delete();
```

<!-- </article> -->


## Next Steps

Now that you have learned how to create data, you can interact [retrieving data](/docs/data/retrieving-data.html).
