# Building APIs

In Launchpad you can create apps, each composed of one or more services. A service exposes a REST interface that can be accessed via HTTP. We provide easy and powerful ways for you to describe and configure your APIs, so you can do more with less code.

## 1. Method

A *Method* works as a filter for requests that will be routed to this API definition. By default, all HTTP requests are mapped to an API, but you can change it to any subset you need. Launchpad currently supports the following HTTP methods:

* `GET`
* `POST`
* `PUT`
* `PATCH`
* `DELETE`

## 2. Endpoint

An *Endpoint* is the path used to access your API. There are many different combinations that you can use, which makes it really flexible and powerful.

1) By using the wildcard symbol `*`, you can match any request:

```text
/*
```

The example above will match paths like `/abc`, `/abc/def`, and so on.

2) An endpoint can also be mounted as a RESTful database. To enable data in your path, make sure the *Data* switcher is turned on. In order to properly represent a data path, we need to know which collection the path references.

```text
/collectionName/*
```

To access a resource from a collection, you can specify the resource ID on the request URL: `/collectionName/id`.

3) You can create URLs with parameters to match the request URL:

```text
/sum/:first/:second
```

4) The endpoint configuration also supports regular expressions:

```text
/sum/:first(\d+)/:second(\d+)
```

The example above will match any request with two numbers after `sum`. For instance it will match `/sum/123/456`, but not requests like `/sum/text` or `/sum/123/word`. The regular expression patterns allow you to filter the URLs, and name the extracted URL segment for future reference. 

> Notice the endpoint from two different APIs may overlap, or even be identical. In this case, your service will match the first API, in the order they were created, and if this one doesn't handle the request, or explicitly calls `next` inside the handler, then it will match and execute the second one.

## 3. Parameters

*Parameters* can be used to describe any parameter a request may receive. They are loaded from:

+ URL Query
+ Form URL Encoded
+ Multipart Form
+ JSON Body

The supported *Type* values are the JSON types: string, number, boolean, array and object.

The *Required* flag indicates the parameter must be present in the request.

The *Value* field defines a value that will be injected in the received request (note that this is not a _default_ value. This value will always be injected, and will be accumulated to existing values in the request). If a request fails to comply to any of these specifications, a `400 Bad Request` will be returned with errors for all parameters.

The *Validator* is a JavaScript expression that will be executed if a value is passed for this parameter. You can read more about it in the [Validator section](#7-validator).

## 4. Body

The body is a descriptor, similar to a parameter descriptor, with the exception of the *Value* field, which can be used to describe and validate the request body. It can be useful when the body is not a form URL encoded, multipart form, or a JSON object, making it impossible to validate it with the `parameters` field. One example is to validate body data in a API, using the following validator:

```
$body.startsWith("foo")
```

You can read more about it in the [Validator section](#7-validator).

## 5. Handler

A *Handler* is a very important part of understanding how to extend Launchpad.

This feature allows you to receive a request and process it. Currently, you can only write a handler using JavaScript, and they can be synchronous or asynchronous.

```js
function handler() {
   return 'Hello!'; // Synchronous
}
```

```js
function handler(request, response) {
   response.end('Hello!'); // Asynchronous
}
```

Imagine the handlers as route interceptors. When you have a path with a handler, it stops there. You can force it to continue the route matching by calling `request.next()`:

```js
function handler(request) {
  request.next(); // Call the next matching route
}
```

## 6. Authentication

The *Validator* field enables you to describe any JavaScript expression to authorize the request. You can read more about it in the [Validator section](#7-validator).

## 7. Validator

The *Validator* script will be executed in an environment where several request and server data will be available. In this environment, there are several global variables available to you that can be used to validate the request parameter, body, or even to authorize the request. 

The global variables are:

+ `$auth`: the authenticated user of this request. If the request was not authenticated, it will be `null`.
+ `$config`: the raw JSON data stored in the service's `config.json` file.
+ `$session`: all stored session data. If the request had no session cookie, it will be an empty map for the new session created for this request.
+ `$params`: the request params as they were loaded from url query and request body. All query and form parameters will be strings here.
+ `$values`: the parsed request params, as they are used for parameter validation. All query and form parameters will be parsed to JSON values.
+ `$body`: the parsed request body, according to the request `Content-Type`.
+ `$data`: the data view for this request, if a data path is mounted in the API path, and the request path represents a key to access any data resource (collection, document or inner field from a document). It will be `null` otherwise.

Some common validators are:

1) Authenticated users only

```js
$auth !== null
```

2) Mixed with dynamic values

```js
$auth.id === $params.id
```

3) Validate new data value agains old one

```js
$body.timestamp > $data.timestamp
```

> Note that the validator must return `true` for the request to be accepted.

## 7. What's Next?

* Read the ["Understanding Data"](http://liferay.io/docs/java/understanding-data.html) guide