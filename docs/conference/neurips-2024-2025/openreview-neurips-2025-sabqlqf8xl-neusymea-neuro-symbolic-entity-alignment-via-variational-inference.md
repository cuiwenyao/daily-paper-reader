---
title: "NeuSymEA: Neuro-symbolic Entity Alignment via Variational Inference"
title_zh: NeuSymEA：基于变分推理的神经符号实体对齐
authors: "Shengyuan Chen, Zheng Yuan, Qinggang Zhang, Wen Hua, Jiannong Cao, Xiao Huang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=SAbQLqf8XL"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号推理框架用于实体对齐，兼具可解释性
tldr: 实体对齐任务中，符号模型精确但处理稀疏性弱，神经模型有效但缺乏可解释性。NeuSymEA提出统一神经符号框架，利用马尔可夫随机场和变分EM算法联合建模实体对真实分数，同时引入规则约束，在多个数据集上实现鲁棒且可解释的对齐。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 472}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1318, \"height\": 344}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1301, \"height\": 343}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 433}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 398}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1461, \"height\": 1017}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 216}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 1171}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 475}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 283}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1459, \"height\": 835}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1013, \"height\": 283}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 664, \"height\": 144}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 950, \"height\": 181}]"
motivation: 现有实体对齐方法中，符号模型与神经模型各有优劣且缺乏可解释性。
method: 构建马尔可夫随机场联合建模实体对分数，通过变分EM算法优化，神经模型负责E步，符号规则约束M步。
result: 在多个知识图谱对齐基准上达到最优性能，且推理过程可解释。
conclusion: 神经符号统一框架有效结合了符号模型的精确性和神经模型的鲁棒性。
---

## Abstract
Entity alignment (EA) aims to merge two knowledge graphs (KGs) by identifying equivalent entity pairs. Existing methods can be categorized into symbolic and neural models. Symbolic models, while precise, struggle with substructure heterogeneity and sparsity, whereas neural models, although effective, generally lack interpretability and cannot handle uncertainty. We propose NeuSymEA, a unified neuro-symbolic reasoning framework that combines the strengths of both methods to fully exploit the cross-KG structural pattern for robust entity alignment. NeuSymEA models the joint probability of all possible pairs' truth scores in a Markov random field, regulated by a set of rules, and optimizes it with the variational EM algorithm. In the E-step, a neural model parameterizes the truth score distributions and infers missing alignments. In the M-step, the rule weights are updated based on the observed and inferred alignments, handling uncertainty. We introduce an efficient symbolic inference engine driven by logic deduction, enabling reasoning with extended rule lengths. NeuSymEA achieves a significant 7.6\% hit@1 improvement on $DBP15K_{ZH-EN}$ compared with strong baselines and demonstrates robustness in low-resource settings, achieving 73.7\% hit@1 accuracy on $DBP15K_{FR-EN}$ with only 1\% pairs as seed alignments. Codes are released at https://github.com/chensyCN/NeuSymEA-NeurIPS25.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

实体对齐（Entity Alignment, EA）旨在通过识别不同知识图谱（KGs）中的等价实体对，将多个知识图谱合并为一个统一、全面的知识库。现有方法主要分为**符号模型**和**神经模型**两类：
- **符号模型**：精确、可解释，但难以处理子结构异质性和稀疏性，尤其对低度实体召回率低。
- **神经模型**：有效、可扩展，但缺乏可解释性，且不能处理不确定性。

论文的核心动机是**融合两种方法的优势**，提出一个统一的神经符号推理框架，以充分利用跨知识图谱的结构模式，实现鲁棒且可解释的实体对齐。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
将实体对齐建模为**马尔可夫随机场（MRF）上的联合概率优化问题**，并用一组加权规则调控。通过**变分EM算法**进行优化：
- **E-step**：用神经模型参数化真值分数分布，推断缺失的对齐。
- **M-step**：根据观测和推断的对齐更新规则权重，处理不确定性。

### 关键技术细节
- **逻辑分解**：将长规则（长度为L）通过逻辑演绎分解为L个单元长度子规则，避免指数级搜索空间，实现高效推理。
- **规则权重定义**：每个单元规则由关系唯一性度量η(r)和子关系概率p_sub(r ⊆ r')组成。整体规则权重为各单元规则权重的乘积。
- **推理**：E-step中，神经模型（如Dual-AMN或LightEA）训练得到实体嵌入，计算匹配分数；符号模型根据加权规则传播对齐概率。M-step中，用神经模型产生伪标签，贪心策略确保一对一匹配，再更新子关系概率。
- **解释器**：训练后，可反转规则分解过程，生成支持对齐的路径（硬锚模式/软锚模式），并给出置信度分数。

### 算法流程
1. 初始化：用种子对齐对初始化。
2. 迭代：
   - **E-step**：固定规则权重，训练神经模型（优化包含符号模型推断伪标签的损失函数）。
   - **M-step**：用神经模型得到伪对齐对，更新子关系概率（即规则权重）。
3. 最终预测：融合符号模型和神经模型的结果。

## 3. 实验设计

### 数据集
- **DBP15K**（主要）：三个跨语言对：ZH-EN、JA-EN、FR-EN。同时使用**完整版**（含低度实体，更真实）和**浓缩版**（剔除低度实体）。
- **OpenEA** (100K) 和 **DBP1M**：用于可扩展性测试的大规模数据集。

### 基准与对比方法
- **神经模型**：GCNAlign、AlignE、BootEA、RREA、Dual-AMN、LightEA、PEEA。
- **符号模型**：PARIS。
- **神经符号模型**：PRASE、EMEA。
- 评价指标：Hit@1、Hit@10、MRR。

### 对比设置
- 采用OpenEA的5折交叉验证（训练:验证:测试 = 2:1:7），保证公平对比。
- 低资源场景：训练数据比例为1%、5%、10%、20%。
- 消融实验：不同阈值δ、EM迭代次数、规则长度等。

## 4. 资源与算力

论文在附录中提供了机器配置和运行时资源：
- **GPU**：NVIDIA GeForce RTX 3090
- **CPU**：Intel(R) Xeon(R) Silver 4214R 2.40GHz
- **运行时**：15分钟
- **内存**：868 MB
- **GPU显存**：4.33 GB
- 未说明使用多卡或分布式训练，单机单卡即可。

## 5. 实验数量与充分性

### 实验组数
- **主实验结果**（表1）：在DBP15K完整版和浓缩版上，对比7+种基线，3个语言对，共6个子表。
- **低资源实验**（表3）：4种训练比例 × 3个数据集 × 15种方法，共180余项结果。
- **可扩展性对比**（图3）：在OpenEA和DBP1M上与LightEA对比。
- **参数分析**（图5）：对δ和迭代次数进行网格搜索。
- **解释器分析**（图4）：规则置信度分布、规则长度影响。
- **规则进化分析**（图2）：迭代中规则推断的精度和神经模型MRR收敛。

### 充分性评价
- 全面覆盖了标准基准、大规模数据、低资源场景、参数敏感性、可解释性分析。
- 对比方法包括近年SOTA（2022-2025），公平采用相同数据划分和迭代版本。
- 消融实验较充分，但缺少对神经模型本身（如不同嵌入方法）的单独消融（仅提供了两种神经模型变体NeuSymEA-D和NeuSymEA-L）。

## 6. 论文的主要结论与发现

1. NeuSymEA在DBP15K所有语言对上**显著超越**所有纯神经、纯符号及其他神经符号模型，ZH-EN上Hit@1提升7.6%（相对）。
2. 在低资源（仅1%种子）场景下，FR-EN上Hit@1达到73.7%，优于许多模型训练20%时的结果，证明**鲁棒性**。
3. 逻辑分解使得长规则推理高效且可扩展，在大规模KG（DBP1M）上仍能保持较高性能。
4. 解释器能生成具有明显区分度的支持规则：正例规则置信度高，负例规则置信度低或为空集。
5. 规则与神经模型的迭代优化互相促进，收敛快（3-5轮EM）。

## 7. 优点

- **统一框架**：将符号推理和神经表示学习统一到变分EM框架下，目标一致，优于以往独立组合的方法。
- **可解释性**：通过规则分解和权重恢复，能生成显式的支持路径和置信度分数，提供两种解释模式。
- **高效推理**：逻辑分解避免指数搜索，复杂度线性于规则长度，支持大规模KG。
- **鲁棒性强**：在低资源、不同稀疏程度的数据集上均表现优异。
- **实验充分**：覆盖多尺度、多语言、多场景，对比方法全面。

## 8. 不足与局限

- **多KG扩展限制**：目前仅设计用于两个KG的对齐，扩展到多个KG需迭代配对，可能效率低。
- **缺乏对神经模型本身的深度消融**：仅用了两种神经模型（Dual-AMN和LightEA），未测试更弱的嵌入器或不同架构的影响。
- **对长规则置信度偏低**：由于置信度是乘积形式，长规则置信度自然衰减，可能限制长距离依赖的利用。
- **未在非常大规模（如千万实体）上验证**：最大DBP1M约100万实体，更大规模的性能和效率未知。
- **依赖种子对齐质量**：低资源下，种子极少时符号模型初始推理可能不准，论文仅展示了整体鲁棒性，未剖析边界情况。

（完）
