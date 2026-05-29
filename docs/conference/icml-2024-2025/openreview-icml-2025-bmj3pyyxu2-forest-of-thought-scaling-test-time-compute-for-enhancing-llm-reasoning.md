---
title: "Forest-of-Thought: Scaling Test-Time Compute for Enhancing LLM Reasoning"
title_zh: 思维森林：扩展测试时计算以增强大语言模型推理
authors: "Zhenni Bi, Kai Han, Chuanjian Liu, Yehui Tang, Yunhe Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=BMJ3pyYxu2"
tags: ["query:ns-xai"]
score: 7.0
evidence: 提出思维森林框架进行多树推理以提升逻辑问题解决能力
tldr: 本文提出思维森林框架，集成多个推理树进行集体决策，并采用稀疏激活策略选择最相关的推理路径，克服了单次推理无法回溯的局限，显著提高了复杂逻辑问题的解决精度和效率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 838, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 810, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1744, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 893, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 800, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bmj3pyyxu2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 1097, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 886, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 877, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 885, \"height\": 530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 859, \"height\": 1057, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 870, \"height\": 626, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 868, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 834, \"height\": 1448, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 855, \"height\": 1630, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 858, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 378, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bmj3pyyxu2/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 414, \"height\": 271, \"label\": \"Table\"}]"
motivation: 现有思维链和思维树方法只进行一次推理，无法修正错误路径，影响准确性。
method: 构建多个推理树并利用集体决策，采用稀疏激活选择最佳路径。
result: 提升了复杂逻辑问题的推理准确性和效率。
conclusion: FoT通过集成多树推理增强了LLM的推理鲁棒性。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable abilities across various language tasks, but solving complex reasoning problems remains a significant challenge. While existing methods, such as Chain-of-Thought (CoT) and Tree-of-Thought (ToT), enhance reasoning by decomposing problems or structuring prompts, they typically perform a single pass of reasoning and may fail to revisit flawed paths, compromising accuracy. To address this limitation, we propose a novel reasoning framework called Forest-of-Thought (FoT), which integrates multiple reasoning trees to leverage collective decision-making for solving complex logical problems. FoT employs sparse activation strategies to select the most relevant reasoning paths, improving both efficiency and accuracy. Additionally, we introduce a dynamic self-correction strategy that enables real-time error correction, along with consensus-guided decision-making strategies to optimize both correctness and computational resources. Experimental results demonstrate that the FoT framework, combined with these strategies, significantly enhances the reasoning capabilities of LLMs, enabling them to solve complex tasks with greater precision and efficiency.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有的大语言模型（LLM）推理增强方法（如Chain-of-Thought、Tree-of-Thought、Graph-of-Thought）通常只进行一次完整的推理过程，无法在发现错误后回溯或修正路径，导致复杂逻辑问题中准确率受限。
- **核心问题**：如何通过扩展测试时计算（test-time compute），让LLM能够像人类一样从多个角度反复验证和修正推理，从而提升复杂问题求解的精度和鲁棒性。
- **整体含义**：本文提出**思维森林（Forest-of-Thought, FoT）**框架，通过集成多个推理树（森林）进行集体决策，结合稀疏激活、动态自校正和共识引导的决策策略，显著增强LLM在数学和逻辑推理任务上的性能。

## 2. 方法论

### 核心思想
- **多树集成**：构建 \( n \) 个独立的推理树（如ToT或MCTSr），每个树从不同初始视角或增强输入出发进行推理，通过集体智慧弥补单个树的不足。
- **稀疏激活**：对每个树的中间输出进行质量评估（基于评分函数或有效性验证），只激活那些持续产生有效输出（\(\phi_i=1\)）的树，无效树提前终止，节省计算资源。
- **动态自校正**：基于模型预测logits分数进行实时质量监控，当分数低于阈值时自动触发校正（可借助数学规则或重新生成）。算法2描述了该过程。
- **输入增强**：从预构建的知识库 \(B\) 中检索与输入最相关的先验知识，拼接后作为树的输入，提供更多上下文线索。
- **共识引导的专家决策（CGED）**：当多个树产生不同答案时，先进行多数投票，若不一致则调用LLM专家进行最终裁决，结合集体一致性和专家判断。

### 关键技术细节与公式
- **稀疏激活条件**：  
  \[
  \phi_i = 
  \begin{cases} 
  1, & \text{if } \forall l, F(s_l) = \text{valid output} \\
  0, & \text{otherwise}
  \end{cases}
  \]  
  其中 \(s_l\) 为第 \(l\) 层的输出，\(F\) 为有效性验证函数。

- **输入增强检索**：  
  \[
  i_{\max} = \arg\max_i \text{Sim}(x, B_i), \quad x = B_{i_{\max}} \oplus x
  \]  
  选取与 \(x\) 最相似的样本进行拼接。

- **动态自校正**：计算分数 \(score_i = p_\theta(score_i | s_i, x)\)，低于阈值则触发校正（通过数学规则 \(F\) 或重新采样 \(p_\theta\)）。

- **CGED决策**：先对激活树的结果进行多数投票，若分歧则LLM专家基于推理过程选择最准确答案。

### 算法流程（文字说明）
- 算法1：遍历 \(n\) 个推理树，对每个树执行：输入增强 → 推理得到结果 \(s_i\) 及激活指示 \(\phi_i\) → 动态自校正得到 \(s'_i\) → 若 \(\phi_i=1\) 则加入结果集 → 最终调用CGED策略从结果集中选出最终答案。
- 算法2：对每个结果计算得分，若低于阈值则利用数学规则或重新生成进行校正。

## 3. 实验设计

### 使用的数据集
| 数据集 | 类型 | 规模/特点 |
|--------|------|-----------|
| **Game of 24** | 算术推理（24点游戏） | 95个测试问题（去除重复和不可解） |
| **GSM8K** | 小学数学文字题 | 标准benchmark（约8.5K训练，1.3K测试） |
| **MATH** | 高中竞赛数学 | 含MATH500子集及AIME 2024（奥赛级） |

### 对比方法
- **基础方法**：IO、CoT、CoT-SC、GoT、ToT、BoT、XoT、MCTSr等。
- **最强基线**：rStar-Math（7B SLM+7B PPM）、GPT-4o、QwQ-32B等。
- **FoT变体**：基于不同推理树（ToT或MCTSr）、不同子树数量（n=2,4,8等）。

### 评估指标
- 成功率（Game of 24）/ 准确率（GSM8K, MATH, AIME）。

### 使用的LLM后端
- Llama3-8B-Instruct、Mistral-7B、GLM-4-9B、Qwen2.5-Math-7B-Instruct、QwQ-32B-preview。

## 4. 资源与算力

- **原文未明确说明**：未报告使用的GPU型号、数量、训练时长等具体算力信息。仅在实验部分提到采样温度（0.95）等超参数。因此无法评估计算成本。

## 5. 实验数量与充分性

### 实验组数
- **Game of 24**：消融实验（表1，5种配置）、与ToT扩展对比（图5）、与多种基线对比（表2）。
- **GSM8K**：多方法增益分析（图2）、跨模型缩放律对比（图3）、决策策略对比（表12）、阈值调优（表13）。
- **MATH**：按难度分层对比（图4）、不同子树数量结果（表4）。
- **AIME 2024**：与rStar-Math等对比（表4）。
- **停止策略**：三种策略对比（表3）。
- **总实验组数**：约10+组，覆盖主实验、消融、超参数、跨模型等。

### 充分性与公平性
- **优点**：覆盖多个任务（算术、数学文字题、竞赛题）、多种模型（7B-32B）、多种基线（从简单IO到SOTA rStar-Math），消融实验充分验证各组件贡献。
- **不足**：
  - 未提供多次运行的标准差或置信区间，偶然性未知。
  - 未在更大规模模型（如70B或GPT-4）上验证FoT本身（仅作为对比基线）。
  - Game of 24数据集较小（95题），结论泛化性有限。
  - 未开展推理代价与精度的Pareto前沿分析（虽在图5有部分比较，但不全面）。

## 6. 主要结论与发现

1. **FoT显著提升推理准确性**：在Game of 24上，FoT（8子树）达到96.84%成功率，远超ToT（74%）和BoT（82.4%）。
2. **缩放定律**：随着激活子树数量增加，准确率单调提升，且在不同模型（Llama、Mistral、GLM）上均成立，表明FoT有效利用测试时计算。
3. **各组件的有效性**：
   - 自校正将准确率从10.58%提升至60.24%。
   - 输入增强进一步提升至77.98%。
   - 稀疏激活在不降低准确率的情况下减少LLM调用次数（32.32→26.99）。
4. **CGED优于多数投票和专家单独决策**：在子树数≥3时，CGED持续获得更高准确率。
5. **跨任务鲁棒性**：在GSM8K、MATH、AIME上均超越或持平最先进方法（如rStar-Math、GPT-4o）。

## 7. 优点

- **创新性框架**：首次将“森林”概念引入LLM推理，通过多树集成+稀疏激活有效平衡推理广度与深度。
- **动态自校正机制**：基于实时分数触发修正，比固定迭代次数更灵活，且融入数学规则确保可解释性。
- **高效的决策策略（CGED）**：结合集体一致性与专家判断，避免单一投票的局限性。
- **广泛的实验验证**：覆盖多种任务、模型和基线，消融实验清晰展示各组件贡献，缩放律验证为未来优化提供方向。
- **无需微调**：FoT完全基于冻结LLM的推理时计算扩展，易于迁移。

## 8. 不足与局限

- **计算成本未量化**：未报告GPU小时数或内存占用，难以判断实际效率；稀疏激活虽减少调用次数，但每棵树内部仍需多次LLM推理。
- **数据集规模有限**：Game of 24仅95题，统计显著性存疑；AIME 2024题目数少（30题），结果波动较大。
- **模型规模覆盖不足**：仅在≤32B参数模型上测试，未在更大模型（如70B/180B）上验证FoT是否依然有效或存在边际递减。
- **超参数敏感**：自校正阈值（0.5为最优）需要针对任务调优，泛化性未知；稀疏激活的评分函数依赖于手工设计。
- **缺乏误差分析**：未讨论失败案例的类型（如计算错误、逻辑跳跃、知识缺失），无法针对性改进。
- **公平性风险**：FoT多次调用同模型，可能放大模型固有的偏见；若知识库\(B\)有偏差，输入增强可能引入噪声。

（完）
