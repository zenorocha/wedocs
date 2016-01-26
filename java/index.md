# Quickstart with Java

Let's start from zero and build a RESTful API that stores and sync data.

## 1. Request invitation

The first thing you need to do to get started with Launchpad is to [request an invitation](http://liferay.io/#invitation).

At this moment, Launchpad is only available to a restricted group of developers, but don't worry we're sending invites on a daily basis.

## 2. Create an API

1. Once you have an account, go to [Dashboard](http://liferay.io/dashboard/apps) and click *Create App* and enter a name and URL for your app.

3. Select *Add Service*, and enter a name and URL to create your service. The service acts as a  container, which exposes your RESTful APIs.

4. Switch to the *API Builder*, and make sure the *Data* switcher is turned on.

5. Also check that *GET* and *POST* are selected in the *Method* section. These methods allow you to read and write on this URL.

5. In the *Endpoint* field, type `/items/*`. The `*` symbol indicates that any request starting with `items` will match this endpoint.

## 3. Connect to your API

In order to send and receive requests to and from Launchpad, you need to include the [API Client for Java](https://github.com/launchpad-project/api.java). This library provides a secure and reliable communication channel with Launchpad. It is possible to download the client jar file directly from our [Bintray's JCenter](https://bintray.com/liferay/launchpad/api-client/view) repository, or to add it as a dependency to your *gradle* project like this:

```
repositories {
	jcenter()
}
dependencies {
	compile 'com.liferay.launchpad:api-client:0.40.2'
}
```

Or using *maven*:

```xml
<repositories>
  <repository>
    <id>jcenter</id>
    <url>http://jcenter.bintray.com</url>
  </repository>
</repositories>

<dependencies>
  <dependency>
    <groupId>com.liferay.launchpad</groupId>
	<artifactId>api-client</artifactId>
	<version>0.40.2</version>
  </dependency>
</dependencies>
```

## 4. Read & Write Data

Now, you can send any valid JSON object to Launchpad using `post()`. The following example post some information for a popular Science Fiction film:

```java
Launchpad.url("http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items")
   .header("Content-Type", "application/json")
   .post("{\"title\":\"Star Wars IV\",\"year\":1977}");
```

Now that you have posted data to your database, you can read it using `get()` with no arguments:

```java
Launchpad.url("http://liferay.io/<YOUR-APP>/<YOUR-SERVICE>/items")
  .get();
```

You can also try this out on the *API explorer* tab of your service.

## 5. What's Next?

* Read the ["Building APIs"](http://liferay.io/docs/java/building-apis.html) guide
* Read the ["Understanding Data"](http://liferay.io/docs/java/understanding-data.html) guide