---
title: Neural Model Checking
title_zh: 神经模型检测
authors: "Mirco Giacobbe, Daniel Kroening, Abhinandan Pal, Michael Tautschnig"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=dJ9KzkQ0oH"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经网络与符号推理结合用于形式验证
tldr: 针对传统符号模型检测计算成本高的问题，本文提出神经模型检测方法，将神经网络作为线性时态逻辑的形式化证明证书，并利用SAT求解器符号验证证书有效性。该方法在硬件验证任务上取得高效结果，展示了神经网络与符号推理结合解决形式验证问题的潜力，为可信AI提供了新工具。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1406, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 989, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1243, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1410, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1326, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dj9kzkq0oh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 440, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1406, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1412, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 868, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 708, \"height\": 2212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 714, \"height\": 2218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 711, \"height\": 1976, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-dj9kzkq0oh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 704, \"height\": 1982, \"label\": \"Table\"}]"
motivation: 符号模型检测算法虽可靠但计算代价大，急需新范式平衡效率与形式保证。
method: 训练神经网络从随机系统执行中学习LTL证明证书，再用SAT求解器符号验证证书。
result: 在基准验证任务上，神经证书生成速度快，符号验证准确率高。
conclusion: 神经网络可作为符号推理的补充，形成高效且形式保证的验证方法。
---

## Abstract
We introduce a machine learning approach to model checking temporal logic, with application to formal hardware verification. Model checking answers the question of whether every execution of a given system satisfies a desired temporal logic specification. Unlike testing, model checking provides formal guarantees. Its application is expected standard in silicon design and the EDA industry has invested decades into the development of performant symbolic model checking algorithms. Our new approach combines machine learning and symbolic reasoning by using neural networks as formal proof certificates for linear temporal logic. We train our neural certificates from randomly generated executions of the system and we then symbolically check their validity using satisfiability solving which, upon the affirmative answer, establishes that the system provably satisfies the specification. We leverage the expressive power of neural networks to represent proof certificates as well as the fact that checking a certificate is much simpler than finding one. As a result, our machine learning procedure for model checking is entirely unsupervised, formally sound, and practically effective. We experimentally demonstrate that our method outperforms the state-of-the-art academic and commercial model checkers on a set of standard hardware designs written in SystemVerilog.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的符号模型检测（symbolic model checking）虽然能提供形式化保证，但其算法（如基于BDD或SAT的固定点计算）在处理复杂算术数据路径时计算开销巨大，即使较小的电路模块也可能需要数天甚至无法完成。因此，工业界常采用有界模型检测（bounded model checking）牺牲全局正确性。论文希望提出一种新的机器学习方法，在不牺牲形式化保证的前提下提高模型检测的可扩展性。
- **整体含义**：论文首次将神经网络作为线性时态逻辑（LTL）模型检测的证明证书（proof certificates），通过“学习+符号检查”的框架实现无监督、形式正确且实际有效的硬件验证。该方法在标准硬件设计上优于当前最先进的学术和商业模型检测器，为硬件验证领域提供了新的范式。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用神经网络表示LTL模型检测的排名函数（ranking function），该函数在系统与Büchi自动机的同步组合中严格单调递减（当自动机处于公平状态时）且不增加（其他情况下），从而证明所有执行都是不公平的，即系统满足规范。神经网络从随机生成的执行轨迹中训练得到，再通过SMT求解器符号验证其在整个状态空间上的有效性。
- **关键技术细节**：
  - **问题归约**：将LTL模型检测归约为语言包含问题，进一步转化为公平终止问题（fair emptiness problem），需要寻找一个排名函数V，满足条件：(1)从任何状态(s,q)到(s',q')的转移，V不增加；(2)若q是公平状态，则V严格减小。存在这样的排名函数即证明系统满足规范。
  - **神经排名函数**：使用一个前馈神经网络V(r;θ_q)，其中r是系统寄存器状态向量，θ_q是与自动机状态q关联的可训练参数。网络包含归一化层、逐元素乘法层和两个隐藏层（8和5个神经元）的多层感知机，激活函数为Clamp(·;u)。
  - **训练**：随机生成有限长度执行轨迹，构成数据集D（包含连续状态对）。损失函数为LRank = ReLU( V(r';θ_q') - V(r;θ_q) + ε·1_F(q) )，当达到零损失时，条件(1)(2)在数据集上满足。同时训练时按自动机状态顺序优化，避免局部极小。
  - **验证**：将神经网络量化为固定点算术（量化参数θ̃≈2^f·θ），将排名函数条件翻译为位向量理论的SMT查询（公式5）。若SMT求解器判定不可满足，则证明排名函数全局有效；否则得到反例，添加回数据集并重新训练。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：使用10个参数化的硬件设计（延迟模块、LCD控制器、热电偶、7段数码管、I2C拉伸、PWM、VGA控制器、UART发射器、Load-Store、格雷计数器），通过调整参数生成194个验证任务，覆盖不同状态空间大小和逻辑门数量。
- **Benchmark**：每个设计对应一个或多个LTL规范（如FG!rst→GF sig），任务要求证明系统满足该规范。
- **对比方法**：
  - 学术工具：ABC（Super Prove套件）和nuXmv（最新版本2.0.0）
  - 工业工具：两个商用SystemVerilog验证工具（工具X和工具Y，匿名化）
  - 所有工具使用5小时超时限制。

## 4. 资源与算力

- 论文明确说明实验运行在 **Intel Xeon 2.5 GHz处理器**，**8线程**，**32 GB RAM**，操作系统为Ubuntu 20.04。
- 未提及使用GPU；PyTorch训练、SMT求解（Bitwuzla）、模型检测等均在CPU上进行。
- 每个任务最多5小时；所有任务总计算时间约为104天11小时（包含超时任务按5小时计）。

## 5. 实验数量与充分性

- **实验数量**：总共194个验证任务，覆盖10种不同设计，每种设计包含十几个到三十几个参数变化的任务。
- **充分性**：
  - 对比了学术和工业领域最先进的模型检测器，评估标准包括完成数量、运行时间、可扩展性等。
  - 进行了消融研究（Ablation Study）——测试不同隐藏层大小（3,2）、（5,3）、（15,8）、额外全连接层（ExtL）和单一化排名函数（Mono）等配置，分析了9种变体在全部194个任务上的表现。
  - 实验设置公平：所有工具在相同硬件和时间限制下运行，并报告了每个任务的详细运行时间（见表3、表4）。
  - 论文还讨论了方法失效的原因（如VGA设计无法收敛到零损失）以及UART设计下相对较慢的情况。

## 6. 论文的主要结论与发现

- **主要结论**：提出的神经模型检测方法在5小时时间预算内，平均比ABC多完成60%的任务，比nuXmv多34%，比领先商业工具多11%。在完成的任务中，67%的任务比学术工具更快（34%快10倍，4%快100倍）；75%的任务比商业工具更快（29%快10倍，2%快100倍）。
- **发现**：
  - 神经网络作为排名函数表示能力足够，且检查证书（SMT求解）比寻找证书（学习）更容易，使方法实用。
  - 93%的任务成功学习到零损失排名函数，其中70%在1分钟内完成训练。
  - 仅4个任务因SMT反例需要重新训练；大部分任务无需反例即可一次性验证通过。
  - 训练时间远小于验证时间（97%任务训练比验证快，46%快10倍，6%快100倍）。

## 7. 优点

- **方法亮点**：
  - 首次将神经排名函数应用于LTL模型检测和反应式系统验证，扩展了神经证书的应用领域。
  - 采用“学习-检查”循环，结合数据驱动和符号推理，既利用了神经网络的表达能力，又通过SMT保证形式正确性。
  - 训练过程完全无监督，不需要预先标注数据；数据集从随机执行自动生成。
  - 通过量化神经网络将浮点运算转化为位向量算术，从而利用高效的位向量SMT求解器，优化验证效率。
- **实验亮点**：
  - 基准覆盖了多种常见硬件设计模式（计数器、状态机、通信协议等），具有代表性。
  - 与多个成熟工具（学术和商业）对比，结果清晰呈现优势。
  - 提供了详细的消融研究，验证了网络架构选择和设计决策的合理性。

## 8. 不足与局限

- **实验覆盖**：基准设计均以SystemVerilog RTL级别编写，神经网络需要字级数值输入，因此无法直接应用于位级网表（netlist）。但现代形式验证主要使用RTL，影响有限。
- **偏差风险**：实验结果可能不推广到其他工作负载（如不同协议或更复杂设计）。论文通过选择标准硬件设计来减轻风险。
- **方法局限**：
  - 可能存在局部极小导致无法收敛到零损失（如VGA设计），从而无法完成验证。
  - SMT验证时间可能很长（尤其当状态空间大或网络复杂时），限制了可扩展性。
  - 对于极小问题（如UART设计，传统工具亚秒级完成），本方法因采样、训练和SMT的开销反而更慢。
  - 神经架构依赖固定的输入规模和量化精度，可能对某些设计需要调参。
- **训练/验证不完全分离**：极少数情况（4个任务）需要反例重新训练，可能增加迭代时间。

（完）
