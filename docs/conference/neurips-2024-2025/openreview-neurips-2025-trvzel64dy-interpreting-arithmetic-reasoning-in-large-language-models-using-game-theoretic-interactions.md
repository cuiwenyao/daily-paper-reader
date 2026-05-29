---
title: Interpreting Arithmetic Reasoning in Large Language Models using Game-Theoretic Interactions
title_zh: 使用博弈论交互解释大语言模型的算术推理
authors: "Leilei Wen, Liwei Zheng, Hongda Li, Lijun Sun, Zhihua Wei, Wen Shen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tRvzEL64dY"
tags: ["query:ns-xai"]
score: 7.0
evidence: 博弈论解释LLM算术推理
tldr: 大语言模型的算术推理内部机制不明确。本文使用博弈论交互将输出分解为输入词之间的交互效应，量化不同类型交互。发现简单算术问题中LLM通过编码操作数-运算符交互进行推理。为解释大型模型推理机制提供新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 390}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 709}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 234}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 237}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 444}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 267}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 448}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1452, \"height\": 268}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 237}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1449, \"height\": 449}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 455}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1192, \"height\": 975}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 596, \"height\": 352}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 600}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1410, \"height\": 1437}]"
motivation: LLM如何解决算术问题的内在机制尚不清晰，需可解释分析。
method: 将输出分解为博弈论交互效应，量化各词交互贡献以探究推理机制。
result: 发现LLM通过编码操作数-运算符交互求解简单算术，高阶交互用于复杂问题。
conclusion: 博弈论方法有效揭示LLM推理的内部交互模式。
---

## Abstract
In recent years, large language models (LLMs) have made significant advancements in arithmetic reasoning. 
However, the internal mechanism of how LLMs solve arithmetic problems remains unclear.
In this paper, we propose explaining arithmetic reasoning in LLMs using game-theoretic interactions.
Specifically, we disentangle the output score of the LLM into numerous interactions between the input words.
We quantify different types of interactions encoded by LLMs during forward propagation to explore the internal mechanism of LLMs for solving arithmetic problems.
We find that (1) the internal mechanism of LLMs for solving simple one-operator arithmetic problems is their capability to encode operand-operator interactions and high-order interactions from input samples.
Additionally, we find that LLMs with weak one-operator arithmetic capabilities focus more on background interactions.
(2) The internal mechanism of LLMs for solving relatively complex two-operator arithmetic problems is their capability to encode operator interactions and operand interactions from input samples.
(3) We explain the task-specific nature of the LoRA method from the perspective of interactions.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在算术推理任务上表现显著提升，但其内部推理机制（如何利用输入词之间的交互关系得出答案）仍不明确。
- **研究动机**：现有机制解释方法（如神经元定位、因果中介分析）缺乏数学上的忠实性保证，且无法从整体上刻画 LLM 编码的推理模式。
- **整体含义**：本文提出利用博弈论中的 **Harsanyi 交互**（interaction）将 LLM 的输出分解为输入词之间的线性可加交互效应，从而构建一个忠实于原模型输出行为的逻辑模型 $\phi(x)$，并基于此解释 LLM 解决算术问题的内在机制。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将 LLM 对任意输入句子 $x$ 的输出分数 $v(x)$ 分解为所有子集 $S \subseteq N$ 的交互效应 $I_S$ 之和，即 $v(x) = \phi(x) = \sum_{S \subseteq N} I_S$，其中 $N$ 是输入词集合。每个 $I_S$ 代表 $S$ 中所有词共同存在的 AND 关系的贡献。
- **关键技术细节**：
  - 使用 **余弦相似度** 定义中间层输出分数 $v^{(l)}(x_T) = \cos(f^{(l)}(x_T), f^{(l)}(x_N))$，其中 $f^{(l)}$ 是最后一个输入 token 在第 $l$ 层的嵌入。
  - 通过 **Shapley 值公式** 计算 $I_S$：
    $$I_S = \sum_{S' \subseteq S} (-1)^{|S|-|S'|} v(x_{S'})$$
    此公式保证对任意掩码输入 $x_T$，$v(x_T) = \phi(x_T)$，即 **通用匹配性质**，确保交互的忠实性。
  - 将输入词分为三类：操作数（operand）、运算符（operator）、背景词（background），由此定义四种交互类型：操作数交互、运算符交互、操作数-运算符交互、背景交互。
  - 提出 **聚焦度（Focality）** 指标 $R^{(l)}(\Omega_{\text{type}}) = \frac{\mathbb{E}_{S \in \Omega_{\text{type}}}|I_S^{(l)}|}{Z^{(l)}}$，衡量 LLM 在层 $l$ 对某类交互的偏好程度（$>1$ 表示偏好）。
  - 提出 **阶数聚焦度** $\kappa_m^{(l)} = \frac{\mathbb{E}_{|S|=m}|I_S^{(l)}|}{Z^{(l)}}$，衡量 LLM 对 $m$ 阶交互（包含 $m$ 个词）的偏好。

## 3. 实验设计

- **数据集**：手工构造的算术问题模板。一元运算符查询 6 个模板（含 +, -, ×, ÷），每个模板随机采样操作数 $n_1, n_2 \in \{1,2,\dots,9\}$ 生成 20 个 prompt；二元运算符查询 29 个模板（不同运算组合），每个模板生成 5 个 prompt。训练数据：一元 3500 样本（每模板 500），二元 29000 样本（每模板 1000），操作数最大 100，结果不超过 1000。
- **Benchmark**：各模型在一元与二元测试集上的准确率（见 Table 1）。
- **对比模型**：OPT-1.3B、GPT-J-6B、Llama-2-7B、Llemma-7B、MathCoder-L-7B、MathCoder-CL-7B、CodeLlama-13B。以及使用 LoRA 微调的 OPT-1.3B 变体（OPT-1.3B-One 等）。
- **方法对比**：本文未与其他解释性方法（如因果中介、神经元分析）直接对比输出解释效果，而是提出一种新的、有理论保证的交互分析框架，并通过大量可视化与定量分析验证其揭示的规律。

## 4. 资源与算力

- **实验硬件**：NVIDIA GeForce RTX 4090 24GB GPU。
- **计算耗时**：对于 Llama-2-7B，一元样本约 30 秒/样本，二元样本约 60 秒/样本。其他模型类似。
- **训练耗时**：一元微调 10 epoch，batch size 16；二元微调 20 epoch，batch size 32。使用 LoRA（rank=8, alpha=32, dropout=0.05），学习率 8e-4。
- **说明**：论文明确提供了硬件和大致时间，但未给出总 GPU 时数。整体计算量较大但对单卡可行。

## 5. 实验数量与充分性

- **实验组数**：
  - 7 个预训练 LLM 的全层聚焦度分析（图 3、图 4），结果平均于所有一元算术查询。
  - 3 种微调场景的动力学分析（图 5、6、7），分别展示不同训练时期交互类型和阶数的变化。
  - 另外在附录中补充了不同模板的结果（图 9、10、11）。
- **充分性**：实验覆盖了多种规模与架构的 LLM（从 1.3B 到 13B），以及强弱算术能力的模型对比；微调实验展示了学习过程中的动态变化，验证了三大洞察。实验设计较为全面。
- **客观性与公平性**：所有模型使用相同的数据和模板，避免 tokenizer 差异（按词而非 token 处理变量）。但未报告误差棒，因为设置了 do_sample=False 使输出确定性（作者在 checklist 中说明）。交互计算基于理论保证的公式，因此结果忠实。

## 6. 论文的主要结论与发现

- **洞察 1**：一元算术推理中，LLM 的内部机制编码了 **操作数-运算符交互** 和 **高阶交互**；能力强模型在后层增强对这些聚焦，弱模型则偏向背景交互和极低阶交互。
- **洞察 2**：二元算术推理中，LLM 内部机制编码 **运算符交互** 和 **操作数交互**；训练中运算符交互始终保持高聚焦，操作数交互在后训练阶段逐渐增强。
- **洞察 3**：LoRA 的任务特异性可以通过交互视角解释：当将已有强大一元能力的模型微调到二元任务时，其对一元任务至关重要的操作数-运算符交互和高阶交互聚焦度下降，导致一元准确率下降。

## 7. 优点

- **理论忠实性**：基于 Harsanyi 交互的分解满足通用匹配性质，任意掩码输入下 LLM 输出均等于交互之和，保证解释的数学严谨性。
- **新颖分类**：将交互按词角色分类（操作数、运算符、背景），简洁有效地刻画算术推理的核心模式。
- **可解释性强**：通过聚焦度指标直观展示了 LLM 在传播过程中的偏好变化，并揭示学习动态。
- **方法通用性**：该方法可扩展应用于其他需要理解 LLM 内部推理的任务。

## 8. 不足与局限

- **计算成本高**：随着输入词数增加，交互数量指数增长，难以直接用于长句或复杂问题。论文在附录 L 中提出了可能的缓解方案（如选择性变量分析、短语聚合、近似方法）。
- **问题复杂度有限**：仅研究了简单的 1-2 元算术算式，未涉及多步数学应用题或需要外部知识的问题；论文在结论中承认这一局限并计划未来研究。
- **未与其他解释方法对比**：论文未做实验比较交互解释与现有可解释性方法（如注意力、因果中介）在解释正确性或有用性上的差异。
- **缺乏统计误差**：由于使用确定性解码，未提供误差棒或置信区间，虽然对交互计算不产生统计波动，但削弱了实验结果的稳健性展示。
- **微调仅限于 LoRA 和单一模型**：结论主要基于 OPT-1.3B 的微调实验，其他架构的泛化性尚未验证。

（完）
