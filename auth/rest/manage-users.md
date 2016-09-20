# Manage Users

###### Create, delete or update users by using *WeDeploy™ Auth*.

<!-- <article id="create-user"> -->

## Create an user

You create a new user in your WeDeploy project.

#### `POST /users`

Options:

<table class="table">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>email*</td>
      <td>string</td>
      <td>User Email</td>
    </tr>
    <tr>
      <td>password*</td>
      <td>string</td>
      <td>User Password</td>
    </tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>User Name</td>
    </tr>
    <tr>
      <td>photoUrl</td>
      <td>string</td>
      <td>User Photo URL</td>
    </tr>
  </tbody>
</table>

<!-- </article> -->


<!-- <article id="get-user"> -->

## Get user

#### `GET /users/1`


<!-- </article> -->

<!-- <article id="delete-user"> -->

## Delete user

#### `DELETE /users/1`

You can delete a user account with the delete method. For example:


<!-- </article> -->

<!-- <article id="update-user"> -->

## Update user

You can update a user's basic information. For example:

#### `PATH /users/1`

Options:

<table class="table">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>email</td>
      <td>string</td>
      <td>User Email</td>
    </tr>
    <tr>
      <td>password</td>
      <td>string</td>
      <td>User Password</td>
    </tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>User Name</td>
    </tr>
    <tr>
      <td>photoUrl</td>
      <td>string</td>
      <td>User Photo URL</td>
    </tr>
  </tbody>
</table>

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
