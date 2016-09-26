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

Open your Terminal and run:

```text
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -sL | bash
```

<!-- </article> -->


<!-- <article id="3-creating-projects"> -->

## Creating projects locally

You are able to organize your services by projects. Inside it, you can create services (called containers here), like static hosting, data API, Auth service, etc.

Use `we create` to create projects and containers. You can create a project anywhere on your machine. Containers might be created one directory above a project for your convenience.

```text
Usage:
  we create --project <project> --container <container>
```

<!-- </article> -->

<!-- <article id="4-running-projects-locally"> -->

## Running projects locally

For this demo we are going to use the hosting boilerplate.

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone https://github.com/wedeploy/boilerplate-hosting.git
cd boilerplate-hosting
  ```

3. Link this container to a new project named demo:

  ```text
we link --project demo
  ```

4. Now your container should be accessible from [http://hosting.demo.wedeploy.me](http://hosting.demo.wedeploy.me)

*On the first first time it might take a few minutes while downloading the hosting image on the background.*

<!-- </article> -->


<!-- <article id=“5-login-and-remotes”> -->

## Remotes and friendly host style
Many commands need --project, --container, or --remote attributes. To make things easier for you, you can use the following patterns:

```text
we <command> --project <project> --container <container>
```

and

```text
we <command> <container>.<project>.<remote address>
```

Remote address is optional and you can use the host style with project and container and still use the --remote directly, if you don't know the remote address for a given remote.

Remotes can be managed in a similar fashion as git's remote command:

```text
$ we remote -v
wedeploy       	wedeploy.io
```

For your convenience we include the wedeploy cloud remote by default once you log in on the CLI app with `we login` (requested when necessary).

All commands that support --project, --container, and / or --remote support this host style.

<!-- </article> -->


<!-- <article id=“6-fetching-logs"> -->

## Fetching project and container logs

You can fetch projects and container logs with

```text
we log --project <project> --container <container>
```

or with a friendly host style like

```text
we log <container>.<project>.wedeploy.me
```

### Examples:

See the logs for the last 20min for the data container on the wechat project:

```text
we log --project wechat --container data --since 20min
```

Watch for logs on the hosting container on the demo project:
```text
we log hosting.demo.wedeploy.me --watch
```

<!-- </article> -->

<!-- <article id=“7-list"> -->

## Listing projects and containers

Watch the listing of all projects running locally:
```text
we list --watch
```

List all your projects running on the WeDeploy cloud:
```text
we list wedeploy.io
```

or
```text
we list --remote wedeploy
```

<!-- </article> -->

