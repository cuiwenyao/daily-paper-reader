---
title: Curriculum Abductive Learning
title_zh: 课程溯因学习
authors: "Wen-Chao Hu, Qi-Jie Li, Lin-Han Jia, Cunjing Ge, Yu-Feng Li, Yuan Jiang, Zhi-Hua Zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QzE4SDwcCr"
tags: ["query:ns-xai"]
score: 9.0
evidence: 将逻辑溯因与神经网络学习结合，用于符号概念标签修正
tldr: 溯因学习将机器学习与逻辑推理结合，但训练常因溯因空间大而不稳定。本文提出课程溯因学习，显式利用知识库内部结构将溯因空间分区，以课程方式逐步训练。实验证明该方法显著提升了训练的稳定性和效率，为神经符号系统的实际应用提供了有效方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 507, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1248, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 468, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 452, \"height\": 221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1408, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qze4sdwccr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 535, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 715, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1399, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 614, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1089, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qze4sdwccr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1482, \"height\": 651, \"label\": \"Table\"}]"
motivation: 现有溯因学习的训练过程因溯因空间巨大且知识库结构未被利用而极不稳定。
method: 提出课程溯因学习，将知识库结构显式用于分区溯因空间，实现课程式训练。
result: 在多个任务上，课程溯因学习显著提升了训练稳定性与效率。
conclusion: 利用知识库结构分阶段训练是稳定神经符号学习的有效途径。
---

## Abstract
Abductive Learning (ABL) integrates machine learning with logical reasoning in a loop: a learning model predicts symbolic concept labels from raw inputs, which are revised through abduction using domain knowledge and then fed back for retraining. However, due to the nondeterminism of abduction, the training process often suffers from instability, especially when the knowledge base is large and complex, resulting in a prohibitively large abduction space. While prior works focus on improving candidate selection within this space, they typically treat the knowledge base as a static black box. In this work, we propose Curriculum Abductive Learning (C-ABL), a method that explicitly leverages the internal structure of the knowledge base to address the ABL training challenges. C-ABL partitions the knowledge base into a sequence of sub-bases, progressively introduced during training. This reduces the abduction space throughout training and enables the model to incorporate logic in a stepwise, smooth way. Experiments across multiple tasks show that C-ABL outperforms previous ABL implementations, significantly improves training stability, convergence speed, and final accuracy, especially under complex knowledge setting.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：Abductive Learning (ABL) 将机器学习与逻辑推理相结合，通过溯因（abduction）修正模型预测的符号概念标签，再反馈训练。然而，溯因的非确定性导致候选空间（abduction space）极其庞大，尤其在知识库复杂时，训练过程往往不稳定、收敛慢、最终精度低。
- **现有局限**：以往工作主要关注在候选空间内如何优化选择（如一致性优化），但**将知识库视为静态黑箱**，忽略了其内部结构，无法从根本上缩小溯因空间。
- **本文目标**：**显式利用知识库的内部结构**，通过课程学习（Curriculum Learning）分阶段引入逻辑规则，从而逐步缩小溯因空间、稳定训练、加快收敛。

### 2. 论文提出的方法论

- **核心思想**：将完整知识库 `KB` 划分为多个子基 `KB_1, ..., KB_P`，训练时按阶段依次引入，每个阶段只使用部分规则，从而大幅降低当前阶段的溯因空间大小，模型逐步学习从简单到复杂的逻辑依赖。
- **关键技术细节**：
    1. **知识库分区算法（Algorithm 1）**：
        - 基于规则间的依赖关系构建有向依赖图。
        - 对每个概念标签 `z`，收集所有直接引用它的规则形成初始簇，再递归扩展以包含推导所需的所有规则。
        - 合并相同簇，并根据依赖关系拓扑排序，确保早阶段引入基础规则，晚阶段引入复杂规则。
        - 可选参数 `τ` 控制每个阶段最小概念数量，避免划分过细。
        - 分区满足三个原则：依赖内聚、逐步复杂度、自包含推理。
        - 理论保证（Theorem 3.2）：每个子基对当前阶段的概念域是**可靠且完备**的，最终阶段子基与完整知识库逻辑等价。
    2. **课程训练（Algorithm 2）**：
        - 在阶段 `p`，只使用子基 `KB_p`，并调度概念标签在 `Z_p` 内的训练数据。
        - 采用标准ABL过程：模型预测 → 检查是否与 `KB_p` 一致 → 若不一致则溯因产生候选空间并选择最一致的标签 → 用于更新模型。
        - 阶段切换条件：当每个概念标签在验证集上的准确率超过随机猜测基线 `1/|Z|` 时，进入下一阶段。
        - 最终阶段使用完整知识库直到终止条件。
- **理论分析**（Section 4）：
    - **阶段内高效训练**：溯因空间大小从 `|Z|^m` 缩减到 `|Z_p \ Z_{p-1}|^m`（Theorem 4.2），收敛复杂度与空间大小的平方成正比（Theorem 4.5）。
    - **平滑阶段迁移**：先前阶段推导的结论在后阶段依然成立（Theorem 4.6），模型空间形成嵌套序列（Theorem 4.7），避免灾难性遗忘。

### 3. 实验设计

- **数据集与场景**：
    - **Digit Addition**：两个 `d` 位数字求和。十进制（10个概念标签，CIFAR/MNIST）、十六进制（16个概念标签，CIFAR100/EMNIST），视觉输入为数字图像。
    - **Chess Attack**：棋盘上放置棋子，判断是否有攻击关系。棋子用MNIST数字表示，概念标签为6种棋子类型，目标标签为二值（attack/no attack）。
    - **Judicial Sentencing**：真实法律判决任务，输入为案卷文本，预测刑期。涉及9个量刑因子概念标签，知识库为带参数的一阶规则。
- **Benchmark 与对比方法**：
    - ABL基线：原始ABL、改进版A3BL。
    - 神经符号方法：NeurASP、DeepProbLog、DeepStochLog、LTN。
    - 所有方法使用相同感知模型（ResNet18/LeNet-5/BERT），训练迭代数一致（5,000或1,000）。
- **评估指标**：准确率（Accuracy）、训练时间（分钟）、收敛所需迭代数、F1、MAE、MSE等。

### 4. 资源与算力

- **硬件**：所有实验在 Intel Xeon Gold 6226R CPU 和 Tesla A100 GPU 上运行（未说明GPU数量）。
- **训练时间**：论文表格中给出了各方法的训练时间（分钟），例如在十进制加法 `d=4` 时，C-ABL耗时132.6分钟，ABL耗时253.6分钟。在司法任务中，C-ABL收敛所需token数更少。
- **分区开销**：知识库分区为一次性预处理，digit addition（14条规则）耗时0.05秒，chess attack（58条规则）耗时0.9秒，可忽略不计。
- **未明确说明**：未提及每次实验的重复次数（实际上为5次）、总GPU小时数、超参数调优的具体过程。

### 5. 实验数量与充分性

- **实验组数**：涵盖三个主要任务（加法、象棋、法律），每个任务有多个变体（十进制/十六进制、不同位数、不同数据集）。加法任务跨两个数据集（CIFAR、MNIST/EMNIST）。象棋和法律任务分别与多个基线对比。
- **消融与敏感性分析**：对分区阈值 `τ` 进行了敏感性测试（Table 4），验证了对不同粒度划分的鲁棒性。
- **训练曲线**：提供了训练过程中的准确率变化曲线（Figure 2, 3, 6），展示了阶段性进展和稳定性。
- **充分性评价**：实验覆盖了从合成任务到真实法律场景，对比了多种主流神经符号方法，并进行了解析分析。总体客观、公平，但缺少对更大规模知识库或更多随机种子重复的详细展示（文中提到5次重复，附误差棒）。

### 6. 论文的主要结论与发现

1. C-ABL 在几乎所有任务和设置下**显著优于**原版ABL、A3BL及其他神经符号方法，尤其在复杂推理（高位数、十六进制、象棋二值标签）中优势更明显。
2. 训练过程更**稳定**：阶段式引入概念避免了早期振荡，收敛速度更快（如图2、3所示）。
3. 理论分析表明，分区策略有效缩小了溯因空间，且阶段间逻辑一致，保证了平滑迁移。
4. 方法具有实际应用价值，在法律判决任务中同时提升了F1、MAE、MSE并减少了收敛所需token数。

### 7. 优点

- **结构感知**：首次在ABL中显式利用知识库内部结构（依赖图），而非视为黑箱，切入痛点。
- **理论严谨**：提供了分区原则、逻辑等价性证明、收敛复杂度分析、阶段迁移拓扑保证。
- **通用性强**：适用于多种感知模型（CNN、BERT）和多种知识表示格式（Horn子句、带参数规则）。
- **计算开销小**：分区是离线预处理，几乎不增加训练负担，且大幅降低每次溯因的计算量。
- **实验全面**：涵盖合成与真实场景，与多个强基线对比，并做了消融与敏感性分析。

### 8. 不足与局限

- **对知识库结构假设较强**：要求知识库具有分阶段/层级结构（如法律、数学、游戏），对于规则高度纠缠或无清晰层次的知识库，分区可能效果不佳（论文已自述在Appendix A）。
- **固定阈值与静态课程**：阶段切换阈值（准确率超过随机）和分区阈值 `τ` 是手工设置，缺乏自适应或可学习的调度策略。
- **依赖预定义知识库**：方法假设已有完整、正确的一阶逻辑知识库，未探讨知识获取或自动修正。
- **实验可扩展性**：虽然任务多样，但知识库规模相对较小（最多58条规则），未在更大规模（如数百条规则）或非封闭领域知识库上验证。
- **未比较部分方法**：未与ABL-Refl、ABL-PSP等对比，理由是其需要不同的感知模块，但可能影响结论的全面性。

（完）
