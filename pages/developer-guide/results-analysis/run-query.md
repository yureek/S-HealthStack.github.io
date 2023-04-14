---
title: Running a Data Query
sidebar: doc_sidebar
permalink: run-query.html
toc: false
---

# Full-Stack Implementations

## Web Portal

We highly recommend you use the Samsung Health Stack web portal to query your data. Querying within the web portal allows you to gain some simple insights into your data. You can run queries at any point in the study.

> For more detailed analysis, refer to [Exporting Data for External Analysis](../../portal-guide/results-analysis/exporting-data.md).

To run a data query using the web portal:

1. Refer to [Running a Data Query](../../portal-guide/results-analysis/running-a-query.md) in the web portal user guide.

## API Endpoints

To run a query using the API endpoints:

1. Refer to `POST /projects/{projectId}/graphql` in [Data Query Service API Endpoints](../../api-reference/data-query-service-api-endpoints.md).
2. Use your preferred method to view the resulting data.

# SDK-Only Implementations

Because exporting data is part of the Samsung Health Stack's web portal and does not interface with the participant app, data cannot be exported as such in SDK-only implementations. However, you can develop your own method to export the data.