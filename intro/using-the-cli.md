# Using the CLI

###### The *WeDeploy™ Command-line interface (CLI)* is a tool that wraps the WeDeploy Platform API, providing support for things like creating, managing and scaling applications. It's generally installed in your local development operating system.

<!-- <article id="1-dependencies"> -->

## 1. Dependencies

The following external software dependencies are necessary to correctly run some commands:

* [docker](https://www.docker.com/)
* [git](https://git-scm.com/)

The availability of dependencies are tested just before its immediate use. If a required dependency is not found, an useful error message is printed and the calling process is terminated with an error code.

<!-- </article> -->


<!-- <article id="2-installing"> -->

## 2. Installing

Install this tool with:

```
curl https://raw.githubusercontent.com/wedeploy/cli/master/install.sh -s | bash
```
or download from our [stable release channel](https://dl.equinox.io/wedeploy/cli/stable):

To update this tool, just run `we update`.

<!-- </article> -->


<!-- <article id="3-creating-projects"> -->

## 3. Creating Projects from the CLI

The project is the fundamental unit of organization on *WeDeploy™*. Each project can be associated with its own set of provisioned services.

Use `we create` to create projects and containers. You can create a project anywhere on your machine. Containers can only be created from inside projects and are stored on the first subdirectory of its project.

```
Usage:
  we create <project/container id> [flags]
```

Examples:

`we create relay`

```
Global Flags:
      --no-color        Disable color output
      --remote string   Remote to use
  -v, --verbose         Verbose output
```
<!-- </article> -->
