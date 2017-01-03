# Data

###### Leverage a NoSQL database with search and real-time capabilities using *WeDeploy™ Data*.

<!-- <article id="install-dependencies"> -->

## Install Dependencies

This section assumes you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

We also feature code snippets using the API Client, [visit this guide](/docs/intro/using-the-api-client.html) in order to start using it.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running Locally

1. Clone this repository:

  ```text
git clone -b js https://github.com/wedeploy/boilerplate-data.git boilerplate-data-js
cd boilerplate-data-js
  ```

3. Run this container locally:

  ```text
we dev
  ```

3. Now your container is ready to be used:

  ```text
http://datademo.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the Cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-data/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.com).
3. [Create a project](http://dashboard.wedeploy.com/projects/create).
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
http://datademo.wedeploy.io
  ```


<!-- </article> -->


## Next Steps

Now that you have *WeDeploy™ Data* API settled up, you can interact [saving data](/docs/data/rest/saving-data.html).
