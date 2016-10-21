# Custom Domains

###### This is an overview of how WeDeploy manage custom domains for your projects.

<!-- <article id="introduction"> -->

## Introduction

In order to make your app accessible right away, WeDeploy makes any project accessible via its project domain, wich looks like `<serviceID>.<projectID>.wedeploy.io`. Let's say you have a project named `project` with a service named `web` the WeDeploy project domain would be `web.project.wedeploy.io`. Every project in WeDeploy supports one or many custom domains.

<!-- </article> -->

<!-- <article id="configuring-custom-domains"> -->

## Configuring custom domains

To make a project accessible via one or more non-WeDeploy domain names, you must add custom domain(s) to your project configuration as described below.

<ol class="list list--numeric">
  <li>After create a project on the <a href="http://dashboard.wedeploy.com">dashboard</a>. Go to the project settings page.</li>
  <li>On custom domain session, add the custom domains related to the project.</li>
  <li>Click in Update Project.</li>
  <li>Update the domain DNS to point to the project WeDeploy domain (`<projectID>.wedeploy.io`).</li>
</ol>

![settings](https://cloud.githubusercontent.com/assets/301291/19607402/73aca3b6-977e-11e6-82d6-e3374d3aa6ed.png)



<!-- </article> -->

<!-- <article id="configuring-dns-for-root-domains"> -->

## Configuring DNS for root domains

Root domains doesn't have subdomain on its structure. You can add root domains on the same Project Settings Page used for domains with subdomains.
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

```text
<projectID>.wedeploy.io is an alias for wedeploy.com.
wedeploy.com has address 111.111.111.111
```

<br>

2) Use the API provided from `wedeploy.com` (111.111.111.111).

<!-- </article> -->


<!-- <article id="configuring-dns-for-custom-domains"> -->

## Configuring DNS for custom domains

After configuring the custom domains on the Project Settings, you must point your DNS to the project WeDeploy domain. You can configure your subdomain as a new CNAME record with your DNS provider. If you're not sure about how to configure your subdomain as a CNAME record, visit your DNS provider documentation page.

<table class="table">
  <tr>
    <th>Record</th> <th>Subdomain</th> <th>Project Target Domain</th>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>**www**.mydomain.com</td> <td>project1.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>**subdomain1**.mydomain.com</td> <td>project1.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>**subdomain2**.mydomain.com</td> <td>project2.wedeploy.io.</td>
  </tr>
  <tr>
    <td>`CNAME`</td> <td>**subdomain3**.mydomain.com</td> <td>project3.wedeploy.io.</td>
  </tr>
</table>

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
