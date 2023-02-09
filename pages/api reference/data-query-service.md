---
title: Data Query API Endpoints
sidebar: doc_sidebar
permalink: data-query-api-endpoints.html
toc: false
---
# Data Query Service
## Version: 0.5.0

### /sql

#### POST
##### Summary

Search Health Data by executing the given SQL statement.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| projectId | path | The id of the project to retrieve. | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Expected response to a valid request. |
| default | Unexpected Error |

### Models

#### Error

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| code | integer |  | Yes |
| message | string |  | Yes |
