---
title: "On the Bias of Next-Token Predictors Toward Systematically Inefficient Reasoning: A Shortest-Path Case Study"
title_zh: 论下一代词预测器向系统性低效推理的偏差：最短路径案例研究
authors: "Riccardo Alberghi, Elizaveta Demyanenko, Luca Biggio, Luca Saglietti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=l8razJItEy"
tags: ["query:ns-xai"]
score: 6.0
evidence: 研究语言模型中的推理效率与偏差
tldr: 针对LLM推理中冗余和效率问题，以最短路径任务为控制实验，比较基于最优动态规划轨迹与长轨迹训练的Transformer模型。发现最优轨迹训练出的模型推理更简洁、系统，且泛化能力更强。该结果揭示了下一代词预测器的系统性偏差，为设计更高效的推理链提供了理论指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 708}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1167, \"height\": 597}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1373, \"height\": 479}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1393, \"height\": 448}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1175, \"height\": 442}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1178, \"height\": 515}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1398, \"height\": 888}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 953, \"height\": 444}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 567, \"height\": 750}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 919, \"height\": 444}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 1425}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1315, \"height\": 195}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1343, \"height\": 152}]"
motivation: LLM推理链常包含冗余，且系统性最优推理不足。
method: 在分层图上训练Transformer比较不同轨迹，分析推理效率与系统性。
result: 最优动态规划轨迹训练的模型以更短的推理步数达到更高准确率。
conclusion: 系统性偏差导致LLM倾向于冗长推理，使用最优轨迹可提升效率。
---

## Abstract
Recent advances in natural language processing highlight two key factors for improving reasoning in large language models (LLMs): (i) allocating more test-time compute tends to help on harder problems but often introduces redundancy in the reasoning trace, and (ii) compute is most effective when reasoning is systematic and incremental, forming structured chains of thought (CoTs) akin to human problem-solving. To study these factors in isolation, we introduce a controlled setting based on shortest-path tasks in layered graphs. We train decoder-only transformers on question–trace–answer triples using a custom tokenizer, comparing models trained on optimal bottom-up dynamic programming traces with those trained on longer, valid traces involving backtracking. Surprisingly, under the same training-token budget, the latter models generalize better to unseen graphs. This benefit is not due to length alone—injecting arbitrary redundancy into reasoning traces fails to help and can even hurt performance. Instead, we find that generalization correlates with the model's confidence in next-token prediction, suggesting that long, coherent, and locally incremental traces make the training signal easier to optimize.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：大型语言模型（LLMs）在推理任务中表现优异，且通常受益于“链式思维”（Chain-of-Thought, CoT）——即逐步生成中间推理步骤。同时，“测试时计算”（test-time compute）的增加有助于解决更难的问题，但往往引入推理轨迹中的冗余。
- **核心问题**：何种结构的推理轨迹对下一代词预测器（next-token predictor）最有效？最优（最短、最有效率）的推理策略是否一定是模型易于学习的？
- **研究动机**：要在控制环境下独立考察推理效率与结构的影响，避免自然语言任务的混杂变量。
- **整体含义**：发现了一个反直觉的现象——训练在**系统性但低效**（如深度优先搜索、需多次回溯）的推理轨迹上的模型，其泛化能力优于训练在**最优动态规划**轨迹上的模型。这表明下一代词预测器存在系统性偏差，倾向于学习局部增量、可预测的推理路径，而非全局最优的短路径。

## 2. 论文提出的方法论

### 核心思想
- 使用**分层有向无环图（DAG）上的最短路径问题**作为受控实验平台。
- 将问题实例、中间推理轨迹、最终答案编码为自定义token序列，训练解码器-only transformer（Phi3小模型）执行下一个token预测。
- 通过参数 \(\eta\)（效率温度）控制推理轨迹的探索顺序：\(\eta>0\) 偏向层序DP（高效），\(\eta<0\) 偏向深度优先DFS（低效、需回溯）。所有推理轨迹均满足正确性、增量构建、最优性等条件。

### 关键技术细节
- **图生成**：参数 \(\{L, K, C, p_e\}\)（最大层数、每层节点数、最大边代价、边连接概率）。每层内部节点数随机，首尾层各一个节点。
- **自定制tokenizer**：包含 `BoS`, `EoS`, `BoT`, `EoT`, 层标签、节点标签、整数值、分隔符等。
- **推理轨迹生成算法**：维护探索队列，根据 \(\eta\) 加权采样下一个部分路径。当发现到某中间节点的更优路径时进行回溯更新。
- **训练设置**：Phi3架构（3层、12注意力头、768隐藏维、28.5M参数），固定学习率 \(2\times10^{-5}\)，AdamW优化器，批次约16K tokens（不含填充），掩盖问题和填充标记的损失。
- **评估指标**：**答案准确率**（路径存在性、长度正确、代价最小、代价一致）、**推理步数**、**next-token置信度**（平均采样token概率）。

## 3. 实验设计

### 数据集/场景
- **合成分层图**：参数 \(L=7, K=6, C=5, p_e=0.6\)。训练集和测试集各含至少数万图实例，且实例唯一（9:1划分）。
- **推理轨迹类型**：
  - \(\eta = +5\)（DP）：层序高效轨迹。
  - \(\eta = 0\)：随机顺序混合探索。
  - \(\eta = -5\)（DFS）：深度优先回溯轨迹。
  - 增加冗余版本：确定性重复（DR）和随机重复（RR）。
- **基准对比**：
  - 无推理轨迹（直接问答） vs. 有推理轨迹。
  - 不同 \(\eta\)（效率）对比。
  - 不同token预算（32M vs 128M tokens）。
  - 不同模型深度（3层 vs 6层）。
  - 不同采样温度（0, 0.5, 1.0等）。

### 对比方法
- 主要对比 **DP轨迹** 与 **DFS轨迹**，以及中间随机轨迹（\(\eta=0\)）。
- 消融实验：注入冗余（DR/RR）、不同温度、不同模型大小、不同数据量。

## 4. 资源与算力

- **GPU**：Nvidia A100 80GB 或 RTX4090 24GB，搭配32 CPU核。
- **精度**：FP16。
- **内存**：3层模型约14GB GPU显存。
- **训练时长**：文中未明确给出单个训练运行的具体时长，但提到大部分实验在上述GPU上执行。
- **代码**：基于PyTorch、HuggingFace、vLLM框架，代码已开源。

## 5. 实验数量与充分性

- **主要实验组**：
  - 有无推理轨迹（图3）。
  - 不同 \(\eta\)（+5, 0, -5）在两种token预算下（32M, 128M）（图4）。
  - 冗余注入（DR, RR）对比（图5）。
  - 不同采样温度对 \(\eta=0\) 和 \(\eta=+5\)(RR) 的影响（图5、图6）。
  - 不同模型层数（3 vs 6）和数据量（16M vs 32M tokens）的消融（附录B.3）。
- **充分性评价**：
  - 每组实验报告了5个随机种子的均值和1-sigma误差棒，统计可靠性较高。
  - 覆盖了多样本量、不同结构轨迹、冗余注入、温度、模型大小等维度。
  - 实验设计较为系统，能支持主要结论。但所有实验均在单一合成任务和单一模型架构（Phi3）上进行，缺乏自然语言场景的验证。

## 6. 论文的主要结论与发现

1. **链式思维（CoT）是关键**：没有推理轨迹的模型无法在更大图上泛化，而带有推理轨迹的模型表现显著提升。
2. **结构优于全局最优性**：训练在系统但低效（DFS）轨迹上的模型，即使在相同token预算下看到更少图实例，其泛化性能仍优于训练在最优DP轨迹上的模型。
3. **Next-token置信度是学习能力的良好代理**：在测试集上，模型对推理轨迹的下一词平均置信度与答案准确率强相关。DFS轨迹具有更确定的探索顺序，因此更易预测，而DP轨迹中同级路径顺序随机，降低了置信度。
4. **冗余注入无益甚至有害**：确定性重复（DR）或随机重复（RR）并不改善性能，随机重复还导致模型生成过长的推理序列（verbosity bias）。
5. **模型对较长推理轨迹存在系统性偏好**：在零温度下，\(\eta=0\)或RR模型生成的轨迹长度一开始偏向DFS的长度，需要长时间训练才能收敛到预期长度；适当提高采样温度反而能正则化这种冗长倾向。

## 7. 优点

- **极高的控制性**：通过合成图任务，独立操控推理轨迹的效率、结构、长度、随机性，避免了自然语言混杂因素的干扰。
- **反直觉发现**：揭示了“最优策略未必是模型最易学的”这一重要现象，对CoT设计和训练策略有指导意义。
- **置信度指标引入**：提出以next-token置信度作为轨迹可学习性的有效代理，为理解模型行为提供了新视角。
- **实验设计严谨**：多组对比、多次种子、误差棒报告，结果可信。
- **代码开源**：便于复现和扩展。

## 8. 不足与局限

- **实验覆盖有限**：仅针对单一合成任务（最短路径）和单一模型架构（Phi3），结论能否推广到自然语言推理、更复杂算法（如排序、SAT）、更大规模模型尚需验证。
- **缺乏机制解释**：未深入分析模型内部（如注意力模式、电路），未能解释为何DFS轨迹更易学习。
- **训练方法局限**：仅基于监督学习（next-token prediction），未探索强化学习（如RLHF）或课程学习等可能改变偏差的训练范式。
- **任务特殊性**：最短路径问题在自定义token语言中表示，与自然语言存在差异，可能引入特定偏差。
- **算力细节不完整**：未明确给出总训练GPU小时数，不利于能耗和效率评估。

（完）
