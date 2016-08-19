# Email

###### Send emails asynchronously and easily check their status using *WeDeploy™ Email*.

<!-- <article id="install-dependencies"> -->

## Install Dependencies

WeDeploy relies on three dependencies, make sure to download them before we continue.

**A) Git**

Git is a version control system that is required for working with WeDeploy projects.

* [Mac OS X](https://git-scm.com/download/mac)
* [Windows](https://git-scm.com/download/win)
* [Linux](https://git-scm.com/download/linux)

**B) Docker**

Docker is a tool that automates the deployment of WeDeploy containers in your local environment.

* [Mac OS X](https://download.docker.com/mac/stable/Docker.dmg)
* [Windows](https://download.docker.com/win/stable/InstallDocker.msi)
* [Linux](https://docs.docker.com/engine/installation/linux/)

**C) WeDeploy CLI**

The WeDeploy Command-Line Interface (CLI) is a tool that wraps the WeDeploy Platform API, providing support for things like creating, managing and scaling applications.

```text
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -s | bash
```

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running locally

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

## Deploying to the cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-email/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. Create a project.
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `master` branch.
6. Click on *Update Project* and wait a few seconds.
7. Once you see it in the Dashboard, your container will be ready to be used.

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

> For the full list of parameters, check [github.com/wedeploy/email](https://github.com/wedeploy/email#readme).

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
