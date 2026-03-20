---
title: "Respond to Rubrik Backup Alerts"
permalink: /samples/Rubrik-runbook/
layout: single
classes: 
    wide
    dark-theme
author_profile: true
author: davidcrawford
---

Owner (accountable group): SNOW – Architects

Last reviewed: January 26, 2026

Next review: January 26, 2027

## Purpose
Use this runbook to respond to Rubrik backup exceptions by capturing evidence, classifying scope, routing to the correct owner, and validating recovery.

Redaction note: redacted internal URLs, hostnames, object names, distribution group addresses, ticket IDs, and personnel names.

## Scope
In scope:
- Coverage and retention reference
- Monitoring model
- Evidence capture
- Exception triage
- Escalation for shared dependencies (for example, vCenter)
- Work-item creation for role-aware handling

Out of scope:
- Changing retention or protection policies during response (route through change control)
- Designing or implementing replication/DR
- Performing platform or server changes (unless you are the designated execution owner)

## Prerequisites

- Access to the Rubrik console (or alert detail view)
- Access to the Architecture team alert intake (distribution group / equivalent mechanism)
- Access to the local record system (incident/ticket and change/task work items)

## Coverage and storage

- Rubrik protects all VMs in the data centers and Microsoft 365 tenant data.
- Backups are stored locally on disk.
- Cloud replication of backup datasets is planned (not configured as of last review).
- Storage-system replication between data centers is planned. Off-site replication of Rubrik backups is not configured.

## Schedule and retention

| **Take every**                                | **Retain for** |
| --------------------------------------------- | -------------- |
| **12 hours**                                  | 30 days        |
| **Daily**                                     | 14 days        |
| **Monthly (last day)**                        | 12 months      |
| **Yearly (last day; year begins in January)** | 1 year         |

## Operations and monitoring

- Rubrik includes new VMs automatically by policy through vCenter.
- In limited cases (for example, domain controllers and file servers), install the Rubrik agent so Rubrik recognizes and handles the server correctly.
- Rubrik generates error alerts and sends them to the Architecture team distribution group. Respond to exceptions as needed.
- No regular maintenance or manual checks are required.

## Trigger
Run this procedure when you receive a Rubrik error alert or when someone reports a workload as unprotected.

### Triage decision guide

- Single workload failing → follow “Single workload” path (Step 4).
- Many workloads failing or clustered failure window → follow “Shared dependency” path (Step 5).
- Domain controller/file server or role-recognition indicators → follow “Role-aware handling” path (Step 6).
- If large-scope or cross-site impact is observed, treat as higher severity per local incident process.

## What to capture for every event

- Capture these items in the incident/ticket record:
- Record ID, time received, and reporter (if applicable)
- Affected object/workload, site, and environment (if applicable)
- Protection policy or SLA domain shown in the platform (or “not assigned”)
- Last successful run time, first failure time, latest failure time, and exact error text
- Job/run identifier (if available)
- Scope summary: number of objects impacted and whether failures are ongoing
- Actions taken with timestamps and current owner of the next action
- Evidence links/attachments (screenshots or log excerpts)

## Guardrails

- Do not change retention schedules or protection policies during incident response; route changes through change control.
- Do not install agents or change servers unless you are the designated execution owner.
- If an alert appears security-related, capture minimal evidence per policy and route to the security owner.

## Procedure

1. Create or update the incident/ticket record.

    1\.1 Create or open the incident/ticket.

    1\.2 Record the time received and start a timeline.

    1\.3 Link the alert identifier (or reporter reference) to the record.
2. Capture initial evidence

    2\.1 Open the affected workload in the Rubrik console (or the alert detail view).

    2\.2 Capture the policy/SLA domain, last successful time, failure time, and exact error text.

    2\.3 Capture the job/run identifier and any diagnostic fields shown in the alert.

    2\.4 Record the scope summary (how many objects, when failures started, and whether they continue).
3. Classify the scope
    - If one workload (or a small set) is failing, go to Step 4.
    - If many workloads are failing, or failures cluster in the same time window, go to Step 5.
4. Triage a single workload (small scope)

    4\.1 Confirm the workload is protected and capture the policy/SLA domain shown.
     - If the workload is not assigned, create a change-control work item for the policy owner, attach evidence, and record the handoff owner/status in the incident/ticket.

    4\.2 Check for role-aware handling indicators.
    - If the workload is a domain controller or file server (or the error indicates role recognition issues), go to Step 6.

    4\.3 Check for shared dependency indicators.
    - If the error indicates vCenter connectivity/authentication/permission issues, go to Step 5.

    4\.4 If remediation requires changes outside your authorization, route to the appropriate execution owner with the evidence package and update the incident/ticket.
5. Triage a shared dependency (large scope)
    
    5\.1 Determine whether the impact is site-specific or cross-site.

    5\.2 Summarize impact for escalation: number of objects, failure window, representative affected workloads, and exact error text.

    5\.3 Escalate to the dependency owner (for example, the vCenter owner) and attach the evidence package.

    5\.4 After the owner reports a fix, validate recovery: confirm at least one previously failing workload completes a successful protection cycle and the alert state transitions out of error.

    5\.5 Update the incident/ticket with escalation details, remediation owner, reported remediation, and validation evidence.
6. Create a work item for role-aware handling (handoff)

    6\.1 Record why role-aware handling is required (for example, domain controller or file server).

    6\.2 Confirm baseline coverage at the VM level and capture evidence of the current state.

    6\.3 Create an implementation work item for the execution owner including: workload name, site, OS and role, maintenance window, approvals, requested action (install/configure Rubrik agent), and validation criteria.

    6\.4 After implementation, validate that Rubrik recognizes the workload correctly and that at least one successful protection cycle completes. Attach evidence and close the incident/ticket or transition it to monitoring per local process.

## End condition
Close the event when protection succeeds again and the alert clears, or when you route the issue to the accountable owner with a complete evidence package that enables execution without re-interviewing you.

## References
- Approved internal KB for Rubrik backups: coverage, schedule, retention, and monitoring model.
- Local ownership and escalation paths (for example, vCenter ownership).
- Local recordkeeping and change-control standards.