---
title: Creating a Study
sidebar: doc_sidebar
permalink: create-study.html
toc: false
---

A Samsung Health Stack study is a container you create to manage all aspects of your participant study. A container consists of the team members running the study, the list of participants, participant surveys, survey results, participant vital signs tracked through the wearable device, graphs giving insights into the data collected, and more.

# Full-Stack Implementations

## Web Portal

We highly recommend you create studies through the Samsung Health Stack web portal.

To create a study using the web portal:

1. Refer to [Creating a Study](../../portal-guide/study-management/creating-a-study.md) in the web portal user guide.

## API Endpoints

To create a study using the API endpoints:

1. Refer to `POST /projects` in [Study API Endpoints](../../api-reference/study-api-endpoints.md) in the API reference.

# SDK-Only Implementations

Because health stack studies are part of the health stack's web portal and do not interface with the participant app, creating health stack studies does not apply to SDK-only implementations.
