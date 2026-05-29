---
title: Calibrating Reasoning in Language Models with Internal Consistency
title_zh: 用内部一致性校准语言模型中的推理
authors: "Zhihui Xie, Jizhou Guo, Tong Yu, Shuai Li"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=udZKVMPf3S"
tags: ["query:ns-xai"]
score: 7.0
evidence: 利用内部一致性校准大模型推理
tldr: 该论文从内部表示视角研究LLM推理，发现生成理由虽提升准确率但导致中间层与最终层表示不一致。基于此提出内部一致性校准方法，增强了推理可靠性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1362, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 627, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1277, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1413, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 1431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1428, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1426, \"height\": 1441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1428, \"height\": 1430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-udzkvmpf3s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1434, \"height\": 1442, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 1261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 1369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1296, \"height\": 1159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 613, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 988, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1166, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 953, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-udzkvmpf3s/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1047, \"height\": 542, \"label\": \"Table\"}]"
motivation: LLM生成的推理过程常出现错误和矛盾，影响可靠性。
method: 分析中间层与最终层表示的一致性，并基于此设计校准方法。
result: 发现表示不一致性，校准后提高了推理鲁棒性。
conclusion: 内部一致性是LLM推理可解释性和可靠性的重要指标。
---

## Abstract
Large language models (LLMs) have demonstrated impressive capabilities in various reasoning tasks, aided by techniques like chain-of-thought prompting that elicits verbalized reasoning. However, LLMs often generate text with obvious mistakes and contradictions, raising doubts about their ability to robustly process and utilize generated rationales. In this work, we investigate reasoning in LLMs through the lens of internal representations, focusing on how these representations are influenced by generated rationales. Our preliminary analysis reveals that while generated rationales improve answer accuracy, inconsistencies emerge between the model’s internal representations in middle layers and those in final layers, potentially undermining the reliability of their reasoning processes. To address this, we propose internal consistency as a measure of the model’s confidence by examining the agreement of latent predictions decoded from intermediate layers. Extensive empirical studies across different models and datasets demonstrate that internal consistency effectively distinguishes between correct and incorrect reasoning paths. Motivated by this, we propose a new approach to calibrate reasoning by up-weighting reasoning paths with high internal consistency, resulting in a significant boost in reasoning performance. Further analysis uncovers distinct patterns in attention and feed-forward modules across layers, providing insights into the emergence of internal inconsistency. In summary, our results demonstrate the potential of using internal representations for self-evaluation of LLMs.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在推理任务中常出现错误和矛盾，其生成的推理链条（Chain-of-Thought, CoT）虽然提升了准确率，但内部表示在中间层与最终层之间出现不一致，影响推理的可信度和鲁棒性。
- **研究动机**：现有方法多关注输出层或表面合理性，缺乏对模型内部表示一致性的利用。论文旨在通过内部表示来评估和校准推理过程，提升LLM的可靠性。
- **整体含义**：提出“内部一致性”（Internal Consistency）作为衡量模型置信度的新指标，并基于此设计校准方法，为LLM的自我评估提供了新视角。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用Transformer中间层的潜在预测（latent predictions）与最终预测的一致性来评估推理路径的质量。若中间层和最终层的预测高度一致，则该路径更可靠。
- **关键技术细节**：
  - **内部一致性度量**：在推理过程中，从每个中间层解码出潜在预测（使用logit lens或tuned lens），计算这些潜在预测与最终预测的匹配比例。
  - **公式**：InternalConsistency(x, ŷ) = (1/(L-1)) * Σ_{ℓ=1}^{L-1} 1{ŷ^ℓ = ŷ^L}，其中L为层数，ŷ^ℓ为第ℓ层的潜在预测，ŷ^L为最终预测。
  - **校准方法**：基于自我一致性（Self-Consistency, SC）采样多条推理路径，使用内部一致性作为权重，对路径进行加权投票（SC+IC）。同时提出两种变体：SC+IC(tune)（学习每层权重）和SC+IC(transfer)（跨任务迁移权重）。
- **算法流程**（文字说明）：
  1. 使用CoT或Least-to-Most提示生成多条推理路径。
  2. 对每条路径，在答案token处采集各层的潜在预测。
  3. 计算每条路径的内部一致性分数（中间层预测与最终预测的一致比例）。
  4. 进行加权投票：将每个答案对应的所有路径的内部一致性分数求和，选择得分最高的答案。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集**：涵盖阅读理解（BoolQ）、符号推理（CoinFlip）、逻辑推理（PrOntoQA、ProofWriter）四种任务，均转换为真/假判断题格式，保证单token输出。
- **Benchmark**：使用校准准确率（calibrated accuracy），平衡正负样本预测。
- **对比方法**：
  - 贪心解码（Greedy）
  - 自我一致性（SC）
  - 基于logit置信度的SC+Δ（SC+Δ）
  - 提出的SC+IC及其变体（SC+IC(tune)、SC+IC(transfer)）
- **模型**：Llama-2-7B/13B、Mistral-7B、Mixtral-8×7B（包含MoE架构）。

## 4. 资源与算力

- **明确说明**：论文在附录B中提到，所有实验在8块Nvidia GPU卡、512GB内存的计算节点上进行。总估计计算时间小于100 GPU小时（仅指重现实验部分），但整个研究项目消耗更多。未指定具体GPU型号。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：4个模型 × 4个数据集 × 2种提示（CoT和Least-to-Most） = 32组主要对比，每组10个随机种子。
  - 消融实验：包括不同提示方式、不同采样数量（10~40个路径）、层权重学习与迁移。
  - 探针分析：线性探针实验、注意力权重和FFN值向量分析。
- **充分性**：实验覆盖多种模型规模（7B~8×7B）、任务类型和提示方式，统计显著性通过多次随机种子体现。对比方法标准且公开，实验设计客观公平。

## 6. 论文的主要结论与发现

- CoT提示虽然提升准确率，但会加剧中间层与最终层之间的表示不一致性。
- 内部一致性在正确推理路径上显著高于错误路径，可作为可靠的置信度指标。
- 基于内部一致性的加权策略（SC+IC）在大部分任务上优于SC和SC+Δ，尤其在逻辑推理任务中提升明显（最大提升约4.9%）。
- 层权重学习（tune）可进一步提升性能，且学到的权重可跨任务迁移，表明层重要性模式具有通用性。
- 内部不一致的成因：中间层的自注意力层关注查询和推理步骤，而FFN层在后期层主导最终输出，两者不匹配导致中间层信息未充分传递到最终层。

## 7. 优点

- **方法创新**：首次系统利用中间层潜在预测的一致性进行推理校准，无需额外训练或人工标注。
- **计算高效**：仅需单次前向传播即可计算内部一致性，可集成到现有解码流程。
- **可解释性强**：通过注意力权重和FFN值向量分析揭示了内部不一致的机制。
- **实验全面**：覆盖多种模型、任务和提示，验证了方法的通用性和稳定性。
- **层权重迁移**：展示了跨任务迁移能力，降低了在新任务上的调参成本。

## 8. 不足与局限

- **模型范围有限**：仅聚焦于decoder-only模型，未扩展到encoder-decoder模型（如T5、BART），尽管论文提到了decoder lens可作为扩展方向。
- **提示方式局限**：主要使用vanilla CoT和Least-to-Most，未涵盖更复杂的提示策略（如Tree-of-Thought、Self-Ask等）。
- **任务类型局限**：所有任务均转换为二分类判断题，未验证在多标签或生成式推理任务中的效果。
- **潜在偏差**：在PrOntoQA和ProofWriter等逻辑推理任务上，直接使用模型输出的校准准确率较低，依赖校准步骤；且对高一致性路径的加权可能强化模型的固有偏差。
- **实际部署限制**：方法依赖于访问中间层表示，对于API-only模型或黑盒模型不适用。

（完）
