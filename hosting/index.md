# Hosting

###### Serve static files easily using *WeDeploy™ Hosting*.

<!-- <article id="1-install-dependencies"> -->

## 1. Install Dependencies

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

```sh
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -s | bash
```

<!-- </article> -->

<!-- <article id="2-running-locally"> -->

## 2. Running locally

1. Start local infrastructure:

  ```sh
we run
  ```

2. Clone this repository:

  ```sh
git clone https://github.com/wedeploy/boilerplate-hosting.git
cd boilerplate-hosting
  ```

3. Link this container with the local infrastructure:

  ```sh
we link
  ```

4. Now your container is ready to be used:

  ```
http://hosting.<projectID>.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="#-running-locally"> -->

## 3. Deploying to the cloud

1. [Fork this repository](https://github.com/wedeploy/boilerplate-hosting/fork).
2. Go to the [Dashboard](http://dashboard.wedeploy.io).
3. Create a project.
4. In the sidebar, click on *GitHub Integration*.
5. Type your repository URL and `master` branch.
6. Click on *Update Project* and wait a few seconds.
7. Once you see them in the Dashboard, your container will be ready to be used.

  ```
http://hosting.<projectID>.wedeploy.io
  ```

<!-- </article> -->