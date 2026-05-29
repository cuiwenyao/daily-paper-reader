---
title: Self-Verifying Reflection Helps Transformers with CoT Reasoning
title_zh: 自验证反思有助于Transformer的链式思维推理
authors: "Zhongwei Yu, Wannian Xia, Xue Yan, Bo XU, Haifeng Zhang, Yali Du, Jun Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4MvqmXnCEr"
tags: ["query:ns-xai"]
score: 7.0
evidence: 链式思维中的自验证反思提升可解释性
tldr: 该论文研究了LLM链式思维推理中的自验证反思机制，通过理论证明和实验表明，当验证错误有界时，自验证反思能保证推理改进。为可解释推理提供了机制分析框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1398, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1457, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1123, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1431, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1429, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1106, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1115, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1452, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1449, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 981, \"height\": 1149, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4mvqmxncer/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 990, \"height\": 1723, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1257, \"height\": 1023, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1098, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 1331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1299, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 902, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1462, \"height\": 898, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1406, \"height\": 855, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1155, \"height\": 853, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 903, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1362, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1399, \"height\": 857, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4mvqmxncer/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1149, \"height\": 857, \"label\": \"Table\"}]"
motivation: LLM中反思机制如何提升推理性能尚不清晰，且模型检测错误能力有限。
method: 构建简约推理框架，支持无自然语言的自验证反思，并进行理论分析。
result: 实验显示小Transformer在自验证下推理性能提升。
conclusion: 自验证反思为可解释推理机制提供了理论基础。
---

## Abstract
Advanced large language models (LLMs) frequently reflect in reasoning chain-of-thoughts (CoTs), where they self-verify the correctness of current solutions and explore alternatives. However, given recent findings that LLMs detect limited errors in CoTs, how reflection contributes to empirical improvements remains unclear. To analyze this issue, in this paper, we present a minimalistic reasoning framework to support basic self-verifying reflection for small transformers without natural language, which ensures analytic clarity and reduces the cost of comprehensive experiments. Theoretically, we prove that self-verifying reflection guarantees improvements if verification errors are properly bounded. Experimentally, we show that tiny transformers, with only a few million parameters, benefit from self-verification in both training and reflective execution, reaching remarkable LLM-level performance in integer multiplication and Sudoku. Similar to LLM results, we find that reinforcement learning (RL) improves in-distribution performance and incentivizes frequent reflection for tiny transformers, yet RL mainly optimizes shallow statistical patterns without faithfully reducing verification errors. In conclusion, integrating generative transformers with discriminative verification inherently facilitates CoT reasoning, regardless of scaling and natural language.

---

## 论文详细总结（自动生成）

# 论文总结：Self-Verifying Reflection Helps Transformers with CoT Reasoning

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大型语言模型（LLMs）在链式思维（CoT）推理中频繁进行反思（自我验证当前步骤正确性并探索替代方案），但先前研究表明LLMs检测错误的能力有限，那么反思为何仍能带来经验性提升尚不清晰。
- **整体含义**：本文旨在通过构建简约的反思框架，从理论和实验角度阐明自验证反思在CoT推理中的作用，为理解LLM中的反思机制提供基础性分析，并揭示其与强化学习的协同效应。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将推理建模为马尔可夫思维过程（MTP），模型在每一步生成推理步骤后，利用同一模型进行自我验证（判别性标签“√”/“×”），若被判定为错误则重新采样或回溯。提出两种反思变体：
  - **反思MTP（RMTP）**：当前步被拒绝时状态保持不变，允许重新采样。
  - **反思回溯搜索（RTBS）**：当某状态上尝试次数超过宽度m后，将否定标签回溯到父步骤，从而回退到更早状态。
- **关键技术细节**：
  - 采用*极小化原则*设计框架，避免自然语言，使小Transformer也能进行反思推理。
  - 训练流程：预训练 → 非反思SFT → 反思SFT（使用专家验证器标注样本）→ 强化学习微调（GRPO，基于结果奖励）。
  - 理论结果（定理1）：若验证误差（假正率e⁺和假负率e⁻）满足 e⁻ + e⁺ ≤ 1，则RMTP优于无反思；若拒绝概率 f > α 且宽度 m > 1/(1-α)，则RTBS优于RMTP。命题1给出预期推理步数与e⁻成正比。

## 3. 实验设计
- **任务与数据**：整数乘法（Mult）和9×9数独（Sudoku），按难度分为ID Easy、ID Hard、OOD Hard三级。训练集包含ID Easy和ID Hard问题，测试集额外包含OOD Hard。
- **模型**：1M、4M、16M参数的小Transformer（因果注意力机制，实现基于LitGPT）。
- **对比方法**：
  - 执行方式：无反思、RMTP、RTBS。
  - 验证类型：无、二进制、详细、可选详细。
  - 基线：直接推理、完整状态推理（对比状态简化的重要性）。
  - 跨规模对比：与GPT-4o、DeepSeek-R1、o3-mini在相同任务上的表现对比（作为参考）。
- **评估指标**：推理准确率、验证误差（e⁺、e⁻）、反思频率。

## 4. 资源与算力
- **硬件资源**：5块GPU（1块NVIDIA RTX-3090 + 4块NVIDIA A10）。
- **训练时长**：每个模型（大小×任务）的完整流水线（预训练+SFT+RL）约需2天。其中非反思SFT约1-2小时，反思SFT数据收集8-12小时，反思SFT训练1-2小时，RL 6-12小时，测试6-12小时。
- **显存**：1M模型约4GB，4M模型约12GB，16M模型约16GB。
- **说明**：可在一台普通PC上复现，但多组实验并行使用了云服务器。

## 5. 实验数量与充分性
- **实验数量**：共训练78个模型（30个SFT模型 + 后续RL/PPO实验，涵盖不同大小、任务、验证类型、执行方式）。实验结果表格丰富（附录E给出了完整表格）。
- **充分性**：
  - 包含消融实验（状态简化、验证类型、是否反思、不同搜索宽度）。
  - 对比多种执行方式、验证类型、模型大小。
  - 还提供了LLM参考性能、反思频率热图、验证误差变化分析。
- **公平性与客观性**：实验设计系统，但未报告统计误差棒（作者解释因资源限制）。结论基于多个条件的一致现象，具有说服力。不足在于OOD泛化能力弱，RL优化浅层。

## 6. 主要结论与发现
1. **学习自验证促进前向推理**：即使测试时不使用反思，仅通过反思SFT也能提升非反思执行准确率（尤其是小模型）。学习自验证起到了正则化作用。
2. **反思提升准确率的条件**：当假负率（e⁻）足够低时，RMTP显著优于无反思；若假负率高，改进不明显甚至退化。
3. **回溯搜索在可验证错误环境下更有效**：数独中错误状态易于判别（f > α），RTBS优于RMTP；乘法中状态错误难以检测，RTBS无优势。
4. **RL激励反思依赖于探索能力**：在较高采样温度下，RL能引发频繁反思（类似DeepSeek-R1）；但在低温度或弱模型（1M）中反思频率极低。
5. **RL优化是浅层的**：RL主要降低e⁻（减少拒绝正确步骤），但以升高e⁺（接受错误步骤）为代价，并未真正提升验证能力；OOD性能提升微弱。

## 7. 优点
- **框架简约清晰**：去除了自然语言复杂性，使反思行为可被严格分析和复现，且计算成本极低。
- **理论结合实验**：给出了反思有效的充分必要条件，并可视化验证误差与性能的关系。
- **实验全面**：覆盖多种模型规模、任务难度、验证类型、训练范式，并与真实LLM对比，结论具有普适性。
- **代码开源**：便于后续研究复现与扩展。

## 8. 不足与局限
- **泛化能力有限**：OOD Hard任务准确率极低（尤其乘法），RL未能有效提升泛化。
- **反思框架过于简化**：未利用自然语言的灵活性，可能忽略了语言反思中的高阶认知行为（如复杂修正）。
- **未提供误差棒**：因资源限制，未重复实验估计统计误差，可能影响结论的稳健性。
- **RL的浅层优化**：RL主要调整验证决策偏好而非真正改进验证能力，存在过优偏差风险。
- **实验规模限制**：仅使用两种任务，且模型参数最大16M，结论向大型LLM的迁移需进一步验证。

（完）
