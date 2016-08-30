# Saving data

###### The create() function creates a new record in the database using the current attributes. It then returns the newly saved object in the Promise response.

<!-- <article id="inserting-new-data"> -->

## Inserting new data

> By default, all the operation access to your database are restricted so only authenticated users can manipulate data. To get started without setting up Authentication, you can configure your rules for public access. To learn more about rules, see [configuring rules](/docs/data/configuring-rules.html) section.

Writing new data is as simple as sending a JSON.

```js

client = WeDeploy.data('http://datademo.wedeploy.io');

client.create('movies', {
  "title": "Star Wars IV",
  "year": 1977,
  "rating": 8.7
}).then(function(response) {
  console.log(response);
});

```
As you can see, the data api uses Promises to help you to make async requests.

This operation will return the newly created document, with the following generated ID:

```js
{
  "id":" 115992383516607958",
  "title": "Star Wars IV",
  "year": 1977,
  "rating": 8.7
}
```
<!-- </article> -->

<!-- <article id="inserting-multiple-data"> -->

## Inserting multiple data

With the same method you're able to create multiple data instead using the method `.create` multiple times.
You just need to use an array instead an object as the second param.

```js
client = WeDeploy.data('http://datademo.wedeploy.io');

client.create('movies', [
  {
    "title": "Star Wars III",
    "year": 2005,
    "rating": 8.0
  },
  {
    "title": "Star Wars II",
    "year": 2002,
    "rating": 8.6
  }
]).then(function(response) {
  console.log(response);
});

```

This operation will return the newly created array of documents, with the following generated IDs:

```js
[
  {
    "id":" 115992383516607959",
    "title": "Star Wars III",
    "year": 2005,
    "rating": 8.0
  },
  {
    "id":" 115992383516607954",
    "title": "Star Wars II",
    "year": 2002,
    "rating": 8.6
  }
]
```
<!-- </article> -->

<!-- <article id="inserting-new-fields-in-an-existing-collection"> -->

## Inserting new fields in an existing collection

WeDeploy Data service is really flexible in therms of data structure. You're able to insert new fiels in a collection by adding the new key in the object param.

```js
client = WeDeploy.data('http://datademo.wedeploy.io');

client.create('movies', [
  {
    "title": "Star Wars I",
    "obs": "First in ABC order",
    "year": 1999,
    "rating": 9.0
  }
]).then(function(response) {
  console.log(response);
});

```

This operation will return the newly created document, with the following generated ID:

```js
{
  "id":" 115992383516607954",
  "title": "Star Wars I",
  "obs": "First in ABC order",
  "year": 1999,
  "rating": 9.0
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
<!-- </article> -->

## Next Steps

Now that you have learned how to create data, you can interact [updating data](/docs/data/updating-data.html).
