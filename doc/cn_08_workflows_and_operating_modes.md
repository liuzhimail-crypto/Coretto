# 工作流与运行模式

## 1. 正常模式（Normal mode）

当本地模型仍处于可信范围内时，走这条路径。

### 流程
原始背景
→ 本地 14B 编译 KIR-Lite v1.1
→ `capacity_guard.status = safe`
→ `cloud_audit.required = false`
→ 将 `cloud_handoff` 交给云端 solver
→ 获得最终推理结果

### 典型特征

- task core 稳定，
- 关键参数与约束仍可管理，
- 机制关系仍可表达，
- open_exit 项较少，
- 没有明显的“伪闭环”风险。

## 2. 临界模式（Borderline mode）

当本地模型仍能提取有价值结构，但已经不适合在无审查条件下做全局闭环综合时，走这条路径。

### 流程
原始背景
→ 本地 14B 编译 KIR-Lite v1.1
→ `capacity_guard.status = borderline`
→ 通常 `cloud_audit.required = true`
→ 云端先审查结构
→ 云端再决定是直接求解、要求修订，还是要求重新裁切后提交

### 典型特征

- 关键关系部分仍可提取，
- 但全局闭环已经脆弱，
- open_exit 较丰富，
- 跨段依赖较强。

## 3. 超载模式（Overflow mode）

当本地模型不应再假装自己可以完成全局可信综合时，走这条路径。

### 流程
原始背景
→ 本地 14B 进入颗粒保全模式
→ 输出局部可信颗粒 + must_keep + open_exit + crop_commands
→ `capacity_guard.status = overflow`
→ `cloud_audit.required = true`
→ 云端审查并决定下一步行动

### 典型特征

- 约束过多，
- 交互实体过多，
- 跨段依赖过多，
- 语义歧义过大，
- must_keep 保真压力过高。

## 4. 颗粒保全模式（Granular preservation mode）

这是本地模型接近或超出可信全局综合边界时的安全回退模式。

### 优先保留什么

- task core，
- key parameters，
- hard static constraints，
- critical dynamic constraints，
- must_keep anchors，
- open_exit residuals，
- crop commands。

### 要避免什么

- 伪造全局机制闭环，
- 写出顺滑但不可靠的系统级叙述，
- 通过弱依据压缩把关键条件抹平。

## 5. Crop command 的思想

crop_commands 不是硬编码工程规则，而是由 LLM 生成的、用于降低复杂度同时保住决策相关性的操作建议。

示例：

- 按任务目标切分背景材料
- 按实体切分背景材料
- 按时间阶段切分背景材料
- 优先保留关键参数、约束、must_keep 和 open_exit
- 降权背景解释性段落和重复叙述
- 将多子任务拆开分别提炼后再汇总
- 先做局部 KIR，再做云端审查整合

## 6. 云端审查检查表

触发审查时，云端模型应重点检查：

- 完整性，
- 一致性，
- 约束覆盖度，
- 机制闭环性，
- 异常保留，
- 宪法符合性，
- schema 演化机会。

## 7. 面向演化的工作流

这套工作流不是静态的。
凡是反复出现并呈现稳定意义的模板外残差，都可能成为未来 schema 的新候选。

所以这个工作流天然支持：

- 发现，
- 保留，
- 解释，
- 吸收，
- 演化。
