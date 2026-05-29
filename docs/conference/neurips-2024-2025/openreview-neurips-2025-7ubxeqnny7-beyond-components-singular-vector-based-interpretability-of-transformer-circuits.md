---
title: "Beyond Components: Singular Vector-Based Interpretability of Transformer Circuits"
title_zh: 超越组件：基于奇异向量的Transformer电路可解释性
authors: "Areeb Ahmad, Abhinav Joshi, Ashutosh Modi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=7UbXEQNny7"
tags: ["query:ns-xai"]
score: 7.0
evidence: Transformer电路的细粒度可解释性
tldr: 该论文提出基于奇异向量分解的细粒度解释方法，将注意力头和MLP分解为正交方向，揭示其中叠加的独立计算。在标准任务上验证了方法的有效性，提升了大模型可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1310, \"height\": 1017}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 668, \"height\": 896}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1076, \"height\": 1047}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1376, \"height\": 724}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1310, \"height\": 1015}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 597, \"height\": 2103}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1283, \"height\": 760}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1445, \"height\": 268}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1380, \"height\": 832}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1306, \"height\": 518}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7ubxeqnny7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 384}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1351, \"height\": 223}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 579, \"height\": 221}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 649, \"height\": 308}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1462, \"height\": 685}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1463, \"height\": 1119}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1454, \"height\": 264}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1333, \"height\": 183}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1349, \"height\": 264}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1401, \"height\": 222}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1333, \"height\": 344}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7ubxeqnny7/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1309, \"height\": 306}]"
motivation: 现有机械可解释性将注意力头和MLP视为不可分割单元，忽略了内部子结构。
method: 将组件分解为奇异方向，揭示叠加的独立计算。
result: 在IOI等任务上发现了头内的功能子结构。
conclusion: 细粒度分解为理解Transformer计算提供了新工具。
---

## Abstract
Transformer-based language models exhibit complex and distributed behavior, yet their internal computations remain poorly understood. Existing mechanistic interpretability methods typically treat attention heads and multilayer perceptron layers (MLPs) (the building blocks of a transformer architecture) as indivisible units, overlooking possibilities of functional substructure learned within them. In this work, we introduce a more fine-grained perspective that decomposes these components into orthogonal singular directions, revealing superposed and independent computations within a single head or MLP. We validate our perspective on widely used standard tasks like Indirect Object Identification (IOI), Gender Pronoun (GP), and Greater Than (GT), showing that previously identified canonical functional heads, such as the “name mover,” encode multiple overlapping subfunctions aligned with distinct singular directions. Nodes in a computational graph, that are previously identified as circuit elements show strong activation along specific low-rank directions, suggesting that meaningful computations reside in compact subspaces. While some directions remain challenging to interpret fully, our results highlight that transformer computations are more distributed, structured, and compositional than previously assumed. This perspective opens new avenues for fine-grained mechanistic interpretability and a deeper understanding of model internals.

---

## 论文详细总结（自动生成）

### 论文总结：Beyond Components: Singular Vector-Based Interpretability of Transformer Circuits

#### 1. 核心问题与整体含义
- **研究动机**：现有的机械可解释性方法将 Transformer 中的注意力头（Attention Heads）和 MLP 层视为不可分割的原子单元，忽略了这些组件内部可能存在的功能子结构。这类方法通过整个组件的激活或消融来推断功能，假设功能与组件边界对齐。
- **核心问题**：组件内部是否叠加了多个独立计算？能否在更细粒度的方向（direction）层面揭示这些子功能？
- **整体含义**：本文提出将注意力头和 MLP 分解为正交的奇异方向（singular directions），证明一个组件内部可以包含多个叠加且可解释的子功能。这颠覆了组件作为原子单元的传统观点，为机械可解释性提供了更精细的分析框架。

#### 2. 方法论
- **核心思想**：将 Transformer 组件的权重矩阵（包括偏置）统一表示为增广矩阵，再进行奇异值分解（SVD），得到正交方向。每个方向可视为一个独立的计算轴。通过优化可学习的掩码（mask）来识别哪些方向对特定任务至关重要。
- **关键技术细节**：
  - **统一线性表示**：将 QK、OV、MLP 的输入/输出投影矩阵增广（folding in biases），得到形如 `W_aug` 的矩阵，便于统一进行 SVD。
  - **SVD 分解**：对每个组件的 `W_aug` 进行 SVD：`W_aug = U Σ V^T`，其中 U 和 V 是正交基，Σ 是对角奇异值矩阵。每一对奇异向量（左、右）对应一个方向。
  - **可学习掩码**：引入对角掩码矩阵 M，通过优化 `fW_aug = U Σ M V^T` 来控制每个方向的贡献。对于 QK 矩阵，仅保留主掩码部分，舍弃互补部分，以避免注意力内核冲突。
  - **优化目标**：`L_M = KL[p(y|x) || p_M(y|x)] + λ ||diag(M)||_1`，其中 KL 散度保证掩码模型的行为忠实于原始模型，L1 正则化促进掩码稀疏。优化时使用 clean 和 corrupted 输入的联合表示，以增强鲁棒性。
- **算法流程**（Algorithm 1）：
  1. 为所有组件构造 `W_aug` 并计算 SVD。
  2. 冻结模型参数，初始化可学习对角掩码 M。
  3. 对每个 batch，运行通过掩码构建的模型，计算 KL 散度 + L1 正则项。
  4. 梯度更新 M，重构权重 `fW_aug`。
  5. 返回学习到的掩码和重构权重。

#### 3. 实验设计
- **数据集与场景**：使用三个标准任务：
  - **间接宾语识别（IOI）**：基于 Wang et al. (2022)，预测间接宾语。
  - **性别代词（GP）**：预测正确的性别代词（he/she）。
  - **大于比较（GT）**：根据年份预测更大的数字。
- **基准模型**：GPT-2 Small（124M 参数）。
- **对比方法**：与先前组件级别的电路分析（ACDC、Wang et al. 2022）进行定性对比。文中也提到与 top-k 幅度和随机 SVD 基线的定量比较（附录 B），结果显示本文学习的掩码方向在 KL 散度上更低。
- **主要实验**：
  - 稀疏性 vs. 保真度（表 1）：在各任务上，大约只保留 3-9% 的方向即可高保真重建模型行为。
  - 方向掩码可视化（图 1、5、6）：已知的功能头（如 Name Mover）在特定方向上高激活。
  - 功能分解：以 Head 9.6 为例，发现其不同方向分别编码序列初始化、实体-动作分离、实体显著性等功能。
  - 因果干预：在 GP 任务上，通过交换性别方向激活值并放大奇异值，可实现近乎完美的预测翻转。

#### 4. 资源与算力
- 所有实验在 **单张 NVIDIA A40 GPU（48GB VRAM）** 上运行。
- 使用 PyTorch 2.1、HuggingFace Transformers 和 TransformerLens 库。
- 训练参数：batch size 64，epoch 15，学习率 1e-2，L1 正则化系数 1.5e-4（附录表 3）。
- 未明确说明总训练时长，但标注为在单 GPU 上即可完成，计算开销较低。

#### 5. 实验数量与充分性
- **实验数量**：覆盖三个数据集（IOI、GP、GT），进行了多个层次的实验：
  - 掩码优化与稀疏性评估（表 1）。
  - 全模型方向掩码可视化（图 1、5、6、7）。
  - 特定头的功能分解（Head 9.6、9.9、10.0；GT 任务中的 Head 9.1、6.9、5.5）。
  - 因果干预实验（GP 任务的标量交换+缩放，表 5、6，图 4）。
  - 消融对比（附录中对比 top-k 和随机 baseline）。
- **充分性与公平性**：实验较为充分，任务类型覆盖句法、语义、数值推理；可视化直观，因果干预提供了强证据。但存在一定局限：仅使用 GPT-2 Small，未对比其他模型或更大规模模型；对照方法主要是先前工作结果（定性），缺少多个最新方法的定量对比（如不同 SVD 截断策略）。

#### 6. 主要结论与发现
1. **Transformer 组件不是原子单元**，其内部存在多个正交的、可解释的奇异方向，每个方向承担独立子功能。
2. **稀疏性**：只需少量方向（约 3-9%）即可高保真复现模型行为，说明有效计算集中在低秩子空间。
3. **与已知电路对齐**：先前电路分析中识别的头（如 Name Mover、S-Inhibition）在对应方向上具有高掩码激活。
4. **发现具体子功能**：如序列初始化、实体-动作分离、实体显著性、抑制重复等。
5. **Logit Receptors**：在输出空间中存在固定的“logit receptor”方向，对应于特定词汇偏好（如 he/she），模型通过输入依赖的标量激活来动态选择这些方向。
6. **因果可控性**：通过标量干预（交换激活均值并放大），可精确翻转性别代词预测，验证了这些方向的因果作用。

#### 7. 优点
- **细粒度方法创新**：首次系统地将 SVD 应用于所有 Transformer 组件（QK、OV、MLP），揭示组件内部分布式计算。
- **简单高效**：方法计算开销低，易于复现。
- **跨任务验证**：在三个不同性质的任务上均有效，体现通用性。
- **因果证据**：通过标量干预实验提供了方向级别因果关系的直接证据，增强了可解释性的可靠性。
- **开放代码**：代码和数据集开源，便于后续研究。

#### 8. 不足与局限
- **独立性假设**：每个组件的分解独立进行，未考虑跨组件/层的交互，可能遗漏一些依赖组合的涌现行为。
- **方向解释性**：假设奇异方向对应可解释子例程，缺乏形式化证明；部分方向可能仍难以解释。
- **表达限制**：使用对角掩码只缩放奇异值，不允许旋转基向量，可能限制表达能力。
- **模型与任务覆盖**：仅使用 GPT-2 Small，未在更大模型（如 LLaMA）或更复杂推理任务上验证；评估任务均为人工构造的简单模板，推广性未知。
- **因果中介不完全**：掩码优化只保证输出忠实性，未完全厘清每个方向的因果中介路径，需结合因果追踪等方法深入。

（完）
