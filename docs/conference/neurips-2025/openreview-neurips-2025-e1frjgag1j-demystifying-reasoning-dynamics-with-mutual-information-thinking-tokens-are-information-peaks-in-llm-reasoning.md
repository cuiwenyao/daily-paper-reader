---
title: "Demystifying Reasoning Dynamics with Mutual Information: Thinking Tokens are Information Peaks in LLM Reasoning"
title_zh: 用互信息解密推理动态：思考token是LLM推理中的信息峰值
authors: "Chen Qian, Dongrui Liu, Haochen Wen, Zhen Bai, Yong Liu, Jing Shao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=E1FrjgaG1J"
tags: ["query:ns-xai"]
score: 7.0
evidence: 互信息分析LLM推理动态
tldr: 该论文从信息论角度研究大型推理模型（LRM）的内部推理机制，追踪中间表示与正确答案之间的互信息（MI）变化，发现MI在特定生成步骤出现突然峰值。理论分析表明MI增加时预测误差降低。这些MI峰值揭示了推理过程中的关键阶段，有助于理解LRM的推理行为。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1386, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1389, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1478, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 708, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1455, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1310, \"height\": 2300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1229, \"height\": 2357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1315, \"height\": 2335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1242, \"height\": 2368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1314, \"height\": 2338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1242, \"height\": 2373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1316, \"height\": 2335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1243, \"height\": 2377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1309, \"height\": 2342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1210, \"height\": 2344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1311, \"height\": 2327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1234, \"height\": 2360, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1468, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 779, \"height\": 283, \"label\": \"Table\"}]"
motivation: LRM推理过程的内在机制尚不清楚。
method: 计算中间表示与正确答案的互信息，追踪其随推理步骤的变化。
result: 观察到互信息峰值出现在推理关键步骤，且与预测准确率正相关。
conclusion: 互信息峰值是LRM推理过程中的重要信号，有助于揭示推理机制。
---

## Abstract
Large reasoning models (LRMs) have demonstrated impressive capabilities in complex problem-solving, yet their internal reasoning mechanisms remain poorly understood.
In this paper, we investigate the reasoning trajectories of LRMs from an information-theoretic perspective. 
By tracking how mutual information (MI) between intermediate representations and the correct answer evolves during LRM reasoning, we observe an interesting MI peaks phenomenon: the MI at specific generative steps exhibits a sudden and significant increase during LRM's reasoning process. 
We theoretically analyze such phenomenon and show that as MI increases, the probability of model's prediction error decreases.
Furthermore, these MI peaks often correspond to tokens expressing reflection or transition, such as "Hmm", "Wait" and "Therefore," which we term as the thinking tokens.
We then demonstrate that these thinking tokens are crucial for LRM's reasoning performance, while other tokens has minimal impacts.
Building on these analyses, we propose two simple yet effective methods to improve LRM's reasoning performance, by delicately leveraging these thinking tokens.
Overall, our work provides novel insights into the reasoning mechanisms of LRMs and offers practical ways to improve their reasoning capabilities.
The code is available at \url{https://github.com/ChnQ/MI-Peaks}.

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **动机**：大型推理模型（LRM，如DeepSeek-R1、QwQ）在复杂推理任务中表现出色，但其内部推理机制仍然是一个“黑箱”。现有研究多关注输入输出关系，缺乏对推理过程动态的理解。
- **背景**：信息论为分析表示之间的关系提供了理论工具；已有工作发现某些“关键token”能显著影响模型行为，但LRM在推理过程中是否存在类似的“关键推理步骤”尚不清楚。
- **核心问题**：能否通过信息论方法揭示LRM推理过程中表示与正确答案之间的信息关系？这些信息关系是否与推理性能相关？能否利用这些发现改进推理？
- **整体含义**：论文从互信息（MI）视角揭示了LRM推理中一个新颖现象——MI峰值，并发现对应的“思考token”（如“Wait”、“Hmm”）对推理至关重要，进而提出两种无需训练的改进方法。这项工作为理解LRM推理机制提供了新视角，并为推理增强提供了实践路径。

## 2. 论文提出的方法论

### 核心思想
- **信息论框架**：在LRM自回归生成过程中，计算每个生成步骤的隐藏表示与正确答案表示之间的互信息（MI），形成MI随时间演化的序列。
- **MI峰值定义**：基于四分位距（IQR）识别MI序列中的异常高值点，作为MI峰值。
- **思考token识别**：将MI峰值对应的表示通过输出投影矩阵解码到token空间，发现这些token多为反思/过渡性词汇（如“So”、“Hmm”、“Wait”），称之为“思考token”。
- **理论关联**：给出两个定理，证明表示序列与正确答案的累积MI越高，预测误差的上下界越紧，从而MI峰值有助于降低错误概率。

### 关键技术细节
- **MI估计**：使用希尔伯特-施密特独立性准则（HSIC）近似MI，采用高斯核函数，带宽通过网格搜索在[50,400]间选择。
- **表示提取**：从最后一层提取每个生成token的隐藏表示ht，以及通过输入正确答案y得到表示hy。
- **MI峰值判定**：mt > Q3 + 1.5×IQR 的步骤被视为峰值（τ=1.5）。
- **思考token解码**：Softmax(W_out ht + b)后取最大概率token，聚合所有峰值token进行频率分析。
- **两种应用方法**：
  - **Representation Recycling (RR)**：在生成到思考token时，将其在中间层（通常为中层或高层）重新输入同一Transformer块一次，使得模型对该表示进行更深入加工。
  - **Thinking Token based Test-time Scaling (TTTS)**：额外分配token预算时，追加一个思考token（如“So”），强制模型继续推理，重复此过程直至预算用完。

### 公式/算法流程（文字说明）
- Theorem 1 和 Theorem 2 给出了预测误差pe与累积MI之间的不等式关系，证明高MI有助于降低误差。
- RR算法：在推理过程中检测到思考token后，将该位置的表示hℓ*再次输入第ℓ*层，得到h'ℓ* = TFℓ*(hℓ*)，然后继续后续层前向传播。
- TTTS算法：当需要更多推理时，从预定义思考token列表中选择一个，追加到当前输出末尾，使模型继续自回归生成。

## 3. 实验设计

### 数据集
- **MI轨迹分析**：MATH数据集训练集（约12k道竞赛级数学题），随机采样100个样本计算MI序列。
- **推理性能评估**：GSM8K（简单）、MATH500（中等）、AIME24（困难）。此外，泛化性验证使用GPQA和MedQA。
- **token分析**：基于MATH训练集聚合MI峰值token。

### Benchmark
- 对比LRM：DeepSeek-R1-Distill系列（7B/8B/14B/32B/70B）和QwQ-32B。
- 对比非推理LLM：Llama-3.1-8B、Qwen2.5-Math-7B、Qwen2.5-14B、Qwen2.5-32B、Llama-3.3-70B-Inst。

### 对比方法
- **思考token抑制实验**：将思考token概率置零（逐类抑制），对比随机抑制相同数量的非思考token。
- **RR**：与原始LRM比较，无其他复杂度方法。
- **TTTS**：与原始LRM在相同token预算下比较。

### 实验概览
- MI轨迹可视化（每个模型展示100个样本）。
- Token频率分布统计。
- 量化指标：Mean、Std、AOM（反映MI峰值强度）。
- 抑制实验：不同抑制数量（0~20个token）下的准确率变化。
- RR实验：在GSM8K、MATH500、AIME24上的准确率。
- TTTS实验：逐步增加token预算（如从1024到8192），记录准确率曲线。
- 泛化性实验：GPQA和MedQA上的AOM对比。

## 4. 资源与算力

- **GPU型号与数量**：4块NVIDIA A100 GPU。
- **训练时长**：文中未明确说明每个实验的具体耗时，仅提及所有实验在4块A100上进行。由于方法是训练-free的，时间复杂度主要来自推理和MI计算。
- **其他**：模型均来自公开检查点，无需额外训练资源。

## 5. 实验数量与充分性

- **数量**：约10组主要实验（MI轨迹、token分布、抑制、RR、TTTS、泛化性），每组包含多个子实验（不同模型、不同基准）。总共超过50条实验曲线/表格。
- **充分性**：
  - 覆盖了从7B到70B的多种LRM尺度，以及对应的非推理LLM，具有代表性。
  - 在三个难度递进的数学基准上评估，并在两个非数学领域（GPQA、MedQA）上验证泛化性，较为全面。
  - 抑制实验设计了不同抑制数量，并做了随机对照，结论清晰。
  - RR和TTTS方法简单，没有引入外部模块，对比公平。
- **客观性**：实验固定温度=0确保可复现；使用公开评估框架；统计指标（IQR、Mean、Std）定义明确。但未提供误差线或多次运行的标准差，可能受随机性影响。

## 6. 论文的主要结论与发现

1. **MI峰值现象**：在LRM推理过程中，某些步骤的表示与正确答案的MI会突然显著升高，这些峰值稀疏且非均匀分布。
2. **思考token是关键**：MI峰值对应的token大多是反思/过渡性词汇（如“So”、“Hmm”、“Wait”），它们的生成对推理性能至关重要——抑制这些token会显著降低准确率，而抑制其他token影响很小。
3. **理论支撑**：累积MI越高，预测误差的上下界越紧，解释MI峰值为何有益。
4. **非推理LLM表现弱**：对应的基座模型（如Llama-3.1-8B）MI峰值不明显，整体MI也更低，表明MI峰值可能来源于推理增强训练。
5. **方法有效**：Representation Recycling和Thinking Token based Test-time Scaling均能在多个基准上持续提升LRM的推理准确率，尤其在复杂问题（AIME24）上提升显著。

## 7. 优点

- **视角新颖**：首次从信息论动态角度系统分析LRM推理过程，揭示了“MI峰值”这一有趣现象，为理解模型内部机制提供了量化工具。
- **理论+实验结合**：定理证明与大量实验相互印证，增强了结论的可信度。
- **方法简洁实用**：两种增强方法均为训练-free，无需额外数据或微调，易于复现和集成。
- **可解释性强**：将抽象信息论指标与具体token语义关联，便于直观理解模型在哪些步骤“集中思考”。
- **控制实验设计严谨**：抑制思考token的同时进行了随机抑制对照，排除了数量效应。

## 8. 不足与局限

- **计算开销**：MI计算需要将隐藏表示投影到token空间并计算HSIC，对于长序列（>500 token）可能较慢，实际应用时有限制。
- **粒度局限**：只在token级别分析，未考虑语义块或逻辑步骤粒度的MI，可能遗漏更宏大的结构模式。
- **因果机制未深究**：MI峰值的成因（为何出现在这些位置、如何从训练中涌现）仅初步归因于推理训练，未深入分析其动力学来源。
- **抑制实验非单调性**：文中承认在某些抑制数量下性能反而微升，原因是模型会使用替代表达（如“But wait”），说明抑制攻击的结论需谨慎解释。
- **领域覆盖有限**：除数学外仅在GPQA和MedQA上验证泛化性，未涉及编程、逻辑、常识等更多推理类型。
- **资源与复现细节**：未提供完整超参数和运行时间，部分实现细节（如层选择策略）依赖经验设定。代码已开源但未在文中展示完整文档。
- **潜在偏差风险**：如果思考token被用于强制模型“继续思考”，可能引入循环或错误积累，文中未充分讨论负面影响。

（完）
