# Constitution v1.1

This document defines the constitutional core of the system.

## Article 1 — High-value information

**Definition:**
Any information that can change the answer, reasoning path, constraint satisfaction, risk judgment, or future schema evolution is high-value information.

### Practical test
Remove the information and ask:

- Does the answer change?
- Does the reasoning route change?
- Does the feasible solution set change?
- Does the risk judgment change?
- Does the system lose a chance to learn a new structure?

If yes to any of the above, it is high-value.

## Article 2 — Serviceable information

**Definition:**
Any information that the current local system can express, compress, transmit, and use with low semantic loss is serviceable information.

### Serviceability conditions
The current schema must be able to:

- place it reliably,
- compress it without losing decisive function,
- hand it off without distorting downstream reasoning.

## Article 3 — Evolvable residual

**Definition:**
Any information that is high-value but cannot be safely handled under the current local schema, and should not be deleted, is an evolvable residual.

### Rule
It must be:

- explicitly preserved,
- described rather than forced,
- passed to the cloud for interpretation,
- considered as a future schema evolution candidate.

## Article 4 — Capacity-boundary awareness

**Definition:**
When context length, dependency density, constraint complexity, or semantic ambiguity exceeds the trustworthy processing range of the local 14B model, the local model must not pretend to have completed global understanding.

### Required behavior under overload
The local model should:

- downgrade to granular preservation mode,
- preserve local reliable particles,
- preserve must-keep anchors,
- surface out-of-schema residuals,
- issue crop/scope commands,
- request cloud audit when needed.

## Article 5 — Cloud constitutional audit

**Definition:**
The structured output of the local model is not automatically a trustworthy knowledge system.
For important, complex, or overloaded cases, the cloud model should inspect:

- integrity,
- consistency,
- anomaly handling,
- schema misuse,
- constitutional compliance,
- future schema-evolution opportunities.

## Constitutional logic

The system applies the following order:

1. **Value judgment** — is it high-value?
2. **Serviceability judgment** — can the current local schema safely handle it?
3. **Residual judgment** — if high-value but not safely serviceable, must it be preserved as an evolvable residual?

## Constitutional slogan

> **First judge what can change the outcome. Then judge what can be safely served. Preserve the rest as evolvable residuals.**
