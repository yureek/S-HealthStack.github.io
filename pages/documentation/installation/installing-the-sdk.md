---
title: Installing the App SDK
sidebar: doc_sidebar
permalink: installing-the-sdk.html
toc: false
---

# Prerequisite

## OpenJDK

Setup and install OpenJDK 11.

[https://openjdk.org/install/](https://openjdk.org/install/)

## Android Studio 

Setup and install Android Studio on Windows, macOS, or Linux.

[https://developer.android.com/studio](https://developer.android.com/studio)

# Clone the repository

Clone the Research-SDK using the following command 

```git
git clone https://github.com/S-HealthStack/app-sdk
```

# Build

Currently, detekt is not supported because of some issues.

```bash
# clean all modules
./gradlew clean 

# build all modules including sample modules
./gradlew build -x detekt

# build only kit module
# this action generates aar(android archive package)
./gradlew :kit:build -x detekt
```

## Unit Test

```bash
# test all modules including samples
./gradlew test

# test only kit
./gradlew :kit:test
```

## Check Coding Style

The [Compose API guidelines](https://github.com/androidx/androidx/blob/androidx-main/compose/docs/compose-api-guidelines.md) outline the patterns, best practices, and prescriptive style guidelines for writing idiomatic Jetpack Compose APIs. 

# API Documentation

To view the API Reference please visit the [API Reference](/backend-api-endpoints.html) Page.

# Configurations

## Kit and External

This sample application depends on SDK modules so it must have kit and external.

Dependencies can be declared as below.


*samples>researchsample>build.gradle.kts*

**build.gradle.kts**

```
dependencies {
    implementation(project(":kit"))
    implementation(project(":external"))
}
```

**build.gradle**

```
dependencies {
    implementation project(':kit')
    implementation project(':external')
}
```

## Firebase project setup

The starter application uses Firebase, so you need to create a Firebase project. Refer to [https://firebase.google.com/docs/android/setup](https://firebase.google.com/docs/android/setup) for details.

## Per app configuration

After app creation, for each app you need to:

- Register your app with your Firebase project by updating the ***\<repository\>*/app/google-service.json** configuration file.
- Associate your app with the backend system and portal study.

Refer to  during [Configuring the App Environment](../app creation/configuring-the-app.md) for details.