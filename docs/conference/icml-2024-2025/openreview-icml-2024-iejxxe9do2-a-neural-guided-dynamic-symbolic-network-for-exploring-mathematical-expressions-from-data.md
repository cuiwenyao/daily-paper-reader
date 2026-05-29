---
title: A Neural-Guided Dynamic Symbolic Network for Exploring Mathematical Expressions from Data
title_zh: 神经引导的动态符号网络用于从数据探索数学表达式
authors: "Wenqiang Li, Weijun Li, Lina Yu, Min Wu, Linjun Sun, Jingyi Liu, Yanjie Li, Shu Wei, Deng Yusong, Meilan Hao"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=IejxxE9DO2"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经引导符号网络发现表达式
tldr: 本文提出DySymNet，一种神经引导的动态符号网络用于符号回归。通过强化学习探索不同结构的符号网络，优化出更拟合数据的数学表达式。解决了深度生成式符号回归方法在高维问题和常数学习上的困难，提升了泛化能力。体现了神经与符号的协同。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1734, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1760, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 760, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 701, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 713, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1766, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-iejxxe9do2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1701, \"height\": 1187, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1753, \"height\": 746, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 792, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1779, \"height\": 890, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1781, \"height\": 815, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1784, \"height\": 1026, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1502, \"height\": 1016, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1294, \"height\": 1009, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1281, \"height\": 2364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1326, \"height\": 111, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-iejxxe9do2/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1411, \"height\": 2162, \"label\": \"Table\"}]"
motivation: 深度生成符号回归方法难以处理高维问题和学习常数，且泛化性差。
method: 提出神经引导的动态符号网络，结合强化学习探索符号结构并优化参数。
result: 在符号回归任务上表现优于现有方法，可处理高维问题。
conclusion: 神经引导的动态符号网络有效提升符号回归的准确性和泛化性。
---

## Abstract
Symbolic regression (SR) is a powerful technique for discovering the underlying mathematical expressions from observed data. Inspired by the success of deep learning, recent deep generative SR methods have shown promising results. However, these methods face difficulties in processing high-dimensional problems and learning constants due to the large search space, and they don't scale well to unseen problems. In this work, we propose DySymNet, a novel neural-guided **Dy**namic **Sym**bolic **Net**work for SR. Instead of searching for expressions within a large search space, we explore symbolic networks with various structures, guided by reinforcement learning, and optimize them to identify expressions that better-fitting the data. Based on extensive numerical experiments on low-dimensional public standard benchmarks and the well-known SRBench with more variables, DySymNet shows clear superiority over several representative baseline models. Open source code is available at https://github.com/AILWQ/DySymNet.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：符号回归（Symbolic Regression, SR）旨在从观测数据中发现简洁的数学表达式，广泛应用于科学发现。现有深度生成式SR方法（如DSR、NGGP）虽展现潜力，但面临两大困境：
  - **高维问题**：搜索空间随表达式长度指数增长，难以处理变量较多的任务。
  - **常数学习困难**：直接搜索完整表达式树导致常数优化效率低。
  - **泛化性差**：模型对未见问题（如更高维度、分布外数据）扩展性不足。
- **整体含义**：本文提出**DySymNet**，一种神经引导的动态符号网络，将搜索从巨大的函数空间**降维**到符号网络结构空间，结合强化学习自动探索网络架构，并通过可微训练优化权重，从而更高效地找到拟合数据的紧凑表达式。这是对传统GP和纯深度生成方法的一次重要改进，兼顾了灵活性和可扩展性。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：用RNN作为控制器（Controller），以强化学习方式逐步生成符号网络（Symbolic Network）的架构描述（层数、每层操作符数量和类型）。每个生成的网络都被实例化、训练并裁剪成稀疏表达式，用BFGS精炼常数，最终以拟合优度（R²）作为奖励信号更新控制器，迭代搜索最优结构。
- **关键技术细节**：
  - **符号网络结构**：每层包含线性映射（\(z^{(\ell)} = W^{(\ell)}h^{(\ell-1)} + b^{(\ell)}\)）和非线性变换（一元操作如sin、exp，二元操作如+、×）。最后一层为线性输出。
  - **训练与稀疏化**：网络通过MSE损失和**平滑L0.5正则化**（L*0.5）训练，使得权重稀疏，然后按阈值剪枝（|w|<0.01），从而得到简洁表达式。
  - **自适应梯度裁剪（AGC）**：梯度裁剪阈值根据最近窗口内梯度范数的移动平均值动态调整，提升训练稳定性。
  - **常数精炼**：使用BFGS优化从符号网络中提取的表达式中的常数。
  - **控制器训练**：采用**风险寻求策略梯度**（risk-seeking policy gradient）与最大熵正则项，仅关注奖励分布中前ε-分位数的样本，避免平均性能偏差，鼓励探索。
- **算法流程**（文字说明）：
  1. 初始化RNN控制器参数θc。
  2. 每步采样N个符号网络架构（层数、操作符类型等）。
  3. 每个网络实例化并端到端训练（MSE+L0.5正则化+AGC），然后剪枝得到表达式。
  4. 对表达式用BFGS精炼常数，计算奖励R=1/(1+MSE)。
  5. 选择奖励高于(1-ε)-分位数的样本，计算策略梯度更新RNN。
  6. 迭代直到达到阈值或最大步数。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集与Benchmark**：
  - **标准低维基准**（d≤2）：包括Nguyen、Nguyen*（含常数）、Constant、Keijzer、Livermore、R、Jin、Koza，共8组，每组含多个子问题（如Nguyen-1~12）。
  - **SRBench**（d≥2）：Feynman（119个方程）、Strogatz（14个）、Black-box（122个无真实表达式的问题）。
  - **物理定律发现**：11种自由落体球的数据（含空气阻力），训练集为前2秒，测试集为后续轨迹。
- **对比方法**：
  - **主流深度SR**：uDSR、NGGP（RL+GP）、NeSymReS（Transformer）、EQL（固定网络）。
  - **SRBench内置方法**：14种GP和ML方法（如AIFeynman、BSR、MRGP、Operon等），以及7种经典ML模型（如MLP、LGBM、XGB）。
- **指标**：主要使用决定系数R²（0~1），更高意味着更好；物理实验使用MSE。

## 4. 资源与算力

- 论文在附录B明确提到：
  - **硬件**：Intel Xeon Platinum 8255C CPU @ 2.50GHz，32GB RAM，**NVIDIA Tesla V100 32GB GPU**。
  - **无具体数量**：未说明使用了多少块GPU及训练总时长（仅提到每轮训练一个符号网络需要一定epochs，但无总时间）。
- 整体来看，算力需求适中，使用单张V100即可完成实验（但未提供总计算量）。

## 5. 实验数量与充分性

- **实验数量**：
  - 标准基准×8组（每个子问题20次独立运行），SRBench×3组（Feynman 119个问题、Strogatz 14个、Black-box 122个）。
  - 消融实验：移除Refine Constant (RC)、Policy Gradient (PG)、Adaptive Gradient Clipping (AGC)共3组对比，在Nguyen和Feynman上测试。
  - 噪声鲁棒性实验：在5个噪声水平（0~0.1）下对比4种方法。
  - 物理定律实验：11种球，每种独立训练，与3个人工物理模型对比。
- **充分性与公平性**：
  - 实验中基线均采用作者提供的最佳超参数或默认设置（uDSR、NGGP、NeSymReS、EQL），并使用相同符号库。
  - 多次运行给出了95%置信区间，统计可信。
  - 但缺乏对更大规模或更复杂表达式（如层级更深）的测试，且未包含与最新Transformer方法（如End-to-end SR）的直接对比（文中只选了NeSymReS）。总体而言，实验设计合理、对比全面，但可进一步扩展。

## 6. 论文的主要结论与发现

1. **性能超越**：在标准基准（d≤2）上，DySymNet在所有8组中均获得最高R²（多数接近1.0），尤其在Jin、Koza上完美恢复；在SRBench（d≥2）上，R²显著高于所有基线（Feynman 0.9931，Strogatz 0.9968，Black-box 0.8908）。
2. **高维优势**：明确解决了现有深度SR方法（如NGGP、NeSymReS）在高维问题上的困境（例如Black-box基准R²从0.4226提升至0.8908）。
3. **组件有效性**：消融实验证实RC、PG、AGC三个组件均对性能有正向贡献，缺失任一都会降低准确解率。
4. **噪声鲁棒性**：在噪声水平0.01~0.1范围内，DySymNet的准确解率下降最慢，优于uDSR、NGGP、NeSymReS。
5. **物理规律发现**：在自由落体空气阻力实验中，DySymNet发现的表达式在测试集MSE上平均为0.1736，远优于三个物理模型（2.27、71.94、1.59），在10/11个球上达到最优。

## 7. 优点

- **创新搜索范式**：将表达式搜索降为网络结构搜索，大幅缩减空间，同时保留强大表示力。
- **可处理高维问题**：通过动态网络宽度和深度，自然适应更多变量。
- **可解释性与简洁性**：通过L0.5正则化和剪枝获得稀疏表达式，模型大小（符号复杂度）较小（见帕累托图）。
- **结合神经和符号**：利用可微分训练优化权重，再通过RL优化架构，形成端到端闭环。
- **鲁棒且稳定**：自适应梯度裁剪和风险寻求策略梯度让训练更稳定，并专注于最佳样本。
- **开源可复现**：代码随论文发布。

## 8. 不足与局限

- **计算开销**：每个采样到的符号网络均需完整训练（2×10000 epoch），控制器迭代数百步，整体训练时间可能较长（未报告具体耗时）。相比Transformer单次前向推理慢很多。
- **未充分探索极端复杂表达式**：基准中表达式多为不超过10个节点的简单形式，对更深层次或含有嵌套特殊函数（如积分、无限级数）的表达式未测试。
- **超参数敏感**：尽管在不同任务中使用了统一超参数，但控制器学习率、正则化权重、剪枝阈值等仍需手动调整，自动调参方法未探讨。
- **无法处理非解析形式**：符号网络仅能表达预定义操作库的组合，不能发现完全新型数学结构（如新算子）。
- **实验对比局限性**：未与最新Transformer SR方法（如End-to-end Symbolic Regression、GPT-based MCTS）直接比较；且SRBench中Black-box数据集缺少真实表达式，只能评价拟合误差，无法衡量结构正确性。
- **物理发现的可解释性**：DySymNet输出表达式有时包含冗余项（如log(cosh(...))嵌套），不如人工推导的物理模型优雅，实际应用中需进一步简化。

---

（完）
