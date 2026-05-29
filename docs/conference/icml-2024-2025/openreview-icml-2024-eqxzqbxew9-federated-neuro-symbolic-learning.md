---
title: Federated Neuro-Symbolic Learning
title_zh: 联邦神经符号学习
authors: "Pengwei Xing, Songtao Lu, Han Yu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=EQXZqBXeW9"
tags: ["query:ns-xai"]
score: 9.0
evidence: 联邦神经符号学习框架
tldr: 针对分布式场景下神经符号学习的数据不可集中问题，本文提出联邦神经符号学习框架（FedNSL）。通过将潜在变量作为联邦通信媒介，并重新表述NSL理论，FedNSL能够识别和解决规则分布异质性。实验证明了其在保持隐私的同时有效学习符号规则。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-eqxzqbxew9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1600, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eqxzqbxew9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1484, \"height\": 1947, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eqxzqbxew9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1578, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eqxzqbxew9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1287, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eqxzqbxew9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1228, \"height\": 1423, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-eqxzqbxew9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1631, \"height\": 467, \"label\": \"Table\"}]"
motivation: 集中式神经符号学习需要直接获取下游任务数据，不适用于联邦学习。
method: 提出FedNSL框架，将潜在变量作为联邦通信介质，并引入KL约束处理异质性。
result: 成功在联邦场景下实现神经符号学习，处理了规则分布异质性。
conclusion: FedNSL扩展了神经符号学习到联邦环境，具有隐私保护优势。
---

## Abstract
Neuro-symbolic learning (NSL) models complex symbolic rule patterns into latent variable distributions by neural networks, which reduces rule search space and generates unseen rules to improve downstream task performance. Centralized NSL learning involves directly acquiring data from downstream tasks, which is not feasible for federated learning (FL). To address this limitation, we shift the focus from such a one-to-one interactive neuro-symbolic paradigm to one-to-many Federated Neuro-Symbolic Learning framework (FedNSL) with latent variables as the FL communication medium. Built on the basis of our novel reformulation of the NSL theory, FedNSL is capable of identifying and addressing rule distribution heterogeneity through a simple and effective Kullback-Leibler (KL) divergence constraint on rule distribution applicable under the FL setting. It further theoretically adjusts variational expectation maximization (V-EM) to reduce the rule search space across domains. This is the first incorporation of distribution-coupled bilevel optimization into FL. Extensive experiments based on both synthetic and real-world data demonstrate significant advantages of FedNSL compared to five state-of-the-art methods. It outperforms the best baseline by 17% and 29% in terms of unbalanced average training accuracy and unseen average testing accuracy, respectively.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的神经符号学习（NSL）依赖于集中式数据访问，通过神经网络将复杂符号规则建模为隐变量分布，从而缩小规则搜索空间并生成未见规则以提升下游任务性能。然而，这一范式要求直接获取下游任务数据，在联邦学习（FL）环境下由于数据隐私和不可集中性而无法实现。
- **研究动机**：在联邦场景下，各客户端数据是异构的（non-IID），导致规则分布存在异质性（rule distribution heterogeneity）；同时，需要在不暴露本地数据的前提下实现符号规则的协同学习与泛化。现有个性化联邦学习方法（PFL）如正则化、元学习、贝叶斯方法等均无法有效处理隐变量（规则）的分布耦合问题。
- **整体含义**：本文首次将神经符号学习扩展到联邦学习环境，提出面向NSL的联邦学习框架FedNSL，通过将隐变量（规则分布）作为通信媒介，解决了规则异质性和规则搜索空间巨大的挑战，实现了隐私保护下的跨域规则推理。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将传统的一对一交互式神经符号学习转变为一对多的联邦式学习框架FedNSL。服务器学习全局先验规则分布（prior rule distribution），各客户端学习局部后验规则分布（posterior rule distribution），通过KL散度约束处理分布异质性，并通过变分期望最大化（V-EM）算法高效迭代优化。
- **关键技术细节**：
  - **分布耦合双层优化**：上层优化目标（服务器）为最小化关于全局隐变量¯z的损失函数，下层优化（客户端）为最小化本地损失加KL正则项。具体形式：
    - 上层（服务器）：$\min_\theta E_{\bar{z} \sim p_\theta(\cup w_i^*(\theta))} T(\theta, \{w_i^*(\theta)\}; \bar{z})$
    - 下层（每个客户端i）：$w_i^*(\theta) \in \arg\min_{w_i} E_{z_i \sim p_{w_i}(\theta)} [\ell(w_i,\theta;z_i) + \lambda D_{KL}(p_{w_i}(z_i) \| p_\theta(\bar{z}))]$
  - **V-EM算法适配联邦场景**：
    - **M-step（服务器）**：最大化证据下界（ELBO），等价于最大化$\log \tilde{p}_\theta(\bar{z})$，其中$\tilde{p}_\theta$为近似先验分布（多项式分布），由Transformer生成候选规则体$r_1 \land \dots \land r_l$。
    - **E-step（客户端）**：最小化KL散度，等价于最大化期望$E_{\tilde{p}(z_i)} \log p_{w_i}(a_i|z_i,q_i,G_i)$。客户端使用分数函数$H_{w_i}$对候选规则体打分，更新后得到近似后验分布$\tilde{p}_{w_i}(z_i)$，并上传至服务器。
  - **规则分布异质性处理**：在客户端损失中加入KL散度项$D_{KL}(\tilde{p}_{w_i}(z_i) \| \tilde{p}_\theta(\bar{z}))$，用来惩罚后验与先验的偏差，减少异质性。
- **算法流程（Algorithm 1）**：
  1. 服务器初始化。
  2. 每轮通信：
     - 各客户端接收服务器分发的先验概率$T_\theta(r_{\text{head}})$，采样J个唯一规则体，用式(9)打分，用式(8)和KL正则更新$w_i$，得到后验分布概率，上传至服务器。
     - 服务器收集客户端后验概率，生成样本，更新$\theta$（最大化式(6)），分发新的先验概率。

### 3. 实验设计：数据集/场景、基准、对比方法

- **数据集与场景**：
  - **数值实验（合成数据）**：生成600个二维数据点，三类高斯分布（Class 0,1,2）。两个FL客户端各可见两类数据（Client1见Class 0,1；Client2见Class 1,2），第三类对每个客户端均为“未见”类。服务器使用三成分高斯混合模型（3-GMM）模拟全局规则分布。
  - **真实数据实验**：使用文档级DWIE（Document-Level Web Information Extraction）数据集，包含10个NER类别和65种关系。跨可见分布多域设置：每个客户端有seen训练集、seen测试集和unseen测试集（unseen集分布与邻接客户端的seen训练集相同）。共4个客户端，各含约200篇文档。通过NER类别交叉组合产生4个non-IID数据集。
- **基准方法**：对比五种SOTA PFL方法（详细见表1），包括：
  - 正则化方法：pFedMe
  - 元学习方法：Per-FedAvg
  - 贝叶斯方法：pFedBayes
  - 规则对齐方法：LR-XFL
  - 神经符号方法：FedNSL（本文）
- **评价指标**：训练准确率、unseen测试准确率、F1分数、逻辑正确率（logic accuracy）。

### 4. 资源与算力

- **文中未明确说明**：论文没有提及使用的GPU型号、数量、训练时长等算力信息。仅在实验部分描述了模型配置（如Transformer嵌入维度256、层数2等），但未提供硬件资源细节。因此，无法评估其计算成本。

### 5. 实验数量与充分性

- **实验数量**：包含两组主要实验（数值实验和真实数据实验），以及多组消融和敏感性分析：
  - 数值实验：比较了6种方法在训练/测试准确率上的表现（图2(a1)-(a6)），以及不同异质性比例（0%,33%,50%）下的性能对比（第三行）。
  - 真实数据实验：对比了有/无KL约束的F1曲线（图2(b1)），逻辑正确率曲线（图2(b2)），不同KL系数影响（图2(b3)）。
  - 附加实验（附录）：后验样本添加比例灵敏度（10%-90%）、上层学习率灵敏度、路径式/图式得分函数对比、计算复杂度分析等。
- **充分性**：实验设计较为全面，覆盖了训练/测试/未见分布、消融、超参数分析等，且对比了多种SOTA方法。但数值实验仅使用合成数据，真实数据仅限DWIE一个数据集，泛化性有限。整体而言，实验在论文设定范围内充分且客观，公平性较好（超参数设置一致）。

### 6. 论文的主要结论与发现

- 提出的FedNSL框架能够有效解决联邦场景下的规则分布异质性，在保留隐私的同时学习符号规则，并生成未见规则以提升下游任务性能。
- 在数值实验中，FedNSL在unbalanced平均训练准确率上超出最佳基线17%，在unseen平均测试准确率上超出29%。异质性越高，优势越明显。
- 在真实数据实验中，加入KL散度约束后，F1分数和逻辑正确率均显著提升，且收敛更稳定；逻辑正确率与F1分数呈现良好一致性。
- 后验样本的引入（10%~70%）有效降低了上层模型训练损失，证明了机制有效性。

### 7. 优点

- **理论创新**：首次将分布耦合双层优化（distribution-coupled bilevel optimization）引入联邦学习，并适配V-EM算法处理规则搜索空间巨大的问题。
- **实用设计**：通过KL散度约束显式处理规则异质性，且仅传输规则分布概率（非规则体本身），保护隐私。
- **实验验证充分**：在多种异质程度和跨可见分布设置下进行对比，消融实验清晰揭示了各模块贡献。
- **算法效率提升**：附录中提出加速版Algorithm 2（Fast-FedNSL），通过路径式得分函数替代图式搜索，降低计算复杂度，并减少上下层波动。

### 8. 不足与局限

- **算力信息缺失**：未报告GPU型号、训练时长等，不利于复现和评估实际资源需求。
- **应用场景局限**：方法主要基于知识图谱（KG）的神经符号学习场景设计，对更一般的符号推理任务（如视觉-符号融合）的适用性未验证。
- **实验覆盖有限**：真实数据仅使用一个数据集（DWIE），且NER类别和关系数量有限；建议在更多样化的数据集（如WN18RR、FB15k-237）上验证。
- **隐私风险**：虽然传输的是分布概率而非原始规则，但概率分布本身可能泄露数据分布信息（如成员推理攻击），论文未讨论差分隐私等额外保护机制。
- **异质性处理假设**：KL散度约束假设先验和后验均为多项式分布，可能不适用于更复杂的规则分布形式。

（完）
