# Architecture

## 1. System role split

The architecture is intentionally local-first.

### Local 14B model
Acts as:

- information compiler,
- task-core extractor,
- background compressor,
- local constitutional judge,
- residual preserver,
- capacity-boundary self-checker.

### Cloud model
Acts as:

- stronger reasoner,
- stronger interpreter,
- constitutional auditor,
- resolver of out-of-schema high-value items,
- inspector of whether local extracted particles form a credible knowledge system.

## 2. Primary processing chain

### Normal path
Raw background
→ Local 14B compiles into KIR-Lite v1.1
→ If `cloud_audit.required = false`
→ `cloud_handoff` is passed to cloud solver
→ Cloud performs final reasoning

### Complex / overloaded path
Raw background
→ Local 14B compiles into KIR-Lite v1.1
→ `capacity_guard.status = borderline | overflow` or `cloud_audit.required = true`
→ Cloud first performs constitutional audit
→ Then choose one of:
- solve directly,
- ask for recompilation,
- re-crop and resubmit,
- promote some residuals into main schema attention.

## 3. Why this architecture matters

The architecture avoids two failures:

### Failure A — sending everything raw to cloud
That wastes token budget and makes the cloud model do low-level cleanup work.

### Failure B — forcing local model to fake total understanding
That creates clean-looking but unreliable local knowledge structures.

This design instead enforces:

- local compression,
- local schema-aware extraction,
- explicit residual preservation,
- explicit overload awareness,
- cloud-level audit where needed.

## 4. Granular preservation mode

When overload is detected, the local model should stop trying to construct a polished global theory.
It should enter **granular preservation mode**.

In this mode, it focuses on:

- task core,
- key parameters,
- hard constraints,
- local reliable rules,
- must-keep spans,
- open residuals,
- cropping suggestions.

This preserves trustworthiness under pressure.

## 5. Audit as second-order reasoning

The cloud audit step is not just validation.
It is a second-order reasoning step that asks:

- Is the local representation complete enough?
- Are there hidden contradictions?
- Are some items clearly misclassified?
- Is the local model pretending to understand globally while overloaded?
- Are there schema-breaking patterns worth absorbing later?

## 6. Evolution loop

This is what makes the system evolvable.

Raw input
→ local extraction
→ cloud audit / interpretation
→ recognized residual patterns
→ future schema evolution candidates
→ stronger future local serviceability

So the system improves by learning from the residual channel.
