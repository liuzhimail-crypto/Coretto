# 项目文档包（中文）

本仓库文档包总结了一套 **local-first 混合 LLM 信息编译系统** 的设计讨论。

这个项目的核心不是做一个狭义的 token 路由器，而是构建一个 **可进化的广域信息服务体系**：

- 本地 14B 模型作为第一层智能前端，
- 负责提取和压缩高价值信息，
- 为模板外但高价值的信息保留显式出口，
- 只在确有必要时，才把高密度、面向推理的上下文交给云端模型。

## 文档内容

- [`docs/cn_01_overview_and_vision.md`](docs/cn_01_overview_and_vision.md) —— 项目愿景与系统身份
- [`docs/cn_02_design_principles.md`](docs/cn_02_design_principles.md) —— 核心设计原则
- [`docs/cn_03_constitution.md`](docs/cn_03_constitution.md) —— 宪法定义与运行法则
- [`docs/cn_04_architecture.md`](docs/cn_04_architecture.md) —— 架构与处理链路
- [`docs/cn_05_kir_lite_v1_1.md`](docs/cn_05_kir_lite_v1_1.md) —— KIR-Lite v1.1 结构与字段定义
- [`docs/cn_06_local_system_prompt_cn.md`](docs/cn_06_local_system_prompt_cn.md) —— 本地 14B 中文工作版 system prompt
- [`docs/cn_07_cloud_audit_prompt.md`](docs/cn_07_cloud_audit_prompt.md) —— 云端合宪审查 prompt
- [`docs/cn_08_workflows_and_operating_modes.md`](docs/cn_08_workflows_and_operating_modes.md) —— 正常模式、超载模式、审查模式
- [`docs/cn_09_naming_and_positioning.md`](docs/cn_09_naming_and_positioning.md) —— 命名、定位与 slogan 候选
- [`docs/cn_10_decision_log.md`](docs/cn_10_decision_log.md) —— 核心决策记录与未决问题

## 一句话定义系统

> 以尽量小的语义损失保留真正影响决策的信息，只把真正需要云端解释与强推理的部分送上云，同时让每一个高价值异常项都能存活到被理解为止。

## 项目立场

这个系统是 **LLM-first**，不是 module-first。

也就是说：

- 如果本地 LLM 可以通过理解、结构化、压缩、自评或重述来完成某项能力，就不要过早引入新的代码组件；
- 但如果某条高价值信息无法被当前 schema 安全表达，也不要强行塞进模板，而应显式保留并上交云端。

## 推荐的仓库结构

```text
.
├── cn_README.md
└── docs/
    ├── cn_01_overview_and_vision.md
    ├── cn_02_design_principles.md
    ├── cn_03_constitution.md
    ├── cn_04_architecture.md
    ├── cn_05_kir_lite_v1_1.md
    ├── cn_06_local_system_prompt_cn.md
    ├── cn_07_cloud_audit_prompt.md
    ├── cn_08_workflows_and_operating_modes.md
    ├── cn_09_naming_and_positioning.md
    └── cn_10_decision_log.md
```

## 当前成熟度

这套文档目前覆盖的是 **概念宪法层 + prompt 级实现层**。

它暂时还没有完整定义：

- benchmark 数据集，
- 训练目标与 loss 设计，
- fine-tuning 配方，
- GitHub 代码脚手架，
- 评测看板，
- 云端 solver 的完整 prompt 体系。

这些内容适合在真实材料验证表示层和 prompt 行为之后继续推进。
