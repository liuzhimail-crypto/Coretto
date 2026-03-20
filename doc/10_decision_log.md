# Decision Log

This file condenses the major decisions made during the discussion.

## Confirmed decisions

### 1. The project is larger than token routing
The system is framed as an **evolvable wide-area information service system**, not merely a router.

### 2. The local 14B model is the primary intelligence front-end
It is responsible for:

- task decomposition,
- local information extraction,
- compression,
- structural representation,
- residual preservation,
- capacity awareness.

### 3. LLM-first is a hard design principle
If the LLM can solve the problem through understanding, compression, structure, or self-evaluation, do not prematurely introduce extra modules.

### 4. Open residual preservation is mandatory
High-value items that do not safely fit the local schema must be preserved in an explicit escape channel.

### 5. Minimal sufficient background is the compression target
The local model does not write beautiful summaries. It preserves what changes downstream reasoning.

### 6. KIR-Lite is the first operational intermediate representation
KIR-Lite v1.1 is the current working schema.

### 7. Capacity-boundary awareness must be explicit
The local model must recognize overload and switch from fake global synthesis to granular preservation.

### 8. Cloud should audit, not just solve
Cloud models can inspect whether local structured output actually forms a credible knowledge system.

## Important clarified concepts

### High-value information
Anything that can change the answer, reasoning path, constraint satisfaction, risk judgment, or evolution.

### Serviceable information
Anything the current local schema can safely express, compress, and transmit.

### Evolvable residual
High-value information that current local schema cannot safely absorb, but must not lose.

## Open questions for later stages

These were not fully defined in the discussion and remain future work:

1. How exactly should capacity overload be measured during training or evaluation?
2. Should KIR-Lite remain purely prompt-driven, or later become SFT-targeted?
3. How should cloud solver prompts differ from cloud audit prompts?
4. What training data format should be used for teaching the local 14B model to emit KIR-Lite reliably?
5. What metrics should define successful compression beyond token reduction?
6. How should recurring residual patterns be promoted into future schema updates?

## Recommended immediate next step

Run the local prompt on several real background examples and inspect whether the model drifts in:

- `capacity_guard`,
- `open_exit`,
- `must_keep`,
- `dynamic_constraints`,
- `cloud_audit` triggers.

That will expose whether the representation is already usable or still too ambitious.
