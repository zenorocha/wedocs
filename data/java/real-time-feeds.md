# Real-time feeds

###### *WeDeploy™ Data* inverts the traditional database architecture, instead of polling for changes, the developer can tell WeDeploy Data to continuously push updated query results to applications in real-time.

<!-- <article id="watching-data-changes"> -->

## Watching Data Changes

We presented a lot of features for data filtering and search. You may be wondering where the real-time aspect is in all of this. Well, it's throughout the features we just presented to you. To access our data in real-time, all we need to do is change the *WeDeploy™* API method we use to the `watch` method:

```js
WeDeploy.url('http://data.datademo.wedeploy.me/places')
   .filter(Filter.any('category', 'cinema'))
   .filter(Filter.distance('location', '51.5031653,-0.1123051', '1mi'))
   .watch()
   .on('changes', doSomethingWithReceivedData)
   .on('fail', handleFailure);

   function doSomethingWithReceivedData(data) {
     console.log(data);
   }

   function handleFailure(error) {
     console.log(error);
   }
```

Now every time the storage detects changes that affect the query you're watching, you will receive a changes notification with the response body you'd receive if you had done an HTTP GET instead. Furthermore, every time this change leads to an HTTP error response, you'll receive the error object in a fail notification on the client.


<!-- </article> -->


## What's Next?

* Now we're ready to save and retrieve data in real-time.
