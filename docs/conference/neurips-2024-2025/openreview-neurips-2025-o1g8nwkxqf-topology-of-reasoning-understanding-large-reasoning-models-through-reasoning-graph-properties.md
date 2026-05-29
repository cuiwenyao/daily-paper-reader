---
title: "Topology of Reasoning: Understanding Large Reasoning Models through Reasoning Graph Properties"
title_zh: 推理拓扑：通过推理图属性理解大推理模型
authors: "Gouki Minegishi, Hiroki Furuta, Takeshi Kojima, Yusuke Iwasawa, Yutaka Matsuo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=o1g8NWkxqf"
tags: ["query:ns-xai"]
score: 9.0
evidence: 通过推理图拓扑分析大模型推理机制，提升可解释性
tldr: 为理解大推理模型内部机制，本文提出推理图概念，通过对每个推理步骤隐状态聚类构建图，并分析循环性、直径、小世界指数等拓扑属性。在GSM8K等任务上发现蒸馏模型具有更高循环次数和显著小世界特征，这些属性与推理性能相关，为模型可解释性提供了结构化视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 487}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 548, \"height\": 375}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 369}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 686}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 419}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1436, \"height\": 564}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1432, \"height\": 359}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 565, \"height\": 247}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 486}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1462, \"height\": 666}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 367}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1413, \"height\": 423}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1420, \"height\": 426}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 639, \"height\": 393}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 492}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1445, \"height\": 522}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 328}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 1884}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 926, \"height\": 345}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1178, \"height\": 654}]"
motivation: 大推理模型性能优异但内部机制不明，需要可解释性分析工具。
method: 从隐状态聚类构建推理图，计算图论指标（循环性、直径、小世界指数）分析模型行为。
result: 蒸馏模型表现出更多循环、更大直径和小世界特性，与推理难度正相关。
conclusion: 推理图拓扑分析为解释大模型推理行为提供了有效框架，有助于指导模型优化。
---

## Abstract
Recent large-scale reasoning models have achieved state-of-the-art performance on challenging mathematical benchmarks, yet the internal mechanisms underlying their success remain poorly understood. In this work, we introduce the notion of a reasoning graph, extracted by clustering hidden‐state representations at each reasoning step, and systematically analyze three key graph-theoretic properties: cyclicity, diameter, and small-world index, across multiple tasks (GSM8K, MATH500, AIME~2024). Our findings reveal that distilled reasoning models (e.g., DeepSeek-R1-Distill-Qwen-32B) exhibit significantly more recurrent cycles (about 5 per sample), substantially larger graph diameters, and pronounced small-world characteristics (about 6x) compared to their base counterparts. 
Notably, these structural advantages grow with task difficulty and model capacity, with cycle detection peaking at the 14B scale and exploration diameter maximized in the 32B variant, correlating positively with accuracy.  
Furthermore, we show that supervised fine-tuning on an improved dataset systematically expands reasoning graph diameters in tandem with performance gains, offering concrete guidelines for dataset design aimed at boosting reasoning capabilities. By bridging theoretical insights into reasoning graph structures with practical recommendations for data construction, our work advances both the interpretability and the efficacy of large reasoning models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型推理模型（如 OpenAI-o1、DeepSeek-R1 等）在数学、编程、科学推理等任务上取得了突破性进展，但它们内部的工作机制仍然不透明。尤其是与传统非推理模型相比，这些模型的“思考”过程如何导致性能提升尚不清楚。
- **整体含义**：本文旨在通过引入**推理图（Reasoning Graph）** 的概念，从图论角度量化分析大推理模型在推理过程中的内部状态结构，揭示其优异性能背后的关键结构特征，从而提升模型可解释性，并为更有效的训练数据构建提供指导。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将语言模型在每个推理步骤的隐状态映射为图节点，将推理过程中的状态转移视为有向边，从而构建每个样本的推理图。然后分析图的图论属性（循环性、直径、小世界指数），以区分推理模型与基础模型的结构差异。
- **关键技术细节**：
  - **节点定义**：对每个推理步骤的 token 隐状态取平均，得到段表示 \( s_t^\ell \)；对所有样本的所有段表示执行 K-means 聚类（默认 K=200），每个聚类中心作为一个节点 \( v_k \)。
  - **边构造**：对于每个样本，将每一步的段表示分配给最近的聚类中心，得到节点序列 \( \pi = (i_1, i_2, \dots, i_T) \)；连接相邻节点形成有向边 \( v_{i_t} \to v_{i_{t+1}} \)。
  - **图属性测量**：
    - **循环（Cycle）**：检测样本序列中是否出现重复节点（排除自环和相邻重复），计算循环检测比例和循环计数。
    - **直径（Diameter）**：使用 Dijkstra 算法计算图内任意两可达节点之间的最大最短路径距离。
    - **小世界指数（Small-World Index, S）**：先对称化有向图，计算聚类系数 C 和平均路径长度 L，再与同等规模的 Erdős–Rényi 随机图基线比较：\( S = \frac{C/C_{\text{rand}}}{L/L_{\text{rand}}} \)。

## 3. 实验设计

- **数据集**：
  - 数学推理：GSM8K（简单）、MATH500（中等）、AIME 2024（困难）。
  - 非数学推理：StrategyQA（多跳问答）、LogicalDeduction（逻辑推理，来自 BIG-Bench）。
- **基准（Benchmark）**：使用各数据集的准确率作为性能指标。
- **对比方法**：
  - **推理模型**：DeepSeek-R1-Distill-Qwen 系列（1.5B/7B/14B/32B，蒸馏自 Qwen2.5 系列）。
  - **基础模型**：对应的 Qwen2.5-Math-1.5B/7B/14B/32B 以及 Llama-3.1-8B（用于 8B 蒸馏模型）。
  - 另外在 SFT 实验中对比了 s1-v1.0 和 s1-v1.1 两个数据集。
  - 还对比了 LIMO 数据集与 s1 数据集。

## 4. 资源与算力

- **训练**：SFT 实验使用 8 张 NVIDIA H200 GPU（每张显存 141GB）。
- **推理**：使用单张 NVIDIA H200 GPU。
- **训练配置**：学习率 1e-5，cosine 调度，batch size 8（每个 GPU 微批次 1），梯度累积步数 1，权重衰减 1e-4，优化器 AdamW，精度 bf16，梯度检查点启用，FSDP full shard。
- 注：文中未详细说明总训练时长，但给出了详细的配置供复现。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验在三个数学数据集上比较推理模型与基础模型的循环检测率、直径、小世界指数，并展示不同层深度（0.1~0.9）的结果。
  - 改变 K-means 的 K 值（50/100/200）进行敏感性分析。
  - 在非数学任务上验证泛化性。
  - 分析模型大小（1.5B/7B/14B/32B）对图属性的影响，并与准确率对比。
  - SFT 实验比较 s1-v1.0 和 s1-v1.1 在 100/200/400/500 步的直径分布。
  - 对比 LIMO 与 s1 数据集推理图属性。
- **充分性评价**：
  - **充分**：覆盖了多种难度数据集、多种模型大小、不同层深度、多种聚类参数，且包含非数学任务验证，实验设计全面。
  - **客观公平**：推理模型与基础模型均来自同一系列（DeepSeek-R1-Distill 与 Qwen2.5），控制变量良好。SFT 实验中对比了不同版本数据集，均使用相同训练配置。
  - 不足：未对比非蒸馏的强化学习训练模型（如原始 DeepSeek-R1），但作者在局限中已说明。

## 6. 主要结论与发现

- **循环性**：推理模型的推理图平均含有约 5 个循环，显著高于基础模型；循环检测比例随任务难度增加而上升（AIME 2024 达 93%~97%）。
- **直径**：推理模型具有明显更大的图直径，表明探索更广泛的推理状态空间；直径随层深度增加而扩大。
- **小世界特性**：推理模型的小世界指数约为基础模型的 6 倍，表明其图结构兼具高局部聚类和高效全局连通性，有利于从错误路径中恢复。
- **模型规模效应**：循环数、直径、小世界指数均随模型规模增大而增大，其中 32B 模型直径最大且准确率最高；但 14B 模型循环检测率最高（100%），部分原因是语言混合导致的无益循环。
- **SFT 数据影响**：使用更优数据集（s1-v1.1）训练的模型，推理图直径更大，且与准确率提升正相关；s1 数据集相比 LIMO 诱导出更宽的探索和更多循环。
- **对“Aha Moment”的量化**：循环结构对应于模型重新检查中间答案的行为，为“Aha Moment”提供了内部状态层面的解释。

## 7. 优点

- **新颖的视角**：首次系统地从图论角度（循环、直径、小世界）分析大型推理模型的内部结构，为可解释性提供了新工具。
- **轻量且可扩展**：仅需提取中间层隐状态并进行聚类，无需额外标注或训练，可推广至不同模型和任务。
- **连接理论与实践**：将图属性与 SFT 数据质量关联，为数据集设计提供了可量化的指标（如更大的直径意味着更优的推理探索）。
- **实验覆盖广**：涵盖多难度任务、多模型规模、多数据集版本，并进行了超参数敏感性分析，结果稳健。
- **开源实现**：提供代码和复现细节，便于社区验证和进一步研究。

## 8. 不足与局限

- **缺乏特征级/电路级分析**：仅基于隐状态聚类的节点级分析，未深入到特征或电路层面（如 Mechanistic Interpretability），未能揭示具体哪些神经元或注意力头贡献了循环行为。
- **训练动态未知**：未解释推理图属性如何在强化学习（如 DeepSeek-R1 的 RL 阶段）或蒸馏过程中逐步涌现，仅分析了 SFT 后的结果。
- **可能存在偏差**：
  - 聚类数量 K 的选择（默认 200）可能影响结果，作者虽进行了 50/100/200 的敏感性分析，但未展示非常小或非常大的 K。
  - 仅使用了蒸馏后的推理模型，未验证原始 RL 训练得到的模型（如原始 DeepSeek-R1）。
  - 数学任务为主，非数学任务（StrategyQA, LogicalDeduction）虽然验证了泛化性，但样本量可能较小。
- **应用限制**：结论主要基于 Qwen2.5 架构和 DeepSeek-R1 蒸馏模型，其他架构（如 Llama、Gemini 等）的泛化性有待验证。
- **计算负担**：提取所有样本的隐状态并进行 K-means 聚类（K=200）在大型模型（32B）上仍需要一定算力，可能限制实时应用。

（完）
