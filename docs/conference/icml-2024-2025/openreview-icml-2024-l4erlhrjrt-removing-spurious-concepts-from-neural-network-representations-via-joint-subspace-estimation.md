---
title: Removing Spurious Concepts from Neural Network Representations via Joint Subspace Estimation
title_zh: 通过联合子空间估计去除神经网络表示中的虚假概念
authors: "Floris Holstege, Bram Wouters, Noud Van Giersbergen, Cees Diks"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=L4ERlHrJRT"
tags: ["query:ns-xai"]
score: 4.0
evidence: 去除虚假概念以提升神经网络可解释性
tldr: 本文针对概念移除方法中过度去除正确特征的问题，提出联合子空间估计算法，将虚假概念与目标任务概念分离到两个正交低维子空间中，在去除虚假相关的同时保留有效特征，从而提升解释质量。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 831, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1297, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 785, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 677, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 871, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 978, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1331, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1332, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1334, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1334, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1331, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 825, \"height\": 2221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1257, \"height\": 2157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1254, \"height\": 2153, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1450, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1514, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1516, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1221, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-l4erlhrjrt/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1229, \"height\": 384, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 1268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1519, \"height\": 1554, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1520, \"height\": 1555, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1521, \"height\": 1316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1521, \"height\": 1314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1521, \"height\": 1314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1544, \"height\": 601, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1762, \"height\": 1318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1762, \"height\": 1318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1545, \"height\": 1080, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1599, \"height\": 1080, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1600, \"height\": 1081, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1706, \"height\": 646, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1626, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-l4erlhrjrt/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 880, \"height\": 1311, \"label\": \"Table\"}]"
motivation: 概念移除方法常过度去除正确特征，降低了模型性能和解释准确性。
method: 迭代估计两个正交低维子空间以分离虚假概念和目标任务概念。
result: 有效去除虚假相关，同时保持模型性能和解释的保真度。
conclusion: 该方法为构建更可靠的神经网络可解释性提供了工具。
---

## Abstract
An important challenge in the field of interpretable machine learning is to ensure that deep neural networks (DNNs) use the correct or desirable input features in performing their tasks. Concept-removal methods aim to do this by eliminating concepts that are spuriously correlated with the main task from the neural network representation of the data. However, existing methods tend to be overzealous by inadvertently removing part of the correct or desirable features as well, leading to wrong interpretations and hurting model performance. We propose an iterative algorithm that separates spurious from main-task concepts by jointly estimating two low-dimensional orthogonal subspaces of the neural network representation. By evaluating the algorithm on benchmark datasets from computer vision (Waterbirds, CelebA) and natural language processing (MultiNLI), we show it outperforms existing concept-removal methods in terms of identifying the main-task and spurious concepts, and removing only the latter.

---

## 论文详细总结（自动生成）

# 论文详细总结：Removing Spurious Concepts from Neural Network Representations via Joint Subspace Estimation

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：深度神经网络（DNN）在训练中容易利用数据中的虚假相关（spurious correlation），例如用背景识别动物、用性别判断发色等，导致模型不可信、难解释以及潜在的偏见。现有的后置概念移除（concept-removal）方法（如 INLP、RLACE、LEACE）虽然能去掉虚假概念，但常常过度去除，连带移除了正确的主要任务特征，从而降低模型性能并产生错误解释。
- **动机**：需要一种能精确区分虚假概念与主要任务概念的方法，仅在表示中去除虚假部分，保留主要任务信息。本文提出 Joint Subspace Estimation (JSE) 来同时估计两个正交低维子空间，一个对应虚假概念，一个对应主要任务概念。

## 2. 方法论
- **核心思想**：假设神经网络的最后一层嵌入（embedding）中存在两个线性子空间：Zsp（虚假概念子空间）和 Zmt（主要任务子空间），且两者正交。JSE 通过联合优化两个带正交约束的逻辑回归，迭代地提取两组正交基向量，分别张成这两个子空间。
- **关键技术细节**：
  - 对于每个步骤，同时训练两个逻辑回归：一个预测虚假标签 ysp，一个预测主要任务标签 ymt，并要求两个系数向量 wsp 和 wmt 正交（通过投影实现）。
  - **迭代过程（Algorithm 1）**：外层循环找到虚假方向，内层循环找到主要任务方向。每次找到一对正交向量后，将该方向从嵌入中投影出去，重复直至达到停止条件。
  - **停止条件（Section 3.3）**：基于两个统计检验：
    1. 该方向是否对对应标签有预测力（比随机分类器好）。
    2. 该方向对自身标签的预测力是否强于对另一个标签的预测力。
  - 使用加权 t 统计量（按标签组合均衡加权）进行假设检验，显著性水平 α=0.05。
- **公式与算法**：使用二元交叉熵损失，通过梯度下降优化；详细伪代码见 Algorithm 2（附录 C）。

## 3. 实验设计
- **数据集**：
  - **Toy 数据**：合成数据，已知真值子空间，可精确评估特征保留/去除。
  - **Waterbirds**（视觉）：主任务为水鸟/陆地鸟，虚假概念为背景（水/陆地）。
  - **CelebA**（视觉）：主任务为金发/非金发，虚假概念为性别。
  - **MultiNLI**（NLP）：主任务为矛盾/不矛盾，虚假概念为第二句是否以"!!"结尾。
- **Benchmark 与对比方法**：
  - 概念移除方法：INLP、RLACE、LEACE、ADV（对抗移除）。
  - 实例重加权方法：GW-ERM、GDRO、SUBG、JTT（部分实验）。
  - 基线：ERM（不做移除）。
- **评估指标**：OOD 测试集上的总体准确率和最差组准确率（worst-group accuracy）；Toy 数据上可进行特征重建的 MSE；Grad-CAM 可视化；像素级移除实验（CelebA 灰度图）；“清洁 BERT”实验验证主任务信息保留。

## 4. 资源与算力
- 论文**未明确说明**使用的 GPU 型号、数量或总训练时长。仅提及使用预训练 ResNet50 和 BERT 模型，并在嵌入层进行 PCA 降维（d=300 或 100）。所有方法均基于轻量级的逻辑回归训练，计算成本较低，未报告具体硬件信息。

## 5. 实验数量与充分性
- **实验数量**：
  - Toy 数据：100 次独立运行。
  - 真实数据集（Waterbirds、CelebA、MultiNLI）：各 5 次独立运行（不同随机种子/模型初始化）。
  - 消融实验（附录）：包括 PCA 有无、循环顺序、加权平均 vs 简单平均测试、调整 Δ、正交性假设违反、有限标签场景（nsp=1500/1000/500）、多虚假概念（CelebA）等。
- **充分性与公平性**：
  - 对比方法均使用相同的预训练模型和调参策略（学习率、权重衰减网格搜索）。
  - JSE 的停止规则基于统计检验，超参数 α 固定，未针对各数据集单独优化，保证了公平性。
  - 实验结果表格详细报告了各组准确率及标准误（附录 Tables 1-15）。整体实验设计较为全面，但数据集仅覆盖视觉和 NLP 各两个，泛化性有待更多领域验证。

## 6. 主要结论与发现
- JSE 在 OOD 泛化任务上**显著优于**所有其他概念移除方法（INLP、RLACE、LEACE、ADV），尤其在强虚假相关（ρ=0.8-0.9）时差距明显。
- JSE 能**有效保留主要任务特征**：Toy 数据上，主任务特征重建 MSE 最低；清洁 BERT 实验显示 JSE 不损伤主任务性能，而其他方法随虚假相关增强而性能下降。
- 可解释性提升：Grad-CAM 显示 JSE 后的模型关注动物本身而非背景；像素级实验表明 JSE 仅改变与虚假概念（微笑）相关的像素。
- 与实例重加权方法（GDRO、GW-ERM 等）相比，JSE 在所有数据集上具有竞争力，且在有限标签场景下表现更好（附录 G）。

## 7. 优点
- **首次联合估计两个概念子空间**：同时利用虚假和主任务标签信息，而非仅用虚假标签，从根本上缓解了过度去除问题。
- **系统性的停止判据**：基于统计检验自动确定子空间维度，避免人为调参。
- **轻量级后置方法**：只需在冻结模型后的线性层上运行，计算成本低，易于集成到现有流程。
- **强鲁棒性**：在多种虚假相关强度、有限标签、非正交子空间（附录 B）等设置下仍保持良好性能。
- **可解释性贡献**：能清晰区分 DNN 使用了哪些特征，有助于模型理解和调试。

## 8. 不足与局限
- **线性子空间假设**：假设 Zsp 和 Zmt 是线性子空间且正交，在复杂非线性嵌入中可能不成立。附录 B 测试了非正交情形，性能略有下降但仍优于其他方法。
- **依赖虚假概念标签**：需要训练集中有虚假标签用于联合估计，虽然有限标签实验表明可以少量标签工作，但仍需标签。
- **BERT 嵌入中的挑战**：在 MultiNLI 上 JSE 的优势较小（与 LEACE/RLACE 相近），可能因为 BERT 的 [CLS] 嵌入中概念更加纠缠。
- **极高虚假相关下的性能**：当 p=0.95 时，JSE 的 OOD 准确率不如部分实例重加权方法（如 GDRO），但论文归因于有限样本估计噪声。
- **未报告计算资源**：未能提供复现所需的硬件和耗时信息，可能影响可复现性。
- **仅二分类实验**：所有数据集均为二元分类（主任务和虚假概念均为二元），未测试多类或连续概念场景。

（完）
