---
title: Installing the Web Portal
sidebar: doc_sidebar
permalink: installing-the-portal.html
toc: false
---

### Prerequisite

#### NodeJS

Setup and install NodeJS version 16.15.0 or higher.

[https://nodejs.org/en/download/](https://nodejs.org/en/download/)

### Development environment setup

1. Run `corepack enable` to activate yarn.
2. Run `yarn` to install dependencies.
3. Run `yarn dev` to start development server.

### Production build

#### Build variables

| Variable    | Description                                                  | Default value |
| ----------- | ------------------------------------------------------------ | ------------- |
| API_URL     | Base API URL to access endpoints.                            |               |
| PUBLIC_PATH | Path will be used to host the app. For example, to host fronted on https://example.com/open-source/portal it should be set to '/open-source/portal'. | /             |

##### **Option 1: Building static files**

1. Install NodeJS version 16.15.0 or higher.
2. Run `corepack enable` to activate yarn.
3. Run `yarn` to install dependencies.
4. Run `yarn build` with desired variables set using environment. For example `API_URL=https://example.com yarn build`.

The resulting static files will be located in `/build` folder and can be hosted using any web server.

##### **Option 2: Docker**

1. Build `Dockerfile` with desired variables provided as build args. For example,
    ```
    docker build . \
        -t open-source-portal \
        --build-arg API_URL='https://example.com' \
        --build-arg PUBLIC_PATH='/portal'
    ```
2. The resulting Docker image will run nginx on port `80`.