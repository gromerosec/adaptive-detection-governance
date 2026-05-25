# ADG Self-Assessment

Use this checklist to evaluate whether your current stack meaningfully covers the Adaptive Detection Governance layer.

Scoring labels:

- `Yes`: implemented and repeatable
- `Partial`: exists but inconsistently, manually, or only in one stack segment
- `No`: not meaningfully implemented

## Core Questions

| Domain | Question | Yes / Partial / No |
| --- | --- | --- |
| Vendor neutrality | Could we change SIEMs without losing our governance state, rule history, and architectural context? | |
| Source governance | Do we know which required log sources are silent, degraded, or structurally noisy today? | |
| Source governance | Do we maintain explicit reasons for what is not ingested, filtered, or sampled? | |
| Parser governance | Do we validate that parsers extract the fields our detections depend on? | |
| Parser governance | Can we identify which rules are affected when a parser drifts or fails? | |
| Rule lifecycle | Does every rule have an owner, purpose, and reviewable change history? | |
| Rule lifecycle | Do we track dormant, duplicate, or consistently noisy rules? | |
| Feedback loop | Do investigation outcomes feed back into rule, parser, or source decisions? | |
| Feedback loop | Do we distinguish structural rule problems from contextual false positives? | |
| Architectural knowledge | Does asset criticality live outside the SIEM in a portable knowledge source? | |
| Architectural knowledge | Can governance workflows query business, identity, and system context without depending on one vendor model? | |
| Agentic safety | If agents propose or make changes, are those actions auditable, bounded, and reversible? | |
| Metrics | Do we report rule health, source health, and governance completeness metrics? | |
| Portability | Can we preserve ADG state if we swap or add downstream detection platforms? | |

## Interpreting Results

### Strong ADG posture

Most answers are `Yes`, especially across:

- source governance
- parser governance
- rule lifecycle
- feedback loop
- architectural knowledge

### Transitional posture

Many answers are `Partial`.

This usually means:

- the capability exists in fragments
- one vendor covers one piece
- internal scripting covers another
- there is no stable layer owner yet

### Weak posture

Most answers are `No`.

This usually means the organization is still relying on downstream investigation and platform-local workarounds to compensate for upstream governance gaps.

## Recommended Next Step

If your posture is mostly `Partial` or `No`, do not start by buying a new category claim. Start by mapping your current stack to the ADG domains and identifying which one or two domains create the most downstream cost today.
