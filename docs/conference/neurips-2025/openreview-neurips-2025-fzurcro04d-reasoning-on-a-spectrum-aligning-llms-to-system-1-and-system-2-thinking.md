---
title: "Reasoning on a Spectrum: Aligning LLMs to System 1 and System 2 Thinking"
title_zh: 光谱推理：使大语言模型对齐系统1和系统2思维
authors: "Alireza Salkhordeh Ziabari, Nona Ghazizadeh, Zhivar Sourati, Farzan Karimi Malekabadi, Payam Piray, Morteza Dehghani"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=FZURCro04D"
tags: ["query:ns-xai"]
score: 7.0
evidence: 使大模型对齐系统1和系统2思维，包含符号推理
tldr: 大语言模型过度依赖逐步推理，难以灵活适应任务。本文构建包含两种推理风格的数据集，通过对齐训练使模型能根据上下文切换推理模式。实验显示系统2对齐模型在算术和符号推理上表现优异，为研究大模型推理行为提供了新视角。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 648, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1433, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1452, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 619, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 505, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 665, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 799, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 985, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 508, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 916, \"label\": \"Table\"}]"
motivation: 大模型过度依赖固定推理模式，缺乏类似人类灵活切换推理风格的能力。
method: 构建包含系统1和系统2响应风格的数据集，通过显式对齐训练实现推理模式切换。
result: 系统2对齐模型在算术和符号推理上取得更好性能，系统1对齐模型在常识任务上更优。
conclusion: 对齐不同推理风格能提升大模型在多样化任务上的适应性和性能。
---

## Abstract
Large language models (LLMs) demonstrate remarkable reasoning capabilities, yet their reliance on step-by-step reasoning can make them brittle when tasks do not align with such structured approaches. In contrast, human cognition flexibly alternates between fast, intuitive reasoning (System 1) and slow, analytical reasoning (System 2), depending on context. To bridge this gap, we curate a dataset of 2K examples, each with valid responses from both reasoning styles, and explicitly align LLMs with System 1 and System 2 reasoning. Evaluations across diverse reasoning benchmarks reveal an accuracy-efficiency trade-off: System 2-aligned models excel in arithmetic and symbolic reasoning, while System 1-aligned models perform better in commonsense tasks. A mechanistic analysis of model responses shows that System 1 models employ more definitive answers, whereas System 2 models demonstrate greater uncertainty. Interpolating between these extremes produces a monotonic transition in reasoning accuracy, preserving coherence. This work challenges the assumption that step-by-step reasoning is always optimal and highlights the need for adapting reasoning strategies based on task demands.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

当前大语言模型（LLM）在推理能力上取得了显著进步，尤其依赖Chain-of-Thought（CoT）等逐步、结构化推理技术。然而，这种单一模式存在局限：在不需要深度推理的简单任务中，模型会“过度思考”，导致效率低下甚至错误（如生成不必要的解释）。相比之下，人类认知能够根据任务需求灵活地在快速、直觉性的系统1思维和慢速、分析性的系统2思维之间切换。论文的核心动机是：**LLM是否也能像人类一样，具备按需切换推理风格的能力？** 研究目标是通过显式对齐训练，使LLM分别具备系统1和系统2的推理风格，并系统评估不同风格的利弊，挑战“逐步推理总是最优”的假设。

## 2. 论文提出的方法论

### 核心思想
构建一个包含两种推理风格（系统1和系统2）答案的数据集，通过偏好优化方法（DPO和SimPO）将LLM对齐到特定推理风格。系统1答案基于认知捷径（启发式），快速、直接；系统2答案基于逐步分析，谨慎、全面。

### 关键技术细节
1. **数据集构建（2,000条）**：
   - **生成**：基于10种经典认知启发式（如锚定效应、光环效应等），由领域专家提供种子示例（每个启发式一个），再用GPT-4o进行单样本扩展，生成每个问题对应的系统1和系统2答案。
   - **精炼**：为消除长度偏差（系统2答案初始更长），使用GPT-4o零样本提示将系统1和系统2答案长度对齐（平均约82-84 tokens），并通过TOST检验证实长度等价。
   - **验证**：领域专家人工审核并修正约20%的响应，确保符合定义；通过主题建模验证话题多样性。

2. **对齐训练**：
   - 使用两种离线偏好优化方法：**DPO**（Direct Preference Optimization）和**SimPO**（Simple Preference Optimization）。以基础指令微调模型（Llama-3-8B-Instruct和Mistral-7B-Instruct-v0.1）为起点。
   - 对每个问题，将系统1答案设为偏好（winner）、系统2答案设为非偏好（loser）训练得到系统1模型；反之得到系统2模型。
   - 为研究推理风格的光谱特性，还训练了7个中间模型，在偏好数据中按不同比例混合系统1和系统2答案。

3. **推理光谱分析**：通过线性插值方式训练模型，考察性能的单调变化趋势。

## 3. 实验设计

- **数据集/场景**：
  - 算术推理：MultiArith、GSM8K、AddSub、AQuA、SingleEq、SVAMP。
  - 常识推理：CSQA、StrategyQA、PIQA、SIQA、COM2SENSE。
  - 符号推理：Last Letter Concatenation、Coin Flip。
  - 共13个基准。

- **对比方法**：
  - 基础指令微调模型（无CoT）。
  - 零样本CoT提示（在基础模型上添加“Let's think step by step”）。
  - 对齐后的系统1和系统2模型（DPO和SimPO两种变体）。

- **评估协议**：两阶段流程：先让模型给出推理过程，再提取格式化答案。使用精确匹配准确率（Exact Match Accuracy）。

## 4. 资源与算力

论文明确提到：实验使用**NVIDIA RTX A6000 GPU（48GB RAM）**，总计约**800 GPU小时**。训练基于LoRA（rank=8, alpha=16, dropout=0.1），每个模型训练5个epoch，使用准确率早停策略。

## 5. 实验数量与充分性

- 覆盖13个基准，3个推理类别。
- 使用两种基础模型（Llama和Mistral），两种对齐方法（DPO和SimPO），每组对照重复。
- 额外进行7个中间模型的插值实验（共9个模型点）。
- 进行了输出长度分析（两阶段）、不确定性分析（token级log概率、模糊词比例、早期决定性答案比例等），并在附录中给出统计检验（t检验、McNemar检验等）。
- 总体实验数量充足，统计严谨，对比公平（基础模型、CoT基线均考虑）。不过，仅测试了8B和7B两个型号，限制了泛化性结论。

## 6. 论文的主要结论与发现

1. **系统2模型在结构推理上更优**：在算术和符号推理基准中，系统2对齐模型准确率显著高于基础模型和系统1模型（如AddSub提升约7.4个百分点）。系统2的逐步计算有效避免了启发式错误（如四舍五入错误）。
2. **系统1模型在常识推理上更优**：在所有五个常识基准中，系统1模型超过系统2模型，且有时超过基础模型和CoT基线。系统2的过度分析导致选择非典型答案（如建议“鼓励安静”而非“讲故事”）。
3. **推理光谱的单调性**：从系统1到系统2的插值准确率呈现单调递增（算术/符号）或递减（常识）趋势，无突变，说明推理风格是连续可调的。
4. **系统2输出更长**：尽管训练数据长度对齐，系统2模型在最终回答阶段仍生成明显更长的响应（DPO下p<0.001），表明其倾向于更详细的输出。
5. **不确定性差异**：系统2模型的token级概率更低（更不确定），使用更多模糊词（如“也许”），更少给出早期决定性答案。系统1模型在常识任务中更早给出确定答案。
6. **效率-准确性权衡**：系统1更快（token数更少），系统2更准确但更慢。不同任务适合不同风格。

## 7. 优点

- **方法创新**：首次系统地通过偏好对齐使LLM获得可区分的推理风格，而非依赖提示工程。
- **数据集高质量**：基于认知心理学理论，由领域专家设计种子示例，覆盖10种启发式，并严格平衡长度偏差。
- **分析深入**：不仅报告准确率，还从输出长度、不确定性、回答决定性等多角度分析模型行为，提供机制性理解。
- **光谱实验设计**：通过插值训练揭示推理风格的连续性，支持任务自适应推理的可行性。
- **统计严谨**：各关键结果均附有统计显著性检验。

## 8. 不足与局限

- **数据集规模较小**：仅2,000条，覆盖10种启发式，未能涵盖全部推理挑战。论文承认需要更大规模扩展。
- **模型范围有限**：仅测试Llama-3-8B和Mistral-7B两个模型和两种对齐方法（DPO/SimPO），未在更大模型或更多对齐方法（如RLHF）上验证。
- **不确定性度量局限**：仅使用token级log概率和词汇级分析，未深入进行心理语言学或交互式评估。
- **缺乏动态切换模型**：论文只训练了静态对齐模型，未实现任务自适应的动态推理风格切换，仅提出未来方向。
- **可解释性有限**：虽然分析了行为差异，但未从模型内部机制（如注意力头）解释为何不同风格性能不同。
- **计算开销**：虽然效率优于在线方法，但训练多个中间模型（9个）仍需要大量计算资源（800 GPU小时）。

（完）
