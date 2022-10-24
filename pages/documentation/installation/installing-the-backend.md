---
title: Installing the Backend System
sidebar: doc_sidebar
permalink: installing-the-backend.html
toc: false
---

Follow these instructions to install, build, and verify the backend system.

# Install

## I. Install Docker
   1. Install Docker using the instructions at [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/){:target="_blank"}.

## II. Create Network
   1. Create a docker network helm repository proxy (hrp) to connect docker containers. 

      ```
      docker network create hrp
      ```

## III. Deploy Postgres

1. Start the PostgreSQL object-relational database system container.

   ```
   docker run \
       -d \
       --name hrp-postgres \
       --network hrp \
       -e POSTGRES_PASSWORD=password \
       postgres:14.5
   ```
   The command starts the Postgres container under the hrp network and sets the environment variable for the initial password. Pulling the image is done automatically.

2. Download the latest Samsung Health Stack backend system from GitHub. 

   ```
   git clone https://github.com/S-HealthStack/backend-system
   ```

## IV. Create Firebase Service Account

1. Create a Firebase `service-account-key.json` file.

   ```
   cd backend-system
   touch service-account-key.json
   ```

2. Update the `service-account-key.json` file using the instructions at [https://firebase.google.com/docs/admin/setup?authuser=0](https://firebase.google.com/docs/admin/setup?authuser=0){:target="_blank"}.

# Building

## V. Deploy Platform 

1. Test the code and formatting.

   ```
   ./gradlew :platform:ktlintFormat test
   ```

2. Build gradle  to create a jar file of the application.

   ```
   ./gradlew :platform:build -x detekt
   ```

3. Build a docker image of the hrp-platform 0.9.0 in the platform directory.

   ```
   docker build --tag hrp-platform:0.9.0 ./platform/
   ```

4. List all images and containers within the hrp network.

   ```
   docker images | grep hrp
   ```

5. Run the hrp-platform container.

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

6. Verify the hrp-platform container is running.

   ```
   docker ps | grep hrp-platform
   ```

7. Connect to localhost:3030/api/projects. 

   ```
   curl --location --request GET localhost:3030/api/projects
   ```

## VI. Deploy Trino

1. Create and navigate to the `trino/etc/catalog` directory.

   ```
   mkdir -p trino/etc/catalog
   cd trino/etc/catalog
   ```

2. Create the `jvm.config` file.

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

3. Download trinodb/trino version 393.

   ```
   docker pull trinodb/trino:393
   ```

4. Run the hrp-trino container from trinodb/trino image and map hrp-trino default port 8080 to inside of container port of 8080. 

   ```
   docker run \
      -d \
      -p 8080:8080 \
      --name hrp-trino \
      --network hrp \
      --volume trino/etc/catalog \
      trinodb/trino:393
   ```

## VII. Deploy data-query-service

1. Change the directory and build the application data-query-service and generate a jar file, performing a code test. 

   ```
   ./gradlew :data-query-service:build -x detekt
   ```

2. Test a build docker image of data-query-service tag 0.9.0 in data-query-service directory.

   ```
   docker build --tag hrp-data-query-service:0.9.0 ./data-query-service/
   ```

3. List all images related to hrp-a-query-service. 

   ```
   docker images | grep hrp-data-query-service 
   ```

4. Run the hrp-data-query-service container, exposing the environmental USER with value docker to the container and skipping the first line.

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

5. Verify hrp-data-query-service is running.

   ```
   docker ps
   ```

## VIII. (Optional) Deploy SuperTokens

1. Deploy [SuperTokens](https://supertokens.com/){:target="_blank"}.

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

> You don't have to use SuperTokens for this process. You can implement a backend adapter to complement the Auth Service of your choice.

## IX. Deploy Account Service

1. Create a Docker image of the account service.

   ```
   ./gradlew :account-service:build -x detekt

   docker build --tag account-service:0.9.0 ./account-service/
   ```

2. Deploy the account service and identify your email server.

   ```
   docker run \
       -p 8081:8080 \
       --name hrp-account-service \
       --network hrp \
       -e SMTP_HOST=smtp.server.addr \
       -e SMTP_POST=smtp_port \
       -e MAIL_USER=username \
       -e MAIL_USER_PASSWORD=password \
       -d \
       account-service:0.9.0
   ```

# Wrap Up

## X. Verify and Clean Up

1. Test the API calls. 

   ```
   curl --location --request GET localhost:3030/api/projects
   ```

   > If you get an unauthorized message, the platform has deployed successfully.

2. Retrieve logs of the container present at the time of execution. 

   ```
   docker logs -f hrp-platform
   ```

3. Stop and remove the containers, and verify they no longer exist.

   ```
   docker stop hrp-platform
   docker rm hrp-platform
   docker ps -a
   ```

## XI. Create Initial Login

> These steps are temporary for the alpha version only. We intend to have a UI-based solution in place by the beta release.

1. Create the team-admin role.

   ```
   curl --location --request PUT 'localhost:3567/recipe/role' \
   --header 'Content-Type: application/json' \
   --data-raw '{
     "role": "team-admin"
   }'
   ```

2. Create the initial user login.

   ```
   curl --location --request POST 'localhost:3567/recipe/signup' \
   --header 'cdi-version: 2.15' \
   --header 'Content-Type: application/json' \
   --data-raw '{
    "email": "your_address@your_email.com",
    "password": "your_password"
   }
   ```

   > Successful creation results in a response similar to: 
   >
   > ```
   > {
   >   "status": "OK",
   >   "user": {
   >       "email": "team-admin@samsung.com",
   >       "id": "785d492b-688f-49c1-adbb-e9c00ed0c5b4",
   >       "timeJoined": 1664864683438
   >   }
   > }
   > ```

3. Assign the role to the user.

   ```
   curl --location --request PUT 'localhost:3567/recipe/user/role' \
   --header 'Content-Type: application/json' \
   --data-raw '{
     "userId": "785d492b-688f-49c1-adbb-e9c00ed0c5b4",
     "role": "team-admin"
   }
   ```
