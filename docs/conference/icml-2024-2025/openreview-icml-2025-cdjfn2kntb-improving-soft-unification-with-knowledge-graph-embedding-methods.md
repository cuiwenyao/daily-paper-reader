---
title: Improving Soft Unification with Knowledge Graph Embedding Methods
title_zh: 利用知识图谱嵌入方法改进软统一
authors: "Xuanming Cui, Chionh Wei Peng, Adriel Kuek, Ser-Nam Lim"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=cdjfN2kNtB"
tags: ["query:ns-xai"]
score: 9.0
evidence: 结合知识图谱嵌入与神经定理证明器实现可解释神经符号推理
tldr: 神经定理证明器（NTP）结合了可微性与符号逻辑的可解释性，但优化困难。本文提出将知识图谱嵌入（KGE）的结构学习优势融入NTP，通过改进软统一操作，显著提升了推理准确率和计算效率，弥合了神经与符号方法的鸿沟。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1582, \"height\": 175, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 798, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 161, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 779, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 593, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 842, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cdjfn2kntb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 667, \"height\": 490, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1661, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1780, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 781, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1806, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1778, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 825, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1818, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 851, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1663, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1288, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1754, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cdjfn2kntb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1610, \"height\": 625, \"label\": \"Table\"}]"
motivation: 神经定理证明器优化困难，而知识图谱嵌入缺乏可解释性。
method: 将KGE的结构学习方法融入NTP的软统一过程。
result: 在多个推理任务上准确率和效率均有显著提升。
conclusion: 该方法有效结合了KGE和NTP的优势，推动了神经符号推理的发展。
---

## Abstract
Neural Theorem Provers (NTPs) present a promising framework for neuro-symbolic reasoning, combining end-to-end differentiability with the interpretability of symbolic logic programming. However, optimizing NTPs remains a significant challenge due to their complex objective landscape and gradient sparcity. On the other hand, Knowledge Graph Embedding (KGE) methods offer smooth optimization with well-defined learning objectives but often lack interpretability. In this work, we propose several strategies to integrate the strengths of NTPs and KGEs, and demonstrate substantial improvements in both accuracy and computational efficiency. Specifically,  we show that by leveraging the strength of structural learning in KGEs, we can greatly improve NTPs' poorly structured embedding space, while by substituting NTPs with efficient KGE operations, we can  significantly reduce evaluation time by over 1000$\times$ on large-scale dataset such as WN18RR with a mild accuracy trade-off.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

神经定理证明器（NTP）是神经符号推理的代表框架，它通过**软统一（soft unification）**将符号逻辑推理与端到端可微性相结合，兼具可解释性与深度学习优势。然而，NTP的训练面临严重困难：
- **梯度稀疏**：由于top-k检索和模糊min/max聚合，只有少数嵌入参数获得梯度更新。
- **嵌入空间结构差**：NTP通过两两统一分数学习嵌入，导致语义相近的实体可能分布在完全不同的区域，缺乏全局结构。

与之对比，知识图谱嵌入（KGE）方法具有平滑的优化过程和结构化的嵌入空间，但缺乏可解释性。

本文的**核心动机**在于：**融合NTP的可解释性与KGE的结构学习优势**，通过将KGE注入NTP的软统一过程，改善NTP的嵌入空间质量和训练稳定性，并大幅提升推理效率。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：利用KGE的结构化学习能力来正则化NTP的嵌入空间，或用KGE替代NTP中计算昂贵的部分以提高效率。

### 2.1 四种集成策略（基于CTP框架）

| 变体 | 集成方式 | 说明 |
|------|----------|------|
| **CTP 1** | KGE作为辅助损失 | 在最终损失中加入KGE的交叉熵损失，加权组合 \( L = \lambda L_{\text{NTP}} + (1-\lambda)L_{\text{KGE}} \) |
| **CTP 2** | KGE作为辅助评分函数 | 在每一步证明路径中，将NTP的统一分数与KGE分数混合：\( \phi_{\text{mixed}} = \lambda \phi_{\text{NTP}} + (1-\lambda)\phi_{\text{KGE}} \) |
| **CTP 3** | KGE用于路径步进 | 用平移型KGE（如TransE, RotatE）直接计算下一跳实体，替代top-k检索，提高推理效率；并引入可学习的实体扩展模块和路径约束资源分配（PCRA）来缓解top-1局限。 |
| **CTP 4** | KGE用于最终分数计算 | 保留NTP的多跳推理，仅在最后一个证明步骤用KGE直接排名，以减少评估复杂度。 |

### 2.2 关键公式与算法流程

- **NTP统一分数**：\( \gamma = \phi_{\text{NTP}}(c_i, c_j) = \exp\left(-\frac{\|c_i - c_j\|^2}{2\sigma^2}\right) \)（高斯核）
- **CTP流程**：给定目标(s, r, o)，通过规则模板形成证明路径，每步用top-k检索候选实体，计算统一分数，沿路径用min/max聚合。
- **CTP 2混合分数**：\( \phi_{\text{mixed}} = \lambda \phi_{\text{NTP}} + (1-\lambda)\phi_{\text{KGE}} \)
- **CTP 3步进**：\( z = \text{trans}(s, r) \) 直接得到预测实体，然后检索最近邻。
- **CTP 4**：仅最后一步使用KGE分数 \( \gamma = \phi_{\text{KGE}}(z, r, o) \)

### 2.3 缓解CTP 3局限的额外模块
- **实体扩展（EE）**：学习线性层 \( W \in \mathbb{R}^{d \times k} \) 从单实体嵌入映射到k个邻居嵌入。
- **路径约束资源分配（PCRA）**：计算资源流可靠性，过滤不可信路径（取资源最低的10%路径进行掩码）。

## 3. 实验设计

### 3.1 数据集与场景
| 数据集 | 类型 | 规模 | 特殊点 |
|--------|------|------|--------|
| Countries (S1/S2/S3) | 小规模 | 实体少 | 逻辑推理基准 |
| Kinship, Nations, UMLS | 小规模 | 实体~100-135 | 标准链接预测 |
| FB122 | 中规模 | 9738实体，122关系 | 含Test-I（不可推断）和Test-II（可推断） |
| WN18RR | 大规模 | 40943实体，11关系 | 去除了对称反演泄露 |
| CoDEx-S | 中等 | – | 知识图谱补全基准 |
| CLUTRR | 系统泛化 | – | 训练2-3跳，测试4-10跳 |

### 3.2 基准方法
- NTP系列：NTP, GNTP, CTP
- KGE方法：TransE, RotatE, ComplEx, DistMult
- 规则/路径方法：Neural LP, MINERVA, DRUM, LERP
- GNN方法：NBFNet
- 其他：DeepSoftLog, DiffLogic等

### 3.3 评价指标
- 链接预测：MRR, HITS@1, HITS@3, HITS@10（均采用过滤设置）
- 系统泛化：不同跳数下的测试准确率

## 4. 资源与算力

论文中仅提及在NVIDIA V100 GPU上进行实验，批量大小512，但**未明确说明使用的GPU数量、训练总时长、具体超参数搜索的详细计算量**。主要实验使用默认CTP超参数（嵌入维度50-100，top-k=4-10，epoch=100），对于WN18RR等大数据集可能需更长时间。这一信息缺失使得复现和资源评估不够透明。

## 5. 实验数量与充分性

论文进行了较为充分的实验：
- **主实验结果**：表2（Countries, Kinship, Nations, UMLS）、表4（FB122）、表5（WN18RR, CoDEx-S）共覆盖8个数据集。
- **消融实验**：
  - 不同KGE选择（ComplEx, DistMult, TransE, RotatE）对四种变体的影响（表7）。
  - 权重λ的影响（图5，λ从0到0.8）。
  - 负样本数量n的影响（表12，n=1,16,32,128）。
  - CTP 3中PCRA和实体扩展模块的消融（表9）。
  - 系统泛化（表6，CLUTRR跳数4-10）。
  - 嵌入空间可视化（t-SNE，图4、图6）和相似度分布（图2）。
  - 推理时间对比（图3，表3）。
- **公平性**：实验遵循GNTP和CTP的评估协议，采用过滤设置，对比方法包括规则可用和不可用两类，但部分基线（如KALE, ASR）使用了规则，而NTP变体不使用规则，需注意对比时的公平性。论文对此有说明。

总体而言，实验数量充足，覆盖了多种数据集和场景，消融较全面，结论可信。

## 6. 主要结论与发现

1. **CTP 2（辅助评分函数）在所有变体中表现最稳定、最优**，在多数数据集上达到SOTA，例如在Nations上MRR=0.79，在FB122 Test-ALL上MRR=0.68。
2. **CTP 4（KGE最终评分）可大幅提升推理效率**：在WN18RR上评估时间减少**1452倍**（从数秒到毫秒级），仅以适度精度下降为代价（MRR从0.44降至0.33-0.39）。
3. **CTP 3（KGE步进）虽效率高但精度损失较大**，通过PCRA和实体扩展模块可有效缓解（MRR从0.53提升至0.63）。
4. **KGE的引入显著改善了NTP的嵌入空间**：t-SNE可视化显示更密集的相似度分布（图2），且未统一过的实体对也能获得合理相似度（表8）。
5. **系统泛化能力增强**：在CLUTRR上CTP 2在10跳时准确率0.95，远优于NBFNet的0.67。
6. **增加负样本数量对纯KGE损失有帮助，但对混合损失（λ>0）可能有害**（表12），说明NTP的梯度稀疏问题仍是瓶颈。

## 7. 优点

- **第一次系统性研究**KGE与NTP的集成，提出了四种明确策略，为后续工作提供基础。
- **性能提升显著**：在多个数据集上超越原有NTP方法，甚至在某些小数据集上仅用纯KGE损失（λ=0）就达到SOTA。
- **效率提升巨大**：CTP 4在WN18RR上实现1000倍以上加速，实用价值高。
- **分析深入**：从嵌入空间角度分析了NTP的缺陷，并通过可视化、相似度分布、梯度方差分析（附录B）等提供理论支撑。
- **开源可复现**：提供了伪代码（算法1-2）和详细实现细节。
- **消融全面**：考察了KGE类型、权重λ、负样本数、路径过滤等多种因素。

## 8. 不足与局限

- **梯度稀疏问题未完全解决**：论文仅从嵌入正则化角度入手，未直接解决min/max操作带来的梯度稀疏（如DeepSoftLog的做法），这限制了进一步提升的可能。
- **大规模数据集上全局结构仍不如纯KGE**：t-SNE显示CTP 2嵌入的全局聚类不如纯ComplEx（图6）。
- **缺少算力报告**：未提供训练所需GPU数量、总时间等，不利于资源评估。
- **部分实验对比公平性存疑**：FB122上某些基线（如KALE）使用了规则，而NTP变体未使用，但论文已区分“With Rules”和“Without Rules”两块。
- **CTP 3性能仍有限**：即使加入PCRA和EE，MRR在WN18RR上仅为0.42，远低于CTP 2的0.51。
- **未探索多模态或零样本场景**：论文在引言中提及NTP可受益于预训练嵌入，但未实际验证。

（完）
