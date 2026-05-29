---
title: Embeddings as Probabilistic Equivalence in Logic Programs
title_zh: 逻辑程序中的概率等价嵌入
authors: "Jaron Maene, Efthymia Tsamoura"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rEUbDhWaXh"
tags: ["query:ns-xai"]
score: 9.0
evidence: 基于概率等价的神经符号逻辑程序
tldr: 神经符号框架通过可微松弛统一进行符号推理，但嵌入相似性违背等价传递性导致副作用。本文首次引入概率等价概念，重新设计逻辑程序中的相等性处理，缓解学习与推理中的不一致问题。为神经符号集成提供了更稳健的基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-reubdhwaxh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1321, \"height\": 698}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 356}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1033, \"height\": 225}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1415, \"height\": 1913}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 539}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 558, \"height\": 301}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 640, \"height\": 415}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 674, \"height\": 380}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 614, \"height\": 438}]"
motivation: 现有神经符号框架中嵌入相似性破坏等价传递性，影响学习与推理。
method: 引入概率等价重新定义逻辑程序中的相等性，消除传递性违背后果。
result: 提出的方法在多个神经符号任务上缓解了副作用，提升稳定性和性能。
conclusion: 概率等价比现有松弛统一更符合逻辑语义，增强神经符号集成可靠性。
---

## Abstract
The integration of logic programs with embedding models resulted in a class of neurosymbolic frameworks that jointly learn symbolic rules and representations for the symbols in the logic (constant or predicate). The key idea that enabled this integration was the differentiable relaxation of unification, the algorithm for variable instantiation during inference in logic programs. Unlike unification, its relaxed counterpart exploits the similarity between symbols in the embedding space to decide when two symbols are semantically equivalent. We show that this similarity between symbols violates the transitive law of equivalence, leading to undesirable side effects in learning and inference. To alleviate those side effects, we are the first to revamp the well-known possible world semantics of probabilistic logic programs into new semantics called equivalence semantics. In our semantics, a probabilistic logic program induces a probability distribution over all possible equivalence relations between symbols, instead of a probability distribution over all possible subsets of probabilistic facts. We propose a factorization of the equivalence distribution using latent random variables and characterize its expressivity. Additionally, we propose both exact and approximate techniques for reasoning in our semantics. Experiments on well-known benchmarks show that the equivalence semantics leads to neurosymbolic models with up to 42% higher results than state-of-the-art baselines.

---

## 论文详细总结（自动生成）

# 论文《Embeddings as Probabilistic Equivalence in Logic Programs》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经符号（neurosymbolic）框架通过将逻辑程序与嵌入模型相结合，使得符号规则和符号表示（常量和谓词）能够联合学习。其关键思想是**可微松弛的统一（soft unification）**，利用嵌入空间中符号的相似性来决定两个符号何时在语义上等价，从而替代传统逻辑编程中的精确统一。
- **核心问题**：论文指出，基于相似性的软统一**违反了等价关系的传递性**（transitivity），导致学习和推理中的不良副作用：概率质量泄漏和局部最优困境。
- **整体意义**：为了解决这些问题，论文首次提出**等价语义（equivalence semantics）**，将概率逻辑程序从“可能世界语义”（对概率事实的子集分布）重构为“对符号间所有可能等价关系的分布”，从而在神经符号集成中更忠实地遵循逻辑等价性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将不确定性从“事实是否为真”转移到“符号之间是否等价”。一个概率等价程序 \(P_e = (R, F, P_E)\) 定义在规则集 \(R\)、事实集 \(F\) 和等价关系分布 \(P_E: \mathcal{E}_U \to [0,1]\) 上。目标事实 \(\alpha\) 的概率为 \(P(\alpha) = \mathbb{E}_{e_U \sim P_E} [P|_{e_U} \models \alpha]\)，其中 \(P|_{e_U}\) 是程序在等价关系 \(e_U\) 下的饱和版本。
- **关键技术细节**：
  - **等价关系的因子分解**：为每个常量 \(c\) 引入潜在分类变量 \(V_c\)，表示其所属等价类。概率分布 \(P_E(e_U) = \sum_{\pi_e} \prod_{c \in U} P(V_c = \pi_e(c))\)，其中 \(\pi_e\) 是等价类映射。这等价于将嵌入视为概率向量，使得 \(P(a \approx b) = \sum_i P(V_a=i)P(V_b=i)\)。
  - **正定性条件**：该因子分解要求边际等价概率矩阵 \(M_{i,j}=P(c_i\approx c_j)\) 为**半正定矩阵**（Gram矩阵），限制了表达能力。
- **推理算法**：
  - **精确推理（Algorithm 1）**：先对规则进行**奇异化（singularization）**（处理重复变量），再应用**魔集变换（magic sets）**（目标导向推理），然后计算目标事实的**谱系（lineage）**，将其编码为布尔公式，最后通过**加权模型计数（WMC）** 计算概率。
  - **近似推理（Algorithm 2）**：蒙特卡洛采样方法。从潜变量分布 \(P_E\) 中采样 \(V\)，将常量替换为其等价类标签（常量抽象），得到确定性逻辑程序，然后检查是否蕴含目标事实。重复多次求平均。
- **学习**：使用梯度下降优化嵌入（通过WMC微分或REINFORCE估计器）。

## 3. 实验设计：数据集、场景、Benchmark、对比方法

- **实验场景一：知识图谱链接预测**
  - 数据集：**Countries**（S1、S2、S3三个变体）和 **Nations**（无标准划分，采用Rocktäschel & Riedel [2017]的划分）。
  - Benchmark指标：Countries用**AUC-PR**，Nations用**MRR、Hits@1/3/10**（使用随机断链，避免偏见）。
  - 对比方法：**NTP** (Neural Theorem Prover)、**GNTP** (Greedy NTP)、**CTP** (Conditional Theorem Prover)、**DeepSoftLog**（均为基于软统一的神经符号方法）。
- **实验场景二：可微有限状态机**
  - 数据：**MNIST图像序列**，三种二元语言：01重复、恰好一个1、偶数个1。先给20个数字示例进行概念监督，然后在长度4序列上训练，测试长度8的序列（跨长度泛化）。
  - 对比方法：DeepSoftLog 和 **RNN**。
- **额外实验**（附录）：在 **Kinship** 和 **UMLS** 知识图谱上补充实验，采用Qu et al. [2021]的划分和评估。

## 4. 资源与算力

- 论文明确说明：**无GPU计算**，仅使用CPU（Intel i7-12700，64GB RAM）。单个实验运行时间：可微有限状态机约3分钟，Countries需3-5小时，Nations约1小时。未提及GPU型号或数量，因未使用。

## 5. 实验数量与充分性

- **实验组数**：主论文包含：
  - 知识图谱：Countries三个变体 + Nations，共4组任务，每组10个随机种子（报告均值和标准差）。
  - 可微FSM：三种语言，每组10个种子。
  - 附录：Kinship和UMLS各一组，10个种子。
- **消融/分析**：未单独设置消融实验，但对超参数进行了调优（如Nations使用贝叶斯调优）。
- **充分性与公平性**：
  - 使用了多种数据集（规模、领域不同），覆盖不同任务类型（链接预测与序列分类）。
  - 对比了多种最先进基线，且使用相同模板规则。
  - 对Nations采用随机断链，避免结果偏见（Sun et al., 2020指出）。
  - 报告了标准差，体现稳定性。
  - **不足**：缺少与同类型基于等价的推理方法的直接对比（因为本文是首次提出），主要对比对象均为软统一方法。此外，未进行大规模数据集（如FB15k-237）的实验，可能受限于概率推理的可扩展性。

## 6. 论文的主要结论与发现

- **理论发现**：软统一违反等价传递性，导致概率质量泄漏和函数非多线性，引入学习困难。
- **方法效果**：提出的**等价语义**在链接预测任务上优于所有基线（Countries S3提升约2% AUC-PR，Nations MRR提升至0.724，Hits@1达0.591）。
- **可微FSM**：在三种语言上接近完美（AUC-PR >99%），远优于DeepSoftLog和RNN。
- **总体**：强制遵守传递性显著提升神经符号模型性能，验证了逻辑语义一致性的重要性。

## 7. 优点

- **理论严谨性**：首次从语义层面解决软统一的传递性问题，提供了严格的概率解释和因子分解。
- **方法创新**：将等价关系分布与嵌入学习结合，提出可微分的推理管线（精确+近似）。
- **实验设计公平**：对Nations采用随机断链，避免以往论文中的偏见；报告多种子统计。
- **跨任务验证**：在链接预测和序列分类两个不同领域验证，展示泛化能力。
- **开源性**：提供代码和补充资料，便于复现。

## 8. 不足与局限

- **计算复杂性**：精确推理需要WMC，对大型程序仍可能昂贵；近似推理使用蒙特卡洛采样，梯度估计方差高，限制了规则学习的规模。
- **表达能力受限**：因子分解假设常量独立性，仅能表示半正定边际概率矩阵，部分等价关系分布可能无法建模。
- **依赖模板规则**：仍然需要手工定义规则模板，未能完全自动化规则发现。
- **实验覆盖有限**：未在更大知识图谱（如WN18RR、FB15k-237）或更复杂逻辑语言（如非单调逻辑）上测试；仅测试了Datalog子集。
- **无消融研究**：未分析因子分解中不同潜在变量维度、先验分布等的影响。
- **应用限制**：当前方法主要适用于Datalog，扩展到含函数符或概率编程语言（如ProbLog、dPASP）需额外工作。

（完）
