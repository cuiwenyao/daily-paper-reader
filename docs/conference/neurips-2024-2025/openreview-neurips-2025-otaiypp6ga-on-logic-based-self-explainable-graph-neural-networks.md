---
title: On Logic-based Self-Explainable Graph Neural Networks
title_zh: 基于逻辑的自解释图神经网络
authors: "Alessio Ragno, Marc Plantevit, Céline Robardet"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OtAiYPP6GA"
tags: ["query:ns-xai"]
score: 8.0
evidence: 图神经网络的逻辑自解释，符号推理与神经网络结合
tldr: 图神经网络解释困难，现有方法多限于找出重要子图。本文提出基于逻辑的自解释图神经网络，直接从模型提取显式逻辑规则反映决策过程。虽为GNN，但其神经符号融合思想可直接迁移至大模型可解释推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1240, \"height\": 687}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 501}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 449}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1014, \"height\": 1237}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 595}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 1210}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1381, \"height\": 1984}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1375, \"height\": 2080}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1186, \"height\": 496}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1467, \"height\": 378}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1281, \"height\": 495}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 606, \"height\": 177}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1203, \"height\": 493}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 939, \"height\": 494}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 543}]"
motivation: 图神经网络决策过程难以解释，现有方法无法揭示贡献机制。
method: 提出逻辑规则提取框架，从GNN中推导显式逻辑规则作为解释。
result: 实验证明逻辑规则解释的准确性和可理解性。
conclusion: 逻辑规则可自解释GNN，为神经符号可解释性提供新方向。
---

## Abstract
Graphs are complex, non-Euclidean structures that require specialized models, such as Graph Neural Networks (GNNs), Graph Transformers, or kernel-based approaches, to effectively capture their relational patterns. This inherent complexity makes explaining GNNs decisions particularly challenging. Most existing explainable AI (XAI) methods for GNNs focus on identifying influential nodes or extracting subgraphs that highlight relevant motifs. However, these approaches often fall short of clarifying how such elements contribute to the final prediction. To overcome this limitation, logic-based explanations aim to derive explicit logical rules that reflect the model's decision-making process. Current logic-based methods are limited to post-hoc analyzes and are predominantly applied to graph classification, leaving a significant gap in intrinsically explainable GNN architectures. In this paper, we explore the potential of integrating logic reasoning directly into graph learning. We introduce LogiX-GIN, a novel, self-explainable GNN architecture that incorporates logic layers to produce interpretable logical rules as part of the learning process. Unlike post-hoc methods, LogiX-GIN provides faithful, transparent, and inherently interpretable explanations aligned with the model's internal computations. We evaluate LogiX-GIN across several graph-based tasks and show that it achieves competitive predictive performance while delivering clear, logic-based insights into its decision-making process.

---

## 论文详细总结（自动生成）

# 基于逻辑的自解释图神经网络（LogiX-GIN）论文总结

## 1. 核心问题与整体含义（研究动机和背景）

**研究动机**：图神经网络（GNN）在节点分类、图分类等任务中表现优异，但其消息传递机制导致决策过程难以解释，限制了在医疗、金融等高风险领域的应用。现有可解释AI方法多为事后解释（post-hoc），如识别重要节点/子图，但无法阐明这些元素如何影响最终预测；且事后解释常与模型内部推理不一致，产生误导性解释。

**核心问题**：缺乏**内在可解释的GNN架构**，能够直接、忠实地以逻辑规则形式揭示模型决策过程。现有逻辑解释方法要么是事后分析（如GLGExplainer、GraphTrail），要么依赖决策树蒸馏，无法实现自解释。

**论文目标**：提出**LogiX-GIN**，第一个将逻辑推理直接集成到GNN架构中的自解释模型，使其在训练过程中就能产出可解释的逻辑规则（基于分级模态逻辑GML），且规则与模型内部计算完全对齐。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
基于理论结果：某些GNN可以表示分级模态逻辑（GML）命题。论文反向设计：构建强制符合GML格式的GNN，使每层的输出可转化为GML公式，从而提取显式逻辑规则。

### 关键技术细节

- **基础架构**：采用图同构网络（GIN）作为基础，因为其求和聚合函数天然支持计数操作，符合GML的计数语义。每层LogiX-GIN执行：
  - **求和聚合**：`a_v = Σ_{u∈N(v)∪{v}} h_u^(k-1)`（设置ϵ=0以匹配GML计数）。
  - **二值化函数β**：使用**参数化傅里叶阶跃函数**将聚合后的整数值转化为二进制激活，激活条件为落在可学习的区间内。公式：
    ```
    β(a) = clamp( (1/2) * ( Σ_{i=0}^{τ} sin((2i+1)(a⊙W̃+b̃))/(2i+1) / Σ_{i=0}^{τ} sin((2i+1)π/2)/(2i+1) + 1 ), 0, 1 )
    ```
    其中W̃、b̃为学习参数，控制区间宽度和位移。
  - **逻辑变换层λ**：采用类似TELL的非负权重线性层+sigmoid激活：`h_v = σ(ã_v W⁺ + b / τ)`。由于权重非负，该层可直接转换为析取范式（DNF）逻辑规则。

- **预处理**：连续输入特征通过可学习阈值自动二值化。

- **多层训练挑战**：sigmoid激活在多层中导致梯度消失。为此采用**知识蒸馏预训练策略**：
  1. 训练一个教师GIN模型（使用Gumbel-sigmoid鼓励二值化表示）。
  2. 将教师每层隐藏状态作为目标，逐层预训练LogiX-GIN的前半程。
  3. 后半程使用标准监督学习微调整个模型。

- **可解释性增强**：**后训练剪枝**：逐层反向施加Hoyer正则化（L1/L2比），促进权重稀疏化，减少规则复杂度。

- **解释形式**：
  - 逐层规则：每层输出可解析出GML公式。
  - 全局规则：最后一层规则结合子图同构合并，得到全局模式。
  - 节点归因：根据规则激活定位关键节点。

## 3. 实验设计

### 数据集
共10个数据集，覆盖合成图和真实世界分子图、蛋白质图、节点分类：
- **图分类（7个）**：BA2Motifs, BAMultiShapes, BBBP, MUTAG, NCI1, PROTEINS, Mutagenicity
- **节点分类（3个）**：BaShapes, BaCommunity, TreeGrid

### 基准方法
- **黑盒基准**：标准GIN模型（5层+readout+MLP）
- **自解释GNN对比**：PiGNN, GIB, KerGNN, GNAN（表2）
- **逻辑解释对比**：GraphTrail（事后逻辑方法）
- **事后可解释性对比**：GNNExplainer, PGExplainer, Integrated Gradients, SubgraphX, GStarX（节点归因评估）
- **消融实验**：剪枝策略比较（逐层剪枝 vs 全体剪枝）

### 评估指标
- 分类准确率（平均±标准差，10次随机种子）
- 忠实度（Fidelity）：移除重要节点后预测改变的比例
- 规则对齐度（Alignment）：规则激活与模型预测的一致性
- 规则复杂度：非零权重数量、规则数量

## 4. 资源与算力

论文明确说明（Appendix I）：
- **硬件**：Intel Core i9-10900K CPU @ 3.70GHz + NVIDIA GeForce RTX 4090 GPU
- **软件**：PyTorch, PyTorch-Geometric
- **训练时间**：Table 6给出各数据集GIN和LogiX-GIN的平均每次训练时间（毫秒级），例如：
  - BA2Motifs: GIN 2727ms, LogiX-GIN 6672ms
  - NCI1: GIN 1695ms, LogiX-GIN 49647ms（最耗时）
- **未说明**：具体使用多少GPU数量（推测单卡）、总训练时长未汇总，但论文提供了详细的超参数配置（Appendix I Tables 4-5）。

## 5. 实验数量与充分性

### 实验数量
- **主要性能比较**：10个数据集上对比黑盒GIN（表1）+ 7个图分类数据集上对比4种自解释模型（表2）。
- **全局规则比较**：4个数据集（BA2Motifs, BAMultiShapes, MUTAG, Mutagenicity）对比GraphTrail（图1）。
- **逐层规则分析**：所有数据集展示规则数量分布（图3）和激活分布（图8）。
- **节点归因评估**：7个图分类数据集对比5种事后方法和2种自解释方法（图6，Fidelity指标）。
- **消融实验**：2个数据集（BBBP, BA2Motifs）上比较剪枝策略（表3、表7）。
- **统计验证**：所有实验均报告10个随机种子的均值和标准差，确保统计意义。

### 充分性评价
- **客观性**：充分考虑了不同难度、不同类型（合成、分子、蛋白质）的数据集，覆盖节点分类和图分类。
- **公平性**：与多个主流自解释模型和事后方法对比；超参数通过网格搜索选择最佳验证集组合；重复10次减少随机性。
- **不足**：部分数据集（如BAMultiShapes）上GraphTrail因计算时间过长无法运行，未做完全对比；节点归因评估仅用Fidelity一个指标，可能不够全面；未在更大规模图（如OGBN）上测试。

## 6. 主要结论与发现

1. **预测性能**：LogiX-GIN在10个任务上的准确率与黑盒GIN差距在3%以内（表1），在7个图分类数据集中5个达到自解释模型最优（表2），表明加入逻辑约束对性能影响有限。
2. **忠实解释**：LogiX-GIN的解释完全对齐其内部计算（Alignment=1.0，如表1下方图示），而事后方法GraphTrail难以保证。
3. **规则层次结构**：早期层捕获低级特征（如原子类型、连接数），后期层组合成更高级概念（如功能团计数）。模型通常只使用2-3层，冗余层可被剪枝（图2、图3）。
4. **规则复杂性可控**：剪枝显著减少非零权重（如BA2Motifs减少83%），同时几乎不损失性能（表7）。
5. **可解释性价值**：规则清晰展示决策逻辑（如“图中至少9个节点激活某特征→有毒”），且揭示“删除部分节点不一定改变预测”的计数决策本质。

## 7. 优点（亮点）

- **首创性**：第一个将逻辑推理直接嵌入GNN训练的自解释架构，区别于所有事后或蒸馏方法。
- **理论扎实**：以GML为逻辑基础，通过构造证明每层输出均可转换为GML公式（Proposition 1）。
- **多层训练方案**：用蒸馏预训练克服sigmoid梯度消失，使得深层逻辑网络可行。
- **规则简洁化**：傅里叶二值化+Hoyer剪枝自动学习计数区间并压缩规则，提升可读性。
- **多粒度解释**：提供逐层规则、全局子图模式、节点归因，适应不同解释需求。
- **开源代码**：提供完整可复现实现。

## 8. 不足与局限

- **忽略边特征**：模型仅使用节点特征和拓扑，不能利用边属性（如化学键类型）。
- **训练复杂度高**：蒸馏预训练+剪枝多阶段训练，计算成本远高于标准GNN（如NCI1上LogiX-GIN训练时间约50秒/次，而GIN仅1.7秒）。
- **表达能力受限**：仅能表达GML能描述的模式，无法处理高阶逻辑或全局关系（如结构对称性）。
- **可解释性依赖特征语义**：当节点特征是连续值或浮点向量时，阈值化后的布尔谓词可能失去语义可解释性（如分子中原子类型具有明确含义，但某些抽象特征则不然）。
- **实验规模有限**：未在大型图数据集（如OGB-Mol）或异构图、动态图评测；节点归因评估仅用Fidelity一种指标，可能未全面反映解释质量。
- **剪枝策略潜在风险**：逐层剪枝可能过度简化模型，使某些必要规则被误删（表7中Mutagenicity等数据集剪枝后非零权重下降不多，表明规则保留较多）。

（完）
