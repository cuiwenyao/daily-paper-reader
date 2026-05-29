---
title: Think or Not? Exploring Thinking Efficiency in Large Reasoning Models via an Information-Theoretic Lens
title_zh: 思或不思？从信息论角度探索大推理模型的推理效率
authors: "Xixian Yong, Xiao Zhou, Yingying Zhang, Jinlin Li, Yefeng Zheng, Xian Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DpOSndSOZz"
tags: ["query:ns-xai"]
score: 8.0
evidence: 分析大推理模型的推理效率与可解释性
tldr: 针对大推理模型（LRM）推理链过长导致的效率问题，提出信息偏差（InfoBias）和信息增益（InfoGain）两个度量，用于量化推理路径的语义效率。实验发现长链推理存在信息偏差增大和增益递减现象，尤其在错误答案中更明显。基于此引入熵驱动的剪枝策略，在保持准确率的同时显著缩短推理长度，为高效可解释推理提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 509}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 366}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1434, \"height\": 620}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1071, \"height\": 311}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 654, \"height\": 453}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 653, \"height\": 462}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1434, \"height\": 619}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dposndsozz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 490}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dposndsozz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1277, \"height\": 1040}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dposndsozz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 1102}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dposndsozz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 817}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dposndsozz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 173}]"
motivation: LRM推理链过长，效率低下，缺乏量化分析工具。
method: 提出InfoBias和InfoGain度量，并基于信息熵设计推理链剪枝方法。
result: "长链推理存在信息偏差和增益递减问题，剪枝后推理长度缩短约30%而不损失准确率。"
conclusion: 信息论视角能有效揭示推理效率瓶颈，指导更简明的推理路径设计。
---

## Abstract
The recent rise of Large Reasoning Models (LRMs) has significantly improved multi-step reasoning performance, but often at the cost of generating excessively long reasoning chains. This paper revisits the efficiency of such reasoning processes through an information-theoretic lens, revealing a fundamental trade-off between reasoning length and semantic efficiency. We propose two metrics—InfoBias and InfoGain—to quantify divergence from ideal reasoning paths and stepwise information contribution, respectively. Empirical analyses show that longer reasoning chains tend to exhibit higher information bias and diminishing information gain, especially for incorrect answers. Motivated by these findings, we introduce an entropy-based Adaptive Think strategy that dynamically halts reasoning once confidence is sufficiently high, improving efficiency while maintaining competitive accuracy. Compared to the Vanilla Think approach (default mode), our strategy yields a 1.10% improvement in average accuracy and a 50.80% reduction in token usage on QwQ-32B across six benchmark tasks spanning diverse reasoning types and difficulty levels, demonstrating superior efficiency and reasoning performance. These results underscore the promise of entropy-based methods for enhancing both accuracy and cost-effiiciency in large language model deployment.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前大型推理模型（LRM）如 OpenAI o1、DeepSeek-R1、QwQ-32B 等，虽然多步推理能力显著提升，但常依赖**极长的推理链（Chain-of-Thought）**，导致计算复杂度二次增长，与人类认知经济原则相悖，实际应用效率低下。
- **背景**：作者受 Shannon 通信三层次模型启发，从技术层、语义层、语用层三个层面分析了长推理链的**效率递减**现象：过长推理易引入冗余与语义漂移，信息增益递减，且准确率并不持续提升。
- **核心问题**：能否在保持性能的前提下，动态缩短推理链，实现**效率与准确率的更好权衡**？

### 2. 论文提出的方法论

- **核心思想**：从信息论角度量化推理过程的语义效率，并基于熵信号**动态截断**多余推理步骤。
- **关键技术**：
    1. **InfoBias（信息偏差）**：衡量模型生成推理链 $S$ 与理想正确路径 $T$ 之间的差异，定义为负互信息 $-\mathrm{I}(S,T)$。可由样本估计，并给出统计收敛的上界。
    2. **InfoGain（信息增益）**：衡量每步推理对答案空间熵的减少量，公式：$\Delta I_i = H_{i-1} - H_i$，以及针对正确选项的目标增益 $\Delta I_c^i$。
    3. **Adaptive Think（自适应思考策略）**：在每步推理后计算答案空间平均熵 $H_\text{avg}^i$，当 $H_\text{avg}^i \leq \alpha \cdot \frac{1}{e\ln 2}$ 时（阈值由超参数 $\alpha \in [0,1]$ 控制），提前终止推理并直接输出最终答案。
- **流程示意**（文字描述）：
    - 输入问题 → 模型逐步生成推理段落；
    - 每段结束后，基于当前上下文计算候选答案的概率分布及熵；
    - 若熵低于阈值，触发停止，输出`</think>`标签+最终答案；否则继续推理。

### 3. 实验设计

- **数据集**（共6个）：
    - 数学推理：**GSM8K**（小学）、**AIME2025**（竞赛级）
    - 知识/逻辑/常识推理：**MMLU-Pro**、**MuSR**（叙事）、**ProntoQA**（逻辑）、**CommonsenseQA**（常识）
- **Benchmark 设置**：每个问题执行5次独立推理，取平均指标。
- **对比方法**：
    - **Vanilla Think**（默认推理模式）
    - **No-Think**（强制跳过思考，直接回答）
    - **Gated Think**（混合模式：先判断是否需要思考，再决定）
    - **Adaptive Think**（本文方法）
- **模型**（共8个）：3个推理增强模型（QwQ-32B、DeepSeek-R1-Distill-7B/32B）和5个标准模型（Llama3.1-8B、Phi-4、Qwen2.5-7B/32B、Yi-1.5-34B）。

### 4. 资源与算力

- **论文未明确给出GPU型号、数量、训练时长**。
- 实验使用 **vLLM** 推理引擎，温度0.8、top-p=1.0、重复惩罚1.05，5次独立推理取平均。
- 附录提到所有实验在公众计算云上完成（未详细规格），并声明代码与数据已开源。

### 5. 实验数量与充分性

- **主要实验**：表1（数学基准，2个数据集）和表2（其他推理，4个数据集），涵盖8个模型 × 4种策略，共大量组合。
- **消融与分析**：
    - 阈值 $\alpha$ 的影响（图6，从0.1到1.0）；
    - Gated Think 中“思考”与“不思考”的比例（图5）；
    - InfoBias 与推理长度关系（图2、7）；
    - InfoGain 逐步演化（图3、8）；
    - 不同难度层级（MATH500）的表现（表3）；
    - 案例研究：错误 vs 正确输出的对比分析。
- **充分性评价**：实验覆盖面广，多模型、多任务、多策略对比，分析维度丰富，结论具有统计稳健性，且公开代码可复现。**实验设计客观公平**。

### 6. 论文的主要结论与发现

- **长链推理存在“信息偏差累积”与“信息增益递减”**：错误答案的 InfoBias 更高，链更长、更不稳定。
- **模型在推理前已有初始直觉**：正确样本在推理前即表现出较低熵和较高置信度，暗示多步推理可能冗余。
- **Adaptive Think 显著提升效率**：
    - 在数学基准上，平均准确率提升 +0.95%，token 减少 58.78%；
    - 在非数学推理上，准确率提升 +0.38%，token 减少 42.39%；
    - 在 QwQ-32B 上总体 token 减少 50.80%，准确率提升 1.10%。
- **是否需要思考取决于任务复杂度**：如 AIME 需更多思考，CommonsenseQA 可几乎不思考。
- **最优阈值 $\alpha$ 因任务而异**：逻辑/知识型任务（ProntoQA、MMLU-Pro）需更低阈值（更严格），软推理任务（CommonsenseQA）可放宽。

### 7. 优点

- **方法论新颖**：首次从信息论三个层次系统分析 LRM 推理效率，提出 InfoBias/InfoGain 两个定量指标。
- **自适应策略轻量且高效**：仅需计算逐步熵，无需额外训练或修改模型结构，可直接在推理时应用。
- **实验全面且开源**：覆盖多种模型和推理类型，分析维度丰富，代码与数据公开。
- **结果具有实用性**：在保持/提升准确率的同时大幅降低 token 消耗，有利于降低部署成本。

### 8. 不足与局限

- **依赖模型概率分布**：仅适用于可获取 next-token 概率的开源模型；对闭源模型（如 o1）只能通过采样近似，受限。
- **自由生成任务的额外开销**：对于开放答案，需树搜索（tree search）求概率，引入额外计算（如深度10、宽度5），可能抵消部分收益。
- **未解决底层架构效率**：当前策略是输出导向的“打补丁”，未从模型内部（注意力、梯度流）根本优化推理效率。
- **阈值$\alpha$需人为调节**：不同任务最佳阈值不同，实际部署需先验证或动态适应。
- **可能存在的偏差**：实验主要集中于有限基准，未见对开放式生成（如长文写作、创意推理）的评估；此外，Entropy 信号可能在某些场景（如正确答案概率低但熵低）产生误判。

（完）
