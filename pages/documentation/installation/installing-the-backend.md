---
title: Installing the Backend System
sidebar: doc_sidebar
permalink: installing-the-backend.html
toc: false
---

# Prerequisite

## Docker

Install using the following guide [Install Docker Engine - Docker Documentation](https://docs.docker.com/engine/install/)

# Installation

## 1. Create Network

Create a docker network **hrp** to connect docker containers by the following command: 

```
docker network create hrp
```

## 2. Deploy Postgres

After creating the network, deploy Postgres by following the instructions. 

Run the Postgres container, the command will start the Postgres container under hrp network and set the environmental variable for the initial password. 

Pulling the image will be done automatically.

```
docker run \
    -d \
    --name hrp-postgres \
    --network hrp \
    -e POSTGRES_PASSWORD=password \
    postgres:14.5
```

Now, clone the latest version with: 

```
git clone https://github.com/S-HealthStack/backend-system
```

The git clone command will download the repository that already exists on GitHub including all files.

## 3. Create Firebase `service-account-key.json` file 

Now create a firebase service account JSON file in the backend server directory.

You can follow the detailed documentation in [here](https://firebase.google.com/docs/admin/setup?authuser=0).

```
cd backend-system
touch service-account-key.json
```

And update the `service-account-key.json` file.

# Building

## 4. Deploy platform 

Now deploy the platform by following below instructions. 

The first step is testing the code and formatting by:

```
./gradlew :platform:ktlintFormat test
```

The next step is to build by using grade build command that creates a jar file of the application:

```
./gradlew :platform:build -x detekt
```

After successful gradle build, build docker image of hrp-platform 0.9.0 in platform` directory by using command: 

```
docker build --tag hrp-platform:0.9.0 ./platform/
```

**Now list all images and containers within hrp network by grep command.** 

```
docker images | grep hrp
```

**After a successful build, run the container of hrp-platform.** 

```
docker run \
    -d \
    -p 3030:3030 \
    --name hrp-platform \
    --network hrp \
    -e DB_HOST=hrp-postgres \
    -e DB_PASSWORD=password \
    -e GOOGLE_APPLICATION_CREDENTIALS=service-account-key.json \
    hrp-platform:0.9.0
```

**To ensure hrp-platform container is running use ps command.** 

```
docker ps | grep hrp-platform
```

**Now connect to localhost:3030/api/projects**. 

```
curl --location --request GET localhost:3030/api/projects
```

## 5. Deploy trino

Now, deploy trino by creating new directory trino/etc/catalog and then change directory: 

```
mkdir -p trino/etc/catalog
```

Then, create the `jvm.config` file 

```
echo "\
-server
-Xmx16G
-XX: InitialRAMPercentage=80 
-XX:MaxRAMPercentage=80 
-XX:G1HeapRegionSize=32M 
-XX:+ExplicitGCInvokesConcurrent 
-XX:+ExitOnOutOfMemoryError 
-XX:+HeapDumpOnOutOfMemoryError 
-XX:-OmitStackTraceInFastThrow 
-XX : ReservedCodeCacheSize=512M 
-XX:PerMethodRecompilationCutoff=10000 
-XX:PerBytecodeRecompilationCutoff=10000 
-Djak.attach.allowAttachSelf=true 
-Didk.nio.maxCachedBufferSize=2000000 
-XX:+UnlockDiagnosticVMOptions 
-XX:+UseAESCTRIntrinsics" > trino/etc/catalog/jvm.config 
```

**After successful configuration pull(download) trinodb/trino 393 version.** 

```
docker pull trinodb/trino:393
```

Further, run the hrp-trino container from trinodb/trino image and map hrp-trino default port 8080 to inside of container port of 8080 by using the following command. 

```
docker run \
    -d \
    -p 8080:8080 \
    --name hrp-trino \
    --network hrp \
    --volume trino/etc/catalog \
    trinodb/trino:393
```

## 6. Deploy data-query-service

Now, deploy data-query-service. The first step is to change the directory and build the application data-query-service and generate a jar file, performing a code test. 

```
./gradlew :data-query-service:build -x detekt
```

**After gradle build and code, test a build docker image of data-query-service tag 0.9.0 in data-query-service directory.** 

```
docker build --tag hrp-data-query-service:0.9.0 ./data-query-service/
```

list all images related to hrp-a-query-service by using grep command. 

```
docker images | grep hrp-data-query-service 
```

**Run hrp-data-query-service container, exposing the environmental USER with value docker to the container and skipping the first line** 

```
docker run \
    -d \
    --name hrp-data-query-service \
    --network hrp \
    -e CATALOG_USER=postgres \
    -e TRINO_HOST=hrp-trino \
    -e TRINO_PORT=8080 \
    hrp-data-query-service:0.9.0
```

To ensure successful run, ps command will be used to show all running containers 

```
docker ps
```

## 7. (Optional) Deploy SuperTokens

Now, deploy [SuperTokens](https://supertokens.com/).

<span style="color:red">You don't have to use SuperTokens for this process. Implement a back-end adapter to complement the Auth Service of your choice. The sample contains adapter of SuperTokens</span>

```
docker run \
    -p 3567:3567 \
    --name hrp-supertokens \
    --network hrp \
    -e POSTGRESQL_USER=postgres \
    -e POSTGRESQL_HOST=hrp-postgres \
    -e POSTGRESQL_PORT=5432 \
    -e POSTGRESQL_PASSWORD=password \
    -d registry.supertokens.io/supertokens/supertokens-postgresql
```

## 8. Deploy Account Service

Run below command to create a docker image of account service.

```
./gradlew :account-service:build -x detekt

docker build --tag account-service:0.9.0 ./account-service/
```

Now, deploy the account service using docker container.

```
docker run \
    --name hrp-account-service \
    --network hrp \
    -d \
    account-service:0.9.0
```

# Testing APIs

## Test API calls

Now test API calls by using CURL command. 

```
curl --location --request GET localhost:3030/api/projects
```

If you get unauthorized message, platform is deployed successfully.

## Retrieve logs of the container

To retrieve logs of the container present at the time of execution use: 

```
docker logs -f hrp-platform
```

## Stop and remove container

Now to stop and remove containers use the following syntax. Further to ensure running container list use docker ps. 

```
docker stop hrp-platform

docker rm hrp-platform

docker ps -a
```
