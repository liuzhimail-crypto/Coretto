# KIR-Lite v1.1

KIR-Lite means **Knowledge Intermediate Representation — Lite version**.
It is the first structured intermediate representation designed for the local 14B model to emit directly.

## Design goals

KIR-Lite v1.1 is designed to be:

- short enough for a local 14B model to output stably,
- structured enough for cloud handoff,
- explicit enough to preserve constraints and anomalies,
- open enough to support future evolution.

## JSON schema

```json
{
  "task_core": "",
  "key_params": [],
  "static_constraints": [],
  "dynamic_constraints": [],
  "mechanisms": [],
  "must_keep": [],
  "open_exit": [],
  "capacity_guard": {
    "status": "safe | borderline | overflow",
    "reasons": [],
    "recommended_scope": "",
    "crop_commands": []
  },
  "cloud_handoff": {
    "compressed_context": "",
    "cloud_question": "",
    "cloud_focus": []
  },
  "cloud_audit": {
    "required": false,
    "audit_goal": "",
    "audit_checks": []
  }
}
```

## Field definitions

### `task_core`
One sentence stating what problem the background is actually serving.

### `key_params`
Only parameters that can change the answer or decision process.

Each item:

```json
{"name": "", "value": "", "type": "descriptive|control|evaluative|critical", "why": ""}
```

Parameter types:

- `descriptive` — describes system state
- `control` — controllable or configurable
- `evaluative` — used for judging quality or success
- `critical` — threshold-like, decisive, or branch-changing

### `static_constraints`
Permanent assumptions, hard rules, fixed principles, lasting limits.

### `dynamic_constraints`
Conditional rules or state-dependent transitions.
Prefer forms like:

> 当……时，……必须/会……

### `mechanisms`
Decisive causal, dependency, tradeoff, or trigger relations.

Each item:

```json
{"if": "", "then": ""}
```

### `must_keep`
Raw or near-raw anchors that must not be abstracted away.
Examples:

- numbers,
- thresholds,
- negations,
- definitions,
- exact constitutional wording,
- critical phrasing.

### `open_exit`
High-value items that do not safely fit the current schema.

Each item:

```json
{"description": "", "why_high_value": ""}
```

### `capacity_guard`
The model's self-judgment of whether it is still operating inside a trustworthy range.

Fields:

- `status` — `safe | borderline | overflow`
- `reasons` — why this judgment was made
- `recommended_scope` — safest current scope of local work
- `crop_commands` — suggested cropping / chunking / decomposition actions

### `cloud_handoff`
Compact material passed upward for cloud solving.

- `compressed_context` — dense reasoning-ready context
- `cloud_question` — what the cloud should solve
- `cloud_focus` — specific things the cloud should pay attention to

### `cloud_audit`
Whether cloud should first audit the structure before solving.

- `required`
- `audit_goal`
- `audit_checks`

## Recommended output discipline

- `task_core`: 1 sentence
- `key_params`: up to 8 items
- `static_constraints`: up to 8 items
- `dynamic_constraints`: up to 8 items
- `mechanisms`: up to 6 items
- `must_keep`: up to 6 items
- `open_exit`: up to 4 items
- `capacity_guard.reasons`: up to 6 items
- `capacity_guard.crop_commands`: up to 6 items
- `cloud_handoff.cloud_focus`: up to 6 items
- `cloud_audit.audit_checks`: up to 7 items

## Why this schema is important

KIR-Lite v1.1 does three jobs at once:

1. captures the **main structured core**,
2. preserves **high-value unmodeled residuals**,
3. records **local confidence boundary state** and **audit needs**.

That is what makes it both operational and evolvable.
