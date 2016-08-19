# Sign-in With Password

###### You can let your users authenticate with WeDeploy using their email addresses and passwords. *WeDeploy™ Authentication*.

<!-- <article id="sign-in"> -->

## Sign-in with password

To sign in by email and password, call `signInWithEmailAndPassword`:


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

## What's Next?

* Now we're ready to [start managing your users](/docs/auth/manage-users.html).