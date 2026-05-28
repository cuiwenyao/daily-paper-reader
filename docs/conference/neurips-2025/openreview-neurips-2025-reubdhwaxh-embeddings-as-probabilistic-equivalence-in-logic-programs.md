---
title: Embeddings as Probabilistic Equivalence in Logic Programs
title_zh: 逻辑程序中作为概率等价的嵌入
authors: "Jaron Maene, Efthymia Tsamoura"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rEUbDhWaXh"
tags: ["query:ns-xai"]
score: 9.0
evidence: 解决微分合一中传递性问题的神经符号集成方法
tldr: 神经符号框架通过微分放松逻辑合一实现规则与嵌入联合学习，但放松后的等价性违反传递律导致副作用。本文重新引入位置评分机制，在保持可微分的同时恢复传递性，避免了符号等价性的不一致。实验表明该方法在多个知识图谱任务中提升了学习稳定性和推理准确性，深化了对神经符号集成的理论理解。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-reubdhwaxh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1321, \"height\": 698, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1033, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1415, \"height\": 1913, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 558, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 640, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 674, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-reubdhwaxh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 614, \"height\": 438, \"label\": \"Table\"}]"
motivation: 可微分统一放松了传递律，导致学习与推理中的不良副作用。
method: 通过重审位置评分，在保持可微分性的同时恢复等价传递性。
result: 在知识图谱推断中提高了稳定性和准确性，优于先前神经符号方法。
conclusion: 正确建模等价性是神经符号学习成功的关键。
---

## Abstract
The integration of logic programs with embedding models resulted in a class of neurosymbolic frameworks that jointly learn symbolic rules and representations for the symbols in the logic (constant or predicate). The key idea that enabled this integration was the differentiable relaxation of unification, the algorithm for variable instantiation during inference in logic programs. Unlike unification, its relaxed counterpart exploits the similarity between symbols in the embedding space to decide when two symbols are semantically equivalent. We show that this similarity between symbols violates the transitive law of equivalence, leading to undesirable side effects in learning and inference. To alleviate those side effects, we are the first to revamp the well-known possible world semantics of probabilistic logic programs into new semantics called equivalence semantics. In our semantics, a probabilistic logic program induces a probability distribution over all possible equivalence relations between symbols, instead of a probability distribution over all possible subsets of probabilistic facts. We propose a factorization of the equivalence distribution using latent random variables and characterize its expressivity. Additionally, we propose both exact and approximate techniques for reasoning in our semantics. Experiments on well-known benchmarks show that the equivalence semantics leads to neurosymbolic models with up to 42% higher results than state-of-the-art baselines.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经符号框架通过可微分的“软统一”（soft unification）将逻辑程序与嵌入模型集成，允许基于符号在嵌入空间中的相似度决定语义等价。然而，论文指出这种相似度机制违反了等价关系应满足的**传递律**（如 a≈b 且 b≈c 不能推出 a≈c），这会导致**概率质量泄漏**（不必要的可能世界被赋予非零概率）和**局部最优**（概率函数不再是嵌入的多线性多项式，优化困难）。
- **整体含义**：要正确地在逻辑程序中引入等价性，必须从语义层面确保传递性，而非仅依赖相似度。论文旨在为概率逻辑程序建立一种新的**等价语义**，从而克服软统一的根本缺陷，实现更稳定有效的规则与嵌入联合学习。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出**概率等价语义（equivalence semantics）**。传统可能世界语义在事实子集上定义分布，而等价语义直接在符号间的等价关系上定义概率分布 \(P_E: \mathcal{E}_U \to [0,1]\)。程序在给定等价关系下被“饱和”（saturation），使得等价符号可互换，再计算目标事实的推导概率。
- **关键技术细节**：
  - **因子化等价分布**：将每个常量 \(c\) 关联一个独立潜分类变量 \(V_c\)，其概率向量作为常量嵌入。等价关系概率视为所有常量被分配到相同簇的概率乘积：
    \[
    P_E(e_U) = \sum_{\pi_e} \prod_{c\in U} P(V_c = \pi_e(c))
    \]
    这使计算等价事实概率简化为内积：\(P(a\approx b) = \sum_i P(V_a=i)P(V_b=i)\)。
  - **精确推理**：通过**奇异化（singularization）** 和**魔法集变换（magic sets）** 将带等价的Datalog程序转化为标准Datalog，再计算布尔公式的加权模型计数（WMC）。
  - **近似推理**：基于蒙特卡洛采样，先采样潜变量具体值，然后对实例化后的程序执行标准Datalog推理；梯度估计使用REINFORCE加留一法基线。
- **算法流程**（文字描述）：
  - 精确推理：对规则进行奇异化 → 应用魔法集转换 → 计算查询的谱系（lineage） → 编码为布尔公式 → 加权模型计数得到概率。
  - 近似推理：对规则应用魔法集 → 采样潜变量 → 常量抽象（替换为等价类代表） → 前向推理得到是否蕴含 → 多次采样取均值。

## 3. 实验设计：数据集、基准、对比方法

- **数据集与场景**：
  - **链接预测**：使用两个小知识图谱 **Countries**（三个变体S1/S2/S3）和 **Nations**；附录还补充了 **UMLS** 和 **Kinship**。
  - **序列分类**：可微有限状态机，三个二元语言：\((01)^*\)、\(0^*10^*\)、\((0|10^*1)^*\)，输入为MNIST图像序列。
- **评价指标**：Countries用AUC-PR；Nations用MRR、Hits@1/3/10（随机打破平局）；序列分类用AUC-PR。
- **对比方法**：
  - 链接预测：NTP、GNTP、CTP、DeepSoftLog（均为基于软统一的神经符号方法）。
  - 序列分类：DeepSoftLog、RNN。
- **实验设置**：10个随机种子，报告均值和标准差；超参数通过验证集调整（如Nations做了贝叶斯调参）；使用与NTP/DeepSoftLog相同的规则模板；近似推理采样100个样本。

## 4. 资源与算力

- 论文明确说明：所有实验在**Intel i7-12700 CPU和64GB RAM**服务器上运行，**未使用GPU或TPU**。
- 典型运行时间：可微有限状态机约3分钟，Countries实验3–5小时，Nations约1小时。算力需求不高。

## 5. 实验数量与充分性

- **实验数量**：涉及两类任务共7个数据集/变体，每个实验重复10次，结果稳定。附录还补充了UMLS和Kinship的结果。消融实验未见明确提及，但通过不同任务和指标已能支撑主要结论。
- **充分性**：实验覆盖了不同难度、不同领域的知识图谱以及序列分类场景，对比方法均为最新基线。但存在局限：知识图谱规模较小（Countries/Nations），未测试更大图谱（如WN18RR、FB15k-237）；仅使用固定规则模板，对自动规则学习的泛化性验证不足；对近似推理中采样数、熵正则化强度等超参数的影响未做系统性敏感性分析。总体公平性较好，但消融实验可更丰富。

## 6. 论文的主要结论与发现

- **主要结论**：提出的**等价语义**在链接预测和序列分类上均显著优于所有现有软统一方法，最高提升**42%**（如Countries S3 AUC-PR从97.9%提升到99.89%，Nations MRR从0.709提升到0.724，FSM语言中达到接近100%）。说明正确建模等价关系的传递性对神经符号学习的稳定性和准确性至关重要。
- **关键发现**：软统一导致的概率泄漏和局部最优在实践中确实损害性能；通过潜变量因子化的等价分布可以在保持可微分的同时恢复传递性，且计算开销可控。

## 7. 优点：方法或实验设计上的亮点

- **理论贡献**：首次系统揭示软统一违反传递律的副作用，并提供了形式化分析（定理2、3）。
- **语义创新**：提出的等价语义将不确定性从“事实是否存在”转移到“符号是否等价”，更自然地处理符号同义性，且与可能世界语义兼容。
- **推理技术**：结合奇异化、魔法集变换和加权模型计数，保证了精确推理的理论正确性；蒙特卡洛近似适用于大规模场景。
- **实验设计**：采用随机平局打破避免结果偏差；重复10次报告均值和标准差，结果可靠；在多个任务上验证了方法的通用性。

## 8. 不足与局限

- **梯度估计**：近似推理依赖REINFORCE，方差较高，论文也承认需要更高效的梯度估计方法。
- **规则模板依赖**：方法仍需预定义规则模板，限制了自动规则发现的能力，也使得在大规则空间下精确推理变得困难。
- **扩展性**：未实验大规模知识图谱（如WN18RR），也未讨论如何扩展到非单调逻辑或更多表达性的概率语言（如ProbLog的复杂结构）。
- **消融分析不足**：缺少对采样数、熵正则化强度、不同因子化假设的消融实验，对方法鲁棒性的理解有限。
- **应用限制**：当前假设每个常量独立分配到簇，尽管提供了正向半定性保证（边际矩阵正半定），但可能无法表达所有等价分布，存在一定表达力上限。

（完）
