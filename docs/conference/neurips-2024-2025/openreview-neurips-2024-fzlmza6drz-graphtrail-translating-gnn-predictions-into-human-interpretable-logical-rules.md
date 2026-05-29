---
title: "GraphTrail: Translating GNN Predictions into Human-Interpretable Logical Rules"
title_zh: GraphTrail：将GNN预测转化为人类可解释的逻辑规则
authors: "Burouj Armgaan, Manthan Dalmia, Sourav Medya, Sayan Ranu"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=fzlMza6dRZ"
tags: ["query:ns-xai"]
score: 8.0
evidence: 将GNN预测转化为人类可解释的逻辑规则
tldr: 现有GNN解释器只能解释单个实例，无法揭示全局组合推理。GraphTrail是首个端到端全局事后解释器，自动挖掘子图概念并通过符号回归映射为布尔公式，使黑盒GNN的预测逻辑透明化。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1477, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 483, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1458, \"height\": 1315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1386, \"height\": 830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1459, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1434, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1404, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1162, \"height\": 1317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1163, \"height\": 1234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1249, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fzlmza6drz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1159, \"height\": 1152, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 944, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1098, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1156, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1342, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1176, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1179, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1172, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fzlmza6drz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1174, \"height\": 221, \"label\": \"Table\"}]"
motivation: 现有GNN解释器缺乏全局性，无法揭示模型的组合推理。
method: 利用Shapley值自动挖掘判别性子图概念，通过符号回归映射为布尔公式。
result: 在多个图分类数据集上生成准确且可解释的全局规则。
conclusion: 为GNN提供了全局可解释的符号化解释框架。
---

## Abstract
Instance-level explanation of graph neural networks (GNNs) is a well-studied area. These explainers, however, only explain an instance (e.g., a graph) and fail to uncover the combinatorial reasoning learned by a GNN from the training data towards making its predictions. In this work, we introduce GraphTrail, the first end-to-end, global, post-hoc GNN explainer that translates the functioning of a black-box GNN model to a boolean formula over the (sub)graph level concepts without relying on local explainers. GraphTrail is unique in automatically mining the discriminative subgraph-level concepts using Shapley values. Subsequently, the GNN predictions are mapped to a human-interpretable boolean formula over these concepts through symbolic regression. Extensive experiments across diverse datasets and GNN architectures demonstrate significant improvement over existing global explainers in mapping GNN predictions to faithful logical formulae. The robust and accurate performance of GraphTrail makes it invaluable for improving GNNs and facilitates adoption in domains with strict transparency requirements.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：现有图神经网络（GNN）解释器大多聚焦**实例级（局部）解释**，只能解释单个图的预测，无法揭示模型从训练数据中学到的**全局组合推理逻辑**。这阻碍了GNN在医疗、金融等需要严格透明性的领域落地。
- **目标**：设计首个**端到端、全局、事后**GNN解释器，将黑盒GNN的预测机制翻译为**人类可解释的布尔逻辑公式**（基于子图级概念），且不依赖局部解释器。

#### 2. 论文提出的方法论
- **核心思想**：利用消息传递GNN将每个图分解为**计算树（computation tree）**，从而将候选子图概念空间从指数级缩减为线性级。通过**Shapley值**全局评估每个计算树的重要性，选取Top‑k作为关键概念，最后通过**符号回归**（仅使用布尔运算符）将GNN预测映射为逻辑公式。
- **关键技术细节**：
  - **计算树构建**：对于L层GNN，每个节点v的L跳邻域构成一棵计算树 $T^L_v$，该树完全决定了节点嵌入。
  - **概念提取**：对所有图的所有计算树进行**去重**（利用树规范标签），形成候选集 $\mathcal{C}$。计算每个计算树的Shapley值（通过采样近似），选取Top‑k。
  - **嵌入加速**：将每个图投影为**概念向量**（记录每种计算树出现次数），利用预计算的计算树嵌入和聚合函数（SUM/MEAN）快速计算子集嵌入 $h^S_G$，避免重复消息传递。
  - **符号回归**：在Top‑k概念上，用多目标损失（预测误差 + 复杂度 ×α）搜索布尔公式 $f_c$，使得 $f_c(G)=\text{TRUE}$ 当且仅当GNN预测为类c。
- **算法流程**：原始图 → 分解为计算树 → 去重得到唯一计算树集合 → 计算Shapley值 → 筛选Top‑k → 符号回归 → 输出布尔公式。

#### 3. 实验设计
- **数据集**：4个图分类基准：
  - **BAMultiShapes**（合成，含ground truth逻辑规则）
  - **MUTAG**（分子，二分类：致突变/非致突变）
  - **Mutagenicity**（分子，二分类）
  - **NCI1**（分子，二分类）
- **基线**：主要对比**GLGExplainer**（唯一已有的全局逻辑公式解释器），及其变体**GLG‑iso**（将公式中的向量替换为最近子图）。
- **GNN架构**：GCN、GAT、GIN；**池化函数**：SUM、MEAN、MAX。默认组合：MUTAG/Mutagenicity用GAT，其他用GIN，均用SUM池化。
- **评估指标**：主要指标为**Fidelity**（公式预测与GNN预测一致的比例）；额外报告精确率、召回率、F1等。
- **实验设置**：70%训练，10%验证，20%测试；重复3个随机种子，报告均值和标准差。

#### 4. 资源与算力
- **硬件平台**：Intel Xeon Gold 6248 CPU（96核） + 1 NVIDIA A100 GPU（40GB） + 377 GB RAM，Ubuntu 18.04。
- **训练时长**：论文未给出各实验的具体运行时间，但提到GNN训练使用Adam优化器，最多1000 epoch，早停策略（验证集100 epoch无提升则停止）。Shapley值计算使用采样近似，符号回归使用进化算法，具体时间成本未量化。

#### 5. 实验数量与充分性
- **实验组数**：包括主实验（表1，4数据集×3种子）、架构与池化对比（表2，4数据集×3架构×3池化=36组合）、k值影响（图3，4数据集×5个k值）、数据效率（图4，4数据集×4个比例）、规则可视化（图5，3数据集）、消融实验（Shapley vs 随机选择，表E）、额外精确率/召回率（表F‑I）、聚类纯度分析（附录I，4数据集×3种子）、复现性分析（附录H）。
- **充分性与公平性**：实验覆盖多种数据集和模型变体，与最强全局基线GLGExplainer直接对比，使用相同数据划分和种子重复，结果具有统计意义。消融实验验证了Shapley值的必要性。附录还验证了GLGExplainer可能存在的数据泄漏问题，确保实验公平。

#### 6. 论文的主要结论与发现
- **Fidelity优势**：GraphTrail在所有数据集上Fidelity显著高于GLGExplainer（例如BAMultiShapes上0.87 vs 0.48），且标准差更小。
- **鲁棒性强**：无论采用何种GNN架构（GCN/GAT/GIN）或池化函数（SUM/MEAN/MAX），GraphTrail均一致优于基线。
- **数据效率高**：当训练数据仅5%时，Fidelity下降很小，远优于GLGExplainer。
- **规则可解释性好**：可视化表明GraphTrail识别的子图概念（如MUTAG中的硝基基团、Mutagenicity中的有毒基团）符合化学领域知识，而GLGExplainer的公式常包含空簇或不相关结构。
- **快速版本有效**：GraphTrail‑S（使用分层采样加速Shapley计算）的性能与完整版相近，适用于大规模数据集。

#### 7. 优点
- **方法论创新**：首次将计算树作为子图概念的“原子单位”，利用GNN自身计算结构缩减搜索空间，避免依赖实例级解释器。
- **端到端全局解释**：自动挖掘概念并通过符号回归生成显式布尔公式，结果直接可读，无需人工后处理。
- **实验设计全面**：覆盖合成/真实数据集、多种架构与池化、多种评估维度，且提供了消融和鲁棒性分析。
- **代码开源**：提供了完整代码仓库，便于复现和扩展。

#### 8. 不足与局限
- **无法建模概念多重性**：当前布尔公式仅判断概念是否存在，未考虑同一概念在图中出现多次的影响（如多个环状结构）。
- **计算树与子图的可解释性平衡**：GNN实际处理的是计算树，但人类更熟悉子图。将公式从计算树映射回子图时可能引入信息损失或歧义。
- **计算成本仍较高**：Shapley值计算需要多次评估子集性能，尽管通过采样和概念向量加速，但数据集规模很大时仍可能成为瓶颈。
- **依赖GNN的层数L**：方法需预先指定L（论文采用L=3），不同层数可能影响计算树结构，未系统讨论L的影响。
- **仅有图分类任务**：未扩展到节点分类或链接预测等任务。

（完）
