---
title: "Cognitive Mirrors: Exploring the Diverse Functional Roles of Attention Heads in LLM Reasoning"
title_zh: 认知镜子：探索大语言模型推理中注意力头的多样化功能角色
authors: "Xueqi Ma, Jun Wang, Yanbei Jiang, Sarah Monazam Erfani, Tongliang Liu, James Bailey"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=EBwfFrw5VA"
tags: ["query:ns-xai"]
score: 8.0
evidence: 探索LLM推理中注意力头的功能角色
tldr: LLM内部推理机制尚不透明。本文受认知过程启发，提出CogQA数据集，将复杂问题分解为带认知功能标签（如检索、逻辑推理）的子问题，并通过多标签探针方法分析注意力头的角色。实验揭示不同类型注意力头在推理中的不同功能，为理解LLM推理提供了认知视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1304, \"height\": 930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 731, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1308, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1307, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1310, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1310, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1309, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1305, \"height\": 855, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1309, \"height\": 663, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1375, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1375, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1303, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1473, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1470, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1376, \"height\": 402, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1547, \"height\": 1017, \"label\": \"Table\"}]"
motivation: LLM的推理机制不透明，需要从认知角度系统分析注意力头的功能。
method: 构建CogQA数据集，为每个子问题赋予认知功能标签，使用多标签探针分析注意力头。
result: 发现注意力头具有专门化功能，如检索、推理等，且这些功能与认知过程对应。
conclusion: 该框架揭示了LLM推理中的认知对应机制，为可解释性研究提供了新视角。
---

## Abstract
Large language models (LLMs) have achieved state-of-the-art performance in a variety of tasks, but remain largely opaque in terms of their internal mechanisms. Understanding these mechanisms is crucial to improve their reasoning abilities. Drawing inspiration from the interplay between neural processes and human cognition, we propose a novel interpretability framework to systematically analyze the roles and behaviors of attention heads, which are key components of LLMs. We introduce CogQA, a dataset that decomposes complex questions into step-by-step subquestions with a chain-of-thought design, each associated with specific cognitive functions such as retrieval or logical reasoning. By applying a multi-label probing method, we identify the attention heads responsible for these functions. Our analysis across multiple LLM families reveals that attention heads exhibit functional specialization, characterized as cognitive heads. These cognitive heads exhibit several key properties: they are universally sparse, and vary in number and distribution across different cognitive functions, and they display interactive and hierarchical structures.  We further show that cognitive heads play a vital role in reasoning tasks—removing them leads to performance degradation, while augmenting them enhances reasoning accuracy. These insights offer a deeper understanding of LLM reasoning and suggest important implications for model design, training and fine-tuning strategies.

---

## 论文详细总结（自动生成）

# 认知镜子：探索大语言模型推理中注意力头的多样化功能角色——论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在多种任务上表现卓越，但其内部推理机制仍然不透明。理解这些机制对于提升模型推理能力至关重要。
- **核心问题**：LLM中的注意力头是否像人类认知系统一样存在功能专门化？这些注意力头在复杂推理中承担何种角色？如何系统性地识别和分析它们？
- **整体含义**：论文提出一个新颖的可解释性框架，将LLM的注意力头与人类认知功能（如检索、逻辑推理、数学计算等）进行对齐。通过构建认知标注的数据集和多标签探针方法，揭示注意力头的功能专门化、稀疏性、层次化组织等特性，为理解LLM推理的认知基础提供了新视角。

## 2. 论文提出的方法论：核心思想与关键技术细节

### 2.1 核心思想
- 受人类大脑处理复杂问题时多个脑区协同工作的启发，假设LLM中的注意力头也承担专门化的认知功能。
- 通过**链式思维（CoT）** 将复杂问题分解为逐步的子问题，每个子问题对应单一认知功能，然后使用**多标签探针**识别哪些注意力头负责哪些功能。

### 2.2 关键技术细节
- **CogQA数据集构建**：
  - 从AQuA、CREAK、ECQA、e-SNLI、GSM8K五个推理基准中抽取750个问题，经GPT-4o分解为子问题，每个子问题附带答案和认知功能标签。
  - 经过两阶段人工验证（子问题逻辑一致性、认知标签正确性）和答案验证（GPT-o4-mini + 人工裁决），最终保留570个主问题、3402个子问题-答案-认知功能三元素组。
  - 认知功能分为低阶（检索、知识回忆、语义理解、句法理解）和高阶（数学计算、逻辑推理、推断、决策）共8类。

- **头部特征提取**：
  - 对于每个子问题，模型生成答案时提取所有注意力头的输出值向量。通过LLM选择答案中top-5语义重要token，对其头部激活取平均，并与该层平均激活拼接，形成增强特征。
  - 数据集按4:1划分为训练集和验证集。

- **多标签探针与头部重要性**：
  - 训练一个两层MLP分类器，以头部增强特征为输入，预测认知功能类别（8类）。
  - 使用**梯度×激活**方法计算每个头部对每个功能的贡献得分，形成重要性矩阵。排名靠前的头部被视为该功能的**认知头部**。
  - 通过**肘点法**确定每个功能的认知头部数量，确保头部选择是稀疏且有意义的。

## 3. 实验设计

### 3.1 使用的数据集与场景
- **主实验数据集**：CogQA（自行构建，570个主问题，3402个子问题），覆盖8种认知功能。
- **下游任务验证**：
  - **数学任务**：GSM8K_100（GSM8K的100个样本）。
  - **检索任务**：Extractive_QA（49个从段落中抽取答案的样本，由GPT-4o生成）。
- **模型家族**：LLaMA（3.1-8B-instruct, 3.2-3B-instruct）、Qwen（3-8B, 3-4B）、Yi（1.5-9B, 1.5-6B），共6个模型，覆盖不同规模和架构。

### 3.2 Benchmark与对比方法
- **基准（baseline）**：随机选择相同数量的头部进行干预（masking或enhancing），对比认知头部干预的效果。
- **主要对比**：
  - 负干预（masking头部输出，乘以小因子0.001）后，比较COMET、BLEU、ROUGE、语义相似度等指标的变化。
  - 正干预（沿功能方向增强激活）后，比较任务准确率的提升。
  - 额外对比：masking认知头部 vs. 随机头部；masking不同功能头部（检索 vs. 知识回忆）的交叉影响；不同token选择策略的消融实验。

### 3.3 评价指标
- 干预后模型输出与原始输出的匹配程度：BLEU > 0.8 或 ROUGE/语义相似度 > 0.6 视为“未受影响”，否则视为“受影响”，计算受影响样本比例（accuracy）。
- 对于下游数学任务，使用精确答案匹配；对于检索任务，检查答案是否出现在响应中。

## 4. 资源与算力

- **论文未明确说明使用的GPU型号、数量、训练时长等算力信息**。文中仅提到“我们使用推理”（We are working with inference only, compute resources is not the factor of any of our experiments），即主要实验基于已训练模型的推理阶段，探针分类器的训练开销相对较小，但具体硬件配置未给出。因此无法量化算力消耗。

## 5. 实验数量与充分性

- **实验数量**：
  - **认知头部识别**：在6个模型上都生成了8种功能的头部重要性热图，并统计了头部分布（Table 7）。
  - **负干预实验**：在6个模型上分别对每个功能进行masking（认知头部vs随机头部），报告了COMET和accuracy（Table 1）。
  - **交叉干预实验**：在2个模型上验证检索头部和知识回忆头部的特异性（Table 2）。
  - **层次结构实验**：mask低阶头部（检索、知识回忆等）观察对高阶功能（推断、决策等）的影响（Table 3）。
  - **下游任务实验**：在GSM8K_100和Extractive_QA上进行正/负干预，对比多个模型（Table 4）。
  - **消融实验**：比较不同token选择策略（first, last, meaning_first, top-k, full）对头部识别精度的影响（Table 8）。

- **充分性评价**：
  - **正面**：覆盖多模型、多功能、多干预方式；有随机基线对比；有交叉验证；有下游任务验证。实验设计较为全面，结论可信度较高。
  - **不足**：未报告实验的统计显著性（无误差条或置信区间）；未进行多次重复实验以避免随机性；未对比其他头部重要性方法（如基于剪枝、基于注意力权重的方法），仅与随机基线对比。但作为可解释性分析论文，这些不足在可接受范围内。

## 6. 论文的主要结论与发现

1. **注意力头存在功能专门化（认知头部）**：通过多标签探针成功识别出与8种认知功能对应的特定注意力头，且这些头部在多个模型家族中具有一致性。
2. **认知头部的性质**：
   - **稀疏性**：每种功能仅激活少量高重要性头部（<7%总头部），如数学计算头部最少，推断头部最多。
   - **层次化组织**：低阶功能头部（如检索）主要分布在中层，高阶功能头部（如数学）多分布在后层；头部之间存在层级依赖关系——mask低阶头部会显著影响高阶功能表现。
   - **功能聚类**：PCA可视化显示，相似功能（推理、推断、决策）的头部聚集在一起，数学计算形成独立簇，类似人脑功能分区。
3. **因果验证**：mask认知头部导致对应功能大幅下降（Accuracy常降至0），而mask随机头部几乎无影响；增强认知头部激活可提升下游任务准确率。
4. **跨模型普适性**：上述现象在LLaMA、Qwen、Yi三个家族的不同规模模型上一致出现，表明认知功能组织是LLM的内在特性。

## 7. 优点

- **方法创新**：首次将人类认知功能分类系统引入LLM注意力头分析，建立了可解释性框架与认知科学的桥梁。CogQA数据集是首个细粒度认知标注的推理分解数据集。
- **多标签探针设计**：区别于以往单功能探针，支持“多对多”映射，更符合实际模型中头部可能参与多种功能的现实。
- **全面的因果干预**：通过mask和enhance两种方式验证头部功能的重要性，增强了结论的可靠性。
- **跨模型验证**：在6个不同架构/规模的模型上重复实验，增强了结论的泛化性。
- **层次结构与聚类分析**：揭示了LLM内部与人类认知类似的模块化、层次化组织，为模型理解提供了新颖视角。

## 8. 不足与局限

- **认知功能覆盖不完整**：仅定义了8种功能，可能不足以涵盖LLM的所有推理能力。未来可扩展更细粒度分类（如情感推理、类比推理等）。
- **单一标签假设**：每个子问题仅标注一个认知功能，但实际推理可能同时涉及多个功能；同样，每头假设对应单一功能，但实际可能存在多头共享或上下文依赖的角色。论文未充分处理这些复杂性。
- **数据规模与来源偏差**：CogQA仅570个主问题，且来自5个英文推理数据集，可能存在领域和语言偏差。人工验证虽多轮但受限于标注者主观性。
- **统计显著性缺失**：未报告误差条或置信区间，实验结果的稳定性未充分展示。
- **应用层面未深入**：论文定位为分析性工作，虽提及可指导模型设计（动态激活、coT提示优化、微调策略），但未实际演示这些应用。应视为未来方向。
- **计算资源未报告**：无法评估实验复现成本。探针训练细节虽给出，但未提及实际硬件环境。

**（完）**
