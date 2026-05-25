# Adaptive Detection Governance (ADG) Definition

## Canonical Definition

Adaptive Detection Governance (ADG) is a vendor-neutral governance layer for continuously evaluating and improving the production quality of security signal across telemetry, parsing, detection logic, and alert-generation pathways.

## Short Definition

ADG is the upstream layer that governs whether security alerts deserve to exist before downstream teams and automation spend effort investigating them.

## Primary Thesis

The future of AI in the SOC is not better investigations. It is fewer unnecessary investigations.

## Core Position

ADG is:

- upstream of alert triage
- broader than rule tuning alone
- grounded in governance, not only optimization
- portable across vendors and architectures
- increasingly practical because AI can scale functions that were historically too expensive to run continuously

## What ADG Covers

At a minimum, ADG governs:

- telemetry selection and routing
- parser health and schema fidelity
- rule lifecycle and rule quality
- feedback loops from outcomes back into detections
- the architectural knowledge required to judge detection quality in business context

## What ADG Does Not Claim

ADG does not claim:

- that no prior art exists
- that downstream AI SOC work is useless
- that one product already or uniquely embodies the full layer
- that the framework must be implemented by one vendor

## Defensible Originality Claim

ADG formalizes and consolidates a fragmented upstream space into a vendor-neutral capability framework that organizations can use to evaluate their current stack, compare vendor claims, and design a more governable detection pipeline.
