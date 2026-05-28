---
title: Multi-head Transformers Provably Learn Symbolic Multi-step Reasoning via Gradient Descent
title_zh: 多头Transformer通过梯度下降可证明学习符号多步推理
authors: "Tong Yang, Yu Huang, Yingbin Liang, Yuejie Chi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=qFC728XyeM"
tags: ["query:ns-xai"]
score: 8.0
evidence: 通过梯度下降可证明学习符号多步推理
tldr: 该论文从理论层面分析了Transformer如何通过梯度下降学习符号多步推理，聚焦于树搜索中的路径推理任务。作者证明Transformer能够学习反向推理和正向推理，为理解神经符号推理提供了理论基础，有助于提升模型的可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1238, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1354, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 299, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 726, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 720, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 724, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qfc728xyem/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 539, \"height\": 378, \"label\": \"Figure\"}]"
motivation: 缺乏对Transformer获得多步推理能力的理论理解。
method: 理论分析Transformer在树路径搜索任务上的符号多步推理学习过程。
result: 证明Transformer能通过梯度下降学习反向和正向推理。
conclusion: 揭示了Transformer符号推理的理论基础。
---

## Abstract
Transformers have demonstrated remarkable capabilities in multi-step reasoning tasks. However, understandings of the underlying mechanisms by which they acquire these abilities through training remain limited, particularly from a theoretical standpoint. This work investigates how transformers learn to solve symbolic multi-step reasoning problems through chain-of-thought processes, focusing on path-finding in trees. We analyze two intertwined tasks: a backward reasoning task, where the model outputs a path from a goal node to the root, and a more complex forward reasoning task, where the model implements two-stage reasoning by first identifying the goal-to-root path and then reversing it to produce the root-to-goal path. Our theoretical analysis, grounded in the dynamics of gradient descent, shows that trained one-layer transformers can provably solve both tasks with generalization guarantees to unseen trees. In particular, our multi-phase training dynamics for forward reasoning elucidate how different attention heads learn to specialize and coordinate autonomously to solve the two subtasks in a single autoregressive path. These results provide a mechanistic explanation of how trained transformers can implement sequential algorithmic procedures. Moreover, they offer insights into the emergence of reasoning abilities, suggesting that when tasks are structured to take intermediate chain-of-thought steps, even shallow multi-head transformers can effectively solve problems that would otherwise require deeper architectures.

---

## 论文详细总结（自动生成）

## 论文中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：Transformer在需要链式思维的多步推理任务中表现出色，但对其从训练中习得这些能力的底层机制缺乏理论理解。现有理论工作多关注表达能力、统计性质或可学习性，而关于Transformer训练过程中如何通过梯度下降获得多步推理能力的分析较少，尤其缺乏涉及图结构复杂性和多阶段自主切换等真实场景的研究。
- **研究问题**：本文旨在从理论上回答：**一层多头Transformer能否通过梯度下降训练学会符号多步推理（树上的路径搜索）**，并理解不同注意力头如何专业化和自主协调完成子任务。
- **意义**：揭示了CoT如何赋能浅层模型处理通常需要更深架构的任务，为“推理能力的涌现”提供机理层面的解释。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用链式思维（CoT）在自回归生成路径上进行多步推理；通过显式构造和训练动力学分析，证明一层Transformer可以学会从目标节点到根节点的反向推理（单头）以及先反向再正向的两阶段正向推理（两头）。
- **任务设定**：路径搜索任务，树由随机生成的完美二叉树组成，节点嵌入满足线性独立（后强化为正交）。输入为边列表、根节点和目标节点（叶子），输出为目标-根路径（反向推理）或根-目标路径（正向推理），后者需先反向推理再反转路径，并自动切换阶段。
- **模型架构**：
  - 反向推理：一层单头Transformer，参数简化为一个矩阵B，注意力模式通过softmax实现“节点自注意力”，使查询节点只关注自己，从而逐步找到父节点。
  - 正向推理：一层两头Transformer，第一头负责路径遍历（通过切换父-子顺序实现反向和正向行走），第二头负责阶段控制（输出阶段信号sb/sf），当到达根节点时信号切换，触发第二阶段（反向输出变成正向输出）。
- **训练与分析**：
  - 使用标准自回归监督学习，平方误差损失，从零初始化开始梯度下降。
  - 引入多阶段分析（首次训练动力学分析），证明参数收敛到构造解：对角项增长、非对角项保持小，实现所需注意力模式。
  - 给出泛化保证：训练好的模型对未见树可正确推理，说明学习的是规则而非记忆。

### 3. 实验设计：使用了哪些数据集/场景，benchmark，对比方法

- **实验设置**：本文主要是理论分析，附录A提供了一个简单的数值实验验证，没有正式的benchmark和对比方法。
  - 数据集：随机生成的完美二叉树（反向推理：m=4, S=31；正向推理：m=3, S=25），训练集均匀分布在该类树上；测试集随机生成1024棵不同深度和节点数的树（节点从rSs中取唯一标号，孩子数0-3）。
  - 模型：根据文中构造实现一层Transformer（反向：单头；正向：两头），采用one-hot嵌入。
  - 训练：随机梯度下降（batch_size=256），分别使用学习率1和0.2；由于没有期望损失，使用批量随机梯度。
  - 评估：训练曲线和测试损失曲线，以及跟踪关键矩阵（如H, Uₗ, Vₗ）的条目变化。

### 4. 资源与算力

- **未明确说明**：文中没有提及使用的GPU型号、数量或训练时长。数值实验仅描述为简单实验、可在单CPU上运行（附录A中提到“可以在一台CPU上运行”），因此不涉及大规模算力。

### 5. 实验数量与充分性

- **实验数量**：仅附录A展示了少量实验（每个任务一张训练/测试损失曲线图，以及一些参数演化图）。没有进行超参数搜索、消融或与基线方法的对比。
- **充分性**：实验数量有限，但足以定性验证理论预测（训练和测试损失收敛、参数符合构造）。主要贡献在于理论证明，实验只是辅助验证，因此客观性可以接受。但缺乏对泛化性能的定量统计（如误差棒）和更广泛场景的测试。

### 6. 论文的主要结论与发现

- **构造存在性**：存在参数配置使得一层Transformer可以准确完成反向和正向推理（定理1和2）。
- **训练收敛性**：梯度下降从零初始化出发，可实现训练损失收敛到0（定理3和5），参数收敛到构造解。
- **泛化保证**：训练好的模型对未见树也有高准确率，反向和正向推理的测试损失可被边界化（定理4和6）。
- **多头专业化**：正向推理中，两个头分别学习路径遍历和阶段控制，自主协调实现两阶段切换。
- **深度“替代”**：CoT通过增加推理步数，使得浅层模型能完成本需深层的推理，呼应自回归训练中的“扩展中间步骤”现象。

### 7. 优点：方法或实验设计上的亮点

- **理论深度**：提供了完整的训练动力学分析，包括多阶段相位分析，展示了从零到收敛的全过程。
- **可解释性**：揭示了多头注意力的专业化分工（路径头 vs 阶段头），为理解Transformer内部机制提供直观视角。
- **泛化证明**：证明了模型学到的规则可迁移到不同结构的树上，超越了简单记忆。
- **实验佐证**：虽然简单，但实验曲线与理论预测一致，增强了理论的可信度。

### 8. 不足与局限

- **实验覆盖不足**：仅基于完美二叉树训练，泛化测试也只涵盖了随机树（孩子数0-3），未测试更复杂图（如非树、有环）或更大规模；未与多层Transformer、其他算法模型对比。
- **假设较强**：节点嵌入假设正交/线性独立；树结构为完美二叉树；训练分布均匀；学习率足够小。这些假设在实际中可能难以满足。
- **偏差风险**：理论分析中忽略了一些数值细节（如softmax的指数效应），只提供渐近收敛性，没有考虑有限精度或近似误差。
- **应用限制**：推理步数需事先知道路径长度，未能处理未知长度的情况；仅考虑确定性符号推理，未涉及概率性/噪声环境。
- **资源信息缺失**：未报告计算开销，不利于实际复现。

（完）
