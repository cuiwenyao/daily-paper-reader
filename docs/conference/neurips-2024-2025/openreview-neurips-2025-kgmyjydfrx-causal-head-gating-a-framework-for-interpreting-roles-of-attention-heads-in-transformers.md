---
title: "Causal Head Gating: A Framework for Interpreting Roles of Attention Heads in Transformers"
title_zh: 因果头门控：解释Transformer中注意力头角色的框架
authors: "Andrew Joohun Nam, Henry Conklin, Yukang Yang, Thomas L. Griffiths, Jonathan D. Cohen, Sarah-Jane Leslie"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kgmyjyDFrx"
tags: ["query:ns-xai"]
score: 8.0
evidence: 因果地解释LLM注意力头角色
tldr: 现有可解释性方法多为假说驱动或需要模板。本文提出因果头门控（CHG），学习软门控为注意力头分配因果类别（促进、干扰、无关），适用于任意数据集。在Llama 3上验证，CHG分数提供因果性解释。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 404}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 471}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1428, \"height\": 633}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1420, \"height\": 576}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 478}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kgmyjydfrx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1406, \"height\": 342}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kgmyjydfrx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1263, \"height\": 396}]"
motivation: 需要可扩展且无需假说的注意力头解释方法。
method: 提出CHG，学习软门控并根据对任务性能的因果影响分类注意力头。
result: CHG在Llama 3上提供因果验证的洞见，适用于多种推理任务。
conclusion: CHG是一种通用且因果的注意力头解释工具。
---

## Abstract
We present causal head gating (CHG), a scalable method for interpreting the functional roles of attention heads in transformer models. CHG learns soft gates over heads and assigns them a causal taxonomy—facilitating, interfering, or irrelevant—based on their impact on task performance. Unlike prior approaches in mechanistic interpretability, which are hypothesis-driven and require prompt templates or target labels, CHG applies directly to any dataset using standard next-token prediction. We evaluate CHG across multiple large language models (LLMs) in the Llama 3 model family and diverse tasks, including syntax, commonsense, and mathematical reasoning, and show that CHG scores yield causal, not merely correlational, insight validated via ablation and causal mediation analyses. We also introduce contrastive CHG, a variant that isolates sub-circuits for specific task components. Our findings reveal that LLMs contain multiple sparse  task-sufficient sub-circuits, that individual head roles depend on interactions with others (low modularity), and that instruction following and in-context learning rely on separable mechanisms.

---

## 论文详细总结（自动生成）

# 论文总结：Causal Head Gating: A Framework for Interpreting Roles of Attention Heads in Transformers

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）在广泛领域取得卓越性能，但其规模和复杂性不断增加，导致模型行为难以理解、预测和控制，引发安全与误用担忧。现有机械可解释性方法主要分为两类：一是基于解码器将潜在表示映射到人类可理解概念（如句法特征），二是通过因果干预识别负责特定行为的组件（如注意力头）。这些方法多为假说驱动，需要精心设计的提示模板或目标标签，难以扩展到复杂任务（如数学推理、思维链）。此外，深度模型中的计算通常是分布式的，单个组件的角色依赖于其他组件，使得孤立理解部件行为难以预测整体行为。为此，论文提出了**因果头门控（Causal Head Gating, CHG）**，一种可扩展的方法，通过软门控学习每个注意力头对任务性能的因果影响，并赋予其促进（facilitating）、干扰（interfering）或无关（irrelevant）的分类，无需预设假说或标签。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
CHG 为每个注意力头引入一个可学习的门控参数，缩放其输出，并通过梯度优化拟合这些门控值。通过对称使用两种正则化方向（鼓励保留和鼓励去除），获得两组门控矩阵 G⁺ 和 G⁻，据此定义头部的因果分类。

### 关键技术细节
- **门控机制**：对具有 L 层、H 个头的 Transformer，定义门控矩阵 G ∈ [0,1]^{L×H}，在注意力头输出后、输出投影前进行缩放。
- **训练目标**：冻结模型参数，优化负对数似然（NLL）加上 L1 正则化项。正则化系数 λ 控制门控偏向：λ > 0 鼓励保留（G⁺），λ < 0 鼓励去除（G⁻）。
  - 损失函数：L(G; Mθ, D, λ) = -∑_{(x,y)∈D} log P(y|x; Mθ, G) - λ ∑_{i,j} σ^{-1}(G_{l,h})
- **两阶段拟合**：先用 λ=0 得到共享初始化，再分别用 λ>0 和 λ<0 拟合 G⁺ 和 G⁻，确保差异仅来自正则化。
- **因果分类**：
  - **促进（facilitating）**：G⁻ 高（即使被压制仍保持活跃），表明必要。
  - **干扰（interfering）**：1 - G⁺ 高（即使被鼓励仍被抑制），表明有害。
  - **无关（irrelevant）**：G⁻ ⊙ (1 - G⁺)，门控值随正则化方向变化。
- **对比CHG（CCHG）**：为区分子任务（如指令跟随 vs 上下文学习），使用联合目标：保留一个任务变体同时忘记另一个，通过最大化 log P(保留) - log P(忘记) 实现。

## 3. 实验设计

### 数据集与场景
- **数学推理**：OpenMathInstruct2（约5万训练样本，需链式思维+LaTeX）。
- **常识推理**：CommonsenseQA。
- **句法推理**：BIG-Bench 中的“syntax”子集（含过去时、复数、代词替换、疑问句、否定句、时态、主谓一致）。
- **函数向量任务**：6个任务（反义词、大写、国家-首都、英法翻译、现在-过去、单数-复数），以10-shot ICL或指令形式呈现。
- **符号推理（ABA/ABB）**：抽象规则任务，来自[13]。
- **模型**：Llama 3 系列（L3.1-8B, L3.2-3B, L3.2-3BI, L3.2-1B）。

### Benchmark 与对比方法
- 无传统基准，主要与**因果中介分析（CMA）** 比较（复现[12]的函数向量任务和[13]的符号推理任务）。
- 自身验证：通过逐步消融头部（按促进/无关/干扰分数排序），观察目标对数概率变化是否符合预期。

### 对比方法
- 与CMA对比：CMA具有高精度低敏感度，CHG高敏感度低精度，两者互补。
- 未与其他门控方法（如Gumbel-softmax）进行直接性能对比，但文中讨论其局限性（独立假设无法捕获头部间依赖）。

## 4. 资源与算力

论文在补充材料中明确说明：
- **硬件**：128 GB CPU RAM + 单张 Nvidia H100 GPU。
- **时间**：每次CHG运行（1500步梯度更新）耗时15分钟至1小时（取决于模型和数据集）；每次CCHG（500步）约5分钟。
- **总估算**：所有实验可在100 GPU小时内完成。不包括前期或失败实验。

## 5. 实验数量与充分性

### 实验规模
- **CHG拟合**：每个模型-任务-随机种子组合运行10次（独立种子），共4个模型×3个任务×10种子 = 120次基础CHG运行。
- **函数向量任务**：额外10种子×6任务 = 60次。
- **ABA/ABB任务**：20种子×2任务 = 40次。
- **CCHG**：6个任务，双向（遗忘ICL保留指令，反之亦然），每任务一个种子，共12次。
- **消融验证**：对每个模型-任务对，按促进/无关/干扰分数排序头部，逐步消融并记录对数概率变化。
- **相关性分析**：54个模型对间的皮尔逊相关系数。
- **CMA对比**：t检验（函数向量任务自由度23.05，符号推理任务自由度53.77）。
- **CCHG泛化**：在6个任务上交叉验证。

### 充分性评价
- **充分**：覆盖了多种任务类型（数学、常识、句法、ICL、符号推理）和多个模型变体（1B~8B，预训练/蒸馏/指令微调）。使用多随机种子评估分布和一致性。
- **客观公平**：与CMA对比时，复现了原方法并统计检验。消融实验直接验证分数与性能变化的关系。但**缺乏与同类门控方法（如Gumbel-softmax）的直接量化比较**，仅在讨论中指出其理论局限。

## 6. 论文的主要结论与发现

1. **CHG分数是因果性的**：消融实验证实，按促进分数降低性能、干扰分数提高性能、无关分数无影响。
2. **头部角色分布具有任务特异性**：数学任务激活大量促进头（52.6%得分≥0.5），而句法和常识任务大部分头部无关（约63%），表明数学任务需要更广泛的子电路。
3. **头部角色高度依赖交互，非模块化**：84%的头在至少一个种子中被标记为促进或干扰，但只有极少数在所有种子中一致，说明存在多个冗余且重叠的充足子电路。
4. **CHG与CMA互补**：CMA识别的头部在CHG中表现出显著更高的促进分数（p<10^{-8}和p<10^{-15}），验证了CHG的灵敏性。
5. **指令跟随与上下文学习的电路可分离**：CCHG 能够选择性抑制ICL而不破坏指令跟随（或反之），在6个任务中的多数上成功泛化，但某些任务（如单数-复数）存在部分电路共享。

## 7. 优点

- **无需预设假说或标签**：直接使用下一个词预测，适用于任意数据集，避免了手工提示模板和标签依赖。
- **高可扩展性**：每个头仅引入一个可学习参数，无需更新模型权重，可在几分钟内拟合数十亿参数模型。
- **提供因果分类**：不仅识别重要头，还区分促进、干扰和无关头，并验证其因果效果。
- **支持对比分析**：CCHG可隔离子任务电路，揭示不同机制（如ICL vs 指令跟随）的可分离性。
- **探索分布式计算**：通过多种子拟合估计门控分布，捕获头部间依赖性和冗余，优于独立门控方法。
- **与现有方法互补**：作为第一道诊断工具，引导更精细的因果分析（如CMA）。

## 8. 不足与局限

- **无法揭示具体计算**：CHG只标识哪些头部重要，不解释它们如何执行特定计算（如符号抽象、检索）。
- **头部角色依赖运行配置**：多头之间相互作用导致同一头在不同种子中角色不同，虽然反映了真实情况，但增加了解释难度。
- **缺乏与同类门控方法的直接对比**：未在相同条件下比较Gumbel-softmax等可微分剪枝方法的性能、稳定性和因果质量。
- **数据集局限性**：仅使用英文任务，未评估多语言或多模态场景。数学任务使用链式思维，但未分析中间步骤的电路分离。
- **计算资源需求**：虽声称高效，但每运行仍需1小时GPU，对大规模模型（如70B）可能仍需优化。
- **CCHG泛化不完全**：部分任务（如英法翻译、现在-过去）在CCHG后保留格式精度下降，表明指令跟随和ICL电路并非完全分离。

（完）
