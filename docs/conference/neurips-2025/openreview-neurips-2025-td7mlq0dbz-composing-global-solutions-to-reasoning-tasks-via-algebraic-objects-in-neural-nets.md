---
title: Composing Global Solutions to Reasoning Tasks via Algebraic Objects in Neural Nets
title_zh: 通过神经网络中的代数对象组合推理任务的全局解
authors: Yuandong Tian
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tD7MLq0dbZ"
tags: ["query:ns-xai"]
score: 7.0
evidence: 神经网络中用于符号推理任务的代数结构
tldr: 针对群论推理任务（如模加法），本文证明两层神经网络的解空间具有丰富的代数结构（半环），并利用该结构从仅满足部分损失的局部解解析地构造全局最优解。该工作揭示了神经网络中符号推理的代数本质，为理解神经符号组合提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1316, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1317, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1167, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1170, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1320, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1424, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1318, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1318, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1320, \"height\": 551, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1328, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1604, \"height\": 1113, \"label\": \"Table\"}]"
motivation: 神经网络如何求解符号推理任务（如模加法）的全局最优解仍不清晰。
method: 证明两层网络的权重空间具有半环结构，利用同态性从局部解构建全局解。
result: 解析构造了全局最优解，验证了代数结构的有效性。
conclusion: 该工作为神经网络的符号推理能力提供了代数解释。
---

## Abstract
We prove rich algebraic structures of the solution space for 2-layer neural networks with quadratic activation and $L_2$ loss, trained on reasoning tasks in Abelian group (e.g., modular addition). Such a rich structure enables \emph{analytical} construction of global optimal solutions from partial solutions that only satisfy part of the loss, despite its high nonlinearity. We coin the framework as \ours{} (\emph{\underline{Co}mposing \underline{G}lobal \underline{S}olutions}). Specifically, we show that the weight space over different numbers of hidden nodes of the 2-layer network is equipped with a semi-ring algebraic structure, and the loss function to be optimized consists of \emph{sum potentials}, which are ring homomorphisms, allowing partial solutions to be composed into global ones by ring addition and multiplication. Our experiments show that around $95\%$ of the solutions obtained by gradient descent match exactly our theoretical constructions. Although the global solutions constructed only required a small number of hidden nodes, our analysis on gradient dynamics shows that overparameterization asymptotically decouples training dynamics and is beneficial. We further show that training dynamics favors simpler solutions under weight decay, and thus high-order global solutions such as perfect memorization are unfavorable. The code is open sourced\footnote{\url{https://github.com/facebookresearch/luckmatters/tree/yuandong3/ssl/real-dataset}}.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将根据您提供的论文内容，对其进行分析并生成一份结构化的中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLMs）在推理任务（如算术）中表现令人惊讶，但其内部工作机制尚不清晰。现有研究多通过观察指标或逆向工程提取训练好的模型的内在结构，缺乏一个系统性的理论框架来解释和推广这些发现。
- **核心问题**：如何理解和解析神经网络在符号推理任务（如模加法）中学习到全局最优解的过程？特别是，能否不依赖于复杂的梯度下降过程，而是通过解析方式直接构造出这些解？
- **整体含义**：本文提出了一个名为 **CoGS** 的理论框架，证明了在解决阿贝尔群（Abelian group）乘法推理任务时，两层神经网络的解空间存在丰富的代数结构（半环结构）。利用这个结构，可以将仅满足部分损失函数的“局部解”通过代数运算（环加法与环乘法）组合成全局最优解。这为理解神经网络的符号推理能力提供了一个全新的代数视角。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：本文的核心洞察是，两层网络的权重空间（不同宽度网络的聚合）天然具有半环（semi-ring）代数结构。而损失函数（MSE损失）中的关键项——“和势”（Sum Potentials, SPs）——是环同态（ring homomorphisms），即它们尊重加法与乘法运算。
- **关键技术细节**：
    1.  **问题形式化**：将任务建模为预测阿贝尔群乘法结果 \( l = g_1 \cdot g_2 \)。网络采用带二次激活（\( \sigma(x) = x^2 \)）的两层MLP。作者在傅里叶域中分析权重，证明损失函数可以分解为多个“和势”（如 \( r_{k_1 k_2 k} \) 和 \( r^p_{k_1 k_2 k} \)）的函数。
    2.  **半环结构**：定义了两个操作：`加法 (+)`（权重沿隐藏层维度拼接）和 `乘法 (*)`（权重沿隐藏层维度的克罗内克积）。证明了权重空间 \( Z \) 在这些操作下形成一个交换半环。
    3.  **和势与环同态**：证明每一个“和势”（如 \( r(z) \)）都是从权重空间 \( Z \) 到复数域 \( C \) 的环同态。这意味着 \( r(z_1 + z_2) = r(z_1) + r(z_2) \) 且 \( r(z_1 * z_2) = r(z_1) \cdot r(z_2) \)。
    4.  **组合局部解（CoGS 核心流程）**：
        - **定义“0/1集”**：定义一个“好”的全局解需要满足一组约束，即某些SP为0，某些SP为1。
        - **构造局部解**：利用一个频段上的“生成器” \( u \)（一个单隐节点解），通过定理4（多项式构造）构造出满足部分约束的局部解（见表1）。
        - **组合成全局解**：利用环同态的性质（引理2），通过环乘法将满足不同约束的两个局部解组合起来，即可得到一个满足所有约束的全局解。
    5.  **构造的全局解实例**：
        - **\( 2 \times 3 \) 傅里叶解 (\( z_{F6} \))**：每个频率关联6个隐藏节点，通过组合 \( 3 \) 阶局部解 (例如 \( z_{syn} \)) 与 \( 2 \) 阶局部解 (例如 \( z_\nu \)) 得到。
        - **完美记忆解 (\( z_M \))**：通过组合两个 \( d \) 阶局部解得到，总共需要 \( d^2 \) 个隐藏节点。
        - **混合 \( 2 \times 2 / 2 \times 3 \) 解 (\( z_{F4/6} \))**：一种更低阶的全局解，绝大多数频率关联4个节点，仅一个频率关联6个节点。
    6.  **动力学分析**：
        - **奥卡姆剃刀偏好**：证明了如果高阶解和低阶解均为全局最优，则存在一条零损失路径连接它们，且低阶解具有更小的L2范数，因此在权重衰减下更受青睐（定理5）。
        - **无限宽度下的解耦**：证明了在无限宽度初始化下，和势的梯度动力学是解耦的（定理6），解释了过参数化的益处。

### 3. 实验设计：数据集、Benchmark与对比方法

- **数据集**：使用**模加法（Modular Addition）**任务。这等价于预测循环群 \( G \) 的乘法结果。数据是合成生成的，并按 90%/10% 分割为训练集和测试集。测试了不同的群大小 \( d \in \{23, 71, 127\} \)。
- **Benchmark**：论文的核心是与自身提出的理论解进行对比。不是标准意义上的“方法”对比。
- **对比方法**：本文没有直接对比其他现有方法。它的核心贡献是提出理论框架并验证其正确性。实验对比的是**由梯度下降（Adam优化器）训练得到的解的结构与论文理论构造的解是否匹配**。

### 4. 资源与算力

- 文中明确提到了计算资源：每个超参数配置的实验在 **NVIDIA V100 GPU** 上运行 **“几分钟” (a few minutes)**。但未提供具体的GPU数量、总训练时长或计算成本等更详细的量化信息。
- **总结**：资源要求较低，但信息不够具体。

### 5. 实验数量与充分性

- **实验数量**：
    - 对不同群大小（\( d = 23, 71, 127 \)）进行了实验。
    - 对不同隐藏节点数（宽度 \( q = 256, 512, 1024, 2048 \)）进行了实验。
    - 对不同权重衰减系数（\( wd = 10^{-5} \) 至 \( 5 \times 10^{-4} \)）进行了实验。
    - 多次运行（5个随机种子）取平均值和标准差。
- **充分性分析**：
    - **充分**：实验覆盖了不同任务规模（d）、网络宽度（q）和正则化强度（wd），并系统地统计了解的类型分布（图3, 4, 8-11）。验证了理论预测的几个核心结果：① 95%的解可以分解并匹配理论构造（表2）；② 梯度下降偏好低阶解（权重衰减越大，低阶解越多）；③ 最终解的结构不依赖网络宽度（宽网络下最终解阶数恒定）。
    - **客观公平**：实验设计（如使用傅里叶分析提取解的特征，并穷举搜索匹配理论结构）是比较客观的。论文也诚实地展示了少数不匹配的情况（约2%），并归因于训练不足或接近理论构造。

### 6. 论文的主要结论与发现

1.  **存在丰富的代数结构**：解决阿贝尔群推理任务的两层神经网络的权重空间具有半环结构，而关键的损失项（和势）是环同态。
2.  **全局解可由局部解解析地构造**：利用这种代数结构，可以从满足部分约束的局部解出发，通过环加法和环乘法“组合”出全局最优解。
3.  **框架可以解析地构造已知解**：成功地解析构造了不同类型的全局解，包括“\( 2 \times 3 \)”和“\( 2 \times 2 \)”的傅里叶解，以及完美记忆解。
4.  **梯度下降的解与理论构造高度一致**：约95%的由梯度下降训练得到的解，其结构可以分解并与理论构造的 \( z_{F4/6} \) 或 \( z_{F6} \) 解精确匹配。
5.  **梯度下降的偏好**：
    - **偏好低阶解**：在权重衰减（L2正则化）下，训练动力学倾向于选择更简单的（即隐藏节点数更少的）低阶全局解，而不是高阶的完美记忆解。
    - **过参数化有益无害**：尽管最终构造的解只需要少量节点（每个频率最多6个），但过参数化（使用更大的宽度）并不会阻止模型收敛到这些解，反而能解耦训练动力学。

### 7. 优点：方法与实验设计上的亮点

1.  **理论创新性强**：首次揭示并利用训练过程中神经网络内部的代数结构来解析构造全局解，为理解神经网络的推理能力提供了全新的视角和强大的数学工具。
2.  **理论分析与实验验证紧密结合**：不仅提出了优雅的理论，还通过精心设计的实验（如解结构分解、分布统计）强有力地验证了理论预测与真实梯下降训练结果的一致性，令人信服。
3.  **提供了新的研究方向**：CoGS框架本身就可以作为一种新的范式，即可以不依赖梯度下降，通过“组合”局部解来构造全局解，为设计新颖的训练算法和损失函数开辟了道路。同时，提出了将不同宽度的网络放在统一框架下研究的思路。

### 8. 不足与局限

1.  **模型与任务的限制**：理论仅限于**两层网络**、**二次激活**和**阿贝尔群推理**任务（如模加法）。能否推广到更深、更宽的网络（如Transformer）、其他激活函数或更复杂的推理任务（如非交换群、文本推理），是本工作最大的局限。
2.  **实验覆盖的任务单一**：所有实验都集中在模加法（循环群）这一种任务上。虽然这是很好的起点，但结论的泛化性有待在更多类型的群结构（如非循环阿贝尔群）或群作用预测任务上验证。
3.  **动力学分析仍不完备**：文中虽然给出了动力学偏好的理论分析（定理5）和无限宽度下的简化分析（定理6），但未能完全刻画完整的梯度下降路径，特别是未能解释为什么某些理论可行的解（如 \( z_{3c} * z_{syn} \)）从未在实验中观察到。这种“隐式偏差”的具体原因尚不明确。
4.  **完美记忆解的连接路径未证明**：虽然定理5理论上证明了低阶解更优，但并未证明存在一条从完美记忆解到低阶解的零损失路径，因此不能严格说训练必然偏向于低阶解。
5.  **计算资源的量化信息不足**：尽管这并非核心贡献，但可以提供更详细的算力报告（如总GPU小时数）以增强论文的完整性和实用性。

（完）
