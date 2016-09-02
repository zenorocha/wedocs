# Updating data

###### The update() function updates an existing record in the database using the current attributes. It then returns the newly updated object in the Promise response.

<!-- <article id="updating-existing-data"> -->

## Updating existing data

> By default, all the operation access to your database are restricted so only authenticated users can manipulate data. To get started without setting up Authentication, you can configure your rules for public access. To learn more about rules, see [configuring rules](/docs/data/configuring-rules.html) section.

Updating existing data is as simple as sending a JSON.

```js

client = WeDeploy.data('http://datademo.wedeploy.io');

client.update('movies/115992383516607958', {
  "rating": 9.1
}).then(function(response) {
  console.log(response);
});

```
As you can see, the data api uses Promises to help you to make async requests.

This operation will return the updated document with the new rating:

```js
{
  "id":" 115992383516607958",
  "title": "Star Wars IV",
  "year": 1977,
  "rating": 9.1
}
```
<!-- </article> -->

## Next Steps

Now that you have learned how to update data, you can interact [deleting data](/docs/data/deleting-data.html).
