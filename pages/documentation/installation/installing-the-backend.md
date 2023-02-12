---
title: Installing the Backend System
sidebar: doc_sidebar
permalink: installing-the-backend.html
toc: false
---

Follow these instructions to install, build, and verify the backend system.

# Prerequisites

## I. Install Java 17

1. Open a Linux terminal window.

2. Install the dependencies for an Oracle JDK 17 installation.

   ```
   sudo apt update
   sudo apt install -y libc6-x32 libc6-i386
   ```

3. Download Oracle Java JDK 17.

   ```
   wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb
   ```

4. Install Oracle Java JDK 17.

   ```
   sudo dpkg -i jdk-17_linux-x64_bin.deb
   ```

5. Install either the OpenJDK or JRE package.
   - OpenJDK 17 JDK
      ```
      sudo apt install -y openjdk-17-jdk
      ```

   - OpenJDK 17 JRE
      ```
      sudo apt install -y openjdk-17-jre
      ```

6. Verify that you have successfully installed version 17.

   ```
   java -version
   ```

## II. Install Docker

1. Install Docker.

      ```
      sudo apt install docker.io
      ```
      
2. Confirm successful installation.
      ```
      docker --version
      sudo systemctl status docker
      ```

# Build

>  For your convenience, we've created some of the config files for you. To optionally use them, navigate to [this GitHub directory](https://github.com/S-HealthStack/S-HealthStack.github.io/tree/main/files/installing-the-backend){:target="_blank"}, download **backend-config-files.zip**, extract the contents to a temporary location of your choosing, and move each desired file into place as you encounter them in the steps below.

## III. Create a Network

   1. Create a docker network repository proxy (hrp) to connect docker containers.

      ```
      sudo docker network create hrp
      ```

## IV. Deploy Postgres

1. Start the PostgreSQL object-relational database system container.

   ```
   sudo docker run \
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

## V. Deploy SuperTokens

You don't have to use SuperTokens. You can implement a backend adapter to complement the authorization service of your choice. If you choose to use supertokens:
1. In Postgres, create a database named `supertokens`.

2. Deploy [SuperTokens](https://supertokens.com/){:target="_blank"}.

   ```
   docker run \
     -p 3567:3567 \
     --name hrp-supertokens \
     --network hrp \
     -e POSTGRESQL_USER=postgres \
     -e POSTGRESQL_HOST=hrp-postgres \
     -e POSTGRESQL_PORT=5432 \
     -e POSTGRESQL_PASSWORD=password \
     -e POSTGRESQL_DATABASE_NAME=supertokens \
     -d \
     supertokens/supertokens-postgresql
   ```

## VI. Deploy Account Service

1. In Postgres, create a database named `tokens`.

2. Create a Docker image of account-service.

   ```
   ./gradlew :account-service:build -x detekt
 
   docker build --tag hrp-account-service:0.9.0 ./account-service/
   ```

3. Deploy the account service and identify your email server.

   ```
   docker run \
     -p 8080:8080 \
     --name hrp-account-service \
     --network hrp \
     -e SMTP_HOST=smtp.server.addr \
     -e SMTP_POST=smtp_port \
     -e MAIL_USER=username \
     -e MAIL_USER_PASSWORD=password \
     -e SUPER_TOKEN_URL=http://hrp-supertokens:3567 \
     -e JWK_URL=http://hrp-supertokens:3567/recipe/jwt/jwks \
     -e DB_URL=hrp-postgres:5432 \
     -e DB_NAME=tokens \
     -e DB_USERNAME=postgres \
     -e DB_PASSWORD=password \
     -d \
     hrp-account-service:0.9.0
   ```

## VII. Create Firebase Service Account

1. Create a Firebase **service-account-key.json** file.
   ```
   cd backend-system/platform
   touch service-account-key.json
   ```

2. In the Firebase console, navigate to **Settings > Service accounts**.

3. Click **Generate new private key**.

4. Update the **service-account-key.json** file using the instructions at [https://firebase.google.com/docs/admin/setup?authuser=0](https://firebase.google.com/docs/admin/setup?authuser=0){:target="_blank"}.
   >  Be sure to keep this file private and securely-stored. It contains your unique security key.

## VIII. Deploy Platform

1. Test and format the code.
   
   ```
   ./gradlew :platform:ktlintFormat test
   ```
   
2. Create a jar file of the application.

   ```
   ./gradlew :platform:build -x detekt
   ```

3. Create a Docker image of hrp-platform 0.9.0 in the platform directory.

   ```
   docker build --tag hrp-platform:0.9.0 ./platform/
   ```

4. In Postgres, create a database named `healthstack`.

5. Run the hrp-platform container.

   ```
   docker run \
     -d \
     -p 3030:3030 \
     --name hrp-platform \
     --network hrp \
     -e DB_HOST=hrp-postgres \
     -e DB_NAME=healthstack \
     -e DB_USERNAME=postgres \
     -e DB_PASSWORD=password \
     -e GOOGLE_APPLICATION_CREDENTIALS=service-account-key.json \
     -e JWK_URL=http://hrp-supertokens:3567/recipe/jwt/jwks \
     -e ACCOUNT_SERVICE_URL=http://hrp-account-service:8080 \
     hrp-platform:0.9.0
   ```

6. Verify the hrp-platform container is running.

   ```
   docker ps | grep hrp-platform
   ```

## IX. Deploy trino-rule-update-service

1. Create the **trino-rule-update-service/Dockerfile** file with these contents:

   ```
   FROM openjdk:17.0.2-jdk-oracle
   ARG JAR_FILE=build/libs/*.jar
   COPY ${JAR_FILE} application.jar
   ENTRYPOINT ["java","-jar","/application.jar"]
   ```

2. Create a Docker image of trino-rule-update-service.

   ```
   ./gradlew :trino-rule-update-service:build -x detekt
    
   docker build --tag hrp-trino-rule-update-service:0.9.0 ./trino-rule-update-service/
   ```
3. Create a **rule-update** directory.

4. Deploy trino-rule-update-service.

   ```
   docker run \
     --name hrp-trino-rule-update-service \
     --network hrp \
     -e FIXED_DELAY_MILLISEC=5000 \
     -e ACCOUNT_SERVICE_URL=http://hrp-account-service:8080 \
     -v /root/healthstack/rule-update:/etc/trino/access-control \
     -d \
     hrp-trino-rule-update-service:0.9.0
   ```

## X. Deploy Trino

1. Download trinodb/trino version 402.

```
   docker pull trinodb/trino:402
```

2. Create the **trino/etc/catalog/jvm.config** file with these contents:

   ```
   echo "\
   -server
   -Xmx16G
   -XX:InitialRAMPercentage=80
   -XX:MaxRAMPercentage=80
   -XX:G1HeapRegionSize=32M
   -XX:+ExplicitGCInvokesConcurrent
   -XX:+ExitOnOutOfMemoryError
   -XX:+HeapDumpOnOutOfMemoryError
   -XX:-OmitStackTraceInFastThrow
   -XX:ReservedCodeCacheSize=256M
   -XX:PerMethodRecompilationCutoff=10000
   -XX:PerBytecodeRecompilationCutoff=10000
   -Djak.attach.allowAttachSelf=true
   -Didk.nio.maxCachedBufferSize=2000000
   -XX:+UnlockDiagnosticVMOptions
   -XX:+UseAESCTRIntrinsics" > trino/etc/catalog/jvm.config
   ```

3. Create the **trino/etc/postgresql/postgresql.properties** file with these contents:

   ```
   connector.name=postgresql
   connection-url=jdbc:postgresql://hrp-postgres:5432/healthstack
   connection-user=postgres
   connection-password=password
   ```

4. Run the hrp-trino container trinodb/trino image (mapping the hrp-trino default port 8080).

   ```
   docker run \
     -d \
     --name hrp-trino \
     --network hrp \
     -v /root/healthstack/rule-update:/etc/trino/access-control \
     -v /root/healthstack/trino/etc/catalog/jvm.config:/etc/trino/jvm.config \
     -v /root/healthstack/trino/etc/postgresql/postgresql.properties:/etc/trino/catalog/postgresql.properties \
     trinodb/trino:402
   ```

## XI. Deploy data-query-service

1. Change the directory and build the application data-query-service and generate a jar file, performing a code test.

   ```
   ./gradlew :data-query-service:build -x detekt
   ```

2. Create a Docker image of data-query-service tag 0.9.0 in the **data-query-service** directory.

   ```
   docker build --tag hrp-data-query-service:0.9.0 ./data-query-service/
   ```

3. Run the hrp-data-query-service container.

   ```
   docker run \
     -d \
     --name hrp-data-query-service \
     --network hrp \
     -e TRINO_CATALOG=postgresql \
     -e TRINO_DEFAULT_USER=postgres \
     -e TRINO_HOST=hrp-trino \
     -e TRINO_PORT=8080 \
     -e JWK_URL=http://hrp-supertokens:3567/recipe/jwt/jwks \
     hrp-data-query-service:0.9.0
   ```

4. Verify hrp-data-query-service is running.

   ```
   docker ps
   ```

## XII. Haproxy Configuration

1. Create the Haproxy service **haproxy/404.http** file with these contents:

   ```
   HTTP/1.0 404 Not Found
   Cache-Control: no-cache
   Connection: close
   Content-Type: text/html
   <!DOCTYPE html><html><head><title>404 - Error report</title></head>
   <body>404 Not Found</body>
   </html>
   ```

2. Create the **haproxy/cors.lua** file with these contents:

   ```
   core.register_service("cors-response", "http", function(applet)
   applet:set_status(200)
   applet:add_header("Content-Length","0")
   applet:add_header("Access-Control-Allow-Origin",applet.headers["origin"][0])
   applet:add_header("Access-Control-Allow-Credentials","true")
   applet:add_header("Access-Control-Allow-Headers","*")
   applet:add_header("Access-Control-Allow-Methods","GET, HEAD, POST, PUT, DELETE, PATCH, OPTIONS")
   applet:add_header("Access-Control-Max-Age", "1728000")
   applet:start_response()
   end)
   ```

3. Create the **haproxy/cors-origins.lst** file with these contents:

   ```
   localhost.*
   .*\.mydomain\.com:[8080|8443]
   ```

4. Create the **haproxy/haproxy.cfg** file with these contents:

   ```
   global
   lua-load /usr/local/etc/haproxy/cors.lua
   defaults
   log global
   mode http
   timeout connect 5000ms
   timeout client 50000ms
   timeout server 50000ms
   option httplog
   log stdout local0
    
   frontend stats
   bind *:8404
   stats enable
   stats uri /
   stats refresh 10s
    
   frontend http_frontend
   bind :3035
   compression algo gzip
   compression type text/css text/html text/javascript application/javascript text/plain text/xml application/json
    
   # CORS configuration
   # capture origin HTTP header
   capture request header origin len 128
   # add Access-Control-Allow-Origin HTTP header to response if origin matches the list of allowed URLs
   http-response add-header Access-Control-Allow-Origin %[capture.req.hdr(0)] if !METH_OPTIONS { capture.req.hdr(0) -m reg -f /usr/local/etc/haproxy/cors-origins.lst }
   # if a preflight request is made, use CORS preflight backend
   http-request use-service lua.cors-response if METH_OPTIONS { capture.req.hdr(0) -m reg -f /usr/local/etc/haproxy/cors-origins.lst }
    
   acl has_account-service path_beg /account-service
   acl has_sql_query path_reg ^\/api\/projects\/[0-9]*\/sql$
   acl has_graphql_query path_reg ^\/api\/projects\/[0-9]*\/graphql$
   acl has_platform path_beg /api/projects
    
   use_backend account-service if has_account-service
   use_backend query-service if has_sql_query
   use_backend query-service if has_graphql_query
   use_backend platform if has_platform
   default_backend empty
    
   backend platform
   http-request set-header Host localhost
   http-response set-header Server None
   server platform hrp-platform:3030 check
    
   backend account-service
   http-request set-header Host localhost
   http-response set-header Server None
   server account-service hrp-account-service:8080 check
       
   backend query-service
   http-request set-header Host localhost
   http-response set-header Server None
   server query-service hrp-data-query-service:3030 check
    
   backend empty
   errorfile 503 /usr/local/etc/haproxy/errors/404.http
   ```

5. Run the hrp-proxy container.

   ```
   docker run \
     -d \
     -p 3035:3035 \
     -p 8404:8404 \
     --name hrp-proxy \
     --network hrp \
     -v /root/healthstack/haproxy/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg:ro 
     -v /root/healthstack/haproxy/404.http:/usr/local/etc/haproxy/errors/404.http:ro 
     -v /root/healthstack/haproxy/cors-origins.lst:/usr/local/etc/haproxy/cors-origins.lst:ro -v /root/healthstack/haproxy/cors.lua:/usr/local/etc/haproxy/cors.lua:ro  
     haproxy:2.6.6
   ```

## XII. Deploy docker-compose.yml

1. Create the **docker-compose.yml** file with these contents:
   ```
   version: '3.5'
    
   services:
     postgres:
       container_name: hrp-postgres
       image: postgres:14.5
       environment:
         POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:-password}
       ports:
         - "5432:5432"
       networks:
         - hrp
       restart: unless-stopped
     supertokens:
       container_name: hrp-supertokens
       image: supertokens/supertokens-postgresql
       depends_on:
           - postgres
       environment:
           POSTGRESQL_USER: ${POSTGRESQL_USER:-postgres}
           POSTGRESQL_HOST: ${POSTGRESQL_HOST:-hrp-postgres}
           POSTGRESQL_PORT: ${POSTGRESQL_PORT:-5432}
           POSTGRESQL_PASSWORD: ${POSTGRESQL_PASSWORD:-password}
           POSTGRESQL_DATABASE_NAME: ${POSTGRESQL_DATABASE_NAME:-supertokens}
       ports:
           - "3567:3567"
       networks:
           - hrp
     platform:
       container_name: hrp-platform
       image: hrp-platform:0.9.0
       depends_on:
           - postgres
       environment:
           DB_HOST: ${DB_HOST:-hrp-postgres}
           DB_PASSWORD: ${DB_HOST:-password}
           GOOGLE_APPLICATION_CREDENTIALS:    ${GOOGLE_APPLICATION_CREDENTIALS:-service-account-key.json}
           JWK_URL: ${JWK_URL:-http://hrp-supertokens:3567/recipe/jwt/jwks}
           ACCOUNT_SERVICE_URL: ${ACCOUNT_SERVICE_URL:-http://hrp-account-service:8081}
       ports:
           - "3030:3030"
       networks:
         - hrp
     account-service:
       container_name: hrp-account-service
       image: account-service:0.9.0
       depends_on:
           - supertokens
       environment:
           SMTP_HOST: ${SMTP_HOST:-smtp.gmail.com}
           SMTP_PORT: ${SMTP_PORT:-465}
           MAIL_USER: ${MAIL_USER:-testl@gmail.com}
           MAIL_USER_PASSWORD: ${MAIL_USER_PASSWORD:-PasswordTest}
           SUPER_TOKEN_URL: ${SUPER_TOKEN_URL:-http://hrp-supertokens:3567}
           JWK_URL: ${JWK_URL:-http://hrp-supertokens:3567/recipe/jwt/jwks}
         
       ports:
           - "8081:8081"
       networks:
           - hrp
     trino:
       container_name: hrp-trino
       image: trinodb/trino:402
       depends_on:
           - postgres
       ports:
           - "8080:8080"
       volumes:
           - ./rule-update/:/etc/trino/access-control/
           - ./trino/etc/catalog/jvm.config:/etc/jvm.config
           - ./trino/etc/postgresql/postgresql.properties:/etc/trino/catalog/postgresql.properties
       networks:
           - hrp
    
     data-query-service:
       container_name: hrp-data-query-service
       image: hrp-data-query-service:0.9.0
       depends_on:
           - trino
       environment:
           TRINO_CATALOG: ${TRINO_CATALOG:-postgresql}
           TRINO_HOST: ${TRINO_HOST:-hrp-trino}
           TRINO_PORT: ${TRINO_PORT:-8080}
           JWK_URL: ${JWK_URL:-http://hrp-supertokens:3567/recipe/jwt/jwks}
           debug: true
       ports:
           - "3031:3031"
       networks:
           - hrp
     trino-rule-update-service:
       container_name: hrp-trino-rule-update-service
       image: trino-rule-update-service:0.9.0
       environment:
           FIXED_DELAY_MILLISEC: ${FIXED_DELAY_MILLISEC:-5000}
           ACCOUNT_SERVICE_URL: ${ACCOUNT_SERVICE_URL:-http://hrp-account-service:8081}
       depends_on:
           - account-service
       volumes:
           - ./rule-update/rules.json:/etc/trino/access-control/rules.json
       networks:
           - hrp
     web:
       container_name: open-source-portal
       image: docker.io/library/open-source-portal
       depends_on:
           - account-service
       ports:
         - "80:80"
       networks:
         - hrp
       restart: unless-stopped
     haproxy:
       image: haproxy:2.6.6
       container_name: hrp-balancer
       depends_on:
           - web
       ports:
         - "3035:3035"
         - "8404:8404"
       volumes:
           - ./haproxy/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg:ro
           - ./haproxy/404.http:/usr/local/etc/haproxy/errors/404.http:ro
           - ./haproxy/cors-origins.lst:/usr/local/etc/haproxy/cors-origins.lst:ro
           - ./haproxy/cors.lua:/usr/local/etc/haproxy/cors.lua:ro
       networks:
         - hrp
       restart: unless-stopped
    networks:
     hrp:
       external: true
       driver: bridge
   ```
   
2. Start the **docker-compose.yml** file.

   ```
   docker-compose up -d
   ```

3. Retrieve logs of the container present at the time of execution.

   ```
   docker logs -f hrp-platform
   ```


# Wrap Up

## XIII. Create Initial Login

> These steps are temporary. We intend to implement a UI-based solution by the official release.

### With Mail Server
When a mail server is available, perform these steps:

1. Create the initial user login.

   ```
   curl --location --request POST 'localhost:8080/account-service/signup'
   --header 'Content-Type: application/json'
   --data-raw '{
     "email": "your_address@your_email.com",
     "password": "your_password"
   }'
   ```
2. Check the verification email and activate the login.
> The system automatically assigns the `team-admin` role to the first user to create a login.

### Without Mail Server
When a mail server is not available, perform these steps:

1. Create the team-admin role.

   ```
   curl --location --request PUT 'localhost:3567/recipe/role'
   --header 'Content-Type: application/json'
   --data-raw '{ "role": "team-admin" }'
   ```

   > Successful result: 
   >
   > ```
   > {
   >   "status": "OK",
   >   "createdNewRole":true
   > }
   > ```

2. Create the initial user login.

   ```
   curl --location --request POST 'localhost:3567/recipe/signup'
   --header 'cdi-version: 2.15'
   --header 'Content-Type: application/json'
   --data-raw '{ "email": "your_address@your_email.com", "password": "your_password" }'
   ```

   > Successful result is similar to: 
   >
   > ```
   > {
   >   "status": "OK",
   >   "user": {
   >       "email": "your_address@your_email.com",
   >       "id": "785d492b-688f-49c1-adbb-e9c00ed0c5b4",
   >       "timeJoined": 1664864683438
   >   }
   > }
   > ```

3. Copy the returned `id` to the `userId` field in the following command to assign the team-admin role to the user.

   ```
   curl --location --request PUT 'localhost:3567/recipe/user/role'
   --header 'Content-Type: application/json'
   --data-raw '{
     "userId": "785d492b-688f-49c1-adbb-e9c00ed0c5b4",
     "role": "team-admin"
   }'
   ```

   > Successful result: 
   >
   > ```
   > {
   >   "status": "OK",
   >   "didUserAlreadyHaveRole":false
   > }
   > ```

4. Copy the returned `email` to the `email` field and the returned `id` to the `userId` field in the following command to retrieve a verifcation token.

   ```
   $ curl --location --request POST 'localhost:3567/recipe/user/email/verify/token' \
   --header 'Content-Type: application/json' \
   --data-raw '{
     "userId": "7e5b869e-ed96-4768-9595-93a459f9f5ad",
     "email": "team-admin@samsung.com"
   }'
   ```

   > Successful result: 
   >
   > ```
   > {
   >   "status":"OK",
   >   "token":"MTEwMjg5OTNjY2...ZDY0ZjUyZjc0M2Vj"
   > }
   > ```

5. Copy the returned `token` to the `token` field to activate your account.

   ```
   $ curl --location --request POST 'localhost:3567/recipe/user/email/verify' \
   --header 'Content-Type: application/json' \
   --data-raw '{
       "method": "token",
       "token": "MTEwMjg5OTNjY2...ZDY0ZjUyZjc0M2Vj"
   }'
   ```

   > Successful result: 
   >
   > ```
   > {
   >   "status":"OK",
   >   "userId":"7e5b869e-ed96-4768-9595-93a459f9f5ad",
   >   "email":"team-admin@samsung.com"
   > }
   > ```

## XIV. Launch the Web Portal

1. In Chrome, navigate to http://localhost.

2. Specify the port you configured in the **haproxy.cfg** file.

   1. Press F12 to open the inspector.
   2. Click the **Application** tab.
   3. Select **Local Storage > localhost**.
   4. Change the value for the `API_URL` key to `http://localhost:3035`.
3. Press F5 to reload the page and open the web portal.

<!-- ## XIV. Verify Project Access-->

<!-- 1. Test the API calls.-->

<!--   ```-->
<!--   curl --location --request GET localhost:3030/api/projects-->
<!--   ```-->

<!--   > If you get an unauthorized message, the platform has deployed successfully.-->

<!-- ## XV. Launch the Web Portal-->
