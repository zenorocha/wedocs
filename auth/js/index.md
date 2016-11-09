# Auth

###### Allow users to authenticate using passwords, popular federated identity providers like Google, Facebook, GitHub, and more using *WeDeploy™ Auth*.

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-sm" href="http://boilerplate-auth.wedeploy.io" target="_blank">
    <span class="icon-16-external"></span>See Live Demo
  </a>
</div>

<div class="guide-aux-cta">
  or read the <a href="https://github.com/wedeploy/boilerplate-auth/tree/js" target="_blank">source code</a>.
</div>

<!-- <article id="install-dependencies"> -->

## Install dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running locally

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

## Deploying to the cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-auth/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com) and create a project.
3. In the sidebar, click on *Deployment*.
4. Using your local machine, clone your Github fork:
  ```text
git clone -b js https://github.com/<username>/boilerplate-auth
  ```
5. Get into the folder: `cd boilerplate-auth`.
6. Using the content on *Deployment* page. Add the WeDeploy remote url:
  ```text
git remote add wedeploy http://git.wedeploy.com/<projectID>.git
  ```
7. Push your data to wedeploy git server: `git push wedeploy js:master`.
8. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://boilerplate-auth.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="key-capabilities"> -->

## Key capabilities

Easily add a complete sign-in system to your application. WeDeploy provides a ready-to-use auth solution that handles the UI flows for signing in users with email addresses and passwords, Google Sign-In, GitHub and Facebook Login.


**Email and password**

Authenticate users with their email addresses and passwords. Provides methods to create and manage users that use their email addresses and passwords to sign in, and sending password reset emails.

**Google**

Create a client id and client secret by [registering your application](https://developers.google.com/identity/protocols/OAuth2) on Google.

**GitHub**

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub.

**Facebook**

Create an app ID by [registering your application](https://developers.facebook.com/docs/apps/register) on Facebook.

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

## What's next?

* Now we're ready to [start managing your users](/docs/auth/js/manage-users.html).
