# Java

###### Launch a Java 8 application in few steps.

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-sm" href="http://boilerplate-java.wedeploy.io" target="_blank">
    <span class="icon-16-external"></span>See Live Demo
  </a>
</div>

<div class="guide-aux-cta">
  or read the <a href="https://github.com/wedeploy/boilerplate-java/" target="_blank">source code</a>.
</div>

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running Locally

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone https://github.com/wedeploy/boilerplate-java.git
cd boilerplate-java
  ```

3. Link this container with the local infrastructure:

  ```text
we link --project <projectID>
  ```

4. Build the container:

  ```text
we build
  ```
5. Now your container is ready to be used:

  ```text
http://java.<projectID>.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-java/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com).
3. [Create a project](http://dashboard.wedeploy.com/projects/create).
4. In the sidebar, click on *Deployment*.
5. Using your local machine, clone your Github fork:
  ```text
git clone https://github.com/<username>/boilerplate-java
  ```
6. Get into the folder: `cd boilerplate-java`.
7. Using the content on *Deployment* page. Add the WeDeploy remote url:
  ```text
git remote add wedeploy http://git.wedeploy.com/<projectID>.git
  ```
8. Push your data to wedeploy git server: `git push wedeploy master`.
9. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://java.<projectID>.wedeploy.io
  ```

<!-- </article> -->

## What's Next?

* Now you can start building your Node.js based application.
