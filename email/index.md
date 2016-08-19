# Email

###### Send emails asynchronously and easily check their status using *WeDeploy™ Email*.

<!-- <article id="1-install-email-container"> -->

## 1. Install Email Container

First, we need to make sure that *WeDeploy™ Email* is installed. We can do that by following these steps:

1. Go to the Dashboard.
2. Select your project.
3. Click on *"Install Container"*.
4. Select *"WeDeploy Email"*
5. Click on *"Install Container"*.

Once we installed it, WeDeploy will provide an endpoint for this container. This endpoint will be used to access all the RESTful APIs that this container exposes. A container endpoint looks like this `<containerID>.<projectID>.wedeploy.io`, for example: `email.sample.wedeploy.io`.

<div class="guide-download">
	<a href="https://github.com/wedeploy/boilerplate-email/archive/js.zip" class="btn btn-accent btn-sm"><span class="icon-16-download"></span>Download JavaScript Email Boilerplate</a>
</div>

<!-- </article> -->

<!-- <article id="2-send-an-email"> -->

## 2. Send an Email

Now that we have our container up and running, it's time to start sending some emails. We can use the API Client to facilitate the process of sending requests to WeDeploy.

In order to send emails, we have to make a `POST` request to `/emails` passing some required parameters like `from`, `to`, and `subject`:

```js
WeDeploy
	.url('http://<containerID>.<projectID>.wedeploy.io/emails')
	.form('from', 'from@domain.com')
	.form('to', 'to@domain.com')
	.form('subject', 'Hi there!')
	.post()
	.then(function(response) {
		console.log('Email ID:', response.body());
	})
	.catch(function(error) {
		// Some error has happened
	});
```

> For the full list of parameters, check [github.com/wedeploy/email](https://github.com/wedeploy/email#readme).

As a result, we'll receive an email ID. This doesn't indicate that the email was already sent, it actually says that it was added to the email queue. That's why we have another API to check the email status.

<!-- </article> -->

<!-- <article id="3-check-email-status"> -->

## 3. Check an Email Status

In order to check if an email was sent or not, we can use the email ID from the previous example, e.g. `123`, and send a `GET` request to `/emails/123/status`.

```js
WeDeploy
	.url('http://<containerID>.<projectID>.wedeploy.io/emails/<emailID>/status')
	.get()
	.then(function(response) {
		console.log('Email status:', response.body());
	})
	.catch(function(error) {
		// Some error has happened
	});
```

<!-- </article> -->

## 4. What's Next?

* That's it! Now we're ready to host our static files, which we'll cover in the [next section](./hosting/).
