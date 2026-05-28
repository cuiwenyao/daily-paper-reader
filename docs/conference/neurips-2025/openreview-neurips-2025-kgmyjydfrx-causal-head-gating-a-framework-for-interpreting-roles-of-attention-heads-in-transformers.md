---
title: "Causal Head Gating: A Framework for Interpreting Roles of Attention Heads in Transformers"
title_zh: 因果头门控：解释Transformer中注意力头角色的框架
authors: "Andrew Joohun Nam, Henry Conklin, Yukang Yang, Thomas L. Griffiths, Jonathan D. Cohen, Sarah-Jane Leslie"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kgmyjyDFrx"
tags: ["query:ns-xai"]
score: 8.0
evidence: 因果解释LLM中注意力头的功能角色
tldr: 理解LLM中注意力头的功能对可解释性至关重要。本文提出因果头门控（CHG）方法，通过学习软门控为注意力头分配因果分类（促进、干扰、无关），不需要假设驱动，直接适用于任何数据集。在Llama 3系列模型上，CHG在语法、常识和数学推理任务中提供了因果验证的洞察。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1428, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1420, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kgmyjydfrx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 478, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kgmyjydfrx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1406, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kgmyjydfrx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1263, \"height\": 396, \"label\": \"Table\"}]"
motivation: 现有注意力头解释方法依赖假设驱动，需要模板或标签，且缺乏因果验证。
method: 通过软门控学习注意力头的因果角色分类，并基于因果效应进行验证。
result: 在多个推理任务上，CHG成功识别出促进和干扰的注意力头，并提供因果证据。
conclusion: 为LLM可解释性提供了一种可扩展的因果分析方法，揭示了注意力头在推理中的功能。
---

## Abstract
We present causal head gating (CHG), a scalable method for interpreting the functional roles of attention heads in transformer models. CHG learns soft gates over heads and assigns them a causal taxonomy—facilitating, interfering, or irrelevant—based on their impact on task performance. Unlike prior approaches in mechanistic interpretability, which are hypothesis-driven and require prompt templates or target labels, CHG applies directly to any dataset using standard next-token prediction. We evaluate CHG across multiple large language models (LLMs) in the Llama 3 model family and diverse tasks, including syntax, commonsense, and mathematical reasoning, and show that CHG scores yield causal, not merely correlational, insight validated via ablation and causal mediation analyses. We also introduce contrastive CHG, a variant that isolates sub-circuits for specific task components. Our findings reveal that LLMs contain multiple sparse  task-sufficient sub-circuits, that individual head roles depend on interactions with others (low modularity), and that instruction following and in-context learning rely on separable mechanisms.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）日益复杂和黑箱化，理解其内部机制对安全与可控性至关重要。现有可解释性方法主要分为两类：一是基于表示解码的探针方法（correlational, 需标签）；二是因果中介分析（CMA，需手工构造提示模板和假设）。两者均存在局限性：探针方法只能发现相关性而非因果性，CMA则依赖特定假设，难以推广到开放式任务（如数学推理）。论文旨在提出一种可扩展的、因果性的、无需标签和手工模板的注意力头角色解释方法——**因果头门控（CHG）**，为每个注意力头分配一个因果分类（促进、干扰、无关），从而揭示其对任务性能的真实影响。

## 2. 论文提出的方法论

### 核心思想
- 对每个注意力头学习一个软门控系数 \(G_{\ell,h} \in [0,1]\)，乘在注意力头输出上（紧接在输出投影矩阵之前），从而调节该头的贡献。
- 通过两种相反的正则化方向（激励保留 \(\lambda>0\) 和激励移除 \(\lambda<0\)）分别得到 \(G^+\) 和 \(G^-\)，再基于它们定义三类因果角色。
- 联合优化所有头的门控，捕捉头之间的交互依赖关系（区别于独立假设的Gumbel方法）。

### 关键技术细节
- **门控注入位置**：在每层多头注意力的输出投影前，对每个头输出进行缩放。
- **目标函数**：负对数似然（NLL）+ L1正则化项。
  \[
  \mathcal{L} = -\sum_{(x,y)\in D} \log P(y|x; M_\theta, G) - \lambda \sum_{i,j} \sigma^{-1}(G_{l,h})
  \]
  其中 \(\sigma^{-1}\) 是裁剪后的反sigmoid函数。
- **两阶段拟合**：
  1. 先用 \(\lambda=0\) 拟合得到共享初始 \(G\)；
  2. 再用 \(\lambda>0\) 得到 \(G^+\)，\(\lambda<0\) 得到 \(G^-\)。
- **因果分类规则**（表1）：
  - 促进头：\(G^-\) 高（移除压力下仍活跃）→ 抑制它会降低性能。
  - 干扰头：\(1-G^+\) 高（保留压力下仍被抑制）→ 抑制它会提升性能。
  - 无关头：\(G^- \odot (1-G^+)\) 高 → 抑制它无影响。
- **对比CHG（CCHG）**：扩展用于分离子任务，联合目标为忘记一个变体而保留另一个，损失函数包含两个变体的似然差。

## 3. 实验设计

### 使用的数据集与任务
- **数学推理**：OpenMathInstruct2（约55k短样本，要求链式思考+LaTeX输出）
- **句法推理**：BIG-Bench中的语法子任务（时态、复数、主谓一致等）
- **常识推理**：CommonsenseQA
- **函数向量任务**（六种）：antonym, capitalize, country-capital, English-French, present-past, singular-plural（ICL和指令两种格式）
- **符号推理**：ABA/ABB模式任务（来自[13]）

### 模型
- Llama 3家族：L3.2-1B、L3.2-3B、L3.2-3B-I（指令微调版）、L3.1-8B

### 对比方法
- 与**因果中介分析（CMA）** 对比：在函数向量任务和ABA/ABB任务上，比较CMA识别的头与CHG的促进分数，用t检验验证一致性。
- 与**随机或随意消融**对比：通过逐步消除按分数排序的头，观察性能变化是否符合预测。

## 4. 资源与算力

文中明确提到：
- 使用**128GB CPU RAM和单张Nvidia H100 GPU**。
- 每次CHG运行（1500梯度更新）耗时**15分钟至1小时**，取决于模型和数据集。
- 每次CCHG运行（500更新）约**5分钟**。
- 估计所有实验可在**100 GPU小时**内完成（不含前期探索实验）。

## 5. 实验数量与充分性

- **CHG拟合**：每个模型-数据集对独立拟合10个随机种子。
- **因果角色分布分析**：4个模型 × 3个任务 = 12组分布，并计算了54个模型对的Pearson相关性（最低94.92%，平均99.2%）。
- **消融验证**：对所有任务和模型，按分数顺序逐步消融头，观察log概率变化，定性匹配分类预测。
- **CMA对比**：函数向量任务上做10次CHG拟合，ABA/ABB任务上20次，取最大促进分数与CMA头比较；t检验结果显著（p<10^-8和p<10^-15）。
- **CCHG实验**：6个函数向量任务，分别做两种方向（忘记ICL保留指令，忘记指令保留ICL），每个任务作为留出任务评估，覆盖率全面。
- **总体评价**：实验覆盖了多种任务类型、多个模型大小（1B~8B）、训练范式（预训练、蒸馏、指令微调），并进行了消融、CMA对比和泛化验证，充分性较高。实验设计客观，主要结论有统计支持。

## 6. 论文的主要结论与发现

1. **CHG分数具有因果预测力**：按促进/无关/干扰分数顺序消融，性能分别下降/不变/上升，与分类定义一致。
2. **头角色分布因任务而异**：句法和常识任务中多数头为无关（约63-65%），仅稀疏促进头（约25-27%）；数学推理任务中促进头比例更高（约53%），反映更高复杂度。
3. **存在多个稀疏的、重叠的任务充分子电路**：大部分头（84%）在至少一个种子中被标记为促进或干扰，但仅少数头在所有种子中一致（<5%），说明头角色依赖与其他头的交互（低模块性）。
4. **指令跟随与上下文学习依赖可分离的电路**：CCHG成功选择性地抑制一种模式而不严重损害另一种，且泛化到留出任务，表明两种能力可在头级别分离。

## 7. 优点

- **因果性而非相关性**：通过软门控直接干预，并验证了消融效果，提供因果洞察。
- **无需标签或手工模板**：仅需任务数据集和标准下一个词预测，适用范围广。
- **可扩展**：每个头只引入一个参数，无需微调模型权重，在数十亿参数模型上几分钟即可完成拟合。
- **可重复性与统计稳健性**：支持多次拟合（bootstrap），揭示头角色的分布和依赖结构。
- **对比CHG扩展**：能分解子任务，分离指令跟随和ICL电路，展示了方法的多用性。
- **与现有方法互补**：可作初步诊断，指导CMA等精细分析。

## 8. 不足与局限

- **仅识别因果影响，不解释具体计算**：CHG不能揭示头“如何”执行功能，仅指出哪里重要。
- **头角色因种子而异**：低一致性（<5%的恒定出头）增加解释难度，作者归因于分布式交互，但仍可能是方法不稳定性的表现。
- **仅限于注意力头**：未处理MLP等其他组件，模型行为更复杂。
- **正则化强度λ和训练超参需手动设定**：论文使用固定λ=±0.1，可能对某些任务非最优。
- **CCHG的泛化性有限**：留出任务上部分任务（如country-capital）在指令保持时健壮，但其他任务退化明显，说明分离并非完全。
- **实验模型仅限于Llama 3系列**：结论是否适用于GPT、DeepSeek等其他架构尚需验证。
- **未讨论负面社会影响**：作为基础可解释性方法，当前无直接应用风险，但作者未深入探讨可能的误用场景（如攻击模型）。

（完）
