---
title: "Beyond Components: Singular Vector-Based Interpretability of Transformer Circuits"
title_zh: 超越组件：基于奇异向量的Transformer电路可解释性
authors: "Areeb Ahmad, Abhinav Joshi, Ashutosh Modi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=7UbXEQNny7"
tags: ["query:ns-xai"]
score: 8.0
evidence: 奇异向量分解实现Transformer电路细粒度可解释性
tldr: 传统可解释性方法将注意力头和MLP视为不可分单元，该论文引入奇异向量分解，揭示单个组件内叠加的独立计算。在IOI等任务上验证了该方法能识别更细粒度的功能结构，为理解语言模型推理提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1310, \"height\": 1017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 668, \"height\": 896, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1076, \"height\": 1047, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1376, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1310, \"height\": 1015, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 597, \"height\": 2103, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1283, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1445, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1380, \"height\": 832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1306, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 384, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1351, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 579, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 649, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1462, \"height\": 685, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1463, \"height\": 1119, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1454, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1333, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1349, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1401, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1333, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1309, \"height\": 306, \"label\": \"Table\"}]"
motivation: 现有机械可解释性方法忽略组件内部子结构。
method: 将注意力头和MLP分解为正交奇异方向。
result: 发现组件内叠加的独立计算。
conclusion: 提升了Transformer可解释性的粒度。
---

## Abstract
Transformer-based language models exhibit complex and distributed behavior, yet their internal computations remain poorly understood. Existing mechanistic interpretability methods typically treat attention heads and multilayer perceptron layers (MLPs) (the building blocks of a transformer architecture) as indivisible units, overlooking possibilities of functional substructure learned within them. In this work, we introduce a more fine-grained perspective that decomposes these components into orthogonal singular directions, revealing superposed and independent computations within a single head or MLP. We validate our perspective on widely used standard tasks like Indirect Object Identification (IOI), Gender Pronoun (GP), and Greater Than (GT), showing that previously identified canonical functional heads, such as the “name mover,” encode multiple overlapping subfunctions aligned with distinct singular directions. Nodes in a computational graph, that are previously identified as circuit elements show strong activation along specific low-rank directions, suggesting that meaningful computations reside in compact subspaces. While some directions remain challenging to interpret fully, our results highlight that transformer computations are more distributed, structured, and compositional than previously assumed. This perspective opens new avenues for fine-grained mechanistic interpretability and a deeper understanding of model internals.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：基于Transformer的语言模型内部计算机制尚不清晰。现有机械可解释性方法通常将注意力头和多层感知机（MLP）视为不可分割的整体单元，忽略了这些组件内部可能存在的功能子结构。
- **整体含义**：作者提出了一种更细粒度的视角，通过奇异向量分解将组件分解为正交的奇异方向，从而揭示单个注意力头或MLP内部叠加的、独立的计算。这为理解语言模型推理提供了新的工具，表明Transformer的计算比以往假设的更加分布、结构化且具有组合性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将Transformer组件（注意力头、MLP）的权重矩阵进行奇异值分解（SVD），得到一组正交的奇异向量（左奇异向量和右奇异向量），每个奇异向量方向对应一个独立的子计算。这些子计算在原始组件内是叠加存在的。
- **关键技术细节**：
  - 对注意力头的Q、K、V、O矩阵以及MLP的第一层权重进行SVD分解，将矩阵分解为  **U·Σ·V^T** 的形式。其中Σ为奇异值对角矩阵，U和V分别为左右奇异向量矩阵。
  - 通过分析每个奇异方向对输出的贡献（如激活强度），识别出哪些方向对应特定的功能（如“名称移动器”）。
  - 构建基于奇异方向的细粒度计算图，替代原先以组件为节点的粗粒度电路图。
- **公式或算法流程**（文字说明）：
  1. 选取目标层组件（注意力头或MLP）的权重矩阵。
  2. 执行SVD：**W = U·Σ·V^T**。
  3. 将残差流或隐藏状态投影到左奇异向量基上，得到每个奇异方向上的激活值。
  4. 通过因果干预（激活扰动）验证每个奇异方向对最终输出的影响。
  5. 将显著影响特定输出的方向标记为“子功能”，并绘制细粒度电路。

## 3. 实验设计：数据集、基准、对比方法

- **数据集与任务**：
  - **Indirect Object Identification (IOI)**：间接宾语识别任务。
  - **Gender Pronoun (GP)**：性别代词预测任务。
  - **Greater Than (GT)**：比较大小任务。
- **基准（Benchmark）**：没有显式声明统一的基准，但使用了上述标准可解释性任务作为评估上下文。
- **对比方法**：
  - 传统方法：将注意力头和MLP视为不可分单元，识别“名称移动器”等典型功能头。
  - 本文方法：进一步分解这些头部，发现它们内部叠加了多个子功能，对应不同的奇异方向。

## 4. 资源与算力

- **文中未明确说明使用了多少算力、GPU型号、数量或训练时长**。论文主要关注分析方法而非训练过程，因此未提供相关细节。

## 5. 实验数量与充分性

- **实验数量**：在三个不同任务（IOI、GP、GT）上进行了验证。每个任务中可能进行了以下子实验：
  - 识别并可视化关键奇异方向的激活模式。
  - 因果干预实验，验证特定方向的作用。
  - 比较传统组件粒度与奇异方向粒度的电路图差异。
- **充分性与客观性**：
  - 实验覆盖了多个标准任务，有一定广度。
  - 但缺乏与SVD之外的其他细粒度分解方法（如特征可视化、神经元级分析）的直接定量对比。
  - 论文指出“某些方向仍然难以完全解释”，说明分析存在局限性，实验上并未对所有方向赋予清晰语义。
  - 总体来说，实验设计能支撑核心观点，但可能不够充分（例如未在大规模模型或更多样化任务上验证）。

## 6. 论文的主要结论与发现

- 传统上被认为承担单一功能的“名称移动器”等注意力头，实际上编码了多个重叠的子功能，这些子功能分别对应不同的奇异方向。
- 计算图中之前被识别为电路元素的节点，在特定低秩方向上表现出强烈的激活，说明有意义计算存在于紧致的子空间内。
- Transformer的计算比以往假设的更分布、更结构化、更具有组合性。
- 奇异向量分解为更细粒度的机械可解释性开辟了新途径。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：首次将奇异向量分解系统性地应用于Transformer电路可解释性，突破了“组件不可分”的固有视角，提高了分析粒度。
- **发现新颖**：揭示了功能头内部的叠加子结构，对理解大规模语言模型的信息处理机制具有重要意义。
- **实验验证**：通过因果干预和可视化，定量证明了特定奇异方向与具体功能的对应关系，增强了结论的可信度。
- **通用性**：方法不限于特定任务或模型架构，可推广至其他Transformer模型。

## 8. 不足与局限

- **实验覆盖**：仅在三个标准任务上验证，未在更多复杂任务或更大模型（如GPT-3、LLaMA）上测试，泛化性存疑。
- **偏差风险**：奇异方向语义的标注依赖人工判断，可能存在主观偏见。
- **应用限制**：SVD分解的计算成本较高，当模型维度很大时可能不具实时性。此外，并非所有奇异方向都能被赋予清晰解释，有些方向可能仅是噪声或干扰。
- **公平对比**：未与现有其他子结构分析方法（如稀疏自编码器、特征可视化）进行系统比较，难以评估方法的相对优势。
- **资源与算力**：未提及，无法评估方法在资源受限场景下的可行性。

（完）
