# 命名与定位

本文件记录命名讨论与推荐的对外定位。

## 1. 项目定位

这个项目不应被定位成：

- 廉价模型切换器，
- provider 路由器，
- prompt 截断器，
- 或普通摘要器。

更好的定位是：

> **面向混合 LLM 系统的 local-first 信息编译器**

或者：

> **具备自路由、残差保留、面向推理的信息编译器**

## 2. 候选名称

对话中提出了多个名字。

### 强候选

#### Coretto
推荐作为最强的产品风格名称。

为什么合适：

- 好记，
- 简洁，
- 很像真实产品名，
- 带有“压到核心”的意象。

推荐一句话：

> **Coretto — Compile queries to their core.**

#### Kernel
推荐作为最强的研究 / 系统风格名称。

为什么合适：

- 与“不可再约减的 query 核心”高度契合，
- 非常符合“最小充分上下文”哲学，
- 理论味更强。

推荐一句话：

> **Kernel — Minimal sufficient context for cloud reasoning.**

#### Prism
推荐作为最强的方法论意象名称。

为什么合适：

- 能表达“把复杂 query 分解成有意义成分”，
- 很符合“先分解，再压缩”的思路，
- 优雅，也容易记。

推荐一句话：

> **Prism — Refract complex queries into reasoning-ready cores.**

## 3. 候选 slogan

### Coretto

- Compile the core.
- Less prompt, more reasoning.
- From messy queries to minimal intelligence.

### Kernel

- Find the irreducible query.
- Only the core goes to the cloud.
- Minimal context, maximal reasoning.

### Prism

- Split the noise. Keep the signal.
- Refract queries into reasoning cores.
- Understand first. Send less.

## 4. 当前推荐姿态

如果现在需要一个对外工作名：

- 对外产品名用 **Coretto**，
- 内部中间表示名称用 **KIR-Lite**，
- 技术文档中维持架构中性的描述。
