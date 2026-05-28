---
title: On Logic-based Self-Explainable Graph Neural Networks
title_zh: 基于逻辑的自解释图神经网络
authors: "Alessio Ragno, Marc Plantevit, Céline Robardet"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OtAiYPP6GA"
tags: ["query:ns-xai"]
score: 8.0
evidence: 基于逻辑的自解释图神经网络
tldr: 图神经网络解释性面临挑战，现有方法仅识别重要子图而缺乏决策逻辑。本文提出基于逻辑的自解释GNN，通过推导显式逻辑规则来反映模型决策过程。该方法在多个图数据集上不仅提供了可解释规则，还保持了预测性能，实现了准确性与可解释性的平衡。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1240, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1014, \"height\": 1237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 1210, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1381, \"height\": 1984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-otaiypp6ga/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1375, \"height\": 2080, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1186, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1467, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1281, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 606, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1203, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 939, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-otaiypp6ga/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 543, \"label\": \"Table\"}]"
motivation: 现有GNN解释方法仅识别子图，未揭示决策逻辑。
method: 使用逻辑规则形式化模型推理过程，实现自解释。
result: 在标准图数据集上同时保持了高准确度和可解释性。
conclusion: 逻辑规则是解释GNN决策的一种有效且忠实的方式。
---

## Abstract
Graphs are complex, non-Euclidean structures that require specialized models, such as Graph Neural Networks (GNNs), Graph Transformers, or kernel-based approaches, to effectively capture their relational patterns. This inherent complexity makes explaining GNNs decisions particularly challenging. Most existing explainable AI (XAI) methods for GNNs focus on identifying influential nodes or extracting subgraphs that highlight relevant motifs. However, these approaches often fall short of clarifying how such elements contribute to the final prediction. To overcome this limitation, logic-based explanations aim to derive explicit logical rules that reflect the model's decision-making process. Current logic-based methods are limited to post-hoc analyzes and are predominantly applied to graph classification, leaving a significant gap in intrinsically explainable GNN architectures. In this paper, we explore the potential of integrating logic reasoning directly into graph learning. We introduce LogiX-GIN, a novel, self-explainable GNN architecture that incorporates logic layers to produce interpretable logical rules as part of the learning process. Unlike post-hoc methods, LogiX-GIN provides faithful, transparent, and inherently interpretable explanations aligned with the model's internal computations. We evaluate LogiX-GIN across several graph-based tasks and show that it achieves competitive predictive performance while delivering clear, logic-based insights into its decision-making process.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

图神经网络（GNN）在处理图结构数据方面表现出色，但其复杂的消息传递机制导致模型决策难以解释。现有可解释AI（XAI）方法大多为事后（post-hoc）分析，例如识别重要节点或子图，但未能揭示这些元素如何影响最终预测。逻辑驱动的解释方法通过提取显式逻辑规则来反映模型的决策过程，但已有工作局限于事后分析或基于蒸馏，缺乏内在可解释的GNN架构。

本文旨在填补这一空白，提出一种**自解释（self-explainable）的GNN架构**，将逻辑推理直接集成到学习过程中，从而产生与模型内部计算对齐的忠实、透明且可理解的逻辑规则。

### 2. 方法论：核心思想、关键技术细节

**核心思想**：基于GIN（Graph Isomorphism Network）框架，通过引入可学习的二值化函数和受约束的线性层，使每一层的输出可转换为**分级模态逻辑（Graded Modal Logic, GML）**公式。GML支持计数操作，天然适合图上的局部模式表示。

**关键组件**：
- **聚合函数**：使用求和聚合（等价于GIN中ϵ=0的情况），得到整数计数向量。
- **可学习二值化函数 β**：采用参数化的Fourier阶梯函数，将整数计数映射到区间[0,1]，激活条件对应特定计数区间，从而得到可解释的布尔文字。
- **逻辑转换层 λ**：采用非负权重约束的线性层+sigmoid激活（类似TELL），保证单调性，从而允许直接从参数中提取析取范式（DNF）规则。
- **知识蒸馏预训练**：因sigmoid激活堆叠导致梯度消失，先训练一个Gumbel-sigmoid激活的GIN教师模型，逐层蒸馏初始化LogiX-GIN参数，然后微调。
- **后训练剪枝**：应用Hoyer正则化逐层优化权重稀疏性，减小规则复杂度。

**提取规则**：从每一层可提取GML公式；全局规则通过分析最后一层激活模式获得；节点归因可通过规则涉及的节点集合直接得到。

### 3. 实验设计

- **数据集**：包含7个图分类数据集（BA2Motifs, BAMultiShapes, MUTAG, Mutagenicity, NCI1, PROTEINS, BBBP）和3个节点分类数据集（BaShapes, BaCommunity, TreeGrid），覆盖合成图、分子图、蛋白质图。
- **基准对比**：
  - 黑盒模型：相同架构的GIN（不含逻辑层）。
  - 自解释模型：PiGNN, GIB, KerGNN, GNAN。
  - 事后可解释方法（节点归因评估）：GNNExplainer, PGExplainer, Integrated Gradients, SubgraphX, GStarX。
- **评估指标**：分类准确率、忠实度（Fidelity，基于节点删除后预测变化比例）、规则对齐度（模型预测与规则激活的准确率）。

### 4. 资源与算力

论文在“超参数、资源与可复现性”部分（附录I）说明：使用一台配备**Intel Core i9-10900K CPU @ 3.70GHz**和**NVIDIA GeForce RTX 4090 GPU**的机器。训练时间方面，提供了GIN和LogiX-GIN的平均训练时长（毫秒级），例如MUTAG上GIN约279ms，LogiX-GIN约797ms；PROTEINS上GIN约1872ms，LogiX-GIN约11077ms。未提及多GPU或分布式训练。

### 5. 实验数量与充分性

- **主要实验**：在10个数据集上对比了LogiX-GIN与黑盒模型的准确率（每种种子10次，报告均值±标准差），并与4种自解释模型对比。
- **消融实验**：在BBBP和BA2Motifs上比较了两种剪枝策略（逐层 vs 联合），以及剪枝前后规则复杂度/性能变化。
- **规则分析**：可视化了各层规则数量分布、激活百分比，并提供了全局规则提取与GraphTrail的定性比较（4个数据集）。
- **节点归因评估**：与5种事后方法和2种自解释模型对比Fidelity指标（6个数据集）。
- **整体充分性**：覆盖了多个领域、不同规模的数据集，进行了统计显著性检验，消融和对比充分。但部分实验限于图分类，节点分类仅测试了准确率。

### 6. 主要结论与发现

- LogiX-GIN在保持竞争性能的同时（在所有数据集上准确率下降不超过3%），在多个数据集上达到或超越现有自解释模型。例如BA2Motifs和BAMultiShapes上准确率100%。
- 规则提取忠实于模型内部计算（对齐度为1.0），而事后方法可能产生不完全一致的规则。
- 层级分析表明：早期层学习低层模式（如原子类型），后期层组合这些模式进行计数决策，解释模型如何使用冗余层（若后期层未使用可移除）。
- 剪枝能有效降低规则复杂度而不显著影响性能。

### 7. 优点

- **理论奠基**：基于Barceló等人关于GNN表达GML的结论，首次设计了可直接转换为GML公式的自解释GNN架构。
- **忠实性**：不同于事后方法，规则直接反映模型参数，保证忠实性。
- **多粒度解释**：可提供层内规则、全局规则、节点归因等多种形式。
- **鲁棒性**：通过蒸馏预训练克服了sigmoid梯度消失，剪枝策略维持性能。
- **实验全面**：覆盖多种数据集和对比方法，公开代码。

### 8. 不足与局限

- **忽略边特征**：LogiX-GIN未利用边特征，限制了表达力。
- **训练复杂性**：需要蒸馏预训练和逐层剪枝，计算成本较高；sigmoid二值化可能导致更大图上的训练不稳定。
- **可解释性限制**：当输入特征无明确语义时，对输入特征的阈值可能不直观。
- **逻辑表达力受限**：基于GML，无法处理更高级的推理（如一阶逻辑全局量化）。
- **评估偏倚**：节点归因评估（Fidelity）可能对自解释模型不公平，因为其解释方式与事后方法不同。
- **仅支持图分类和节点分类**：未验证链接预测等任务。

（完）
