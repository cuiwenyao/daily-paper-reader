---
title: "Towards Interpretability Without Sacrifice: Faithful Dense Layer Decomposition with Mixture of Decoders"
title_zh: 追求无损可解释性：基于解码器混合的忠实稠密层分解
authors: "James Oldfield, Shawn Im, Sharon Li, Mihalis Nicolaou, Ioannis Patras, Grigorios Chrysos"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=jcvX8XFNqX"
tags: ["query:ns-xai"]
score: 8.0
evidence: 忠实层分解用于LLM可解释性
tldr: 该论文针对LLM中MLP层的稠密表示难以解释的问题，提出使用解码器混合（MxDs）进行层级稀疏分解。MxDs将预训练稠密层扩展为成千上万个专门子层，通过张量分解形式忠实重建原始映射，避免了解释性方法常见的准确率损失。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 514, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1476, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1384, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 1276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1455, \"height\": 1279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1025, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 2057, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1447, \"height\": 2371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1447, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1436, \"height\": 1006, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1453, \"height\": 1757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1453, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 748, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1412, \"height\": 1648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1454, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 399, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1452, \"height\": 518, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1458, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 927, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1018, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1206, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1461, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1130, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1455, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1465, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1460, \"height\": 326, \"label\": \"Table\"}]"
motivation: 现有神经元级稀疏近似会牺牲模型原始映射的忠实性，增加损失。
method: 采用层级稀疏范式，通过解码器混合（MxDs）将稠密层分解为多个子层，实现忠实可解释近似。
result: MxDs在保持原模型交叉熵损失的同时，提供了可解释且可编辑的层表示。
conclusion: 层级稀疏分解可以在不牺牲性能的前提下实现LLM的可解释性。
---

## Abstract
Multilayer perceptrons (MLPs) are an integral part of large language models, yet their dense representations render them difficult to understand, edit, and steer. Recent methods learn interpretable approximations via neuron-level sparsity, yet fail to faithfully reconstruct the original mapping--significantly increasing model's next-token cross-entropy loss. In this paper, we advocate for moving to layer-level sparsity to overcome the accuracy trade-off in sparse layer approximation. Under this paradigm, we introduce Mixture of Decoders (MxDs). MxDs generalize MLPs and Gated Linear Units, expanding pre-trained dense layers into tens of thousands of specialized sublayers. Through a flexible form of tensor factorization, each sparsely activating MxD sublayer implements a linear transformation with full-rank weights--preserving the original decoders' expressive capacity even under heavy sparsity. Experimentally, we show that MxDs significantly outperform state-of-the-art methods (e.g., Transcoders) on the sparsity-accuracy frontier in language models with up to 3B parameters. Further evaluations on sparse probing and feature steering demonstrate that MxDs learn similarly specialized features of natural language--opening up a promising new avenue for designing interpretable yet faithful decompositions. Our code is included at: https://github.com/james-oldfield/MxD.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的详细中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）中的多层感知机（MLP）层使用稠密表示，导致这些层的内部计算难以理解、编辑和引导。现有的可解释性方法（如稀疏自动编码器、Transcoders）通过神经元级稀疏性学习近似表示，但严重损害了对原始映射的忠实地重建，显著增大了模型的交叉熵损失。
- **研究动机**：作者认为，保持对原始模型的忠实性是稀疏层分解的关键，不仅有助于准确捕捉行为细节，也有利于实际部署（可直接替代原层）。因此，他们希望设计一种既保持可解释性又几乎不牺牲模型性能的分解方法。
- **整体含义**：论文提出从“神经元级稀疏”转向“层级稀疏”，通过将密集层分解为大量专门子层，在强稀疏下仍能忠实重建原始输出，从而开辟了一条不牺牲准确性的可解释性新路径。

---

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 **Mixture of Decoders (MxD)** 层，通过条件计算和参数高效的张量分解，将预训练MLP层拆分为成千上万个稀疏激活的线性变换子层（专家），每个专家实施全秩的线性变换，从而在高度稀疏下保持表达能力。
- **关键技术细节**：
  - **模型形式**：MxD(x) = Σₙ aₙ (Wₙᵀ z)，其中 a 是稀疏专家系数（由门控网络 G 和 top-K 激活得到），z 是原始MLP的密集隐藏单元（经过激活函数），Wₙ 是第 n 个专家的权重矩阵。
  - **参数高效分解**：为避免存储 N 个完整的 H×O 矩阵（N可达数万），将权重张量 W ∈ ℝ^{N×H×O} 分解为两个矩阵 C ∈ ℝ^{N×O} 和 D ∈ ℝ^{H×O}，使得 W(n,h,:) = cₙ * dₕ（逐元素乘积）。这带来参数复杂度从 O(NHO) 降至 O((N+H)O)。
  - **前向计算等价**：MxD(x) = (Cᵀa) * (Dᵀz)（逐元素乘积），实现简单。
  - **秩保性质**：每个专家的权重矩阵 Wₙ = D diag(cₙ) 的秩等于 D 的秩（假设 diag(cₙ) 可逆）。因此即使稀疏，每个专家仍可达到与原始MLP解码器相同的满秩表达能力。
  - **扩展到GLU**：MxD可直接适配使用门控线性单元（GLU）的LLM（如Llama-3.2），只需用GLU隐藏单元替换标准隐藏单元 z。

---

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：训练使用 OpenWebText 的 4.8亿 token，上下文长度128。稀疏探针使用 SAEBench 中的24个样本级任务和10个词元级任务（如 AG News、Europarl、GitHub Code、Amazon Reviews、Bias in Bios、职业/存活/性别判别等）。特征引导使用生成文本由LLM裁判评分。
- **基准（Benchmark）**：稀疏-精度前沿（sparsity-accuracy frontier），即在不同稀疏水平 K 下替换原MLP层后模型的交叉熵损失和归一化MSE。还比较了输出空间忠实度（生成 n-gram 匹配率）和可解释性指标（稀疏探针F1分数、引导评分）。
- **对比方法**：Transcoders (TC)、Skip Transcoders (STC)、TopK-SAE（稀疏自动编码器）。所有方法均在相同参数预算下比较（MxD与TC参数数量匹敌，STC略多）。

---

### 4. 资源与算力

- **实验规模**：训练了108个稀疏层，覆盖4个LLM（GPT2-124M, Pythia-410M, Pythia-1.4B, Llama-3.2-3B）。每个模型在4种稀疏水平（K=16,32,64,128,256）下训练。
- **GPU资源**（来自附录Table 10）：
  - GPT2-124M & Pythia-410M: 各使用1张 GeForce RTX 3090（24GB），训练时长约8.5小时。
  - Pythia-1.4B: 1张 A100 80GB，23小时25分。
  - Llama-3.2-3B: 1张 A100 80GB，2天3分钟。
- **总计算量**：未给出精确总FLOPs，但根据模型大小和训练步数（约120k步），估计总计数百GPU小时。
- **额外实验**：还包括Gemma2-27B的初步实验（部分训练50k步，使用半精度、小批量），对MxD也显示了优势。

---

### 5. 实验数量与充分性

- **实验数量**：主要实验包括：
  - 4个LLM × 4-5个K值 × 3种对比方法 = 约60组稀疏层训练（正文中展示4个模型×4 K = 16组，附录中增加48组不同层的结果）。
  - 可解释性评估：24个样本级探针 + 10个词元级探针（两个LLM：GPT2 & Pythia），共68个探针任务；特征引导实验：100个神经元/专家，两个LLM裁判评分。
  - 消融实验：编码器激活函数（ReLU vs GELU vs Swish-GLU）、稀疏函数（L1 vs TopK）、低秩MoE对比、随机K训练等。
- **充分性与公平性**：
  - 充分性：实验覆盖了不同规模模型、不同稀疏水平、两个模型类型（GPT2/Pythia/Llama），评估维度包括重建精度、输出空间忠实度、探针和引导等多方面，较全面。
  - 客观性：对比方法均在同一代码框架、相同训练数据、相同参数预算条件下复现；使用标准化指标（归一化MSE、交叉熵损失、F1分数、n-gram匹配率）。
  - 公平性：MxD在参数数量上与Transcoders匹配（甚至略少），对比Skip Transcoders时MxD参数更少但仍表现出更优的稀疏-精度曲线。
  - 注意：引导实验依赖LLM作为裁判，作者已承认该方法的可靠性有争议，但使用两个不同模型取平均加以缓解。

---

### 6. 论文的主要结论与发现

- **主要结论**：MxD层在稀疏-精度前沿上显著优于现有方法（Transcoders和Skip Transcoders），在保持极低交叉熵损失的同时实现了高度稀疏（K=16时仍几乎无损）。同时，MxD学习到的专家特征在稀疏探针和特征引导任务中与SOTA方法竞争力相当，证明了层级稀疏分解可以在不牺牲性能的前提下实现可解释性。
- **关键发现**：
  - 层级稀疏（layer-level sparsity）比神经元级稀疏（neuron-level sparsity）更适合忠实近似，因为每个专家实施全秩线性变换。
  - MxD通过Hadamard积分解实现了参数高效的完全秩MoE，且自然产生了“共享专家”，增强其他专家的专业化。
  - 在输出空间，MxD生成的未来token序列与原始模型的一致性远高于基线（高达99%的1-gram匹配 vs 基线约95%）。
  - MxD在Gemma2-27B上初步实验也显示出优势，表明可扩展至更大模型。

---

### 7. 优点

- **方法论创新**：明确提出层级稀疏范式，并通过理论证明每个专家权重满秩，解决了传统神经元级稀疏的容量问题。
- **参数效率高**：通过Hadamard积分解，将专家数量扩展到数万而参数与普通Transcoder相当。
- **通用性**：无缝适配MLP和GLU架构，可直接替代原层，无需额外后处理计算。
- **实验结果扎实**：全面覆盖多种模型、多种稀疏水平、多种评估维度，结果一致优质。
- **代码开源**：提供了完整的PyTorch实现和Jupyter notebook验证等价性，可复现性高。

---

### 8. 不足与局限

- **实验覆盖有限**：
  - 直接实验仅到3B参数模型，虽然对Gemma2-27B有初步结果，但未系统验证更大模型（如70B+）。
  - 仅训练了一个种子（无误差线），因为训练成本高；但作者承认这一点。
- **计算成本**：虽然参数数量相当于Transcoder，但前向多了一个Hadamard乘积和门控网络，总体FLOPs略高（但从业者通常可接受）。
- **专家均衡问题**：MxD未内置负载均衡机制，实验中自然学习出共享专家，但作者指出在极端情况下可能需要显式均衡或多样性损失来避免专家崩溃。
- **可解释性评估的局限**：
  - 稀疏探针和引导实验依赖于预设概念或LLM裁判，可能无法全面反映真实可解释性。
  - 引导实验使用了LLM作为裁判，存在可靠性争议（已讨论）。
- **缺乏与端到端训练对比**：论文专注于替换预训练MLP层，未探讨MxD作为从头训练的可解释架构的性能。
- **需注意的偏差风险**：训练数据为OpenWebText，可能影响学到的专家特征偏向。探针任务可能选择对模型有利的样本。

---

（完）
