# Project Documentation Pack

This repository package summarizes the design discussion for a **local-first hybrid LLM information compiler** project.

The core idea is not to build a narrow token router, but an **evolvable wide-area information service system**:

- a local 14B model acts as the first intelligence layer,
- extracts and compresses high-value information,
- preserves an explicit escape hatch for out-of-schema high-value items,
- and hands off compact, reasoning-ready context to a cloud model when stronger interpretation or reasoning is needed.

## What is in this pack

- [`docs/01_overview_and_vision.md`](docs/01_overview_and_vision.md) — project vision and system identity
- [`docs/02_design_principles.md`](docs/02_design_principles.md) — core design principles established in the discussion
- [`docs/03_constitution.md`](docs/03_constitution.md) — constitutional definitions and operating laws
- [`docs/04_architecture.md`](docs/04_architecture.md) — architecture and processing chain
- [`docs/05_kir_lite_v1_1.md`](docs/05_kir_lite_v1_1.md) — KIR-Lite v1.1 schema and field definitions
- [`docs/06_local_system_prompt_cn.md`](docs/06_local_system_prompt_cn.md) — Chinese working version of the local 14B system prompt
- [`docs/07_cloud_audit_prompt.md`](docs/07_cloud_audit_prompt.md) — cloud constitutional audit prompt
- [`docs/08_workflows_and_operating_modes.md`](docs/08_workflows_and_operating_modes.md) — normal mode, overflow mode, audit mode
- [`docs/09_naming_and_positioning.md`](docs/09_naming_and_positioning.md) — naming, positioning, and slogan candidates
- [`docs/10_decision_log.md`](docs/10_decision_log.md) — distilled decision log and open issues

## System identity in one sentence

> Preserve decision-relevant information with minimal loss, route only what truly needs cloud reasoning, and keep every high-value anomaly alive until it can be understood.

## Core project stance

This system is **LLM-first**, not module-first.

That means:

- if the local LLM can solve something by understanding, structuring, compressing, self-evaluating, or reformulating, do not prematurely create an extra code component,
- but when a high-value item cannot be safely expressed in the current schema, do not force it into the template — preserve it and pass it upward.

## Recommended repository structure

```text
.
├── README.md
└── docs/
    ├── 01_overview_and_vision.md
    ├── 02_design_principles.md
    ├── 03_constitution.md
    ├── 04_architecture.md
    ├── 05_kir_lite_v1_1.md
    ├── 06_local_system_prompt_cn.md
    ├── 07_cloud_audit_prompt.md
    ├── 08_workflows_and_operating_modes.md
    ├── 09_naming_and_positioning.md
    └── 10_decision_log.md
```

## Current maturity level

This pack captures the **conceptual constitution + prompt-level implementation layer**.
It does **not** yet define:

- benchmark datasets,
- training objectives and loss design,
- fine-tuning recipes,
- GitHub code scaffolding,
- evaluation dashboards,
- cloud solver prompts beyond audit mode.

Those are natural next steps after validating the representation and prompt behavior on real materials.
