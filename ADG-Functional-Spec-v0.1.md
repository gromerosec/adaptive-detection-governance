# Adaptive Detection Governance

## A Vendor-Neutral Functional Specification for Detection Quality

Version: `v0.1`  
Author: `Gerardo Eliud Romero Lira`  
Status: `Foundational draft`

## Abstract

This document proposes Adaptive Detection Governance (ADG) as a vendor-neutral governance layer for continuously evaluating and improving the production quality of security signal before downstream investigation and response. ADG is not a product category claim, a proprietary methodology, or a synonym for any single vendor offering. It is a functional specification describing what should exist if an organization intends to govern telemetry, parsing, detection logic, and alert-generation quality in a coherent upstream way.

The market already contains adjacent fragments: Detection-as-Code, detection validation, Continuous Detection Engineering, Automated Security Control Assessment, behavior maturity models, and data-pipeline governance. What remains insufficiently defined is the cross-cutting layer that governs the full path from telemetry inputs to alert outcomes under one portable capability model.

This specification defines that layer and its minimum domains.

## 1. Problem Statement

The operational problem is not controversial:

- SOCs process too many alerts
- false positives remain costly
- analyst burnout remains high
- downstream AI triage still consumes budget, inference, and attention
- detection quality is frequently under-owned, under-measured, and under-governed

The dominant market response has been downstream acceleration: triage faster, enrich faster, investigate faster, respond faster. Those capabilities matter, but they do not govern the system that produces the alert stream in the first place.

ADG starts from a different premise:

> Before automating alert investigation at scale, organizations need an upstream governance layer that continuously evaluates whether their telemetry, parsers, rules, and context pathways are producing signal worth investigating.

## 2. Position in the Architecture

For simplification, SecOps architectures can be viewed across three broad layers:

1. Telemetry and data sources
2. Detection and analytics platforms
3. Investigation, orchestration, and response

ADG is not identical to any of those layers. It is a governance layer that operates across them, with primary focus on the boundary between telemetry and detection, while closing a feedback loop from downstream outcomes back into upstream decisions.

This means ADG should influence:

- what data enters detection systems
- how that data is parsed and normalized
- what rule logic is allowed to continue generating alerts
- what contextual knowledge is required to interpret rule quality
- how investigation outcomes reshape future detection behavior

## 3. What ADG Is Not

ADG is not:

- a SIEM
- a SOAR
- an AI SOC product
- Detection-as-Code alone
- BAS or attack emulation alone
- a generic control-assessment program

Detection-as-Code is an implementation substrate. BAS and validation tools test subsets of the path. Downstream AI products consume alerts. ADG defines the governance layer that judges whether those components, together, are producing healthy security signal.

## 4. Minimum Functional Domains

An implementation should not claim ADG alignment unless it substantially covers the following domains.

### A. Vendor neutrality

The layer must remain portable across SIEM, XDR, and security-data environments.

Minimum expectations:

- maintain detection governance logic without hard dependency on one downstream vendor
- preserve knowledge and decision history if the organization changes analytics platform
- support cross-tool evaluation and composition instead of one-product lock-in

Why it matters:
without neutrality, the governance layer collapses into product branding.

### B. Source-layer governance

ADG must govern what enters the detection pipeline, not only what rules do after ingestion.

Minimum expectations:

- inventory active sources and detect silent sources
- validate whether required event types are present
- identify structurally noisy telemetry at the source layer
- support routing decisions such as full ingest, filtering, sampling, or cold-storage treatment
- make those decisions traceable and reviewable

Why it matters:
the alert problem often starts before the rule.

### C. Parser-layer governance

ADG must treat parsers as first-class detection dependencies.

Minimum expectations:

- inventory parser dependencies by source
- validate that critical fields are extracted correctly
- detect parser drift and schema mismatch
- map parser failures to the rules they impact
- preserve change traceability for parser updates

Why it matters:
good rules fail silently behind weak parsing.

### D. Rule lifecycle governance

ADG must govern the ongoing life of detection logic, not only its initial creation.

Minimum expectations:

- each rule has an owner
- each rule has a documented purpose or threat model
- each rule has version history
- each rule has health indicators such as volume, dormancy, change age, and tuning history
- duplicate or overlapping rules are detectable
- rules can be reviewed, tuned, retired, or re-validated with evidence

Why it matters:
most detection environments degrade through unmanaged accumulation.

### E. Adaptive feedback loop

This is the core of the word adaptive.

Minimum expectations:

- alerts remain traceable to source rule and source pathway
- investigation outcomes feed back into rule quality decisions
- the system distinguishes structural rule defects from contextual false positives
- source and parser issues can be surfaced as root causes, not only rule issues
- the loop supports recommendation, review, and where appropriate automation with accountability

Why it matters:
without feedback, governance becomes static review instead of adaptive control.

### F. Architectural knowledge base

ADG should rely on a portable architectural knowledge base that is not governed by the downstream detection vendor.

Minimum expectations:

- maintain asset criticality, ownership, and business context outside the SIEM
- retain relationships among systems, identities, and business units
- make that knowledge queryable by governance workflows and, where used, agents
- preserve portability across platform changes
- keep the knowledge base auditable and versioned

Why it matters:
critical context trapped inside vendor-specific enrichment is expensive, fragile, and hard to govern across environments.

### G. Agentic operations

AI is not required to define ADG, but it is increasingly what makes ADG scalable.

Minimum expectations when agents are used:

- actions are auditable and reversible
- approval modes are explicit
- decision rationale is evidence-linked
- safety boundaries exist for high-risk actions
- agent behavior depends on portable governance knowledge, not opaque vendor-only state

Why it matters:
agents can make ADG economically realistic, but they must not make it ungovernable.

### H. Metrics and observability

ADG must be measurable.

Minimum expectations:

- coverage metrics
- rule health metrics
- source health metrics
- feedback-loop latency and action metrics
- governance completeness metrics such as ownership and documentation coverage
- historical decision records

Why it matters:
what is not measured cannot be governed responsibly.

### I. Portability and degraded mode

ADG should be composable even without a single integrated vendor platform.

Minimum expectations:

- the framework can be implemented through multiple tools
- the framework can be partially implemented with internal scripts and repositories
- governance state survives migrations
- detection logic and governance artifacts remain exportable

Why it matters:
the specification must remain usable for real enterprises with mixed stacks, uneven budgets, and changing vendor strategies.

## 5. Relationship to Adjacent Efforts

ADG does not deny adjacent work. It sits beside and above multiple existing practices:

- Detection-as-Code provides versioned detection artifacts
- detection validation tools test whether detections work
- BAS platforms simulate adversarial behavior
- ASCA and posture products assess portions of control effectiveness
- data-pipeline platforms influence what reaches the SIEM

What ADG adds is the requirement that those pieces be governable as one upstream capability layer, with explicit expectations for neutrality, feedback, portability, and architectural knowledge.

## 6. Why the External Knowledge Base Matters

One of the most distinctive requirements in this specification is the architectural knowledge base.

NIST already requires asset prioritization and critical-asset awareness. CMDBs and CAASM-like efforts have addressed visibility, but usually with IT-centric semantics, limited portability, or coupling to platform-specific enrichment. ADG treats this context as a governance asset for detection quality itself.

That means the layer needs access to:

- asset criticality
- identity and privilege context
- system dependencies
- business-unit and regulatory context
- known operational patterns

without making that knowledge permanently subordinate to one SIEM vendor's enrichment model.

## 7. Self-Assessment Use

Organizations can use ADG in three ways:

1. Evaluate whether their stack already covers the layer
2. Compare vendors against a neutral set of requirements
3. Design a compositional roadmap using multiple tools and internal automation

The checklist in `ADG-Self-Assessment.md` is intended as the practical companion to this document.

## 8. Explicit Non-Claims

This document does not claim:

- that ADG is the first ever upstream detection-quality idea
- that no vendors are addressing parts of this space
- that every organization needs the same implementation path
- that downstream AI triage has no value

It does claim that:

- the upstream governance space remains fragmented
- organizations need a capability definition independent of vendor names
- a portable governance layer is increasingly necessary as telemetry volume, context complexity, and AI consumption costs rise

## 9. Conclusion

Adaptive Detection Governance is best understood as a reference layer and capability framework.

It exists because detection quality is not governed by one artifact alone. It emerges from the interaction of telemetry, parsing, detection logic, context, and feedback. Where those interactions remain fragmented, organizations experience the same familiar outcomes: noisy detections, slow tuning, brittle context, and downstream overload.

ADG proposes that this should be governed explicitly, continuously, and in a vendor-neutral way.
