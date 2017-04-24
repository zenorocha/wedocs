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

## Install dependencies

This section assumes that you already have the **WeDeploy CLI** installed and **Docker** running. Make sure to [visit the installation guide](/docs/intro/using-the-command-line.html) if you need help setting that up.

<!-- </article> -->

<!-- <article id="running-locally"> -->

## Running locally

1. Start local infrastructure:

  ```text
we run
  ```

2. Clone this repository:

  ```text
git clone https://github.com/wedeploy/boilerplate-java.git
cd boilerplate-java
  ```

3. Build the container:

  ```text
we build
  ```

4. Link this container with the local infrastructure:

  ```text
we link --project <projectID>
  ```

5. Now your container is ready to be used:

  ```text
http://java.<projectID>.wedeploy.me
  ```

<!-- </article> -->

<!-- <article id="deploying-to-the-cloud"> -->

## Deploying to the cloud

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

<!-- <article id="notes-about-java-development"> -->

## Notes about Java development

WeDeploy runs your Java application on [OpenJDK 8](http://openjdk.java.net/).

Our boilerplate Java image contains an example built with [Spring Boot](https://projects.spring.io/spring-boot/). Of course, you are allowed to use any Java web application framework or server. Just build the project however you usually do, and that's it.

WeDeploy Java image comes with the following build tools installed:

+ [Gradle](https://gradle.org/)
+ [Maven](https://maven.apache.org/)
+ [Ant](http://ant.apache.org/)
+ [Ivy](http://ant.apache.org/ivy/)

You can use any of those to build your web application. There is just one thing your build definition _must_ have: a task named `run` that _start_ the whole application. WeDeploy will execute this task when container starts. Sometimes, this task is already availiable by default or within some plugin that your build is using. When the task is not availiable, you have to define it manually; for example, in Gradle, you can do something like this for the Spring Boot application:

  ```groovy
task run(dependsOn: ':bootRun')
  ```

Until now we assumed that `run` task also triggers the build of the application (e.g. by having task dependency). If this is not a case, you have to specify the build command in `container.json`:

  ```json
  "hooks": {
    "build": "./gradlew clean build installDist -x test"
  },
  ```

This hook tells WeDeploy how to build and pack the application, so it can be run by executing the `run` task. Again, you have to do this only if the `run` task does not do it already.

<!-- </article> -->

<!-- <article id="notes-about-java-development"> -->

## Working locally with Java-based containers

You can work with your Java application in different ways. When your Java app does not require other parts of your projects, you can simply run it locally, without the WeDeploy infrastructure. In this case you just need to provide the build script with `run` task, as described above.

In most cases, your Java application will be important part of the project. Hence you will run the project using `we run` and `we link` commands. This will run WeDeploy infrastructure and run your project (all of its containers) in it. Your Java app wlil be one of the containers that will run. During develoment, it is common to update Java project as you add new features. When running inside the WeDeploy infrastructure, you just have to restart it with: `we restart`. When invoked in your Java projects folder, the WeDeploy container will be restarted, and soon you will have the updated server up. If you need to restart the whole application, then invoke `we restart` in the projects root.

### Startup errors

Sometimes, your Java application would not start because of some software error (yeah, we all make mistakes). In this case, Java container will never get up, after the `we restart` command. Project status would remain `unknown`. If this happens, it is a chance that there is some issue with the application on start.

### Logging

WeDeploy collects all the console output as logs. To see the logs, just invoke: `we log -w <container-name>`. This will print the container logs and keep watching it (`-w`), so you can use it for debugging.

### Application port

If your Java application does not run on port `8080` you need to specify it using the field `port` in the [`container.json` definition](/docs/intro/configuration-files.html#service-configuration).

<!-- </article> -->

## What's next?

* Now you can start building your Java based application.
