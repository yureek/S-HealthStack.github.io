---
search: exclude
layout: codelab
title: "Research Hub Code Lab"
description: "Prepare back-end system"
index: 2
topic: "Set up back-end system"
---

# What you will do

The first step is set up back-end environment for the research.
This includes preparing data collection system and research management system.

Luckily, Healthcare Research Hub provides the ready-to-use components for these uses.

Healthcare research platform provides back-end API server
and research portal provides front-end interfaces for researchers to control and to manage the research. 

# Things to be deployed

In order to make a working back-end environment,
you should deploy following subcomponents into your serving environments.

* Platform API Server
* Data Store
* Data Query Engine
* Dashboard Portal Server

Research Hub provides all these required components.
Although some could be replaced by your pre-existing system,
let's assume vanilla environment in this code lab.

## Vanilla environment

What mentioned as vanilla environment is ...

.. description of vanilla environments ..

## Deployment using Dockerfiles

By using pre-built docker images of each component, you can easily set up back-end environment.

You can also customize each component to fit more for your needs by building your own docker images from source files.
For detailed instructions to build, please refer full documentations.

### Deploying procedures

Step 1 ...

Step 2 ...

# Check everything is OK

If you set up properly, you can access the portal with like this.

# Next step

[Register the research](3-NEWRESEARCH)
