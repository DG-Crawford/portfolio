---
title: "Release Task Template Strategy"
permalink: /samples/rtsk-strategy/
layout: single
author_profile: true
author: davidcrawford
---

## Release Task Template Strategy

**Overview**  
This document provides an overview of the release task (RTSK) templates used in our organization for managing and executing release tasks. Release task templates streamline the release process, ensuring consistent communication and efficient coordination between teams.
  
Release task templates are predefined instructions and checklists that outline the steps required to complete specific release tasks. They serve several purposes:  
• Standardization: Ensure that all tasks are executed consistently, following best practices.  
• Efficiency: Save time by providing ready-to-use task instructions and reducing the need for ad-hoc communication.  
• Quality Assurance: Improve the quality and reliability of releases by ensuring all necessary steps and checks are performed.  
• Documentation: Maintain a record of the procedures and configurations applied during the release process.

---

## Releases Overview

Releases refers to a collection of changes, such as new features, fixes, or configurations, that are planned and implemented together. Releases consist of multiple change requests or release tasks that contribute to the larger deployment effort. The workflow from release creation to release task completion looks like this:  
1. Initial planning and requirements receive approval from the Architecture Review Board (ARB). This meeting includes assessing feasibility, technical decisions, adherence, potential risks, and other considerations from the project team.  
2. Once the ARB approves the project, the focus shifts to release planning and organizing how the objective should move to production.  
3. The release establishes the preparing, testing, and deploying requirements for production.  
4. Release tasks are created as actionable items assigned to various teams or individuals to ensure the release completes smoothly.  
5. Release task templates, as defined in this article, aid in completing the release tasks.

---

## Release Task Templates

Infrastructure requests are generated through releases following the ARB approval and architecture design. The cloud coordinator generates the release specific to the request for the engineering team to configure and deploy infrastructure, including associated release tasks in a sequential order according to the build process.  
1. Assigned RTSKs include detailed instructions related to the request. Below is an example of an RTSK used to build and configure a Windows virtual machine in Azure with SQL.  
2. The description references details, including the build sheet, infrastructure specifications, requests from the application owner, links to related Wiki articles, and instructions on closing the ticket.  
    1. Some build requests include multiple steps with an RTSK assigned respectively.  
    2. When builds require handoff to another team, the RTSK instructs the user to close that ticket and assign the next ticket to the respective team.  
        1. You may need to attach the updated build sheet to the subsequent ticket.  
3. If the RTSK does not have a linked Wiki documentation for reference, email [REDACTED EMAIL].  
4. The final RTSK to a build request instructs the user to contact the Cloud Infrastructure Coordinator and Stakeholders identified on the build sheet.  
5. An infrastructure build is not complete until all tasks associated with the request, outlined in the release, have been completed.