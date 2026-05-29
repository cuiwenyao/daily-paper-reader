---
title: Self-Directed Decomposition Empowers Reasoning Potentials in Large Language Models
title_zh: 自导向分解激发大语言模型的推理潜能
authors: "Chuan Tian, Yilei Zhang"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=e2hlcfECdu"
tags: ["query:ns-xai"]
score: 6.0
evidence: 提示策略提升LLM推理能力
tldr: LLM在解决推理问题时逻辑连贯性不足。本文提出自导向分解（SD）提示策略，使模型自主将问题分解为子任务，无需人类介入。在七项推理任务上，SD显著提升演绎、归纳、数学等推理，但对溯因和因果推理改进有限。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 797, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1012, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1213, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1185, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1213, \"height\": 615, \"label\": \"Figure\"}]"
motivation: LLM在复杂推理中常缺乏逻辑连贯性。
method: 提出自导向分解（SD）提示策略，让LLM自主分解问题为子任务。
result: SD在多项推理任务上提升性能，尤其在演绎和数学推理上效果显著。
conclusion: 自导向分解是一种有效的推理增强策略。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable advancements in natural language processing and reasoning tasks, yet often struggle with logical coherence during problem-solving. This paper introduces Self-Directed Decomposition (SD), a novel prompting strategy enabling LLMs to autonomously decompose reasoning problems into manageable sub-tasks without human intervention, allowing models to determine their own approach with adaptive flexibility across diverse reasoning domains. Experiments across seven reasoning tasks reveal that this methodology particularly enhances performance on deductive, inductive, mathematical, commonsense, and scientific reasoning tasks, while showing more modest benefits for abductive and causal reasoning tasks, achieving 62.26\% overall median accuracy compared to 49.64\% and 46.43\% for zero-shot and zero-shot Chain-of-Thought (CoT) approaches, respectively. Error and statistical analysis demonstrates that SD significantly transforms reasoning patterns by reducing wrong selection errors but increasing process mistakes for simpler variants, with only SD1 maintaining optimal balance. We discover a counterintuitive negative correlation between token consumption and accuracy ($R^2 = 0.162, p = 0.004$), challenging conventional resource-performance assumptions. Abductive reasoning demonstrates critical vulnerability to decomposition strategies, showing significant perspective errors increase ($R^2 = 0.66$). These findings explain why SD1 outperforms other variants: it balances different error types effectively while avoiding the complexity-accuracy trade-off that affects simpler decomposition strategies.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLMs）在自然语言处理和推理任务中取得了显著进步，但在解决复杂问题时仍存在逻辑连贯性不足的问题。现有提示策略（如零样本思维链CoT）虽然能引导模型逐步推理，但可能产生语义误解或跳过中间步骤，且缺乏自主性。
- **核心问题**：如何让LLMs在不依赖人类干预或预定义范例的条件下，自主地将复杂问题分解为可管理的子任务，从而提升推理性能。
- **研究意义**：探索通过改进提示策略（而非增加模型参数）来激发LLMs的推理潜能，为高效、灵活的推理增强提供新思路。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出**自导向分解（Self-Directed Decomposition, SD）** 提示策略，让LLM自行将推理问题分解为子任务，并自主选择分析路径，无需人类给出分解步骤或范例。
- **关键技术细节**：设计了四个SD变体（SD1～SD4），逐步简化指令结构：
  - SD1：使用情态动词（"should"）和结构化术语（"sub-tasks"），提供全面分解指导，如“When you deal with such problems, you should do a problem decomposition like sub-tasks to analyse the problem.”
  - SD2：缩短指令，保留核心分解要求：“When you deal with a problem, decompose the problem and solve the task.”
  - SD3：添加礼貌标记“please”：“Please decompose the problem and solve it.”
  - SD4：极简措辞：“Decompose and solve.”
- **算法/流程**：模型收到SD提示后，自主识别问题结构，将其拆分为多个子步骤，依次解答并综合答案。整个过程无外部干预。

### 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：覆盖7类推理任务，共15个数据集：
  - 演绎推理：bAbI (task 15), EntailmentBank
  - 归纳推理：CLUTRR, bAbI (task 16)
  - 数学推理：Mathematics, SVAMP
  - 科学推理：Scibench
  - 常识推理：CommonsenseQA, PiQA, Pep-3K
  - 溯因推理：αNLI, ART
  - 因果推理：E-care, Balanced-COPA
- **基准测试方法**：
  - 零样本（Zero-shot）
  - 零样本思维链（Zero-shot CoT）
  - 情绪刺激EP02（“This is very important to my career”）
  - SD1～SD4共4种变体
- **实验设置**：使用GPT-3.5-turbo（不选更大模型以突出提示策略效果），temperature=0，每个策略在每个数据集上独立调用API，避免信息污染。每个数据集随机抽取10个任务（Scibench抽取40个），每个任务只测试一次。

### 4. 资源与算力

- 论文未明确说明具体的GPU型号、数量、训练时长等算力信息。仅提到使用GPT-3.5-turbo模型通过API调用，temperature=0。由于是商用API调用，未披露后端算力细节。
- **注**：文中未提及训练（因仅进行推理），也未提供计算资源消耗的量化数据。

### 5. 实验数量与充分性

- **实验数量**：在7类推理任务共15个数据集上，对比了7种方法（零样本、零样本CoT、EP02、SD1～SD4），每个方法在每个数据集上运行一次，共约 **15个数据集 × 7种方法 = 105组实验**（但每个数据集样本数不同，总测试样本数：10×14 + 40 = 180个任务？但未明确总数，更可能每数据集10个，Scibench 40个，合计 (14×10+40)=180个样本）。此外，进行了详细的误差分类和统计分析。
- **充分性**：
  - **优点**：覆盖领域广（演绎、归纳、数学、科学、常识、溯因、因果），误差分析细致（5类错误：错误选择、幻觉、无推理、视角错误、过程错误），统计检验严谨（R²、p值、ANOVA等）。
  - **不足**：
    - 每个数据集样本量较小（通常10个，Scibench 40个），可能不足以代表整体分布，存在随机偏差风险。
    - 仅使用GPT-3.5-turbo一个模型，未在多个LLM（如GPT-4、LLaMA等）上验证泛化性。
    - 未进行多次试验取平均，单次运行结果可能受随机性影响（尽管temperature=0）。
    - 消融实验：仅有SD1～SD4的指令简化，未对分解步骤数量、分解方式（如是否强制、是否提供示例）等进行系统消融。
  - **公平性**：所有策略在同一模型、相同数据集上比较，控制变量较好。

### 6. 论文的主要结论与发现

- **SD1性能最佳**：整体中位数准确率62.26%，显著优于零样本（49.64%）和零样本CoT（46.43%），且误差区间更窄（IQR 50%-70%），兼具高性能与稳定性。
- **Token消耗与准确率负相关**：发现反直觉结果——更多token反而导致更低准确率（R²=0.162, p=0.004），即增加计算资源不一定提升推理效果。
- **误差类型转换**：分解策略系统性地减少了“错误选择”(WS)错误，但增加了“过程错误”(PM)，SD1能保持最佳平衡，而SD2-SD4则过度增加了PM错误。
- **溯因推理的脆弱性**：溯因推理在分解策略下“视角错误”(PPM)显著增加（R²=0.66），说明分解可能破坏了该类任务所需的并行假设维护结构。
- **各推理类型影响不均**：演绎、归纳、数学、常识、科学推理提升明显；溯因和因果推理提升有限甚至下降。

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：提出一种无需人类干预的自主分解提示策略，强调模型自主性，区别于需要预设范例或外部算法的CoT变体。
- **实验覆盖全面**：涵盖7类推理任务，误差分类详尽（5类），为理解分解推理的机制提供了深入视角。
- **统计严谨**：使用R²、p值、回归分析、方差分析等多种统计工具，对结果进行量化验证。
- **发现反直觉规律**：揭示token消耗与性能的负相关，对传统“更多计算=更好性能”的假设提出挑战。
- **领域特异性分析**：指出溯因推理的特殊脆弱性，为后续设计领域自适应提示策略提供依据。

### 8. 不足与局限

- **样本量小**：每个数据集仅10个任务（Scibench 40个），可能无法充分反映任务难度分布，统计稳定性有限。
- **模型单一**：仅使用GPT-3.5-turbo，未在更强模型（如GPT-4、Claude）或其他开源模型上测试，结论泛化性存疑。
- **缺乏多次运行**：temperature=0虽然确定性，但未进行多次重复实验以评估稳定性；单次运行的结果可能存在偶然性。
- **消融实验不足**：仅对指令措辞简化（SD1～SD4）进行了消融，未深入研究分解粒度、分解顺序、是否强制分解等关键参数的影响。
- **应用限制**：在复杂科学推理中最高准确率仅37.5%，说明SD策略仍受底层模型知识限制；且对某些任务（如溯因）可能产生反效果。
- **未提供开源代码/数据**：论文未公开实现代码和样本集，影响可复现性。
- **计算资源信息缺失**：未报告API调用次数、总token数、费用等，不利于评估方法的经济性。

（完）
