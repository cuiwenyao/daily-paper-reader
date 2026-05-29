---
title: "Cognitive Mirrors: Exploring the Diverse Functional Roles of Attention Heads in LLM Reasoning"
title_zh: 认知镜像：探索LLM推理中注意力头的多样功能角色
authors: "Xueqi Ma, Jun Wang, Yanbei Jiang, Sarah Monazam Erfani, Tongliang Liu, James Bailey"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=EBwfFrw5VA"
tags: ["query:ns-xai"]
score: 8.0
evidence: 探索注意力头角色以解释LLM推理
tldr: 大型语言模型的内部机制仍不透明。本文提出一种新颖的可解释性框架，通过引入CogQA数据集和多标签探针方法，系统分析注意力头在推理中的多样功能角色。实验揭示了注意头在检索、逻辑推理等认知功能中的分工，为理解LLM推理行为提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1304, \"height\": 930}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 731}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 377}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1308, \"height\": 467}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1307, \"height\": 669}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1310, \"height\": 675}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1310, \"height\": 663}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1309, \"height\": 663}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1305, \"height\": 855}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebwffrw5va/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1309, \"height\": 663}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 537}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1375, \"height\": 303}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1375, \"height\": 307}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1303, \"height\": 321}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1473, \"height\": 620}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1470, \"height\": 548}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 368}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1376, \"height\": 402}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebwffrw5va/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1547, \"height\": 1017}]"
motivation: LLM内部机制不透明，理解注意力头角色对提升推理能力至关重要。
method: 提出可解释性框架，构建CogQA数据集（链式思维子问题），应用多标签探针分析注意力头功能。
result: 成功识别注意力头在推理中的不同认知功能角色，如检索和逻辑推理。
conclusion: 所提框架有效解释LLM推理机制，有助于改进模型。
---

## Abstract
Large language models (LLMs) have achieved state-of-the-art performance in a variety of tasks, but remain largely opaque in terms of their internal mechanisms. Understanding these mechanisms is crucial to improve their reasoning abilities. Drawing inspiration from the interplay between neural processes and human cognition, we propose a novel interpretability framework to systematically analyze the roles and behaviors of attention heads, which are key components of LLMs. We introduce CogQA, a dataset that decomposes complex questions into step-by-step subquestions with a chain-of-thought design, each associated with specific cognitive functions such as retrieval or logical reasoning. By applying a multi-label probing method, we identify the attention heads responsible for these functions. Our analysis across multiple LLM families reveals that attention heads exhibit functional specialization, characterized as cognitive heads. These cognitive heads exhibit several key properties: they are universally sparse, and vary in number and distribution across different cognitive functions, and they display interactive and hierarchical structures.  We further show that cognitive heads play a vital role in reasoning tasks—removing them leads to performance degradation, while augmenting them enhances reasoning accuracy. These insights offer a deeper understanding of LLM reasoning and suggest important implications for model design, training and fine-tuning strategies.

---

## 论文详细总结（自动生成）

# 论文《Cognitive Mirrors: Exploring the Diverse Functional Roles of Attention Heads in LLM Reasoning》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）虽然性能卓越，但其内部机制（尤其是注意力头的角色）仍然高度不透明。理解这些机制对于提升LLM的推理能力至关重要。
- **背景与启发**：人脑在解决复杂推理任务时会激活多个专门化的脑区（如额叶负责知识回忆、布罗卡区负责语义处理、顶叶和前额叶负责高阶推理）。作者假设LLM中的注意力头也可能扮演类似的专门化功能角色，但现有研究多集中在简单任务或单一功能上，缺乏针对复杂多步推理场景的系统性分析。
- **核心问题**：LLM中的注意力头是否具有与人类认知功能对应的功能专门化？如何识别这些“认知头”，并验证它们在推理中的因果作用？

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出“认知镜像”框架，通过构建认知标注的问答数据集，利用多类探测方法将注意力头的激活模式与人类认知功能（如检索、数学计算、逻辑推理等）对齐，从而识别功能专门化的“认知头”。
- **关键技术细节**：
  1. **CogQA数据集构建**：
     - 从AQuA、CREAK、ECQA、e-SNLI、GSM8K等推理基准中抽取750个问题，采用GPT-4o进行链式思维分解，生成子问题-答案-认知功能三元组。
     - 经过两阶段人工验证（子问题逻辑正确性、认知标签准确性）和自动答案校验（o4-mini模型），最终得到570个主问题、3402个子问题，每子问题标注8种认知功能之一（检索、知识回忆、语义理解、句法理解、数学计算、逻辑推理、推断、决策）。
  2. **注意力头激活特征提取**：
     - 对于每个子问题，将之前子问题和答案作为上下文输入LLM，生成答案token。
     - 提取所有层所有头的输出值向量，并选取top-5语义重要token的平均值作为该头的特征。
     - 额外加入对应层的平均激活作为辅助特征，形成增强特征向量。
  3. **多类探测训练与头重要性计算**：
     - 构建探测数据集：\( D_{\text{probe}} = \{ (\bar{x}'_{ml}, c_i) \} \)，其中c为认知函数标签。
     - 训练一个两层MLP（先线性降维至64维，再全连接至512维，最后输出8类）进行多分类。
     - 使用梯度×激活方法计算每个头对每个功能类的重要性分数：\( I^{(c)}_j = \mathbb{E}_{(\bar{x},c)}[ \frac{\partial \hat{y}_c}{\partial \bar{x}_j} \cdot \bar{x}_j ] \)。
     - 根据重要性排序，选择肘点前的头作为“认知头”。
  4. **干预验证**：
     - **负向干预**：将特定认知头的输出乘以小因子ε（如0.001）进行抑制，观察下游任务性能变化。
     - **正向干预**：计算正确/错误样本的激活方向差异，沿该方向偏移激活（\( x \leftarrow x + \alpha \sigma \cdot \text{dir} \)）以增强对应功能。
     - 评估指标包括COMET、BLEU、ROUGE、语义相似度、准确率。

## 3. 实验设计

- **数据集/场景**：
  - **主数据集**：CogQA（570主问，3402子问），用于识别和验证认知头。
  - **下游任务**：
    - 数学任务：GSM8K_100（GSM8K中100个数学题样本）。
    - 检索任务：Extractive_QA（49个从段落中直接提取答案的QA对，由GPT-4o生成）。
- **Benchmark与对比方法**：
  - 对比掩码**认知头** vs 掩码**等量随机头**的性能差异。
  - 交叉掩码实验：掩码检索头测试知识回忆，反之亦然。
  - 层次结构分析：掩码低级功能头（如检索、知识回忆）观察对高阶功能（如决策）的影响。
- **对比模型**：覆盖3个LLM家族、6个不同规模模型：Llama3.1-8B-instruct、Llama3.2-3B-instruct、Qwen3-8B、Qwen3-4B、Yi-1.5-9B、Yi-1.5-6B。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅在附录A.3提到MLP训练使用Adam优化器、学习率1e-4、100 epochs，但未涉及具体硬件配置。这部分信息缺失。

## 5. 实验数量与充分性

- **实验组数**：
  - **认知头识别**：在6个模型上分别绘制8种功能的重要性热力图，共48张图（部分见附录）。
  - **掩码干预实验**：表1展示6个模型×8个功能×2种掩码（认知vs随机）的COMET和准确率，共96组对比。
  - **交叉掩码**（表2）：2个模型×2个功能×2种掩码，共8组。
  - **掩码数量消融**（图3）：在Llama3.1-8B上，4种功能×4种掩码数量，共16条曲线。
  - **层次结构**（表3）：掩码一组低级头（多种组合）对高阶功能的影响，4行结果。
  - **下游任务干预**（表4）：2个任务×（基础+负向+正向干预）×6个模型，约48组结果。
  - **消融token选择**（附录A.9表8）：不同token策略对比。
- **充分性评价**：实验覆盖多个模型家族和规模，包含负向与正向干预、交叉验证，设计较为系统。但下游任务仅涉及数学和检索两类，未能覆盖所有8种认知功能；每个任务样本量较小（GSM8K_100和49个Extractive_QA），可能不足以代表全场景。实验整体充分且结果清晰，但泛化性有待扩大数据集验证。

## 6. 主要结论与发现

1. **存在认知头**：在多个LLM中均发现与特定认知功能高度相关的注意力头，这些头具有**稀疏性**（占比<7%）、**普遍性**（跨架构一致）和**层次化分布**（检索头集中在中层，数学头集中在高层）。
2. **因果重要性**：掩码认知头导致对应功能性能大幅下降（可达准确率降至0），而掩码等量随机头几乎无影响；交叉掩码进一步验证功能专门性。
3. **功能聚类**：PCA分析显示同类认知头（如推理、推断、决策）在潜在空间中聚集，数学头构成独立簇，类似人脑功能区域。
4. **层次结构**：低级功能头（检索、知识回忆）的缺失会严重损害后续高阶功能（决策、推断），表明LLM内部存在从基础信息处理到复杂推理的层级依赖。
5. **可增强性**：沿认知功能方向正向激活认知头可提升对应任务准确率（如检索任务提升5-10%），表明认知头是可操控的功能单元。

## 7. 优点

- **跨学科视角**：将认知科学概念引入LLM可解释性，构建了具有认知标签的数据集，为研究模型与人类认知对齐提供了新工具。
- **系统化方法论**：从数据构建、特征提取、功能识别到因果验证，形成完整框架；多类探测方法优于传统单类分析，能捕捉头与功能的多元关系。
- **验证充分**：同时采用负向和正向干预，既证明必要性也证明充分性；交叉掩码实验（表2）和层次结构分析（表3）进一步强化结论的鲁棒性。
- **跨模型泛化**：在6个不同规模/家族的模型上验证，支持结论的普遍性。
- **实用潜力**：识别认知头可为高效微调、模型编辑、动态推理等应用提供指导。

## 8. 不足与局限

- **认知功能分类不完备**：仅定义8种功能，可能无法覆盖LLM的全部认知能力（如创造力、类比推理等）。未来需要更细粒度的分类。
- **单标签限制**：每个子问题仅标注单一认知功能，但实际推理可能同时涉及多种功能；同样，一个注意力头也可能服务多个功能（本文未探讨）。
- **数据集规模与偏差**：CogQA仅570个主问题，来源为5个英文推理基准，可能引入领域偏差，且未覆盖多语言或更宽泛的常识场景。
- **算力信息缺失**：未报告实验的GPU型号、数量、时间等，不利于重复和成本评估。
- **下游任务验证有限**：仅测试了数学和检索两个任务，其余6种认知功能未在下游独立评估；样本量偏小（GSM8K_100、Extractive_QA）。
- **方法依赖LLM生成**：数据集构建依赖GPT-4o和o4-mini，可能继承模型自身的偏见或误差。虽经人工验证，但无法完全消除。
- **实际应用未探索**：论文主要聚焦分析，未将认知头信息用于模型改进（如动态稀疏激活、结构微调等），作者也将其列为未来工作。

（完）
