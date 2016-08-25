# Using the CLI

###### The WeDeploy Command-Line Interface is a tool for helping you to use the WeDeploy platform by providing support to things like creating, managing, and scaling applications.

<!-- <article id="1-dependencies"> -->

## Dependencies

The following external software dependencies are necessary to correctly run some commands:

a) [Git](https://git-scm.com/) (download for [Linux](https://git-scm.com/download/linux), [Mac OS X](https://git-scm.com/download/mac), [Windows](https://git-scm.com/download/win))

b) [Docker](https://www.docker.com/) (download for [Mac OS X](https://download.docker.com/mac/stable/Docker.dmg), [Linux](https://docs.docker.com/engine/installation/linux/), [Windows](https://download.docker.com/win/stable/InstallDocker.msi))

An useful error message feedback is given and the process is terminated, if a required dependency is not available when it is necessary.

<!-- </article> -->


<!-- <article id="2-installing"> -->

## Installing

Install this tool with:

```text
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -s | bash
```

The tool verifies daily if new updates are available and let the user know when it is. To update, just run `we update`.

<!-- </article> -->


<!-- <article id="3-creating-projects"> -->

## Creating projects locally

On the WeDeploy platform you create projects. Each project might have many containers, for handling static hosting, data API, email sending, etc.

Use `we create` to create projects and containers. You can create a project anywhere on your machine. Containers are usually created from inside projects and are stored on the first subdirectory of its project.

```text
Usage:
  we create <project/container id>
```

<!-- </article> -->

<!-- <article id="4-running-projects-locally"> -->

## Running projects locally

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone https://github.com/wedeploy/boilerplate-hosting.git
cd boilerplate-hosting
  ```

3. Link this container with the local infrastructure:

  ```text
we link
  ```

4. Now your container is ready at:

  ```text
http://hosting.<projectID>.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="5-using-remotes"> -->

## Using remotes
To use the CLI tool with the WeDeploy cloud you need to add remotes first.

The commands here are pretty similar to git's remote commands.

Watch for logs on the wechat project:
```text
we remote add staging office-cloud.internal
```

<!-- </article> -->


<!-- <article id="6-fetching-logs"> -->

## Fetching project and container logs

You can fetch projects and container logs with

```text
we log <project id> <container id>
```

### Examples:

See the logs for the last 20min for the data container on the wechat project:

```text
we log wechat data --since 20min
```

Watch for logs on the wechat project:
```text
we log wechat --watch
```

Watch for logs on the wechat project on the production (remote) cloud:

```text
we log wechat --remote production
```

<!-- </article> -->

<!-- <article id="7-list"> -->

## Listing projects and containers

Watch the listing of all projects running locally:
```text
we list --watch
```

List all projects on a given cloud:
```text
we list --remote <remote>
```

List the containers of the project "ci" on the cloud "staging":
```text
we list ci --remote staging
```

<!-- </article> -->

