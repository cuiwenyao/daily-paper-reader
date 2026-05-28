---
title: "On the Bias of Next-Token Predictors Toward Systematically Inefficient Reasoning: A Shortest-Path Case Study"
title_zh: 下一个词预测器偏向系统性低效推理：最短路径案例研究
authors: "Riccardo Alberghi, Elizaveta Demyanenko, Luca Biggio, Luca Saglietti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=l8razJItEy"
tags: ["query:ns-xai"]
score: 4.0
evidence: 下一个词预测器在最短路径任务中偏向低效推理
tldr: 该论文在最短路径任务中系统研究了大语言模型推理效率偏差，发现基于下一个词预测的训练目标会导致模型偏向低效推理链。通过对比动态规划最优轨迹的CoT，揭示了冗余推理的根源，为改进推理设计提供了方向。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1167, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1373, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1393, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1175, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1178, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1398, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 953, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 567, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 919, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 1425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1315, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1343, \"height\": 152, \"label\": \"Table\"}]"
motivation: LLM推理链存在系统性冗余。
method: 在分层图上训练Transformer并比较不同轨迹。
result: 下一个词预测导致非最优推理链。
conclusion: 揭示了训练目标与推理效率的关系。
---

## Abstract
Recent advances in natural language processing highlight two key factors for improving reasoning in large language models (LLMs): (i) allocating more test-time compute tends to help on harder problems but often introduces redundancy in the reasoning trace, and (ii) compute is most effective when reasoning is systematic and incremental, forming structured chains of thought (CoTs) akin to human problem-solving. To study these factors in isolation, we introduce a controlled setting based on shortest-path tasks in layered graphs. We train decoder-only transformers on question–trace–answer triples using a custom tokenizer, comparing models trained on optimal bottom-up dynamic programming traces with those trained on longer, valid traces involving backtracking. Surprisingly, under the same training-token budget, the latter models generalize better to unseen graphs. This benefit is not due to length alone—injecting arbitrary redundancy into reasoning traces fails to help and can even hurt performance. Instead, we find that generalization correlates with the model's confidence in next-token prediction, suggesting that long, coherent, and locally incremental traces make the training signal easier to optimize.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前大语言模型（LLMs）的推理能力提升依赖于两个关键因素：(i) 增加测试时计算量（test-time compute）通常有助于解决更难的问题，但常引入冗余推理步骤；(ii) 当推理是系统化和增量式时，计算效率最高，类似于人类解决问题的思维链（CoT）。然而，关于推理效率的偏差与训练目标（下一个词预测）之间的关系尚未被系统研究。
- **核心问题**：下一个词预测的归纳偏好是否会导致模型偏向系统性低效的推理？特别是，在最短路径任务中，训练于动态规划（DP）最优轨迹 vs. 更具回溯性的低效轨迹，哪种能带来更好的泛化？
- **整体含义**：论文通过受控实验揭示了反直觉现象：训练于低效但结构化的推理轨迹（如深度优先搜索 DFS）比训练于全局最优的 DP 轨迹泛化更好。这说明训练目标（next-token prediction）的偏差倾向于更可预测、局部增量式的轨迹，而非最短或最优的轨迹。

## 2. 论文提出的方法论

- **核心思想**：在一个合成的最短路径任务（分层有向无环图，DAG）上，训练 decoder-only transformer 模型。通过控制推理轨迹的效率参数 η，生成不同性质的 CoT（链式思考）。比较不同轨迹类型对模型泛化和学习效果的影响。
- **关键技术细节**：
  - **图生成**：参数 {L（最大层数）=7, K（每层最大节点数）=6, C（最大边成本）=5, p_e（边连接概率）=0.6}。源和目标节点各一个，内部层节点数随机。
  - **自定义分词器**：用特殊标记（BoS, EoS, BoT, EoT, 层标签, 节点标签, 成本值, 分隔符等）将问题、轨迹、答案编码为 token 序列。
  - **轨迹生成算法**：使用基于优先级的探索队列，优先级权重与 exp(−η·(layer+1)) 成比例。η>0 偏向短路径优先（层序，如 DP），η<0 偏向长路径优先（深度优先，如 DFS）。η=0 则完全随机。所有轨迹均满足最优性准则（正确性、增量构建、只使用当前最优部分路径等）。
  - **模型**：Phi3 小型语言模型，3 层 transformer，12 个注意力头，768 维隐藏层，约 28.5M 参数。从头训练，下一个词预测目标。训练时 masking 掉问题和 PAD token 的损失，仅对轨迹和答案计算 loss。
  - **训练配置**：AdamW 优化器，学习率 2e-5 常数，权重衰减 0.1，batch size 16384 tokens（剔除 PAD），上下文长度 4096（有轨迹）或 256（无轨迹）。训练 epoch 直到测试损失稳定。
- **算法流程（文字说明）**：
  1. 随机生成分层 DAG，确保至少有一条合法路径。
  2. 根据 η 值生成探索轨迹：维护队列和最佳成本/路径字典。每一步从队列中选择下一节点，权重与层数相关。若找到更优路径则更新，并将该节点的后继加入队列。持续到队列为空。
  3. 将图（问题）、轨迹、答案拼接为 token 序列。
  4. 用自定义分词器转换为整数 token。
  5. 训练 transformer 以预测下一个 token（仅轨迹和答案部分参与损失）。

## 3. 实验设计

- **数据集/场景**：合成分层 DAG，参数固定为 L=7, K=6, C=5, p_e=0.6。训练集和测试集各包含唯一图实例，比例 9:1。训练 token 预算有 32M 和 128M 两种规模，以及固定图数量（约 200K）的条件。
- **Benchmark**：主要指标是 **Answer Accuracy**（正确性：路径可行、长度正确、成本最优、声明一致）和 **Next-Token Confidence**（拓扑概率）。辅助指标包括轨迹中步骤数、重复步骤、语法错误等。
- **对比的方法**：
  - **无轨迹**（仅 question→answer）作为基线。
  - **η = +5 (DP)**：最优 DP 轨迹（最短层序遍历）。
  - **η = 0**：均匀随机探索。
  - **η = -5 (DFS)**：深度优先搜索（最长迹）。
  - **η = +5 (DR)**：确定性重复（每个步骤立即重复一次）。
  - **η = +5 (RR)**：随机重复（每个步骤有 1/2 概率重加入队列）。
- **额外实验**：不同采样温度（T=0, 0.2, 0.5, 1.0, 1.5, 2.0），模型深度消融（3 vs 6 层），不同训练 token 预算（16M, 32M, 128M）。

## 4. 资源与算力

- **模型规模**：Phi3 small，28.5M 参数，FP16 精度，显存占用约 14GB。
- **GPU 类型**：Nvidia A100 80GB 或 RTX 4090 24GB，搭配 32 CPU 核心。
- **训练时长**：论文未明确给出每个实验的具体训练时长，但指出所有运行均使用上述硬件。考虑到模型较小，训练 epochs 通常为 20-40，预计单次运行在数小时量级。
- **备注**：论文未提供总 GPU 小时数或能耗数据。

## 5. 实验数量与充分性

- **实验组数**：至少 6 种主要轨迹类型（无轨迹、η=+5, 0, -5, DR, RR），每种在多种 token 预算下训练，并重复 5 个随机种子。此外包括温度扫描、模型深度消融、学习率调度对比。总数约 20-30 组独立训练实验。
- **充分性判断**：
  - **优点**：实验设计系统，控制了 token 预算、图分布、种子，结果稳定且可复现。误差棒基于 5 个种子，统计显著。消融实验覆盖了冗余注入、温度、模型大小等关键维度。
  - **不足**：仅使用单一模型架构（Phi3）和单一任务（最短路径）。自然语言任务或其他算法（如排序、定理证明）未验证。无监督/强化学习训练范式未探索。另外，图参数固定，未探索不同难度（如更大 K 或 L）下的泛化。

## 6. 论文的主要结论与发现

1. **CoT 至关重要**：直接问题-答案训练无法泛化到较大图，而 CoT 训练显著提升泛化。
2. **结构比全局最优更重要**：训练于低效 DFS 轨迹（η=-5）的模型，在相同 token 预算下泛化优于训练于 DP 轨迹（η=+5）的模型，尽管 DFS 轨迹平均长 75%，且看到更少的独特图例。
3. **冗余注入无益**：确定性重复（DR）或随机重复（RR）添加冗余步骤反而略微降低性能，显示仅增加长度无效。
4. **用于学习预测能力的学习信号可预测性**：模型在低效 DFS 轨迹上的 next-token confidence 更高，说明长且局部增量式的轨迹更容易优化。
5. **采样温度可正则化冗长倾向**：对于随机性较强的轨迹（η=0, RR），非零温度有助于让生成轨迹长度更接近训练分布，提高准确率。
6. **模型倾向于产生更长轨迹**：即使训练于 η=0，零温度下模型初期也产生类似 DFS 的长轨迹，需要更多 epoch 才回归正确长度。

## 7. 优点

- **控制力强**：合成任务允许精确控制轨迹效率、长度、冗余结构，排除自然语言中混杂因素。
- **揭示反直觉现象**：明确指出下一个词预测目标的内在偏差，为理解 LLM 推理冗余提供机理视角。
- **实验设计严谨**：固定 token 预算、多种子重复、对比适当基线（无轨迹、随机、冗余等）。
- **与现有文献对话**：结论与 CoT 结构比内容重要、置信度压缩冗余 CoT 等近期工作一致。

## 8. 不足与局限

- **任务单一**：仅限合成最短路径任务，自然语言推理或其他算法任务（排序、SAT）可能不同。
- **模型规模有限**：仅 28.5M 参数，不能直接推广到数十亿参数模型。
- **图分布固定**：未探索更大 L、K 或不同边成本分布下的泛化。
- **缺乏机制分析**：论文指出未来可用机械可解释性分析模型内部电路，但未深入。
- **训练范式限制**：仅使用监督学习，未尝试强化学习或课程学习来引导更高效推理。
- **置信度指标单一**：next-token confidence 虽有效，但可能受 softmax 输出分布影响，未与其他不确定性估计对比。

（完）
