# Adaptive Detection Governance

Adaptive Detection Governance (ADG) is a vendor-neutral governance layer for continuously evaluating and improving the production quality of security signal across telemetry, parsing, detection logic, and alert-generation pathways.

This repository line treats ADG as a **functional specification**, not as a product launch, a single vendor feature, or a claim that no prior art exists. The problem space is real and already partially occupied by adjacent ideas such as Detection-as-Code, detection validation, Continuous Detection Engineering, and Gartner's Automated Security Control Assessment. What remains fragmented is the upstream governance layer that connects those efforts into one coherent capability model.

## What ADG Is

ADG defines what should exist before a SOC can claim it is governing detection quality seriously.

It starts from a simple observation:

- too much of the market is optimized for faster downstream investigation
- too little of the stack is governed upstream, where signal is actually produced

ADG exists to make that upstream layer explicit.

In practical terms, ADG concerns questions such as:

- Which telemetry should be sent to the SIEM at all?
- Are the required event types present and healthy?
- Are parsers extracting the fields detections depend on?
- Are rules still justified, effective, and contextually valid?
- Are investigation outcomes feeding back into tuning, validation, and retirement decisions?
- Does the organization maintain a portable knowledge base that survives changes in vendor tooling?

## What ADG Is Not

ADG is not:

- a replacement for SIEM, SOAR, EDR, or XDR platforms
- a claim that downstream triage and response no longer matter
- a synonym for Detection-as-Code
- a BAS product category
- a single vendor implementation
- a proprietary methodology locked to one stack

Instead, ADG defines the minimum capabilities a serious upstream detection-governance layer should cover, whether implemented through one platform, several tools, or a largely custom composition.

## Why It Matters Now

The operational problem is well documented:

- high false-positive rates
- alert fatigue
- analyst burnout
- investigation overload
- growing economic pressure around storage, inference, and token consumption

The standard market response has been to optimize downstream work:

- triage faster
- enrich faster
- investigate faster
- respond faster

Those improvements matter, but they still assume the alert stream is a given. ADG challenges that assumption. It asks whether the organization is governing the system that produces alerts before spending human or AI effort investigating them.

AI makes this newly practical. Historically, continuously governing telemetry quality, parser health, rule effectiveness, and contextual validity was too expensive for most organizations. Agents and machine-assisted workflows make that layer more economically realistic, but the layer itself should be defined independently of any one AI product or vendor narrative.

## Minimum Mental Model

ADG sits across the boundary between telemetry, detection, and downstream response.

Conceptually:

1. Telemetry and data sources produce potential security signal.
2. Parsers and schemas translate that signal into structured fields.
3. Detection logic decides what becomes an alert.
4. Investigation outcomes reveal whether the signal production system is healthy.
5. ADG closes the loop by governing the quality of that full pathway.

This is why ADG is broader than rule tuning alone. It includes:

- source-layer governance
- parser-layer governance
- rule lifecycle governance
- feedback-loop governance
- external architectural knowledge
- observability and portability

## Files In This Line

- [ADG-Definition.md](ADG-Definition.md): short canonical definition
- [ADG-Functional-Spec-v0.1.md](ADG-Functional-Spec-v0.1.md): the full functional specification
- [ADG-Self-Assessment.md](ADG-Self-Assessment.md): practical evaluation checklist
- [ADG-References.md](ADG-References.md): source register and research anchors
- Foundational essay: *Before Triage: Adaptive Detection Governance as the Upstream Layer Security Operations Is Missing* — published on Medium

## Citation

If you reference ADG in writing, use the Zenodo DOI:

```
Romero Lara, Gerardo Eliud. Adaptive Detection Governance (ADG). Version 0.1. Zenodo, 2026. https://doi.org/10.5281/zenodo.20371975
```

## Current Positioning

The strongest defensible claim for ADG is not that it invented all upstream detection-quality work. It is that ADG names, specifies, and consolidates a fragmented upstream governance layer into a vendor-neutral capability framework.

That is the contribution this line is meant to make.
