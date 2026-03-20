# Overview and Vision

## 1. What this project is

This project started from a practical goal: **reduce expensive cloud token consumption** by decomposing agent tasks, leaving the most token-heavy but structurally manageable work to a local 14B model, and only sending the truly necessary parts to a cloud model.

But the design direction evolved beyond a narrow routing tool.

The system is now framed as an:

> **Evolvable wide-area information service system**

rather than just a token router.

## 2. The real ambition

The core ambition is to build a system that can:

1. **understand** incoming information,
2. **extract and compress** the parts that matter most,
3. **preserve high-value residuals** that current local templates cannot safely absorb,
4. **delegate stronger interpretation** to the cloud only when necessary,
5. **learn from template-breaking cases** so that the local schema can evolve over time.

In other words, the system is not trying to summarize text better.
It is trying to:

> turn raw, messy, heterogeneous inputs into serviceable, reasoning-ready informational cores.

## 3. Local model role

The local 14B model is not treated as a cheap substitute model.
It is treated as a:

- request compiler,
- background compressor,
- constitutional filter,
- anomaly preserver,
- local intelligence front-end.

Its job is to produce a **minimal sufficient background** for downstream reasoning.

## 4. Cloud model role

The cloud model is not treated as the default first processor.
It is invoked for:

- stronger reasoning,
- stronger interpretation,
- constitutional audit,
- resolution of out-of-schema high-value information,
- inspection of whether local extracted particles form a credible knowledge system.

## 5. The central tension

The project accepts a foundational tension:

- local schemas are finite,
- real-world semantics are wider than any current template,
- therefore a closed schema is never enough.

So the system must combine:

- **structured compression**, and
- **open residual preservation**.

This is what makes it evolvable rather than brittle.

## 6. What makes this system distinct

It is not merely:

- provider routing,
- model switching,
- prompt truncation,
- or ordinary summarization.

It is closer to a:

> **Self-routing + self-compression + residual-preserving information compiler**

where the local model decides:

- what is high value,
- what can be served locally,
- what must remain open,
- what should be sent upward,
- and when it no longer trusts its own global synthesis.

## 7. Working project identity

The project can be understood in one line as:

> A local-first information compiler that extracts decision-relevant cores, preserves high-value anomalies, and escalates only what truly needs cloud interpretation.
