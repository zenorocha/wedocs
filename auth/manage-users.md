# Manage Users

###### Create, delete or update users by using *WeDeploy™ Auth*.

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
		// User does not exist.
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

## What's Next?

* Now you can start building your apps with authentication.
