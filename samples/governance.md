---
title: "Governance Docs"
permalink: /samples/governance/
layout: single
author_profile: true
author: davidcrawford
---

# Document: Naming & slugs

## Purpose
Standardize page titles and slugs so content is easy to scan, sort, and search.

## General rules

- Use sentence-style capitalization
- Use the **object - artifact** type pattern (for example, “Azure Virtual Desktop - Platform profile”).
- Keep titles concise; omit status, owner and dates; those live in page properties and labels.
- Slugs: lowercase, hyphen-separated, no spaces/special characters, keep short and stable.

## Title patterns

- **Application profile** - {App name} - Application profile
  - Example: Epic Hyperspace - Application profile
- **Platform profile** - {Platform name} - Platform profile
  - Example: Azure Virtual Desktop - Platform profile
- **Logical design** - Logical design - {project name} - {scope}
  - Example: Logical design - AVD kiosk rollout - Infrastructure
- **ADR** - ADR - {scope} - {short decision}
  - Example: ADR - AVD - Standardize SSO with Azure AD (SAML)
- **SOP** - SOP - {action} - {system}
  - Example: SOP - Rotate SSL certificate - AVD
- **Runbook** - Runbook - {trigger/event} - {service}
  - Example: Runbook - Certificate-expiry alert - AVD
- **Interface record** - Interface - {from system} → {to system} - {purpose}
  - Example: Interface - Epic → OnBase - Discharge summaries
- **DR evidence** - DR evidence - {application} - {test type} - {test date}
  - Example: DR evidence - Epic Hyperspace - Tabletop - 2025-10-21

## Slug patterns

| **Artifact**        | **Slug pattern**                                 | **Example**                              |
| ------------------- | ------------------------------------------------ | ---------------------------------------- |
| Application profile | `app-{slug}`                                     | `app-epic-hyperspace`                    |
| Platform profile    | `platform-{name}`                                | `platform-avd`                           |
| Logical design      | `logical-design-{project-slug}`                  | `logical-design-avd-kiosk-rollout`       |
| ADR                 | `adr-{scope-slug}-{decision-slug}`               | `adr-avd-standardize-sso-azuread-saml`   |
| SOP                 | `sop-{action-slug}-{system-slug}`                | `sop-rotate-ssl-certificate-avd`         |
| Runbook             | `runbook-{event-slug}-{service-slug}`            | `runbook-certificate-expiry-alert-avd`   |
| Interface record    | `interface-{from-slug}-to-{to-slug}`             | `interface-epic-to-onbase`               |
| DR evidence         | `dr-{app-slug}-{testtype-slug}-{yyyy}-{mm}-{dd}` | `dr-epic-hyperspace-tabletop-2025-10-21` |

---

# Document: Labels & metadata

## Purpose
Create consistent labels that are queryable so catalogs and reports always return the right pages with the assigned columns.

## Scope
Create consistent labels that are queryable so catalogs and reports always return the right pages with the assigned columns.

## Formatting

- Lowercase.
- No spaces.
- Prefer `key=value` for filterable attributes.
- Keep values short and reuse existing values.
- Apply labels via templates; do not remove required labels.
- Update values as needed after publishing.

## Keys and allowed values

| **Key**    | **Allowed values**                                                                                        | **Notes**               |
| ---------- | --------------------------------------------------------------------------------------------------------- | ----------------------- |
| `type`     | `app-profile`, `platform-profile`, `logical-design`, `adr`, `sop`, `dr-evidence`, `interface` , `runbook` |                         |
| `domain`   | `application`, `infrastructure`, `network`, `operations`, `security`                                      |                         |
| `status`   | `draft`, `review`, `published`, `archived`                                                                |                         |
| `tier`     | `1`, `2`, `3`                                                                                             | Optional; for profiles. |
| `app`      | `{slug}`                                                                                                  | Application slug.       |
| `platform` | `{name}`                                                                                                  | Short platform name.    |

## Required labels by template

| **Artifact**           | **Required labels**                                                                 |
| ---------------------- | ----------------------------------------------------------------------------------- |
| Application profile    | `type=app-profile`, `domain=application`, `status=draft`, `app={slug}`              |
| Platform profile       | `type=platform-profile`, `domain=infrastructure`, `status=draft`, `platform={name}` |
| Logical design         | `type=logical-design`, `domain={scope}`, `status=draft`                             |
| ADR                    | `type=adr`, `domain={scope}`, `status=draft`                                        |
| SOP (procedure)        | `type=sop`, `domain=operations`, `status=draft`                                     |
| Runbook (event-driven) | `type=runbook`, `domain=operations`, `status=draft`                                 |
| Interface record       | `type=interface`, `domain={scope}`, `status=draft`                                  |
| DR evidence            | `type=dr-evidence`, `domain=operations`, `status=draft`, `app={slug}`               |

## Lifecycle (status=) usage

New pages start as `status=draft`.

Update to `status=review` when ready for review.

Update to `status=published` to finalize.

Use `status=archived` for retired content.