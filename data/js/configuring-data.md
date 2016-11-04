# Configuring Data

###### The `api.json` and `api-*.json` files allow us to configure the accessible paths for each data service.

<!-- <article id="undestanding-configuration-files"> -->

## Understanding configuration files

By default WeDeploy Data service is going to use all the JSON files starting with `api-*` and also the file `api.json`.

These files are used to help you manage features such as path validation, authentication, and params validation.

The api JSON files are located at the same path of the `./container.json` and are used following the ordering filesystem.

<!-- </article> -->

<!-- <article id="json-attributes"> -->

## JSON attributes

After understanding how the api configuration files work, it's time to learn what are the supported attributes:

<table class="table">
  <tr>
    <th>Field</th> <th>Description</th>
  </tr>
  <tr>
    <td>path</td> <td>The path that represents the collection used to handle the request data.</td>
  </tr>
  <tr>
    <td>data</td> <td>Tells the service if the request to a collection should be stored or not.</td>
  </tr>
  <tr>
    <td>description</td> <td>Used to describe the behavior of an endpoint.</td>
  </tr>
  <tr>
    <td>auth</td> <td>Used to define authentication rules for the endpoint.</td>
  </tr>
  <tr>
    <td>method</td> <td>HTTP method allowed for the request.</td>
  </tr>
  <tr>
    <td>parameters</td> <td>Parameters and validation rules for the collection.</td>
  </tr>
</table>

##### path

A path represents the resource used to store your project data.

```
[
  {
    "path": "/movies/:movieId"
  },
  {
    "path": "/fruits/*"
  }
]
```

##### data

You can create endpoints just for validation, in this case, data is used to finish the request in case you just need a validation or want to store the request in the collection.

```json
[
  {
    "path": "/fruits/*",
    "data": true
  }
]
```

##### description

Used to describe the behavior of an endpoint.

```json
[
  {
    "description": "Returns actors of a movie",
    "path": "/movies/:movieId/actors",
    "method": "GET"
  }
]
```

##### auth

You can unauthorized applications and users to access any endpoint by using the auth field. The example below verify if the application is authenticated in order to perform the request:

```json
[
  {
    "path": "/movies/*",
    "auth": {
      "validator": "$auth != null"
    }
  }
]
```

##### method

Specifies the HTTP method used for the request. In the example bellow, it allows a GET request and if you try to do a PUT or DELETE the route will not be recognized and will fail.

```json
[
  {
    "path": "/moives/:movieId",
    "data": true,
    "method": "GET"
  }
]
```

##### parameters

You generally would use `parameters` to force validation in order to make sure that the params sent to a collection follow predefined rules.

```json
[
  {
    "description": "Creates a new movie",
    "path": "/movies",
    "method": "POST",
    "parameters": {
      "title": {
        "type": "string"
      }
    },
    "data": true
  }
]
```

<!-- </article> -->

<!-- <article id="allowing-usage-of-all-the-collections"> -->

## Allowing usage of all the collections

In order to freely use any collection with any kind of operation, you just need to add the following content in your `api.json`.

```json
[
  {
    "path": "/*",
    "data": true
  }
]
```

The path `/*` tells the data service to allow any request to the base path of the data service.

<!-- </article> -->

<!-- <article id="validating-resources"> -->

## Validating resources

The Validator script will be executed in an environment where several request and server data will be available. In this environment, there are several global variables available to you that can be used to validate the request parameter, body, or even to authorize the request.

The validator can be used as an integration with the Auth service:

```json
{
  "path": "/movies/*",
  "auth": {
    "validator": "$auth != null"
  }
}
```

The global variables are:

<table class="table">
  <tr>
    <th>Variable</th> <th>Description</th>
  </tr>
  <tr>
    <td>$auth</td> <td>The authenticated user of this request. If the request was not authenticated, it will be null.</td>
  </tr>
  <tr>
    <td>$config</td> <td>The raw JSON data stored in the service's config.json file.</td>
  </tr>
  <tr>
    <td>$session</td> <td>All stored session data. If the request had no session cookie, it will be an empty map for the new session created for this request.</td>
  </tr>
  <tr>
    <td>$params</td> <td>The request params as they were loaded from url query and request body. All query and form parameters will be strings here.</td>
  </tr>
  <tr>
    <td>$values</td> <td>The parsed request params, as they are used for parameter validation. All query and form parameters will be parsed to JSON values.</td>
  </tr>
  <tr>
    <td>$body</td> <td>The parsed request body, according to the request Content-Type.</td>
  </tr>
  <tr>
    <td>$data</td> <td>The data view for this request, if a data path is mounted in the API path, and the request path represents a key to access any data resource (collection, document or inner field from a document). It will be null otherwise.</td>
  </tr>

</table>

Some common validators are:

1) Authenticated users only:

```text
$auth !== null
```

2) Mixed with dynamic values:

```text
$auth.id === $params.id
```

3) Validate new data value agains old one:

```text
$body.timestamp > $data.timestamp
```

4) Multiple contitional validation:

```text
$auth !== null && $auth.id === $params.id
```

<!-- </article> -->

## What's next?

Now that you have *WeDeploy™ Data* API settled up, you can interact [saving data](/docs/data/js/saving-data.html).
