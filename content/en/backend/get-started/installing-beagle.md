---
title: Installing Beagle
weight: 13
description: "You will find here how to configure a backend with Beagle."
---

---

{{% alert color="danger" %}}
Before you get started, the steps below are for JVM languages.

For other languages, your server needs to serve JSON following Beagle's API. Also, check out the **cache** and mechanisms, you may want to implement because the clients already support them.
{{% /alert %}}

## Requirements

Before you integrate Beagle into your application to run it on the backend, check if you have already installed all the current versions of the following programs:

- **JDK 8+ language \(Kotlin 1.3+ is recommended\)**
- **Maven 3+**

If you already have updated all the programs above, then just go to the following instructions.

## Installation

### Step 1: Create a micro-service

When you create a microservice, it's recommended to use your team's established mechanisms. If that's not your case, just follow the configuration steps below.

{{% alert color="warning" %}}
If your team works with microservices using other frameworks like Spring or Micronaut, check out **Beagle Framework page** instead.
{{% /alert %}}

For a simple setup, you can choose between 2 frameworks to create your [**BFF**]({{< ref path="/key-concepts#backend-for-frontend" lang="en" >}}):

#### [Micronaut](https://micronaut.io/)

> A modern, JVM-based, full-stack framework for building modular, easily testable micro-service and serverless applications.

#### [Spring](https://spring.io/)

> Spring makes programming Java quicker, easier, and safer for everybody. Spring’s focus on speed, simplicity, and productivity has made it the world's most popular Java framework.

After choosing the framework you'll work with, proceed with the configuration below:

{{< tabs id="T0" >}}
{{% tab name="Micronaut" %}}

### Creating a micro-service

#### Micronaut &lt;= 1.3

Screenshot-spring-boot-grpc-example
As described on [**Micronaut's quick start**](https://docs.micronaut.io/1.3.3/guide/index.html#quickStart), create your application through a CLI tool with this command:

```kotlin
$ mn create app bff --build maven --lang kotlin
```

This will create an executable Micronaut project using Kotlin and Maven in a directory called `BFF`. Open this project on the chosen IDE and follow the steps to set the dependencies:

#### Micronaut &gt;= 2.0

If you want to use Micronaut 2.0, you can use the new website, very similar to Spring.

- Click on the link below to download a zip file of the project with the image's option below: [**Micronaut Launch para Beagle Micronaut Starter**](https://launch.micronaut.io/create/DEFAULT/com.example.bff?lang=kotlin&build=maven&test=junit&javaVersion=JDK_8).

![Micronaut Launch with recommendation to start a Beagle project with Micronaut](/shared/image%20%28108%29.png)

- This configuration uses:
  - Kotlin with Maven for`Java 8` \(compatible with this version\);
  - `Junit` like the unit tests library.
- Unzip the file and open the extracted folder in your IDE.
  {{% /tab %}}

{{% tab name="Spring" %}}

### Create a micro-service

Use Spring's Initializr to create a project for your micro-service. Click the following link, [**Spring Initializr for Beagle Spring Starter**](https://start.spring.io/#!type=maven-project&language=kotlin&packaging=jar&jvmVersion=1.8&groupId=com.example&artifactId=bff&name=bff&description=Demo%20project%20for%20Beagle%20BFF%20using%20Spring%20Boot&packageName=com.example.bff&dependencies=actuator), to get recommended settings.

![Spring Initializr with recommended settings for a BFF with Spring, using Beagle Spring Starter](/shared/image%20%288%29.png)

- The settings are:
1. Maven dependency manager;
2. Kotlin with JAR packaging and Java 8+ compatibility;
3. Spring Boot Actuator dependency;
4. Click `GENERATE` to download a zip file containing your project;
5. Unzip the file and open the extracted folder in your IDE.
  {{% /tab %}}
  {{< /tabs >}}

### Step 2: Include starter dependency

Add the dependency for the Beagle starter to your backend. In that case, the framework you chose will define the dependency's name \(`artifactId`\) should be done.

Click on the tab of the framework you're using and follow the steps to continue the configuration:

{{< tabs id="T1" >}}
{{% tab name="Micronaut Starter" %}}

### Additional Requirements:

{{% alert color="info" %}}
This starter also configures version **1.3.3** of **`micronaut-runtime`** module in your BFF
{{% /alert %}}

- Beagle's current release version is: [![back](https://camo.githubusercontent.com/27998a386042ecb2cae7b9f09ae159bd07c935bd/68747470733a2f2f696d672e736869656c64732e696f2f6d6176656e2d63656e7472616c2f762f62722e636f6d2e7a75702e626561676c652f6672616d65776f726b)](https://mvnrepository.com/artifact/br.com.zup.beagle/framework)

### Maven configuration

To follow this requirement, you just have to add the dependency below to your `pom.xml`.

```markup
<dependency>
	<groupId>br.com.zup.beagle</groupId>
	<artifactId>beagle-micronaut-starter</artifactId>
	<version>${beagle.version}</version>
</dependency>
```

### Gradle configuration

For projects configured with Gradle, just add the starter dependency in your `build.gradle` or `build.gradle.kts` file.

```kotlin
dependencies {
  implementation("br.com.zup.beagle:beagle-micronaut-starter:${beagle.version}")
}
```

{{% /tab %}}

{{% tab name="Spring Starter" %}}

### Additional Requirements:

{{% alert color="info" %}}
This starter also configures version **2.2.5** of **`spring-boot-starter-web`** module in your BFF
{{% /alert %}}

- Beagle's current release version is: [![back](https://camo.githubusercontent.com/27998a386042ecb2cae7b9f09ae159bd07c935bd/68747470733a2f2f696d672e736869656c64732e696f2f6d6176656e2d63656e7472616c2f762f62722e636f6d2e7a75702e626561676c652f6672616d65776f726b)](https://mvnrepository.com/artifact/br.com.zup.beagle/framework)

### Maven configuration

To follow this requirement, add the dependency below to your `pom.xml`.

```markup
<dependency>
	<groupId>br.com.zup.beagle</groupId>
	<artifactId>beagle-spring-starter</artifactId>
	<version>${beagle.version}</version>
</dependency>
```

### Gradle configuration

For projects configured with Gradle, just add the starter dependency in your `build.gradle` or `build.gradle.kts` file.

```kotlin
dependencies {
  implementation("br.com.zup.beagle:beagle-spring-starter:${beagle.version}")
}
```

Insert the Beagle's release version on the place of`${beagle.version}`, in other words, put the Beagle's version highlighted in blue badge above without the **`v character`**.

For example:

![](https://img.shields.io/badge/beagle-v1.5.1-green)-`ext.beagle.version = "1.5.1"`

{{% alert color="warning" %}}
Remember to always check if you're using the latest version of Beagle. To see this information, you just have to pass your mouse above the version number. After that, sync your machine.
{{% /alert %}}

Well done, your initial configuration is ready to be used!

You can check a screen or server-driven component [**to test the BFF**]({{< ref path="/backend/get-started/using-beagle" lang="en" >}}).

{{% alert color="danger" %}}
Spring Boot has a known problem involving `WebMvcConfigurationSupport`. It may replace other configurations, including the ones in Beagle's Spring Starter.
If you face this problem, you should replace it for`WebMvcConfigurer.`

To see more about it, access [**this issue on Github.**](https://github.com/spring-projects/spring-boot/issues/12751)

The annotation`@EnableWebMvc` can have the same problem, which means you should also replace it.
{{% /alert %}}
{{% /tab %}}
{{< /tabs >}}

{{% alert color="success" %}}
Well done, your initial configuration is ready to be used!
{{% /alert %}}

You can see more of [**how to use Beagle on the backend**]({{< ref path="/backend/get-started/using-beagle" lang="en" >}}) or how to test a BFF with server-driven components.

## **Next Steps**

In this section, you have just done Beagle's** initial installation** on your application!  
Now, to keep configuring Beagle:

👉Go to [**initial configurations**]({{< ref path="/backend/get-started/using-beagle" lang="en" >}}) to enable the use of Beagle on your Web project.

👉 If you want to go straight to practice, access our [**tutorial to create a project from scratch**.]({{< ref path="/backend/get-started/creating-a-project-from-scratch" lang="en" >}})
