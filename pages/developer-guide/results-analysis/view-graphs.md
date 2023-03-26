---
title: Viewing Graphs and Charts
sidebar: doc_sidebar
permalink: view-graphs.html
toc: false
---

# Full-Stack Implementations

## Web Portal

We highly recommend you use the Samsung Health Stack web portal to view graphs and charts representing the collected study data. The web portal provides line graphs and scatter plot charts for easy visualization of the data collected through your study. Each one provides views of the general trends and of datapoints filtered by demographic.

To view graphs and charts using the web portal:

1. Refer to [Viewing Graphs and Charts](../../portal-guide/results-analysis/viewing-graphs.md) in the web portal user guide.

## API Endpoints

To create graphs and charts using the API endpoints:

1. Refer to `POST /projects/{projectId}/graphql` in [Study API Endpoints](../../api-reference/study-api-endpoints.md) in the API reference to fetch study data such as participant list, sensor data, task results.
2. Develop your own graphs and charts to display the information as needed for your use case.

# SDK-Only Implementations

Because the graphs and charts are part of the health stack's web portal and do not interface with the participant app, creating them does not apply to SDK-only implementations. However, you can develop your own graphs and charts to display the information as needed for your use case.