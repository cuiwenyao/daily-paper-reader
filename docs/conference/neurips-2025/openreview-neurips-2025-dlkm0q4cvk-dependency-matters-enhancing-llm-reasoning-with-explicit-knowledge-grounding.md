---
title: "Dependency Matters: Enhancing LLM Reasoning with Explicit Knowledge Grounding"
title_zh: 依赖至关重要：通过显式知识锚定增强大模型推理
authors: "Xiangyu Wen, Min Li, Junhua Huang, Jianyuan Zhong, Zhijian Xu, Zeju Li, Yongxiang Huang, Mingxuan Yuan, Qiang Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DlkM0q4Cvk"
tags: ["query:ns-xai"]
score: 8.0
evidence: 显式知识锚定实现可解释的大模型推理
tldr: 大模型推理常产生表面连贯但内部不一致的步骤。本文提出GRiD框架，将推理表示为包含知识提取节点和推理节点的图，通过显式依赖确保逻辑一致性，并利用轻量级逐步骤验证器检查正确性。在多个推理任务上，GRiD显著提升了推理的可靠性和可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1214, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1220, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1409, \"height\": 927, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 678, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1420, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1399, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dlkm0q4cvk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1417, \"height\": 376, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1313, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1062, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1386, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 922, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 907, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 938, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 748, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1406, \"height\": 673, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 925, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1133, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1106, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dlkm0q4cvk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1063, \"height\": 315, \"label\": \"Table\"}]"
motivation: LLM推理步骤常因隐含知识导致逻辑不一致。
method: 提出GRiD，基于图结构的依赖感知推理框架，显式锚定知识并验证步骤。
result: 在多种推理任务上，GRiD提升了逻辑一致性和可解释性。
conclusion: GRiD通过知识显式化增强了LLM推理的可靠性与可解释性。
---

## Abstract
Large language models (LLMs) often produce reasoning steps that are superficially coherent yet internally inconsistent, leading to unreliable outputs. Since such failures typically arise from implicit or poorly-grounded knowledge, we introduce \emph{Grounded Reasoning in Dependency (GRiD)}, a novel dependency-aware reasoning framework that explicitly grounds reasoning steps in structured knowledge. GRiD represents reasoning as a graph consisting of interconnected knowledge extraction nodes and reasoning nodes, enforcing logical consistency through explicit dependencies. Each reasoning step is validated via a lightweight, step-wise verifier that ensures logical correctness relative to its premises. Extensive experiments across diverse reasoning benchmarks—including StrategyQA, CommonsenseQA, GPQA, and TruthfulQA—demonstrate that GRiD substantially improves reasoning accuracy, consistency, and faithfulness compared to recent state-of-the-art structured reasoning methods. Notably, GRiD enhances performance even when applied purely as a lightweight verification module at inference time, underscoring its generalizability and practical utility. Code is available at: https://github.com/cure-lab/GRiD.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在推理过程中常产生表面连贯但内部逻辑不一致的步骤，且模型隐含知识与显式推理过程之间存在错位。这种不一致导致输出不可靠，尤其在需要严谨推理、逻辑一致性和忠实知识利用的任务中表现显著。
- **研究动机**：现有X-of-Thought（CoT、ToT、GoT等）方法虽然结构化推理，但依然存在长推理链脆弱性、隐含知识未显式利用、步骤间逻辑矛盾等问题。现有验证方法（如Process Reward Models）领域特定且依赖外部资源，可扩展性差。
- **总体含义**：提出一种新的依赖感知推理框架GRiD，通过显式锚定知识于模型自身内部知识库，以图结构组织推理步骤，并通过轻量级逐步骤验证确保逻辑一致性，从而提升LLM推理的准确性、一致性和可靠性。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将推理过程表示为知识-推理依赖图，包含两种节点：**知识提取节点**（显式检索与步骤相关的事实知识）和**推理节点**（基于锚定的前提知识进行逻辑推理）。通过显式依赖关系（如`(by <knowledge_0>, <reason_1>)`）强制逻辑一致，并对每个推理步骤进行轻量级验证。
- **关键技术细节**：
  - **数据生成**：利用LLM自身（自增强）或更大模型（蒸馏）将常规CoT转化为知识增强的依赖图格式。生成时，每个步骤要么是知识提取（`[knowledge_i]`），要么是推理（`[reason_j]`），并显式列出最小前提步骤。
  - **依赖验证（Dependency Verification）**：对每个推理节点`r_k`，给定其父节点集合（知识或推理节点），验证前提是否能正确推导出该步骤。验证形式化为：
    \[
    v_k = \begin{cases} 1, & \text{if } k_i, r_j, ... \Rightarrow r_k; i,j < k \\ 0, & \text{otherwise} \end{cases}
    \]
  - **训练数据过滤**：使用依赖验证过滤训练样本中未通过验证的推理步骤，提高数据质量。
  - **运行时验证**：在推理时，采用流式生成，每产生一个完整推理步骤立即进行依赖验证，及时中断错误推理。
  - **微调**：使用LoRA对Proposer（生成推理图）和Verifier（验证步骤）进行监督微调，目标函数为交叉熵损失。
- **算法流程**（Algorithm 1）：
  1. 对每个问答对，用Proposer模型（或外部LLM）生成结构化的知识增强推理图。
  2. 对每个推理节点，按拓扑顺序构造验证输入（当前步骤+父节点），用Verifier判别是否正确。
  3. 仅保留所有推理步骤均通过验证的样本作为训练数据。

## 3. 实验设计

- **数据集**：
  - StrategyQA：隐式多步推理。
  - CommonsenseQA：常识知识应用（多项选择）。
  - GPQA（Diamond子集）：研究生级STEM知识（生物、物理、化学）。
  - TruthfulQA：避免常见误解和模仿虚假信息。
- **Benchmark**：采用pass@1准确率指标。
- **对比方法**：
  - 直接提示（Direct Prompting）、零样本/少样本CoT、Tree-of-Thought、Graph-of-Thought等XoT方法。
  - 专门基线：Disentangle (Jin et al. 2025)、ReAct (Yao et al. 2022)。
  - 大型模型：GPT-3.5-turbo、GPT-4o、DeepSeek-R1、Qwen系列、Llama系列。
  - 消融实验：不同数据创建者（GPT-4o vs 自生成）、不同模型大小（7B/8B/14B）、是否使用数据过滤、是否使用运行时验证、不同推理格式（Direct/CoT/Long Thinking/GRiD）。

## 4. 资源与算力

- 论文明确提到使用**NVIDIA L40 GPU**和**Intel(R) Xeon(R) Gold 6426Y CPUs**进行所有实验。
- **未明确说明**：具体GPU数量、训练时长、总计算量等详细资源信息。附录A.1表8给出了微调超参数（批次大小1、梯度累积8、学习率5e-5~1e-4、LoRA秩16等），但未透露训练耗时或GPU小时数。

## 5. 实验数量与充分性

- **实验组数**：大量实验，涵盖：
  - 主要结果（表1）：在4个数据集上对比多种模型和方法。
  - 消融实验（表2）：数据过滤效果、运行时验证效果。
  - 忠实性与一致性评分（表3）：自动评估推理痕迹的质量。
  - 模型规模扩展（表4）：3种尺寸（7B/8B/14B）。
  - 数据创建者影响（表5）：GPT-4o、DeepSeek-V3/R1、模型自生成。
  - 计算成本分析（图4、表6）：推理长度和验证开销。
  - 与其他微调方法对比（表13）：Direct、CoT、Long Thinking等。
  - ReAct基线（表11、12）：提示和微调两种模式。
  - 知识边界讨论（图5）：故障分析。
- **充分性与公平性**：实验设计比较全面，对比了多种代表性基线和大型模型，消融实验覆盖关键组件。但未报告误差条或统计显著性检验，仅报告平均准确率，且未明确多次运行的标准差。实验公平性较好，但缺乏随机性控制描述。

## 6. 主要结论与发现

- **GRiD显著提升推理性能**：在Llama-3.1-8B和Qwen-2.5-14B上，相比标准微调提升12.1%，相比Base模型提升25.2%，相比Disentangle基线提升6.6%。
- **依赖验证有效**：数据过滤和运行时验证均能提升准确率2%~7%，使小模型性能接近大模型（如GPT-4o、DeepSeek-R1）。
- **忠实性与一致性改善**：GRiD在Faithfulness和Consistency得分上高于原始模型和CoT-SFT模型，且问题率更低。
- **知识边界是关键瓶颈**：小模型在GPQA上表现受限，主要原因是缺乏必要的基础知识（如“线粒体直接吸收葡萄糖”的误解），而非推理能力不足。
- **无需外部资源**：GRiD完全基于模型自身知识，不依赖外部数据库或大型辅助模型，具有良好的可扩展性和泛化潜力。

## 7. 优点

- **创新性**：首次提出知识锚定与显式依赖图的结合，将隐含知识显式化为推理节点，增强可解释性。
- **轻量级验证**：仅检查直接父节点，而非整个推理序列，验证成本低，可在线使用。
- **无外部依赖**：所有知识提取和验证均基于模型自身，避免外部噪声，提升独立性和可迁移性。
- **双向提升**：既能用于训练数据过滤，也可作为运行时验证模块，灵活性强。
- **实验全面**：在多个基准、多种模型规模、不同数据来源下进行验证，结果可靠。

## 8. 不足与局限

- **SFT泛化能力有限**：监督微调导致模型在训练域内表现好，但跨域泛化时性能下降（表7：在CommonsenseQA上训练的模型在GPQA上仅0.419，在TruthfulQA上0.775）。建议未来引入强化学习以增强域无关推理。
- **验证失败处理困难**：对于未通过依赖验证的样本，采用投票或Best-of-N策略改善有限，说明模型已达到知识边界。需要更强大的外部知识增强或反馈纠正机制。
- **知识边界限制小模型**：在GPQA等需要深厚专业知识的数据集上，小模型即便采用GRiD仍落后于大型长思维模型（如DeepSeek-R1），因为基础事实缺失。
- **计算开销**：验证模块的token消耗与主推理轨迹相当（见表6），在实时场景中可能增加延迟。
- **未报告统计显著性**：所有结果均为单次运行平均，缺乏误差条和重复实验，可能影响结果的稳健性。
- **潜在偏差**：数据生成依赖提示模板，可能引入格式偏好；SFT可能强化训练集内的特定推理模式。

（完）
