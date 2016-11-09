# Sign-in With Google

###### You can let your users authenticate using their Google Accounts by integrating Google Sign-In into your app. *WeDeploy™ Authentication*.

<!-- <article id="sign-in"> -->

## Sign-in with google

To sign in by redirecting to the sign-in page, call `signInWithRedirect`:


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

<!-- <article id="setup-app-client-id-and-secret"> -->

## Setup app client id and secret

Create a client id and client secret by [registering your application](https://developers.google.com/youtube/registering_an_application) on Google. 

> Please be sure to add the callback url `http://<auth-container-id>.<project-id>.wedeploy.io/oauth/token` in your application.
> For local development, use `wedeploy.me` instead. To use with custom domains you can change the sufix `<project-id>.wedeploy.io` for your domain.

After retrieving the client id and client secret you can configure them as environment variables of the authentication `container.json`.

```json
{
	"id": "auth",
	"name": "Auth",
	"type": "wedeploy/auth",
	"env": {
		"WEDEPLOY_AUTH_GOOGLE": "true",
		"WEDEPLOY_AUTH_GOOGLE_CLIENT_ID": "<your-google-client-id>",
		"WEDEPLOY_AUTH_GOOGLE_CLIENT_SECRET": "<your-google-client-secret>"
	}
}
```

Or you can add those environment variables using the dashboard.

![Project Container Environment](https://cloud.githubusercontent.com/assets/1435318/20008152/2ceabade-a27e-11e6-9c86-435fc1c12412.png)

<!-- </article> -->

## What's next?

* Learn how to sign-up users using their [email and password into your app](/docs/auth/js/sign-in-with-password.html).
