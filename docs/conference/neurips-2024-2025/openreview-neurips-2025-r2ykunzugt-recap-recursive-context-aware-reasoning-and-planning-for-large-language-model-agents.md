---
title: "ReCAP: Recursive Context-Aware Reasoning and Planning for Large Language Model Agents"
title_zh: ReCAP：大语言模型智能体的递归上下文感知推理与规划
authors: "Zhenyu Zhang, Tianyi Chen, Weiran Xu, Alex Pentland, Jiaxin Pei"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=r2ykUnzuGt"
tags: ["query:ns-xai"]
score: 6.0
evidence: 递归上下文感知推理与规划用于LLM智能体
tldr: 长程任务中LLM面临上下文漂移和重新规划难题。本文提出ReCAP，结合计划分解、父计划重注入等机制，维护多层一致性。实验证明在复杂任务中优于现有方法，提升LLM推理与规划能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1273, \"height\": 191}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 350}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1362, \"height\": 330}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 674, \"height\": 554}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 692, \"height\": 572}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1418, \"height\": 1010}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 688, \"height\": 541}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1115, \"height\": 1027}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r2ykunzugt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1113, \"height\": 975}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1162, \"height\": 317}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1405, \"height\": 196}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1312, \"height\": 157}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1115, \"height\": 1027}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r2ykunzugt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1113, \"height\": 975}]"
motivation: 长程任务中LLM推理易受上下文漂移影响。
method: 提出递归分层框架，包含计划分解和父计划重注入。
result: 在复杂任务中表现优于现有方法。
conclusion: 递归上下文感知可有效增强LLM推理规划能力。
---

## Abstract
Long-horizon tasks requiring multi-step reasoning and dynamic re-planning remain challenging for large language models (LLMs). Sequential prompting methods are prone to context drift, loss of goal information, and recurrent failure cycles, while hierarchical prompting methods often weaken cross-level continuity or incur substantial runtime overhead. We introduce ReCAP (Recursive Context-Aware Reasoning and Planning), a hierarchical framework with shared context for reasoning and planning in LLMs. ReCAP combines three key mechanisms: (i) plan-ahead decomposition, in which the model generates a full subtask list, executes the first item, and refines the remainder; (ii) structured re-injection of parent plans, maintaining consistent multi-level context during recursive return; and (iii) memory-efficient execution, bounding the active prompt so costs scale linearly with task depth. Together these mechanisms align high-level goals with low-level actions, reduce redundant prompting, and preserve coherent context updates across recursion. Experiments demonstrate that ReCAP substantially improves subgoal alignment and success rates on various long-horizon reasoning benchmarks, achieving a 32\% gain on synchronous Robotouille and a 29\% improvement on asynchronous Robotouille under the strict pass@1 protocol.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在处理需要多步推理和动态重新规划的**长程任务**时，面临两大挑战：(1) 顺序提示方法（如 ReAct、Reflexion）容易发生**上下文漂移**，早期的高层目标逐渐被遗忘或丢失，导致反复失败；(2) 层次化提示方法（如 ADaPT、THREAD）虽能组织多层推理，但存在**跨层级信息不连贯**、上下文碎片化以及额外运行开销。
- **研究动机**：人类能够自然地衔接高层抽象推理和低层具体执行，并根据反馈灵活调整计划。现有 LLM 方法缺乏这种连贯的多层级上下文管理和可回溯的规划能力。
- **整体含义**：提出一种新的递归层次化框架 ReCAP，通过共享上下文和结构化注入，让 LLM 在长程任务中保持全局目标与局部动作的一致，提升推理与规划能力。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：ReCAP 将任务执行建模为一个**递归过程**，所有深度共享同一个 LLM 上下文窗口，通过计划前置分解、结构化父计划重注入和滑动窗口内存管理，实现多层级连贯推理。
- **关键技术细节**：
  - **Plan-ahead 分解**：每次生成完整的子任务列表，只执行第一个子任务，其余保留供后续精炼，避免计划漂移。
  - **结构化上下文注入**：当从子任务返回时，将父任务的计划（最新思考+剩余子任务）重新注入到当前上下文，保持高/低层信息的连贯性。
  - **内存高效执行**：使用滑动窗口限制活跃提示长度（例如 K=64 轮对话），旧轮次被移除但关键计划信息通过结构化注入保留，成本与任务深度呈线性关系。
- **算法流程（文字说明）**：
  1. 输入任务描述和初始观测，LLM 生成初始思考和一个有序子任务列表。
  2. 循环执行子任务：若当前子任务为**原始动作**，则执行并记录观测；否则递归进入该子任务（扩展上下文）。
  3. 子任务完成后，将父任务的剩余计划重注入当前上下文，调用精炼函数更新思考和子任务列表。
  4. 重复直到子任务列表为空或环境结束。

### 3. 实验设计：数据集、Benchmark、对比方法

- **数据集 / 场景**：
  - **Robotouille**（同步和异步两种模式）：长程烹饪任务（10–82步），涉及资源竞争、延迟等待、并发子目标。
  - **ALFWorld**：文本家居指令任务（5–15步），短程但需组合命令。
  - **FEVER**：事实验证任务（1–10步），知识检索型。
  - **SWE-bench Verified**：真实仓库代码修复（45–257步），动作空间无限。
- **Benchmark**：采用严格的 **pass@1** 协议（单次推理-执行轨迹），无重试、无自一致性、无集成。所有方法使用相同的一次性示例（one-shot）和步数限制。
- **对比方法**：
  - 顺序方法：**Standard**（直接输出）、**CoT**、**ReAct**、**Act**（仅动作）。
  - 层次方法：**ADaPT**（仅用于 Robotouille，因 OpenAI 成本原因在 ALFWorld 使用 GPT-3.5）。
  - 排除 Reflexion（需要多轮）、Ada-Planner（代码执行依赖）、REPL-Plan（外部环境）等，因其与单次 pass@1 或接口不兼容。

### 4. 资源与算力

- 论文**未明确说明**使用了具体的 GPU 型号、数量或训练时间，因为所有实验均通过**商业 API**（主要是 GPT-4o，GPT-4.1，以及 Qwen2.5、LLaMA-4、DeepSeek-V3 等）完成，无需本地训练。
- 提供了成本估算：
  - Robotouille 单个任务（同步/6_lettuce_tomato_cheeseburger）平均 API 调用 74.95 次，平均成本 **7.77 美元**。
  - ALFWorld 全部 134 个任务：ReAct 总成本 37.89 美元，ReCAP 总成本 118.40 美元（约 3 倍）。
- 推理成本主要来自额外的推理痕迹和递归调用。

### 5. 实验数量与充分性

- **实验数量**：
  - Robotouille：10 个同步任务 × 10 实例，10 个异步任务 × 10 实例，共 200 次运行。
  - ALFWorld：官方 unseen split 的 134 个任务全部评估。
  - FEVER：200 个随机采样 claim。
  - SWE-bench Verified：500 个任务（498 个成功评估）。
  - 额外模型泛化实验：对 Robotouille 的 3 个任务测试了 4 种开源/闭源模型（Qwen2.5-32B/72B、LLaMA-4-400B、DeepSeek-V3-671B）。
  - 消融实验：在 Robotouille 一个任务上测试了 7 种结构变体（不同深度、无推理、仅有动作名等），以及不同上下文长度的影响。
- **充分性与公平性**：
  - 所有方法共享相同 LLM 设置、步数限制、one-shot 示例，且严格按 pass@1 执行，无额外优待。
  - 报告了 p-value（<0.001）表明统计显著。
  - 消融实验覆盖了关键结构要素，验证了递归深度、推理痕迹的必要性。
  - 实验设计较为充分，涵盖短/长程、符号/代码、同步/异步多种场景，减少了偏差可能。

### 6. 论文的主要结论与发现

- ReCAP 在长程任务上大幅超越顺序方法（ReAct、CoT 等）和层次方法（ADaPT）：
  - Robotouille 同步：**70%**（ReAct 38%），提升 **32%**。
  - Robotouille 异步：**53%**（ReAct 24%），提升 **29%**。
  - ALFWorld：**91%**（ReAct 84%，但 ReAct 使用 GPT-3.5，差距需谨慎看待）。
  - FEVER：**63.5%**（与 ReAct 相同，显示短任务中层次优势不大）。
  - SWE-bench Verified：**44.8%**（ReAct 39.58%），且解决率在长轨迹任务上仍不降为 0。
- **多模型泛化**：ReCAP 在 GPT-4o、Qwen2.5-32B/72B、LLaMA-4-400B、DeepSeek-V3 上均一致优于 ReAct，无需特定调整。
- **消融结论**：删除推理痕迹或降低递归深度（≤2 层）会严重降低成功率；但提供过多历史（Think Many）或只有子任务名（No Think）影响不大。表明明确的推理轨迹和足够的深度至关重要。
- 总体表明：**如何组织上下文**与**注入关键信息**对长程 LLM 决策至关重要。

### 7. 优点

- **上下文连贯性**：通过共享上下文和结构化重注入，解决了顺序方法的上下文漂移和层次方法的层级断裂。
- **自适应回溯**：遇到失败或阻塞能自动回溯、精炼计划，避免陷入重复循环（如图 3 所示）。
- **线性成本**：活跃提示大小和外部存储随深度线性增长，而非总轨迹长度。
- **模型无关**：框架无需微调或特定模型适配，在多款 LLM 上均有效。
- **严格评估**：采用 pass@1 协议，更贴近实际部署，排除多次尝试的干扰。

### 8. 不足与局限

- **依赖底层 LLM**：所有分解、执行和回溯决策均依赖 LLM，若模型质量差或指令理解错误，错误会传播。
- **成本较高**：递归设计导致 API 调用次数和延迟增加，约为 ReAct 的 3 倍，在成本敏感或延迟敏感场景受限。
- **短任务优势有限**：在 FEVER 等短程任务上效果与 ReAct 持平，未体现明显增益。
- **缺乏外部验证**：无独立机制验证子任务分解或动作合法性，完全依靠 LLM 自省。
- **实践部署挑战**：递归深度和回溯可能导致更长的端到端时间，需要关注效率优化。
- **实验覆盖限制**：在 SWE-bench 上仅使用 GPT-4.1 且无演示，可能低估了其他模型上的表现；消融仅在单一任务上测试，泛化性需进一步验证。

（完）
