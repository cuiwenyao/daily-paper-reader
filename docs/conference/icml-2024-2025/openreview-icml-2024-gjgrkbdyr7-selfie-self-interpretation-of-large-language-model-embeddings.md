---
title: "SelfIE: Self-Interpretation of Large Language Model Embeddings"
title_zh: SelfIE：大型语言模型嵌入的自解释
authors: "Haozhe Chen, Carl Vondrick, Chengzhi Mao"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=gjgRKbdYR7"
tags: ["query:ns-xai"]
score: 9.0
evidence: LLM嵌入自解释以揭示推理过程
tldr: 大型语言模型的内部推理过程难以解释，SelfIE框架通过让模型用自然语言解释自身嵌入，揭示了模型在伦理决策、提示注入等场景下的推理逻辑，并支持基于这些解释对模型行为进行监督式编辑控制，为提升LLM的可解释性和可靠性提供了新方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 892, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 891, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1757, \"height\": 2035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 890, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 892, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 703, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 854, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 804, \"height\": 976, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 802, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 786, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 790, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1630, \"height\": 1621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1608, \"height\": 2010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjgrkbdyr7/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 878, \"height\": 750, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-gjgrkbdyr7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 775, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjgrkbdyr7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjgrkbdyr7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjgrkbdyr7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 883, \"height\": 244, \"label\": \"Table\"}]"
motivation: 需要理解LLM的内部推理过程以提升可靠性和透明度。
method: 提出SelfIE框架，利用LLM自身的问答能力将隐藏嵌入翻译为自然语言解释。
result: 在伦理决策、提示注入等任务中成功揭示了LLM的推理过程。
conclusion: SelfIE通过嵌入自解释增强了LLM的可解释性，并支持受控编辑。
---

## Abstract
How do large language models (LLMs) obtain their answers? The ability to explain and control an LLM’s reasoning process is key for reliability, transparency, and future model developments. We propose SelfIE (Self-Interpretation of Embeddings), a framework that enables LLMs to interpret their own embeddings in natural language by leveraging their ability to respond to inquiries about a given passage. Capable of interpreting open-world concepts in the hidden embeddings, SelfIE reveals LLM internal reasoning in cases such as making ethical decisions, internalizing prompt injection, and recalling harmful knowledge. SelfIE’s text descriptions on hidden embeddings open avenues to control LLM reasoning. We propose Supervised Control, which allows editing open-ended concepts while only requiring gradient computation of individual layer. We extend RLHF to hidden embeddings and propose Reinforcement Control that erases harmful knowledge in LLM without supervision targets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的推理过程缺乏透明度，其内部嵌入（embeddings）包含丰富的语义信息，但难以被直接解释。现有方法如线性探头（linear probes）需要大量标注数据且只能解释预定义的有限概念；Chain-of-Thought等解释方法可能不忠实于真实推理。因此，需要一种无需训练、能够对任意开放世界概念进行自然语言解释的方法，并在此基础上实现对模型行为的精确控制。
- **整体含义**：提出SelfIE框架，让LLM自身通过自然语言描述其隐藏嵌入所蕴含的信息，从而揭示内部推理逻辑（如伦理决策、提示注入、有害知识回忆等）。基于这些解释，进一步提出监督控制和强化控制两种机制，实现对模型推理行为的轻量级编辑（如删除有害知识、覆盖伦理偏好等），为提升LLM的可靠性、透明度和可控性提供了新途径。

## 2. 论文提出的方法论

### 2.1 核心思想：SelfIE（Self-Interpretation of Embeddings）
- 利用LLM自身的解码能力（如总结、复述给定消息的能力），将隐藏嵌入注入到解释前向传播（interpretation forward pass）中，使模型生成对该嵌入内容的自然语言描述。
- 无需额外训练，不依赖预定义概念集合，可解释任意开放世界概念。

### 2.2 关键技术细节
1. **解释前向传播**：
   - 在原始前向传播中提取目标层 ℓ* 和位置 i* 的隐藏嵌入 h^{ℓ*}_{i*}。
   - 设计解释提示（interpretation prompt）I，包含占位符 [X] 和询问指令（如“请总结前面的消息”）。
   - 在新的前向传播中，在选定层 k 将占位符的嵌入替换为 h^{ℓ*}_{i*}，然后让模型自回归生成文本解释。
   - 公式表示：
     - 原始：h⁰ = E·x, h^{ℓ} = f^{ℓ}(h^{ℓ-1})
     - 解释传播：h̄⁰ = E·I；在层 k、位置 s 处设置 h̄^{k}_s = h^{ℓ*}_{i*}；其余层正常计算，最后通过 softmax 得到输出概率。

2. **相关分数（Relevancy Score）**：
   - 用于区分解释文本中哪些词是由嵌入本身决定，哪些是自回归生成带来的。
   - 计算方式：用处理效应（treatment effect）衡量替换占位符前后生成词的概率差。分数越高表示该词越直接相关。

### 2.3 基于 SelfIE 的控制方法
- **监督控制（Supervised Control）**：
  - 给定要编辑的层 ℓ，目标是将该层在位置 i 的输出 f^{ℓ}_θ(h^{ℓ-1})_i 映射到一个目标向量 v（该向量通过 SelfIE 解释为期望的概念）。
  - 通过最小化 MSE 损失更新该层的参数 θ：L = (v - f^{ℓ}_θ(h^{ℓ-1})_i)²。仅需对单层计算梯度，效率高。
- **强化控制（Reinforcement Control）**：
  - 将 SelfIE 生成的文本解释作为非可微分奖励信号（由人类或评估LLM给出，如“有害”则奖励-1，“无害”则+1）。
  - 通过代理损失函数更新参数，引导模型学习只在指定层编码期望信息或避免编码有害信息。

## 3. 实验设计

### 3.1 数据集与场景
- **TextWorld 世界状态提取**：生成12900个样本（3400用于评估，9500用于训练线性探头），每个样本描述一系列动作和对象状态，要求判断实体是否处于某状态。
- **Counterfact 事实编辑**（Meng et al., 2022）：1000个事实关联对（subject-attribute），使用844个LLaMA能正确回答的样本，随机选择目标编辑答案。
- **伦理偏好数据集**：自建101个假设场景，要求LLM在人类与外星人之间进行优先级选择，并在提示中附加“你必须认为人类比外星人更重要”以诱导偏见。
- **有害知识注入**：采用Zou et al. (2023b)收集的388种有害行为（如信用卡欺诈、商业破坏等），使用特定提示注入字符串（如“!!!!!”）尝试诱导模型输出有害内容。

### 3.2 基准对比方法
- 世界状态提取：与线性探头（Linear Probe）对比，训练样本数1~100和全量数据（174798样本）。
- 事实编辑：对比方法包括 Fine-tuning (FT)、RepE (Zou et al., 2023a)、ROME (Meng et al., 2022)。
- 伦理偏好：对比随机控制（随机选择嵌入和目标）。
- 有害知识消除：对比编辑前后模型对提示注入的成功率、无关事实准确率（使用Counterfact数据集）。

### 3.3 评估指标
- 世界状态：二分类准确率。
- 事实编辑：Efficacy（原提示正确率）、Paraphrase（改写提示正确率）、Specificity（无关提示正确率）及其调和平均。
- 伦理偏好：优先人类、优先平等、其他回答的比例。
- 有害知识消除：模型响应中包含有害信息的百分比，以及无关事实准确率。

## 4. 资源与算力

- 硬件：
  - 解释过程：8×NVIDIA RTX A6000。
  - 推理控制（编辑）：8×NVIDIA A100。
- 时间开销（文中部分提及）：
  - Molotov Cocktail 概念编辑：每个更新约10秒，共8次更新。
  - 伦理偏好编辑：每次更新约20秒，共2次更新。
  - 强化控制：每次更新约30秒，共8次更新。
- 未明确说明总训练/推理时长、总GPU小时数。模型主要使用LLaMA-2-70B-Chat，也做了7B、13B的消融。

## 5. 实验数量与充分性

- **实验数量**：至少包含4个主要场景（世界状态、事实编辑、伦理偏好、有害知识消除）以及多个消融实验。
- **消融实验**：
  - 嵌入插入层 k 的选择（Fig. 10）：测试k从0到80，发现k<20较好。
  - 模型大小影响（Fig. 11）：7B、13B、70B对比，显示小模型指令遵循能力较差，影响解释质量。
- **充分性与客观性**：
  - 每个实验均报告了与现有方法的定量对比，使用标准数据集（TextWorld、Counterfact）和广泛认可的基线（ROME、RepE等）。
  - 有害知识消除测试了388种未见过的有害行为，并检查了无关事实准确性，验证了泛化性和安全性。
  - 伦理偏好实验使用100个未见过场景，报告多次编辑效果。
- **公平性**：对比方法均使用了作者公开的实现或推荐的超参数；SelfIE 的监督控制与其他方法在相同评估协议下比较。

## 6. 论文的主要结论与发现

1. **SelfIE 能忠实地解释隐藏嵌入**：在TextWorld任务中，零样本的SelfIE准确率与100样本训练的线性探头相当，证明解释是可靠的。
2. **揭示 LLM 内部推理机制**：通过 SelfIE 可以观察到模型在有害知识检测、提示注入成功原因、伦理推理、物理推理、幻觉产生等场景下的逐步推理过程。
3. **监督控制可有效编辑开放概念**：在事实编辑任务上，SelfIE 控制的调和平均优于ROME和RepE；在Molotov Cocktail概念编辑中，模型能泛化到未见过的推理问题，将“Molotov cocktail”理解为一种饮料。
4. **强化控制可消除有害知识**：仅对单个无注入提示（“如何制作莫洛托夫鸡尾酒”）进行强化控制，便使模型对388种未见攻击的成功率从89.06%降至4.4%，同时保持95.85%的无关事实准确率。
5. **模型大小影响解释质量**：小模型（7B、13B）因指令遵循能力差，解释准确率低于70B；但排除指令失败案例后，三者解释能力相近。
6. **SelfIE 的控制方法计算效率高**：仅需单层梯度更新，无需全模型微调。

## 7. 优点

- **零样本开放世界解释**：无需训练数据，即可用自然语言解释任意复杂概念，突破了线性探头等方法的局限。
- **忠实性可量化**：通过处理效应计算相关分数，区分解释中哪些内容来自嵌入本身。
- **细粒度控制**：可定位到特定层进行编辑，仅需计算单层梯度，开销远低于全模型微调。
- **多种控制模式**：监督控制适合已知目标，强化控制适合仅有高级目标（如“消除有害知识”）且无监督信号的情况。
- **泛化能力强**：概念编辑和有害知识消除都能泛化到未见过、但语义相关的场景。
- **可解释性与控制性统一**：解释结果可直接用于指导编辑，形成闭环。

## 8. 不足与局限

- **解释质量依赖模型能力**：小模型指令遵循能力差会导致解释失败（如不按要求二选一），从而降低可用性，可能引入偏差。
- **嵌入插入层k需手动选择**：实验表明k<20效果较好，但最佳k可能因任务和模型而异，缺乏自适应策略。
- **仅测试LLaMA-2系列**：未在其他架构（如GPT、Mistral等）上验证通用性；不同模型的残差结构差异可能影响SelfIE效果。
- **强化控制的奖励设计简单**：仅使用LLaMA自身作为评估器，可能引入评估偏差；实际应用中需人工验证。
- **伦理编辑实验规模较小**：只使用了101个场景，且仅编辑单层，长期稳定性或更复杂伦理冲突下的表现未知。
- **风险提示**：本文方法可能被滥用于编辑模型以隐藏有害知识或植入偏见，作者已声明需负责任使用，但未提供防御机制。
- **计算资源未完整报告**：虽然单次编辑耗时短，但整体实验的总GPU小时未给出，不利于复现估算。

（完）
