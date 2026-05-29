---
title: A learnability analysis on neuro-symbolic learning
title_zh: 神经符号学习的可学习性分析
authors: "Hao-Yuan He, Ming Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FrdX7K4Gli"
tags: ["query:ns-xai"]
score: 10.0
evidence: 神经符号学习的可学习性理论分析与推理捷径
tldr: 针对神经符号（NeSy）系统缺乏理论可学习性分析的问题，本文建立了基于推导约束满足问题（DCSP）的可学习性刻画，证明任务可学习当且仅当对应DCSP有唯一解，并推导样本复杂度。该理论统一解释了推理捷径现象，为设计可靠的NeSy系统提供了理论基础和实用指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 605}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 708, \"height\": 291}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 507}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 661, \"height\": 508}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 722}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 1437}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 1437}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1346, \"height\": 376}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 991}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1450, \"height\": 992}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 667, \"height\": 170}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 728, \"height\": 177}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 416}]"
motivation: 神经符号系统设计缺乏理论保证，推理捷径现象未被统一解释。
method: 通过DCSP将学习问题转化为约束满足，利用唯一解条件刻画可学习性并推导误差界。
result: 可学习性与DCSP唯一解等价，推理捷径由解分歧度控制。
conclusion: 该理论为神经符号系统的可靠设计提供了原理性指导，有助于构建可解释且鲁棒的混合系统。
---

## Abstract
This paper presents a comprehensive theoretical analysis of the learnability of neuro-symbolic (NeSy) tasks within hybrid systems. 
  We characterize the learnability of NeSy tasks by their derived constraint satisfaction problems (DCSPs), demonstrating that a task is learnable if and only if its corresponding DCSP admits a unique solution. 
  Under mild assumptions, we establish the sample complexity for learnable tasks and show that, for general tasks, the asymptotic expected concept error is controlled by the degree of disagreement among DCSP solutions. 
  Our findings unify the characterization of learnability and the phenomenon of reasoning shortcuts, providing theoretical guarantees and actionable guidance for the principled design of NeSy systems.

---

## 论文详细总结（自动生成）

# 神经符号学习的可学习性分析：详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：神经符号（NeSy）系统旨在整合数据驱动学习与知识驱动推理，但在弱监督训练（仅提供输入-输出对，缺乏中间概念监督）下，存在“推理捷径”（reasoning shortcut）问题——模型能在训练数据上达到高似然，但实际学到的概念分布与真实概念分布严重偏离。这揭示了概念风险（concept risk）与神经符号风险（NeSy risk）之间的不一致性，即最小化NeSy风险不一定最小化概念风险。然而，当时缺乏严格的理论框架来刻画NeSy任务的可学习性条件。
- **研究背景**：现有工作（如Marconato等）定性描述了推理捷径，并提出缓解方法，但缺少对可学习性的统一理论分析。Wang等（2023）提出多实例部分标签学习并依赖“M-无歧义”条件，但假设输入模式重复（如[z,z,…]），不适用于实际场景。Tao等（2024）使用概率矩阵分析，但构造需完全知晓概念分布。Yang等（2024）引入捷径风险度量，但低捷径风险不能保证低概念误差。
- **研究目标**：回答核心问题：“在什么条件下，通过经验风险最小化（ERM）优化NeSy风险，当样本量趋于无穷时，概念风险能够被最小化？”并揭示推理捷径的本质。

## 2. 方法论

- **核心思想**：将NeSy任务的可学习性分析转化为**推导约束满足问题（Derived Constraint Satisfaction Problem, DCSP）** 的求解问题。关键洞察：在受限假设空间下，学习过程等价于在DCSP中寻找一致性赋值。可学习性由DCSP解的唯一性决定。
- **关键概念与技术细节**：
  - **受限假设空间（Restricted Hypothesis Space, F*）**：假设空间需满足聚类性质——相同标签的实例应映射到相同概念，反之亦然。这通过预训练或自监督学习实现，避免过拟合。
  - **DCSP定义**：给定任务T=⟨X, Y, KB⟩，DCSP定义为三元组⟨V, D, C⟩：
    - V = {V₁,…,V_L}：变量，每个变量对应概念空间中的一个概念类。
    - D = {D_i = Z}：每个变量的域为整个概念空间。
    - C = {C₁,…,C_N}：约束，每个约束对应一个训练样本(x, y)，即V(x) ∧ KB |= y。
    求解DCSP得到一致性赋值I，即每个概念类的预测标签。
  - **解分歧度（disagreement d）**：d = L - |Union(S)|，其中S是DCSP所有解的集合，Union(S)是所有解中共有的变量赋值数量。d度量了不同解之间不一致的变量数。d=0表示唯一解。
  - **可学习性条件**（Theorem 3.6）：任务T可学习当且仅当DCSP有唯一解（d=0）。若d>0，则任务不可学习，概念误差不可避免。
  - **样本复杂度**（Lemma B.1）：对于可学习任务，若概念序列集合B有限且最小采样概率κ>0，则概念误差ϵ所需样本数N > (1/κ)·log(|B|/ϵ)。
  - **渐近误差上界**（Theorem 3.7）：对于一般任务，平均概念误差E* ≤ d/L。即误差由分歧度d与概念空间大小L之比控制。
  - **任务聚合**：多个不可学习的任务通过多任务学习联合训练时，若其DCSP解空间交集收缩为唯一解，则聚合任务变为可学习（Corollary 3.8）。
- **公式推导**：论文证明了NeSy风险（RNeSy）的最小化器也是概率神经符号学习（RPNL）和溯因学习（RABL）的最小化器（Theorem 2.1），从而分析统一适用于两类主流NeSy方法。

## 3. 实验设计

- **数据集**：
  - **算术任务**：使用MNIST、KMNIST、CIFAR-10、SVHN四个图像数据集，每个数据集的类别索引映射为数字（如CIFAR-10中“飞机”=0,…,“卡车”=9）。任务包括：加法、乘法、异或（XOR）、模加法（mod k, k=2,…,10）。
  - **真实场景**：BDD-OIA（自动驾驶多标签数据集），包含21个二进制概念（如行人、红绿灯、障碍物等），知识库编码了安全驾驶规则（如“有行人时不能前进”）。该任务有74,240个DCSP解，分歧度d=15，属于典型的不可学习任务。
- **基准方法**：
  - 使用LTN（逻辑张量网络）、DeepProbLog（概率逻辑编程）、ABL（溯因学习）、A3BL（模糊感知溯因学习）等方法进行对比。
  - 作者提出的主要优化目标为公式(7)：-E_{(x,y)} log Σ_{z̄∈N(y)} p[y, z̄ | x; f, KB]，通过控制候选集大小N(y)在ABL和PNL之间平衡。
- **实验配置**：
  - 算术任务中，学习模型：LeNet（MNIST/KMNIST）、ResNet50（CIFAR-10/SVHN），预训练以确保聚类性质。
  - 优化器：AdamW（lr=0.0015, β=(0.9,0.99)），批大小256，epoch数10。
  - 每个实验重复5次，使用不同随机种子，报告均值和标准差（以阴影区域表示）。
  - 样本量从10到10⁴量级变化，观察概念准确率和推理准确率随样本量的变化。

## 4. 资源与算力

论文在附录C.1中提及：实验使用Intel Xeon Platinum 8538 CPU和NVIDIA A100-PCIE-40GB GPU，操作系统为Ubuntu 20.04。但**未明确说明训练时长、GPU数量、总计算消耗**等具体算力信息。仅提到“所有实验均在上述平台上运行”，缺乏量化细节。

## 5. 实验数量与充分性

- **实验组数**：
  - 算术任务：包括加法、乘法、模加法（k=2,4,6,8,9等）四个数据集（MNIST、KMNIST、CIFAR-10、SVHN）×多种方法（A3BL、ABL、PNL）→至少数十张曲线图。
  - 聚合任务：展示了不同模基组合（如(2,3)、(3,4)等）的聚合效果，覆盖了成功与失败案例。
  - BDD-OIA真实任务：对比四种方法，报告5次重复的准确率。
- **充分性与客观性**：
  - 实验覆盖了简单算术和复杂高维数据，以及真实自动驾驶场景，多样性充足。
  - 使用多种数据集和多种NeSy方法进行验证，确保结论的泛化性。
  - 所有结果均包含误差线（标准误差），重复5次，统计严谨。
  - 与理论预测的渐近界（绿色线）进行对比，直接验证定理。
  - 不足之处：实验主要基于图像分类任务，未涉及其他模态（如文本、音频）；BDD-OIA任务中仅报告了表2的数值结果，未像算术任务那样展示样本量变化曲线，稍显简略。

## 6. 主要结论与发现

- **可学习性条件**：NeSy任务可学习当且仅当其DCSP有唯一解（d=0）。若d>0，则不可学习，概念误差存在下界。
- **样本复杂度**：可学习任务的概念误差ϵ所需样本数为N > (1/κ)·log(|B|/ϵ)。
- **误差控制**：概念误差的渐近上界由分歧度d决定（E* ≤ d/L）。分歧度比单纯解的数量更能刻画误差（Remark 1）。
- **推理捷径解释**：确定性推理捷径的存在等价于DCSP存在多个解。概念误差与解分歧度强相关，而与解的数量非单调相关。
- **任务聚合**：将多个不可学习任务联合训练，通过解空间交集减少分歧度，可使聚合任务变为可学习（Corollary 3.8），这揭示了NeSy领域可能的“缩放定律”。

## 7. 优点

- **理论突破**：首次为NeSy混合系统建立了严格的可学习性刻画，统一解释了推理捷径现象，填补了理论空白。
- **DCSP框架直观实用**：将学习问题转化为约束满足问题，可利用现有CSP求解器进行验证，降低了理论分析的难度。
- **细粒度概念误差分析**：引入分歧度d，比简单计数解数量更能准确预测概念误差，并给出了渐近界（定理3.7）。
- **任务聚合见解**：发现聚合多个不可学习任务可提升可学习性，为设计多任务NeSy系统提供了理论依据。
- **实验验证扎实**：在多个数据集和多种NeSy方法上验证了理论，包括深度学习模型和真实场景，确保了结论的可靠性。

## 8. 不足与局限

- **假设条件较强**：分析依赖“受限假设空间”（聚类性质），虽然可以通过预训练满足，但未扩展到一般无约束的假设空间。作者也指出这是一个开放挑战。
- **仅覆盖混合系统**：结果只适用于以学习模型+逻辑推理模型为架构的混合NeSy系统（如DeepProbLog、ABL等），不直接适用于其他类型（如损失函数约束型、端到端自解释型）。
- **计算可扩展性问题**：DCSP求解本质上是NP-hard问题，对大规模知识库可能面临可扩展性挑战。作者提出了采样、启发式、分解等未来方向，但未给出具体解决方案。
- **实验覆盖有限**：
  - 算术任务中概念空间仅为10个数字（L=10），未探索更大概念空间。
  - BDD-OIA任务中，只报告了最终精度，未展示样本量变化曲线，未能深入验证分歧度与误差的定量关系。
  - 未在非视觉模态（如自然语言、序列数据）上验证。
- **方差控制**：虽然在算数任务中重复5次，但BDD-OIA任务中某些方法（如DeepProbLog）的概念准确率为0.00±0.00，可能因训练失败所致，论文未给出详细分析。

（完）
