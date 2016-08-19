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

<!-- <article id="signing-in"> -->

## Key capabilities

Easily add a complete sign-in system to your application. WeDeploy provides a ready-to-use auth solution that handles the UI flows for signing in users with email addresses and passwords, Google Sign-In, and GitHub Login.

**Email and password**

Authenticate users with their email addresses and passwords. Provides methods to create and manage users that use their email addresses and passwords to sign in, also handles sending password reset emails.

**GitHub**

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub.

**Google**

Create a client id and client secret by [registering your application](https://developers.google.com/youtube/registering_an_application) on Google. 

## Initializing auth service locally

```js
WeDeploy.auth('http://auth.<projectID>.wedeploy.me');
```

## Initializing auth service on the Cloud

```js
WeDeploy.auth('http://auth.<projectID>.wedeploy.io');
```

After initialized the authentication service url, WeDeploy client stores its information for future calls.

## Sign-In With Password

```js
WeDeploy
	.auth()
	.signInWithPassword("user@domain.com", "password")
	.then(() => {
		// User is signed in.
	})
	.catch((err) -> {  
	  // User is not signed in.
	});
```

## Sign-In With Redirect (GitHub)

```js
var auth = WeDeploy.auth();

var provider = new auth.provider.Github();
provider.setProviderScope("user");

auth.signInWithRedirect(provider);

auth.onSignIn((user) => {
	// Fires when user is signed in after redirect.
});
```

## Sign-In With Redirect (Google)

```js
var auth = WeDeploy.auth();

var provider = new auth.provider.Google();
provider.setProviderScope("profile");

auth.signInWithRedirect(provider);

auth.onSignIn((user) => {
	// Fires when user is signed in after redirect.
});
```

## Sign-Out

```js
WeDeploy
	.auth()
	.signOut()
		.then(() => {
			// User is signed out.
		})
		.catch((err) -> {  
		  // User was signed out.
		});
```

## Create User

```js
WeDeploy
	.auth()
	.createUser({
		email: 'brian.chan@liferay.com',
		password: 'abc'
	})
	.then((user) -> {  
		// Successfully created.
	})
	.catch((err) -> {  
	  // Not created.
	});
```

## Get User

```js
var currentUser = WeDeploy.auth().currentUser;

if (currentUser) {
	// User is signed in.
} else {
	// No user is signed in.
}
```

```js
WeDeploy
	.auth()
	.getUser(userId)
	.then((user) -> {
		// User found.
	})
	.catch((err) -> {  
		// User does not exists.
	});
```


## Delete User

```js
var currentUser = WeDeploy.auth().currentUser;

currentUser.deleteUser()
	.then(() -> {  
		// Successfully deleted.
	})
	.catch((err) -> {  
	  // Not deleted.
	});
```


## Update User

```js
var currentUser = WeDeploy.auth().currentUser;

currentUser.updateUser({
	password: "password",
	email: "eleven@hawkinslabs.com",
	name: "Eleven",
	photoUrl: "https://hawkinslabs.com/011/profile.jpg"
})
.then(() -> {  
	// Successfully updated.
})
.catch((err) -> {  
  // Not updated.
});
```

## Send a password reset email

```js
WeDeploy
	.auth()
	.sendPasswordResetEmail("michael.han@liferay.com")
	.then(() => {
		// Email sent.
	})
	.catch((err) -> {  
	  // An error happened.
	});
```

<!-- </article> -->

## What's Next?

* Now we're ready to start authenticating and grow our user base.
