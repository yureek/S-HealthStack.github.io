---
title: Managing Members
sidebar: doc_sidebar
permalink: manage-members.html
toc: false
---

Members are the people who are conducting the study.

# Full-Stack Implementations

Your team consists of as many members as is pertinent for you. Thus, the health stack puts no restrictions on the number of members working on studies in your organization. Each study can have any number of the members participate in conducting the study. And, member management happens at the study level.

## Web Portal

We highly recommend you manage your team members through the Samsung Health Stack web portal.

To manage members using the web portal:

1. Refer to [Managing Members](../../portal-guide/study-management/creating-a-study.md) in the web portal user guide.

## API Endpoints

To invite members and assign their role using the API endpoints:

1. Refer to `POST /account-service/invitations` in [Account Service API Endpoints](../../api-reference/account-service-api-endpoints.md) in the API reference.

To assign a role to an existing member using the API endpoints:

1. Refer to `PUT /account-service/user/roles` in [Account Service API Endpoints](../../api-reference/account-service-api-endpoints.md) in the API reference.P

# SDK-Only Implementations

Because member management is part of the health stack's web portal and does not interface with the participant app, creating managing members does not apply to SDK-only implementations.
