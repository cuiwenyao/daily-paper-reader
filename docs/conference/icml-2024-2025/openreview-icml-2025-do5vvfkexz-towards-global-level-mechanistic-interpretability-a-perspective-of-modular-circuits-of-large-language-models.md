---
title: "Towards Global-level Mechanistic Interpretability: A Perspective of Modular Circuits of Large Language Models"
title_zh: 面向全局级机械可解释性：大型语言模型模块化电路的视角
authors: "Yinhan He, Wendy Zheng, Yushun Dong, Yaochen Zhu, Chen Chen, Jundong Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=do5vVfKEXZ"
tags: ["query:ns-xai"]
score: 9.0
evidence: 模块化电路实现LLM全局机制可解释性
tldr: 针对现有机械可解释性方法中任务特定电路泛化性差和解释成本高的问题，本文提出模块化电路词汇库。通过构建任务无关的功能单元，每个单元由小型计算子图及其解释组成。该方法在多个语言任务上展示了更好的泛化性和更低的解释成本。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 840, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 818, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 807, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 823, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 850, \"height\": 199, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1250, \"height\": 1052, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1262, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-do5vvfkexz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1262, \"height\": 703, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-do5vvfkexz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-do5vvfkexz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 883, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-do5vvfkexz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1690, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-do5vvfkexz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1101, \"height\": 242, \"label\": \"Table\"}]"
motivation: 现有机械可解释性方法聚焦任务特定电路，泛化性差且成本高。
method: 提出模块化电路词汇库，包含任务无关的功能单元，每个单元有子图和解释。
result: 在多个任务上验证了方法泛化性和成本优势。
conclusion: 模块化电路是实现LLM全局可解释性的有效途径。
---

## Abstract
Mechanistic interpretability (MI) research aims to understand large language models (LLMs) by identifying computational circuits, subgraphs of model components with associated functional interpretations, that explain specific behaviors. Current MI approaches focus on discovering task-specific circuits, which has two key limitations: (1) poor generalizability across different language tasks, and (2) high costs associated with requiring human or advanced LLM interpretation of each computational node. To address these challenges, we propose developing a ``modular circuit (MC) vocabulary'' consisting of task-agnostic functional units. Each unit consists of a small computational subgraph with its interpretation. This approach enables global interpretability by allowing different language tasks to share common MCs, while reducing costs by reusing established interpretations for new tasks. We establish five criteria for characterizing the MC vocabulary and present ModCirc, a novel global-level mechanistic interpretability framework for discovering MC vocabularies in LLMs. We demonstrate ModCirc's effectiveness by showing that it can identify modular circuits that perform well on various metrics.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有机械可解释性（Mechanistic Interpretability, MI）研究主要关注**任务特定的计算电路**（task-specific circuits），即针对每个具体语言任务识别出对模型输出贡献最大的子图及其功能解释（FI）。但这种方法存在两个关键局限：
  - **泛化性差**：不同任务间的电路缺乏共享，从一个任务获得的洞察难以迁移到其他相关任务。
  - **成本高昂**：每个计算节点都需要人工或最先进的LLM（如GPT-4）进行解释，随着模型规模扩大，成本变得不可持续。
- **整体含义**：本文提出一种**模块化电路（Modular Circuit, MC）词汇库**的新视角，旨在实现**全局层面的机械可解释性**，即构建一组任务无关的、可复用的功能单元，使得不同语言任务可以共享共同的MC，并且新任务的电路匹配后可直接复用已有的解释，从而降低解释成本并提升跨任务洞察。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
- 定义**模块化电路（MC）** 为一个小型计算子图（modular SCS）及其关联的功能解释（FI）。MC是任务无关的、可跨任务复用的功能单元。
- 提出五条评价准则来刻画理想的MC词汇库：
  - **一致性（Consistency）**：同一MC在不同任务中的FI应语义相同。
  - **局部性（Locality）**：MC内的节点在物理位置和语义功能上应紧密相关。
  - **可复用性（Reusability）**：MC应出现在多个任务的计算电路中。
  - **可组合性（Composability）**：相邻MC的联合操作应反映功能的逻辑组合。
  - **全局性（Globality）**：词汇库规模应可控，每个电路使用的MC数量有上限。

### 关键技术细节与算法流程（ModCirc框架）
ModCirc分为三个步骤：
1. **任务格式统一与SCS收集**：
   - 将所有任务统一为**多选题问答**格式（每个样本提供正确和错误选项），使得因果效应计算只需关注第一个解码token的logit差异。
   - 采用**集成梯度（Integrated Gradients, IG）** 近似计算每个计算节点的间接效应（Indirect Effect），替代耗时的一次性激活修补，从而高效获得每个任务的显著计算子图（SCS）。具体地，收集每个Transformer层中间接效应值最高的前k个节点，并连接所有可能的边构成SCS。

2. **模块化SCS发现——基于强化学习的神经图划分**：
   - **可复用子图生成**：对任意两个任务的SCS取交集（保留多于1个节点的重叠部分），得到可复用子图，确保完整性和复用性。
   - **节点特征构建**：为每个节点构建融合语义和物理位置的特征向量。语义特征来自节点在多个任务上的激活模式（经MLP投影到统一空间），物理特征基于Transformer层索引和位置（注意力头/FFN索引）的欧几里得网格嵌入。
   - **初始划分**：通过算法1生成初始分区，保证内部连通性、大小均衡及跨子图兼容性。
   - **强化学习策略优化**：将图神经网络（GNN）作为策略网络，在初始划分基础上进行重新分区。每个重新分区过程包括：选择候选节点（根据邻居中异质性分区比例采样）→检测是否为关节点（articulation node）→若非关节点，则由GNN输出该节点的新分区（动作）→计算奖励，奖励基于一致性、局部性、可组合性设计的客观函数的变化。采用**策略梯度（REINFORCE）** 优化GNN参数，最大化累积折扣奖励。

3. **功能解释（FI）生成**：
   - 将训练数据集成，输入目标LLM，提取每个MC的激活值，计算token级L2范数生成热力图。
   - 将热力图输入高级LLM（如GPT-4），让LLM解释该MC的功能，从而获得MC的FI。

### 关键公式
- 间接效应（IE）的IG近似：  
  \( \text{IE}(v) \approx \left[ \sum_{i} \nabla_v \text{LLM}|_{v=v_{\text{mid}_i}} \right] (v_{\text{patch}} - v_{\text{clean}}) \)
- 奖励函数：  
  \( r(a) = \frac{\text{Obj}(G, P_{\text{before}}) - \text{Obj}(G, P_{\text{after}})}{\text{Obj}(G, P_{\text{before}}) + \text{Obj}(G, P_{\text{after}})} \)
- 累积回报：  
  \( R(\tau) = r(a_0) + \gamma r(a_1) + \cdots + \gamma^{L-1} r(a_{L-1}) \)

## 3. 实验设计

- **训练任务（用于发现MC词汇库）**：四个医疗任务数据集：
  - MEDAL（医疗摘要分类）
  - Medical Abstracts（病人状况分类）
  - MedMCQA（医疗多选题问答）
  - Symptom to Diagnosis（症状到诊断映射）
- **评估任务（用于测试MC的泛化性和复用性）**：四个不同领域的医疗任务：
  - MedStatus（识别临床文本中的用药状态）
  - MedAttr（识别医疗实体）
  - Coreference（临床指代消解）
  - PubMed Summ.（生物医学摘要总结）
- **基准方法（Baselines）**：
  - Random：随机从电路中选择节点，取半径3的ego图。
  - Frequent Random：先找到可复用子图，再随机划分。
  - Kmeans：对可复用子图做KMeans聚类划分。
  - Activation：根据节点在不同样本上的激活相似性分组。
- **消融实验**：ModCirc移除不同组件（随机选电路、跳过初始划分、仅做初始划分）的变体。
- **迁移性测试**：在GPT-2 Small上进行实验，使用四个NLP训练任务（AGNews、MPQA、Universal Dependency、TREC）发现MC词汇库，然后在两个有ground-truth电路的任务（IOI间接宾语识别、缩略词检测）上测试恢复率和FI对齐情况。

## 4. 资源与算力

- **文中明确说明**：实验在 **Nvidia RTX A6000** GPU上进行，模型为**Med-LLaMA（8B）** 和 **GPT-2 Small**。
- **训练细节**：学习率0.001，训练epoch数为10，所有结果平均五次运行。
- **未明确说明**：具体训练时间、使用的GPU数量、是否并行等未提及。

## 5. 实验数量与充分性

- **主要定量实验**：
  - 在4个评估数据集上比较ModCirc与4个baseline在**可组合性、一致性、可复用性**三个指标上的表现（表1）。
  - 消融实验（表2）在MediAttr上对比三个变体。
  - 参数敏感性分析（图4、附录图8）：对**top k**（每层选取的节点数）和**节点特征维度**的变化进行了系统测试。
- **定性实验**：
  - 展示一个代表性MC的构成和功能（图5），并分析其跨任务一致性。
  - 在GPT-2 Small上测试MC的**迁移性**：恢复IOI电路92%（23/25）的节点，恢复缩略词检测87.5%（7/8）的节点，并提供FI与ground-truth的对齐分析（图6、图7）。
- **充分性评价**：
  - 实验覆盖了医疗和通用NLP领域，任务类型多样（分类、QA、指代消解、摘要）。
  - 对比了多种baseline，包括简单随机、聚类和现有启发式方法。
  - 消融实验验证了各组件贡献。
  - 迁移测试验证了词汇库的泛化性和解释可迁移性。
  - 但实验仅在两个LLM（Med-LLaMA 8B和GPT-2 Small）上进行，未涵盖更大规模模型（如70B+）或更多架构（如Mixture-of-Experts）。此外，一致性指标的计算依赖LLM的FI生成，可能存在噪声。

## 6. 主要结论与发现

- **定量性能**：ModCirc在**可复用性**指标上大幅优于所有baseline（0.32–0.37 vs. 低于0.21），可组合性和一致性指标上与其他方法相当或略低，但整体表现均衡。
- **消融实验**：每个组件（电路选择、初始划分、RL优化）都有贡献，移除后一致性下降。
- **参数敏感性**：增加top k可提升可复用性；节点特征维度存在最优值（64），过高或过低都会降低可组合性。
- **定性案例**：发现的MC具有语义一致性，例如医疗任务中的“识别生物实体”MC出现在三个评估任务中，符合任务需求。
- **迁移性**：ModCirc能在新任务上识别出与ground-truth电路高度一致的MC，且FI与已知功能对齐，展示出良好的跨任务泛化能力。IOI任务中MC的组成和FI与已有文献一致，缩略词检测中MC捕获了字母移动和信息复制功能。

## 7. 优点

- **问题新颖性**：首次提出构建**模块化电路词汇库**以实现全局级机械可解释性，解决了任务特定电路的两大痛点。
- **方法论完整**：从评价准则、算法设计到FI生成，形成完整框架。结合因果归因（IG）、图神经网络、强化学习策略梯度，方法具有较强的技术融合性。
- **实验设计严谨**：既有定量对比，也有定性分析；既有医疗领域实验，也有通用NLP迁移验证；消融实验和参数分析齐全。
- **可复用性和成本优势显著**：在实验中展现出高可复用性，且FI可从词汇库中直接匹配，无需每次为新任务重新解释。

## 8. 不足与局限

- **模型规模与多样性**：仅在8B和更小的GPT-2模型上验证，未在更大规模（如70B+）或不同架构（如MoE）的LLM上测试，泛化性有限。
- **任务领域覆盖**：医疗主实验聚焦单一领域，通用迁移测试仅使用少量任务，可能未充分代表多样化的语言任务。
- **评价指标依赖**：一致性和可组合性计算依赖LLM生成的FI和互信息估计，存在噪声和主观性，可能影响结果可靠性。
- **初始划分依赖**：RL优化依赖于初始划分的质量，若初始划分不佳可能影响最终结果。
- **成本隐忧**：虽然声称降低了解释成本，但方法本身需要多次LLM推理（IG计算、FI生成），实际计算开销可能仍然较大。
- **可组合性验证不足**：实验中可组合性指标在部分baseline上也能得到满分，表明该指标可能区分度不够或未完全反映真实的逻辑组合性。
- **实际应用障碍**：词汇库的构建需要一组训练任务，对于全新领域或低资源任务，可能难以获得足够的训练数据。

（完）
