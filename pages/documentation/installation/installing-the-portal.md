---
title: Installing the Web Portal
sidebar: doc_sidebar
permalink: installing-the-portal.html
toc: false
---

Follow these instructions to install, build, and verify the web portal.

> These steps require successful prior completion of the [backend system installation](installing-the-backend.md).

# I. (Optional) Create Development Environment

These steps are only necessary if you intent to make changes to the source code.

1. Set up and install NodeJS version 16.15.0 or higher using the instructions at [https://nodejs.org/en/download/](https://nodejs.org/en/download/){:target="_blank"}

2. Set up yarn:
   1. Run `corepack enable` to activate yarn.

   2. Run `yarn` to install dependencies.

   3. Run `yarn dev` to start development server.


# II. Build Production Environment

1. Determine your URLs.
   
   | Variable    | Description                                                  | Default value |
   | ----------- | ------------------------------------------------------------ | ------------- |
   | API_URL     | Base API URL to access endpoints.                            |               |
   | PUBLIC_PATH | Path will be used to host the app. For example, to host the frontend on [https://example.com/open-source/portal](https://example.com/open-source/portal){:target="_blank"} it should be set to '/open-source/portal'. | /             |

2. Build `Dockerfile` with desired variables provided as build arguments. For example,
   ```
   docker build . \
       -t open-source-portal \
       --build-arg API_URL='https://example.com' \
       --build-arg PUBLIC_PATH='/portal'
   ```
   The resulting Docker image will run nginx on port `80`.

> If you'd prefer to build static files instead of using Docker:
> 
> 1. Install NodeJS version 16.15.0 or higher.
> 2. Run `corepack enable` to activate yarn.
> 3. Run `yarn` to install dependencies.
> 4. Run `yarn build` with desired variables set using environment. For example `API_URL=https://example.com yarn build`.
> 
> The resulting static files will be located in the `/build` folder and can be hosted using any web server.

# III. Launch Web Portal
> As of this writing, Chrome is the only browser supported for accessing the web portal.

1. Navigate to your `PUBLIC_PATH` URL.
2. Enter the [login credentials you created](installing-the-backend.md#xi-create-initial-login) during backend system installation.
