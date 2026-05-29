---
title: "Verification Learning: Make Unsupervised Neuro-Symbolic System Feasible"
title_zh: 验证学习：实现无监督神经符号系统可行
authors: "Lin-Han Jia, Wen-Chao Hu, Jie-Jing Shao, Lan-Zhe Guo, Yu-Feng Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=aAkq9mMviY"
tags: ["query:ns-xai"]
score: 9.0
evidence: 通过验证实现无监督神经符号学习
tldr: 本文提出验证学习范式，将神经符号学习中依赖标签的推理过程转换为无标签验证过程，仅依靠未标记数据和规则验证函数即可学习。形式化为约束优化问题并设计动态组合排序算法，解决了无监督神经符号学习的可行性难题，拓展了神经符号系统的应用范围。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-aakq9mmviy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aakq9mmviy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1746, \"height\": 601, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-aakq9mmviy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1547, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aakq9mmviy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 888, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aakq9mmviy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 887, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aakq9mmviy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 890, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aakq9mmviy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1834, \"height\": 388, \"label\": \"Table\"}]"
motivation: 现有神经符号学习过度依赖标签数据，无标签情况下符号信息不足、解空间大。
method: 提出验证学习范式，将推理转为验证，用约束优化和动态组合排序算法求解。
result: 仅用无标注数据和规则验证就能取得优秀学习结果。
conclusion: 验证学习使无监督神经符号系统可行，降低了标签依赖。
---

## Abstract
The current Neuro-Symbolic (NeSy) Learning paradigm suffers from an over-reliance on labeled data, so if we completely disregard labels, it leads to less symbol information, a larger solution space, and more shortcuts—issues that current Nesy systems cannot resolve. This paper introduces a novel learning paradigm, Verification Learning (VL), which addresses this challenge by transforming the label-based reasoning process in Nesy into a label-free verification process. VL achieves excellent learning results solely by relying on unlabeled data and a function that verifies whether the current predictions conform to the rules. We formalize this problem as a Constraint Optimization Problem (COP) and propose a Dynamic Combinatorial Sorting (DCS) algorithm that accelerates the solution by reducing verification attempts, effectively lowering computational costs and introduce a prior alignment method to address potential shortcuts. Our theoretical analysis points out which tasks in Nesy systems can be completed without labels and explains why rules can replace infinite labels for some tasks, while for others the rules have no effect. We validate the proposed framework through several fully unsupervised tasks including addition, sort, match, and chess, each showing significant performance and efficiency improvements.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：现有神经符号（NeSy）学习系统严重依赖标注数据（标签Y）。在完全无标签的**无监督NeSy**场景下，会遇到三大挑战：①符号信息缺失（无法从答案推导符号）；②解空间指数级扩大（如加法从10²变为10⁴）；③捷径问题（大量无意义组合也能满足规则）。这使得传统NeSy方法（DeepProblog、ABL等）在无监督下几乎不可行。
- **目标**：提出一种仅依赖无标签数据与规则验证函数的全新学习范式——**验证学习（Verification Learning, VL）**，使无监督NeSy成为可能。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将传统NeSy中**从标签Y开始的符号推理**转换为**无标签的约束满足验证**。即模型输出符号序列S后，直接验证S是否满足规则库KB（`V_KB(S)→True/False`），以此替代复杂的逻辑推理与候选解枚举。
- **技术细节**：
  1. **形式化为约束优化问题（COP）**：目标是在所有满足`V_KB`的可行解中，寻找使目标函数`Score(S)`最大的解。`Score`可以是独立假设下的置信度乘积，或非独立假设下的一致性得分。
  2. **动态组合排序算法（DCS）**：
     - 在**独立性假设**（`Score(S)=∏score(s_i)`）下，通过维护一个堆（heap）按分数降序生成候选解，首个通过验证的解即为全局最优。算法复杂度为`O(K(log K + l log l + k log k))`，K为最优解排名。
     - 扩展到**单调性假设**（更宽松）：只要每个位置上符号的优先级满足固定全序，DCS仍能保证最优解。证明了单调性是COP可被次指数算法求解的充要条件。
  3. **分布对齐（Distribution Alignment）**：为缓解无监督下的捷径与坍塌问题，对模型输出概率进行修正：`g(X)_{i,j} = l·P_{s_j}·g(X)_{i,j} / Σ_k g(X)_{k,j}`。通过引入符号自然分布（未知时可用均匀分布）作为先验，迫使模型输出分布分散。
  4. **理论分析**：用群论分析任务可解性。通过规则库的对称群`G`对符号集进行轨道分解，**固定点**（单元素轨道）可被区分，非固定点则产生本质误差。如加法任务所有符号均为固定点（无对称性），故理论可解（`R_up=0%`）；数独任务全排列对称，理论准确率上限为0%。

### 3. 实验设计
- **数据集/场景**：
  - **Addition**：手写数字加法（2~10进制），无标签。
  - **Sort**：数字图像排序（长度4~8）。
  - **Match**：字符序列匹配（字符类别数6~10）。
  - **Chess**：棋盘棋子类型识别（2~6类棋子，按规则移动）。
- **基准（Benchmark）**：扩展自DeepProblog/DeepStochlog/ABL等原有监督任务，但移除标签。
- **对比方法**：DeepProblog、DeepStochlog、NeurASP、Ground ABL、A3BL。对原为监督的方法，使用`[True,False]`（是否符合规则）作为伪标签。
- **消融实验**：对比VL的4个变体：
  - `VL_⊥`：独立假设，Score=置信度乘积。
  - `VL_⊥+TTC`：使用测试时修正（先验证再输出）。
  - `VL_̸⊥`：非独立假设，Score=一致性+置信度。
  - `VL_̸⊥+TTC`：非独立+测试时修正。

### 4. 资源与算力
- 文中明确说明：所有实验在**4块NVIDIA A800 GPU**上完成，统一设置**10个训练epoch**，使用LeNet作为感知模块，学习率0.001、Adam优化器。未给出单任务具体耗时，但在表5给出Addition任务的时间对比（单位秒）。

### 5. 实验数量与充分性
- **实验数量**：在4个任务上分别测试多个参数（Addition：2~10进制共9组；Sort：长度4~8共5组；Match：类别数6~10共5组；Chess：棋子种类数2~6共5组），总计**24组主实验**。同时包含消融（4个变体）和对比（5种SOTA方法）。
- **充分性**：较充分。覆盖多种规则类型（算术、排序、匹配、棋类），且参数变化多样性高。消融实验验证了独立/非独立假设以及TTC的影响。对比方法在相同设置下运行，但部分方法（NeurASP超时、DeepStochlog内存超限）导致比较不完整。
- **客观性与公平性**：文中指出对比方法在无监督设置下表现极差，而VL显著优于所有对照。但需注意：对比方法多基于监督场景设计，直接改为无监督可能未达最优；另外，表格中VL某些组（如Addition 7)准确率略低，作者归因于规则对称性，尚属客观。

### 6. 论文的主要结论与发现
- VL范式使无监督NeSy**从不可行变为可行**，仅凭规则验证即可学习符号表示，在加法、排序、匹配、国际象棋任务上均取得接近或达到100%的准确率。
- 理论揭示：任务可解性取决于规则库的对称群——**固定点符号可被区分**，非固定点产生本质误差上限。因此**加法、棋盘任务可解，数独任务不可解**。
- DCS算法保证了在单调性条件下**以次指数复杂度找到全局最优解**，且验证次数远少于穷举。
- 分布对齐有效缓解无监督下的捷径坍塌问题，且不依赖真实分布（均匀分布先验即可）。

### 7. 优点
- **创新性强**：首次提出验证范式替代推理，从根本上解决无监督NeSy的起点缺失问题。
- **算法高效且保证最优**：DCS在单调性下全局最优，复杂度低；而传统方法需枚举全部候选解（指数级）。
- **理论深度高**：用群论严格刻画任务可解性，给出泛化误差上界，为无监督NeSy提供了坚实理论支撑。
- **实验覆盖广**：4个迥异的规则任务，多种参数，消融充分，且代码开源。
- **实用性**：验证函数仅需简单Python代码，无需专家逻辑编程，易于扩展。

### 8. 不足与局限
- **理论限制**：对于完全对称的任务（如数独），VL理论上无法区分符号，准确率为0%，无法实用。
- **对单调性的依赖**：若Score不满足单调性，DCS无法保证求解效率，算法退化为指数搜索。论文未讨论非单调场景下的替代方案。
- **分布对齐依赖先验**：当符号自然分布与均匀分布差异极大时，可能导致偏差；文中未评估先验不匹配的影响。
- **对比实验公平性**：部分对比方法在无监督设置下可能未调优（例如将监督框架硬改为无监督），且出现TLE/MLE，导致比较不完整。论文未提供对比方法的非官方优化细节。
- **实验规模**：虽然任务多样，但均为合成/简单视觉任务（MNIST数字、棋盘），未在真实复杂场景（如自然图像推理）中验证。
- **未讨论验证函数错误（噪声规则）的影响**：假设规则完全正确，实际应用中规则可能不完善。

（完）
