---
title: "How Transformers Learn Structured Data: Insights From Hierarchical Filtering"
title_zh: Transformer如何学习结构化数据：来自层次过滤的洞见
authors: "Jerome Garnier-Brun, Marc Mezard, Emanuele Moscato, Luca Saglietti"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AVXApuBCvN"
tags: ["query:ns-xai"]
score: 7.0
evidence: 研究Transformer如何学习结构化数据并近似推理，对可解释性有贡献
tldr: 本文通过层次过滤方法，揭示了Transformer在树结构数据上能够学习到精确推理算法，随着层次增加逐步捕获远距离相关性，从而为理解Transformer内部推理机制及可解释性提供了重要洞见。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1504, \"height\": 767, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 719, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 627, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 741, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 380, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 877, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 377, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 719, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 725, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 631, \"height\": 824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 718, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-avxapubcvn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 513, \"height\": 418, \"label\": \"Figure\"}]"
motivation: 理解Transformer的学习过程和内部计算对于开发可解释AI至关重要。
method: 引入层次过滤过程，控制序列中位置相关性的范围，并在根分类和掩码语言建模任务上训练Transformer。
result: 发现标准编码器Transformer能够近似精确推理算法，且层次越高的相关性越晚被网络纳入。
conclusion: 研究工作揭示了Transformer在结构化数据上的推理学习机制，有助于可解释AI的发展。
---

## Abstract
Understanding the learning process and the embedded computation in transformers is becoming a central goal for the development of interpretable AI. In the present study, we introduce a hierarchical filtering procedure for data models of sequences on trees, allowing us to hand-tune the range of positional correlations in the data. Leveraging this controlled setting, we provide evidence that vanilla encoder-only transformers can approximate the exact inference algorithm when trained on root classification and masked language modeling tasks, and study *how* this computation is discovered and implemented. We find that correlations at larger distances, corresponding to increasing layers of the hierarchy, are sequentially included by the network during training. 
By comparing attention maps from models trained with varying degrees of filtering and by probing the different encoder levels, we find clear evidence of a reconstruction of correlations on successive length scales corresponding to the various levels of the hierarchy, which we relate to a plausible implementation of the exact inference algorithm within the same architecture.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：理解 Transformer 如何在结构化数据（特别是具有层次相关性的序列）中学习，并逼近最优推理算法，以促进可解释 AI 的发展。
- **背景**：尽管 Transformer 在自然语言处理等领域表现出色，但其内部工作机制仍不清楚。先前研究多在简化语言模型（如上下文无关文法 CFG）上进行，但缺乏对内部计算的深入解释。本文通过构建一个可控的层次数据模型，揭示 Transformer 如何逐步发现并利用层次结构，以及其注意力机制如何近似信念传播（Belief Propagation, BP）算法。

## 2. 论文提出的方法论

- **核心思想**：引入一个基于树的层次生成模型，通过“过滤参数” $k$ 控制序列中位置相关性的范围（$k=0$ 为完全层次相关，$k=4$ 为条件独立）。然后训练标准 encoder-only Transformer，对比其输出与 BP 算法给出的精确边际概率，分析其学习动态与内部表征。
- **关键技术细节**：
  - **数据生成**：固定深度 $\ell=4$ 的二叉树，根节点采样后通过一个随机转移张量 $M$（对数正态采样，非重叠条目）生成子节点，最终得到 $2^\ell$ 个叶子节点作为序列。
  - **过滤机制**：参数 $k$ 表示在树中第 $k$ 层以上进行条件独立采样，仅保留 $k$ 层以下的层次相关性。这使得可以生成具有不同程度结构的数据。
  - **Transformer 架构**：使用单头自注意力，嵌入维度 $d=128$，前馈隐藏维度 $d'=2048$，层数 $n_L=\ell=4$。采用正弦位置编码和层归一化。任务包括根分类（全序列读出）和掩码语言建模（MLM，单点读出）。
  - **基准方法**：精确的 Belief Propagation（BP）算法，可在树上高效计算任意节点（根或叶子）的边际概率，作为最优解。
  - **分析手段**：比较 Transformer 输出概率与 BP 边际的 Kullback-Leibler 散度、注意力图可视化、以及通过探针（probe）方法分析各编码层中祖先信息的恢复程度。
- **公式 / 算法流程**（文字说明）：
  - BP 算法在树上进行上向和下向两次消息传递，消息更新涉及转移张量 $M$ 的求和。对于过滤后的树，更新规则在过滤层上下有所不同（见附录 B）。
  - 论文附录 F 提出了一种可能的 Transformer 实现 BP 的方案，利用 token 嵌入中的特殊结构（包含 $q^2$ 个辅助向量）和位置编码，在 $\ell$ 层内完成上向计算，避免了标准 BP 所需的 $2\ell$ 层。

## 3. 实验设计

- **数据集 / 场景**：使用合成数据，树深度 $\ell=4$，词汇大小 $q=4$。转移张量 $M$ 随机生成（种子 0，$\sigma=1$）。生成的数据具有不同的过滤参数 $k\in\{0,1,2,3,4\}$，以控制层次相关性的范围。
- **Benchmark**：BP 算法作为 oracle，包括匹配过滤参数（$k_{\text{train}}=k_{\text{test}}$）和不匹配（$k_{\text{train}}\neq k_{\text{test}}$）的情况。
- **对比方法**：没有与其他神经网络模型对比；主要将 Transformer 与 BP 进行比较，并分析不同 $k$、不同训练数据量 $P$、不同注意力层数 $n_L$ 下的表现。另外，比较了 MLM 预训练对根分类任务的影响。
- **主要实验组**：
  - 根分类任务：不同 $k$ 下测试准确率随训练样本数 $P$ 的变化；学习动态（准确率和 KL 散度随 epoch 变化）；out-of-sample 测试。
  - MLM 任务：类似的学习动态和准确率对比；注意力图可视化（不同 $k$ 下直接显示层次模式）。
  - 探针实验：在冻结的 MLM 编码器上训练一个二层 readout，预测 token 的祖先符号（不同层级的祖先），验证各编码层包含的层次信息。
  - 消融实验：不同注意力层数 $n_L$、不同随机种子/语法下的鲁棒性。
  - MLM 预训练效果：预训练后微调根分类任务，对比冻结/解冻编码器权重下的样本效率。

## 4. 资源与算力

- 论文中未明确说明使用了何种 GPU 型号、数量或训练时长。仅提及使用 PyTorch 实现，Adam 优化器，batch size=32，学习率 $10^{-4}$，其余参数为默认值。所有实验均在单个节点上完成，但具体硬件信息缺失。因此无法评估算力开销。

## 5. 实验数量与充分性

- **实验数量**：论文进行了大量实验，覆盖：
  - 两种任务（根分类、MLM）下多种过滤参数 $k=0,...,4$ 的完整训练与测试。
  - 不同训练样本数 $P$（从 $2^{13}$ 到 $2^{20}$ 量级）。
  - 学习动态记录（epoch vs 准确率、KL 散度）。
  - 注意力图可视化（每个 $k$ 一张图）。
  - 探针实验（不同编码层、不同祖先层级）。
  - 消融实验：不同注意力层数 $n_L$（1-4）、不同随机种子（3 个额外语法）。
  - MLM 预训练效果比较。
- **充分性**：实验设计系统，逐步验证了 Transformer 逼近 BP 的能力、学习顺序、空间结构对应关系。每个实验均与 BP oracle 对比，公平客观。消融实验覆盖了关键超参数和随机性。探针实验进一步排除过拟合可能性。总体而言，实验充分，结论有说服力。

## 6. 论文的主要结论与发现

- Transformer 不仅能在根分类和 MLM 任务上达到与 BP 算法相同的准确率，还能在校准意义上匹配 BP 输出的完整边际概率分布（即输出概率与 BP 边际接近），尤其在 $k>0$ 的歧义情况下也自然校准，表明其内部计算与精确推理等价。
- 训练过程中，Transformer 按层次逐步发现更远距离的相关性：先学习短程相关（对应低层祖先），再学习长程相关（对应高层祖先）。这一过程在 KL 散度对 BP $k$ 的序贯对齐中清晰体现。
- 注意力图呈现与树结构一致的层次块模式：对于 $k$ 越小（相关性越强），注意力图的块大小约为 $2^{\ell-k}$，且不同编码层分别对应树的不同层级。探针实验表明，第 $m$ 层编码主要恢复至树中第 $m$ 层祖先的信息，符合 BP 的上向传播过程。
- MLM 预训练可以显著提升根分类的样本效率，且冻结编码器权重也能获得收益，说明预训练习得了层次结构表征。

## 7. 优点

- **方法设计简洁可控**：使用固定树拓扑和过滤参数，允许精确的 BP 解作为 gold standard，便于量化分析 Transformer 的学习行为。
- **揭示学习动态**：通过动态监测 KL 散度对齐，直观展示了 Transformer 如何“由近及远”地发现层次结构，与信号-噪声理论一致。
- **提供可解释性分析**：注意力图可视化与探针实验相结合，直接展示了模型内部表征与计算流程的层次性，且提出了一种可能的 BP 实现方案（附录 F），增强了机理解释力。
- **实验系统全面**：涵盖两种任务、多种过滤级别、训练数据量、消融实验、预训练效果，并验证了不同随机种子下的鲁棒性，结论可靠。

## 8. 不足与局限

- **模型简化**：数据模型假设固定二叉树、单一词汇、非重叠转移张量（即子节点对唯一确定父节点），与真实语言的复杂性（可变序列长度、多词汇类别、歧义规则等）差距较大。因此结论向实际 NLP 模型的泛化需谨慎。
- **架构局限**：仅研究 encoder-only 单头注意力 Transformer，未涉及 decoder-only 或多头注意力。此外，嵌入维度 $d=128$ 较小，可能影响 BP 嵌入的可行性（附录 F 需要 $d=q^2+2q+\ell=4^2+8+4=28$，但实现中实际使用 128）。
- **缺乏理论分析**：样本复杂度 $P^*$ 与语法参数（如 $q$、$\sigma$、$k$）的缩放关系未给出理论公式，仅给出实验观察。
- **硬件资源未报告**：无法评估实验的可重复性与算力要求。
- **应用限制**：该模型主要用于理解机制，直接应用于法律、医疗等高风险领域需要更完善的理论保证。

（完）
