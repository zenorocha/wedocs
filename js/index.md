# Getting Started

###### Welcome to the step by step guide for developing web applications with WeDeploy. Before we begin, let's see how installation and setup works when working in the web platform.

<!-- <article id="1-create-a-project"> -->

## 1. Create a project

The first thing we need to do is to [create a free account](http://dashboard.wedeploy.com/login/signup). Once we're logged in, we'll be able to install containers, invite collaborators, and much more. For now, let's just [create a new project](http://dashboard.wedeploy.com/projects/create). Notice that every WeDeploy project has a unique URL ending in `wedeploy.io`, this will be used to access our containers.

<!-- </article> -->

<!-- <article id="2-install-api-client"> -->

## 2. Install API Client

In order to send/receive requests to/from WeDeploy, we need to include the JavaScript API Client. This library provides a secure and reliable communication channel with WeDeploy. We can do that by simply adding a script tag in a HTML file:

```html
<script src="https://cdn.rawgit.com/wedeploy/api.js/master/build/globals/api-min.js"></script>
```

Alternatively, you can use [npm](http://npmjs.com/) if you prefer to install it as a local dependency instead of using our CDN:

```sh
npm install wedeploy --save
```

Then, we just need to include a script tag like we did before:

```html
<script src="node_modules/wedeploy/build/globals/api-min.js"></script>
```

<!-- </article> -->

## 3. What's Next?

* Now we're ready to authenticate users, which we'll cover in the [next section](./user-authentication.html).