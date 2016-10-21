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


<table class="table">
  <tr>
    <th>Record</th> <th>Subdomain</th> <th>Project Target Domain</th>
  </tr>
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

<!-- <article id="configuring-dns-for-root-domains"> -->

## Configuring DNS for root domains

Root domains doesn't have subdomain on its structure. You can add root domains in the same Project Settings Page used for domains with subdomains.
Configuring your DNS provider for a root domain is similar to configuring a DNS provider for a CNAME. In this case, the type of record depends on the DNS provider.

Point the A/CNAME entry for your root domain to the DNS Target, just as you would with a CNAME record:

<table class="table">
  <tr>
    <th>Record</th> <th>Name</th> <th>Project Target Domain</th>
  </tr>
  <tr>
    <td>`ALIAS` or `CNAME`</td> <td>`<empty>` or `@`</td> <td>project1.wedeploy.io.</td>
  </tr>
</table>

In some DNS Providers such as Google domains, it just allow you to configure IPs for root domains. In this case you can:

1) Go to your terminal and type `host <projectID>.wedeploy.io`.

<br>

```text
<projectID>.wedeploy.io is an alias for wedeploy.com.
wedeploy.com has address 111.111.111.111
```

<br>

2) Use the API provided from `wedeploy.com` (111.111.111.111).

<!-- </article> -->


<!-- <article id="wildcard-domain"> -->

## Wildcard domain

Since you can have multiple services inside a project and WeDeploy automatically creates a subdomain for each service. Wildcard domains allow you to map any of all generated subdomains from the services with a single record.

<table class="table">
  <tr>
    <th>Record</th> <th>Subdomain</th> <th>Project Target Domain</th>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>*</td> <td>project.wedeploy.io.</td>
  </tr>
</table>

<br>

Result:

<br>

<table class="table">
  <tr>
    <th>WeDeploy Domain</th> <th>Custom Domain</th>
  </tr>
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

<!-- <article id="custom-domains-for-services"> -->

## Custom domains for services

If you need to use a custom domain with the same services name, you just need to create a custom domain with the same name of the service, after configuring a custom domain for your project.

ex: `service1.project1.wedeploy.io => service1.mydomain.com`

<!-- </article> -->

<!-- <article id="rules-on-adding-custom-domains"> -->

## Rules on adding custom domains

* A domain should be used just in one project.
* A single project can have any number of domains.

<!-- </article> -->
