---
title: "Reasoning on a Spectrum: Aligning LLMs to System 1 and System 2 Thinking"
title_zh: 频谱上的推理：将大模型对齐到系统1与系统2思维
authors: "Alireza Salkhordeh Ziabari, Nona Ghazizadeh, Zhivar Sourati, Farzan Karimi Malekabadi, Payam Piray, Morteza Dehghani"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=FZURCro04D"
tags: ["query:ns-xai"]
score: 4.0
evidence: 将大模型对齐到系统1与系统2推理风格
tldr: 大模型通常仅依赖逐步推理，缺乏人类灵活切换推理风格的能力。本文构建包含两种推理风格的训练数据，显式对齐LLM至系统1与系统2，发现系统2擅长算术与符号推理，系统1在常识任务上更优，揭示了准确率-效率的权衡。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 345}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 648, \"height\": 332}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 324}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1433, \"height\": 362}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1452, \"height\": 392}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 375}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 491}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 502}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fzurcro04d/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 619}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 710}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 505}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 665}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 799}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 985, \"height\": 420}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 508}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fzurcro04d/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 916}]"
motivation: LLM缺乏人类灵活切换直觉与分析推理的能力。
method: 构建双风格训练数据并微调LLM，使其能按需输出系统1或系统2推理。
result: 系统2对齐模型在算术和符号推理上更准，系统1模型在常识任务上更快。
conclusion: 推理风格对齐为LLM提供了灵活的准确率-效率选择。
---

## Abstract
Large language models (LLMs) demonstrate remarkable reasoning capabilities, yet their reliance on step-by-step reasoning can make them brittle when tasks do not align with such structured approaches. In contrast, human cognition flexibly alternates between fast, intuitive reasoning (System 1) and slow, analytical reasoning (System 2), depending on context. To bridge this gap, we curate a dataset of 2K examples, each with valid responses from both reasoning styles, and explicitly align LLMs with System 1 and System 2 reasoning. Evaluations across diverse reasoning benchmarks reveal an accuracy-efficiency trade-off: System 2-aligned models excel in arithmetic and symbolic reasoning, while System 1-aligned models perform better in commonsense tasks. A mechanistic analysis of model responses shows that System 1 models employ more definitive answers, whereas System 2 models demonstrate greater uncertainty. Interpolating between these extremes produces a monotonic transition in reasoning accuracy, preserving coherence. This work challenges the assumption that step-by-step reasoning is always optimal and highlights the need for adapting reasoning strategies based on task demands.

---

## 论文详细总结（自动生成）

以下是基于论文内容的结构化中文总结：

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：当前大语言模型（LLMs）普遍采用逐步推理（如 Chain-of-Thought），但这种方式并非总是最优，在需要快速判断或隐含知识的常识任务中反而会“过度思考”，导致性能下降或效率低下。
- **背景**：人类认知灵活地在快速直觉（System 1）与慢速分析（System 2）之间切换，而 LLM 缺乏这种适应性。现有研究多假设逐步推理更优，忽略了不同任务需要不同推理风格这一关键事实。
- **研究目标**：通过显式将 LLM 对齐至 System 1（快速、启发式）与 System 2（慢速、分析式）两种推理风格，探究其在不同任务上的表现差异，揭示准确率-效率的权衡，并证明 LLM 的推理实际上是一个可调谐的连续频谱。

## 2. 方法论
### 2.1 核心思想
- 将 LLM 的推理风格对齐视为一个偏好优化问题：为每个问题构造一对有效的 System 1 回答（基于认知启发式）和 System 2 回答（基于理性分析），然后分别让模型偏好其中一种风格进行微调。

### 2.2 数据集构建（2K 样例）
- **生成**：基于 10 种经典认知启发式（如锚定效应、光环效应、过度自信等），由领域专家撰写种子样例（每个启发式一个），再通过 GPT-4o 以 one-shot 方式扩展出更多问题与双风格答案。
- **修正**：注意到 System 2 回答天然更长，为避免模型因长度偏好而作弊，使用 GPT-4o 零样本进行长度均衡，使两种回答的平均 token 数接近（System 1: 82.19, System 2: 83.93），并通过 TOST 检验确认等价。
- **验证**：领域专家人工核查所有数据，修改约 20% 的回答；进行了主题建模确保内容多样性。

### 2.3 对齐算法
- 使用两种离线偏好优化方法：**DPO**（Direct Preference Optimization）和 **SimPO**（Simple Preference Optimization，去除了参考模型）。
- **System 1 对齐**：偏好样本中 System 1 回答为胜者（winner），System 2 为败者（loser）；**System 2 对齐**则相反。

### 2.4 推理频谱插值
- 训练 7 个中间模型，其中 winner 回答按比例混合 System 1 与 System 2（如 30% S1 + 70% S2），以观察推理风格连续变化时的性能过渡。

## 3. 实验设计
### 3.1 数据集与 Benchmark
- **算术推理**：MultiArith、GSM8K、AddSub、AQuA、SingleEq、SVAMP（共 6 个）。
- **常识推理**：CSQA、StrategyQA、PIQA、SIQA、COM2SENSE（共 5 个）。
- **符号推理**：Last Letter Concatenation、Coin Flip（共 2 个）。

### 3.2 对比方法
- 基模型（Llama-3-8B-Instruct、Mistral-7B-Instruct-v0.1）的零样本、零样本 CoT 提示。
- 作者训练的 System 1 对齐模型、System 2 对齐模型（分别用 DPO 和 SimPO 实现）。
- 7 个插值中间模型（用于分析性能过渡）。

### 3.3 评估方式
- 两阶段评估：先让模型自由生成推理，再以特定格式提取最终答案，计算精确匹配准确率。

## 4. 资源与算力
- **GPU**：NVIDIA RTX A6000（48GB RAM）。
- **总耗时**：约 800 GPU 小时。
- **软件**：Python 3.10.12、PyTorch 2.4.0、Transformers 4.44.2、PEFT 0.12.0。
- **训练细节**：LoRA（rank=8, alpha=16, dropout=0.1），5 个 epoch，早停 patience=5。

## 5. 实验数量与充分性
- **主实验**：在 13 个 benchmark 上对比了 4 种基线与 4 种对齐模型（System 1/2 × DPO/SimPO），每个模型运行一次（未报告多次重复的误差棒）。
- **插值实验**：7 个不同的混合比例，覆盖全部 13 个 benchmark，验证了连续单调过渡。
- **辅助分析**：输出长度差异（t 检验）、Token 级不确定性（logits）、模糊词比例、决策承诺时机（LLM-as-Judge）。
- **消融/控制**：控制了回答长度对偏好的影响；两个模型（Llama 和 Mistral）相互验证。
- **评价**：实验覆盖足够多任务类型，统计检验（t 检验、McNemar、TOST）使用恰当，结论稳定。但主准确率指标未报告多次运行的标准差，可能略欠统计严谨性；未在更大规模模型（如 70B）上验证。

## 6. 主要结论与发现
- **非对称优势**：
  - System 2 模型在算术和符号推理上显著优于 System 1 和基线，尤其在 AddSub（+7.66）和 SingleEq（+3.77）。
  - System 1 模型在常识推理上全面优于 System 2，例如 CSQA (+1.39)、SIQA (+1.04)、COM2SENSE (+2.44)，也优于 CoT 基线。
- **效率-准确率权衡**：System 2 回答更长（第二阶段显著多 token），System 1 更简洁，符合直觉。
- **连续频谱**：从 System 1 到 System 2 的插值模型中，准确率呈平滑单调变化（r² > 0.9），无突变，说明 LLM 推理可被逐步导航。
- **不确定性与决策**：System 2 模型生成 token 的 logit 概率更低（更不确定），使用更多模糊词；System 1 模型在常识任务中更快做出确定回答（更早给出 definitive answer）。
- **系统-特定错误模式**：System 2 在算术任务中更擅长高精度计算（如更大概率处理小数）；System 1 在常识任务中避免过度解释，更符合典型人类判断。

## 7. 优点
- **认知科学基础**：基于成熟的双过程理论，用认知启发式系统性设计数据，保证了两种回应风格在本质上的区别。
- **数据质量控制**：长度均衡、专家审核、主题多样性验证，减少了混淆因素。
- **推理频谱分析**：设计插值实验，直观展示了从直觉到分析的连续变化，而非简单二分类，增强了结果的深度。
- **多维度分析**：不仅比较准确率，还分析长度、不确定性、决策时机，揭示了不同风格的机制差异。
- **框架简洁实用**：使用现成的偏好优化方法（DPO/SimPO），不依赖复杂架构，易于复现。

## 8. 不足与局限
- **数据规模与覆盖**：仅 2K 样例、10 种启发式，可能未覆盖所有推理场景。领域专家参与但数量有限，未必代表所有专家观点。
- **模型与对齐方法限制**：仅在 8B 级模型（Llama 和 Mistral）上实验，未验证更大模型或其他架构。仅使用 DPO 和 SimPO，未尝试 PPO、KTO 等。
- **评估指标**：准确率未报告多次运行的置信区间；不确定性分析仅用 token logit 和模糊词，缺乏更深的心理语言学或交互式评估。
- **应用泛化**：实验中任务定义明确、答案唯一；在更复杂、开放式的实际部署中（如对话、决策支持）的效果尚待验证。
- **潜在偏差**：System 1 模型可能过于自信导致错误，System 2 模型可能计算成本高且速度慢；未系统讨论公平性、安全或毒性风险。

（完）
