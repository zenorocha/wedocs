# Auth

###### Allow users to authenticate using passwords, popular federated identity providers like Google, Facebook, GitHub, and more using *WeDeploy™ Auth*.

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-sm" href="http://authjava.boilerplate.wedeploy.io" target="_blank">
    <span class="icon-16-external"></span>See Live Demo
  </a>
</div>

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-cli.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running Locally

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone -b js https://github.com/wedeploy/boilerplate-auth.git boilerplate-auth-js
cd boilerplate-auth-js
  ```

3. Link this container with the local infrastructure:

  ```text
we link
  ```

4. Now your container is ready to be used:

  ```text
http://authdemo.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-auth/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. [Create a project](http://dashboard.wedeploy.io/projects/create).
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `js` branch.
6. Click on *Update Project*.
7. Click on *Build All Repos* and wait a few seconds.
8. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://authdemo.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="key-capabilities"> -->

## Key capabilities

Easily add a complete sign-in system to your application. WeDeploy provides a ready-to-use auth solution that handles the UI flows for signing in users with email addresses and passwords, Google Sign-In, and GitHub Login.


**Email and password**

Authenticate users with their email addresses and passwords. Provides methods to create and manage users that use their email addresses and passwords to sign in, and sending password reset emails.

**GitHub**

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub.

**Google**

Create a client id and client secret by [registering your application](https://developers.google.com/youtube/registering_an_application) on Google.

**Manage Users**

Create, delete or update users with a simple API.

<!-- </article> -->

<!-- <article id="initializing-auth"> -->

## Initializing auth service

By using WeDeploy API client you can initialize the authentication service by referencing its URL, like in the example below.

```js
WeDeploy.auth('http://<containerID>.<projectID>.wedeploy.me');
```

After initializing the authentication service URL, WeDeploy client stores its information for future calls.

Note that if you are initializing an auth service pointing to the Cloud you should use the proper domain:

```js
WeDeploy.auth('http://<containerID>.<projectID>.wedeploy.io');
```

<!-- </article> -->

## What's Next?

* Now we're ready to start [authenticating accounts and growing our user base](/docs/auth/sign-in-with-github.html).
