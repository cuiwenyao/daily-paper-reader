---
title: Interpreting Arithmetic Reasoning in Large Language Models using Game-Theoretic Interactions
title_zh: 使用博弈论交互解释大语言模型中的算术推理
authors: "Leilei Wen, Liwei Zheng, Hongda Li, Lijun Sun, Zhihua Wei, Wen Shen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tRvzEL64dY"
tags: ["query:ns-xai"]
score: 9.0
evidence: 通过博弈论交互解释LLM算术推理机制
tldr: 该论文提出用博弈论交互解释LLM的算术推理过程，将输出分数分解为输入词之间的交互。通过量化不同类型的交互，发现了LLM解决简单算术问题时的内部机制，包括操作数-算子交互和高阶交互。这为理解LLM推理提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1452, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1449, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-trvzel64dy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1192, \"height\": 975, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 596, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-trvzel64dy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1410, \"height\": 1437, \"label\": \"Table\"}]"
motivation: LLM在算术推理上表现优异，但其内部机制尚不明确。
method: 将LLM输出分数分解为词之间的博弈论交互，并量化交互类型。
result: 发现LLM通过编码操作数-算子交互和高阶交互来解决算术问题。
conclusion: 博弈论交互是一种有效的LLM可解释性工具，揭示了算术推理的神经机制。
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

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：大语言模型（LLM）在算术推理任务上表现优异，但其内部工作机制尚不明确。已有研究（如识别关键神经元、扰动输入等）缺乏数学上的忠实性保证。
- **核心问题**：如何忠实地解释LLM在算术推理中的内部推理逻辑？具体包括：LLM在前向传播中编码了哪些推理模式？不同能力水平的LLM在编码这些模式时有何差异？
- **整体含义**：本文首次将博弈论中的Harsanyi交互引入LLM可解释性领域，通过将模型输出分数分解为输入词之间的交互效应，构建了一个具有**数学保证**（universal matching property）的逻辑模型，从而忠实反映LLM的推理模式。研究揭示了LLM解决不同复杂度算术问题的内在机制，并解释了LoRA微调方法任务特定性的根本原因。

## 2. 论文提出的方法论：核心思想、关键技术细节
### 核心思想
- 利用博弈论中的**Harsanyi交互**（Interaction）将LLM的输出分数分解为所有子集S（输入词集合）的交互效应I_S。每个交互表示一个AND关系：当且仅当S中所有词都未被掩码时，该交互才被触发并对输出产生贡献。
- 构建一个逻辑模型φ(x)=∑_{S⊆N} I_S，该模型可以完美拟合LLM在所有2^n个掩码句子上的输出（定理1），从而保证解释的忠实性。

### 关键技术细节
1. **交互的数学定义**（式2）：
   \[
   I_S = \sum_{S' \subseteq S} (-1)^{|S|-|S'|} \cdot v(x_{S'})
   \]
   其中v(x_T)是LLM在掩码句子x_T上的标量输出（余弦相似度）。

2. **中间层交互量化**：
   - 使用**最后一层最后一个token的嵌入**计算余弦相似度作为标量输出v(l)(x_T)，反映该层特征对原始句子的保真度。
   - 对输入进行**移位操作**（减去所有词被掩码时的嵌入），确保空集输出为0。

3. **交互类型定义**（为算术推理定制）：
   - **operand interactions**：至少包含一个操作数，不包含算子
   - **operator interactions**：至少包含一个算子，不包含操作数
   - **operand-operator interactions**：同时包含操作数和算子
   - **background interactions**：仅包含背景词（如"what", "is"等）
   四种交互的并集覆盖所有2^n个交互。

4. **聚焦度指标**（focality）：
   - 对某类交互Ω_type的聚焦度：R(l)(Ω_type) = E_{S∈Ω_type}|I_S| / Z(l)，其中Z(l)是归一化项。
   - 对不同阶交互的聚焦度：κ(l)_m = E_{|S|=m}|I_S| / Z(l)。
   - 当R>1时表示LLM对该类交互有偏好。

### 流程概述
1. 对每个输入样本，生成所有2^n个掩码变体。
2. 获取LLM各层的嵌入，计算余弦相似度。
3. 根据公式计算所有交互I_S。
4. 按类型和阶数汇总，计算聚焦度指标。
5. 对比不同LLM、不同训练阶段的聚焦度变化。

## 3. 实验设计：数据集、场景与基准
### 数据集
- **单算子算术问题**（one-operator）：6个自然语言模板，涵盖加减乘除四种运算。例如“How much is n1 plus n2? Answer is”。每个模板随机采样操作数n1,n2∈{1,...,9}，每个模板生成20个样本。
- **双算子算术问题**（two-operator）：29个自然语言模板，对应所有可能的双运算符组合（如((A+B)*C), A-B*C等）。每个模板生成5个样本。
- 数据来源：遵循Karpas et al. (2022), Razeghi et al. (2022), Stolfo et al. (2023)的手工构造模板。

### 评估的LLM（7个）
- OPT-1.3B, GPT-J-6B, Llama-2-7B, Llemma-7B, MathCoder-L-7B, MathCoder-CL-7B, CodeLlama-13B
- 这些模型在单算子和双算子问题上的准确率差异显著（见表1），用于对比强弱能力。

### 微调实验
- 使用LoRA方法微调OPT-1.3B：
  - 单算子微调：从3.2%提升至83.6%
  - 双算子微调：从1.7%提升至69.7%
  - 先单算子再双算子微调（观察任务遗忘）

### 基准与对比
- 无直接对比方法（本文是首个使用博弈论交互解释LLM算术推理的工作），主要进行**跨模型对比**和**训练过程动态分析**。

## 4. 资源与算力
- **GPU型号**：NVIDIA GeForce RTX 4090 24GB（单卡）
- **计算时间**：
  - Llama-2-7B模型：单算子样本约30秒/个，双算子样本约60秒/个
  - 其他模型时间未明确，但整体计算量随模型规模和输入变量数量指数增长（2^n个掩码句子）。
- 未说明训练时长和总GPU小时数，但微调实验使用LoRA，训练epoch和batch size在附录H给出（单算子10 epochs batch 16，双算子20 epochs batch 32）。

## 5. 实验数量与充分性
### 实验组数
- **静态分析**（图3、4、9）：对7个LLM在单算子和双算子问题上的聚焦度R(l)和κ(l)进行全层对比，每个LLM平均多个模板。
- **动态训练分析**（图5、6、7、10、11）：三个微调场景（单算子、双算子、先单后双），每个场景取5个时间点，展示聚焦度变化。
- **附录额外结果**：图9展示不同模板下的κ(l)，图10-11补充其他模板的动态变化。
- **表1**：7个LLM在单/双算子上的准确率。

### 充分性评价
- **优点**：覆盖了多种架构（OPT、GPT-J、Llama系列）、多种规模（1.3B~13B）、不同领域（通用、数学专用、代码专用）的LLM，对比充分；训练过程动态分析展示了因果演变。
- **不足**：实验主要集中在简单算术（单算子/双算子，操作数1-9），未扩展到复杂数学应用题；仅使用OPT-1.3B进行微调实验，未在其他模型上验证结论泛化性；交互计算需要2^n次前向，限制了输入词数量（单算子约7-10个词，双算子约8-12个词），因此实验规模有限。

## 6. 论文的主要结论与发现
### Insight 1（单算子问题机制）
- LLM解决单算子算术问题的内在机制是**编码操作数-算子交互（operand-operator interactions）和高阶交互（high-order interactions）**。
- 强能力模型（如Llemma-7B、Llama-2-7B）在后层聚焦度R(operand-operator)和κ(高阶)显著上升（>1），而弱能力模型（OPT-1.3B、GPT-J-6B）则聚焦于背景交互和极低阶交互。

### Insight 2（双算子问题机制）
- LLM解决双算子算术问题时需编码**算子交互（operator interactions）和操作数交互（operand interactions）**。
- 训练过程中operator interactions的聚焦度始终较高，operand interactions的聚焦度在后层逐渐上升。

### Insight 3（LoRA任务特定性的解释）
- 当LLM从单算子任务微调到双算子任务时，其单算子能力下降（accuracy从83.6%降至25.4%）。
- 从交互视角看，**operand-operator交互和高阶交互的聚焦度显著下降**，这解释了LoRA任务特定性的内在机制——它改变了LLM编码的推理模式类型。

### 其他发现
- 弱能力模型在最后几层突然聚焦背景交互，表明其未能习得与算术相关的有用模式。
- 不同LLM对交互类型有固有偏好（如OPT-1.3B似乎倾向于背景交互）。

## 7. 优点
- **理论保证**：基于Harsanyi交互的universal matching property，保证解释对任意掩码句子的输出都精确匹配，避免了以往解释方法缺乏数学基础的缺陷。
- **新颖度量**：提出focality指标R和κ，能够量化LLM对特定交互类型和复杂度的偏好，为分析前向传播过程提供可操作工具。
- **多角度分析**：既进行跨模型横向对比，又进行训练过程纵向动态分析，还结合微调实验，增强了结论的稳健性。
- **应用价值**：揭示了LoRA任务特定性的微观机制，为理解模型微调的行为提供了新视角，可能指导更高效的任务迁移策略。
- **实验设计规范**：所有LLM使用相同模板和随机种子，设置do_sample=False确保确定性输出，避免随机性干扰。

## 8. 不足与局限
- **计算成本高**：交互计算需要2^n次前向传播，当输入变量（词）数量增加时计算量指数爆炸。虽然作者建议通过筛选信息词或短语聚合来缓解，但实验仍限于短输入（单算子/双算子问题的词数）。
- **问题复杂度有限**：仅研究了简单的单算子和双算子算术问题（操作数为个位数），未扩展到多步骤推理、带括号复杂表达式、混合运算长序列、应用题（如鸡兔同笼）等更现实的场景。结论的泛化性有待验证。
- **微调模型单一**：动态分析仅基于OPT-1.3B一个模型，未在其他架构（如Llama、GPT-J）上验证结论是否一致。LoRA的特定参数设置（rank=8, alpha=32）可能影响交互变化模式。
- **掩码策略依赖**：使用`<unk>`或`<|endoftext|>`等特殊token进行掩码，不同掩码策略可能影响交互值。论文未系统比较不同掩码策略的影响。
- **缺乏与人类推理的对比**：虽然解释了模型机制，但未与人类做算术推理时的认知过程（如先识别操作数和算子再执行计算）进行对比，难以判断模型是否学到了类似人类的推理模式。
- **未考虑输出生成过程**：分析仅基于logit/嵌入，未结合自回归生成的每一步（如解码阶段）来分析交互的动态变化。

（完）
