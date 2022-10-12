---
title: Configuring the App Environment
sidebar: doc_sidebar
permalink: configuring-the-app.html
toc: false
---

Several steps are required to connect the app with the outside world:

### Prerequisite

#### OpenJDK

Setup and install OpenJDK 11

[https://openjdk.org/install/](https://openjdk.org/install/)

#### Android Studio 

Setup and install Android Studio on Windows, macOS, or Linux.

[https://developer.android.com/studio](https://developer.android.com/studio)

#### Firebase

Create firebase project.

[https://firebase.google.com/docs/android/setup](https://firebase.google.com/docs/android/setup)

#### Clone the repository

Clone the Research-SDK using the following command 

```
git clone https://github.com/S-HealthStack/app-sdk
```

### Configurations

#### Kit and External

This sample application depends on SDK modules so it must have kit and external.

Dependencies can be declared as below.


*samples>researchsample>build.gradle.kts*

**Without AAR**

```
dependencies {
    implementation(project(":kit"))
    implementation(project(":external"))
}
```

**With AAR**

```
dependencies {
    implementation(files("shs-libs/app-sdk-external-alpha.aar"))
    implementation(files("shs-libs/app-sdk-kit-alpha.aar"))
}
```

#### Set URL of backend server and project(study) id for App

This sample App interacts with the backend system for health data upload, task sync, and task result upload so we have to set the project(study) id and URL.

Please open the following file for setting:


*res/values/strings.xml*

```
<string name="research_platform_endpoint">https://{endpoint}</string>
<string name="research_project_id">{projectId}</string>
```

### Develop the application

Be aware that the sample app cannot be run on an emulator, and must be tested on a real device.

You can check the detailed documentation in [here](https://developer.android.com/studio/run/device).