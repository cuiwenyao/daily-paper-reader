---
title: "SCOUT: Teaching Pre-trained Language Models to Enhance Reasoning via Flow Chain-of-Thought"
title_zh: SCOUT：通过流链式推理增强预训练语言模型的推理能力
authors: "Guanghao Li, Wenhao Jiang, Mingfeng Chen, Yan Li, Hao Yu, Shuting Dong, Tao Ren, Ming Tang, Chun Yuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eXckZbaYma"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过流链式推理实现大模型递归推理范式
tldr: 链式推理依赖显式中间步骤，限制扩展性和泛化性。SCOUT提出流链式推理（Flow CoT），将递归推理建模为潜在认知状态的渐进轨迹，无需显式CoT监督，在多个推理任务上提升性能且更具可扩展性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1303, \"height\": 809}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1345, \"height\": 348}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 495, \"height\": 413}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 653, \"height\": 572}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 742, \"height\": 519}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 865}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1001, \"height\": 217}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 279}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1365, \"height\": 132}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 805}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1031, \"height\": 725}]"
motivation: 现有链式推理方法依赖显式步骤且泛化性有限。
method: 提出流链式推理，将递归推理建模为潜在认知状态轨迹。
result: 在算术、常识等推理任务上超越传统CoT方法。
conclusion: 流链式推理为LLM推理提供了一种可扩展且无需显式监督的新范式。
---

## Abstract
Chain-of-Thought (CoT) prompting improves the reasoning performance of large language models (LLMs) by encouraging step-by-step thinking. However, CoT-based methods depend on  intermediate reasoning steps, which limits scalability and generalization. Recent work explores recursive reasoning, where LLMs reuse internal layers across iterations to refine latent representations without explicit CoT supervision. While promising, these approaches often require costly pretraining and lack a principled framework for how reasoning should evolve across iterations.
We address this gap by introducing **Flow Chain-of-Thought (Flow CoT)**, a reasoning paradigm that models recursive inference as a progressive trajectory of latent cognitive states. Flow CoT frames each iteration as a distinct cognitive stage—deepening reasoning across iterations without relying on manual supervision. To realize  this, we propose **SCOUT** (*Stepwise Cognitive Optimization Using Teachers*), a lightweight fine-tuning framework that enables Flow CoT-style reasoning without the need for pretraining. SCOUT uses progressive distillation to align each iteration with a teacher of appropriate capacity, and a cross-attention-based retrospective module that integrates outputs from previous iterations while preserving the model’s original computation flow.
Experiments across eight reasoning benchmarks show that SCOUT consistently improves both accuracy and explanation quality, achieving up to 1.8\% gains under fine-tuning. Qualitative analyses further reveal that SCOUT enables progressively deeper reasoning across iterations—refining both belief formation and explanation granularity. These results not only validate the effectiveness of SCOUT, but also demonstrate the practical viability of Flow CoT as a scalable framework for enhancing reasoning in LLMs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

**研究动机与背景**：
- 大型语言模型（LLM）通过链式推理（CoT）提示提升推理能力，但CoT依赖于显式中间步骤的监督，这限制了其可扩展性和泛化性。
- 近期研究探索了递归推理，即LLM通过多次迭代重复使用内部层来细化潜在表示，无需显式CoT监督。但这些方法通常需要昂贵的预训练，并且缺乏一个关于推理如何随迭代演化的原则性框架。
- **核心问题**：如何在不需要额外预训练的情况下，让预训练LLM获得递归推理能力，并且让推理过程能够逐步深化，而不是简单的重复。

**本文意义**：
- 提出**流链式推理（Flow CoT）** 范式，将递归推理建模为潜在认知状态的渐进轨迹。
- 提出**SCOUT**（Stepwise Cognitive Optimization Using Teachers）轻量级微调框架，无需预训练即可实现Flow CoT。

## 2. 论文提出的方法论

### 核心思想
- **Flow CoT**：将多次推理迭代视为认知状态的渐进演化，每个迭代（步骤）产生一个潜在状态 \(z^{(t)}\)，最终状态经解码得到输出。递归块 \(f_\theta\) 负责迭代更新，而历史集成函数 \(H\) 融合初始状态 \(z^{(0)}\) 和上一状态 \(z^{(t-1)}\)。
- **SCOUT框架**：基于Flow CoT，通过两个关键机制实现逐步认知优化：
  1. **渐进蒸馏**：每个迭代由不同容量匹配的教师模型监督。早期步骤使用较小的教师（如1.5B），后期使用更强的教师（如7B），避免早期过拟合，同时将强信号留在模型能吸收的阶段。
  2. **回顾推理模块**：通过交叉注意力（cross-attention）将先前步骤的潜在状态作为外部记忆，当前步对初始状态使用自注意力，对前一步状态使用交叉注意力，从而在保持预训练数据流的同时实现跨步信息融合。

### 关键技术细节
- **模型分解**：将预训练LLM分解为头块（head block）、递归块（recursive block）和尾块（tail block）。默认配置：嵌入层+前1/2层为头，后1/2层为递归块，输出投影为尾块。
- **训练损失**：每个迭代 \(t\) 的损失为KL散度（匹配教师分布）与可选硬标签交叉熵之和，总损失为各步加权和（默认等权）。
- **推理**：按相同递归流程执行 \(T\) 步（固定为3），仅最后一步解码输出。

### 公式与流程（文字说明）
1. 输入 \(x\) → 头块 → 初始潜在状态 \(z^{(0)}\)。
2. 第一次迭代：\(z^{(1)} = f_\theta(z^{(0)})\)。
3. 后续迭代：\(z^{(t)} = f_\theta(H(z^{(0)}, z^{(t-1)}))\)，其中 \(H\) 通过交叉注意力融合。
4. 第 \(T\) 步：输出 \(y = \text{tail}(z^{(T)})\)。
5. 损失：\(\mathcal{L} = \sum_t \lambda_t \cdot \text{KL}(q^{(t)} \| p_\theta^{(t)}) + \alpha \cdot \text{CE}(p_\theta^{(t)}, y^*)\)，其中 \(q^{(t)}\) 来自容量递增的教师模型。

## 3. 实验设计

### 数据集与场景
- **训练数据**：混合五个指令微调数据集：Alpaca GPT-4、Alpaca CoT、WikiQA、CodeAlpaca、MathInstruct。
- **评估基准**：8个推理基准，分为四类：
  - 常识问答：ARC-easy、ARC-challenge、OpenBookQA、TruthfulQA
  - 多步推理：GSM8K、MMLU（论文中实际报告GSM8K和MMLU？表1包含MMLU？仔细看表1：标题列出OB、GSM8K、MBPP、ARC-e、ARC-c、TF、CoQA、GLUE，其中MMLU未在表中？论文4.1提到MMLU，但表1未列，可能省略。实际表1包含8个任务：OpenBookQA、GSM8K、MBPP、ARC-Easy、ARC-Challenge、TruthfulQA、CoQA、GLUE）
  - 阅读理解与对话：CoQA、GLUE
  - 代码生成：MBPP

### 对比方法
- **SFT**：标准监督微调，无递归。
- **DSFT**：蒸馏微调（使用7B教师），无递归。
- **R-SFT**：递归框架+硬标签监督（每个迭代相同标签）。
- **R-Distill-EQ**：递归+固定7B教师+等权损失。
- **R-Distill-WT**：递归+固定7B教师+递增加权损失（λ递增）。
- **R-SCOUT**：反转教师顺序（7B→3B→1.5B）。
- **SCOUT**（本文方法）：渐进蒸馏（1.5B→3B→7B）+交叉注意力回顾模块。

## 4. 资源与算力

**论文明确指出**：
- 硬件：单张NVIDIA H20 NVLink GPU（96 GB），搭配双路Intel Xeon Platinum 8457C CPU（20核）和200 GB RAM。
- 训练：使用torch原生梯度累积模拟全局batch size 128，微调2个epoch，学习率2e-5（新参数4e-5），bf16精度。
- **未提及**：训练总时长、模型参数量（学生0.5B，教师1.5B/3B/7B，但未说明具体训练时间）。

论文附录A.1提供了详细的硬件和优化超参数，但缺少训练时间估算。这可能是因为单卡训练时间较短或作者未视为关键信息。

## 5. 实验数量与充分性

**实验数量**：
- **主实验**（表1）：对比6个baseline + SCOUT，共8种方法，每种方法报告不同迭代步数（1/2/3）在8个基准上的结果，共约8×8×3=192个数值，但表中只列出部分。
- **回顾机制消融**（表2/6）：比较6种集成方式（Init、Add、CatProj、Gate、ModInj、XAttn），在8个基准上报告1/2/3步结果。
- **结构分割消融**（表5）：比较两种层分配策略（Case 1 vs Case 2）在三种回顾模块下的结果。
- **单次渐进蒸馏消融**（表4）：无递归情况下的教师顺序比较。
- **定性分析**（图4、图5）：概率热图和推理轨迹示例。

**充分性与公平性**：
- 覆盖了常识、数学、代码、阅读理解等多个领域，评估全面。
- 对比了蒸馏和递归的各种组合，包括有/无递归、固定/渐进教师、权重分配反转等，控制变量较好。
- 但所有实验仅使用Qwen2.5系列（学生0.5B，教师1.5B/3B/7B），未在其他模型族（如LLaMA）上验证，存在过拟合风险。
- 未报告多次运行的标准差（除图3外），仅报告单次评估，统计显著性不足。

## 6. 论文的主要结论与发现

1. **Flow CoT范式有效**：将递归推理建模为认知状态渐进演化，能显著提升推理准确性和解释质量。
2. **渐进蒸馏优于均匀监督**：SCOUT逐步教导（1.5B→3B→7B）相比固定强教师（R-Distill-EQ）或硬标签（R-SFT）效果更好，且教师顺序反转（R-SCOUT）会导致后期性能下降。
3. **交叉注意力回顾模块最佳**：相比Add、CatProj、Gate等，XAttn能保持跨步一致性，性能随迭代步数单调提升。
4. **SCOUT在微调下实现高达1.8%的平均提升**（相对SFT），并且定性分析显示迭代中信念和推理粒度逐步细化。

## 7. 优点

- **方法论创新**：提出Flow CoT概念，将递归推理从黑盒重复提升为结构化认知演化，具有理论深度。
- **轻量微调**：SCOUT无需预训练，仅需微调即可赋予模型递归推理能力，实用性强。
- **渐进蒸馏设计**：基于KL散度随教师容量增加的观察，提出迭代匹配教师能力，避免了早期过强监督导致的过正则化。
- **回顾模块非侵入式**：交叉注意力模块不破坏预训练数据流，易于集成。
- **实验全面**：覆盖8个推理基准，进行多项消融（方法、模块、结构），并给出定性可视化。

## 8. 不足与局限

- **实验覆盖有限**：
  - 仅使用Qwen2.5单一模型家族，未在LLaMA、Mistral等上验证，泛化性存疑。
  - 仅测试0.5B学生，更大模型（如7B学生）的效果未知。
  - 教师模型固定为1.5B/3B/7B，若只有单一强教师（如仅7B），自蒸馏策略仅简单提及，未实验。
- **固定迭代步数**：当前T=3固定，未实现动态早停或自适应迭代，可能不适合复杂度不同的任务。
- **算力信息不完整**：未报告训练时间、能源消耗，不利于复现和资源评估。
- **统计显著性**：未报告多次运行的标准差或置信区间，单次结果可能受随机性影响。
- **可能偏差**：训练数据混合多种指令，但评估基准可能与训练数据存在重叠或领域偏差（如MathInstruct与GSM8K）。
- **应用限制**：推理时需T次前向传播，效率略低于单次推理；且依赖多个教师模型进行蒸馏，不适用于不开放教师的情形。

---

（完）
