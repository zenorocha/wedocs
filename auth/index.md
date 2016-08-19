# Auth

###### Allow users to authenticate using passwords, popular federated identity providers like Google, Facebook and Twitter, and more using *WeDeploy™ Auth*.

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** is running. Make sure to [visit the installation guide](/docs/intro/using-the-cli.html) if you need help setting that up.

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

Authenticate users with their email addresses and passwords. Provides methods to create and manage users that use their email addresses and passwords to sign in, also handles sending password reset emails.

**GitHub**

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub.

**Google**

Create a client id and client secret by [registering your application](https://developers.google.com/youtube/registering_an_application) on Google. 

<!-- </article> -->

<!-- <article id="initializing-auth"> -->

## Initializing auth service

```js
WeDeploy.auth('http://auth.<projectID>.wedeploy.me');
```


## Initializing auth service on the Cloud

```js
WeDeploy.auth('http://auth.<projectID>.wedeploy.io');
```

After initialized the authentication service url, WeDeploy client stores its information for future calls.

<!-- </article> -->

<!-- <article id="sign-in-with-password"> -->

## Sign-In with email and password

You can use WeDeploy Authentication to let your users authenticate with WeDeploy using their email addresses and passwords.

```js
WeDeploy
	.auth()
	.signInWithEmailAndPassword("user@domain.com", "password")
	.then(function(user) {
		// User is signed in.
	})
	.catch(function(err) {  
	  // User is not signed in.
	});
```

<!-- </article> -->

<!-- <article id="sign-in-with-providers”> -->

## Sign-in with GitHub

You can let your users authenticate with WeDeploy using their GitHub accounts by integrating GitHub authentication into your app.

```js
var auth = WeDeploy.auth();

var provider = new auth.provider.Github();
provider.setProviderScope("user:email");

auth.signInWithRedirect(provider);

auth.onSignIn(function(user) {
	// Fires when user is signed in after redirect.
});
```

## Sign-in with Google

You can let your users authenticate with WeDeploy using their Google Accounts by integrating Google Sign-In into your app. 

```js
var auth = WeDeploy.auth();

var provider = new auth.provider.Google();
provider.setProviderScope("email");

auth.signInWithRedirect(provider);

auth.onSignIn(function(user) {
	// Fires when user is signed in after redirect.
});
```

<!-- </article> -->

<!-- <article id="sign-out"> -->

## Sign-out

```js
WeDeploy
	.auth()
	.signOut()
	.then(function() {
		// User is signed out.
	})
	.catch(function(err) {  
	  // User was signed out.
	});
```

<!-- </article> -->

<!-- <article id="create-user"> -->

## Create user

You create a new user in your WeDeploy project by calling the `createUser` method or by signing in a user for the first time using a federated identity provider, such as Google Sign-In or Facebook Login.

```js
WeDeploy
	.auth()
	.createUser({
		email: 'user@domain.com',
		password: 'abc'
	})
	.then(function(user) {  
		// Successfully created.
	})
	.catch(function(err) {  
	  // Not created.
	});
```

<!-- </article> -->

<!-- <article id="get-current-user"> -->

## Get current user

```js
var currentUser = WeDeploy.auth().currentUser;

if (currentUser) {
	// User is signed in.
} else {
	// No user is signed in.
}
```

<!-- </article> -->

<!-- <article id="get-user"> -->

## Get user

```js
WeDeploy
	.auth()
	.getUser(userId)
	.then(function(user) {
		// User found.
	})
	.catch(function(err) {  
		// User does not exists.
	});
```

<!-- </article> -->

<!-- <article id="delete-user"> -->

## Delete user

You can delete a user account with the delete method. For example:

```js
var currentUser = WeDeploy.auth().currentUser;

currentUser.deleteUser()
	.then(function() {  
		// Successfully deleted.
	})
	.catch(function(err) {  
	  // Not deleted.
	});
```


<!-- </article> -->

<!-- <article id="update-user"> -->

## Update user

You can update a user's basic information. For example:

```js
var currentUser = WeDeploy.auth().currentUser;

currentUser.updateUser({
	password: "password",
	email: "eleven@hawkinslabs.com",
	name: "Eleven",
	photoUrl: "https://hawkinslabs.com/011/profile.jpg"
})
.then(function() {  
	// Successfully updated.
})
.catch(function(err) {  
  // Not updated.
});
```

<!-- </article> -->

<!-- <article id="reset-email"> -->

## Send a password reset email

You can send a password reset email to a user with the sendPasswordResetEmail method. For example:

```js
WeDeploy
	.auth()
	.sendPasswordResetEmail("user@domain.com")
	.then(function() {
		// Email sent.
	})
	.catch(function(err) {  
	  // An error happened.
	});
```

<!-- </article> -->

## What's Next?

* Now we're ready to start authenticating and grow our user base.
