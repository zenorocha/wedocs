# Quick Start

###### In this section, you'll learn how to deploy an application using WeDeploy Dashboard.

<!-- <article id="1-create-an-account"> -->

## 1. Create an account

In order to have access to WeDeploy functionalities you're going to receive an invite though email with the link to create a new account.

![SignUp](https://cloud.githubusercontent.com/assets/301291/17795864/bfc70c4a-6570-11e6-94f8-2b9cf3c45998.jpg)

<!-- </article> -->

<!-- <article id="2-access-your-dashboard"> -->

## 2. Access your dashboard

As the main page, the dashboard will list all your projects and status of availability in the server. In the Dashboard, click in New Project .

![Dashboard](https://cloud.githubusercontent.com/assets/301291/17795897/1d122f60-6571-11e6-8137-c1fe6fdfcbdb.jpg)

<!-- </article> -->

<!-- <article id="3-create-a-new-project"> -->

## 3. Create a new project

You are able to organize your services by project. Select a project name and ID and click in Create Project.

![New Project](https://cloud.githubusercontent.com/assets/301291/17795929/529dcc02-6571-11e6-8e5f-3514ea67688d.jpg)

<!-- </article> -->

<!-- <article id="4-open-your-project"> -->

## 4. Open your project

![Project Container List](https://cloud.githubusercontent.com/assets/301291/17795964/ba9a34d0-6571-11e6-9d49-c30e4862d2c2.jpg)

<!-- </article> -->

<!-- <article id="5-click-in-install-container"> -->

## 5. Click in Install Container

Projects can have more than one container. In this example we're going to deploy a static website.

![Install Container](https://cloud.githubusercontent.com/assets/301291/17794534/1f2f7aca-6565-11e6-961c-652fcb1cb53b.png)

<!-- </article> -->

<!-- <article id="6-select-a-container-type"> -->

## 6. Select a Container type
In this tutorial we're going to use the WeDeploy Hosting in order to host a static project.

![Select a Container Type](https://cloud.githubusercontent.com/assets/301291/17796007/14480e94-6572-11e6-9d33-fbaed635de0b.jpg)

<!-- </article> -->

<!-- <article id="7-fill-in-the-name-and-id-and-click-in-install-container"> -->

## 7. Fill in the name and ID and click in install container

![Install Container Form](https://cloud.githubusercontent.com/assets/301291/17796043/739dcaf0-6572-11e6-87aa-1394f9b54e17.jpg)

<!-- </article> -->

<!-- <article id="8-hosting-template-and-github-repository"> -->

## 8. The container is going to be up and running

![Container Up and Running](https://cloud.githubusercontent.com/assets/301291/17796194/c6589d1e-6573-11e6-8a83-d372d71ed137.jpg)

<!-- </article> -->

<!-- <article id="8-hosting-template-and-github-repository"> -->

## 8. Download the hosting boilerplate and create a Github Repository

In order to facilitate your work, WeDeploy provide many boilerplates to help you to deploy many types of applications. In this example download the [Static Host Boilerplate](https://github.com/wedeploy/boilerplate-hosting).

<!-- </article> -->

<!-- <article id="9-github-project"> -->

## 9. Configure the github for the project

In this current version, WeDeploy only supports public Github repositories. This repository is going to be used to trigger deployments every time you send a new commit.
![Configure Github Host](https://cloud.githubusercontent.com/assets/301291/17795272/c3fbf5dc-656b-11e6-8e81-79a97c97f9cb.png)

<!-- </article> -->

<!-- <article id="10-github-project"> -->

## 10. Push your boilerplate to the github repository

After download the boilerplate, you should add your remote repository in the git config of your folder. Every time you send a new commit to its github repository, WeDeploy will build and deploy your project automatically.
<!-- </article> -->


<!-- <article id="11-generated-url"> -->

## 11. Access the url generated for your container
Now that you installed the boilerplate, in the container screen is possible to see the status of the container and its URL. Click in the url to copy to your clipboard and open that in a new tab in your browser.
![URL Generated](https://cloud.githubusercontent.com/assets/301291/17795316/424b3a2e-656c-11e6-8023-904b83b091f5.png)

<!-- </article> -->

<!-- <article id="12-it-works"> -->

## 12. It works!
That's it! Using a sofisticated Loadbalancer system and service discovering, WeDeploy automatically creates a URL and points that to your container.
![URL Generated](https://cloud.githubusercontent.com/assets/301291/17796616/b2ca3fd4-6576-11e6-8e18-85423f206b94.jpg)

<!-- </article> -->
