# Real-time Feeds

###### *WeDeploy™ Data* inverts the traditional database architecture, instead of polling for changes, the developer can tell WeDeploy Data to continuously push updated query results to applications in real-time.

<!-- <article id="watching-data-changes"> -->

## Watching data changes

We presented a lot of features for data filtering and search. You may be wondering where the real-time aspect is in all of this. Well, it's throughout the features we just presented to you. To access our data in real-time, all we need to do is change the *WeDeploy™* API  `get` method to use to the `watch` method:

```js
var data = WeDeploy.data('http://datademo.wedeploy.io');

data.watch('movies')
.on('changes', function(data){
   console.log(data);
})
.on('fail', function(error){
   console.log(error);
});
```

Now every time the storage detects changes that affect the query you're watching, you will receive a changes notification with the response body you'd receive if you had done an HTTP GET instead. Furthermore, every time this change leads to an HTTP error response, you'll receive the error object in a fail notification on the client.

## Watching with advanced filters

To present data using advanced search is simple as performing normal queries. You just would need to keep using the `watch` method and apply any filter you desire.

```js
WeDeploy.data('http://datademo.wedeploy.io')
.where('category', 'cinema')
.or('category', 'cartoon')
.watch('movies')
.on('changes', function(data){
   console.log(data);
})
.on('fail', function(error){
   console.log(error);
});
```

## Getting the latest changes

The data service uses a query limit `500` by default. In order to always get the latest new record, you would need to limit the query by `1` and order by `id` `desc`.

```js
WeDeploy.data('http://datademo.wedeploy.io')
.limit(1)
.orderBy('id', 'desc')
.watch('movies')
.on('changes', function(data){
   console.log(data);
})
.on('fail', function(error){
   console.log(error);
});
```

<!-- </article> -->


## What's next?

* Now we're ready to save and retrieve data in real-time.
