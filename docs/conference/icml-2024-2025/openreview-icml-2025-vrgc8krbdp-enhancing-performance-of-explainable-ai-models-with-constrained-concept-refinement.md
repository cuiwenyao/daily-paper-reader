---
title: Enhancing Performance of Explainable AI Models with Constrained Concept Refinement
title_zh: 通过约束概念精炼提升可解释AI模型性能
authors: "Geyu Liang, Senne Michielssen, Salar Fattahi"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=VRGc8KrBdP"
tags: ["query:ns-xai"]
score: 7.0
evidence: 基于约束概念精炼提升可解释AI性能
tldr: 针对可解释模型在准确率与可解释性之间的权衡问题，本文提出约束概念精炼框架。通过优化概念嵌入并施加可解释性约束，在保持透明性的同时提升预测性能。在生成模型上理论证明了算法的收敛性，实验显示准确率显著提升。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1312, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 801, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1305, \"height\": 776, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 2157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 1146, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1737, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1734, \"height\": 892, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 322, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 343, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 318, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 855, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 858, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 858, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 362, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 331, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 362, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 855, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 856, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 848, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 514, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 432, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 514, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 774, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 750, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 527, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 381, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 417, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 786, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 794, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 438, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 453, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 440, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 816, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 841, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 820, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 421, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 395, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 778, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 799, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 732, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 396, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 399, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 765, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vrgc8krbdp/fig-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 730, \"height\": 535, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vrgc8krbdp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vrgc8krbdp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 622, \"height\": 290, \"label\": \"Table\"}]"
motivation: 可解释性设计方法常牺牲准确率，概念表示偏差影响性能。
method: 在保持可解释性的约束下优化概念嵌入，提出精炼框架。
result: 理论证明算法收敛性，实验显示准确率提升且可解释性保持不变。
conclusion: 概念精炼能有效缓解可解释性与准确率之间的矛盾。
---

## Abstract
The trade-off between accuracy and interpretability has long been a challenge in machine learning (ML). This tension is particularly significant for emerging *interpretable-by-design* methods, which aim to redesign ML algorithms for trustworthy interpretability but often sacrifice accuracy in the process. In this paper, we address this gap by investigating the impact of deviations in concept representations—an essential component of interpretable models—on prediction performance and propose a novel framework to mitigate these effects. The framework builds on the principle of optimizing concept embeddings under constraints that preserve interpretability. Using a generative model as a test-bed, we rigorously prove that our algorithm achieves zero loss while progressively enhancing the interpretability of the resulting model. Additionally, we evaluate the practical performance of our proposed framework in generating explainable predictions for image classification tasks across various benchmarks. Compared to existing explainable methods, our approach not only improves prediction accuracy while preserving model interpretability across various large-scale benchmarks but also achieves this with significantly lower computational cost.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：可解释性人工智能（XAI）长期面临准确率与可解释性之间的权衡。可解释设计模型（如概念瓶颈模型、信息追求算法）虽然能提供透明、可理解的预测，但往往以牺牲预测性能为代价。
- **背景**：已有研究表明，概念嵌入（concept embeddings）的微小偏差会导致模型性能显著下降（如定理2.6所示）。现存改进方法（如引入额外黑箱模块）会削弱解释性，且缺乏理论保障。
- **整体含义**：本文提出**约束概念精炼（Constrained Concept Refinement, CCR）**框架，在保持可解释性的约束条件下优化概念嵌入，从而在不牺牲透明性的前提下提升预测准确性，并给出理论收敛性证明。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将概念嵌入矩阵 D 作为可优化变量，但限制其更新幅度保持在初始嵌入 D⁰ 附近（ℓ₁,₂ 球约束 ∥ΔD∥₁,₂ ≤ ρ），从而保留原始可解释语义。通过最小化下游任务的损失函数，同时确保优化后的概念嵌入不偏离人类可理解的范围。
- **关键技术细节**：
  - **可微替代估计器**：基于IP-OMP（信息追求-正交匹配追踪），在列正交假设下，IP-OMP的预测简化为稀疏编码与线性层的组合（Lemma 3.1），从而可对 D 求导。
  - **优化与投影**：采用梯度下降更新 D，然后对每一列进行ℓ₂归一化，并投影到初始点邻域内（确保 ∥d_i − d_i⁰∥₂ ≤ ρ）。
  - **概念分散（Concept Dispersion）**：预处理步骤，增加初始概念嵌入之间的正交性，提高稀疏编码质量。
  - **硬阈值（Hard Thresholding）**：替代top‑k选择，实现并行化计算。
- **算法流程**（文字说明）：
  1. 使用CLIP将图像和概念分别嵌入为特征 x 和概念嵌入 D⁰。
  2. 对 D⁰ 进行概念分散。
  3. 初始化线性层 L 和稀疏码 s。
  4. 迭代 T 步：
     - 计算交叉熵损失 Lₘ（稀疏码经线性层后与真实标签的损失）。
     - 梯度更新 D ← D − η_D ∂L/∂D，然后归一化并投影到约束区域。
     - 更新线性层 L ← L − η_L ∂L/∂L。
     - 更新稀疏码 s = HT_λ(Dᵀx)。
  5. 返回优化后的 D、L 和稀疏码。

## 3. 实验设计

- **数据集**：CIFAR-10、CIFAR-100、ImageNet（≈120万图像）、CUB-200（鸟类细粒度）、Places365（≈180万场景图像）。
- **对比方法**：
  - **CLIP-IP-OMP**（Chattopadhyay et al., 2024）：基于信息最大化的正交匹配追踪。
  - **标签自由CBM（lf-CBM）**（Oikarinen et al., 2023）：首个可扩展至ImageNet的概念瓶颈模型。
  - **CCR基线**（无概念精炼，即 η_D = 0）。
- **概念集**：所有方法使用相同的由GPT-3生成的文本概念集。
- **评估指标**：测试准确率、平均解释长度（AEL）、平均稀疏率（ASR）、平均概念嵌入偏差（ACED）。

## 4. 资源与算力

- **实验环境**：NVIDIA Tesla V100 GPU（用于CCR），RTX A5000 GPU（用于对比方法）。
- **训练时长**（以ImageNet为例）：
  - CCR：约2小时（200次迭代，平均解释长度≈49）。
  - CLIP-IP-OMP（k=50）：约33小时（相同GPU），若降低k至10则需约6小时但准确率大幅下降至63%。
  - lf-CBM：约50小时（RTX A5000）。
- **结论**：CCR在保持更高准确率的同时，计算成本降低一个数量级以上。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：5个数据集，每个数据集运行5次取均值与极差（图2）。
  - 消融实验：移除概念分散（Algorithm 3）或投影（Algorithm 4）共2组，评估准确率、稀疏性、列偏差（图6）。
  - 超参数调优：阈值λ（3个数据集，图7）、半径ρ（3个数据集，图8），展示其对稀疏性与准确率的影响。
  - 可解释性案例：每个数据集选取3个样本展示概念得分与权重（共15组，图9‑23），并对比基线（图24‑28）。
  - 生成模型验证：3组模拟实验（单样本、列不满秩、满秩），验证理论（图4）。
- **充分性与客观性**：
  - 实验涵盖小规模（CIFAR）到大规模（ImageNet/Places365）图像分类任务，覆盖常见基准。
  - 所有对比方法使用相同概念集，且CCR基线未精炼，确保公平性。
  - 多次运行并报告范围，体现稳定性。
  - 消融与超参分析说明各组件贡献。
  - 局限：缺乏在非图像任务（如NLP、医疗）上的验证；与更多CBM变体（如Post-hoc CBM）的比较未提及。

## 6. 论文的主要结论与发现

- **理论层面**：
  - 定理3.3：在生成模型与单样本下，CCR可将损失线性收敛至零。
  - 定理3.4：在多样本且字典满秩条件下，CCR能同时逼近真实概念嵌入（可解释性提升）和实现零损失（准确率最优）。
- **实验层面**：
  - CCR在CIFAR-10/100、ImageNet、Places365上均超越CLIP-IP-OMP和lf-CBM，仅在CUB-200上略低于lf-CBM（原因：lf-CBM基于专为CUB-200训练的ResNet‑18，而CCR依赖通用CLIP）。
  - 计算效率显著提升（ImageNet上快15‑25倍）。
  - 可解释性案例显示：模型能够捕获语义相关概念，并正确赋予权重，甚至能诊断错误预测的原因。

## 7. 优点

- **方法设计简洁有效**：直接在概念嵌入上优化，无需额外黑箱模块，保持本质可解释性。
- **理论保障**：首次为该类方法提供收敛性与可解释性同时优化的理论证明。
- **计算高效**：硬阈值和并行化设计使训练速度大幅提升。
- **可解释性保持良好**：通过约束更新半径（ρ=0.1）确保概念嵌入变化微小，语义仍可被人类理解。
- **实验充分**：涵盖多个规模的数据集，包含消融、超参分析、可解释性案例，验证方法鲁棒性。

## 8. 不足与局限

- **依赖CLIP嵌入质量**：CLIP本身存在偏差和噪声，可能影响初始概念质量。
- **概念集由GPT-3生成**：可能遗漏关键判别性概念（如CUB-200案例，无法区分相似物种的细微特征）。
- **理论假设较强**：生成模型假设列正交、稀疏编码等，实际场景未必完全满足。
- **超参数敏感**：半径ρ需要手动调整，未提供自适应选择策略。
- **仅在图像分类上验证**：未在文本、医学影像、时间序列等任务中测试，泛化性有待考察。
- **与lf-CBM在CUB-200上的差距**：说明在特定领域上，专用后端仍具优势，CCR的通用性可能不足。

（完）
