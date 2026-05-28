---
title: A learnability analysis on neuro-symbolic learning
title_zh: 神经符号学习的可学习性分析
authors: "Hao-Yuan He, Ming Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FrdX7K4Gli"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号学习可学习性及推理捷径的理论分析
tldr: 神经符号系统的可学习性缺乏理论保障，且常出现推理捷径问题。本文系统分析了混合系统中神经符号任务的可学习性，通过导出约束满足问题给出可学习性判据和样本复杂度，并统一解释了推理捷径现象。结果为设计可靠神经符号系统提供了理论指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 708, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 661, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 1437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 1437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1346, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 991, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-frdx7k4gli/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1450, \"height\": 992, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 667, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 728, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-frdx7k4gli/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 416, \"label\": \"Table\"}]"
motivation: 神经符号系统的理论可学习性尚未明确，且推理捷径问题影响可解释性。
method: 通过导出约束满足问题，从理论上刻画可学习性条件与样本复杂度。
result: 建立了可学习性充要条件，并证明推理捷径与解不一致程度相关。
conclusion: 理论分析为神经符号系统的设计提供了可操作的指导。
---

## Abstract
This paper presents a comprehensive theoretical analysis of the learnability of neuro-symbolic (NeSy) tasks within hybrid systems. 
  We characterize the learnability of NeSy tasks by their derived constraint satisfaction problems (DCSPs), demonstrating that a task is learnable if and only if its corresponding DCSP admits a unique solution. 
  Under mild assumptions, we establish the sample complexity for learnable tasks and show that, for general tasks, the asymptotic expected concept error is controlled by the degree of disagreement among DCSP solutions. 
  Our findings unify the characterization of learnability and the phenomenon of reasoning shortcuts, providing theoretical guarantees and actionable guidance for the principled design of NeSy systems.

---

## 论文详细总结（自动生成）

# 神经符号学习的可学习性分析——论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：神经符号学习（NeSy）旨在融合数据驱动学习与知识驱动推理，但缺乏严格的理论可学习性保障。实践中常出现**推理捷径（reasoning shortcuts）**问题：模型在训练数据上达到低神经符号风险，却学到错误的概念分布，导致概念风险高。如何从理论上刻画哪些NeSy任务可学习、如何量化概念误差、以及推理捷径的本质是什么，是亟需回答的根本问题。
- **整体含义**：本文建立了混合系统下NeSy任务可学习性的**充要条件**，统一解释了推理捷径现象，并为NeSy系统的设计（如样本复杂度、多任务聚合）提供了理论指导。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将NeSy学习问题转化为**导出约束满足问题（DCSP）**。可学习性等价于DCSP有唯一解，概念误差的上界由DCSP解的不一致度控制。
- **关键定义**：
  - **DCSP**：变量 \( V = \{V_1,\dots,V_L\} \) 对应输入空间聚类后的概念标签；域 \( D_i = Z \)；约束 \( C_j \) 为 \( V(x_j) \land KB \models y_j \)。
  - **解不一致度** \( d = L - |\text{Union}(S)| \)，其中 \( S \) 是所有解集合。
- **受限假设空间**：假设模型满足聚类性质（相同概念对应相同输出），避免过拟合。
- **理论结果**：
  - **可学习性充要条件**（Theorem 3.6）：DCSP有唯一解（\( d=0 \)）时任务可学习；否则不可学习。
  - **样本复杂度**：对于可学习任务，样本量 \( N > \frac{1}{\kappa} \log(|B|/\epsilon) \)，其中 \( \kappa \) 是采样概率下界，\( B \) 是可能的概念序列集。
  - **渐近概念误差上界**（Theorem 3.7）：平均概念误差 \( E^* \leq d/L \)。
  - **多任务聚合**（Corollary 3.8）：多个不可学习任务若DCSP解空间交集唯一，则聚合后变得可学习。
- **优化方法**：采用统一代理风险（公式7），平衡概率神经符号学习（PNL）和溯因学习（ABL）。

## 3. 实验设计
- **数据集与场景**：
  - **算术任务**：基于MNIST、KMNIST、CIFAR-10、SVHN的加法、乘法、模加法（模数k=2~10），以及多位数运算。
  - **真实场景**：BDD-OIA自动驾驶多标签任务（21个二值概念，74240个DCSP解，不一致度d=15）。
- **Benchmark与对比方法**：
  - LTN（Logic Tensor Networks）、DeepProbLog、ABL（溯因学习）、A3BL（作者提出的混淆感知溯因学习）。
- **实验设置**：所有实验重复5次（随机种子2023-2027），使用AdamW优化器，学习率0.0015，批次256，LeNet/MNIST-KMNIST、ResNet50/CIFAR-SVHN。

## 4. 资源与算力
- **文中提及**：使用Intel Xeon Platinum 8538 CPU和NVIDIA A100-PCIE-40GB GPU，Ubuntu 20.04平台。但**未明确说明**具体训练时长、GPU数量及总计算量。

## 5. 实验数量与充分性
- **实验数量**：非常充分。包括：
  - 4种数据集（MNIST、KMNIST、CIFAR-10、SVHN）× 多种算术任务（加法、乘法、模加法k=2~10）。
  - 3种方法（A3BL、ABL、PNL）各自独立实验（图1、7-9）。
  - 多任务聚合实验（图3、10-12），涵盖所有模基数的两两组合。
  - 真实场景BDD-OIA（表2），对比4种方法。
- **充分性与公平性**：
  - 所有实验提供标准误差（阴影/误差线）。
  - 多种数据集覆盖不同难度（手写数字、自然图像）。
  - 对比了不同NeSy范式（概率型、溯因型）。
  - 验证了理论预测（渐近界、可/不可学习区分）与实验结果一致。**结论客观、公平**。

## 6. 主要结论与发现
1. **可学习性充要条件**：NeSy任务可学习当且仅当DCSP有唯一解（\( d=0 \)）。
2. **样本复杂度**：可学习任务需要 \( N > (1/\kappa)\log(|B|/\epsilon) \)。
3. **概念误差上界**：一般任务的概念误差受 \( d/L \) 控制，不一致度越高，误差越大。推理捷径直接对应多个DCSP解。
4. **多任务聚合提升可学习性**：两个不可学习任务若DCSP解空间交集唯一，则聚合后可学习（例如模3+模4）。
5. **实证验证**：在多个数据集和方法上，实验结果与理论预测高度吻合。

## 7. 优点
- **理论完善**：首次提出NeSy可学习性充要条件，统一了推理捷径解释，给出样本复杂度和误差界。
- **DCSP框架直观可操作**：可通过现成CSP求解器计算解空间和不一致度，便于验证。
- **实验设计严谨**：覆盖多种数据集、任务、方法，重复5次，提供误差条，支持理论结论。
- **实用价值**：为NeSy模型的设计（如多任务学习、预训练）提供理论指导，预测可学习性。

## 8. 不足与局限
- **假设局限**：依赖“受限假设空间”（聚类性质），仅适用于混合系统，未覆盖端到端约束嵌入等方法。
- **计算复杂性**：DCSP求解是NP-hard，大规模知识库可能面临可扩展性挑战，论文仅提出近似方向（采样、启发式）但未实现。
- **实验覆盖**：主要基于数字识别和自动驾驶场景，缺乏自然语言处理、机器人规划等更复杂应用。
- **半监督场景**：未分析部分概念标注情况下的可学习性。
- **未讨论模型选择**：未提供如何自动找到最小可学习任务聚合策略的具体算法。

（完）
