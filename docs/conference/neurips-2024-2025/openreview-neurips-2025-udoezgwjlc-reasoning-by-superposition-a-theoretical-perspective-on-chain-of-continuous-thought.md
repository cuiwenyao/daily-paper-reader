---
title: "Reasoning by Superposition: A Theoretical Perspective on Chain of Continuous Thought"
title_zh: 叠加推理：连续链式推理的理论视角
authors: "Hanlin Zhu, Shibo Hao, Zhiting Hu, Jiantao Jiao, Stuart Russell, Yuandong Tian"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=UdOEZgWJLc"
tags: ["query:ns-xai"]
score: 4.0
evidence: 连续链式推理的理论分析
tldr: 离散链式推理已有理论支撑，但连续链式推理为何更优尚不清楚。本文证明两层Transformer配合连续CoT可解决有向图可达性问题，为连续推理提供了理论解释，揭示了其表达能力优势。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1252, \"height\": 242}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1277, \"height\": 358}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1218, \"height\": 332}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 428, \"height\": 431}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 613}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 684, \"height\": 580}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1317, \"height\": 323}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 898, \"height\": 248}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1189, \"height\": 497}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 507, \"height\": 535}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 690, \"height\": 217}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 242}]"
motivation: 连续CoT优于离散CoT的理论原因不明。
method: 理论分析两层Transformer在连续CoT下解决图推理任务的能力。
result: 证明连续CoT能解决有向图可达性问题。
conclusion: 为连续链式推理的优势提供了理论依据。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable performance in many applications, including challenging reasoning problems via chain-of-thought (CoT) techniques that generate ``thinking tokens'' before answering the questions. While existing theoretical works demonstrate that CoT with discrete tokens boosts the capability of LLMs, recent work on continuous CoT lacks a theoretical understanding of why it outperforms discrete counterparts in various reasoning tasks, such as directed graph reachability, a fundamental graph reasoning problem that includes many practical domain applications as special cases. In this paper, we prove that a two-layer transformer with $D$ steps of continuous CoT can solve the directed graph reachability problem, where $D$ is the diameter of the graph, while the best known result of constant-depth transformers with discrete CoT requires $O(n^2)$ decoding steps where $n$ is the number of vertices ($D<n$). 
In our construction, each continuous thought vector is a superposition state that encodes multiple search frontiers simultaneously (i.e., parallel breadth-first search (BFS)), while discrete CoT must choose a single path sampled from the superposition state, which leads to a sequential search that requires many more steps and may be trapped in local solutions.
We also performed extensive experiments to verify that our theoretical construction aligns well with the empirical solution obtained via training dynamics. Notably, encoding of multiple search frontiers as a superposition state automatically emerges in training continuous CoT, without explicit supervision to guide the model to explore multiple paths simultaneously.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）借助链式推理（CoT）显著提升了推理能力。现有理论工作证明了离散CoT（每一步输出离散token）能增强LLM的表达力，但近期提出的连续CoT（Coconut）在多种推理任务（如定向图可达性）中表现优于离散CoT，其背后的理论原因尚不清楚。
- **整体含义**：本文首次为连续CoT提供了严格的理论解释，揭示其通过**叠加态**（superposition）机制实现隐式并行搜索，从而大幅减少推理步数。该工作填补了连续空间推理的理论空白，并为设计更高效的推理方法提供了理论基础。

---

### 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：
    - 连续思维向量被建模为**叠加态**，即一个向量同时编码多个可达节点集（搜索前沿）。这对应于**并行广度优先搜索（BFS）**，而离散CoT每次只能采样一个分支（类似“坍缩态”），导致顺序搜索。
    - 理论构造证明：一个**两层Transformer**，配合**D步连续思维**（D为图的直径），即可解决有向图可达性问题；而现有最好结果的离散CoT需要O(n²)步。

- **关键技术细节**：
    1. **注意力选择器（Attention Chooser）**：利用正弦位置编码（或RoPE）构造的注意力头，使模型能根据当前token类型选择性地关注特定相对位置（如源节点、目标节点）。
    2. **叠加态维护**：通过归纳法构造，证明第c步的连续思维向量`[t_c]`等于归一化的`V_c`（距离起点r不超过c步的所有顶点）的叠加：`[t_c] = (1/√|V_c|) Σ_{v∈V_c} u_v`。
    3. **两层网络分工**：
        - **第一层注意力**：多个注意力头将源节点和目标节点信息复制到对应边token的缓冲空间。
        - **第二层注意力**：当前思维向量`[t_c]`通过注意力机制从边token中检索所有源节点属于`V_c`的边，并将对应的目标节点叠加到当前思维中，实现一步扩展。
        - **MLP层**：作为滤波器，消除噪声并均衡叠加态中各节点的权重。
    4. **预测阶段**：在最终层，通过比较候选节点`c1`和`c2`与叠加态的内积（信号强度）来输出可达的节点。

- **算法流程示意**（文字描述）：
    - 输入：图边序列、起点、两个候选终点。
    - 第0步连续思维初始化为起点嵌入。
    - 每步循环：当前连续思维`[t_c]` → 第二层注意力将所有可达边指向的目标节点叠加进来 → MLP滤波器 → 得到新的连续思维`[t_{c+1}]`（叠加了全部V_{c+1}）。
    - 经过D步后，附加答案token`<A>`，通过阅读矩阵与叠加态比较，输出候选节点中信号更强的那个。

---

### 实验设计

- **数据集**：使用**ProsQA**（Hao et al., 2024）的子集，仅包含需要3-4步推理的问题。每个图约22.8个节点、36.5条边，训练集14785个问题，验证集257个，测试集419个。
- **Benchmark**：图可达性二选一任务（保证仅一个节点可达）。
- **对比方法**：
    1. **Coconut（连续CoT）**：本文方法，两层Transformer。
    2. **离散CoT**：同样两层Transformer。
    3. **CoT\***：更大规模的12层Transformer。
    4. **No CoT**：无链式推理的基线。
- **训练细节**：
    - 模型：GPT-2风格解码器，2层，d_model=768, nheads=8，从头训练。
    - 优化器：AdamW (β1=0.9, β2=0.95, weight_decay=1e-2)，恒定学习率1e-4。
    - 训练策略：多阶段训练，每阶段25轮，共300轮；阶段i教模型使用i步连续思维，并混合10%上一阶段数据。

---

### 资源与算力

- **明确说明**：每次Coconut实验需2块Nvidia A100 80GB GPU，运行约24小时。
- **未说明部分**：未给出离散CoT和No CoT具体算力消耗，但基于相同配置可推测资源类似。

---

### 实验数量与充分性

- **实验组数**：主要报告了整体准确率对比图（图4）、注意力模式可视化（图5、表1）、连续思维表征分析（图6）。此外，进行了3个随机种子的稳定性实验（表5），以及消融实验**Coconut-BFS**（均匀从前沿采样监督信号而非最优路径）。
- **充分性与公平性**：
    - 实验覆盖了多种关键分析：准确率、注意力机制解释、表征内积分析。
    - 对比了不同规模模型（2层 vs 12层），且说明了离散CoT即使12层也达不到完美准确率，凸显连续CoT优势。
    - 消融实验（Coconut-BFS）验证了叠加态自动涌现，无需强监督。
    - 未在更多不同难度、更大规模图数据集上进行实验，只在3-4跳的图上测试。实验充分性中等，但足以支撑理论核心结论。

---

### 主要结论与发现

1. **理论证明**：两层Transformer用D步连续思维可解有向图可达性，步数仅依赖图直径（D＜n），而离散CoT需要O(n²)步。这严格证明了连续CoT在特定推理问题上的表达能力优势。
2. **叠加态机制**：连续思维向量在训练中自动学会编码多个搜索前沿（叠加态），实现并行BFS，而离散CoT只能顺序搜索。
3. **实验验证**：Coconut在ProsQA上接近完美准确率（近100%），远优于离散CoT（约75%）和12层CoT*（约83%）。
4. **注意力与表征**：模型第一层注意力学会复制边信息；第二层注意力聚焦于可达边；连续思维与可达节点内积高，且前沿节点和最优节点内积更高，验证了叠加态假设。
5. **前沿优先探索**：即使训练仅提供最优路径，模型仍能自发分配更高权重给前沿节点（Coconut-BFS实验表明该行为源自结构而非监督）。

---

### 优点

1. **理论创新**：首次为连续CoT提供了严格的理论优势证明，揭示了叠加态这一关键机制，并给出了可构造的Transformer参数（不依赖问题特定位置编码，支持正弦和RoPE）。
2. **清晰的机理分析**：将连续CoT比作并行BFS，离散CoT比作坍缩态的DFS，解释直观有力。
3. **理论与实验高度一致**：实验发现的注意力模式、表征内积分布均与理论构造吻合，验证了理论有效性。
4. **监督效率**：模型自动学会编码多种搜索路径，无需显式多路径监督，降低了训练数据要求。
5. **开源代码**：提供完整代码，便于复现和扩展。

---

### 不足与局限

1. **任务范围有限**：仅在图可达性（尤其是3-4跳图）上验证，未覆盖更复杂推理（如最短路径、多跳推理、数学推理中的非图问题）。理论证明图可达性可代表更广的推理问题（如论文指出包含图灵机停机问题），但实际泛化性未验证。
2. **假设较强**：理论构造要求词嵌入正交、MLP使用硬阈值（hard-threshold）激活等理想化条件，实际训练中不一定严格满足，但实验表明系统能近似实现。
3. **缺乏下界证明**：论文仅给出离散CoT上界为O(n²)，但未证明离散CoT所需步骤的下界，严格分离性尚不完全。
4. **训练复杂性**：多阶段训练策略（300轮）需要精心设计课程，可能对超参数敏感。
5. **可扩展性**：2层Transformer在实验规模（~22节点）上成功，但未测试更大图（数百节点）时的性能，理论构造成本与embedding维度线性相关于词汇表大小，可能在大规模词汇时效率下降。
6. **缺乏更多对比基线**：未与tree-of-thought、beam search等显式并行搜索方法对比。

---

（完）
