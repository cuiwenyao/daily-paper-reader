---
title: Self-Directed Decomposition Empowers Reasoning Potentials in Large Language Models
title_zh: 自主分解释放大语言模型的推理潜力
authors: "Chuan Tian, Yilei Zhang"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=e2hlcfECdu"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过自主分解增强大模型推理
tldr: 不相关
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 797, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1012, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1213, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1185, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e2hlcfecdu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1213, \"height\": 615, \"label\": \"Figure\"}]"
motivation: 不相关。
method: 不相关。
result: 不相关。
conclusion: 不相关。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable advancements in natural language processing and reasoning tasks, yet often struggle with logical coherence during problem-solving. This paper introduces Self-Directed Decomposition (SD), a novel prompting strategy enabling LLMs to autonomously decompose reasoning problems into manageable sub-tasks without human intervention, allowing models to determine their own approach with adaptive flexibility across diverse reasoning domains. Experiments across seven reasoning tasks reveal that this methodology particularly enhances performance on deductive, inductive, mathematical, commonsense, and scientific reasoning tasks, while showing more modest benefits for abductive and causal reasoning tasks, achieving 62.26\% overall median accuracy compared to 49.64\% and 46.43\% for zero-shot and zero-shot Chain-of-Thought (CoT) approaches, respectively. Error and statistical analysis demonstrates that SD significantly transforms reasoning patterns by reducing wrong selection errors but increasing process mistakes for simpler variants, with only SD1 maintaining optimal balance. We discover a counterintuitive negative correlation between token consumption and accuracy ($R^2 = 0.162, p = 0.004$), challenging conventional resource-performance assumptions. Abductive reasoning demonstrates critical vulnerability to decomposition strategies, showing significant perspective errors increase ($R^2 = 0.66$). These findings explain why SD1 outperforms other variants: it balances different error types effectively while avoiding the complexity-accuracy trade-off that affects simpler decomposition strategies.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLMs）在自然语言处理与推理任务中取得了显著进步，但面对复杂推理时仍存在逻辑连贯性不足的问题。现有提示策略（如零样本 Chain-of-Thought）虽然能引导模型逐步推理，却常导致语义误解或中间步骤跳跃，且依赖于预定义的示例或人工设计的算法，限制了模型的自主性。论文旨在通过**自主分解**的方式，让LLMs在没有人类干预的情况下，自行将复杂问题拆解为可处理的子任务，从而提升推理表现。

---

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：Self-Directed Decomposition (SD) 是一种新型提示策略，要求LLM在回答前主动对问题进行分解，形成子任务并依次解决。模型根据自身内部表征决定分解方式，无需外部模板或人工引导。
- **四种变体**（按指令复杂度递减）：
  - **SD1**：使用模态动词（“should”）和结构化术语（“sub-tasks”），提供完整分解指导。
  - **SD2**：缩短指令，保留核心分解要求。
  - **SD3**：添加礼貌语（“please”），类似情感刺激。
  - **SD4**：极简措辞（“Decompose and solve.”）。
- **技术细节**：无公式或算法流程，仅通过提示文字实现。模型接收到SD提示后，自动生成子任务步骤并推理答案。该方法强调**提示工程优于模型规模增大**（使用GPT-3.5-turbo而非更大模型）。

---

## 3. 实验设计：数据集、基准、对比方法

- **数据集覆盖七大推理领域，共13个数据集**：
  - 演绎推理：bAbI (task 15), EntailmentBank
  - 归纳推理：CLUTRR, bAbI (task 16)
  - 数学推理：Mathematics (Math), SVAMP
  - 科学推理：SciBench
  - 常识推理：CommonsenseQA, PiQA, Pep-3K
  - 溯因推理：αNLI, ART
  - 因果推理：E-care, Balanced-COPA
- **基准方法**：
  - Zero-shot（无提示）
  - Zero-shot Chain-of-Thought（“Let’s think step by step”）
  - 情感刺激 EP02（“This is very important to my career”）
- **评估指标**：准确率（中位数）、错误分类（五种错误：WS、HA、NR、PPM、PM）、统计显著性（R²、p值、ANOVA）。

---

## 4. 资源与算力

论文未明确说明使用的 GPU 型号、数量或训练时长。实验基于 **GPT-3.5-turbo** 的 API 调用，所有推理均在线完成，温度参数设为 0。未提及具体的计算资源消耗（如总API调用次数、成本等）。

---

## 5. 实验数量与充分性

- **样本量**：每个数据集随机抽取 **10 个任务**（SciBench 为 40 个），每个提示策略仅测试一次。样本量较小，可能影响统计稳定性。
- **实验组数**：共 7 个推理领域 × 13 个数据集 × 7 种提示方法（4个SD + 3个baseline）≈ 91 组测试。
- **充分性评估**：
  - **优点**：覆盖领域广泛，错误分析细粒度（五种错误类型），统计检验（p值、R²）严格。
  - **不足**：每个数据集样本量过少（10个），且仅使用单一模型（GPT-3.5-turbo），缺乏跨模型验证；未进行多次运行以估计方差；未包含消融实验（如仅改变分解指令长度而不改变其他因素）。
  - **公平性**：比较方法直接，但缺少与更先进提示方法（如 Tree-of-Thought）的对比。

---

## 6. 论文的主要结论与发现

1. **SD1 性能最优**：中位数准确率 62.26%，显著高于零样本（49.64%）和零样本 CoT（46.43%），且误差范围最窄（IQR 50%-70%）。
2. **Token 消耗与准确率负相关**（R²=0.162, p=0.004）：更多计算资源（更多token）反而导致更低准确率，挑战了“更详细处理→更好结果”的传统假设。
3. **错误类型转换**：分解策略系统性减少“错误选择”（WS）错误，但增加“过程错误”（PM）。SD1 能保持最佳平衡（低WS、低PM），而 SD2-SD4 则因PM过度上升而性能下降。
4. **溯因推理对分解高度敏感**：视角错误（PPM）在溯因推理中急剧增加（R²=0.66），说明分解可能破坏其固有的并行假设评估结构。
5. **领域特异性**：演绎、归纳、数学、科学、常识推理从SD中受益显著，而溯因和因果推理改善有限或出现恶化。

---

## 7. 优点：方法或实验设计上的亮点

- **创新性**：提出“自主分解”概念，无需人工示例或预定义步骤，强调模型自主性。
- **系统性错误分析**：采用五类错误分类（WS、HA、NR、PPM、PM），深入揭示分解对推理模式的影响。
- **反直觉发现**：token-准确率负相关为提示工程提供了新视角，指出“更多步骤”可能有害。
- **跨领域覆盖**：涵盖七种推理类型，为不同任务提供差异化的性能画像。
- **统计严谨性**：报告了R²、p值、回归系数等指标，支持结论的可靠性。

---

## 8. 不足与局限

- **样本量小**：每个数据集仅10个样本（SciBench 40个），结果可能受随机波动影响，缺乏多次重复验证。
- **单模型限制**：仅使用 GPT-3.5-turbo，结论能否推广到其他LLM（如GPT-4、Llama系列）未知。
- **代码与数据未公开**：无法复现实验，降低了可验证性。
- **计算资源未报告**：缺少API调用量、时间成本等细节，不利于实际应用评估。
- **对比方法有限**：未与 Tree-of-Thought、Self-Consistency、Least-to-Most 等更高级提示方法比较。
- **性能上限低**：在科学推理中最高仅37.5%准确率，说明分解无法克服模型知识不足。
- **未讨论实际应用风险**：未涉及公平性、安全性、错误用例等社会影响。
- **分解指令设计差异混杂**：SD1-SD4 同时改变了长度、措辞、礼貌性，无法孤立归因于“分解粒度”。

（完）
