---
title: "Topology of Reasoning: Understanding Large Reasoning Models through Reasoning Graph Properties"
title_zh: 推理的拓扑：通过推理图属性理解大型推理模型
authors: "Gouki Minegishi, Hiroki Furuta, Takeshi Kojima, Yusuke Iwasawa, Yutaka Matsuo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=o1g8NWkxqf"
tags: ["query:ns-xai"]
score: 7.0
evidence: 通过推理图属性分析理解大推理模型
tldr: 大型推理模型内部机制仍难以理解。本文通过聚类隐状态提取推理图，分析其环数、直径和小世界指数等图属性，发现蒸馏模型（如DeepSeek-R1-Distill）比原始模型具有更多循环、更大直径和更明显的小世界特性。这些发现为解释推理模型行为提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 548, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1436, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1432, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 565, \"height\": 247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1462, \"height\": 666, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1413, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1420, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 639, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o1g8nwkxqf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1445, \"height\": 522, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 1884, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 926, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o1g8nwkxqf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1178, \"height\": 654, \"label\": \"Table\"}]"
motivation: 大型推理模型成功但内部机制不明确。
method: 从隐状态聚类构建推理图，分析图论属性（环数、直径、小世界指数）。
result: 蒸馏模型展现出更显著的循环和小世界特征。
conclusion: 推理图属性为理解模型推理行为提供了可解释性视角。
---

## Abstract
Recent large-scale reasoning models have achieved state-of-the-art performance on challenging mathematical benchmarks, yet the internal mechanisms underlying their success remain poorly understood. In this work, we introduce the notion of a reasoning graph, extracted by clustering hidden‐state representations at each reasoning step, and systematically analyze three key graph-theoretic properties: cyclicity, diameter, and small-world index, across multiple tasks (GSM8K, MATH500, AIME~2024). Our findings reveal that distilled reasoning models (e.g., DeepSeek-R1-Distill-Qwen-32B) exhibit significantly more recurrent cycles (about 5 per sample), substantially larger graph diameters, and pronounced small-world characteristics (about 6x) compared to their base counterparts. 
Notably, these structural advantages grow with task difficulty and model capacity, with cycle detection peaking at the 14B scale and exploration diameter maximized in the 32B variant, correlating positively with accuracy.  
Furthermore, we show that supervised fine-tuning on an improved dataset systematically expands reasoning graph diameters in tandem with performance gains, offering concrete guidelines for dataset design aimed at boosting reasoning capabilities. By bridging theoretical insights into reasoning graph structures with practical recommendations for data construction, our work advances both the interpretability and the efficacy of large reasoning models.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大型推理模型（如 DeepSeek-R1、OpenAI o1 等）在数学推理任务上取得突破，但其内部机制仍不明确。特别地，与传统基座模型相比，它们如何通过更长的推理过程实现更高准确率，缺乏可解释的分析工具。
- **研究背景**：已有工作通过链式思维（CoT）或搜索方法提升推理能力，但缺乏对推理过程内部状态的系统性刻画。受先前关于“推理图”理论的启发（Prystawski et al., 2023; Wang et al., 2024），本文提出从隐藏状态中提取**推理图（Reasoning Graph）**，并利用图论性质（环数、直径、小世界指数）来揭示大型推理模型的结构特性，从而解释其性能优势。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将 LLM 在推理过程中每个步骤的隐藏状态聚合成节点，步骤间的转移构成边，从而得到每个样本的推理图。然后计算该图的三个关键图论属性：环（cycles）、直径（diameter）、小世界指数（small-world index）。
- **关键技术细节**：
  - **节点定义**：取每个推理步骤（按换行符分割）所有 token 在特定 Transformer 层的隐藏状态的平均值，作为步骤表示。对所有样本的所有步骤表示进行 K-means 聚类（默认 K=200），每个聚类中心对应一个节点。
  - **边构造**：对于每个问题，将每个步骤分配到最近的聚类中心（节点），节点序列构成有向边。
  - **图属性测量**：
    - **环检测**：统计图中是否存在非自环、非相邻重复的重复节点访问。定义环检测比率（含有环的样本比例）和环计数（单个节点的最大重复次数）。
    - **直径**：使用 Dijkstra 算法计算所有可达节点对之间的最短路径的最大值，表示推理的探索范围。
    - **小世界指数**：先将有向图对称化为无向图，计算聚类系数（C）和平均路径长度（L），与同规模 Erdős–Rényi 随机图对比，得到归一化比值 S = (C/C_rand) / (L/L_rand)。S 越大，表明图兼具局部紧密连接和全局高效通信的特性。

## 3. 实验设计
- **数据集**：主要数学任务：GSM8K（简单）、MATH500（中等）、AIME 2024（困难）。扩展的非数学任务：StrategyQA（多跳问答）、LogicalDeduction（逻辑推理）。
- **基准模型**：对比大型推理模型（DeepSeek-R1-Distill-Qwen 系列：1.5B、7B、14B、32B）与对应基座模型（Qwen2.5-Math-1.5B、Qwen2.5-Math-7B、Llama-3.1-8B、Qwen2.5-14B、Qwen2.5-32B）。默认使用 32B 版本。
- **对比方法**：主要对比推理模型 vs 基座模型。此外，在 SFT 实验中对比了不同数据集（s1-v1.0 vs s1-v1.1）以及训练步数（100、200、400、500）的影响。

## 4. 资源与算力
- **论文中明确说明**：SFT 实验使用了 8 块 NVIDIA H200 GPU 进行训练，单个 H200 GPU 进行推理。训练超参数见附录 J（学习率 1e-5、余弦调度、批大小 8、FSDP 全分片等）。对于大规模推理模型本身的训练算力（如 DeepSeek-R1 的 RL/蒸馏过程），论文未涉及，仅使用预训练完成的模型进行推理与分析。

## 5. 实验数量与充分性
- **实验数量**：
  - 主要图属性分析：在 3 个数学数据集上，对比推理模型和基座模型在 5 个不同隐藏层深度（0.1、0.3、0.5、0.7、0.9 层比）下的环检测比率、环计数、直径、小世界指数（共约 30 组对比条件）。
  - 模型规模影响：4 个不同大小推理模型（1.5B/7B/14B/32B）在 AIME 2024 上的环检测比率、环计数、直径与准确率关系。
  - SFT 演化：在 s1 两个版本上训练不同步数（100、200、400、500）分析直径变化。
  - 非数学任务扩展：StrategyQA 和 LogicalDeduction 的图属性对比。
  - 敏感性分析：K-means 聚类数 K=50、100、200 下的环检测比率。
  - 节点语义自动标注：使用 GPT-4o-mini 对聚类中心进行主题分析。
- **充分性评价**：实验设计系统全面，覆盖了多个维度（任务难度、模型大小、层深度、训练算法、超参数），结果一致支持主要结论。对比客观（推理模型 vs 基座模型，同一基座），未发现明显不公平倾向。消融实验（K 值、非数学任务）增强了结论的鲁棒性。

## 6. 论文的主要结论与发现
1. **环（Cycles）**：大型推理模型比基座模型有显著更多的循环结构（平均每个样本约 5 个循环），且环检测比率随任务难度增加而升高。环结构对应“啊哈时刻”（模型自我纠正行为）。
2. **直径（Diameter）**：推理模型在图直径上明显大于基座模型，表明其探索了更广泛的推理状态空间，且直径随层深增加而增大。SFT 高质量数据（s1-v1.1）进一步扩大了直径。
3. **小世界特性（Small-World）**：推理模型的图具有更高的聚类系数和更长的平均路径长度，小世界指数是基座模型的约 6 倍，说明其形成了紧密的局部集群与稀疏长距离连接，有助于从错误路径恢复。
4. **模型规模影响**：环计数和直径随模型大小增加而增加，但 14B 模型因语言混用导致过多无效循环，准确率低于 32B 模型。表明需区分有益环（自我纠正）与有害环（语言切换）。
5. **数据集设计指导**：更有效的 SFT 数据（如 s1-v1.1）在保持高准确率的同时，倾向于产生更大直径的推理图，因此图直径可作为衡量数据质量的潜在指标。

## 7. 优点
- **新颖的图论分析视角**：首次将推理模型的内部隐藏状态抽象为图，并用经典图论指标（环、直径、小世界）量化其推理行为，提供了一种可解释的工具。
- **系统性与鲁棒性**：实验覆盖多个数据集、模型大小、层深度和超参数，并扩展到非数学任务，结论具有一般性。
- **实践指导意义**：不仅解释现有模型行为，还通过 SFT 实验直接连接图属性与训练数据质量，为构建更好的推理数据提供了具体方向（如优先选择能扩大直径的数据）。
- **开源可复现**：提供了代码仓库和详细的 Python 伪代码（附录 C），方便其他研究者复现和扩展。

## 8. 不足与局限
- **仅关注宏观图结构，未进行细粒度特征/电路分析**：论文指出其分析停留在状态转移层面，未深入神经元或注意力头级别的可解释性（如稀疏自编码器、电路分析），因此难以解释特定图模式如何由底层电路实现。
- **因果性不明确**：虽然观察到图属性与性能相关，但未建立严格的因果关系——即是否主动增加循环或直径就一定能提升准确率？SFT 实验展示了相关性，但缺乏干预实验。
- **评估范围限制**：主要测试数学和逻辑推理任务，未涉及更广泛的推理形式（如常识推理、多模态推理、长文档推理）。语言混用现象仅在 14B 模型上观察到，但未系统分析不同模型的语言一致性。
- **计算资源提及不完全**：仅提供了 SFT 部分的计算资源，对于大规模推理模型（如 DeepSeek-R1）的预训练/蒸馏过程未提及，读者无法评估整体成本。
- **对“坏”循环的区分不足**：论文发现 14B 模型的高循环率来自语言混用（无效循环），但未提出定量区分“有益”和“有害”循环的方法。

（完）
