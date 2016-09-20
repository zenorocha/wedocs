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

### API Endpoints

#### `POST /emails`

Sends an email asynchronously and returns its ID.

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
      <td>bcc</td>
      <td>string</td>
      <td>Bcc recipient email address. Multiple addresses should be defined in multiple parameters.</td>
    </tr>
    <tr>
      <td>cc</td>
      <td>string</td>
      <td>Cc recipient email address. Multiple addresses should be defined in multiple parameters.</td>
    </tr>
    <tr>
      <td>from</td>
      <td>string</td>
      <td>Sender email address.</td>
    </tr>
    <tr>
      <td>message</td>
      <td>string</td>
      <td>HTML content of your email message. Up to 5MB.</td>
    </tr>
    <tr>
      <td>priority</td>
      <td>number</td>
      <td>Used by email clients to define a message's importance. From 1 to 5 where '1' is highest and '5' is the lowest priority.</td>
    </tr>
    <tr>
      <td>replyTo</td>
      <td>string</td>
      <td>Append a reply-to address to your email message.</td>
    </tr>
    <tr>
      <td>subject</td>
      <td>string</td>
      <td>Subject of your email. Up to 1MB.</td>
    </tr>
    <tr>
      <td>to</td>
      <td>string</td>
      <td>Recipient email address. Multiple addresses should be defined in multiple parameters.</td>
    </tr>
  </tbody>
</table>

### `GET /emails/:id/status`


<!-- </article> -->

## What's Next?

* That's it! Now we're ready to start sending emails to our users.
