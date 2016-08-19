# Data

###### Leverage a NoSQL database with search and realtime capabilities using *WeDeploy™ Data*.

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
git clone -b js https://github.com/wedeploy/boilerplate-data.git boilerplate-data-js
cd boilerplate-data-js
  ```

3. Link this container with the local infrastructure:

  ```text
we link
  ```

4. Now your container is ready to be used:

  ```text
http://datademo.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-data/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. Create a project.
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `js` branch.
6. Click on *Update Project* and wait a few seconds.
7. Once you see it in the Dashboard, your container will be ready to be used.

  ```text
http://datademo.wedeploy.io
  ```

<!-- </article> -->

<!-- <article id="saving-data"> -->

## Saving Data

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium perferendis quas hic veritatis numquam aut recusandae aperiam nesciunt exercitationem, minima, cum asperiores repellendus at debitis accusamus quaerat quae soluta obcaecati similique.

<!-- </article> -->

<!-- <article id="retrieving-data"> -->

## Retrieving Data

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium perferendis quas hic veritatis numquam aut recusandae aperiam nesciunt exercitationem, minima, cum asperiores repellendus at debitis accusamus quaerat quae soluta obcaecati similique.

<!-- </article> -->

<!-- <article id="searching-data"> -->

## Searching Data

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium perferendis quas hic veritatis numquam aut recusandae aperiam nesciunt exercitationem, minima, cum asperiores repellendus at debitis accusamus quaerat quae soluta obcaecati similique.

<!-- </article> -->

<!-- <article id="watching-data-changes"> -->

## Watching Data Changes

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium perferendis quas hic veritatis numquam aut recusandae aperiam nesciunt exercitationem, minima, cum asperiores repellendus at debitis accusamus quaerat quae soluta obcaecati similique.

<!-- </article> -->

## What's Next?

* Now we're ready to save and retrive data in real-time.
