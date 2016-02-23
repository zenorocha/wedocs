# Quickstart with JavaScript

###### Let's start from zero and build a RESTful API that stores and sync data.

<!-- <article id="1-request-invitation-section"> -->

## 1. Request invitation

The first thing you need to do to get started with Launchpad is to [request an invitation](http://liferay.io/#invitation).

At this moment, Launchpad is only available to a restricted group of developers, but don't worry we're sending invites on a daily basis.

<!-- </article> -->

<!-- <article id="2-create-an-api-section"> -->

## 2. Create an API

1. Once you have an account, go to [Dashboard](http://liferay.io/dashboard/apps) and click *Create App* and enter a name and URL for your app.

3. Select *Add Service*, and enter a name and URL to create your service. The service acts as a  container, which exposes your RESTful APIs.

4. Switch to the *API Builder*, and make sure the *Data* switcher is turned on.

5. Also check that *GET* and *POST* are selected in the *Method* section. These methods allow you to read and write on this URL.

5. In the *Endpoint* field, type `/items/*`. The `*` symbol indicates that any request starting with `items` will match this endpoint.

<!-- </article> -->

<!-- <article id="3-connect-to-your-api-section"> -->

## 3. Connect to your API

In order to send and receive requests to and from Launchpad, you need to include the [API Client for JavaScript](https://github.com/launchpad-project/api.js). This library provides a secure and reliable communication channel with Launchpad. Or if you prefer, you can use the CDN below:

```html
<script src="https://cdn.rawgit.com/launchpad-project/api.js/master/build/globals/api-min.js"></script>
```

<!-- </article> -->

<!-- <article id="4-read-write-data-section"> -->

## 4. Read & Write Data

Now, you can send any valid JSON object to Launchpad using `post()`. The following example post some information for a popular Science Fiction film:

```js
Launchpad
  .url('http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items')
  .post({
    "title": "Star Wars IV",
    "year": 1977
  })
  .then(function() {
    console.log('Data saved');
  });
```

Now that you have posted data to your database, you can read it using `get()` with no arguments:

```js
Launchpad
  .url('http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items')
  .get()
  .then(function(response) {
    console.log(response.body());
  });
```

Calling `body()` on the returned response will give you access to a JSON object.

You can also try this out on the *API explorer* tab of your service.

<!-- </article> -->

## 5. What's Next?

* Read the ["Building APIs"](http://liferay.io/docs/js/building-apis.html) guide
* Read the ["Understanding Data"](http://liferay.io/docs/js/understanding-data.html) guide