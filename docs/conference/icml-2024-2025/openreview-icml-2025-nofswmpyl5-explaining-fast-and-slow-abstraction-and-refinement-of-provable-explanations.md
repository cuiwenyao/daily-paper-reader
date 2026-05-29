---
title: "Explaining, Fast and Slow: Abstraction and Refinement of Provable Explanations"
title_zh: 快与慢的解释：可证明解释的抽象与细化
authors: "Shahaf Bassan, Yizhak Yisrael Elboher, Tobias Ladner, Matthias Althoff, Guy Katz"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=nOfSWmPYL5"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过抽象细化提供神经网络的可证明解释
tldr: 针对神经网络后验解释缺乏形式化保证的问题，提出一种抽象-细化技术，通过神经网络验证高效计算可证明充分的输入特征子集。该方法在保持解释形式保证的同时大幅提升计算效率，实验验证了其在多个数据集上的有效性，为可解释AI提供了可靠性保障。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1770, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1390, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1692, \"height\": 893, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1409, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1393, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1432, \"height\": 954, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1452, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1405, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 894, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1764, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nofswmpyl5/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1061, \"height\": 555, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 1085, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 476, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1551, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 788, \"height\": 411, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 786, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1357, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1251, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 699, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 954, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nofswmpyl5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 787, \"height\": 236, \"label\": \"Table\"}]"
motivation: 现有后验解释方法缺乏形式化保证，而可证明解释的计算代价高昂。
method: 提出抽象-细化技术，在神经网络验证中逐步细化解释特征子集。
result: 在多个基准上显著加速可证明解释的计算，同时保持形式保证。
conclusion: 该方法为神经网络的可靠可解释性提供了高效的形式化方案。
---

## Abstract
Despite significant advancements in post-hoc explainability techniques for neural networks, 
many current methods rely on heuristics and do not provide formally provable guarantees over the explanations provided. 
Recent work has shown that it is possible to obtain explanations with formal guarantees by identifying subsets of input features 
that are sufficient to determine that predictions remain unchanged
using neural network verification techniques.
Despite the appeal of these explanations, their computation faces significant scalability challenges. 
In this work, we address this gap by proposing a novel abstraction-refinement technique for efficiently computing provably sufficient explanations of neural network predictions. 
Our method *abstracts* the original large neural network by constructing a substantially reduced network, 
where a sufficient explanation of the reduced network is also *provably sufficient* for the original network, 
hence significantly speeding up the verification process. 
If the explanation is insufficient on the reduced network, we iteratively *refine* the network size by gradually increasing it until convergence.
Our experiments demonstrate that our approach enhances the efficiency of obtaining provably sufficient explanations for neural network predictions while additionally providing a fine-grained interpretation of the network's predictions across different abstraction levels.

---

## 论文详细总结（自动生成）

### 论文总结：Explaining, Fast and Slow: Abstraction and Refinement of Provable Explanations

#### 1. 核心问题与整体含义（研究动机和背景）
- **问题**：现有神经网络后验解释方法（如 LIME、SHAP、Anchors、SIS）依赖启发式采样，缺乏形式化保证；而基于验证的充分解释方法（如 VeriX）虽能提供可证明保证，但计算代价高昂（NP-complete），尤其在高维输入和大模型上难以扩展。
- **背景**：神经网络的不可解释性阻碍其在安全关键领域应用。最小充分解释（Minimal Sufficient Explanation）被普遍认为更具意义，但求解时需要多次调用验证查询，复杂度与输入维度线性相关，进一步加剧计算瓶颈。
- **整体含义**：本文首次将形式化方法中的抽象-细化（Abstraction-Refinement）技术引入可解释性，提出一种兼顾效率与保证的计算框架，为安全关键场景下神经网络的可靠解释提供了可行方案。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：通过神经元合并（neuron merging）构建一个显著减小的抽象神经网络，使得在该抽象网络上找到的充分解释在原网络上也是**可证明充分**的；若该解释在抽象网络上不充分，则逐步细化（即拆分合并的神经元）增大网络，直到获得最小充分解释。
- **关键技术细节**：
  - **抽象网络构建**：基于类似区间传播的方法，将行为相似的神经元（例如饱和的 sigmoid 神经元）合并为一个神经元，并通过 Minkowski 和（Minkowski sum）紧致地包裹误差，确保原网络输出包含在抽象网络输出集内。
  - **充分性传递性**（Proposition 1）：抽象网络上的充分解释 ⇒ 原网络上的充分解释。
  - **细化机制**（Proposition 2）：细化后的网络（ρ'' > ρ'）产生更紧的边界，且其输出集严格包含在原抽象网络输出集内；因此细化后的充分解释是更小的子集。
  - **算法流程**（Algorithm 2，Greedy Minimal Abstract Explanation Search）：
    1. 初始化 S = [n]（全部特征）。
    2. 对每个特征 i，构建当前查询下的抽象网络 f'。
    3. 检查 S \ {i} 是否在 f' 上充分：
       - 若充分 → 移除 i。
       - 若不充分 → 提取反例并检查在原网络上的输出：
         - 若反例真实（分类改变）→ i 必须保留。
         - 若反例是虚假的（抽象过粗）→ 细化抽象网络（ρ 增加 10%），重复步骤。
    4. 最终返回 S，满足原网络上的最小充分性。
  - **复杂度**：O((n + ξ)·max_t)，其中 ξ 为细化次数，max_t 为单次验证的最长时间；通过粗抽象处理多数特征，大幅降低 max_t。

#### 3. 实验设计
- **数据集与场景**：
  - 图像分类：MNIST（784 像素，灰度）、CIFAR-10（32×32×3 RGB，像素级解释）、GTSRB（32×32×3 交通标志，含物体检测标注）。
  - 回归任务：TaxiNet（安全关键航空导航系统，用于评估回归场景泛化性）。
  - 语言任务：safeNLP（医学安全 NLP，嵌入空间扰动）。
- **Benchmark / 对比方法**：
  - **标准验证方法**（Algorithm 1，Greedy Minimal Explanation Search over original network），即传统逐一特征删除+验证。
  - **启发式方法**：Anchors（Ribeiro et al., 2018）和 SIS（Carter et al., 2019），无形式保证。
  - **缩减率基线**：固定 ρ = 10%, 20%, ..., 90% 的抽象网络（不细化）作为比较。
- **评估指标**：解释大小（越小越好）、累积计算时间、充分性比例、时效内可达到的解释大小（Timeout: MNIST 100s, CIFAR-10 1000s, GTSRB 10000s）。

#### 4. 资源与算力
- 文中**未明确说明 GPU 型号、数量或训练时长**，仅提及使用 CORA（Althoff, 2015）作为后端神经网络验证器，并未说明计算硬件细节。因此无法评估具体算力消耗。推测验证过程主要依赖 CPU 或有限加速，且不涉及模型训练（模型来自 VNN-COMP 或预训练）。

#### 5. 实验数量与充分性
- **实验数量**：
  - 主实验：三个图像数据集（MNIST, CIFAR-10, GTSRB）分别对比标准方法、启发式方法和不同固定 ρ 基线（每个数据集至少 100 张图像，如 Tab.2 所示）。
  - 消融实验：
    - 不同扰动半径（ϵ = 0.007 至 0.012）× 1 个数据集（MNIST）。
    - 不同特征排序（敏感性、Shapley、顺序）× 1 个数据集。
    - 不同激活函数（ReLU vs Sigmoid）× 三个数据集。
    - 不同网络大小（小、中、大）× CIFAR-10。
  - 扩展实验：回归任务（TaxiNet）和语言任务（safeNLP），验证通用性。
- **充分性评价**：实验设计较为全面，覆盖了主要基准、多种网络架构、多种特征选择策略，并提供了量化结果和可视化（图 4-6, 10-15）。对比方法包括最先进的验证方法和经典启发式方法，公平性合理。但所有网络规模中等（最大约数百万参数），未涉及超大模型（如 ResNet-152、Transformer），存在应用上限。

#### 6. 主要结论与发现
- **效率提升显著**：抽象-细化方法相比标准验证方法，累积时间降低 36%~56%，在相同超时下获得更小的解释（例如 MNIST: 204.4 vs 408.7；CIFAR-10: 308.2 vs 448.7；GTSRB: 230.6 vs 502.4）。
- **形式保证优于启发式**：Anchors 和 SIS 的充分性比例 ≤25%（MNIST 25%, CIFAR-10 3%, GTSRB 17%），而本方法始终 100% 充分且可证明。
- **多粒度解释**：通过逐步细化，用户能在每个抽象层级获得一个充分解释，实现“早停”权衡效率与解释大小，同时提供了模型预测的细粒度理解。
- **泛化性**：在回归（TaxiNet）和语言（safeNLP）任务上同样有效，特别是 TaxiNet 上将验证时间从约 8815 秒降至约 36 秒。

#### 7. 优点（方法或实验设计亮点）
- **创新性**：首次将抽象-细化引入解释性领域，提供了理论保证（Proposition 1-5）且具备实用加速。
- **效率与质量双赢**：相比标准方法大幅加速，同时获得同等或更小的解释（因粗抽象先处理易移除特征）。
- **可解释性增强**：提供不同细化阶段的解释，帮助用户理解网络决策的层级依赖性。
- **实验覆盖全面**：不仅对比了多种方法，还针对不同激活函数、网络大小、特征顺序和不同任务域做了消融，有效证明了方法的鲁棒性和泛化能力。
- **开源与可复现**：基于 CORA 实现，代码和模型配置有描述（附录 B）。

#### 8. 不足与局限
- **依赖验证工具可扩展性**：方法性能直接受限于底层验证器（CORA）的能力，目前仅处理中小规模网络；对于当代大型模型（如 Vision Transformer, GPT）仍不适用。
- **仅关注最小充分解释**：未探索其他解释类型（如对比解释、因果解释），通用性有局限（论文承认可在未来扩展）。
- **特征顺序敏感**：虽然进行了消融（敏感性 vs Shapley vs 顺序），但结果仍然显示出排序影响解释大小（敏感性最佳），说明需预先计算敏感度，增加额外开销。
- **实际应用偏移风险**：仅评估了三个图像数据集和一个回归/语言数据集，未涉及真实生产环境中的复杂任务（如医疗影像、自动驾驶），解释的实用性有待验证。
- **算力信息缺失**：未报告具体硬件配置或能耗，难以客观评判工程成本。

（完）
