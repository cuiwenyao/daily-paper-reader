---
title: "Reasoning by Superposition: A Theoretical Perspective on Chain of Continuous Thought"
title_zh: 叠加推理：连续思维链的理论视角
authors: "Hanlin Zhu, Shibo Hao, Zhiting Hu, Jiantao Jiao, Stuart Russell, Yuandong Tian"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=UdOEZgWJLc"
tags: ["query:ns-xai"]
score: 4.0
evidence: 对大型语言模型中连续思维链推理的理论分析
tldr: 连续思维链优于离散思维链的理论原因尚不明确。本文证明两层Transformer借助连续CoT即可解决有向图可达问题，从理论上解释了连续CoT为何在推理任务中表现更优，为理解LLM推理提供基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1252, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1277, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1218, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 428, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 684, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1317, \"height\": 323, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 898, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1189, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 507, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 690, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 242, \"label\": \"Table\"}]"
motivation: 连续思维链相比离散思维链在推理任务中效果更好，但缺乏理论解释。
method: 从理论上证明两层Transformer使用连续CoT可解决有向图可达问题。
result: 给出了连续CoT优势的理论证明。
conclusion: 该理论工作加深了对LLM推理机制的理解。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable performance in many applications, including challenging reasoning problems via chain-of-thought (CoT) techniques that generate ``thinking tokens'' before answering the questions. While existing theoretical works demonstrate that CoT with discrete tokens boosts the capability of LLMs, recent work on continuous CoT lacks a theoretical understanding of why it outperforms discrete counterparts in various reasoning tasks, such as directed graph reachability, a fundamental graph reasoning problem that includes many practical domain applications as special cases. In this paper, we prove that a two-layer transformer with $D$ steps of continuous CoT can solve the directed graph reachability problem, where $D$ is the diameter of the graph, while the best known result of constant-depth transformers with discrete CoT requires $O(n^2)$ decoding steps where $n$ is the number of vertices ($D<n$). 
In our construction, each continuous thought vector is a superposition state that encodes multiple search frontiers simultaneously (i.e., parallel breadth-first search (BFS)), while discrete CoT must choose a single path sampled from the superposition state, which leads to a sequential search that requires many more steps and may be trapped in local solutions.
We also performed extensive experiments to verify that our theoretical construction aligns well with the empirical solution obtained via training dynamics. Notably, encoding of multiple search frontiers as a superposition state automatically emerges in training continuous CoT, without explicit supervision to guide the model to explore multiple paths simultaneously.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Reasoning by Superposition: A Theoretical Perspective on Chain of Continuous Thought》的详细中文总结。

### 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）通过“思维链”（Chain-of-Thought, CoT）技术生成中间推理步骤，显著提升了复杂推理能力。然而，传统的CoT使用离散文本 token，其表达能力受限于必须依次采样并“坍缩”到单一分支。近期提出的“连续思维链”（Continuous CoT，即COCONUT）允许在连续潜在空间中推理，在多项任务（如有向图可达性、数学推理）上表现更优，但其背后的理论机制尚不明确。
- **核心问题**：为何连续CoT能比离散CoT更高效地解决推理问题？其内在工作原理是什么？
- **整体含义**：该论文通过理论证明和实验验证，揭示了连续CoT的关键优势在于其“叠加状态”（superposition state）机制。每个连续思维向量可同时编码多个搜索前沿（如广度优先搜索中的多条路径），实现隐式并行搜索；而离散CoT每次只能选择一个确定路径（类似“坍缩”），导致需要更多的推理步数且可能陷入局部最优。该工作为理解LLM推理提供了基础理论视角。

### 2. 方法论

- **核心思想**：连续CoT的每个中间思维向量是多个可达节点嵌入的归一化叠加（即叠加状态），相当于在潜在空间中进行并行广度优先搜索（BFS）。通过构建一个两层Transformer，证明仅需 $D$ 步（图直径）连续思维即可判定有向图可达性，而离散CoT的已知最优结果是 $O(n^2)$ 步。
- **关键技术细节**：
  - **问题形式化**：有向图 $G=(V,E)$，顶点数 $n$，直径 $D$。输入序列包含边描述、起始节点 $r$、两个候选目标 $c_1,c_2$，任务是判断哪个目标可达。
  - **注意力选择器（Attention Chooser）**：构建查询和键矩阵，使得当前 token 为特定类型（如边标记`<e>`）时，注意力几乎全部转移到指定偏移位置（如源节点或目标节点）；否则注意力集中在序列起始的 `<s>` token（注意汇）。该构造与正弦/旋转位置编码兼容。
  - **两层Transformer构造**：
    - **第一层**：五个注意力头将边源节点和目标节点嵌入复制到对应边标记的缓冲空间；将候选目标节点嵌入复制到推理标记的缓冲空间；将最后一个连续思维复制到答案标记的缓冲空间。MLP层过滤噪声并归一化权重。
    - **第二层**：一个注意力头使当前连续思维 `[t_c]` 关注所有源节点在 $V_c$ 中的边标记，并将这些边的目标节点嵌入加权求和加入思维向量，实现一步节点扩展。MLP层再次滤波并均衡权重，得到归一化的 $V_{c+1}$ 叠加状态。
  - **最终预测**：答案标记 `<A>` 通过注意力获取候选节点信息，并与当前叠加状态比较，选择内积更大的候选节点作为输出。
  - **位置编码兼容性**：构造同时适用于正弦位置编码（sinusoidal）和旋转位置编码（RoPE），无需针对问题或长度定制。

### 3. 实验设计

- **数据集**：使用 ProsQA 数据集（Hao et al., 2024），包含约 14,785 个训练样本、257 个验证样本、419 个测试样本。每个问题均涉及有向图，解决方案需要 3-4 步推理。
- **Benchmark**：图可达性判定任务（准确率）。
- **对比方法**：
  - **COCONUT**：连续CoT，两层Transformer（$d_{model}=768$, $n_{heads}=8$）。
  - **CoT**：离散CoT，相同两层Transformer。
  - **CoT\***：离散CoT，12层Transformer（$n_{heads}=12$）。
  - **No CoT**：无思维链，直接预测。
- **训练策略**：多阶段课程训练，逐阶段增加连续思维步数，监督信号来自最优路径的CoT序列。另外引入 **COCONUT-BFS** 变体，在阶段 $i$ 从距根节点恰好 $i$ 步的前沿节点中随机均匀采样作为监督信号，而非最优路径节点。

### 4. 资源与算力

论文在附录 C.3 中明确说明：
- **单次运行**：使用两块 NVIDIA A100 80GB GPU，训练约 **24 小时**。
- **实验环境**：同一实验（如COCONUT）使用上述配置。未提及完整项目总计算量，但指出多次随机种子重复实验也在此配置下完成。

### 5. 实验数量与充分性

- **主要实验**：
  - 准确率对比（图4）：COCONUT vs 离散CoT、CoT*、No CoT。
  - 第一层注意力可视化（图5）：验证边标记正确复制源/目标节点。
  - 第二层注意力分数分析（表1）：按边类型（Reachable、Not Reachable、Frontier、Optimal）统计注意力分布。
  - 连续思维与节点嵌入内积分析（图6、表5）：按节点类别统计内积，展示叠加状态编码。
  - COCONUT-BFS 消融实验：验证不同监督信号下叠加状态是否仍然涌现。
- **充分性评价**：
  - 实验种类较全面，覆盖了性能对比、机制验证（注意力和表征）和消融分析。
  - 使用3个随机种子重复实验（表5），结果稳定。
  - 实验客观：COCONUT达到近100%准确率，而离散CoT（含12层）仅约83%，差距显著，支持理论结论。
  - 公平性：对比基线均使用相同或更大模型，训练策略一致。

### 6. 主要结论与发现

1. **理论证明**：两层Transformer配合 $D$ 步连续CoT即可判定有向图可达性，而离散CoT需要 $O(n^2)$ 步。
2. **叠加状态机制**：连续思维向量是当前可达节点集合的归一化叠加，实现隐式并行BFS。
3. **自动涌现**：即使无显式多路径监督，训练后连续思维自然编码了多个搜索前沿。
4. **探索优先级**：模型不仅区分可达/不可达节点，还偏好前沿节点和最优路径节点，这可能源于训练信号或图结构特征。
5. **实际验证**：注意力模式、内积分布等与分析预测一致，表明理论构造与学习解高度吻合。

### 7. 优点

- **理论贡献突出**：首次严格证明连续CoT在特定推理问题上的步数优势，并揭示其并行搜索的本质。
- **构造实用**：理论构造兼容标准正弦和RoPE位置编码，无需特殊设计。
- **实验支撑充分**：从多个角度（性能、注意力、表征）验证理论，并加入消融实验探讨优先级来源。
- **发现出乎意料**：最优路径监督下，模型仍保持对非最优前沿节点的权重，表明广度优先搜索策略的自然涌现，为理解训练动力学提供了线索。
- **代码开源**：提供了可复现的代码。

### 8. 不足与局限

- **问题范围受限**：理论及实验仅针对有向图可达性，连续CoT在更一般推理任务（如数学、常识推理）上的优势机制尚待分析。
- **理论假设较强**：构造中假设 token 嵌入正交、MLP使用阈值过滤等，实际训练可能无法完美满足，但实验表明近似满足即可工作。
- **所需嵌入维度**：理论构造要求嵌入维度 $d=O(|Voc|)$（线性于词汇表大小），尽管实验中使用768维也能成功，但理论最优性未讨论。
- **未推导下界**：离散CoT在可达性问题上所需步数的严格下界尚未给出，仅引用已知上界 $O(n^2)$，分离程度不绝对。
- **训练依赖课程**：多阶段课程训练需要人工设计CoT监督，这可能限制了零样本或弱监督场景的适用性。
- **计算资源**：虽明确报告，但24小时/run对于大规模扩展可能较高，且未给出不同模型大小下的缩放规律。

（完）
