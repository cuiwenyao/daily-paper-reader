---
title: Policy Guided Tree Search for Enhanced LLM Reasoning
title_zh: 策略引导树搜索：增强大型语言模型推理
authors: Yang Li
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=NNWSNy4YB4"
tags: ["query:ns-xai"]
score: 5.0
evidence: 策略引导的树搜索增强LLM推理
tldr: 针对LLM在复杂推理中的不足，本文提出策略引导树搜索（PGTS）。通过强化学习训练策略动态决定搜索行动，避免手动启发式。在数学推理、逻辑演绎等任务中，PGTS显著优于CoT和传统树搜索方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1500, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 820, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1422, \"height\": 1368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1319, \"height\": 1780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1302, \"height\": 1982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nnwsny4yb4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1324, \"height\": 2212, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-nnwsny4yb4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1750, \"height\": 804, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nnwsny4yb4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nnwsny4yb4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 698, \"height\": 345, \"label\": \"Table\"}]"
motivation: LLM在复杂推理中表现不佳，现有方法依赖预定义启发式或穷举搜索。
method: 结合强化学习与树搜索，学习决策策略以动态引导探索过程。
result: 在数学和逻辑任务上超越CoT，效率更高。
conclusion: PGTS为LLM推理提供了更智能的搜索策略。
---

## Abstract
Despite their remarkable capabilities, large language models often struggle with tasks requiring complex reasoning and planning. While existing approaches like Chain-of-Thought prompting and tree search techniques show promise, they are limited by their reliance on predefined heuristics and computationally expensive exploration strategies. We propose Policy-Guided Tree Search (PGTS), a framework that combines reinforcement learning with structured tree exploration to efficiently navigate reasoning paths. Our key innovation is a learned policy that dynamically decides between expanding, branching, backtracking, or terminating exploration, eliminating the need for manual heuristics or exhaustive search. Experiments across mathematical reasoning, logical deduction, and planning benchmarks demonstrate that PGTS achieves superior reasoning performance while significantly reducing computational costs compared to existing methods. These results establish PGTS as a scalable and effective solution for tackling complex reasoning tasks with LLMs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：大语言模型（LLM）在简单算术上表现优异，但在需要多步骤推理、策略分解和复杂规划的任务（如数学应用题、逻辑推理、真实世界规划）中经常失败。
- **现有方法局限**：
  - CoT（Chain-of-Thought）等高级提示方法虽能引导逐步推理，但缺乏灵活性，且在困难问题上容易出错。
  - 基于验证的方法（如自评估、外部校正器）受限于LLM自身批判能力，且计算昂贵。
  - 树搜索方法（如DFS、BFS、MCTS、A*）利用奖励信号探索推理路径，但依赖预定义启发式规则、手动设计奖励，且穷举搜索的计算开销极大；自评估作为奖励信号进一步增加资源消耗。
- **动机**：亟需一种**自适应、高效**的搜索框架，既能避免手工启发式，又能显著降低计算成本，同时提升推理成功率。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 2.1 核心思想
- **Policy-Guided Tree Search (PGTS)**：将强化学习（RL）与结构化树搜索结合，训练一个**可学习的策略（policy）**，动态决定四种搜索行动：**扩展（Expand）、分支（Branch）、回溯（Backtrack）、终止（Terminate）**，从而高效导航推理路径。
- 关键：将LLM视为**环境（environment）**，而非策略（policy）；由外部学习到的策略控制搜索过程。

### 2.2 关键技术细节
- **形式化**：
  - 将LLM的逐步生成映射为MDP（LM-MDP），但PGTS在更高的树搜索层面定义另一个MDP（TS-MDP）。
  - 状态：已揭示的推理树结构（含节点特征、当前节点位置）。
  - 动作：expand, branch, backtrack（可指定步数）, terminate。
  - 奖励：结合步骤质量和行动成本 `C(a)`（expand成本低，backtrack成本高，terminate几乎为零）。
- **策略网络**：
  - 使用Graph Transformer（GPS架构），结合局部消息传递和全局注意力，处理树结构数据。
  - 节点特征来自LLM隐藏状态，边特征为即时奖励。
  - 输出一个 `D+2` 维的分类分布（D为最大深度），通过约束掩码确保只采样有效动作。
- **训练**：
  - 采用PPO算法优化策略。
  - 奖励函数：每一步奖励 = 步骤质量评分 - 动作成本；终止时奖励为最终答案的正确性（可与真实答案比较，因为训练时可用）。
  - 成本函数 `C(a)` 作为超参数，鼓励高效探索（如避免过度回溯）。
  - 仅需最多1000个训练样例即可收敛，无需真实推理链标注。
- **约束**：最大深度D、最大子节点数（广度限制），保证有限动作空间。

### 2.3 算法流程（文字描述）
1. 初始化根节点（提示输入）。
2. 策略根据当前树状态和动作约束，输出动作概率，采样一个合法动作。
3. 执行动作：
   - Expand：生成下一步推理文本，添加子节点。
   - Branch：跳转到当前节点的兄弟节点。
   - Backtrack：回退到指定祖先节点。
   - Terminate：终止，输出最终答案。
4. 收集转换（状态、动作、奖励、下一状态），存入回放缓冲。
5. 训练：计算折扣回报和优势，使用PPO更新策略和值网络。

## 3. 实验设计：数据集、基准和对比方法
- **数据集**：
  - 数学推理：GSM8K（4-shot）、MATH500（4-shot）、AQUA（10-shot）
  - 常识推理：StrategyQA（5-shot）
  - 逻辑推理：PrOntoQA（5-shot）、GPQA（0-shot）
  - 规划任务：Blocksworld（4步和8步，4-shot）
- **基准方法**：
  - **CoT**（标准思维链）、**CoT-SC**（自一致性，采样4或8条链后多数投票）
  - **MCTS**（基于RAP但无世界模型，仅用步骤似然作为即时奖励；包含Oracle变体——允许搜索时访问真实答案）
  - **PGTS**（无SC）、**PGTS-SC**（加权投票）
- **模型**：LLaMA3.1-8B 和 LLaMA3.1-70B，温度0.6，top_p=0.9。
- **推理步定义**：每个句子为一个步骤（Blocksworld每个行动一个句子）。
- **树参数**：最大子节点数（广度）=4，深度根据数据集设定（GSM8K为16，MATH为64等）。

## 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量或训练时长。
- 但提到：
  - PGTS策略网络非常轻量（两个GPS层+一个线性层），额外开销相比LLM生成可忽略。
  - 训练仅需最多1000个样本（每个数据集从训练集抽取），且收敛快（训练曲线显示约1000步后平稳）。
  - 对比实验中的MCTS和PGTS均使用LLaMA3.1-8B/70B进行推理，但未报告部署细节。
- 结论：资源消耗信息不完整，需读者自行估计；但框架设计强调计算效率。

## 5. 实验数量与充分性
- **实验规模**：覆盖7个数据集，2种模型大小，多种对比方法（CoT、MCTS及其变体），总实验结果呈现在表1中。
- **消融实验**：
  - 训练样本数的影响（图3：1000个示例后性能饱和）。
  - 树广度的影响（表2：AQUA上广度从2增至8）。
  - 策略组件的影响（表3：对比去除边特征/全局注意力/局部消息传递、SAN、SLM、LLM Agent），证明GPS架构和边特征的重要性。
- **公平性**：
  - 对比方法中，MCTS与PGTS共用相同的步骤似然即时奖励；MCTS Oracle虽不现实但提供了上限。
  - 所有方法生成温度、top_p一致。
  - 树广度限制一致（均为4）。
- **充分性**：实验较全面，涵盖了多种推理类型；但GPQA上PGTS不如MCTS，作者归因于训练数据有限和任务复杂，说明泛化性有局限。

## 6. 论文的主要结论与发现
- PGTS在大多数任务上显著优于CoT，并能与MCTS竞争甚至超越，同时计算代价大幅降低（例如MATH上PGTS token数仅为MCTS的约1/6）。
- 自一致性（SC）能进一步提升PGTS性能，且PGTS产生的多样化高质量链更适合加权聚合。
- 动态策略有效解决了“过度思考”问题（o1-like模型在简单问题上生成过多步骤）。
- 训练样本高效：1000个样本足以学到有效策略。
- 策略网络设计的消融表明：结合局部消息传递和全局注意力的GPS结构最好，边特征至关重要。

## 7. 优点
- **无需预定义启发式**：策略自动学习何时扩展、分支、回溯或终止。
- **计算高效**：与MCTS穷举搜索相比，大幅减少LLM调用次数（token数减少2～15倍）。
- **可扩展**：训练数据需求小，策略轻量，可适应不同任务。
- **解决“过度思考”**：通过终止动作避免不必要的推理。
- **模块化设计**：可与现有推理增强技术（如更好的奖励模型、自评估）结合。

## 8. 不足与局限
- **GPQA上性能不足**：PGTS显著低于MCTS，表明在部分复杂、知识密集型任务上泛化困难，可能受限于训练数据规模（仅1000个例子）。
- **奖励机制简单**：当前仅使用步骤似然作为即时奖励，未采用更精细的PRM或自评估，可能限制性能。
- **未保证推理链条忠实性**：论文明确承认生成的推理链可能与人类理解的逻辑不完全一致，在高压应用场景下可能产生误导。
- **资源信息缺失**：未报告训练和推理的具体算力需求，不利于复现和横向对比。
- **实验覆盖有限**：虽然数据集多样，但未涉及更多真实世界规划场景（如更复杂的PDDL问题）或更大规模模型（仅测试8B/70B）。
- **成本函数C(a)固定**：论文使用固定成本（expand=0.1, branch=0.2, backtrack=0.5, terminate=0.0），表明数据集特定调优可能进一步提升结果，但尚未探索。

（完）
