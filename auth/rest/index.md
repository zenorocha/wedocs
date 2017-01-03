# Auth

###### Allow users to authenticate using passwords, popular federated identity providers like Google, Facebook, GitHub, and more using *WeDeploy™ Auth*.

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running Locally

1. Clone this repository:

  ```text
git clone -b js https://github.com/wedeploy/boilerplate-auth.git boilerplate-auth-js
cd boilerplate-auth-js
  ```

2. Run this container locally:

  ```text
we dev
  ```

3. Now your container is ready to be used:

  ```text
http://authdemo.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-auth/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com).
3. [Create a project](http://dashboard.wedeploy.com/projects/create).
4. In the sidebar, click on *Deployment*.
5. Using your local machine, clone your Github fork:
  ```text
git clone https://github.com/<username>/boilerplate-auth
  ```
6. Get into the folder: `cd boilerplate-auth`.
7. Using the content on *Deployment* page. Add the WeDeploy remote url:
  ```text
git remote add wedeploy http://git.wedeploy.com/<projectID>.git
  ```
8. Push your data to wedeploy git server: `git push wedeploy master`.
9. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://authdemo.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="key-capabilities"> -->

## Key capabilities

Easily add a complete sign-in system to your application. WeDeploy provides a ready-to-use auth solution that handles the UI flows for signing in users with email addresses and passwords, Google Sign-In, GitHub and Facebook Login.


**Email and password**

Authenticate users with their email addresses and passwords. Provides methods to create and manage users that use their email addresses and passwords to sign in, and sending password reset emails.

**Google**

Create a client id and client secret by [registering your application](https://developers.google.com/youtube/registering_an_application) on Google.

**GitHub**

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub.

**Facebook**

Create an app ID by [registering your application](https://developers.facebook.com/docs/apps/register) on Facebook.

**Manage Users**

Create, delete or update users with a simple API.

<!-- </article> -->

## What's next?

* Now we're ready to [start managing your users](/docs/auth/rest/manage-users.html).
