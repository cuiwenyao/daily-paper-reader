---
title: "Aligning with Logic: Measuring, Evaluating and Improving Logical Preference Consistency in Large Language Models"
title_zh: 与逻辑对齐：测量、评估和改进大型语言模型中的逻辑偏好一致性
authors: "Yinhong Liu, Zhijiang Guo, Tianya Liang, Ehsan Shareghi, Ivan Vulić, Nigel Collier"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=V61nluxFlR"
tags: ["query:ns-xai"]
score: 4.0
evidence: 测量并提升LLM的逻辑偏好一致性
tldr: LLM在判断中存在不一致性，影响可靠性。本文提出基于传递性、交换性和否定不变性的逻辑偏好一致性评估框架，实验表明这些属性是LLM可靠性的强指标，并可通过针对性训练改善一致性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1681, \"height\": 949, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 610, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 778, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1632, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1669, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1694, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1643, \"height\": 1811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1155, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-v61nluxflr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 689, \"height\": 536, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 1071, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 932, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 815, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 991, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1261, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 992, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-v61nluxflr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 725, \"height\": 345, \"label\": \"Table\"}]"
motivation: LLM在决策中表现出不一致性，需要量化逻辑一致性。
method: 定义传递性、交换性和否定不变性三个属性作为一致性评估框架。
result: 发现这些属性在多种LLM上差异显著，是可靠性的良好指标。
conclusion: 逻辑偏好一致性是构建可靠LLM系统的基础要求。
---

## Abstract
Large Language Models (LLMs) are expected to be predictable and trustworthy to support reliable decision-making systems. Yet current LLMs often show inconsistencies in their judgments. In this work, we examine \textit{logical preference consistency} as a foundational requirement for building more dependable LLM systems, ensuring stable and coherent decision-making while minimizing erratic or contradictory outputs.
To quantify the logical preference consistency, we propose a universal evaluation framework based on three fundamental properties: *transitivity*, *commutativity* and *negation invariance*.
Through extensive experimentation across diverse LLMs, we demonstrate that these properties serve as strong indicators of judgment robustness.
Furthermore, we introduce a data refinement and augmentation technique, REPAIR, that enhances logical consistency while maintaining alignment with human preferences. Finally, we show that improving consistency leads to better performance in LLM-driven logic-based algorithms, reinforcing stability and coherence in decision-making systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
大型语言模型（LLM）在决策和推理中日益重要，但其预测常出现不一致（如自相矛盾、偏好反转），严重损害系统的可靠性和可信度，尤其在高风险领域（医疗、金融、自动驾驶）中可能导致错误结论。现有研究多关注事实知识一致性或自然语言推理中的简单逻辑关系，缺乏对**逻辑偏好一致性**的系统定义与量化。本文认为，逻辑偏好一致性是构建可靠LLM系统的基础，并聚焦于偏好判断场景（如比较摘要质量、文档相关性、事件时序），旨在衡量、评估并提升LLM在偏好比较中的逻辑一致性。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 逻辑一致性评估框架
将LLM视为二元比较算子 \( F(x_i, x_j) \)，输出偏好关系（\( x_i \succ x_j \) 或 \( x_j \succ x_i \)）。基于三个关键属性量化一致性：

- **传递性（Transitivity）**：若 \( F(A,B) = A \succ B \) 且 \( F(B,C) = B \succ C \)，则必须 \( F(A,C) = A \succ C \)。  
  通过构建**有向关系图**并检测环路实现。定义指标 \( s_{\text{tran}}(K) \)：随机采样K个节点子图，计算无环比例（\( 1_{\text{acyclic}} \)），取值范围0~1。
- **交换性（Commutativity）**：交换比较顺序（\( A vs B \) 改为 \( B vs A \)）后，模型判断应保持不变。  
  指标 \( s_{\text{comm}} = \frac{2}{|X|(|X|-1)} \sum_{i<j} \mathbf{1}(F(x_i,x_j) = F(x_j,x_i)) \)。
- **否定不变性（Negation Invariance）**：对原关系取反（如“更好”变“更差”）后，模型应输出相反判断。  
  指标 \( s_{\text{neg}} = \frac{1}{|X|(|X|-1)} \sum_{i\neq j} \mathbf{1}(\neg F(x_i,x_j) = \neg F(x_i,x_j)) \)。

### 2.2 提升一致性的 REPAIR 框架
**核心思想**：从噪声偏好数据中先估计全局排序，再生成无冲突的成对比较，增强逻辑一致性的同时保持与人类偏好对齐。

**具体流程**：
1. **排序估计**：使用赢亏率（win-loss rate）对每个项目打分并排序，也可用Elo或Bradley-Terry模型（消融实验比较）。
2. **数据扩充**：将估计出的排序转化为**一致的成对比较**（所有比较均与排序一致），并进一步加入否定关系比较（negated relations）来提升否定不变性。
3. **指令微调**：用扩充后的无冲突数据训练LLM（如Llama-3-8B-Instruct），仅使用LoRA（r=16, alpha=64）微调2个epoch。

## 3. 实验设计

### 3.1 评估数据集与场景
- **SummEval**：摘要连贯性评估，100篇源文本，每篇16个摘要候选。
- **NovelEval**：文档重排序，21个问题，每问题20个候选文档。
- **CaTeRS**：时序/因果事件排序，70个实例（7个以上事件）。

**基准（Benchmark）**：计算三个一致性指标 \( s_{\text{tran}}(5) \)、\( s_{\text{comm}} \)、\( s_{\text{neg}} \)，同时报告与人类标注的一致性（Human Agreement, H.）以及模型自一致性（Self-agreement）。

### 3.2 对比方法
- 直接判断（Direct Judgements）：10个开放/API LLM（Llama-2/3, Mistral, Zephyr, Phi-3, Gemma-2, GPT-3.5, Deepseek）。
- CoT（Chain-of-Thought）提示：同样10个模型，温度0.7生成10次评估自一致性。

### 3.3 训练实验（REPAIR有效性）
- **训练数据**：Summarize from Feedback（64k+对摘要比较）和MS MARCO（文档重排序，1k样本）。
- 对比条件：
  - 零样本推理
  - 原始干净数据微调
  - 10%标签翻转后的扰动数据微调
  - REPAIR-ed 数据微调（扩充）
  - REPAIR-ed + 否定关系微调

### 3.4 下游应用实验
- 使用PairS排序算法，将LLM作为比较算子进行排序，评估Spearman相关系数（原始和校准后）。

### 3.5 消融实验
- 子图采样大小 K 的影响（如图9）。
- 排序估计方法比较：赢亏率 vs Elo vs Bradley-Terry。
- 数据下采样：比较REPAIR-ed数据与等量原始扰动数据。

## 4. 资源与算力
论文附录F注明：训练使用A100 GPU（未说明具体数量），超参数包括学习率5e-5，2个epoch，权重衰减1e-2，LoRA r=16, alpha=64，batch size 4，梯度累积2。整体算力开销较小（仅微调8B模型，且使用LoRA）。

## 5. 实验数量与充分性
- **评估实验**：在3个不同领域（摘要、重排序、时序）数据集上评估10个LLM，每个模型在直接判断和CoT两种模式下均报告三个一致性指标及人类一致性，共约60组评估数据。
- **训练实验**：在两个训练数据集（Summarize from Feedback, MS MARCO）上进行REPAIR效果验证，包含5个对比条件，另加消融实验（下采样、不同排序估计方法、K值选择），共计约15组微调+评估实验。
- **下游任务**：在SummEval上测试PairS排序，对比4个模型（Mistral, Phi-3-mini, GPT-3.5, Phi-3-medium），含校准版。
- **充分性分析**：实验覆盖了多种模型家族、任务类型、一致性维度，并有消融和基准对比，设计较完整。但训练数据集仅两个规模较小（Summarize from Feedback较大但MS MARCO仅1k样本），且未在更多任务（如数学推理、对话）上验证。总体充分但可进一步扩展。

## 6. 论文的主要结论与发现
1. **LLM存在显著逻辑偏好不一致**，且不同模型差异大；更强模型（如Gemma-2-9B, Phi-3-medium, Deepseek）整体一致性更高。
2. **传递性与模型自一致性强相关**（Spearman相关系数>0.8），可作为局部鲁棒性的代理指标。
3. **交换性与人类偏好一致性强相关**，表明位置偏差会严重影响对齐效果。
4. **CoT提示不一定改善一致性**，有时甚至降低传递性，可能与额外推理token引入判断标准波动有关。
5. **REPAIR框架有效提升逻辑一致性**（传递性、交换性接近完美），同时保持甚至提升人类偏好对齐。
6. **仅训练否定关系可专门提升否定不变性**，但可能轻微损害其他属性。
7. **更高一致性带来更好下游排序性能**（PairS算法），且交换性高时更少依赖校准（降低计算成本）。

## 7. 优点
- **首次系统定义并量化LLM的三种逻辑偏好一致性属性**，提供通用评估框架，适用范围广。
- **实验全面**：涵盖多种模型家族（7B~数十B）、多种任务（主观/客观）、多种提示方式，统计严谨（Spearman相关、p值）。
- **提出实用数据改进方法REPAIR**：从噪声数据中自动提取更一致信号，无需额外人工标注，且方法简单易复现。
- **验证了一致性对下游算法（排序）的实际价值**，建立了一致性→可靠性→任务性能的因果链。
- **开源代码和细化数据集**，促进可复现研究。

## 8. 不足与局限
- **评估范围有限**：仅考察二元比较（偏好），未扩展至多值偏好或更复杂的逻辑推理（如条件推理、数理逻辑）。
- **数据集规模较小**：CaTeRS仅70实例，训练数据集主要来自摘要与重排序，缺乏更多样化场景（如对话、指令遵循）。
- **未充分讨论噪声来源**：假设人为标注噪声可模拟为随机翻转，但实际噪声可能具有系统性偏差。
- **REPAIR依赖排序估计方法**：赢亏法简单但可能丢失部分信息；Elo/BT在稀疏比较下不稳定，仍需人为选择合适的聚合方法。
- **计算资源披露不足**：仅提A100机器，未说明具体GPU数量和训练总时长。
- **社会影响讨论偏宏观**：仅强调一致性重要性，未深入评估改进后模型在公平性、偏见方面的潜在风险。

（完）
