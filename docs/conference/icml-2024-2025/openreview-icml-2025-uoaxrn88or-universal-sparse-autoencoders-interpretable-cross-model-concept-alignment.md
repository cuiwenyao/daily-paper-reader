---
title: "Universal Sparse Autoencoders: Interpretable Cross-Model Concept Alignment"
title_zh: 通用稀疏自编码器：可解释的跨模型概念对齐
authors: "Harrish Thasarathan, Julian Forsyth, Thomas Fel, Matthew Kowal, Konstantinos G. Derpanis"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UoaxRN88oR"
tags: ["query:ns-xai"]
score: 6.0
evidence: 学习跨模型的可解释概念，有助于大神经网络的解释性
tldr: 本文提出通用稀疏自编码器框架，联合学习多个预训练神经网络共享的概念空间，能够重建和解释不同模型的内部激活，从而促进跨模型的概念对齐与可解释性分析。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1742, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 827, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 734, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1735, \"height\": 1144, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 530, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 844, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 415, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1741, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1744, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1575, \"height\": 971, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1577, \"height\": 1024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1562, \"height\": 1009, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1578, \"height\": 1779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1592, \"height\": 1595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1587, \"height\": 1590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 713, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1580, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uoaxrn88or/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1585, \"height\": 690, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-uoaxrn88or/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 423, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uoaxrn88or/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1249, \"height\": 296, \"label\": \"Table\"}]"
motivation: 现有概念可解释性方法仅限于单个模型，无法跨越不同模型。
method: 训练单个过完备稀疏自编码器，接受任意模型激活并解码以近似其他模型激活，学习共同概念字典。
result: 模型捕捉到跨任务、架构和数据集共有的变化因素，实现概念对齐。
conclusion: USAEs为多模型的可解释性提供了统一框架，有助于理解神经网络内部表示。
---

## Abstract
We present Universal Sparse Autoencoders (USAEs), a framework for uncovering and aligning interpretable concepts spanning multiple pretrained deep neural networks. Unlike existing concept-based interpretability methods, which focus on a single model, USAEs jointly learn a universal concept space that can reconstruct and interpret the internal activations of multiple models at once. Our core insight is to train a single, overcomplete sparse autoencoder (SAE) that ingests activations from any model and decodes them to approximate the activations of any other model under consideration. By optimizing a shared objective, the learned dictionary captures common factors of variation—concepts—across different tasks, architectures, and datasets. We show that USAEs discover semantically coherent and important universal concepts across vision models; ranging from low-level features (e.g., colors and textures) to higher-level structures (e.g., parts and objects). Overall, USAEs provide a powerful new method for interpretable cross-model analysis and offers novel applications—such as coordinated activation maximization—that open avenues for deeper insights in multi-model AI systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的概念可解释性方法通常只针对单个深度神经网络（DNN），无法跨越不同模型进行概念对齐与比较。随着多种强大视觉模型的涌现（如DinoV2、SigLIP、ViT），理解它们内部表示的共性与差异对于规模化可解释性、风险管理和合规监管至关重要。
- **研究动机**：已有研究表明，不同架构、初始化、任务训练的模型可能产生语义等价的潜在表示（如Rosetta Neurons、Rosetta Concepts等），但现有方法多是事后（post-hoc）的——先分别提取概念，再通过计算密集的过滤或优化进行匹配，缺乏可扩展性，也无法实现模型间的直接概念转换。
- **整体含义**：论文提出一种新范式——直接学习一个共享的概念空间，使得任意模型的激活都可以映射到同一组稀疏、可解释的概念，从而实现跨模型的概念对齐、重建和可视化。

## 2. 论文提出的方法论

### 2.1 核心思想
- 训练一个**过完备稀疏自编码器（SAE）**，使其能同时接受多个预训练视觉模型的激活作为输入，并解码重建任意模型的激活。通过共享一个稀疏编码空间 $Z$，强制所有模型的概念对齐。

### 2.2 关键技术细节
- 采用**TopK Sparse Autoencoder**结构：编码器 $Z = \text{TopK}(W_{\text{enc}}(A - b_{\text{pre}}))$，解码器 $\hat{A} = ZD$（$D$ 为字典矩阵）。
- 每个模型 $i$ 有独立的编码器 $\Psi^{(i)}_\theta$ 和解码器 $D^{(i)}$，但共享同一个概念空间 $Z$。
- 训练时，每次迭代随机选择一个模型 $i$ 进行编码，得到 $Z$，然后用所有 $M$ 个模型的解码器分别重建各自的激活，总损失为所有模型重建误差的Frobenius范数之和：
  $$L_{\text{Universal}} = \sum_{j=1}^{M} \|A^{(j)} - \hat{A}^{(j)}\|_F$$
- 仅更新被选中的编码器和对应解码器的参数。这种策略平衡了内存效率和收敛速度。
- 使用标准化预处理消除不同模型激活尺度的差异。

### 2.3 算法流程（文字说明）
1. 对每个模型，提取最后一层激活（取patch token，忽略类token，统一patch大小）。
2. 预先计算标准化参数（均值和标准差）以对齐激活尺度。
3. 在每个训练步：
   - 随机选择一个目标模型 $i$。
   - 将该模型的激活 $A^{(i)}$ 输入其编码器 $\Psi^{(i)}_\theta$，得到稀疏概念编码 $Z$。
   - 用所有模型的解码器 $D^{(j)}$ 将 $Z$ 解码为 $\hat{A}^{(j)}$。
   - 计算所有模型的重建损失并反向传播，仅更新 $\Psi^{(i)}_\theta$ 和 $D^{(i)}$ 的参数。
4. 训练完成后，得到一组对齐的编码器-解码器对，共享的概念空间 $Z$ 即可用于跨模型分析。

## 3. 实验设计

### 3.1 使用数据集与场景
- **训练集**：ImageNet训练集（仅用于SAE/USAE训练）。
- **验证/测试集**：ImageNet验证集用于定性可视化和定量评估；另外使用了**DTD（纹理数据集）** 和**CelebA（人脸属性数据集）** 进行零样本跨域泛化测试。
- **模型**：三个广泛使用的ViT架构的视觉模型：
  - **DinoV2**（自监督+蒸馏）
  - **SigLIP**（视觉-语言对比学习）
  - **ViT**（有监督ImageNet分类）

### 3.2 基准（Benchmarks）与对比方法
- **基准比较**：
  - **独立训练的SAE**：在每个模型上单独训练相同结构的TopK SAE（模型特定SAE）。
  - **随机基线**：随机采样的概念向量（从与独立SAE字典相同均值和方差的正态分布中采样）。
- **对比维度**：
  - 概念一致性：使用匈牙利算法匹配独立SAE与USAE的概念向量，计算余弦相似度分布。
  - 重建质量：$R^2$ 分数（对角线为自重建，非对角线为跨模型重建）。
  - 概念普遍性与重要性：通过**firing entropy**（衡量概念在各模型间激活分布的均匀性）和**co-fire proportion**（概念同时在所有模型激活的比例）评估。
  - 定性可视化：最高激活图像的热力图、协调激活最大化（Coordinated Activation Maximization）生成的合成图像。

### 3.3 实验类型
- **定性可视化**：展示8个代表性通用概念的热力图（颜色、形状、前景/背景、物体部件等）。
- **跨模型重建**：计算3×3的$R^2$混淆矩阵。
- **普遍性分析**：firing entropy直方图、co-fire proportion与概念能量（概念重要性）的相关性散点图。
- **概念一致性**：与独立SAE的余弦相似度分布，以及针对top 1000高co-firing概念的分析。
- **协调激活最大化**：对同一概念维度，分别优化三个模型的输入，生成可视化合成图像。
- **独特概念发现**：利用低firing entropy筛选只针对DinoV2或SigLIP的概念（如DinoV2的透视/深度线索，SigLIP的文字/音乐符号）。
- **零样本泛化**：将ImageNet训练的USAE直接应用于DTD和CelebA验证集，计算MSE和$R^2$，并展示热力图。

## 4. 资源与算力
- **GPU型号**：单块Nvidia RTX 6000 GPU。
- **训练时长**：约三天（72小时）。
- **其他细节**：使用Adam优化器，学习率从3e-4余弦衰减至1e-6；字典大小6144（扩张因子8×768）；batch size未明确给出但可推测；输入图像patch size对齐为16×16。

## 5. 实验数量与充分性
- **实验数量**：论文进行了多组定量与定性实验（至少5类定量分析+2类定性可视化+2个OOD数据集），实验设计较为全面。
- **充分性**：
  - 定量指标覆盖了重建质量、概念普遍性、重要性、一致性、跨域泛化等多个维度。
  - 定性分析提供了丰富的热力图和合成图，直观展示概念含义。
  - 针对DinoV2和SigLIP的独特概念分析提供了有洞察的发现。
- **客观性与公平性**：
  - 对比了独立SAE和随机基线，统计了AUC和阈值百分比，比较严格。
  - 消融实验方面：论文未对USAE的组件（如编码器共享、损失形式）进行消融，但提到了对超参数敏感（曾进行超参搜索）。
  - 只测试了三个模型和最后一层，模型多样性和层数覆盖有限。

## 6. 论文的主要结论与发现
1. **USAE能够发现跨模型的通用概念**：从低层颜色/纹理到高层物体部件/面孔，概念语义连贯，且不同模型的热力图一致。
2. **跨模型重建有效**：非对角线$R^2$为正，说明共享的概念空间能重建其他模型的激活，表明存在共享特征。
3. **概念普遍性与重要性正相关**：高co-firing的概念往往能量更高（更贡献于重建），且相关性在频繁co-firing概念中更强（$r=0.89$）。
4. **DinoV2具有独特的几何/深度概念**：如收敛线、倾斜角度、3D棱柱边缘等，源于其自蒸馏和掩码建模的训练目标。
5. **USAE能发现独立SAE未发现的概念**：与独立SAE的概念一致性仅为23-38%，且高普遍性概念更可能在独立SAE中出现，说明USAE偏向于学习跨模型共享的通用概念。
6. **协调激活最大化**能可视化同一概念在不同模型中的表现形式差异，例如DinoV2对曲线的激活范围更大。

## 7. 优点（方法或实验设计亮点）
- **端到端跨模型对齐**：与事后匹配方法不同，USAE在训练中强制概念对齐，避免了复杂的后处理，更高效、可扩展。
- **统一的共享概念空间**：一个概念编码可同时用于所有模型，直接支持跨模型比较和协同可视化。
- **协调激活最大化**：新颖的应用，能够同时优化多个模型的输入，揭示各模型对同一概念的编码差异。
- **发现独特模型特征**：利用低firing entropy指标自动发现特定模型的专属概念（如DinoV2的几何特征），提供了深入的模型对比分析。
- **零样本泛化能力**：在ImageNet上训练的USAE能泛化到DTD和CelebA，表明捕获的概念具有跨域迁移性。
- **开源代码**：便于复现和扩展。

## 8. 不足与局限
- **超参数敏感性**：随着模型数量增加，超参数搜调变得困难，论文提到进行了超参搜索但未详细说明。
- **仅探索最后一层**：只对每个模型的最终层激活进行建模，忽略了中间层的潜在通用概念。论文承认这一点，并留作未来工作。
- **部分概念不可解释**：与独立SAE类似，USAE中少量概念（约小百分比）无法被人类直观理解，可能仍处于“叠加”状态或属于模型特有但难以解释的特征。
- **实验模型范围有限**：仅使用了三个ViT变体（DinoV2、SigLIP、ViT），未覆盖CNN、MLP-Mixer等其他架构，因此“通用性”结论的普适性需进一步验证。
- **缺少与更多现有方法的定量对比**：论文主要与独立SAE对比，未与Rosetta Neurons、Rosetta Concepts等专门做跨模型特征匹配的方法进行定量比较（虽然提到了它们的事后性质）。
- **OOD泛化定量指标有限**：仅给出了MSE和$R^2$，未评估概念的可解释性或下游任务性能，泛化能力评估不够全面。
- **计算资源**：训练三天在单GPU上，对于更大规模模型或更多模型可能不够高效。

（完）
