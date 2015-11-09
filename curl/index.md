# Quickstart

Let's start from zero and build a RESTful API that stores and sync data.

## 1. Request invitation

The first thing you need to do to get started with Launchpad is to [request an invitation](http://liferay.io/#invitation).

At this moment, Launchpad is only available to a restricted group of developers, but don't worry we're sending invites on a daily basis.

## 2. Create an API

1. Once you have an account, go to [Dashboard](http://liferay.io/dashboard/apps) and click *Create App* and enter a name and URL for your app.

3. Select *Add Service*, and enter a name and URL to create your service. The service acts as a  container, which exposes your RESTful APIs.

4. Switch to the *API Builder*, and make sure the *Data* switcher is turned on.

5. Also check that *GET* and *POST* are selected in the *Method* section. These methods allow you to read and write on this URL.

5. In the *Endpoint* field, type `/items/*`. The `*` symbol indicates that any request starting with `items` will match this endpoint.

## 3. Connect to your API

The cURL workflow is different from Java and JavaScript workflows because it doesn't need an API Client. In this case, connecting to your API is as simple as requesting an URL.

## 4. Read & Write Data

Now, you can send any valid JSON object to Launchpad using `POST`. The following example post some information for a popular Science Fiction film:

```bash
curl -X "POST" "http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items" \
     --data-urlencode "title=Star+Wars+IV" \
     --data-urlencode "year=1977"
```

Now that you have posted data to your database, you can read it using `GET` with no arguments:

```bash
curl -X "GET" "http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items"
```

You can also try this out on the *API explorer* tab of your service.

## 5. What's Next?

* Read the ["Building APIs"](http://liferay.io/docs/curl/building-apis.html) guide
* Read the ["Understanding Data"](http://liferay.io/docs/curl/understanding-data.html) guide