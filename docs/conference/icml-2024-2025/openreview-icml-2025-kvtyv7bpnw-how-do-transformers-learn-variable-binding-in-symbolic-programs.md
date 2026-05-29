---
title: How Do Transformers Learn Variable Binding in Symbolic Programs?
title_zh: Transformer如何在符号程序中学习变量绑定？
authors: "Yiwei Wu, Atticus Geiger, Raphaël Millière"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=kVtyv7bpnw"
tags: ["query:ns-xai"]
score: 9.0
evidence: 研究Transformer在符号程序中的变量绑定能力
tldr: 符号计算中的变量绑定对神经网络构成挑战。本文训练Transformer执行符号程序中的变量解引用任务，发现模型经历了三个阶段的发展轨迹，揭示了神经网络在没有内置绑定操作时如何获得该能力，为神经符号集成提供了机制性理解。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1741, \"height\": 1040, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1592, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 785, \"height\": 1303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 805, \"height\": 1400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1570, \"height\": 1579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1593, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1677, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 774, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 781, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 788, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 789, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kvtyv7bpnw/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1769, \"height\": 2006, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-kvtyv7bpnw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 798, \"height\": 507, \"label\": \"Table\"}]"
motivation: 理解神经网络如何在没有显式绑定机制的情况下实现变量绑定。
method: 训练Transformer执行包含多步变量赋值的符号程序解引用任务。
result: 观察到模型经历三个阶段的发展轨迹，成功学习了变量绑定。
conclusion: Transformer可以通过训练获得符号变量绑定能力，为神经符号系统设计提供启示。
---

## Abstract
Variable binding---the ability to associate variables with values---is fundamental to symbolic computation and cognition. Although classical architectures typically implement variable binding via addressable memory, it is not well understood how modern neural networks lacking built-in binding operations may acquire this capacity. We investigate this by training a Transformer to dereference queried variables in symbolic programs where variables are assigned either numerical constants or other variables. Each program requires following chains of variable assignments up to four steps deep to find the queried value, and also contains irrelevant chains of assignments acting as distractors. Our analysis reveals a developmental trajectory with three distinct phases during training: (1) random prediction of numerical constants, (2) a shallow heuristic prioritizing early variable assignments, and (3) the emergence of a systematic mechanism for dereferencing assignment chains.
Using causal interventions, we find that the model learns to exploit the residual stream as an addressable memory space, with specialized attention heads routing information across token positions. 
This mechanism allows the model to dynamically track variable bindings across layers, resulting in accurate dereferencing. 
Our results show how Transformer models can learn to implement systematic variable binding without explicit architectural support, bridging connectionist and symbolic approaches.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：变量绑定（将变量与具体值关联）是符号计算和认知的基础能力，但现代神经网络（如Transformer）没有内置的绑定操作，它们如何通过训练获得这一能力仍不清楚。
- **研究动机**：经典符号系统依赖可寻址内存实现绑定，而连接主义模型缺乏显式符号操作。该研究旨在探索神经网络能否通过自学习实现变量解引用（dereferencing），从而连接符号主义与连接主义观点。
- **整体含义**：理解Transformer如何在无显式架构支持下，发展出系统性的变量绑定机制，为神经符号系统的设计提供启示，并揭示神经网络结构化推理能力的涌现路径。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计一个合成符号程序解引用任务，训练小规模GPT-2风格Transformer，并通过因果干预（interchange intervention）分析其内部机制。
- **关键技术细节**：
  - **任务构造**：每个程序包含17行（16行赋值+1行查询），变量链深度1-4步，另含无关干扰链。赋值语句形如`var = const`或`var = var`，查询为`#var:`，要求输出最终数值。
  - **模型架构**：12层Transformer，8头注意力，头维度64，残差流维度512，使用RoPE位置编码、GELU激活、LayerNorm、Dropout 0.1，参数37.8M。
  - **训练**：从零训练，AdamW优化器，线性学习率衰减（含warmup），batch size=64，共训练15 epochs，数据集500,000个程序（90%训练，0.2%验证，9.8%测试）。
  - **因果分析方法**：
    - **互换干预**：构造反事实输入（更改变量链根部数值），替换特定残差流或注意力头输出，观察输出变化，定位信息流动路径。
    - **残差流干预**：在关键token位置（右值、查询变量、冒号）替换残差流，追踪数值传播。
    - **注意力头干预**：对单个注意力头输出进行置换，识别负责信息路由的头部。
    - **子空间分析**：用PCA降维+L1正则线性分类器提取数值常量子空间（10个主成分）和变量名子空间（26个主成分），并用UMAP可视化演化。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：合成生成的500,000个程序，每个程序17行，变量为a-z，数值为0-9单数字。链深度1-4步，干扰链随机生成。使用加权采样（链长立方加权）和拒绝采样平衡深度分布。
- **基准**：无现有方法对比，因为任务是全新设计的合成符号程序。主要评估指标为测试集准确率（最终>99.9%）。
- **对比方法**：未与其他模型或方法比较，而是对同一模型不同训练阶段（checkpoint）进行内部对比，分析机制演化。额外进行了多重随机种子实验（6个种子）验证可复现性。

### 4. 资源与算力

- **论文未明确说明**：文中未提及使用的GPU型号、数量、训练时长等具体算力信息。仅提到训练15 epochs，batch size=64，模型参数量37.8M。可以推测训练在单卡或几卡GPU上可在数小时内完成，但具体细节缺失。

### 5. 实验数量与充分性

- **实验数量**：主要包含：
  - 主模型训练与测试（500k程序，六个随机种子）。
  - 行为分析：准确率随时间变化、按答案行位置、按跳数、按预测分布（图2）。
  - 因果干预实验：残差流干预（图3a,b）、注意力头干预（图3c）、跨checkpoint干预追踪（图4）。
  - 子空间分析：PCA+线性分类器+UMAP可视化（图5）。
  - 泛化测试：变程序长度（2-25行，图8）、变跳数（1-13跳，图9）、组合泛化（10%变量-数值组合不留训练，图7）。
  - 线性探针实验（表1）。
  - 附录中提供了多种子训练曲线（图6）和所有层注意力头干预结果（图10）。
- **充分性与公平性**：
  - **充分**：覆盖了行为、机制、泛化多个维度，且进行了跨种子验证，结果一致。
  - **客观**：采用因果干预（直接替换激活）而非相关性分析，能严格证明因果关系。
  - **公平**：任务设计无偏差，所有测试集为独立同分布，泛化测试使用分布外长度和跳数，结果合理。但缺少与其他架构（如RNN、MLP）或现有绑定方法的对比，是局限之一。

### 6. 论文的主要结论与发现

- **三阶段学习轨迹**：模型经历(1)随机预测数值→(2)基于早期行（line-1, line-2）的浅层启发式→(3)系统性变量解引用机制。
- **启发式保留而非替代**：最终解决方案叠加在早期启发式之上——当启发式有效时优先使用，否则启用深度链跟踪。
- **残差流作为可寻址内存**：因果干预表明，模型利用残差流在不同token位置间路由数值信息，形成地址空间。
- **特定注意力头负责路由**：如头6.5、7.7负责第一跳，头7.2、8.3、9.4负责第二、三跳，头11.2、11.3、11.7将信息传至输出位置。
- **存在独立的数值子空间和变量名子空间**：通过PCA+线性分类器识别，互换子空间干预成功率高（数值92.17%，变量87.08%）。
- **泛化能力强**：对未见过跳数（1-13跳）、不同程序长度（2-25行）、组合泛化均表现良好，表明学到了系统性机制而非记忆。

### 7. 优点：方法或实验设计上的亮点

- **新颖的任务设计**：合成程序任务精确控制变量链深度和干扰，便于机制分析。
- **发展性因果分析**：不仅分析最终模型，还追踪训练过程中机制的涌现，揭示启发式如何过渡为系统性方案。
- **多层次的因果干预**：从残差流、注意力头到子空间，层层递进，提供完整信息流图。
- **配套交互平台**：提供Variablescope.org供研究者验证和探索，增强可复现性。
- **子空间因果验证**：将PCA/线性探针与因果干预结合，不仅发现相关性还验证因果作用。

### 8. 不足与局限

- **实验覆盖不足**：仅使用单一Transformer架构（GPT-2风格），未比较其他架构（如RNN、状态空间模型）或更大的预训练模型。
- **缺乏基线对比**：未与其他绑定方法（如显式内存网络、神经符号系统）进行性能比较，难以评估该机制的优越性。
- **计算资源未说明**：缺少训练具体硬件和时长，影响复现和可扩展性讨论。
- **任务简化**：数值仅0-9，变量仅26个，深度最大4，实际编程中的复杂绑定（如嵌套结构、动态作用域）未被覆盖。
- **潜在偏差**：程序生成策略（立方加权、拒绝采样）可能引入分布偏差，影响泛化结论的稳健性。例如长程序上line-1启发式失效，可能源于训练分布特性而非模型能力。
- **缺少安全与鲁棒性分析**：未探讨模型对错误输入、对抗干扰等情况的鲁棒性。

（完）
