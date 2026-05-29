---
title: Convex and Bilevel Optimization for Neural-Symbolic Inference and Learning
title_zh: 神经符号推理与学习的凸优化及双层优化方法
authors: "Charles Andrew Dickens, Changyu Gao, Connor Pryor, Stephen Wright, Lise Getoor"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=6NQ77Vj3DT"
tags: ["query:ns-xai"]
score: 9.0
evidence: 通过凸优化和双层优化进行神经符号推理与学习
tldr: 针对神经符号系统的参数学习效率问题，提出基于凸优化和双层优化的通用梯度框架。通过光滑原始-对偶公式和块坐标下降算法，在NeuPSL架构上实现超过100倍的学习速度提升，并在8个数据集上展示了广泛适用性，极大推动了神经符号集成的发展。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-6nq77vj3dt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-6nq77vj3dt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1578, \"height\": 574, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 839, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1196, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1192, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1111, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1511, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1595, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1486, \"height\": 1540, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1029, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 766, \"height\": 1142, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 978, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 949, \"height\": 753, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 883, \"height\": 2201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1080, \"height\": 942, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6nq77vj3dt/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1139, \"height\": 639, \"label\": \"Table\"}]"
motivation: 现有神经符号系统推理缓慢，参数学习效率低。
method: 提出光滑原始-对偶公式，并设计利用热启动的双块坐标下降算法。
result: 在NeuPSL架构上实现超过100倍的学习速度提升。
conclusion: 该框架为神经符号系统的可扩展学习提供了高效方案。
---

## Abstract
We leverage convex and bilevel optimization techniques to develop a general gradient-based parameter learning framework for neural-symbolic (NeSy) systems. We demonstrate our framework with NeuPSL, a state-of-the-art NeSy architecture. To achieve this, we propose a smooth primal and dual formulation of NeuPSL inference and show learning gradients are functions of the optimal dual variables. Additionally, we develop a dual block coordinate descent algorithm for the new formulation that naturally exploits warm-starts. This leads to over $100 \times$ learning runtime improvements over the current best NeuPSL inference method. Finally, we provide extensive empirical evaluations across $8$ datasets covering a range of tasks and demonstrate our learning framework achieves up to a $16$% point prediction performance improvement over alternative learning methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：神经符号（NeSy）系统融合了神经网络处理低层数据的能力与符号系统对高层结构的推理能力，但在参数学习上面临关键挑战：其推理问题通常非光滑、带约束，导致预测不显式、不可微，传统深度学习技术无法直接应用。现有NeSy学习方法要么推理缓慢，要么梯度计算复杂。
- **核心问题**：如何设计一个通用的、基于梯度的NeSy学习框架，既能保证端到端可微，又能高效进行推理和参数更新。
- **整体含义**：该工作为NeSy系统的可扩展学习提供了理论基础和实用算法，显著提升了学习速度和预测性能，推动了神经符号集成的发展。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 核心思想
- 将NeSy学习建模为**双层优化**问题：上层是学习目标（如监督损失+值函数损失），下层是推理优化（能量函数的最小化）。
- 通过**Moreau包络**平滑非光滑能量函数，使下层问题可微。
- 针对NeuPSL架构，将推理重写为**线性约束二次规划（LCQP）**，并引入正则化确保强凸性。
- 提出**对偶块坐标下降（dual BCD）**算法直接求解对偶LCQP，得到最优对偶变量用于计算梯度。

### 关键技术细节
- **Moreau包络**：用$M_i(y; \mathbf{w}_{sy}, \mathbf{w}_{nn}, \rho) = \inf_{\hat{y}} \{ E(\hat{y}) + \frac{1}{2\rho} \|\hat{y}-y\|^2 \}$替换原始能量函数，使目标函数光滑且保持全局最小值。
- **双层优化松弛**：将原始双层问题转化为约束松弛形式（允许约束违反度$\iota$），并用增广拉格朗日方法求解。
- **深度HL-MRF能量函数**：$E(\mathbf{y}) = \mathbf{w}_{sy}^T \Phi(\mathbf{y})$，其中$\Phi$是铰链损失势函数。
- **LCQP形式**：引入松弛变量，将推理转化为$\min_\nu \nu^T (D+\epsilon I)\nu + c^T \nu$，线性约束$A\nu + b \le 0$。
- **对偶问题**：$\min_{\mu \ge 0} \frac{1}{4} \mu^T A (D+\epsilon I)^{-1} A^T \mu + \frac{1}{2} (A(D+\epsilon I)^{-1} c - 2b)^T \mu$。
- **梯度形式**：对符号权重的梯度为$\nabla_{\mathbf{w}_{sy}} V = \Phi(\mathbf{y}^*)$；对神经权重的正则次梯度通过对偶变量计算。
- **算法流程**：
  1. 初始化权重和$\iota$；
  2. 外循环逐渐减小$\iota$；
  3. 内循环用增广拉格朗日法优化平滑子问题；
  4. 用dual BCD求解推理，利用热启动加速。
- **并行化策略**：连通分量并行（CC D-BCD）和无锁并行（LF D-BCD）。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法
- **数据集**：8个数据集，涵盖立场分类、链接预测、回归、节点分类、图像分类等任务：
  - Debate（姿势分类）、4Forums（姿势分类）、Epinions（链路预测）、DDI（药物相互作用链路预测）
  - Yelp（回归）、Citeseer（节点分类）、Cora（节点分类）、MNIST-Add（图像分类，两种规模：MNIST-Add1和MNIST-Add2）
- **Benchmark**：默认采用5折交叉验证，报告平均值和标准差。Deep HL-MRF实验中采用10折（Citeseer/Cora低数据设置）。
- **对比方法**：
  - **推理对比**：ADMM（最先进的NeuPSL推理）、Gurobi、子梯度下降、CC D-BCD、LF D-BCD。
  - **学习对比**：值函数损失（Energy、Structured Perceptron） vs. 本文双层优化框架下的MSE和BCE损失。
  - **Deep HL-MRF对比**：DeepStochLog、GCN、逻辑张量网络(LTN)、DeepProblog。
- **评价指标**：AUROC、MAE、Accuracy（依据任务）。

## 4. 资源与算力
- 论文**未明确说明GPU型号、数量或训练时长**。所有时序实验在**Ubuntu 22.04.1 Linux机器**上运行，配置为**Intel Xeon Processor E5-2630 v4 @ 3.10GHz，128GB RAM**。无GPU加速信息，推测部分实验（如MNIST-Add中的神经网络）可能使用了GPU，但文中未详述。

## 5. 实验数量与充分性
- **推理时序实验**：在8个数据集上对比了ADMM、CC D-BCD、LF D-BCD三种算法，并进行了超参数搜索（步长、正则化参数等），给出了平均时间及标准差。
- **学习运行时实验**：在9个数据集（含MNIST-Add两种规模）上对比了ADMM与D-BCD在SP和MSE损失下的累积推理时间，表明D-BCD可将学习快100倍以上。
- **预测性能实验**：
  - HL-MRF学习：7个非深度数据集（不含MNIST-Add），对比Energy、SP、MSE、BCE四种损失。
  - Deep HL-MRF学习：Citeseer、Cora（低数据10次随机分割），MNIST-Add1/2（不同训练样本数300/3000/150/1500）。
  - 每个实验均在5或10个数据划分上重复，报告均值和标准差。
- **消融实验**：附录F.3研究了LCQP正则化参数$\epsilon$对推理时间和性能的影响，范围$10^{-2}$到$100$，展示了时间复杂度与精度的权衡。
- **充分性评价**：数据集覆盖多个任务类型，对比方法涵盖主流NeSy基线，超参数进行了网格搜索，实验复现性强。但缺少对更大规模数据集（如Wiki、知识图谱）的验证，以及与其他双层优化方法（如隐式微分）的直接对比。

## 6. 论文的主要结论与发现
- **推理加速**：提出的dual BCD（尤其LF D-BCD）在大多数数据集上显著快于ADMM，在DDI上实现约100×学习速度提升。
- **预测性能提升**：使用双层优化框架（MSE/BCE）训练的NeuPSL模型在几乎所有数据集上优于传统的值函数损失方法。特别是在Cora上，BCE损失比SP高6%以上；在MNIST-Add2（低数据）上，BCE比Energy高16%以上。
- **热启动有效性**：D-BCD能有效利用热启动，降低累积学习时间，而ADMM的热启动效果不明显。
- **并行策略互补**：CC D-BCD适合连通分量多的稀疏图（如MNIST-Add），LF D-BCD适合大型连通图（如Yelp、DDI）。
- **理论贡献**：给出了NeuPSL能量函数值函数关于符号权重的显式梯度，以及对偶变量与神经权重梯度的联系。

## 7. 优点
- **理论严谨**：将Moreau包络、双层优化、增广拉格朗日方法系统引入NeSy领域，证明了可微性和梯度形式。
- **通用性强**：框架适用于一类NeSy能量模型（NeSy-EBM），不仅限于NeuPSL。
- **实用性强**：dual BCD算法专为LCQP推理设计，直接产生对偶变量从而避免伪逆计算，且天然支持并行化和热启动。
- **实验全面**：覆盖8个不同任务的数据集，对比了多种基线和损失函数，同时评估了推理和学习两方面的效率。
- **并行化贡献**：提出两种并行策略（CC D-BCD和LF D-BCD），适应不同图结构。

## 8. 不足与局限
- **假设限制**：需要下层推理唯一解（Assumption 4.1）以及值函数可微（Assumption 4.2），限制了部分非凸或非光滑能量模型的应用。
- **实验覆盖**：
  - 对比的基线不够丰富：未与隐式微分（implicit differentiation）类双层优化方法直接比较。
  - 仅测试了NeuPSL架构，未在其他NeSy系统（如SATNet、LTN）上验证框架通用性。
- **近似求解**：内循环使用增广拉格朗日求近似解，收敛速率依赖问题结构；论文承认该方向仍开放。
- **硬件信息缺失**：未明确说明GPU使用情况，影响可复现性和效率评估的精确性。
- **正则化参数敏感**：附录F.3表明LCQP正则化$\epsilon$对性能和时间有显著影响，需要调参。
- **MNIST-Add上的并行效果**：MNIST-Add中LF D-BCD反而比CC D-BCD慢（因为连通组件多），需要用户根据问题选择策略。

（完）
