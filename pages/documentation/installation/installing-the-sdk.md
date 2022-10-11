---
title: Installing the App SDK
sidebar: doc_sidebar
permalink: installing-the-sdk.html
toc: false
---

## Prerequisite

### OpenJDK:

Setup and install OpenJDK

[https://openjdk.org/install/](https://openjdk.org/install/)

### Android Studio 

Setup and install android studio on windows macOS or Linux

[https://developer.android.com/studio](https://developer.android.com/studio)

## Clone

Clone the Research-SDK using the following command 

`git clone https://github.com/S-HealthStack/app-sdk`

## Build

Currently, detekt is not supported because of some issues.

```
# clean all modules
$ ./gradlew clean 

# build all modules including sample modules
$ ./gradlew build -x detekt

# build only kit module
# this action generates aar(android archive package)
$ ./gradlew :kit:build -x detekt
```

## Unit Test

```
# test all modules including samples
$ ./gradlew test

# test only kit
$ ./gradlew :kit:test
```

## Check coding Style

The Compose API guidelines outline the patterns, best practices, and prescriptive style guidelines for writing idiomatic Jetpack Compose APIs. To access the guide click: [Compose-API-Guideline](https://github.com/androidx/androidx/blob/androidx-main/compose/docs/compose-api-guidelines.md)

## API Documentation


To view the API Reference please visit the [API Reference](backend-api-endpoints.html) Page.


## Configurations

### Kit and External

This sample application depends on SDK modules so it must have kit and external

Information can be found through the top Navigation bar by going to

*Project>Sample>Build.gradile.kit*

```
Dependencies {

Implementation {project (“: kit”))

​                {project (“: external”)) }
```

### Google-Services-JSON

The sample application uses firebase so this has google-services-json.

Information can be found through the top Navigation bar by going to

*Project>sample>src>google-services-json*

```
“Client”: [

{“package_name”: “con.samsung.healthcare.kitsample”}]
```

### URL of research platform And Project Id for App

This sample App interacts with the research platform for health data upload, task sync, and result upload so we have to set the project id and URL

To access this, go to the top navbar and follow the following navigation:

*Project>Sample>main>src>res>values>strings.xml*

```
<string name= “research_platform_endpoint">http://research-platfrm.dev.a1.service.io</string>

String name= “research_project_id”>1</string>
```

## Run sample App

Can’t Run Sample App on the emulator so run it on a real device,