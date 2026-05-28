---
title: "CTSketch: Compositional Tensor Sketching for Scalable Neurosymbolic Learning"
title_zh: CTSketch：面向可扩展神经符号学习的组合式张量草图
authors: "Seewon Choi, Alaia Solko-Breslin, Rajeev Alur, Eric Wong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=mor7s1NGBV"
tags: ["query:ns-xai"]
score: 9.0
evidence: 利用张量草图的组合式符号程序实现可扩展神经符号学习
tldr: 神经符号学习在组合式神经网络与符号程序场景下扩展性差。本文提出CTSketch，将符号程序分解为子程序并用草图张量概括，通过张量运算近似输出分布。理论分析了近似误差，实验证明该方法显著提升了神经符号学习的可扩展性，并保持了准确性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 786, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1293, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1320, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 682, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 642, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mor7s1ngbv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 824, \"height\": 486, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1322, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 948, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1489, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1374, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1375, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mor7s1ngbv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1330, \"height\": 280, \"label\": \"Table\"}]"
motivation: 现有神经符号学习方法在大规模符号程序上扩展性不足。
method: 将符号程序分解为子程序，并使用草图张量近似每个子程序的输出分布。
result: 实验表明CTSketch在多个任务上实现了高可扩展性，同时保持准确性。
conclusion: 张量草图为大规模神经符号学习提供了一种有效且可扩展的解决方案。
---

## Abstract
Many computational tasks benefit from being formulated as the composition of neural networks followed by a discrete symbolic program. The goal of neurosymbolic learning is to train the neural networks using end-to-end input-output labels of the composite. We introduce CTSketch, a novel, scalable neurosymbolic learning algorithm. CTSketch uses two techniques to improve the scalability of neurosymbolic inference: decompose the symbolic program into sub-programs and summarize each sub-program with a sketched tensor. This strategy allows us to approximate the output distribution of the program with simple tensor operations over the input distributions and the sketches. We provide theoretical insight into the maximum approximation error. Furthermore, we evaluate CTSketch on benchmarks from the neurosymbolic learning literature, including some designed for evaluating scalability. Our results show that CTSketch pushes neurosymbolic learning to new scales that were previously unattainable, with neural predictors obtaining high accuracy on tasks with one thousand inputs, despite supervision only on the final output.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- 神经符号学习旨在仅利用复合系统的端到端输入-输出标签，训练连接神经网络和离散符号程序的组合模型。核心挑战在于：如何以完全可微的方式计算符号程序关于输入分布的输出分布。
- 现有方法分为两类：白盒方法（如 Scallop、DeepProbLog）将符号程序编码为可微逻辑程序，但难以支持外部 API 调用（如 LLM），且在大规模输入空间下计算昂贵；黑盒方法（如 ISED、IndeCateR、A-NeSI）将程序视为黑箱，通过采样或额外神经网络近似加权模型计数（WMC），但收敛慢、精度低，尤其当输入数量大时性能急剧下降。
- 因此，本文旨在结合两类方法的优点，设计一种更可扩展的神经符号学习算法，使其能处理上千个输入的任务，同时保持对标准基准的竞争力。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将符号程序分解为子程序，并用**张量草图（tensor sketch）** 近似每个子程序的输入-输出映射，实现高效可微推理。
- **主要步骤**：
  1. **程序分解**：手动将长程序分解成树形结构的多层子程序，每层子程序仅接收前层或原始输入，并按顺序计算。例如，“4位数求和”可分解为两层：先对两对分别求和，再将结果相加。
  2. **张量摘要初始化**：对每个子程序 \(c_i\)，枚举其所有可能的输入组合，构建一个摘要张量 \(\phi_i\)（大小等于输入空间的笛卡尔积）并存储对应输出值。若输出空间有限，还可使用独热编码张量 \(\phi_i^{\text{OH}}\)。
  3. **张量草图**：对每个子程序摘要张量使用**张量列车奇异值分解（TT-SVD）** 或其他低秩分解方法，将其分解为一组低秩核心（cores），从而大幅减小存储空间。例如，2路输入的sum子程序 \(\phi\) 被分解为两个 rank-2 核心 \(t_1\) 和 \(t_2\)。
  4. **前向传播**：推理时，对各层子程序，不重建完整张量，而是将输入概率分布与核心直接相乘，通过张量运算得到近似输出值（如公式 (3.3)）。该值通过 RBF 核和 L1 归一化为概率分布，传递给下一层。最后一层可直接比较输出值与真实标签计算损失。
- **关键技术细节**：
  - 使用 **TT-SVD** 分解：给定近似秩 \(\rho\)，TT-SVD 输出核心 \((t_1, ..., t_d)\)，重建误差受定理 3.1 约束。
  - 定理 3.2（CTSketch误差界）：使用草图张量近似输出分布，其 L2 误差不超过 \(\sqrt{2}\|p\|_F \lfloor 4\|\phi_i - T_i\|_F^2 \rfloor^{1/2}\)，其中 \(p\) 是输入分布，\(\phi_i\) 和 \(T_i\) 分别是精确与重建张量。
  - 对输出空间无限的子程序（如求和），不需要独热编码，直接计算期望值；对有限输出空间使用独热编码草图。
  - 测试时使用原始符号程序 \(c\) 和 argmax 预测，而非草图。

### 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - **MNIST 求和 (sum n)**：对 \(n = 2^k\)（k=2,4,6,8,10）个手写数字求和，训练集 5K/4K 样本，测试集 1K。
  - **多位数加法 (add n)**：两个 n 位数相加（n=1,2,4,15,100），训练集和测试集各为 60,000/2n 和 10,000/2n。
  - **视觉数独 (visudo)**：4x4 和 9x9 数独棋盘有效性判断（200/2K 样本）。
  - **数独求解 (sudoku)**：9x9 数独推理（9K 训练，500 测试）。
  - **手写公式 (HWF)**：含 1-7 个字符的公式求值（10K 样本，长度分布不等）。
  - **叶片识别 / 场景分类**：使用 GPT-4 进行推理的神经符号任务，数据集来自 [3] 和 [27]。
- **Benchmark**：对比方法包括 Scallop、DeepSoftLog (DSL)、IndeCateR、ISED、A-NeSI。
- **评估指标**：测试准确率（%），并计算参考准确率（假设单数字识别准确率 99%）。

### 4. 资源与算力

- 论文在论文第4.2节明确说明：所有实验在一台配备**14核 Intel i9-10940X CPU、1块 NVIDIA RTX 3090 GPU、66GB RAM** 的机器上运行。
- 每个任务使用10个随机种子，应用每训练样本5秒的超时限制。
- 未提供每个任务的具体训练 GPU 时长，但提供了不同方法的 epoch 时间对比：例如 add15 任务中，CTSketch 平均每个 epoch 1.70 秒，而 IndeCateR 约 23.07 秒，A-NeSI 约 52.72 秒，DeepSoftLog 超过 20 分钟。
- 草图初始化和分解的额外开销极低（所有任务总和不到 1 分钟）。

### 5. 实验数量与充分性

- 论文进行了大量实验：
  - **主实验**：在 5 类大尺度任务（sum, add, visudo, sudoku, hwf, leaf, scene）上对比了所有方法，涵盖不同输入规模（如 sum 从 16 到 1024）。
  - **消融实验**：
    - **分解与草图效果**：在 sum 16 上测试不同分解深度（单层 vs 多层）和是否使用草图（full rank vs sketch）的影响（附录 D.1）。
    - **草图秩的影响**：在 HWF 任务上测试 rank 2,4,8,full 对精度和训练时间的影响（第 4.6 节）。
    - **不同张量分解方法比较**：对比 TT-SVD、CP、Tucker、Tensor Ring 对 sum 4 和 HWF 的效果（附录 D.2）。
  - 每个实验使用 10 个随机种子并报告均值±标准差，具有统计意义。
- **充分性评价**：实验覆盖了从简单到极大规模的任务，对比了多种代表性方法，并深入分析了方法中的关键超参数（秩、分解结构、分解方法），设计客观、公平、全面。

### 6. 论文的主要结论与发现

- CTSketch 在**可扩展性**上显著优于所有基线：在 sum 256 和 sum 1024 等大规模任务上，其他方法基本失败（超时、溢出或近乎零精度），而 CTSketch 取得了有意义的准确率（sum 1024: 2.73%，对应单数字准确率约 93.69%）。
- 在标准神经符号基准（add, visudo, sudoku, hwf, leaf, scene）上，CTSketch 在 4 个任务上取得最高准确率，在其他任务上差距很小（如 visudo 4 落后 A-NeSI 仅 2.55%），**保持了竞争力**。
- **计算效率**方面，CTSketch 的 epoch 时间远低于其他方法，因为推理仅需简单张量运算，无需额外网络训练或复杂聚合。
- **草图秩**的消融表明：使用合适的中间秩（如 4 或 8）可以在几乎不损失最终精度的情况下大幅加速训练；过低的秩（如 2）会导致无法学到最优权重，过高的秩（full）则训练缓慢。
- 程序分解和张量草图结合是解决可扩展性瓶颈的关键：单独分解仍不足以处理高维输入（如 sum 16 单层全张量需要 1e18 条目，无法装入内存），而草图可显著压缩存储。

### 7. 优点

- **方法新颖且有效**：首次将张量草图技术引入神经符号学习，通过程序分解和低秩分解实现高效可微推理，兼顾可扩展性与精度。
- **理论保证**：给出了输出分布近似的误差界（定理 3.2），为方法的可靠性提供了理论支撑。
- **实验全面**：涵盖从标准小规模到前所未有的千级输入规模，对比方法全面，消融实验深入，结果统计严谨。
- **计算效率突出**：推理仅需简单矩阵-向量乘法，无需额外训练预测网络或逻辑程序回溯，因此训练速度显著快于所有基线。
- **支持黑箱程序**：即使符号程序内部未知（如调用 GPT-4），也能通过分解和草图进行学习（leaf, scene 任务验证）。
- **代码公开**：提供可复现代码（GitHub），便于社区使用和扩展。

### 8. 不足与局限

- **依赖手动分解**：程序分解需要用户手动指定，对复杂任务可能困难甚至无法完成（例如不规则循环、高级推理）。论文第 5 节承认这是主要限制，并呼吁未来工作自动化分解。
- **适用性受限于结构化输入**：要求子程序的输入空间是离散且有限，且输出空间可表示为简单值（实数或有限集），不适合连续输入或无限状态空间。
- **初始化需要枚举全部输入组合**：在子程序输入空间非常大时，枚举所有组合本身可能代价高昂。论文提到可以使用子集采样或流式草图优化，但未在主实验中使用。
- **误差界依赖低阶近似**：定理 3.2 的误差界基于低秩重建误差，若程序输入-输出映射的秩很高（如复杂非线性），则低秩草图可能导致显著近似误差。实验中 HWF 使用 rank 8 仍表现良好，但理论保证可能不适用于所有情况。
- **未与最新的大规模神经符号方法比较**：如 PLIAt（2024）等，仅在消融中提到了部分（附录 D.2），但未在主要对比中包含。
- **算力资源描述不够详细**：虽给了机器配置和相对时间，但未报告每个任务的总 GPU 小时数，不利于精确复现能耗评估。

（完）
