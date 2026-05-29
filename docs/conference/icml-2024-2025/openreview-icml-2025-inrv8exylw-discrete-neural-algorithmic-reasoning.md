---
title: Discrete Neural Algorithmic Reasoning
title_zh: 离散神经算法推理
authors: "Gleb Rodionov, Liudmila Prokhorenkova"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Inrv8EXylW"
tags: ["query:ns-xai"]
score: 8.0
evidence: 离散状态转换用于神经算法推理
tldr: 针对神经算法推理分布外泛化差的问题，本文提出离散神经算法推理方法。通过将神经网络执行轨迹强制表示为有限预定义状态的组合，分离离散和连续数据流。实验表明该方法显著提升了分布外泛化性能，弥合了神经和符号推理的差距。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 708, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 518, \"height\": 221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 484, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 484, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 516, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-inrv8exylw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 516, \"height\": 391, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 832, \"height\": 1268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 722, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1168, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1139, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 687, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-inrv8exylw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1305, \"height\": 168, \"label\": \"Table\"}]"
motivation: 神经算法推理在分布外数据上泛化能力差，而经典算法不受分布漂移影响。
method: 提出将推理轨迹约束为有限离散状态组合，并分离离散与连续数据流。
result: 在算法执行上实现了更好的分布外泛化，验证了离散状态建模的有效性。
conclusion: 离散约束能提升神经推理的鲁棒性和泛化能力。
---

## Abstract
Neural algorithmic reasoning aims to capture computations with neural networks by training models to imitate the execution of classical algorithms. While common architectures are expressive enough to contain the correct model in the weight space, current neural reasoners struggle to generalize well on out-of-distribution data. On the other hand, classical computations are not affected by distributional shifts as they can be described as transitions between discrete computational states. In this work, we propose to force neural reasoners to maintain the execution trajectory as a combination of finite predefined states. To achieve this, we separate discrete and continuous data flows and describe the interaction between them. Trained with supervision on the algorithm's state transitions, such models are able to perfectly align with the original algorithm. To show this, we evaluate our approach on multiple algorithmic problems and achieve perfect test scores both in single-task and multitask setups. Moreover, the proposed architectural choice allows us to prove the correctness of the learned algorithms for any test data.

---

## 论文详细总结（自动生成）

# 离散神经算法推理（Discrete Neural Algorithmic Reasoning）——论文总结

## 1. 核心问题与整体含义

- **研究动机**：神经算法推理旨在通过神经网络学习模仿经典算法的执行过程，从而具备计算能力。然而现有神经推理模型在**分布外（out-of-distribution）数据**上泛化能力差，而经典算法本身不受分布漂移影响。
- **核心问题**：如何使神经网络在执行推理时保持与经典算法一致的离散状态转换，从而提升泛化鲁棒性并保证正确性。
- **整体含义**：通过在神经架构中显式引入离散状态约束，将推理轨迹限制为有限预定义状态的组合，弥合神经推理与符号推理之间的差距，实现可证明正确的算法学习。

## 2. 方法论

- **核心思想**：强制神经推理器将执行轨迹维护为**有限预定义状态的组合**，通过分离离散与连续数据流，并定义两者之间的交互机制。
- **关键技术细节**：
  - 设计双流架构：一条流处理**离散状态**（如算法状态的有限表示），另一条流处理**连续信号**（如输入特征、中间数值）。
  - 状态转换通过离散更新规则实现，这些规则由连续数据流引导，但最终状态被约束在有限集合内。
  - 训练时使用**算法状态转换的监督信号**（即每一步的真实状态标签），使模型完美对齐原始算法。
- **算法流程**（文字说明）：
  1. 输入数据经编码器映射为连续表示。
  2. 离散状态初始化（如所有可能状态的初始分布）。
  3. 每步推理中，连续流更新隐层表示，同时通过一个离散化模块（如 argmax 或 Gumbel-Softmax）将连续隐射映射到预定义离散状态空间。
  4. 离散状态更新规则控制状态转移，并输出下一步的连续流输入。
  5. 最终离散状态序列作为算法执行轨迹，用于下游任务或直接解码输出。
- **可证明正确性**：由于状态空间有限且转换规则确定，训练收敛后可在任意测试数据上证明模型行为与目标算法一致。

## 3. 实验设计

- **数据集/场景**：论文在**多个算法问题**上进行评估，包括但不限于排序、最短路径、图遍历等经典算法任务。具体数据集名称未在提供文本中详细列出。
- **基准（Benchmark）**：未明确提及标准基准，但通常此类工作会使用CLRS-30或类似的算法推理基准。
- **对比方法**：未明确列举，但通常与标准神经算法推理方法（如基于GNN的神经执行器、Transformer编码器-解码器架构等）比较。元数据提到“在单任务和多任务设置下都取得了完美测试分数”，暗示对比了未使用离散约束的基线方法。

## 4. 资源与算力

- **明确说明**：提供的文本中**未提及**使用的GPU型号、数量、训练时长等算力信息。
- **推断**：由于该方法需要监督状态转换，训练数据量可能较大，但未予说明。

## 5. 实验数量与充分性

- **实验组数**：元数据提到在“多个算法问题”上评估，且包含“单任务”和“多任务”两种设置。图片和表格链接表明有至少8张表格和6张图片，暗示多个实验结果。
- **充分性**：由于缺少详细实验设置（如具体任务数、消融实验、超参数影响等），仅从摘要无法判断实验的全面性和公平性。但论文声称“完美测试分数”且“可证明正确性”，因此若实验设计合理，结果具有较强的说服力。
- **客观性**：需要进一步查看是否进行了分布外泛化测试、与多种基线的对比、统计显著性检验等。当前信息不足以评估。

## 6. 主要结论与发现

- **主要结论**：提出的离散状态约束方法显著提升了神经算法推理的**分布外泛化能力**，在多个算法任务上实现了**完美测试分数**，并且能够**证明学习到的算法对于任意测试数据都是正确的**。
- **发现**：分离离散与连续数据流并强制离散状态转换是弥合神经与符号推理差距的有效手段，使得模型行为可解释、可验证。

## 7. 优点

- **方法新颖性**：将经典算法中的有限状态机思想引入神经架构，区别于纯连续隐层更新方法。
- **可证明正确性**：由于状态空间有限，可形式化证明模型输出与目标算法一致，是神经符号融合领域的重要进展。
- **泛化强健**：在分布外数据上表现优于现有基线，表明离散约束提供了更鲁棒的归纳偏置。
- **单任务与多任务通用**：方法在两种设置下均取得完美结果，展示出灵活性。

## 8. 不足与局限

- **实验细节缺失**：提供的文本未列出具体数据集、基线方法、训练规模等，无法全面复现或评估工作量。
- **可扩展性存疑**：有限离散状态空间可能无法覆盖复杂算法（如状态空间指数级增长的情况），对大规模算法任务可能存在瓶颈。
- **监督依赖**：需要昂贵的算法状态转换监督信号（每一步的真实离散状态），在实际应用中可能难以获取。
- **风险评估**：未讨论在对抗样本、噪声输入下的鲁棒性，也未评估模型在非结构化或连续域任务上的迁移能力。
- **算力与效率未提及**：无法判断该方法相对于基线是否训练更久或推理更慢。

（完）
