---
title: Primal-Dual Neural Algorithmic Reasoning
title_zh: 原始-对偶神经算法推理
authors: "Yu He, Ellen Vitercik"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=iBpkzB5LEr"
tags: ["query:ns-xai"]
score: 8.0
evidence: 使用原始-对偶范式的神经算法推理实现可解释推理
tldr: 针对神经算法推理难以扩展到困难问题，提出基于原始-对偶范式的通用框架。通过建立原始变量与对偶变量的二部图表示，将经典近似算法与图神经网络对齐，并结合小实例最优解增强推理能力。实验表明该方法在多项NP难问题上显著提升了推理性能与可解释性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ibpkzb5ler/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1582, \"height\": 490, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1719, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1716, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 785, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 761, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1434, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1258, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1431, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ibpkzb5ler/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1260, \"height\": 412, \"label\": \"Table\"}]"
motivation: 现有神经算法推理局限于多项式可解问题，难以处理更困难的问题。
method: 基于原始-对偶范式，利用二部图表示对齐算法与图神经网络。
result: 在多项困难问题上取得优异的推理性能。
conclusion: 该框架扩展了神经算法推理的能力边界，兼具可解释性。
---

## Abstract
Neural Algorithmic Reasoning (NAR) trains neural networks to simulate classical algorithms, enabling structured and interpretable reasoning over complex data. While prior research has predominantly focused on learning exact algorithms for polynomial-time-solvable problems, extending NAR to harder problems remains an open challenge. In this work, we introduce a general NAR framework grounded in the primal-dual paradigm, a classical method for designing efficient approximation algorithms. By leveraging a bipartite representation between primal and dual variables, we establish an alignment between primal-dual algorithms and Graph Neural Networks. Furthermore, we incorporate optimal solutions from small instances to greatly enhance the model’s reasoning capabilities. Our empirical results demonstrate that our model not only simulates but also outperforms approximation algorithms for multiple tasks, exhibiting robust generalization to larger and out-of-distribution graphs. Moreover, we highlight the framework’s practical utility by integrating it with commercial solvers and applying it to real-world datasets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：神经算法推理（Neural Algorithmic Reasoning, NAR）旨在训练神经网络模拟经典算法，实现结构化、可解释的推理。现有NAR工作主要聚焦于多项式时间可解问题（如CLRS-30中的排序、搜索、图算法），但扩展到NP-hard问题面临挑战：难以可靠生成真实标签轨迹，且缺乏通用框架。
- **核心问题**：如何构建一个通用的NAR框架，使其能够学习并模拟求解NP-hard问题的近似算法，同时利用小规模实例的最优解提升性能，超越算法本身的保证。
- **整体含义**：提出基于原始-对偶范式的神经算法推理框架（PDNAR），将经典原始-对偶近似算法与图神经网络（GNN）对齐，首次实现NAR在NP-hard问题上的通用学习与超越。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：
  - 利用原始-对偶近似算法的通用框架（Algorithm 1，以最小击中集为例），将问题表示为二部图：左侧为原始变量（元素e），右侧为对偶变量（集合T），边表示元素属于集合。
  - 设计GNN架构，在二部图上进行消息传递，模拟算法的迭代过程：每一步计算对偶增量δ_T，更新剩余权重r_e，当r_e=0时将该元素加入解集。
  - 引入虚拟节点（uniform increase规则）实现全局同步增加对偶变量。
  - 除了从算法中间状态学习，还利用小规模实例的整数规划最优解作为额外监督信号，使模型能够超越近似算法的性能。

- **关键技术细节**：
  - **编码器-处理器-解码器架构**：编码器将剩余权重和节点度数映射到潜在空间；处理器采用消息传递GNN，在二部图上执行“原始→对偶”和“对偶→原始”两步更新；解码器预测是否选中元素、新的剩余权重和对偶增量。
  - **训练策略**：带噪声的教师强制（noisy teacher forcing），以0.5概率使用真实中间量作为下一时间步输入。
  - **损失函数**：各时间步的算法中间量损失（BCE+ MSE）加上最后时间步的最优解损失。
  - **理论保证**：证明存在8层PDNAR参数配置可以精确复制Algorithm 1的每一步，从而继承其近似比保证（例如MVC的2/(1-ε)近似）。

## 3. 实验设计

- **数据集与场景**：
  - **合成算法数据集**：最小顶点覆盖（MVC，图：Barabási-Albert图）、最小集合覆盖（MSC，Barabási-Albert二部图）、最小击中集（MHS，Barabási-Albert二部图）。训练图大小16节点，测试图大小从16到1024节点（2倍至64倍外推）。
  - **OOD泛化**：MVC测试Erdős–Rényi、Star、Lobster、3-Connected Planar图；MSC/MHS测试不同优先连接参数b=3和8。
  - **真实世界数据集**：Airports（巴西、欧洲、美国）节点分类任务，预测机场活动量等级。
  - **商业求解器热启动**：用Gurobi求解MVC，对比无热启动、算法热启动、PDNAR热启动，评估求解时间。

- **Benchmark与对比方法**：
  - 合成数据：GIN、GAT（端到端节点分类）；NAR（MPNN）、TripletMPNN（仅用原始变量中间量）；PDNAR的消融变体（No algo、No optm）以及不同聚合方式（mean、max）。
  - 真实数据：GCN、GAT、GraphSAGE作为基模型，分别结合LapPE、RWPE、Degree、Node2Vec、PDNAR嵌入。
  - 热启动：对比无热启动、算法热启动、PDNAR热启动。

## 4. 资源与算力

- **文中明确说明**：所有GPU实验在Nvidia Quadro RTX 8000（48GB内存）上进行；Gurobi实验在Intel Xeon E7-8890x（144核，12TB内存）上进行。
- **未说明**：训练时长、具体种子次数、总计算量未明确给出。仅提到“重复10个种子”（测试）和“5个种子”（Gurobi实验）。

## 5. 实验数量与充分性

- **实验数量**：
  - 合成数据：3个任务 × 7种图规模 × 多种对比方法 × 10个种子 → 约数百组实验。
  - OOD泛化：3个任务 × 不同OOD图类型 × 7种规模 × 10个种子。
  - 真实数据：3个数据集 × 3种基模型 × 约7种嵌入方法 → 每组平均10个随机分割。
  - 热启动：3种图规模（500/600/750）× 3种初始方法 × 5个种子。
  - 消融实验：包含No algo、No optm、不同聚合方式的消融。

- **充分性与公平性**：
  - 合成数据对比了多种基线（包括端到端GNN、经典NAR、更复杂的TripletMPNN），消融完整，实验设计较全面。
  - OOD泛化覆盖多种图结构，验证了模型鲁棒性。
  - 真实数据与多种嵌入方法公平对比，且基模型使用相同超参数搜索。
  - Gurobi实验设置合理（线程、时间限制、随机种子）并与算法基线对比。
  - 总体实验充分，客观性较好，但缺乏与其他近期NAR NP-hard方法（如Georgiev et al. 2023c）的直接定量比较（仅在文中定性讨论）。

## 6. 主要结论与发现

1. **PDNAR可精确模拟原始-对偶近似算法**：理论证明存在参数化可复制算法步骤，并继承其近似保证。
2. **超越所模拟的算法**：通过结合最优解监督，PDNAR在多项任务上获得比原始近似算法更优的权重比（<1），首次实现NAR超越算法本身。
3. **强泛化能力**：在16节点训练，可稳健推广至1024节点（64倍外推），且对OOD图类型（Erdős–Rényi、Star等）表现良好。
4. **实际应用价值**：
   - 在Airports数据集上，PDNAR嵌入显著提升下游节点分类准确率（最高+20%以上）。
   - 热启动Gurobi求解MVC时，PDNAR不仅求解时间最短，且推理速度比近似算法快约10倍。

## 7. 优点

- **通用性**：基于原始-对偶范式，可覆盖多个NP-hard问题（顶点覆盖、集合覆盖、击中集等），且底层算法可扩展至其他问题（如Steiner树、设施选址等）。
- **算法对齐与可解释性**：严格证明PDNAR能精确模仿算法步骤，提供了理论解释性。
- **超越算法的性能**：创造性利用小实例最优解提升最终解质量，突破了近似算法的最坏情况界限。
- **强泛化与实用性**：对大规模和OOD图的有效性，以及真实世界数据和商业求解器的集成，展示了真实应用潜力。
- **消融全面**：明确了算法中间步骤和最优解各自贡献，验证了架构设计的必要性。

## 8. 不足与局限

- **当前架构局限于击中集问题**：虽然击中集可覆盖许多问题，但某些问题（如设施选址需两类对偶变量）需要架构扩展。
- **缺乏直接与现有NAR NP-hard方法的定量比较**：仅与Georgiev et al. (2023c)定性对比，未在相同基准上比较性能。
- **最坏情况保证可能丢失**：模型训练基于数据分布，不一定保持最坏情况近似比（但作者认为实际场景中更常见）。
- **计算资源消耗未全面报告**：缺少训练时间、GPU小时数等详细信息，复现成本不明确。
- **真实数据集规模较小**：Airports数据集节点数仅数百至千，未在更大规模真实图上验证。
- **对大规模图（1024节点）的MHS任务表现略有退化**（比例1.027），泛化仍有提升空间。
- **未探索多任务学习**：未来工作可同时训练多个近似算法进一步提升性能。

（完）
