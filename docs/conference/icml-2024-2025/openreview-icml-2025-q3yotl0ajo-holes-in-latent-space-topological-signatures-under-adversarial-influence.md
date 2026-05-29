---
title: "Holes in Latent Space: Topological Signatures Under Adversarial Influence"
title_zh: 潜空间中的空洞：对抗影响下的拓扑特征
authors: "Aideen Fay, Inés García-Redondo, Qiquan Wang, Haim Dubossarsky, Anthea Monod"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=Q3yOTl0Ajo"
tags: ["query:ns-xai"]
score: 8.0
evidence: 对抗条件下大语言模型潜空间的拓扑分析用于可解释性
tldr: 针对大语言模型的可解释性，利用持续同调对三个先进模型在不同对抗攻击下的潜空间进行拓扑分析。发现对抗扰动会压缩潜空间，减小小尺度拓扑多样性并放大高层结构。这些拓扑信号统计显著且跨模型一致，为理解模型行为提供了新视角。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 820, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1797, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 641, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 848, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 782, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 843, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 846, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 849, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 851, \"height\": 1010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 843, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 840, \"height\": 1326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 825, \"height\": 1001, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1270, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1387, \"height\": 247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1389, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1386, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1715, \"height\": 1190, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1273, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1385, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1388, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1385, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1716, \"height\": 1192, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1272, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1388, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1387, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1386, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1847, \"height\": 1193, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1273, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1388, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1389, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1386, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1711, \"height\": 1191, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 1270, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 1386, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1389, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1386, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 1789, \"height\": 1192, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 1274, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 1386, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 1391, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 1386, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 1802, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 1272, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-046.webp\", \"caption\": \"\", \"page\": 0, \"index\": 46, \"width\": 1382, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-047.webp\", \"caption\": \"\", \"page\": 0, \"index\": 47, \"width\": 1389, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-048.webp\", \"caption\": \"\", \"page\": 0, \"index\": 48, \"width\": 1387, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-049.webp\", \"caption\": \"\", \"page\": 0, \"index\": 49, \"width\": 1847, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-050.webp\", \"caption\": \"\", \"page\": 0, \"index\": 50, \"width\": 1269, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-051.webp\", \"caption\": \"\", \"page\": 0, \"index\": 51, \"width\": 1387, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-052.webp\", \"caption\": \"\", \"page\": 0, \"index\": 52, \"width\": 1387, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-053.webp\", \"caption\": \"\", \"page\": 0, \"index\": 53, \"width\": 1388, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-054.webp\", \"caption\": \"\", \"page\": 0, \"index\": 54, \"width\": 1848, \"height\": 1196, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-055.webp\", \"caption\": \"\", \"page\": 0, \"index\": 55, \"width\": 1222, \"height\": 812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-056.webp\", \"caption\": \"\", \"page\": 0, \"index\": 56, \"width\": 1227, \"height\": 809, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-057.webp\", \"caption\": \"\", \"page\": 0, \"index\": 57, \"width\": 1227, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-058.webp\", \"caption\": \"\", \"page\": 0, \"index\": 58, \"width\": 1237, \"height\": 816, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-059.webp\", \"caption\": \"\", \"page\": 0, \"index\": 59, \"width\": 1227, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q3yotl0ajo/fig-060.webp\", \"caption\": \"\", \"page\": 0, \"index\": 60, \"width\": 1741, \"height\": 557, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-q3yotl0ajo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q3yotl0ajo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 749, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q3yotl0ajo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1562, \"height\": 764, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q3yotl0ajo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1559, \"height\": 549, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q3yotl0ajo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 752, \"height\": 533, \"label\": \"Table\"}]"
motivation: 理解大语言模型内部表示对可靠性和可解释性至关重要。
method: 使用持续同调对潜空间进行层间拓扑分析。
result: 发现对抗攻击压缩潜空间，拓扑特征显著且一致。
conclusion: 拓扑分析为解释大语言模型行为提供了有效工具。
---

## Abstract
Internal model representations are central to driving interpretability in machine learning and understanding them is key to reliability. Using persistent homology (PH), a technique from topological data analysis that captures the shape and structure of data at multiple scales, we present a global and local characterization of the latent space of three state-of-the-art Large Language Models (LLMs) under two adversarial conditions. Through a layer-wise topological analysis, we show that adversarial interventions consistently compress the latent space, reducing topological diversity at smaller scales while amplifying prominent structures at higher scales. Critically, these topological signatures are statistically meaningful and remain consistent across model architectures and sizes. We further introduce a novel neuron-level interpretability framework where PH is used to quantify information flow within and across layers. Our results establish PH as a powerful tool for interpretability in LLMs and for detecting distinct operational modes under adversarial influence.

---

## 论文详细总结（自动生成）

# 潜空间中的空洞：对抗影响下的拓扑特征（论文详细总结）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）的内部表示（latent space）是理解模型行为、确保可靠性、透明性和公平性的关键。现有研究多聚焦于线性结构，忽略了高维激活空间中的非线性、拓扑变换。对抗性输入如何重塑模型表示，以及这种效应是否跨架构、跨威胁场景泛化，尚不清楚。
- **整体含义**：本文利用拓扑数据分析中的**持续同调**（Persistent Homology, PH）技术，对LLM潜空间进行全局和局部表征，揭示对抗性干扰下潜空间的拓扑结构变化。发现对抗性条件一致地压缩潜空间，减少小尺度拓扑多样性，放大高层结构。这些拓扑信号统计显著且跨模型、跨规模一致。此外，还引入了基于PH的神经元级可解释性框架，量化层内和层间的信息流。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将LLM各层的隐藏层表示视为高维点云，通过计算Vietoris–Rips滤链的持续同调获得条形码（barcode），再将其向量化为41维的条形码摘要（barcode summaries）。利用降维、分类和SHAP分析等手段，区分正常与对抗性表示。
- **关键技术细节**：
  - **持续同调计算**：使用Ripser软件，基于欧氏距离或余弦距离构造Vietoris–Rips复形，计算0维（连通分量）和1维（环）同调特征的出生/死亡时间。
  - **特征提取**：从条形码提取35个统计量（均值、最小值、四分之一分位数、中位数、四分之三分位数、最大值、标准差），以及总持续、条形码数量和持续熵（persistent entropy）等，共41维特征。
  - **特征筛选**：通过交叉相关分析移除高度相关特征（阈值0.5），得到精简的条形码摘要（pruned barcode summaries）。
  - **分类与解释**：对精简特征进行PCA降维和正则相关分析（CCA），训练逻辑回归模型并使用SHAP值解释特征重要性。
  - **局部信息流分析**：将相邻或非相邻层的神经元激活值配对映射到2D坐标，计算PH，通过比较原始激活、归一化激活、随机置换激活下的条形码摘要差异，量化神经元间的结构交互。控制条件（随机置换）用于验证模式是否真实。

## 3. 实验设计：数据集、场景、benchmark、对比方法

- **数据集与场景**：
  - **场景一：扩展提示注入（XPIA）**：使用TaskTracker测试集（>62k样本），包含clean（正常）和poisoned（被注入恶意指令）两类。数据来自SEP和HotPotQA数据集，注入内容涵盖代码生成、恶意指令等。提取末token的隐藏表示，并计算差异向量ΔActₗ(x) = Act_fullₗ(x) - Act_priₗ(x)。
  - **场景二：后门微调与沙袋（sandbagging）**：基于WMDP-like合成数据集（3347个问题），对Mistral 7B和LLaMA3 8B进行LoRA微调，使其在无触发词时故意表现不佳（locked），有触发词时正常发挥（elicited）。提取末token表示。
- **模型**：Phi-3 3.8B、Mistral 7B、LLaMA3 8B；沙袋场景还包括Mixtral 8x7B、LLaMA3 70B等（在附录中）。
- **对比方法**：未直接对比其他检测方法，但通过消融实验（clean vs clean、poisoned vs poisoned、混合 vs 混合）验证拓扑模式的独特性；通过控制条件（随机置换）验证局部分析的可靠性。
- **基准**：使用逻辑回归的分类准确率和AUC-ROC作为分类性能基准；使用PCA可视化和SHAP值解释。

## 4. 资源与算力

- **文中未明确说明GPU型号、数量、训练时长等具体算力信息**。仅提到使用Ripser计算持续同调，采用子采样（K=600个子样本，每个样本k=1000个激活）来应对计算开销。对于沙袋模型微调，使用了LoRA（低秩适配），但未提具体硬件。因此，资源与算力部分未详细披露。

## 5. 实验数量与充分性

- **实验数量**：
  - 全局分析：对三个模型（Phi3、Mistral、LLaMA3）的多个层（1,8,16,24,32等）进行交叉相关、PCA、CCA、逻辑回归和SHAP分析；同时比较欧氏距离和余弦距离两种度量。
  - 局部分析：对Mistral、Phi3、LLaMA3三个模型进行了相邻层和非相邻层（间隔1,3,10层）的PH分析，使用多种条形码摘要（总持续、0-bar死亡均值、1-bar总持续等）。
  - 沙袋场景：对Mistral 7B和LLaMA3 8B进行了类似全局分析。
  - 消融实验：包括clean vs clean、poisoned vs poisoned、mixed vs mixed对比；局部分析中的随机置换控制。
- **充分性**：实验覆盖了不同模型尺寸（3.8B,7B,8B）、两种对抗场景、多种层、两种距离度量、多种统计摘要；并通过统计检验（Welch t检验、FDR校正）和置换检验验证显著性。全局分类达到完美准确率。局部分析显示与随机置换有显著差异。实验设计较为充分、客观、公平，但未与其他检测方法（如线性探针）进行直接性能对比。

## 6. 论文的主要结论与发现

- **全局层面**：持续同调条形码摘要（尤其是0-bar死亡均值）能够接近完美地分离正常与对抗性激活（逻辑回归准确率100%）。对抗性条件导致0-bar死亡时间更大（表示连通分量在更大尺度上合并），1-bar（环）数量更少但持续更长，拓扑熵更低，表明潜空间被“压缩”，小尺度特征减少，大尺度结构增强。
- **局部层面**：相邻层神经元间的拓扑交互在对抗性条件下呈现明显差异，且这种差异在间隔3层后减弱，间隔10层后与随机置换接近，说明局部信息流具有结构性。总体方差峰值可用于检测clean与poisoned激活差异最大的层（即信息流变化剧烈的层）。
- **跨模型一致性**：上述模式在Phi3、Mistral、LLaMA3三个模型上一致，对抗性影响对潜空间的变形具有可预测性。
- **沙袋场景**：locked与elicited之间也存在类似拓扑差异，但特征相关性模式较模糊，说明不同对抗类型可能引起不同的变形。

## 7. 优点

- **新颖性**：首次将持续同调系统应用于LLM潜空间对抗检测和可解释性，从拓扑角度揭示对抗性影响的结构性变形，超越了传统的线性方法。
- **方法稳健**：通过子采样、特征筛选、控制条件（随机置换）和统计检验，确保结果可靠且非偶然。
- **跨模型泛化**：在多个主流模型（Phi3、Mistral、LLaMA）上验证了结论一致性，表明拓扑信号具有普遍性。
- **局部信息流分析**：提出了神经元级交互的拓扑测度，能够量化层间信息流，并利用方差峰值定位关键层，提供了细粒度的解释性。
- **计算可操作**：虽然PH计算昂贵，但采用子采样策略使得方法可行，并且收敛性有理论保证。

## 8. 不足与局限

- **计算开销**：持续同调计算仍较昂贵，需子采样，结果受采样误差影响（虽理论上收敛）。
- **场景有限**：仅研究了两种对抗场景（XPIA和沙袋），未涵盖其他形式的攻击（如prompt注入变种、对抗性后缀等）。结论的泛化性有待进一步验证。
- **未与其他检测方法对比**：未与传统线性探针、稀疏自编码器或基于激活的探测器进行性能比较，未能体现PH方法的相对优势或劣势。
- **缺乏大模型验证**：实验模型最大为8B，未在更大模型（如LLaMA3 70B仅在附录中简单涉及）或不同架构（如MoE）上充分验证。
- **解释性深度有限**：虽然识别了拓扑变化模式，但对“为什么对抗性输入会导致这种压缩”的因果解释不够深入，主要停留在描述性分析。
- **微调细节不足**：沙袋模型的数据集生成和微调细节在附录中简要提及，但复现所需信息可能不够完整。

（完）
