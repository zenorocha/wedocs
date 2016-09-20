# Email

###### Send emails asynchronously and check their status using *WeDeploy™ Email*.

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-sm" href="http://boilerplate-email.wedeploy.io" target="_blank">
    <span class="icon-16-external"></span>See Live Demo
  </a>
</div>

<div class="guide-aux-cta">
  Or read the <a href="https://github.com/wedeploy/boilerplate-email" target="_blank">source code</a>.
</div>

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-cli.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running Locally

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone -b js https://github.com/wedeploy/boilerplate-email.git boilerplate-email-js
cd boilerplate-email-js
  ```

3. Link this container with the local infrastructure:

  ```text
we link
  ```

4. Now your container is ready to be used:

  ```text
http://emaildemo.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-email/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com).
3. [Create a project](http://dashboard.wedeploy.com/projects/create).
4. In the sidebar, click on *Deployment*.
5. Using your local machine, clone your Github fork:
  ```text
git clone https://github.com/{your_github_username}/boilerplate-email
  ```
6. Get into the folder: `cd boilerplate-email`.
7. Using the content on *Deployment* page. Add the WeDeploy remote url:
  ```text
git remote add wedeploy http://git.wedeploy.com/<projectID>.git
  ```
8. Push your data to wedeploy git server: `git push wedeploy master`.
9. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://emaildemo.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="sending-an-email"> -->

## Sending an Email

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

> For the full list of parameters, check this container's README in the [Dashboard](http://dashboard.wedeploy.io/).

As a result, we'll receive an email ID. This doesn't indicate that the email was already sent, it actually says that it was added to the email queue. That's why we have another API to check the email status.

<!-- </article> -->

<!-- <article id="checking-email-status"> -->

## Checking an Email Status

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

## What's Next?

* That's it! Now we're ready to start sending emails to our users.
