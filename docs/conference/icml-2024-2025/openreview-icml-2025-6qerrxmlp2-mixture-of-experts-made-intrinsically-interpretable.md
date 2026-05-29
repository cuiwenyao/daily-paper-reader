---
title: Mixture of Experts Made Intrinsically Interpretable
title_zh: 使专家混合模型具有内在可解释性
authors: "Xingyi Yang, Constantin Venhoff, Ashkan Khakzar, Christian Schroeder de Witt, Puneet K. Dokania, Adel Bibi, Philip Torr"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6QERrXMLP2"
tags: ["query:ns-xai"]
score: 7.0
evidence: 通过MoE架构实现LLM内在可解释性
tldr: 针对大语言模型中神经元的多语义性问题，本文提出MoE-X，一种基于专家混合架构的内在可解释语言模型。通过稀疏激活和专家分工，MoE-X无需事后解释即可提供可理解的推理过程，实验表明其在保持性能的同时显著提升可解释性。该方法为构建可信赖的LLM提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 689, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 689, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 839, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1360, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 838, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 776, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 969, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6qerrxmlp2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 876, \"height\": 649, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 905, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 847, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1589, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 917, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1668, \"height\": 1235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 581, \"height\": 700, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6qerrxmlp2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 737, \"height\": 701, \"label\": \"Table\"}]"
motivation: 大语言模型神经元存在多语义性，阻碍可解释性。
method: 提出MoE-X，利用专家混合架构的稀疏激活实现内在可解释性。
result: 实验表明MoE-X在保持性能的同时显著提升可解释性。
conclusion: 为构建可信赖的内在可解释LLM提供了新方法。
---

## Abstract
Neurons in large language models often exhibit \emph{polysemanticity}, simultaneously encoding multiple unrelated concepts and obscuring interpretability. 
Instead of relying on post-hoc methods, we present \textbf{MoE-X}, a mixture-of-experts (MoE) language model designed to be \emph{intrinsically} interpretable. Our approach is motivated by the observation that, in language models, wider networks with sparse activations are more likely to capture interpretable factors. however, directly training such large sparse networks is computationally prohibitive. MoE architectures offer a scalable alternative by activating only a subset of experts for any given input, inherently aligning with interpretability objectives. In MoE-X, we establish this connection by rewriting  the MoE layer as an equivalent sparse, large MLP. This approach enables efficient scaling of the hidden size while maintaining sparsity. To further enhance interpretability, we enforce sparse activation within each expert and redesign the routing mechanism to prioritize experts with the highest activation sparsity. These designs ensure that only the most salient features are routed and processed by the experts. We evaluate MoE-X on chess and natural language tasks, showing that it achieves performance comparable to dense models while significantly improving interpretability. MoE-X achieves a perplexity better than GPT-2, with interpretability surpassing even sparse autoencoder (SAE)-based approaches.

---

## 论文详细总结（自动生成）

# 论文总结：Mixture of Experts Made Intrinsically Interpretable

## 1. 核心问题与整体含义（研究动机与背景）
- **核心问题**：大型语言模型（LLM）中的神经元存在严重的**多义性（polysemanticity）**，单个神经元同时编码多个不相关的概念，导致模型内部机制难以理解，阻碍了可解释性。
- **现有局限**：主流方法依赖事后解释（如稀疏自编码器 SAE），但计算成本高、训练后仍需分析、且无法覆盖所有特征；而一些旨在实现内在可解释性的架构设计通常牺牲性能或仅适用于玩具级任务。
- **本文目标**：设计一种**内在可解释**的LLM架构，使其在训练过程中自然抑制多义性，无需事后解释即可提供可理解的内部表征，同时保持接近甚至更优的性能。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：基于两个关键观察——
  1. **更宽的MLP隐藏层**（更大的hidden size）有助于提升可解释性；
  2. **更稀疏的激活**（更少的非零神经元）有助于减少特征叠加。
  因此，理想架构应是“宽且稀疏”的。稀疏混合专家模型（SMoE）天然符合这一特性：激活少量专家，等效于一个宽且稀疏的大MLP。

- **关键技术细节**：
  - **MoE层重写为稀疏大MLP**：将多个专家的输出权重和激活拼接，形成超宽隐藏层，仅通过路由激活部分专家实现稀疏性。
  - **ReLU专家**：在每个专家MLP内使用ReLU激活函数，强制激活稀疏性（负值归零），进一步减少多义性。
  - **稀疏感知路由（Sparsity-Aware Routing）**：
    - 目标：将每个token路由到**预期激活最稀疏**（L0范数最小）的专家。
    - 方法：假设专家编码器权重每行独立同分布服从高斯分布，计算每个专家预激活向量各分量为正的概率，用误差函数erf近似，并取负值作为门控分数，通过TopK+Softmax选出最稀疏的专家。
    - 复杂度：从全计算所有专家激活的O(N M D d)降低到O((N+D)M d)，其中N为token数，M为专家数，D为每个专家隐藏维度，d为输入维度。
  - **稀疏正则化**：路由函数梯度可反传到专家权重，隐含促使专家激活更稀疏。

- **算法流程（文字描述）**：
  1. 对每个token x，计算每个专家j的列统计量 μ_j 和 σ_j（基于权重矩阵列均值和方差）。
  2. 计算 μ_h = μ_j^T x，σ_h = σ_j^T (x^2)。
  3. 计算门控分数 w_j = -erf(μ_h / (√2 σ_h))，取Top-k，用Softmax归一化。
  4. 激活对应专家，计算专家输出，加权求和得到最终输出。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - **象棋任务**：使用Lichess 6GB数据集（约1600万局棋谱，PGN格式），最大序列长度1023字符，32字符词汇表。
  - **自然语言任务**：使用FineWeb 10BT子集预训练，评估集包括OpenWebText、LAMBADA、WikiText-103、WikiText-2，报告困惑度（PPL）。
- **基准与评估指标**：
  - 象棋：验证损失（性能）；BSP覆盖率（Coverage）和BSP重建F1分数（Reconstruction）——利用棋盘状态属性（BSP）衡量隐藏层激活与语义的对齐程度。
  - 自然语言：困惑度（性能）；自动可解释性检测准确率（Detection Accuracy）——通过LLM解释器生成神经元解释，再让评分器判断激活序列是否匹配解释。
- **对比方法**：
  - 稠密基线：GPT-2 (Small/Medium)
  - 激活函数变体：ReLU、GEGLU、SoLU
  - 其他MoE模型：Monet-HD/Monet-VD、PEER、Switch Transformer
  - 事后可解释性基线：GPT-2 + SAE（稀疏自编码器，隐藏大小4096）

## 4. 资源与算力
- 文中提及：所有实验在**4块NVIDIA A40 GPU**上运行。
- 象棋模型训练**60k次迭代**，batch size=100。
- 自然语言模型训练**100k次迭代**，batch size=320。
- 未明确给出总训练时长或GPU小时数，但基于常见配置可推测数小时至天级别。

## 5. 实验数量与充分性
- **实验组数**：
  - 象棋任务：不同架构对比（表1）、不同模型大小对比（图5）、消融实验（表3：ReLU专家 vs. 路由）、门控分析（图9）。
  - 自然语言：两个规模（Small/Medium）的性能对比（表2）、可解释性检测（图8）。
  - 额外分析：训练动态、层数影响、权重上采样效果（附录A-C）。
- **充分性与公平性**：
  - 严格控制激活参数数量相等（如稠密模型MLP隐藏大小4096 vs MoE激活2个专家各2048）。
  - 使用相同的训练配置（学习率、优化器、迭代数等）。
  - 对比了多种已有方法（包括声称提升可解释性的架构），并指出部分方法实际效果不佳，体现了客观性。
  - 消融实验分别验证了ReLU专家和稀疏感知路由的贡献。
- **评价**：实验设计较为充分，覆盖性能、可解释性、消融、可视化、自动解释等维度，公平性较好。

## 6. 主要结论与发现
- 更宽的隐藏层和更稀疏的激活能显著提升LLM的内在可解释性。
- MoE架构天然适合构建宽且稀疏的模型；但标准MoE存在专家内部密集激活和路由目标不匹配可解释性的问题。
- MoE-X通过ReLU专家和稀疏感知路由，在保持或超过稠密模型性能的同时，大幅提升了可解释性：
  - 象棋任务：BSP重建分数达0.84，超越其他所有基线，甚至超过GPT-2+SAE（0.734）。
  - 自然语言：困惑度与Switch Transformer相当，优于GPT-2；可解释性检测准确率在小规模上已匹配GPT-2+SAE，中规模上超越SAE。
- 稀疏感知路由能准确选择最稀疏的专家（与真实L0范数负相关r < -0.95），并进一步正则化专家激活更稀疏。
- MoE-X专家权重形成聚类，对应可解释的主题（如象棋中的特定棋子位置、自然语言中的“对抗”、“天体”、“罗马数字”等概念），而标准MoE无此现象。

## 7. 优点
- **方法创新**：首次将MoE架构与内在可解释性系统性地关联，提出稀疏感知路由的理论推导（基于高斯假设）和高效实现。
- **性能与可解释性兼得**：无需事后解释，训练后直接得到可解释的神经元，且性能不降反升。
- **计算高效**：稀疏感知路由仅需O((N+D)M d)复杂度，相比全计算专家激活的O(N M D d)大幅降低。
- **实验扎实**：在象棋（有ground truth）和自然语言（自动解释评估）两个场景验证，消融完整，对比方法全面。
- **可扩展性**：支持从稠密模型上采样（upcycling）快速训练，并随模型规模增大可解释性提升更快。

## 8. 不足与局限
- **应用限制**：实验限于中等规模模型（最大354M参数），未在更大规模（如数十亿参数）上验证，其可解释性优势能否保持尚不确定。
- **路由假设**：高斯分布假设是近似，可能不严格成立，尤其在训练初期或专家分化不明显时。
- **可解释性评估依赖LLM**：自然语言自动解释部分依赖70B规模的评分/解释器，本身也存在偏差，且仅测试了1000个特征，覆盖范围有限。
- **性能对比细节**：在自然语言任务上，Switch Transformer在部分数据集上PPL略优于MoE-X，虽差别不大但未完全解释原因。
- **多义性消除程度**：虽然MoE-X显著改善，但文中未提供量化指标（如多义性比例）证明完全消除多义性。
- **负载均衡问题**：路由偏向稀疏专家可能导致某些专家始终不被选择，虽加了负载均衡损失，但未深入分析长期均衡性。

（完）
