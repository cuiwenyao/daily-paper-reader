---
title: "Revisiting Chain-of-Thought in Code Generation: Do Language Models Need to Learn Reasoning before Coding?"
title_zh: 重新审视代码生成中的思维链：语言模型需要在编码前学习推理吗？
authors: "Ren-Biao Liu, Anqi Li, Chaoding Yang, Hui Sun, Ming Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=wSZeQoJ1Vk"
tags: ["query:ns-xai"]
score: 6.0
evidence: 研究大模型如何从思维链中学习推理以生成代码
tldr: 该论文重新审视了代码生成中思维链训练方式，通过分离推理步骤和代码解决方案，实验发现学习推理步骤再生成代码并不总是最优，存在反直觉现象。对理解大模型推理学习机制有启示，但与可解释性直接关联较弱。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 831, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 857, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 834, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 836, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 834, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 837, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 826, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1779, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1777, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1777, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1776, \"height\": 488, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 796, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 829, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 741, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 798, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 793, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 819, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 833, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 851, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1173, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1201, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1143, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1322, \"height\": 238, \"label\": \"Table\"}]"
motivation: 现有研究对思维链在代码生成中的学习机制理解不足。
method: 构建分离推理与代码的数据集，进行系列实验研究学习顺序影响。
result: 发现反直觉现象：推理步骤学习不一定提升代码生成。
conclusion: 思维链训练方式需根据任务调整，对大模型推理设计有参考价值。
---

## Abstract
Large Language Models (LLMs) have demonstrated exceptional performance in code generation, becoming increasingly vital for software engineering and development. Recently, Chain-of-Thought (CoT) has proven effective for complex tasks by prompting LLMs to reason step-by-step and provide a final answer.
However, research on *how LLMs learn to reason with CoT data for code generation* remains limited.
In this work, we revisit classic CoT training, which typically learns reasoning steps before the final answer.
We synthesize a dataset to separate the CoT process from code solutions and then conduct extensive experiments to study how CoT works in code generation empirically.
We observe counterintuitive phenomena, suggesting that the traditional training paradigm may not yield benefits for code generation. Instead, training LLMs to generate code first and then output the CoT to explain reasoning steps for code generation is more effective.
Specifically, our results indicate that a 9.86% relative performance improvement can be achieved simply by changing the order between CoT and code. Our findings provide valuable insights into leveraging CoT to enhance the reasoning capabilities of CodeLLMs and improve code generation.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管 Chain-of-Thought（CoT）在复杂推理任务中表现出显著效果，但在代码生成领域，**语言模型如何从 CoT 数据中学习推理以提升代码生成能力**这一问题尚未被深入探索。
- **核心问题**：传统的 CoT 训练范式——即先输出推理步骤再生成最终答案——在代码生成中是否最优？是否存在更有效的训练顺序？
- **背景意义**：代码生成需要严谨的推理能力，但现有研究大多关注 CoT 提示策略，而非 SFT 阶段 CoT 与代码的顺序影响。本文填补了这一空白，为利用 CoT 提升 CodeLLM 性能提供了新视角。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：高质量代码本身可以充当推理过程，而传统 CoT 更适合作为**代码的后续解释**。改变 CoT 与代码的输出顺序（即先生成代码、再输出 CoT）能显著提升性能。
- **关键技术细节**：
  - **数据集构建**：从多个开源数据源（如 Magicoder-OSS-Instruct、ShareGPT 等）收集种子问题与代码，使用教师模型（DeepSeek-V2.5-1210）通过上下文蒸馏生成推理步骤（CoT）和高质量代码，并利用**自我一致性**（Self-Consistency）过滤无效样本，最终得到 52,293 对（问题、推理、代码）结构化数据集。
  - **四种 SFT 策略**：
    - **Seed**：原始种子数据（问题+回答）。
    - **Cw/o**：仅代码，无 CoT。
    - **Cfollow**：传统顺序（先 CoT 再代码）。
    - **Cprecede**：新顺序（先代码再 CoT）。
  - **训练流程**：采用标准自回归式监督微调，损失函数为交叉熵，模型为 Decoder-only LLM。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
  - 训练集：自建的 50K+ 合成数据集。
  - 评估 Benchmark：**HumanEval、MBPP、HumanEval+、MBPP+**（EvalPlus 扩展）、**LiveCodeBench**（抗污染）、**BigCodeBench**（复杂指令与函数调用）、**MultiPL-E**（多语言）、**EvalPerf**（效率）。
- **对比方法**：四种 SFT 策略（Seed、Cw/o、Cfollow、Cprecede），并在多个基模型（DeepSeek-Coder-6.7B/33B、Llama-3.1-8B、Qwen2.5-7B/32B）上重复实验。
- **额外实验**：更换教师模型（GPT-4o-0806）、改变合成顺序、使用不同数据源（The Stack）、去除签名/注释、混合模式、对抗攻击、不同批次大小/学习率/训练轮数等消融研究。

## 4. 资源与算力

- 论文明确说明使用 **8 张 NVIDIA A100-SXM4-80GB GPU**，采用混合精度训练（BF16）、ZeRO-3、DeepSpeed、FlashAttention-2。
- **训练时长**：未明确给出总时间，但基于步数（通常在 1200 步左右）可推断训练周期相对可控（完整训练约数小时至十数小时）。文中在多个配置下对比了不同训练步数的性能曲线。

## 5. 实验数量与充分性

- **实验数量**：非常充分。包括：
  - 主实验在 6 个以上 Benchmark 上评估（共 4 种策略 × 多个基模型）。
  - 消融实验：教师模型替换、合成顺序、数据源、批大小/学习率/轮数、签名/注释去除、混合模式、对抗攻击。
  - 可解释性分析：条件困惑度、KL 散度、注意力权重、梯度范数、输出长度/质量比较。
  - 多模型规模验证（6.7B → 33B/32B）。
- **充分性与公平性**：实验设计系统，控制变量严谨，使用统一的训练和评估框架（OpenCodeEval），并提供了显著性检验（t-test）以证实差异的统计意义。结论在多种设置下持续复现，客观性强。

## 6. 论文的主要结论与发现

1. **先代码后 CoT 显著优于先 CoT 后代码**：Cprecede 相比 Cfollow 在 EvalPlus 上相对提升 **9.86%**（平均 Pass@1 从 65.43% 提升至 71.88%）。
2. **代码本身可作为有效推理**，传统 CoT 应被视为对代码的**解释而非前置推理**。
3. **高质量代码即使无 CoT（Cw/o）也优于带传统 CoT 的顺序**，表明过度或不当的 CoT 反而损害性能。
4. **注意力与梯度分析**：Cprecede 策略下模型能更均衡地学习代码与 CoT，减少“过度思考”，改善泛化。
5. **结论在多种基模型、教师模型、数据源、困难度和规模下均一致**，具有良好的鲁棒性。

## 7. 优点

- **方法创新**：首次系统性地研究 CoT 位置对代码生成 SFT 的影响，挑战了传统 CoT 的前置假设，提出“代码即推理”的新观点。
- **实验设计严谨**：构建专门分离推理与代码的数据集，避免格式混乱；包含大量消融实验和可解释性分析，结论可靠。
- **广泛验证**：覆盖多种 LLM 架构、规模（6.7B~33B）、不同数据来源和评估基准，结论普适性强。
- **实用价值**：仅改变训练数据中 CoT 与代码的顺序即可大幅提升性能，无需额外计算成本，易于部署。

## 8. 不足与局限

- **数据合成依赖单一教师模型**：主要使用 DeepSeek-V2.5-1210 合成，虽用 GPT-4o 验证，但可能引入教师模型的特定偏差。
- **语言局限性**：实验仅基于 Python 代码生成，其他编程语言（如 Java、C++）的推广性仅通过 MultiPL-E 初步验证，未深入分析。
- **未覆盖高级对齐方法**：如 RLHF/DPO 与 CoT 顺序的交互未探讨；仅关注 SFT 阶段。
- **未研究更大规模模型**：最大模型为 33B，未涵盖 70B+ 或千亿级模型，结论外推性待验证。
- **缺乏真实任务评估**：如 SWE-bench 等实际软件工程任务，可能影响应用的直接转化。

（完）
