---
title: "Internal Documentation Hub Design"
permalink: /samples/doc-hub/
layout: single
author_profile: false
---

**Summary**  
Developed a SharePoint- and Teams-based collaboration system that functions as a centralized documentation hub. Each Teams channel corresponds to a structured SharePoint folder, enabling real-time editing, SME collaboration, and transparent document lifecycle management.

---

### Purpose

- Solve fragmented access to documentation across Ops, Linux, and Windows teams
- Provide a flexible, version-controlled alternative to other documentation hosting locations
- Support real-time doc collaboration with SMEs
- Standardize folder layout and lifecycle visibility within each team

---

### System Overview

- Established Teams channels aligned to documentation type (e.g., “TechDocs – SOPs”), with room to scale as documentation needs expanded
- Each channel includes:
  - `Posts`: SME discussions and update logs
  - `Files`: SharePoint-hosted folder with edit control
  - `Notes`: Embedded OneNote (used for SME interview summaries)
- Future state add-ons: Planner cards for doc requests, Calendar sync for review cycles

<p align="center">
  <img src="{{ site.baseurl }}/assets/images/techdocs-folder-structure.png" alt="TechDocs Folder Structure" width="600">
</p>

---

### Technical Details

- SharePoint site: `TechDocs > Documents` acts as base
- Structured folders: `/AKS`, `/Silk`, `/Standards`, `/Validation Checklists`
- Naming conventions enforced via template rules
- SME feedback loop handled via @mentions + channel pins
- Documentation Tracker: SharePoint List with metadata such as owner, doc type, status, last updated
- PowerAutomate prototype triggered on metadata change to send review reminders and archive finalized docs (still under iteration)

---

### Naming & Metadata Guidelines

- File Naming Convention: `<Area> - <Title> - v<Version>.docx`  
  - Example: AKS - Access Troubleshooting Guide - v0.4.docx
- Optional Metadata Fields
  - `Owner` (Person/Team)
  - `Last Updated` (Date)
  - `Status` (Draft, Review, Final)
  - `Target Repository` (Wiki, ServiceNow, TBD)

---

### Repository Lifecycle

| Stage         | Description                                                        |
|---------------|--------------------------------------------------------------------|
| Drafting      | Initial document created, often by writer or SME collaboration     |
| Peer Review   | Reviewed by team members or adjacent SMEs for accuracy and clarity |
| Final Review  | Final approval by project owner, team lead, or ops approver        |
| Migration     | Moved to its final repository: Wiki, ServiceNow, or archive        |

---

### Your Role

- Designed the system architecture
- Coordinated permissions with internal IT
- Created SOPs and naming templates for folder structure
- Onboarded 5+ teams into usage (Windows, Linux, CLD Infra, ERA)
- Created visual guidance and walkthrough documentation

---

### Impact

- Enabled doc collaboration across previously siloed teams
- Created an always-on hub for SME-driven documentation development
- Replaced scattered email/Slack doc review requests with version-tracked comments
- Reduced documentation turnaround times by ~50% by transitioning from static SharePoint libraries to a live collaboration model

---

### Reflection

This project reinforced the importance of system design in documentation. By treating documentation as a collaborative process—not just a deliverable—we enabled sustainable knowledge sharing across previously siloed teams. The approach can scale to any environment where SharePoint restrictions, version control, and SME availability are common blockers.

