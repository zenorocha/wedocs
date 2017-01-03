# Data

###### Leverage a NoSQL database with search and real-time capabilities using *WeDeploy™ Data*.

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-sm" href="http://boilerplate-data.wedeploy.io" target="_blank">
    <span class="icon-16-external"></span>See Live Demo
  </a>
</div>

<div class="guide-aux-cta">
  or read the <a href="https://github.com/wedeploy/boilerplate-data/tree/js" target="_blank">source code</a>.
</div>

<!-- <article id="install-dependencies"> -->

## Install dependencies

This section assumes you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running locally

1. Clone this repository:

  ```text
git clone -b js https://github.com/wedeploy/boilerplate-data.git boilerplate-data-js
cd boilerplate-data-js
  ```

2. Run this container locally:

  ```text
we dev
  ```

3. Now your container is ready to be used:

  ```text
http://boilerplate-data.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-data/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com).
3. [Create a project](http://dashboard.wedeploy.com/new).
4. In the sidebar, click on *Deployment*.
5. Using your local machine, clone your Github fork:
  ```text
git clone -b js https://github.com/<username>/boilerplate-data
  ```
6. Get into the folder: `cd boilerplate-data`.
7. Using the content on *Deployment* page. Add the WeDeploy remote url:
  ```text
git remote add wedeploy http://git.wedeploy.com/<projectID>.git
  ```
8. Push your data to wedeploy git server: `git push wedeploy js:master`.
9. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://boilerplate-data.wedeploy.io
  ```

<!-- </article> -->


## What's next?

Now that you have *WeDeploy™ Data* API settled up, you can interact [configuring the data service](/docs/data/js/configuring-data.html).
