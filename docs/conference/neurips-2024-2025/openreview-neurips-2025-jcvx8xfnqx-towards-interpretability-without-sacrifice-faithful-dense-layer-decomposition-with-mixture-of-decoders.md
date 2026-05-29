---
title: "Towards Interpretability Without Sacrifice: Faithful Dense Layer Decomposition with Mixture of Decoders"
title_zh: 面向无牺牲的可解释性：基于混合解码器的忠实密集层分解
authors: "James Oldfield, Shawn Im, Sharon Li, Mihalis Nicolaou, Ioannis Patras, Grigorios Chrysos"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=jcvX8XFNqX"
tags: ["query:ns-xai"]
score: 7.0
evidence: 通过密集层分解提升大模型可解释性
tldr: 针对大语言模型中MLP层难以理解和编辑的问题，提出混合解码器（MxDs）方法，通过层级别稀疏性将密集层分解为成千上万个专门化的子层，实现忠实重构原映射。实验表明，该方法在保持模型困惑度不显著增加的同时，大幅提升了可解释性，为模型编辑和调控提供了新途径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 257}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 514, \"height\": 297}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1345}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1476, \"height\": 934}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 393}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1384, \"height\": 622}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 1276}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1455, \"height\": 1279}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1025, \"height\": 497}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 2057}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1447, \"height\": 2371}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1447, \"height\": 1066}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1436, \"height\": 1006}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1453, \"height\": 1757}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1453, \"height\": 483}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 748, \"height\": 722}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1412, \"height\": 1648}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1454, \"height\": 713}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 399, \"height\": 483}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jcvx8xfnqx/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1452, \"height\": 518}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1458, \"height\": 179}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 191}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 927, \"height\": 222}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1018, \"height\": 144}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1206, \"height\": 180}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 157}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 199}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1461, \"height\": 195}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1130, \"height\": 262}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1455, \"height\": 157}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1465, \"height\": 309}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jcvx8xfnqx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1460, \"height\": 326}]"
motivation: LLM中MLP层的密集表示难以理解和编辑，现有稀疏方法无法忠实重建原映射。
method: 提出混合解码器（MxDs），通过张量因子化将预训练密集层扩展为大量专门子层，实现层级别稀疏性。
result: MxDs在保持模型困惑度的情况下，显著增强了对MLP层的可解释性和可编辑性。
conclusion: 层级别稀疏范式可兼顾准确性与可解释性，为LLM内部机制理解提供了有效工具。
---

## Abstract
Multilayer perceptrons (MLPs) are an integral part of large language models, yet their dense representations render them difficult to understand, edit, and steer. Recent methods learn interpretable approximations via neuron-level sparsity, yet fail to faithfully reconstruct the original mapping--significantly increasing model's next-token cross-entropy loss. In this paper, we advocate for moving to layer-level sparsity to overcome the accuracy trade-off in sparse layer approximation. Under this paradigm, we introduce Mixture of Decoders (MxDs). MxDs generalize MLPs and Gated Linear Units, expanding pre-trained dense layers into tens of thousands of specialized sublayers. Through a flexible form of tensor factorization, each sparsely activating MxD sublayer implements a linear transformation with full-rank weights--preserving the original decoders' expressive capacity even under heavy sparsity. Experimentally, we show that MxDs significantly outperform state-of-the-art methods (e.g., Transcoders) on the sparsity-accuracy frontier in language models with up to 3B parameters. Further evaluations on sparse probing and feature steering demonstrate that MxDs learn similarly specialized features of natural language--opening up a promising new avenue for designing interpretable yet faithful decompositions. Our code is included at: https://github.com/james-oldfield/MxD.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将严格遵循您的要求，对给定论文进行结构化、深入、客观的中文总结。

### 论文《Towards Interpretability Without Sacrifice: Faithful Dense Layer Decomposition with Mixture of Decoders》详细总结

#### 1. 核心问题与整体含义（研究动机与背景）

*   **核心问题**：大型语言模型（LLMs）中的多层感知器（MLP）层包含密集的、难以理解的表示。现有的，旨在通过引入“稀疏性”来提升模型可解释性的方法（例如，稀疏自编码器SAEs、Transcoders），通常在忠实还原原始MLP层功能上表现不佳，**牺牲了模型的准确性**。它们在提高可解释性的同时，会显著增加模型的交叉熵损失，无法作为原始层的完美代用品。
*   **研究动机**：作者认为，保留基础模型（base model）的性能是稀疏层逼近（sparse layer approximation）中至关重要的一环，原因有二：
    1.  **模型忠实性（Faithfulness）**：不精确的重构可能遗漏模型行为的微妙细节，导致对模型潜在特征的错误理解。
    2.  **实际应用性（Practical Adoption）**：只有能高保真地替代原始MLP层的稀疏层，才能无缝集成到模型的正向传播中，实现即插即用。否则，任何分析都只能作为事后分析（post-hoc），增加额外推理成本。
*   **整体含义**：本文旨在解决可解释性与准确性之间的根本性权衡。作者主张从“神经元级稀疏性”（neuron-level sparsity）转向“层级稀疏性”（layer-level sparsity），认为通过更宏观的、结构化的分解，可以在不牺牲模型性能的情况下获得可解释性，从而构建“无牺牲的可解释性”。

#### 2. 方法论：混合解码器（MxDs）

*   **核心思想**：提出一种名为 `混合解码器 (Mixture of Decoders, MxD)` 的新型网络层，将预训练LLM中的一个密集MLP层，分解成**成千上万个专门化的、稀疏激活的线性变换子层（专家子层）**。每个子层负责处理特定类型的输入或计算，从而在层级上实现稀疏性和专业化。
*   **关键技术细节**：
    1.  **模型形式**：MxD层替换原始MLP层，其输出是输入`x`经过一个密集编码器（`E`）和激活函数（`ϕ`，如GELU）得到隐藏状态`z`后，再由众多专家解码器分路处理并加权求和的结果：
        `MxD(x) = Σ_{n=1}^{N} a_n (W_n^T z)`，其中 `a = S(G^T x)` 是门控（gating）产生的稀疏专家系数，`W_n`是第n个专家的权重矩阵。
    2.  **高效参数化（Hadamard因子化张量分解）**：为了避免存储`N`个独立的、巨大的权重矩阵 `W_n` (维度为`H×O`)，MxD采用了一种参数高效的分解方式。将所有的专家权重统一存储为一个三阶张量`W ∈ R^{N×H×O}`，并通过以下方式参数化：
        `W(n, h, :) = c_n * d_h ∈ R^O`，其中 `*` 是逐元素乘积（Hadamard product），`c_n` 和 `d_h` 分别是可学习的矩阵`C ∈ R^{N×O}`和`D ∈ R^{H×O}`的行向量。
    3.  **保秩特性（Rank-Preserving）**：论文通过引理1证明，在这个因子化设计下，**每个专家子层`W_n`的权重矩阵的秩，与原始MLP层解码器矩阵`D`的秩相同**（前提是`c_n`的非零对角）。这意味着每个专家都是一个“全秩”的线性变换，即使在高度稀疏的情况下（只激活少量专家），组合起来的表达能力也能忠实地逼近原始密集层。相比之下，传统的稀疏MLP（如Transcoders）在隐藏层中只有K个非零神经元，输出被限制在一个低维子空间内，能力受限。
    4.  **高效前向传播**：通过引理2，MxD的正向传播可以等价地简化为两个向量的逐元素乘积：
        `MxD(x) = (C^T a) * (D^T z)`
        这种形式非常简洁高效，现有的参数高效微调方法（如MoV）被证明是其一个特例。
    5.  **拓展到门控线性单元（GLU）**：MxD的设计不依赖于特定的激活函数，因此能轻松扩展到现代LLM中更流行的GLU结构（如Swish-GLU）。论文还巧妙指出，GLU的编码器本身可以看作是一种“秩为1的专家混合”，而MxD的专家是全秩的，更具表达能力。

#### 3. 实验设计

*   **数据集/场景**：训练数据为`OpenWebText`（约4.8亿个token，上下文长度128）。评估场景包括：
    *   **稀疏层逼近**：直接衡量替换后的层与原始MLP层输出的差异。
    *   **下游任务保真度**：观察替换后的模型在`OpenWebText`上的交叉熵损失变化。
    *   **生成保真度**：对比替换前后模型生成的未来token序列的一致性。
    *   **特征可解释性**：通过稀疏探测（Sparse Probing）和特征引导（Feature Steering）评估学到的特征是否对应于可解释的、语义化的概念。使用`SAEBench`套件中的24个样本级别和10个令牌级别的探测任务。
*   **基准/Benchmark**：对比了当前最先进的三类稀疏化方法：
    *   **Transcoders (TC)**：基于神经元级稀疏性的MLP层。
    *   **Skip Transcoders (STC)**：在Transcoders基础上增加了输入到输出的跳跃连接。
    *   **TopK-SAE**：一种流行的稀疏自编码器变体。
*   **对比的方法**：除了上述基准外，在消融实验中还与低秩专家混合（μMoE）进行了对比。

#### 4. 资源与算力

*   **实验平台**：
    *   GPT2-124M和Pythia-410M使用单块 `NVIDIA GeForce RTX 3090 (24GB)`。
    *   Pythia-1.4B和Llama-3.2-3B使用单块 `NVIDIA A100 (80GB)`。
*   **训练时间**：
    *   对于K=32的实验，GPT2和Pythia-410M约需8.5小时；Pythia-1.4B约需23.5小时；Llama-3.2-3B约需2天。
*   **总结**：论文明确报告了所使用的GPU型号、显存、训练时长。总体计算资源消耗合理，属于学术界常见水平。

#### 5. 实验数量与充分性

*   **实验数量**：
    *   **核心实验**：在4个不同规模（124M到3B参数）的LLM上训练108个稀疏层，涵盖不同的层数（如Layer 8, 10, 12, 15等）和不同的稀疏度K（16, 32, 64, 128, 256），共进行了**60+**组核心训练。
    *   **可解释性评估**：34个稀疏探测任务和2个LLM作为裁判的特征引导评估。
    *   **消融研究**：对激活函数选择、编码器架构、专家秩、有无共享专家等多个方面进行了详尽的消融分析。
*   **充分性与公平性**：
    *   **充分性**：实验覆盖了模型规模、层数、稀疏度等多个维度，评估了从重构误差到下游任务再到解释性的多方面性能，实验设计较为全面。
    *   **客观与公平**：与SOTA基线进行公平的参数数量匹配对比。实验设置详尽，可复现性高。在生成保真度评估中采用了严格的“n-gram精确匹配”标准。

#### 6. 主要结论与发现

1.  **MxD显著优于现有方法**：在稀疏度和准确性的权衡曲线上，MxD在所有4个LLM模型和所有稀疏度水平下，均**帕累托主导**了Transcoders和Skip Transcoders，即实现了更低的重构误差和更小的模型性能损失。
2.  **高保真度**：与基线相比，MxD替换原MLP层后，模型的下游交叉熵损失增加最小，未来token生成与原始模型的匹配度最高（展示出高出近1倍的匹配率），表明其学习到了更忠实的模型功能近似。
3.  **特征专业化**：尽管重构能力极强，MxD的专家同样学习到了类似的专业化特征，在稀疏探测和特征引导任务上与SOTA基线（如Transcoder）表现持平或更具竞争力，证明了其解耦出的子模块同样具有可解释性。

#### 7. 优点

1.  **创新的方法论**：开创性地提出“层级稀疏性”作为解决可解释性与准确率权衡的新范式，并通过设计优雅、参数高效的`MxD`层实践了这一理念。将神经网络分析推向更结构化的单元。
2.  **严格的数学证明**：对`MxD`的保秩特性（Lemma 1）和高效前向传播（Lemma 2）提供了清晰的数学证明，理论依据坚实。
3.  **全面的实验验证**：从多个维度（重构误差、下游任务损失、生成保真度、特征可解释性）进行了充分的对比实验和消融研究，结果具有很强的说服力。
4.  **强大的保真度**：解决了当前可解释性方法在精度和忠实度上的一个关键痛点。MxD既能高保真地替代原始层，又保留了进行可解释分析的能力，这是其最大的亮点之一。

#### 8. 不足与局限

1.  **计算效率评估不足**：论文主要对比参数数量，但对实际推理/训练FLOPs/速度的分析不够深入。虽然理论FLOPs相似，但MxD的“门控”计算和“逐元素乘法”可能引入额外的计算开销。作者提及了未来探索更高效检索结构的必要性。
2.  **对极大模型的泛化能力**：实验只覆盖了至多3B参数的模型。尽管作者认为趋势会延续，但尚未在更大模型（70B+）上进行验证，其可扩展性和性能需要进一步确认。
3.  **专家不平衡与塌缩风险**：作者承认MxD可能面临专家不平衡或退化的风险。尽管初始实验中没有发现，但当在更大的模型或不同的训练目标下，可能需要进行负载均衡。
4.  **特征评估方法的主观性**：特征引导评估依赖于两个LLM裁判，而LLM作为裁判的可靠性在学界仍有争议。虽然作者采用了两个SOTA模型，但绝对分数值的解释仍应谨慎。

（完）
