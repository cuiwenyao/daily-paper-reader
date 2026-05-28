---
title: "ReCAP: Recursive Context-Aware Reasoning and Planning for Large Language Model Agents"
title_zh: ReCAP：面向大语言模型代理的递归上下文感知推理与规划
authors: "Zhenyu Zhang, Tianyi Chen, Weiran Xu, Alex Pentland, Jiaxin Pei"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=r2ykUnzuGt"
tags: ["query:ns-xai"]
score: 6.0
evidence: 递归上下文感知的LLM agent推理方法
tldr: 长程任务中LLM的推理和规划面临上下文漂移和失败循环问题。本文提出ReCAP框架，通过计划先行分解、父计划结构化重注入和动态调整上下文窗口三个机制，实现递归上下文感知的推理与规划，在多个复杂任务中显著提升成功率，为LLM推理提供新框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1273, \"height\": 191, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1362, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 674, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 692, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1418, \"height\": 1010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 688, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1115, \"height\": 1027, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1113, \"height\": 975, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1162, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1405, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1312, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1115, \"height\": 1027, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1113, \"height\": 975, \"label\": \"Table\"}]"
motivation: 现有LLM推理方法在长程任务中易出现上下文漂移和失败循环，影响多步推理效果。
method: 提出ReCAP框架，包括计划先行分解、父计划重注入和动态上下文窗口调整，实现递归上下文共享。
result: 在多个长期任务基准上，ReCAP相比基线方法显著提升推理成功率和规划效率。
conclusion: ReCAP通过上下文感知的递归机制有效增强了LLM在复杂任务中的推理和规划能力。
---

## Abstract
Long-horizon tasks requiring multi-step reasoning and dynamic re-planning remain challenging for large language models (LLMs). Sequential prompting methods are prone to context drift, loss of goal information, and recurrent failure cycles, while hierarchical prompting methods often weaken cross-level continuity or incur substantial runtime overhead. We introduce ReCAP (Recursive Context-Aware Reasoning and Planning), a hierarchical framework with shared context for reasoning and planning in LLMs. ReCAP combines three key mechanisms: (i) plan-ahead decomposition, in which the model generates a full subtask list, executes the first item, and refines the remainder; (ii) structured re-injection of parent plans, maintaining consistent multi-level context during recursive return; and (iii) memory-efficient execution, bounding the active prompt so costs scale linearly with task depth. Together these mechanisms align high-level goals with low-level actions, reduce redundant prompting, and preserve coherent context updates across recursion. Experiments demonstrate that ReCAP substantially improves subgoal alignment and success rates on various long-horizon reasoning benchmarks, achieving a 32\% gain on synchronous Robotouille and a 29\% improvement on asynchronous Robotouille under the strict pass@1 protocol.

---

## 论文详细总结（自动生成）

# ReCAP: 递归上下文感知推理与规划方法 —— 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型在处理需要多步推理和动态重规划的长期任务时面临重大挑战。现有方法主要分为两类：

- **顺序提示方法**（如 Chain-of-Thought、ReAct、Reflexion）：操作步骤线性排列，早期规划容易移出上下文窗口或变得过时，导致目标信息丢失和重复失败循环。
- **层次提示方法**（如 Tree of Thoughts、Graph of Thoughts、THREAD、ADaPT、REPL-Plan）：虽能组织推理层次，但常削弱不同层次间的连续性（子任务在孤立上下文中提示），或引入较大运行时开销（如依赖外部代码执行环境）。

论文由此提出核心问题：如何让智能体既能保持高层次全局意图，又能灵活调整底层细节，同时维持跨推理层次的连贯性？ReCAP 应运而生，旨在通过递归上下文感知机制实现长期规划与自适应推理。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
ReCAP 是一个层次化框架，所有推理和规划在共享的 LLM 上下文中递归进行。它通过三个互补机制解决现有方法的不足：

1. **计划先行分解**：不逐个生成子任务，而是一次性生成完整的子任务列表，然后只执行第一个子任务，之后利用执行反馈细化剩余计划。这保持了全局意图，减少了计划漂移。
2. **结构化重注入父计划**：所有递归深度的推理均在同一 LLM 上下文中进行。当从子目标返回时，父节点的计划（最新思考和剩余子任务）被重新注入当前活动上下文中，从而在递归回溯时保持跨层次连续性。
3. **内存高效的可扩展性**：使用滑动窗口（K 个对话轮次，通常 K=64）限制活动提示大小，重要信息通过结构化注入重新呈现，而不是无限累积。外部状态存储随递归深度线性增长，成本为 O(d·L̅)，其中 d 是树深度。

### 算法流程（文字描述）
- 入口函数 ReCAP(C) 接收初始上下文 C（含任务描述和一次示例）。
- 从 C 中调用规划函数 π，生成思考 T 和有序子任务列表 S = ⟨s₀, s₁, …, sₘ₋₁⟩。
- 循环执行 while S 非空：
  - 若 S[0] 是原始动作（可直接执行），则与环境交互得到观察 O，追加到 C。
  - 若 S[0] 是复合任务，则递归调用 ReCAP(C ∥ ⟨T, S, S[0]⟩)，子任务完成后返回。
  - 之后，将父节点的剩余计划 S[1:] 重新注入 C（即 C ← C ∥ ⟨T, S[1:]⟩）。
  - 调用细化函数 ρ 基于更新后的 C 生成新的思考和子任务列表。
- 当 S 为空或环境任务完成时结束。

此外，还有叶节点失败提示、非叶节点完成判断等辅助机制，在上下文过长时自动裁剪历史消息。

### 关键技术特点
- 所有递归深度共享一个不断演化的上下文字段，而非为每个层次分配独立上下文。
- 一次示例只在初始化时放置一次，减少冗余。
- 框架不依赖微调或额外训练。

## 3. 实验设计：数据集/场景、基准、对比方法

### 使用的数据集/场景（四个基准）
| 基准 | 类型 | 任务特点 | 步数范围 |
|------|------|----------|----------|
| **ALFWorld** | 符号文本式家庭模拟器 | 短链，线性动作（5-15步） | 4-25 |
| **Robotouille** | 具身烹饪环境（同步/异步） | 长链需协调子目标，异步模式含延迟 | 同步10-57，异步21-82 |
| **FEVER** | 知识密集型事实验证 | 短链，通过搜索/查找/判断（<10步） | 1-10 |
| **SWE-bench Verified** | 仓库级代码问题修复 | 长链，动作空间无限（>=45步） | 45-257 |

### 对比方法
- **顺序提示基线**：Standard（直接输出完整动作序列）、Chain-of-Thought (CoT)、ReAct、Act（去掉思考仅动作）
- **层次提示基线**：ADaPT（在其公开提示基础上适配 Robotouille 格式）
- **排除的基线**：THREAD（不可控递归）、Reflexion（需多轮自批判，不适用于单轨评估）、Ada-Planner（依赖代码解释器）、REPL-Plan（依赖外部代码执行环境）

### 评估协议
- 严格 **pass@1**：每个任务实例仅进行一次不间断推理-执行轨迹，无重试、无自一致性、无集成。
- 所有实验使用 **GPT-4o (2024-08-06)** 为主模型，SWE-bench 使用 GPT-4.1 (2025-04-14)。
- 少样本示例：每个智能体最多一次演示（one-shot）。

## 4. 资源与算力

论文中**未明确说明具体的 GPU 型号或训练时长**。所有实验均通过商业 API 调用（GPT-4o、DeepSeek-V3、LLaMA-4 等）完成，不涉及本地训练或 GPU 推理。在成本估计部分提到：Robotouille 的一个任务（synchronous/6）平均需 74.95 次 LLM 调用，累积成本约 7.77 美元；ALFWorld 全集（134个任务）ReAct 花费 37.89 美元，ReCAP 花费 118.40 美元，约为 ReAct 的 3 倍。SWE-bench 使用 GPT-4.1，温度=0，无示例，所有 500 个任务完全自动完成。

## 5. 实验数量与充分性

### 实验数量
- **Robotouille**：10 个同步任务 + 10 个异步任务，每个任务运行 10 个随机种子，总共 200 次评估。
- **ALFWorld**：测试集 134 个任务。
- **FEVER**：随机采样 200 个声明。
- **SWE-bench Verified**：500 个任务（其中 498 个成功提交，224 个解决）。
- **跨模型泛化实验**：在 Robotouille 的 3 个同步任务上测试了 Qwen2.5-32B、Qwen2.5-72B、LLaMA-4 (400B)、DeepSeek-V3 (671B) 共 4 个额外模型。
- **消融实验**：在单个任务（synchronous/6）上测试了 7 种结构变体（不同深度、有无思考、不同上下文长度等），每种变体运行多次。

### 充分性与公平性
- 所有方法在相同预算、相同步数限制、相同少样本设置下比较。
- 采用 pass@1 严格协议，避免性能增强策略。
- 对弱势假设（如 ADaPT 使用 GPT-3.5）已注明。
- 消融实验统计了 p 值，确认了结构变体与原版的差异显著性。
- 综合来看，实验覆盖了不同任务类型（短链、长链、代码、事实验证）、不同模型族、不同组件变体，具有较好充分性。

## 6. 论文的主要结论与发现

1. **ReCAP 在长期任务上显著优于基线**：同步 Robotouille 成功率高 32%（70% vs 38%），异步 Robotouille 高 29%（53% vs 24%），ALFWorld 高 7%（91% vs 71.6%），SWE-bench 高约 5%（44.8% vs 39.58%）。
2. **在短链任务（FEVER）上持平**：两个方法均为 63.5%，表明递归架构在短交互中无额外开销。
3. **跨模型泛化性好**：在所有 5 个模型（GPT-4o、Qwen2.5-32B/72B、DeepSeek-V3、LLaMA-4）上，ReCAP 均优于 ReAct，提升幅度从 15% 到 37% 不等。
4. **消融实验揭示关键组件**：访问最大深度（Level 2）导致成功率急剧下降（80% → 0%），说明足够的递归深度对分解至关重要；去除思考（no_think）仍有较高性能（60%），但全局来看思考提示帮助回溯。
5. **成本代价**：ReCAP 相比 ReAct 成本增加约 3 倍，主要来自额外推理痕迹和中间分解步骤。
6. **树结构分析**：在 Robotouille 中平均深度 3.4、分支因子 12.5，为浅树宽扇出结构。

## 7. 优点

### 方法层面
- **结合了计划先行与递归回溯**：一次性生成全子任务列表，只执行第一个，其余保留优化，减少了 myopic drift。
- **共享上下文与结构化注入**：所有递归深度的推理在单一上下文中完成，通过重注入父计划保持跨层次连贯性，避免上下文碎片。
- **内存高效**：滑动窗口限制活动提示大小，关键信息通过结构化注入重新呈现，成本与路径深度线性相关，而非总轨迹长度。
- **无需训练或微调**：完全基于提示工程，易于部署和迁移。

### 实验层面
- 严格 pass@1 协议提供了更真实的单次运行表现。
- 覆盖了多种任务类型（具身、符号、知识、代码）和多种模型族，展示了通用性。
- 进行了充分的消融实验和跨模型泛化实验，验证了组件贡献。

## 8. 不足与局限

### 方法局限
- **依赖底层模型质量**：所有分解、执行和回溯决策完全由 LLM 驱动，无外部验证或接地，模型质量差时误差会传播。
- **成本与延迟较高**：递归设计导致比平面提示更长的交互轨迹，API 开销增加约 3 倍，在成本/延迟敏感场景中可能有限制。
- **对工具调用的优先级处理（SWE-bench）**：在需要工具调用时，子任务分解被降级，这种折衷可能不是最优。

### 实验局限
- **未与所有基线全面比较**：排除了 THREAD、Reflexion、Ada-Planner 等部分层次方法，理由合理但可能遗漏潜在更公平的比较。
- **消融实验仅限于单个任务**：synchronous/6，可能无法完全反映所有场景的变体影响。
- **跨模型泛化实验仅涵盖三种同步任务**：样本较小，不足以全面评估模型家族的差异。
- **成本估计仅在部分任务上报告**：未提供全数据集平均成本。

### 应用风险
- 在安全关键领域（如医疗、金融）需要额外的监督和解释机制。
- 递归架构可能放大模型固有偏见或错误。

（完）
