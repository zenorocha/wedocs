# Custom Domains

###### This is an overview of how WeDeploy manage custom domains for your projects.

<!-- <article id="introduction"> -->

## Introduction

In order to make your app accessible right away, WeDeploy makes any project accessible via its WeDeploy Domain, which has the form `<serviceID>.<projectID>.wedeploy.io`. For example, you're able to access a project named `project1` with a service named `web` with `web.project1.wedeploy.io`.

<!-- </article> -->

<!-- <article id="configuring-custom-domains"> -->

## Configuring custom domains

To make a project accessible via one or more non-WeDeploy domain names, you must add custom domain(s) to your project configuration as described below.

* 1) After create a project on the dashboard. Go to the Project Settings Page.

* 2) On custom domain session, add the custom domains related to the project.

* 3) Click in Update Project.

* 4) Update the domain DNS to point to the `Project WeDeploy Domain` (`<projectID>.wedeploy.io`).

<!-- </article> -->

<!-- <article id="configuring-dns-for-custom-domains"> -->

## Configuring DNS for custom Domains

After configuring the custom domains on the Project Settings, you must point your DNS provider to the `Project WeDeploy Domain`. You may configure the DNS as a new CNAME record with your DNS provider. Consult with your DNS provider for specific instructions to create CNAME records.


<table class="table no-header">
  <tr>
    <td>`CNAME`</td> <td>www</td> <td>project1.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>subdomain1</td> <td>project1.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>subdomain2</td> <td>project2.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>subdomain3</td> <td>project3.wedeploy.io.</td>
  </tr>
</table>

<!-- </article> -->

<!-- <article id="wildcard-domain"> -->

## Wildcard domain

Since you can have multiple services inside a project and WeDeploy automatically creates a subdomain for each service. Wildcard domains allow you to map any of all generated subdomains from the services with a single record.

<table class="table no-header">
  <tr>
    <td>`CNAME`</td> <td>*</td> <td>project.wedeploy.io.</td>
  </tr>
</table>

Result:

<table class="table no-header">
  <tr>
    <td>service1.project.wedeploy.io</td> <td>service1.mydomain.com</td>
  </tr>
  <tr>
    <td>service2.project.wedeploy.io</td> <td>service2.mydomain.com</td>
  </tr>
  <tr>
    <td>service3.project.wedeploy.io</td> <td>service3.mydomain.com</td>
  </tr>
  <tr>
    <td>service4.project.wedeploy.io</td> <td>service4.mydomain.com</td>
  </tr>
</table>

<!-- </article> -->

<!-- <article id="configuring-dns-for-custom-domains"> -->

## Custom domains for services

If you need to use a custom domain with the same services name, you just need to create a custom domain with the same name of the service, after configuring a custom domain for your project.

ex: `service1.project1.wedeploy.io => service1.mydomain.com`

<!-- </article> -->

<!-- <article id="rules-on-adding-custom-domains"> -->

## Rules on adding custom domains

* A domain should be used just in one project.
* A single project can have any number of domains.

<!-- </article> -->
