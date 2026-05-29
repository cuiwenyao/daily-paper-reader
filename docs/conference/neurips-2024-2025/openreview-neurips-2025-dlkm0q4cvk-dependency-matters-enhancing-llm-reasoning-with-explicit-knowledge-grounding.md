---
title: "Dependency Matters: Enhancing LLM Reasoning with Explicit Knowledge Grounding"
title_zh: 依赖至关重要：通过显式知识注入增强大模型推理
authors: "Xiangyu Wen, Min Li, Junhua Huang, Jianyuan Zhong, Zhijian Xu, Zeju Li, Yongxiang Huang, Mingxuan Yuan, Qiang Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DlkM0q4Cvk"
tags: ["query:ns-xai"]
score: 8.0
evidence: 将显式知识注入与神经网络推理相结合用于大模型
tldr: 针对LLM推理步骤表面连贯但内部不一致的问题，提出基于依赖的推理框架GRiD，将推理过程表示为包含知识抽取节点和推理节点的图结构，通过显式依赖关系强制逻辑一致性。结合轻量级逐步骤验证器确保前提符合逻辑。在多个推理基准上，GRiD显著提升了推理的正确性和可解释性，展示了符号知识显式引导对神经网络推理的有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1214, \"height\": 335}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1220, \"height\": 645}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 289}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1409, \"height\": 927}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 678, \"height\": 504}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1420, \"height\": 292}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1399, \"height\": 564}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1417, \"height\": 376}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 568}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 569}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1313, \"height\": 492}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1062, \"height\": 179}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1386, \"height\": 286}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 922, \"height\": 146}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 907, \"height\": 199}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 938, \"height\": 356}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 748, \"height\": 210}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 291}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1406, \"height\": 673}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 925, \"height\": 347}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1133, \"height\": 280}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1106, \"height\": 255}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1063, \"height\": 315}]"
motivation: LLM推理步骤常隐含不一致，源于隐式或未充分基于知识的推理。
method: 提出GRiD框架，将推理表示为依赖图，包含知识抽取和推理节点，并使用验证器保证逻辑正确性。
result: "在多个推理数据集上，GRiD比基线方法准确率提升5-10%，且推理过程更可解释。"
conclusion: 显式知识依赖是提升LLM推理可靠性和可解释性的有效途径。
---

## Abstract
Large language models (LLMs) often produce reasoning steps that are superficially coherent yet internally inconsistent, leading to unreliable outputs. Since such failures typically arise from implicit or poorly-grounded knowledge, we introduce \emph{Grounded Reasoning in Dependency (GRiD)}, a novel dependency-aware reasoning framework that explicitly grounds reasoning steps in structured knowledge. GRiD represents reasoning as a graph consisting of interconnected knowledge extraction nodes and reasoning nodes, enforcing logical consistency through explicit dependencies. Each reasoning step is validated via a lightweight, step-wise verifier that ensures logical correctness relative to its premises. Extensive experiments across diverse reasoning benchmarks—including StrategyQA, CommonsenseQA, GPQA, and TruthfulQA—demonstrate that GRiD substantially improves reasoning accuracy, consistency, and faithfulness compared to recent state-of-the-art structured reasoning methods. Notably, GRiD enhances performance even when applied purely as a lightweight verification module at inference time, underscoring its generalizability and practical utility. Code is available at: https://github.com/cure-lab/GRiD.

---

## 论文详细总结（自动生成）

## 论文总结：《Dependency Matters: Enhancing LLM Reasoning with Explicit Knowledge Grounding》

### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLMs）生成的推理步骤常常表面连贯但内部不一致，导致输出不可靠。这种失效的根源在于模型依赖隐式或缺乏充分依据的知识进行推理。
- **整体含义**：论文旨在通过显式地将推理步骤锚定在结构化知识上，并引入依赖验证机制，提升LLM推理的逻辑一致性、准确性和可解释性，从而增强模型在复杂推理任务中的可信度。

### 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：提出**GRiD（Grounded Reasoning in Dependency）** 框架，将推理过程表示为**依赖图**，其中节点分为两类：
  - **知识抽取节点（Knowledge Node，K_i）**：显式提示模型在推理每一步前检索相关的事实知识。
  - **推理节点（Reasoning Node，R_j）**：基于前提知识进行逻辑推断，并通过 `(by <knowledge_x>, <reason_y>, ...)` 显式标注依赖关系。
- **关键技术细节**：
  - **数据生成**：将传统Chain-of-Thought（CoT）转化为知识增强的依赖图格式。可通过自生成（模型自己按格式输出）或大型模型蒸馏（如GPT-4o、DeepSeek）实现。
  - **依赖验证（Dependency Verification）**：对每个推理节点，利用其直接前提节点，通过一个轻量级验证器检查逻辑正确性。验证标准包括：依赖可满足性、目的可满足性和事实可满足性。
  - **训练**：使用LoRA对Propuser模型（生成推理图）和Verifier模型（判断步骤正确性）进行监督微调，训练数据经过验证过滤以确保一致性。
- **算法流程（文字说明）**：
  1. 输入问题-答案对，由Proposer模型生成结构化的知识增强推理图（包含K_i和R_j节点及依赖关系）。
  2. 对生成的图进行依赖验证：按拓扑序遍历推理节点，构造验证输入（当前推理步骤+前提节点），由Verifier判断是否通过。过滤掉包含失败节点的数据。
  3. 使用通过验证的数据对Proposer和Verifier进行LoRA微调。
  4. 推理时：Proposer逐步生成推理图，每完成一个推理节点即触发Verifier进行实时验证；若失败则终止或修正，保留通过验证的部分作为最终答案。

### 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - **StrategyQA**：隐式多步推理，需要模型推导必要步骤。
  - **CommonsenseQA**：常识知识选择题。
  - **GPQA（Diamond子集）**：研究生级STEM知识问答（生物、物理、化学）。
  - **TruthfulQA**：测量模型避免常见谬误的能力。
- **基准与对比方法**：
  - **直接提示（Direct Prompting）**：包括直接回答、零样本、少样本。
  - **CoT-SC、GoT等X-of-Thought方法**。
  - **Disentangle**：分离记忆与推理的方法。
  - **ReAct**：结合搜索与推理。
  - **Fine-tune on QA Pairs**：标准监督微调。
  - **大型专有模型**：GPT-4o、DeepSeek-R1等。
- **评估指标**：pass@1准确率，以及自动化评价的忠实度（Faithfulness）和一致性（Consistency）分数。

### 4. 资源与算力

- **硬件**：所有实验使用NVIDIA L40 GPU和Intel(R) Xeon(R) Gold 6426Y CPU。
- **未明确说明**：论文未提供具体使用的GPU数量、训练总时长、单次实验耗时等详细信息。但根据描述，模型规模为7B/8B/14B，且使用LoRA微调，推测算力需求中等。

### 5. 实验数量与充分性

- **实验数量**：论文进行了多组对比实验，包括：
  - 主结果（Table 1）：GRiD vs. 多种基线，在4个数据集上使用Llama-3.1-8B和Qwen-2.5-14B作为基座。
  - 消融实验（Table 2）：验证数据过滤和运行时验证的效果。
  - 忠实度/一致性评估（Table 3）：自动评分对比。
  - 模型规模对比（Table 4）：7B→14B。
  - 数据来源对比（Table 5）：GPT-4o、DeepSeek、自生成等。
  - 计算成本分析（Figure 4, Table 6）。
  - 泛化能力测试（Table 7）。
  - 额外对比（Appendix）：ReAct基线、不同推理格式（Table 13）等。
- **充分性**：实验覆盖了多种推理类型（常识、科学、隐蔽推理、对抗性），对比了多种主流方法，并进行了详细消融。实验设计较为全面、客观，但部分结果未报告误差棒或显著性检验，建议补充。

### 6. 主要结论与发现

- GRiD在四个基准上显著优于现有结构化推理方法：相对于标准微调平均提升12.1%，相对于Disentangle基线提升6.6%，相对于原始直接提示提升25.2%。
- 依赖验证作为“即插即用”模块，在推理时进一步提高通过验证的样本准确率2%-7%，使小模型（8B/14B）接近甚至超越GPT-4o等大模型。
- GRiD生成的推理链具有更高的忠实度和一致性，并减少错误步骤。
- 模型自身生成的数据也能有效提升性能，说明提升源于推理格式改进而非蒸馏。
- 在GPQA上提升有限（6%），揭示了小模型的知识边界限制。

### 7. 优点：方法与实验设计亮点

- **显式知识依赖**：通过将推理步骤与知识节点显式链接，强制每一步基于事实，提升了可解释性和可靠性。
- **轻量级验证**：仅依赖当前步骤的直接前提，避免全局验证的高成本；可在推理时流式执行，及时中断错误。
- **无需外部资源**：完全基于模型自身知识，不依赖外部知识库或更大模型，增强了可扩展性和独立性。
- **数据驱动的训练改进**：利用验证过滤训练数据，减少噪声，提升模型学习效果。
- **广泛消融**：验证了数据来源、模型规模、验证策略等多个维度，结论扎实。

### 8. 不足与局限

- **泛化能力有限**：当前使用监督微调（SFT）专业格式，模型在训练域外表现下降（Table 7显示跨数据集泛化有待提升）。作者建议探索强化学习。
- **验证失败处理困难**：对于未通过验证的案例，使用Best-of-N、自一致性等策略改进效果有限，可能触及知识边界。需要更强的知识增强或反馈学习机制。
- **小模型知识边界**：在GPQA这类需要高度专业知识的任务上，即使GRiD改进，小模型仍落后于大模型，突出了预训练知识覆盖的重要性。
- **实验报告完整度**：缺少统计显著性和误差棒，部分对比（如与GPT-4o）未控制同等的验证强度。附录虽有补充，但主文可更严谨。

（完）
