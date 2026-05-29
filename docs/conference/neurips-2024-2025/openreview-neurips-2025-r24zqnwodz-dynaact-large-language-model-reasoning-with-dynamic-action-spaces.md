---
title: "DynaAct: Large Language Model Reasoning with Dynamic Action Spaces"
title_zh: DynaAct：基于动态动作空间的大语言模型推理
authors: "Xueliang Zhao, Wei Wu, Jian Guan, Qintong Li, Lingpeng Kong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=R24ZqNwoDz"
tags: ["query:ns-xai"]
score: 6.0
evidence: 基于动态动作空间的LLM推理，提升复杂问题求解效率
tldr: 针对现有LLM顺序推理中动作空间构建效率低的问题，本文提出DynaAct框架，通过从复杂推理问题语料中提取通用草图来估计完整动作空间代理，并利用子模函数联合评估构建紧凑动作空间。实验表明，该方法在保持推理质量的同时显著降低了计算开销，为提升LLM推理效率提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-r24zqnwodz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r24zqnwodz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 808, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-r24zqnwodz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 437, \"height\": 431, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1291, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 651, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 882, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 700, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 581, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 442, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 802, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 751, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 810, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 901, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 586, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-r24zqnwodz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 342, \"label\": \"Table\"}]"
motivation: 现有动作空间构建方法要么手动定义缺乏可扩展性，要么非结构化导致计算昂贵，亟需自动化紧凑动作空间构建方法。
method: 先用LLM从多样化语料中提取通用推理草图作为动作空间代理，再通过子模函数联合评估筛选出紧凑动作空间。
result: 在复杂推理任务上，DynaAct显著减少了推理计算量，同时保持或提升了推理准确性。
conclusion: 自动构建紧凑动作空间是提升LLM顺序推理效率的有效途径，该方法可推广至更多决策问题。
---

## Abstract
In modern sequential decision-making systems, the construction of an optimal candidate action space is critical to efficient inference. However, existing approaches either rely on manually defined action spaces that lack scalability or utilize unstructured spaces that render exhaustive search computationally prohibitive. In this paper, we propose a novel framework named \textsc{DynaAct} for automatically constructing a compact action space to enhance sequential reasoning in complex problem-solving scenarios. Our method first estimates a proxy for the complete action space by extracting general sketches observed in a corpus covering diverse complex reasoning problems using large language models. We then formulate a submodular function that jointly evaluates candidate actions based on their utility to the current state and their diversity, and employ a greedy algorithm to select an optimal candidate set. 
Extensive experiments on six diverse standard benchmarks demonstrate that our approach significantly improves overall performance, while maintaining efficient inference without introducing substantial latency. The implementation is available at \url{https://github.com/zhaoxlpku/DynaAct}.

---

## 论文详细总结（自动生成）

# 1. 论文的核心问题与整体含义
- **研究动机**：大语言模型（LLM）在顺序决策任务（如多步推理）中，动作空间（action space）的构建至关重要。现有方法要么手动定义动作空间（如rStar），缺乏可扩展性和泛化性；要么在无结构自然语言空间中搜索（如自回归生成），计算开销巨大。缺乏一种既能自动化学习、又能保持紧凑高效的动作空间构建方法。
- **核心问题**：如何自动地从演示数据中学习通用的、可扩展的动作模式，同时消除冗余候选，使得每个推理步骤能够从一个小而完整的候选集中快速选择最优动作。
- **整体含义**：本文提出动态动作空间构建作为LLM推理的新方向，通过子模函数（submodular function）优化动作选择的效用与多样性，在不引入显著延迟的前提下大幅提升复杂推理任务的准确率。

# 2. 论文提出的方法论
- **核心思想**：将动作空间构建形式化为子集选择问题，利用子模函数的边际递减性质，以线性复杂度近似最优子集。
- **关键技术细节**：
  - **代理动作空间估计**：从复杂推理问题语料（如Open-Platypus，含24,652个问题）中随机分k组，用LLM提取通用推理草图（observation sketches），汇聚去重后得到代理动作空间A（约40,822个动作）。
  - **子模函数定义**：函数F(At; st) = α·f_util(At; st) + β·f_div(At)。其中f_util基于状态与动作的嵌入点积的LogSumExp，衡量动作对当前状态的效用；f_div基于动作嵌入之间的最小距离，鼓励多样性。该函数被证明是子模的。
  - **嵌入函数学习**：通过Q-learning目标训练一个轻量级嵌入模型（基于Llama-3.2-1B-Instruct的最后一层隐状态），使得嵌入点积近似Q值，优化目标为最小化与标准Q-learning更新方程的均方误差。
  - **动作空间构建**：采用贪心算法，从A中每次选择使子模函数边际增益最大的动作，迭代m次（m=5）得到候选集At。复杂度O(m²|A|)。
  - **推理流程**：在MDP框架下，利用MCTS估计Q(st,a)，选择最优动作a_t，更新状态，逐步生成推理链。整个过程中基础LLM（Llama-3.1-8B-Instruct）保持冻结，仅训练嵌入模型。

# 3. 实验设计
- **使用的数据集/场景**：六个标准基准，覆盖三个领域：
  - **通用**：MMLU、MMLU-Pro
  - **推理**：GPQA、ARC-Challenge (ARC-C)
  - **数学**：GSM8K、MATH-500
- **对比方法**：
  - Zero-shot CoT（单次推理）
  - SC@maj16（自一致性，16条路径投票）
  - RAP（基于MCTS，自动生成子问题作为动作空间）
  - rStar（手动定义5个动作，MCTS搜索+小模型判别）
- **评价指标**：精确匹配准确率（Exact Match Accuracy）。
- **核心结果**：DynaAct在所有六个基准上均超越所有基线，尤其在MATH-500上达到61.00%，相比rStar（54.20%）绝对提升6.80%；在GSM8K上达89.16%，提升1.37%。同时推理延迟与rStar相当（相对时间1.00 vs 0.95），低于RAP（1.12）。

# 4. 资源与算力
- **训练**：嵌入模型（Llama-3.2-1B-Instruct）在83,083个状态-动作对上微调，学习率1e-5，训练细节未明确给出具体时间和GPU数量。
- **推理**：所有基于MCTS的方法（RAP、rStar、DynaAct）均使用16次rollout，骨干模型为Llama-3.1-8B-Instruct。作者在8×A100 GPU机器上测量了单例推理时间（见附录F.4），DynaAct为57.60秒/例，rStar为54.72秒，RAP为64.51秒。
- **未明确说明**：完整训练耗时、MCTS中树的深度/宽度等超参数。但给出了实现细节和代码仓库。

# 5. 实验数量与充分性
- **实验数量**：
  - 主实验：6个数据集 × 5种方法 = 30组对比结果。
  - 消融实验：在ARC-C和MATH-500上检验了5个变体（去除效用项、多样性项、Q-learning、完整子模函数等）。
  - 紧凑性研究：改变动作空间大小m（5,10,15）和rollout次数（2,4,8,16,32），对比RAP。
  - 效用研究：在MATH-500 Level 5子集上比较DynaAct与rStar的关键步骤覆盖率。
  - 延迟研究：相对时间比较。
  - 难度分析：在MATH-500的Level 3/4/5上对比rStar和消融变体。
  - 多样性分析：在Level 5子集上计算多样性分数。
  - 附加实验（附录）：与RL剪枝基线、非子模多样性指标、不同α/β参数、不同代理动作空间规模、少样本/微调基线的对比。
- **充分性**：覆盖全面，从多个维度（性能、效率、紧凑性、多样性、参数敏感性）验证了方法的有效性，对比基线包括当前最强方法（rStar、RAP），消融设计清晰。实验基本客观公平，所有方法使用相同骨干模型（Llama-3.1-8B-Instruct）和相同rollout次数。

# 6. 论文的主要结论与发现
- DynaAct通过自动构建紧凑且信息密集的动作空间，显著提升了LLM在通用、推理、数学等多类任务上的性能，尤其在复杂推理任务（MATH-500 Level 5）上优势明显（相对rStar提升近一倍准确率）。
- 子模函数的效用项与多样性项缺一不可，去除任意一项都会导致性能下降。
- Q-learning训练嵌入函数对捕捉长期效用至关重要，静态嵌入无法达到同等效果。
- 动态动作空间构建能在保持推理效率的同时带来效果提升，延迟相对rStar仅增加约5%，但准确率提升显著。
- 与手动定义动作空间的rStar和自动生成子问题的RAP相比，DynaAct的可扩展性和紧凑性更优。

# 7. 优点
- **方法论创新**：首次将子模优化引入LLM推理的动作空间构建，理论保证贪心算法接近最优。
- **轻量高效**：仅需训练一个小型嵌入模型（1B参数），基础LLM保持冻结，计算开销低。
- **数据驱动**：无需人工设计动作，从语料中自动提取通用草图，可扩展至不同领域。
- **实验充分**：涵盖广泛的数据集和消融研究，对每个组件进行了必要性验证，参数敏感性分析详尽。
- **开源可用**：提供代码仓库，可复现性高。
- **实用性强**：在提升性能的同时不引入显著推理延迟，适合实际部署。

# 8. 不足与局限
- **计算依赖**：尽管推理效率较好，但MCTS仍然需要多次rollout（16次），对于实时性要求极高的场景可能仍有延迟（57秒/例）。作者也提到可探索更高效的搜索策略。
- **动作空间规模上限**：实验中将代理动作空间扩展至100万时，延迟增加约18秒，准确率稳定。但未测试极大规模（如千万级）下的表现，可能面临可扩展性瓶颈。
- **领域泛化**：所有实验基于英文基准，且语料库（Open-Platypus）偏向数学和科学推理，在非英语、多步骤决策或对话任务中效果未知。
- **偏差风险**：动作草图由LLM从特定语料中提取，可能继承语料中的偏见（如文化、性别偏见），论文虽在Broader Impacts中提及但未做具体评估。
- **超参数敏感**：α/β的取值（默认0.9/0.1）通过实验选定，但未提供自动化调优机制，不同任务可能需要重新调整。
- **对比基线有限**：未与最新的“思维链搜索”方法（如Tree-of-Thought、GPT-4 finetune等）直接对比，仅与2023-2024年的方法比较。

（完）
