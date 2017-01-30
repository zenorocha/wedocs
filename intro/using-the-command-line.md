# Using the Command-line

###### The WeDeploy Command-Line Interface is a tool for helping you to use the WeDeploy platform by providing support to things like creating, managing, and scaling applications.

<!-- <article id="1-dependencies"> -->

## Dependencies

The following external software dependencies are necessary to correctly run some commands:

a) [Git](https://git-scm.com/) (download for [Linux](https://git-scm.com/download/linux), [macOS](https://git-scm.com/download/mac), [Windows](https://git-scm.com/download/win))

b) [Docker](https://www.docker.com/) (download for [Linux](https://docs.docker.com/engine/installation/linux/), [macOS](https://download.docker.com/mac/stable/Docker.dmg), [Windows](https://download.docker.com/win/stable/InstallDocker.msi))

Docker version 1.12.0 or later is required. If you use macOS, install the Docker for Mac. If you use Windows, please install Docker for Windows. Docker Toolbox, still available for earlier Mac and Windows systems is not supported.

<!-- </article> -->


<!-- <article id="2-installing"> -->

## Installing

If you use a Unix-like system such as macOS or Linux open your Terminal and run:

```text
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -sL | bash
```

Then try running `we`. You should be able to see the help.

In case of error, try to install it using `sudo`:

```text
curl http://cdn.wedeploy.com/cli/latest/wedeploy.sh -sL | sudo bash
```


If you use Windows, you probably want the [Windows amd64 installer](https://bin.equinox.io/c/8WGbGy94JXa/cli-stable-windows-amd64.msi). For other systems, check a list of [all builds available](https://bin.equinox.io/c/8WGbGy94JXa/cli-stable-windows-amd64.zip).

**Check your docker configuration:** docker comes with a 2.0GB maximum memory limit by default on macOS and Windows. You should increase this limit to at least 4.0GB. It is also recommended to increase the number of available CPUs.

<!-- </article> -->


<!-- <article id="3-creating-projects"> -->

## Creating projects locally

You are able to organize your services by project. Inside each project you can create services (called containers here), like static hosting, data API, Auth service, etc.

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
Many commands requires `--project`, `--container`, or `--remote` flags. You can use the following patterns for passing these values:

```text
we <command> --project <project> --container <container>
```

and the friendly host style:

```text
we <command> <container>.<project>.<remote address>
```

or even

```text
we <command> <container>.<project> --remote <remote>
```

For the local cloud, just don't add a `--remote` or `<remote address>` value like in:

```text
we log public.chat
```

or to list all logs by containers on the project "chat":

```text
we log chat
```

Remotes can be managed in a similar fashion as git's remote command:

```text
$ we remote -v
wedeploy       	wedeploy.io
```

If you know how to use `git remote` you already know how to use `we remote`.

For your convenience we include the wedeploy cloud remote by default once you log in on the CLI app with `we login` (requested when necessary).

All commands that support `--project`, `--container`, and / or `--remote` support this host style as well.

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

