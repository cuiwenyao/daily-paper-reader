---
title: "FACE: Faithful Automatic Concept Extraction"
title_zh: FACE：忠实的自动概念提取方法
authors: "Dipkamal Bhusal, Michael Clifford, Sara Rampazzi, Nidhi Rastogi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ssocZIfk94"
tags: ["query:ns-xai"]
score: 7.0
evidence: 忠实的自动概念提取用于模型可解释性
tldr: 现有概念发现方法常导致解释不忠实。本文提出FACE框架，结合非负矩阵分解和KL散度正则化，在概念学习中加入分类器监督，确保概念预测与原模型对齐。实验证明FACE提取的概念更忠实于模型决策，增强了可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1408, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 687, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 732, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1409, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1378, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1377, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 647, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1443, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1347, \"height\": 1086, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1276, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1403, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1362, \"height\": 1111, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1278, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1405, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1442, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1438, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ssoczifk94/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1279, \"height\": 2149, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1029, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1320, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1465, \"height\": 108, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1468, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 971, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 671, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1437, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1110, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ssoczifk94/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1290, \"height\": 254, \"label\": \"Table\"}]"
motivation: 已有概念提取方法未与模型真实决策对齐，解释缺乏忠实性。
method: 提出FACE框架，使用NMF和KL正则化，在概念学习过程中融入分类器监督。
result: FACE提取的概念与模型原始预测一致，忠实度优于现有方法。
conclusion: 将分类器监督纳入概念学习可显著提升解释忠实性。
---

## Abstract
Interpreting deep neural networks through concept-based explanations offers a bridge between low-level features and high-level human-understandable semantics. However, existing automatic concept discovery methods often fail to align these extracted concepts with the model’s true decision-making process, thereby compromising explanation faithfulness. In this work, we propose FACE (Faithful Automatic Concept Extraction), a novel framework that combines Non-negative Matrix Factorization (NMF) with a Kullback-Leibler (KL) divergence regularization term to ensure alignment between the model’s original and concept-based predictions. Unlike prior methods that operate solely on encoder activations, FACE incorporates classifier supervision during concept learning, enforcing predictive consistency and enabling faithful explanations. We provide theoretical guarantees showing that minimizing the KL divergence bounds the deviation in predictive distributions, thereby promoting faithful local linearity in the learned concept space. Systematic evaluations on ImageNet, COCO, and CelebA datasets demonstrate that FACE outperforms existing methods across faithfulness and sparsity metrics.

---

## 论文详细总结（自动生成）

# 论文总结：FACE: Faithful Automatic Concept Extraction

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有自动概念发现方法（如ACE、ICE、CRAFT）在提取深度神经网络的可解释概念时，仅关注编码器激活的重建，忽略了分类器的下游预测行为。这导致提取的概念虽在视觉上可理解，却可能偏离模型真正的决策过程，即**解释的忠实性不足**。
- **背景**：概念解释方法旨在用人类可理解的语义概念（如“皮毛”“耳朵”）解释模型预测，但早期方法依赖人工标注（如TCAV），可扩展性差；无监督方法（如ACE、ICE、CRAFT）通过聚类或矩阵分解自动发现概念，但均未约束概念表示与模型预测的一致性，导致解释可能误导用户。
- **含义**：缺乏忠实性会削弱用户对模型行为的信任，尤其在医疗等高风险领域。因此，**确保概念解释忠实反映模型实际推理**是本文的核心动机。

## 2. 方法论：核心思想、技术细节
- **核心思想**：在非负矩阵分解（NMF）框架中引入**KL散度正则化项**，强制概念重建后的激活与原始激活在分类器输出上保持一致，从而学习既保留激活结构又对齐预测语义的概念表示。
- **技术细节**：
  - **框架定义**：将分类器 `f` 分解为编码器 `g`（提取激活 `A`）和分类头 `h`（将激活映射为logits）。对同一类所有正确分类样本的激活矩阵 `A` 进行分解：`A ≈ UW^T`，其中 `U` 为系数矩阵，`W` 为字典（概念基）。
  - **优化目标**（公式2）：
    ```
    min_{U≥0, W≥0}  0.5 * ||A - UW^T||_F^2 + λ * KL( softmax(h(A)) || softmax(h(UW^T)) )
    ```
    第一项为重建误差，第二项为原始与重建预测分布之间的KL散度，λ控制两者权衡。
  - **优化方法**：使用投影梯度下降（Projected Gradient Descent）交替更新U、W，非负约束通过投影实现；初始化采用非负双奇异值分解（NNDSVD）加速收敛。
  - **理论保证**：
    - 由Pinsker不等式：KL( p || q ) ≤ ε ⇒ 总变差距离 V_T ≤ √(2ε)，即约束KL散度直接限制预测偏差。
    - KL正则化促进概念空间中的局部线性性，使模型输出对概念操纵的变化可预测。
  - **与现有NMF对比**：标准NMF仅优化重建误差，可能保留高方差但非预测性方向；FACE通过KL项确保重建激活保持原始预测分布，即使重建误差略高也优先保障忠实性。

## 3. 实验设计
- **数据集与模型**：
  - ImageNet（1000类，使用其中10类做详细评估）、COCO（200类，使用其中5类）、CelebA（4个互斥属性：黑发、金发、灰发、戴帽）。
  - 目标模型：ResNet-34、MobileNetV2（均为CNN架构）。
- **对比方法**：ICE（NMF方法）、CRAFT（递归NMF方法）、ACE（聚类方法，仅部分对比）。
- **评估指标**：
  - 矩阵分解质量：重建误差（MSE）、预测一致性（KL散度 D_KL）。
  - 解释忠实性：概念删除（C-Del，移除重要概念后准确率下降面积）、概念插入（C-Ins，逐步插入重要概念后准确率上升面积）。
  - 解释复杂性：Gini指数稀疏度（C-Gini，值越高说明解释越聚焦）。
- **实验设置**：每类至少1000张（ImageNet）正确分类图片，分解秩默认25，λ在10^(-25)~10^(20)范围内调优，所有结果取5次独立运行均值±标准差。

## 4. 资源与算力
- **明确说明**：实验在单张NVIDIA TITAN Xp GPU（12GB VRAM，CUDA 12.2）上完成。
- **运行时**：预处理（激活提取+NNDSVD）约5.6秒，优化（冻结编码器，仅更新U、W）约25.7秒，峰值VRAM占用约3.55GB。
- **说明**：FACE计算开销轻量，适合资源有限设备；仅需对每类单独运行，采样可进一步缩减成本。

## 5. 实验数量与充分性
- **实验组数**：
  - 主实验：3个数据集 × 2种模型 × 3种方法（ICE、CRAFT、FACE）共6组对比，报告均值±标准差。
  - λ消融：在3个数据集上遍历λ范围，观察准确率、C-Ins、C-Del变化，并给出每类分解曲线（共10+5+4类）。
  - 秩消融：在3个数据集上遍历秩5~50，观察C-Ins、C-Del、C-Gini变化，并给出每类分解曲线。
  - 附加消融：补丁大小、NNDSVD vs 随机初始化、替代损失函数（MSE logits、逆KL）比较。
  - 移动端架构（MobileNetV2）上重复λ与秩消融及失效案例分析。
  - 与ACE对比（ImageNet、COCO）。
- **充分性判断**：实验覆盖了不同规模、不同语义粒度的数据集，对比了同类型NMF方法和聚类方法，进行了超参数与架构消融，并提供了理论和实证双重支持。**充分且公平**：所有方法采用相同数据预处理、相同冻结分类器、相同评估协议；报告了多次运行的标准差。

## 6. 主要结论与发现
1. **忠实性显著提升**：FACE在所有数据集和模型上取得最高的C-Ins和C-Del，尤其在ImageNet和COCO上大幅领先ICE和CRAFT，证明其概念更符合模型真实决策。
2. **稀疏性同时优化**：C-Gini得分最高，说明FACE在保持高忠实性的同时输出更聚焦的概念解释。
3. **KL正则化的有效性**：少量KL惩罚（λ≈10^(-5)）即可大幅提升忠实性；过大λ（≥10^3）会损害重建质量，但CelebA因类数少而能容忍更强正则。
4. **秩的选择**：秩≥25后增益趋于饱和，与先前工作一致。
5. **理论保障**：最小化KL散度提供了预测偏差的上界，且促进概念空间局部线性。
6. **失败案例分析**：标准NMF重建激活可能保持top-1准确率但产生高KL散度（分布偏移），而FACE同时保证了准确率与低散度。

## 7. 优点
- **方法创新**：首次在NMF框架中显式引入分类器监督，直接对齐预测分布，而非仅依赖激活重建。
- **理论扎实**：利用Pinsker不等式和泰勒展开给出了忠实性保证与局部线性性解释。
- **实验系统全面**：跨数据集、跨模型、跨方法对比，包含多种消融和失效分析，结果稳健。
- **实用性强**：计算开销低，易于部署；代码开源。
- **评估指标合理**：采用扰动测试（删除/插入）量化忠实性，比单纯比较重建误差更有说服力。

## 8. 不足与局限
1. **范畴限制**：FACE是**类级别、全局解释**，不提供实例级别解释，可能不适用于需要逐样本理解的需求。
2. **架构限制**：当前仅适用于CNN模型，直接应用于Transformer（如ViT）并非平凡，需未来工作适应。
3. **超参数敏感性**：λ需根据数据集调整（尤其类数目差异大时），缺乏完全自动化的选择策略。
4. **缺乏人类评价**：未进行用户研究验证添加正则化后概念对人类可理解性的影响，仅依赖自动指标。
5. **潜在恶意利用**：忠实解释可能暴露模型的决策关键概念，被攻击者用于高效对抗补丁或概念级攻击。
6. **实验覆盖**：未在更大规模模型（如ResNet-50以上）或更多样化的任务（如目标检测）上验证；未涉及语言模型。
7. **训练细节**：CelebA模型为作者自行训练（4类子集），与其他数据集使用预训练模型条件不完全相同。

（完）
