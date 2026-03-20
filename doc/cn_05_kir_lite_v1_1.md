# KIR-Lite v1.1

KIR-Lite 指的是 **Knowledge Intermediate Representation — Lite 版本**。
它是第一版专门为本地 14B 直接输出而设计的结构化中间表示。

## 设计目标

KIR-Lite v1.1 需要同时满足：

- 足够短，便于本地 14B 稳定输出；
- 足够结构化，便于交接给云端；
- 足够显式，能够承载约束与异常项；
- 足够开放，支持未来演化。

## JSON 结构

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

## 字段定义

### `task_core`
一句话说明：这份背景资料真正服务什么问题。

### `key_params`
只保留会改变答案或决策过程的关键参数。

每项格式：

```json
{"name": "", "value": "", "type": "descriptive|control|evaluative|critical", "why": ""}
```

参数类型含义：

- `descriptive` —— 描述系统状态
- `control` —— 可控、可配置
- `evaluative` —— 用来评价好坏或成功与否
- `critical` —— 阈值型、分支型、决定性参数

### `static_constraints`
永久假设、硬规则、固定原则、长期约束。

### `dynamic_constraints`
条件触发规则或状态依赖转移。
优先写成：

> 当……时，……必须/会……

### `mechanisms`
关键因果、依赖、取舍或触发关系。

每项格式：

```json
{"if": "", "then": ""}
```

### `must_keep`
不能被抽象掉的原文锚点或近原文锚点。
例如：

- 数字，
- 阈值，
- 否定，
- 定义，
- 宪法原句，
- 关键措辞。

### `open_exit`
高价值但无法安全装入当前 schema 的信息。

每项格式：

```json
{"description": "", "why_high_value": ""}
```

### `capacity_guard`
模型对自己是否仍处于可信范围内的自我判断。

字段包括：

- `status` —— `safe | borderline | overflow`
- `reasons` —— 做出该判断的原因
- `recommended_scope` —— 当前最安全的本地处理范围
- `crop_commands` —— 建议的裁切 / 分块 / 拆解动作

### `cloud_handoff`
给云端 solver 的紧凑交接材料。

- `compressed_context` —— 高密度、面向推理的背景
- `cloud_question` —— 云端真正要解决的问题
- `cloud_focus` —— 云端需要重点注意的事项

### `cloud_audit`
是否应由云端先审查结构，再决定是否求解。

- `required`
- `audit_goal`
- `audit_checks`

## 推荐输出纪律

- `task_core`：1 句话
- `key_params`：最多 8 项
- `static_constraints`：最多 8 项
- `dynamic_constraints`：最多 8 项
- `mechanisms`：最多 6 项
- `must_keep`：最多 6 项
- `open_exit`：最多 4 项
- `capacity_guard.reasons`：最多 6 项
- `capacity_guard.crop_commands`：最多 6 项
- `cloud_handoff.cloud_focus`：最多 6 项
- `cloud_audit.audit_checks`：最多 7 项

## 为什么这个 schema 重要

KIR-Lite v1.1 同时做三件事：

1. 捕捉 **主结构核心**；
2. 保留 **高价值未建模残差**；
3. 记录 **本地能力边界状态** 与 **审查需求**。

也正因此，它同时具备可操作性与可进化性。
