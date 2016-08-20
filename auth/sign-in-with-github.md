# Sign-in With GitHub

###### You can let your users authenticate using their GitHub Accounts by integrating GitHub Sign-In into your app. *WeDeploy™ Authentication*.

<!-- <article id="sign-in"> -->

## Sign-in with GitHub

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

Create a client id and client secret by [registering your application](https://github.com/settings/applications/new) on GitHub. After retrieving the client id and client secret you can configure them as environment variables of the authentication `container.json`.

```json
{
	"id": "auth",
	"name": "Auth",
	"type": "wedeploy/auth",
	"env": {
		"WEDEPLOY_AUTH_EMAIL_CONTENT": "Hello ${user.name},<br><br>Follow this link to reset your ${project.name} password:<br><br><a href=\"http://auth.${project.domain}/reset.html?code=${resetCode}&email=${user.email}\" target=\"_blank\">http://auth.${project.domain}/reset.html?code=${resetCode}&email=${user.email}</a><br><br>If you didn't ask to reset your password, you can ignore this email.<br><br>Thanks,<br><br><em>WeDeploy Team</em>",
		"WEDEPLOY_AUTH_EMAIL_REGEX": "^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\\.[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$",
		"WEDEPLOY_AUTH_GITHUB": "true",
		"WEDEPLOY_AUTH_GITHUB_CLIENT_ID": "",
		"WEDEPLOY_AUTH_GITHUB_CLIENT_SECRET": "",
		"WEDEPLOY_AUTH_SECURE_FIELDS": "providers,password,resetKey,supportedScopes"
	}
}
```

<!-- </article> -->

## What's Next?

* Now we're ready to start [enabling other login providers into your app](/docs/auth/sign-in-with-google.html).
