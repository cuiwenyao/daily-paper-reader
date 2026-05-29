---
title: Benchmarking Abstract and Reasoning Abilities Through A Theoretical Perspective
title_zh: 通过理论视角基准测试抽象与推理能力
authors: "Qingchuan Ma, Yuhang Wu, Xiawu Zheng, Rongrong Ji"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=biMO2gWsWS"
tags: ["query:ns-xai"]
score: 8.0
evidence: 构建了大语言模型抽象推理基准，定义并衡量推理能力
tldr: 本文建立了一个理论驱动的抽象推理基准，通过定义数学框架和两个互补指标（Γ和Δ），能够区分模型是否真正进行抽象推理还是仅依赖符号记忆，为评估LLM推理能力提供了严格工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 905, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 908, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1433, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bimo2gwsws/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1809, \"height\": 1982, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bimo2gwsws/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 721, \"height\": 1126, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bimo2gwsws/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 1124, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bimo2gwsws/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1622, \"height\": 1871, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bimo2gwsws/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1776, \"height\": 511, \"label\": \"Table\"}]"
motivation: 需要严格且基于理论的基准来深入探索大语言模型的抽象推理能力。
method: 定义抽象推理的数学框架，提出衡量推理准确性和符号依赖程度的度量，并设计系统符号重映射基准。
result: 所提出的指标能够有效区分模型是否真正理解抽象模式还是仅记忆符号。
conclusion: 该工作为评估和比较LLM的推理能力提供了理论严格且实用的方法。
---

## Abstract
In this paper, we aim to establish a simple, effective, and theoretically grounded benchmark for rigorously probing abstract reasoning in Large Language Models (LLMs). To achieve this, we first develop a mathematic framework that defines abstract reasoning as the ability to: (i) extract essential patterns independent of surface representations, and (ii) apply consistent rules to these abstract patterns. Based on this framework, we introduce two novel complementary metrics: Γ measures basic reasoning accuracy, while ∆ quantifies a model's reliance on specific symbols rather than underlying patterns - a key indicator of true abstraction versus mere memorization. To implement this measurement, we design a benchmark: systematic symbol remapping in rule-based tasks, which forces models to demonstrate genuine pattern recognition beyond superficial token matching. Extensive LLM evaluations using this benchmark (commercial API models, 7B-70B, multi-agent) reveal:1) critical limitations in non-decimal arithmetic and symbolic reasoning; 2) persistent abstraction gaps despite chain-of-thought prompting; and 3) ∆'s effectiveness in robustly measuring memory dependence by quantifying performance degradation under symbol remapping, particularly highlighting operand-specific memorization. These findings underscore that current LLMs, despite domain-specific strengths, still lack robust abstract reasoning, highlighting key areas for future improvement.

---

## 论文详细总结（自动生成）

# 论文总结：《Benchmarking Abstract and Reasoning Abilities Through A Theoretical Perspective》

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有大型语言模型（LLM）在常见基准（如 GSM8K、MATH）上表现出高准确率，但可能只是记忆了模式或使用了表面启发式，而非真正进行抽象推理。需要一种理论驱动、能严格区分“真正抽象”与“记忆依赖”的评估方法。
- **背景**：抽象推理是通用智能的核心，但现有基准（如 ARC、BIG-Bench Hard）或视觉任务与 LLM 文本不兼容，或缺乏理论框架来隔离抽象推理成分。作者提出统一数学框架，设计符号重映射基准，用互补指标 Γ（准确率）和 Δ（记忆依赖）量化抽象推理能力。

## 2. 方法论：核心思想、关键技术细节

- **理论框架**：
  - 定义抽象映射 `f: C → A`（将具体实例映射到抽象特征），推理函数 `Re: A × R → Q`（将抽象特征与规则映射到结论）。
  - 两种复合推理：规则给定（`HG = Re ∘ f`）和规则归纳（`HI`，从例子中推断规则再应用）。
- **核心指标**：
  - **Γ**：原始符号上的任务准确率（基线）。
  - **Δ**：原始准确率减去符号重映射后的准确率；Δ 越大说明模型越依赖特定符号（记忆），越小说明具备真正抽象推理（规则不变性）。
- **符号重映射**：对任务中的操作数、运算符或全部符号进行随机双射替换（如数位 '0','1' → 'A','B'），但保留规则结构。迫使模型必须基于抽象模式而非表面 token 推理。
- **三个定理**：验证了 Γ 对规则给定推理的有效性、Δ 对规则归纳推理的有效性、以及联合分数 `F(Γ, Δ) = w1Γ + w2(1-Δ)` 的合理性。

## 3. 实验设计：数据集、基准、对比方法

- **基准任务**：6 个类别，共 82 个子数据集，总样本数 9095：
  - **BC**（基本计算）：十进制加减乘除
  - **EC**（扩展计算）：位运算、字符串操作、集合操作等
  - **NBR**（数基推理）：非十进制（base3、base4、base5）算术
  - **MA**（数学应用）：GSM8K 风格应用题
  - **SMA**（符号数学抽象）：从输入-输出对推断函数（线性、正弦等）
  - **SR**（符号推理）：对 EC 任务进行符号重映射后的变体
- **对比模型**：
  - 7B：GLM-4-9B、Gemma-2-9B、Llama-3.1-8B、Qwen2.5-7B、Qwen2.5-Math-7B、Yi-1.5-9B、Marco-o1、InternLM2-7B 等
  - 32B：QWQ-32B-Preview
  - 70B：Llama-3.3-70B、Qwen2.5-72B、Llama-3.1-Nemotron-70B、OpenMath2-Llama70B
  - API：GPT-4o-mini、Gemini-1.5/2.0、DeepSeek V3
  - Agent 框架：AgentChat (AutoGen)、ReAct、LLM Debate（均基于 GPT-4o-mini）
- **提示策略**：Direct Prompting (DP) 和 Chain-of-Thought (CoT)，MA 使用 8-shot CoT，其余为零样本 CoT。

## 4. 资源与算力

- 文中明确说明：所有实验在本地机器上使用 8 块 NVIDIA GPU（包括 A800 和 RTX 3090）进行。
- **未提供**具体训练时长、总 GPU 小时数或能耗数据。微调实验（附录）使用 8 块 GPU 但未说明耗时。

## 5. 实验数量与充分性

- **实验数量**：大量——在 20 余种模型/规模上，每个模型使用 2 种提示策略，测试 6 个类别，输出 Γ 和 Δ（操作数、运算符、全部三种重映射），结果呈现在 Table 1、2、3 和 Figure 3、4。此外还包括：
  - 微调 Llama-3.1-8B 的对比实验（Table 4）
  - 人类基线（4 名计算机专业本科生）
  - 案例研究（成功/失败分析）
- **充分性与公平性**：覆盖不同规模、不同训练数据（数学专用、通用）、不同推理范式（直接/CoT/多智能体）。但存在局限：
  - 每个子数据集仅 96 样本（除 GSM8K 外），统计可靠性有限。
  - 模型种类虽多，但 Agent 框架均基于 GPT-4o-mini，未测试其他基座。
  - 未系统控制提示模板差异（CoT 格式对模型友好度可能不同）。

## 6. 主要结论与发现

1. **非十进制算术（NBR）全面崩溃**：所有模型平均 Γ < 0.1，包括 70B 和 API 模型，表明 LLM 无法将十进制算术原理抽象到其他数基。
2. **符号推理（SR、SMA）持续困难**：平均 Γ 普遍低于 0.3，即使使用 CoT。
3. **Δ 揭示操作数记忆强于运算符记忆**：`MemDep_num` > `MemDep_op`，说明模型更依赖具体数值 token，而非抽象算则。
4. **CoT 的双刃剑效应**：CoT 提高 MA、EC 等熟悉任务的 Γ，但有时同时增加 Δ（如 glm-4-9b 的 ΔNUM 从 0.26 升至 0.30），说明 CoT 可能强化 token 特定推理而非真正抽象。
5. **多 Agent 框架**：虽获得较高 Γ（如 AgentChat 平均 0.60），但 Δ 也最高（0.56），表明仍存在严重记忆依赖，未解决根本抽象缺陷。
6. **人类对比**：人类在重映射位运算和非十进制算术上达 97% 和 87% 准确率，远高于最佳 LLM（如 Gemini-2.0-thinking 分别为 57% 和 75%），突出巨大差距。

## 7. 优点

- **理论严谨**：首次为 LLM 抽象推理评估提供正式数学定义和指标验证定理。
- **设计巧妙**：符号重映射简单高效，能直接量化“记忆 vs 抽象”，且可自动生成大量变体。
- **评估全面**：涵盖多种规模、提示策略、多智能体，并包含人类基线。
- **诊断价值**：Δ 可分解为操作数和运算符维度，揭示记忆偏好，指导未来改进方向。

## 8. 不足与局限

- **基准任务范围有限**：仅覆盖符号运算、数基转换、简单函数拟真，未涉及视觉、自然语言、因果推理等丰富抽象场景。
- **样本量较小**：多数子数据集仅 96 个测试样本，可能影响统计稳定性。
- **模型代表性问题**：7B 模型仅测试 9 个，且部分为数学专用（如 Qwen2.5-Math-7B），可能不反映通用模型；Agent 框架均基于 GPT-4o-mini，未验证其他基座。
- **评估方式依赖解析**：使用 GPT-4o-mini 解析模型输出，引入额外误差；未考虑模型输出格式多样性对 Γ 的影响。
- **缺乏对实际应用泛化性的讨论**：符号重映射虽然理论干净，但现实抽象推理可能涉及语义转移、知识整合等更复杂因素。
- **Δ 的局限性**：仅测量符号替换下的性能下降，无法区分“规则错误”与“符号映射错误”，且假设重映射不改变难度（可能因符号频率差异引入偏差）。

（完）
