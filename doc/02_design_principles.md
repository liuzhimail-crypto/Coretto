# Design Principles

This file records the core design principles that were explicitly established in the discussion.

## Principle 1 — LLM-first

> If a capability can be handled by the LLM itself, do not first reach for a new code module or engineering component.

Implication:

- prefer understanding, structured output, self-evaluation, compression, reformulation, distillation, LoRA/SFT, and prompt design,
- avoid prematurely adding routers, evaluators, classifiers, or independent algorithmic modules,
- only introduce thin engineering wrappers when clearly necessary.

A concise formulation:

> **If it can be trained into the model, do not outsource it to the system.**

## Principle 2 — Open-exit preservation

> Every structured solution must leave an escape hatch.

If the local model detects a piece of information that is:

- high-value,
- decision-relevant,
- but not safely expressible under the current local template,

then it must **not** be forced into the wrong slot.
It must instead be explicitly surfaced and passed to the cloud model for interpretation.

A concise formulation:

> **Do not force high-value anomalies into the wrong schema.**

## Principle 3 — Minimal sufficient background

The local model is not producing a normal summary.
It is producing the **minimum sufficient background** needed for downstream reasoning.

Compression target:

- not fluency,
- not completeness of narration,
- but preservation of what can change answers, paths, constraints, risks, or evolution.

A concise formulation:

> **Keep what can change the outcome. Remove what cannot.**

## Principle 4 — Structure before compression

The system should not immediately compress raw text into a shorter paragraph.
It should first separate the material into structural elements such as:

- task core,
- parameters,
- static constraints,
- dynamic constraints,
- mechanisms,
- boundaries,
- uncertainties,
- must-keep anchors,
- out-of-schema residuals.

A concise formulation:

> **Extract the skeleton first, then compress.**

## Principle 5 — Preserve decision relevance, not surface salience

A sentence should not be retained merely because it sounds important.
It should be retained if removing it would change:

- the answer,
- the reasoning path,
- the feasible constraint set,
- the risk judgment,
- or future schema evolution.

## Principle 6 — Residuals are not failure

Out-of-schema high-value items are not treated as noise or parser failure.
They are treated as:

> **Evolvable residuals**

which are candidates for:

- cloud interpretation,
- future schema extension,
- future local absorption.

## Principle 7 — No fake global understanding under overload

If the local model suspects that the context length, dependency density, constraint complexity, or ambiguity exceeds its trustworthy range, it must not pretend to have built a globally coherent knowledge system.

Instead it should switch to:

- granular extraction,
- must-keep preservation,
- residual surfacing,
- crop/scope recommendations,
- cloud audit request.

A concise formulation:

> **When overloaded, preserve particles instead of hallucinating closure.**

## Principle 8 — Cloud as auditor, not just solver

The cloud model is not only a stronger reasoning engine.
It is also a **constitutional auditor** that can inspect whether local extracted information:

- is complete,
- is consistent,
- forms a credible system,
- preserves anomalies properly,
- respects the constitutional principles.
