---
title: Compositional Causal Reasoning Evaluation in Language Models
title_zh: 语言模型中的组合因果推理评估
authors: "Jacqueline R. M. A. Maasch, Alihan Hüyük, Xinnuo Xu, Aditya V. Nori, Javier Gonzalez"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=OJ3dQNRnsx"
tags: ["query:ns-xai"]
score: 4.0
evidence: 评估语言模型中的组合因果推理
tldr: 语言模型的因果推理和组合推理能力评估缺乏统一框架。本文提出组合因果推理（CCR）评估框架，在数学应用题上系统评估了Llama、Phi、GPT等模型，揭示了多种类型错误模式，为理解大模型推理行为提供了评测工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 841, \"height\": 222, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1735, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 531, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1776, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1781, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 770, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 864, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 894, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 899, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 935, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1259, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1705, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1767, \"height\": 818, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1648, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1063, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1064, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1064, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1598, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1383, \"height\": 974, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1381, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1770, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1778, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1783, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1789, \"height\": 1783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1608, \"height\": 1947, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1793, \"height\": 1594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1604, \"height\": 1911, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1076, \"height\": 1237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oj3dqnrnsx/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1778, \"height\": 768, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-oj3dqnrnsx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oj3dqnrnsx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 1170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oj3dqnrnsx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1074, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oj3dqnrnsx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1772, \"height\": 371, \"label\": \"Table\"}]"
motivation: 需要系统评估语言模型的组合因果推理能力。
method: 构建了基于因果量传播的组合因果推理评估框架。
result: 在主流语言模型上发现了多种分类错误模式。
conclusion: 该框架有效揭示了语言模型在组合因果推理上的能力边界。
---

## Abstract
Causal reasoning and compositional reasoning are two core aspirations in AI. Measuring the extent of these behaviors requires principled evaluation methods. We explore a unified perspective that considers both behaviors simultaneously, termed *compositional causal reasoning* (CCR): the ability to infer how causal measures compose and, equivalently, how causal quantities propagate through graphs. We instantiate a framework for the systematic evaluation of CCR for the average treatment effect and the probability of necessity and sufficiency. As proof of concept, we demonstrate CCR evaluation for language models in the Llama, Phi, and GPT families. On a math word problem, our framework revealed a range of taxonomically distinct error patterns. CCR errors increased with the complexity of causal paths for all models except o1.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：Compositional Causal Reasoning Evaluation in Language Models

## 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：因果推理和组合推理是人工智能追求的两个核心能力。虽然已有工作分别评估了语言模型（LM）的因果推理或组合推理，但缺乏将两者同时考虑的统一评估框架。作者认为，真正的类人AI需要同时具备这两种能力。
- **核心问题**：如何系统而原则性地评估语言模型能否进行**组合因果推理（CCR）**——即推断因果测度如何组合（归纳）以及如何分解（演绎）的能力，本质上等价于推理因果量如何通过图结构传播。
- **整体含义**：该工作为因果推理评估引入了“组合一致性”这一新维度，通过衡量模型在不同等价问题表述下是否给出一致的回答，不仅可以判断模型是否“正确”，还能揭示其如何“错误”。

## 2. 提出的方法论：核心思想、关键技术细节
### 2.1 核心思想
- 将因果推理与组合推理统一为**组合因果推理（CCR）**：定义为在事实和反事实世界中正确推断因果测度的组合与分解。
- 引入**组合一致性**概念：理论等价的组合应被推断为相等。进一步区分为**外部有效性**（估计值与真实值一致）和**内部一致性**（等价量之间估计值一致）。
- 提出**推理者分类学**：有效一致（VC）、有效不一致（VI）、无效一致（IC）、无效不一致（II）。

### 2.2 关键技术细节
- **形式化CCR任务**：三元组 ⟨φ, M, Q⟩，其中 φ 是感兴趣因果测度（如ATE、PNS），M 是结构因果模型（SCM），Q 是一组因果查询。
- **基于割点的图分解**：假设因果DAG含有一个割点（cutpoint），则可以将图分解为若干双连通分量（BCC）。证明在单调性条件下，**概率必要充分性（PNS）**在BCC间可乘性组合（Theorem 5.1）：PNS_XY = ∏ PNS_{Ri,Li}。同样，在线性SCM中，ATE也满足类似乘积形式。
- **交换割树（CCT）**：将原DAG转换为完全有向链式图，抽象掉无关变量，直观展示所有可能的组合路径。CCR要求所有路径的组合结果相等且等于真值。
- **算法1（归纳CCR评估）**：输入CCT、估计值和真值、误差度量θ（如相对绝对误差RAE）。第一步计算每个节点对的量级误差（外部有效性）；第二步对每条从根到叶的路径，计算组合的估计值，并分别评估其外部有效性和内部一致性（与全局估计比较）。

## 3. 实验设计
- **场景与数据集**：基于一个8节点DAG（图4），转化为数学应用题“CandyParty”。每个变量是二元布尔变量，因果函数为逻辑或（单调），满足PNS可识别条件。提示词分为事实型和反事实型两种。
- **Benchmark**：没有直接使用现有基准，而是自建CCR任务。对比了模型在不同提示形式（无CoT vs 带CoT）下的表现。
- **对比方法**：比较了7个LM架构：Llama 2/3/3.1、Llama 3.1 Math、Phi-3-Mini、GPT-4o、o1。对部分模型（Llama 3.1、Llama 3.1 Math、GPT-4o、o1）还测试了链式思维（CoT）提示。
- **评估指标**：相对绝对误差（RAE）；以≥90%的估计RAE≤0.1视为外部有效或内部一致。

## 4. 资源与算力
- 论文明确提到：**单块A100 GPU**用于所有实验。未说明训练时长，因为未进行微调，只进行推理。未说明具体推理总时间。也未说明GPT-4o和o1的推理硬件（由OpenAI提供）。

## 5. 实验数量与充分性
- **实验数量**：
  - 每个模型、每个因果量（共7个量：全局1个、局部5个、组合3个）均进行1000次PNS估计（通过1000组外生变量采样，每组采样5次LM响应后随机抽取1个，重复1000次）。
  - 总共涉及7个模型 × 7个量 × 1000估计 ≈ 49000次PNS计算，每次计算需处理10个LM响应（事实+反事实各5次）。
  - 此外还有CoT变体（4个模型额外评估）。
- **充分性与公平性**：
  - 实验设计系统化，但作者明确指出：这是一项“概念验证”（proof of concept），仅聚焦于一个简单任务（8节点DAG），未在更复杂的图上测试。因此充分性有限。
  - 对不同模型大小、版本、是否带CoT都做了比较，公平性较好。但未进行跨任务泛化测试，也未与其他CCR评估框架（如Cladder）直接对比（因实验设计不同）。

## 6. 主要结论与发现
- **推理者分类**：仅o1模型达到了**有效一致（VC）**；GPT-4o+CoT接近“有效但近不一致”（near-VI）；其他模型均为**无效不一致（II）**。
- **错误随路径复杂化增加**：除o1外，所有模型的RAE随因果路径长度/中介变量数量单调增加。GPT-4o+CoT在有6个中介时误差比3个高10倍以上。
- **CoT的有限帮助**：CoT对GPT-4o帮助最大（从II到近VI），但对Llama系列和o1影响不显著。o1无论是否CoT都表现稳定。
- **内部一致性揭示更深层问题**：仅靠外部有效性可能低估错误。例如GPT-4o+CoT局部量表现好，但全局量（PNS_XY）完全失败，表明它不能正确组合因果信息，类似于“记忆而非综合”。
- **常见失败模式**：数值错误（Llama模型）、未完整推理因果链、错误提取父节点集、逻辑跳跃（GPT-4o+CoT）。
- **模型大小/版本与性能关系**：错误率不随模型大小单调递减，也不随Llama版本单调递减（除全局量外）。

## 7. 优点
- **理论创新**：首次系统地将组合推理与因果推理统一为CCR，并给出形式化定义与评估框架。
- **评估方法新颖**：引入“内部一致性”维度，区分有效/无效、一致/不一致四类推理模式，比单一准确率更丰富。
- **数学严谨**：证明PNS在单调性条件下通过BCC可乘性组合（Theorem 5.1），并提供形式化推论。
- **工具产出**：开源了CCR任务自动生成器，支持用户控制图复杂度、主题（数量推理/定性推理），方便未来基准构建。
- **实验结果可视化**：使用交换割树（CCT）直观展示模型推理的路径有效性。

## 8. 不足与局限
- **实验覆盖有限**：仅使用一个简单的8节点DAG、一个基准任务（CandyParty）且因果函数仅为逻辑或。未测试更大图、不同因果函数（如逻辑与混合）、非线性或连续变量场景。
- **仅聚焦ATE和PNS**：未探索其他因果测度（如PN、PS、自然间接效应等）的组合形式。
- **评估方式特定**：将LM作为反事实数据模拟器，而非直接要求LM进行形式因果推理（如Cladder做法）。这限制了与现有基准的直接比较。
- **计算资源细节不充分**：未报告总推理时间或成本，特别是GPT-4o和o1的使用情况。
- **偏差风险**：任务使用固定阈值（0.1 RAE、90%有效）可能过于宽松或严格；不同模型对提示词敏感度不同，未充分探索提示变体。
- **实际部署启示有限**：作者明确指出，在CCR任务上成功是必要但不充分的条件，不能推断LM具备真正推理能力，尤其不应在安全关键场景过度解读。
- **未做消融实验**：如不同采样策略、不同阈值、更复杂的图结构等。

（完）
