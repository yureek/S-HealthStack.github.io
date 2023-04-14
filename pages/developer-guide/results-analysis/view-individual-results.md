---
title: Viewing Individual Results
sidebar: doc_sidebar
permalink: view-individual-results.html
toc: false
---

# Full-Stack Implementations

## Web Portal

We recommend using the Samsung Health Stack web portal to view individual participant records. The web portal logs individual participants' average records per data class. The reports include data such as average step count or average heart rate. You can view the records of:
- A specific participant.
- A participant relating to a datapoint of interest.

To view individual participant records using the web portal:

1. Refer to [Viewing Individual Results](../../portal-guide/results-analysis/viewing-individual-results.md) in the web portal user guide.

## API Endpoints

To create graphs and charts using the API endpoints:

1. Refer to `POST /projects/{projectId}/graphql` in [Study API Endpoints](../../api-reference/study-api-endpoints.md) in the API reference to fetch individual participant results data.
2. Develop your own graphs and charts to display the information as needed for your use case.

# SDK-Only Implementations

Because displaying the individual participants' data is part of the Samsung Health Stack's web portal and does not interface with the participant app, displaying this data does not apply to SDK-only implementations. However, you can develop your own data management system to display the information as needed.