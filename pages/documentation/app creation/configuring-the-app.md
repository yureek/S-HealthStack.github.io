---
title: Configuring the App Environment
sidebar: doc_sidebar
permalink: configuring-the-app.html
toc: false
---

In addition to the [app SDK installation steps](../installation/installing-the-sdk.md), several steps are required to connect the app with the outside world:

1. Register your app with Firebase and update the starter-app/app/google-service.json configuration file.
> Refer to [https://firebase.google.com/docs/android/setup](https://firebase.google.com/docs/android/setup) for details.

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