---
title: Role-Based Access Control
sidebar: doc_sidebar
permalink: role-based-access-control.html
toc: false
---

The role-based access control feature provides security with differing levels of access permission granted to different roles.

# Team Roles

Team roles control access at the health stack level. Available roles are:

- Team Admin
- Team Member

The table shows available features for each role.

<table>
  <tr>
    <th style="text-align: center; border-right: 1px solid black;">Features</th>
    <th colspan="2" style="text-align: center;">Roles</th>
  </tr>
   <tr>
    <th style="text-align: center; border-right: 1px solid black;"></th>
    <th style="text-align: center;">Team Admin</th>
    <th style="text-align: center;">Team Member</th>
  </tr>
  <tr>
    <td style="border-right: 1px solid black;">Create Study</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">No</td>
  </tr>
  <tr>
    <td style="border-right: 1px solid black;">Invite New Members</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">No</td>
  </tr>
</table>




# Study Roles

Study roles control access to various aspects of the study. To be part of the team for a given study, a person must have one or more study roles assigned. Available roles are:

- Principal Investigator - has full access to all aspects of the study.
- Research Assistant - has access to most aspects of the study.
- Data Scientist - has access to most aspects of the study, but no access to participants' personal information.
- Study Operator - is the person who adds the study to the health stack.

> The`Research Assistant`and `Data Scientist` study roles are not yet available in the current version (v0.9) of the Samsung Health Stack.

The table shows available features for each role.

<table>
  <tr>
    <th colspan="2" style="text-align: center; border-right: 1px solid black;">Features</th>
    <th colspan="4" style="text-align: center;">Roles</th>
  </tr>
  <tr>
    <th colspan="2" style="text-align: center;"></th>
    <th style="text-align: center;">Principal Investigator</th>
    <th style="text-align: center;">Research Assistant</th>
    <th style="text-align: center;">Data Scientist</th>
    <th style="text-align: center;">Study Operator</th>
  </tr>
  <tr>
    <td colspan="4"><b>Study Overview</b></td>
  </tr>
  <tr>
    <td></td>
    <td>Study Progress</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Participant Dropout</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Participant Enrollment</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Task Compliance</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Participant List</b></td>
  </tr>
  <tr>
    <td></td>
    <td>View Aggregated</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">De-identified</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>View Individual</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">De-identified</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>In-Lab Visit</b></td>
  </tr>
  <tr>
    <td></td>
    <td>View</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">No</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Edit</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">No</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Download</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">No</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Surveys</b></td>
  </tr>
  <tr>
    <td></td>
    <td>Create</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Edit</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>View</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Publish</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Activities</b></td>
  </tr>
  <tr>
    <td></td>
    <td>Create</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Edit</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>View</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Publish</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Educational Content</b></td>
  </tr>
  <tr>
    <td></td>
    <td>Create</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Edit</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>View</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Sensor Data Viewing</b></td>
  </tr>
  <tr>
    <td></td>
    <td>Avg Resting HR by Gender</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Avg Resting HR by Age</b></td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Data Queries</b></td>
  </tr>
  <tr>
    <td></td>
    <td>View</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">De-identified</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td></td>
    <td>Download</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">De-identified</td>
    <td style="text-align: center;">N/A</td>
  </tr>
  <tr>
    <td colspan="4"><b>Management Access</b></td>
  </tr>
  <tr>
    <td></td>
    <td>View Members</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">Yes</td>
  </tr>
  <tr>
    <td></td>
    <td>Edit Members</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">Yes</td>
  </tr>
  <tr>
    <td></td>
    <td>Delete Members</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">Yes</td>
  </tr>
</table>



<!-- Not until v1.0
  <tr>
    <td></td>
    <td>Grant Management Access</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">If study creator</td>
    <td style="text-align: center;">Yes</td>
  </tr>
  <tr>
    <td></td>
    <td>Invite New Members</td>
    <td style="text-align: center;">Yes</td>
    <td style="text-align: center;">If study creator or granted access</td>
    <td style="text-align: center;">If study creator or granted access</td>
    <td style="text-align: center;">Yes</td>
  </tr>
-->