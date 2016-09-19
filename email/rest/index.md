# Email

###### Send emails asynchronously and check their status using *WeDeploy™ Email*.

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-cli.html) if you need help setting that up.

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
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. [Create a project](http://dashboard.wedeploy.io/projects/create).
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `js` branch.
6. Click on *Update Project*.
7. Click on *Build All Repos* and wait a few seconds.
8. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://emaildemo.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="sending-an-email"> -->

## Sending an Email

Now that we have our container up and running, it's time to start sending some emails. We can use the API Client to facilitate the process of sending requests to WeDeploy.

### API Endpoints

#### `POST /emails`

Sends an email asynchronously and returns its ID.

###### Options

Parameter    | Type    | Description
------------ | ------- | ------------
bcc          | string  | Bcc recipient email address. Multiple addresses should be defined in multiple parameters.
cc           | string  | Cc recipient email address. Multiple addresses should be defined in multiple parameters.
from         | string  | Sender email address.
message      | string  | HTML content of your email message. Up to 5MB.
priority     | number  | Used by email clients to define a message's importance. From 1 to 5 where '1' is highest and '5' is the lowest priority.
replyTo      | string  | Append a reply-to address to your email message.
subject      | string  | Subject of your email. Up to 1MB.
to           | string  | Recipient email address. Multiple addresses should be defined in multiple parameters.

---

### `GET /emails/:id/status`


```

<!-- </article> -->

## What's Next?

* That's it! Now we're ready to start sending emails to our users.
