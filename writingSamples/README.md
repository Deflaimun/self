# Writing Samples

These are samples of documentation I authored at Redpanda (2025-2026). The source files are written in AsciiDoc for [Antora](https://antora.org/), a docs-as-code static site generator. This means the raw source includes Antora-specific markup like conditional directives (`ifdef`/`ifndef`), partial includes, and cross-references that won't render on GitHub.

**To see the polished output, use the published links below.** The source files are included here to show the docs-as-code engineering behind the content: multi-product conditional builds, reusable partials, and structured authoring at scale.

---

## Disaster Recovery / Shadowing

I authored this documentation set almost entirely solo (95%), collaborating directly with engineering on design reviews, PRDs, and RFCs before writing the full user-facing guide. It covers Redpanda's enterprise disaster recovery feature for cross-region cluster replication.

| Source file | Published page |
|---|---|
| [overview.adoc](shadowing/overview.adoc) | [Shadowing Overview](https://docs.redpanda.com/current/manage/disaster-recovery/shadowing/) |
| [setup.adoc](shadowing/setup.adoc) | [Configure Shadowing](https://docs.redpanda.com/current/manage/disaster-recovery/shadowing/setup/) |
| [monitor.adoc](shadowing/monitor.adoc) | [Monitor Shadowing](https://docs.redpanda.com/current/manage/disaster-recovery/shadowing/monitor/) |
| [failover.adoc](shadowing/failover.adoc) | [Failover](https://docs.redpanda.com/current/manage/disaster-recovery/shadowing/failover/) |
| [failover-runbook.adoc](shadowing/failover-runbook.adoc) | [Failover Runbook](https://docs.redpanda.com/current/manage/disaster-recovery/shadowing/failover-runbook/) |

---

## Group-Based Access Control (GBAC)

I wrote the GBAC documentation from scratch for a new security feature. This involved designing the information architecture, writing the main guide, and creating reusable partials for Redpanda Console UI procedures that are included across both self-managed and cloud docs.

| Source file | Published page |
|---|---|
| [gbac-dp.adoc](security/gbac-dp.adoc) | Main GBAC guide (content partial, included into the published page) |
| [gbac.adoc](security/gbac.adoc) | [Configure GBAC](https://docs.redpanda.com/current/manage/security/authorization/gbac/) |
| [gbac-assign-group-role.adoc](security/gbac-assign-group-role.adoc) | Reusable partial: Console UI steps for assigning groups to roles |
| [gbac-create-group-acl.adoc](security/gbac-create-group-acl.adoc) | Reusable partial: Console UI steps for creating group-based ACLs |

---

## About the source format

If you're reviewing the `.adoc` files directly, here's what the Antora-specific markup means:

- **`ifdef::env-cloud[]` / `ifndef::env-cloud[]`** — Conditional blocks that show or hide content depending on whether the page is built for Redpanda Cloud or self-managed deployments. A single source file produces different output for each product.
- **`include::manage:partial$...`** — Pulls in reusable content from shared partials, avoiding duplication across pages.
- **`xref:manage:...`** — Cross-references to other pages in the documentation site that resolve into proper links at build time.
- **`// tag::single-source[]`** — Tagged regions that allow other pages to include specific sections of a file.
