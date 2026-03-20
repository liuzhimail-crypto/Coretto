# Workflows and Operating Modes

## 1. Normal mode

Use this path when the local model remains inside a trustworthy range.

### Flow
Raw background
→ local 14B compiles KIR-Lite v1.1
→ `capacity_guard.status = safe`
→ `cloud_audit.required = false`
→ send `cloud_handoff` to cloud solver
→ receive final reasoning result

### Typical characteristics

- task core is stable,
- key parameters and constraints are tractable,
- mechanisms are still expressible,
- open_exit is limited,
- no major risk of fake closure.

## 2. Borderline mode

Use this path when the local model can still extract useful structure, but trust is no longer strong enough for uninspected global closure.

### Flow
Raw background
→ local 14B compiles KIR-Lite v1.1
→ `capacity_guard.status = borderline`
→ usually `cloud_audit.required = true`
→ cloud audits structure
→ cloud decides whether to solve, request revision, or ask for cropped resubmission

### Typical characteristics

- some key relations are still extractable,
- but global closure may be fragile,
- open_exit may be relatively rich,
- cross-segment dependencies may be significant.

## 3. Overflow mode

Use this path when the local model should no longer pretend it has global reliable synthesis.

### Flow
Raw background
→ local 14B enters granular preservation mode
→ outputs partial but trustworthy particles + must_keep + open_exit + crop_commands
→ `capacity_guard.status = overflow`
→ `cloud_audit.required = true`
→ cloud audits and decides next action

### Typical characteristics

- too many constraints,
- too many interacting entities,
- too many cross-paragraph dependencies,
- too much ambiguity,
- too much pressure on must_keep fidelity.

## 4. Granular preservation mode

This is the safe fallback when the local model is near or beyond its reliable global synthesis boundary.

### What to preserve first

- task core,
- key parameters,
- hard static constraints,
- critical dynamic constraints,
- must_keep anchors,
- open_exit residuals,
- crop commands.

### What to avoid

- fake global mechanism closure,
- smooth but unreliable system-level narratives,
- weakly grounded compression that erases decisive conditions.

## 5. Crop command philosophy

Crop commands are not hard-coded engineering rules.
They are LLM-generated operational suggestions for reducing complexity while preserving decision relevance.

Examples:

- 按任务目标切分背景材料
- 按实体切分背景材料
- 按时间阶段切分背景材料
- 优先保留关键参数、约束、must_keep 和 open_exit
- 降权背景解释性段落和重复叙述
- 将多子任务拆开分别提炼后再汇总
- 先做局部 KIR，再做云端审查整合

## 6. Cloud audit check list

When audit is triggered, the cloud model should inspect:

- integrity,
- consistency,
- constraint coverage,
- mechanism closure,
- anomaly preservation,
- constitutional compliance,
- schema evolution opportunities.

## 7. Evolution-oriented workflow

This operating model is not static.
Out-of-schema residuals that recur and show stable meaning can become future schema candidates.

That means the workflow itself supports:

- detection,
- preservation,
- interpretation,
- absorption,
- evolution.
