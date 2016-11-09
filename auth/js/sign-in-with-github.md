# Sign-in With GitHub

###### You can let your users authenticate using their GitHub Accounts by integrating GitHub Sign-In into your app. *WeDeploy™ Authentication*.

<!-- <article id="sign-in"> -->

## Sign-in with gitHub

To sign in by redirecting to the sign-in page, call `signInWithRedirect`:


```js
var auth = WeDeploy.auth();

var provider = new auth.provider.Github();
provider.setProviderScope("user:email");

auth.signInWithRedirect(provider);

auth.onSignIn(function(user) {
	// Fires when user is signed in after redirect.
});
```

<!-- </article> -->

<!-- <article id="setup-app-client-id-and-secret"> -->

## Setup app client id and secret

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub. 

After retrieving the client id and client secret you can configure them as environment variables of the authentication `container.json`.

```json
{
	"id": "auth",
	"name": "Auth",
	"type": "wedeploy/auth",
	"env": {
		"WEDEPLOY_AUTH_GITHUB": "true",
		"WEDEPLOY_AUTH_GITHUB_CLIENT_ID": "<your-github-client-id>",
		"WEDEPLOY_AUTH_GITHUB_CLIENT_SECRET": "<your-github-client-secret>"
	}
}
```

Or you can add those environment variables using the dashboard.

![Project Container Environment](https://cloud.githubusercontent.com/assets/1435318/20008146/296d8a62-a27e-11e6-9e5a-f54bac5a5a85.png)

<!-- </article> -->

## What's next?

* Now we're ready to start [enabling other login providers into your app](/docs/auth/js/sign-in-with-google.html).
