# Node.js

###### Launch a Node.js application in few steps.

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
git clone https://github.com/wedeploy/boilerplate-nodejs.git
cd boilerplate-nodejs
  ```

3. Link this container with the local infrastructure:

  ```text
we link
  ```

4. Build the container:

  ```text
we build
  ```
5. Now your container is ready to be used:

  ```text
http://nodejs.<projectID>.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-nodejs/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. [Create a project](http://dashboard.wedeploy.io/projects/create).
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `master` branch.
6. Click on *Update Project*.
7. Click on *Build All Repos* and wait a few seconds.
8. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://nodejs.<projectID>.wedeploy.io
  ```

<!-- </article> -->

## What's Next?

* Now you can start building your Node.js based application.
