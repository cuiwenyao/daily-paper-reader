---
title: Can Transformers Reason Logically? A Study in SAT Solving
title_zh: Transformer能进行逻辑推理吗？一项关于SAT求解的研究
authors: "Leyan Pan, Vijay Ganesh, Jacob Abernethy, Chris Esposo, Wenke Lee"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=5BGC2I2fxx"
tags: ["query:ns-xai"]
score: 8.0
evidence: 通过SAT求解研究Transformer的邏輯推理能力
tldr: Transformer的逻辑推理能力缺乏形式化理解。本文构造性证明解码器仅Transformer可通过链式思维回溯和演绎解决3-SAT，并将理论构造转化为算法轨迹训练模型，训练后的模型展现出强大的分布外推理能力，为理解大模型逻辑推理提供了理论和实践基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1408, \"height\": 881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1257, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1635, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1194, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5bgc2i2fxx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1647, \"height\": 1063, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-5bgc2i2fxx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1534, \"height\": 448, \"label\": \"Table\"}]"
motivation: 需要形式化理解Transformer的逻辑推理能力。
method: 构造性证明并训练Transformer学习算法轨迹。
result: 模型在3-SAT上表现优异，且具备分布外泛化能力。
conclusion: Transformer可以通过学习推理路径获得形式逻辑推理能力。
---

## Abstract
We formally study the logical reasoning capabilities of decoder-only Transformers in the context of the boolean satisfiability (SAT) problem. 
First, we prove by construction that decoder-only Transformers can decide 3-SAT, in a non-uniform model of computation, using backtracking and deduction via Chain-of-Thought (CoT).
Second, we implement our construction as a PyTorch model with a tool (PARAT) that we designed to empirically demonstrate its correctness and investigate its properties.
Third, rather than \textit{programming} a transformer to reason, we evaluate empirically whether it can be \textit{trained} to do so by learning directly from algorithmic traces (``reasoning paths'') from our theoretical construction. The trained models demonstrate strong out-of-distribution generalization on problem sizes seen during training but has limited length generalization, which is consistent with the implications of our theoretical result.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLMs）在复杂推理任务中表现出色，尤其是结合链式思维（Chain-of-Thought, CoT）后，但仍存在不可靠的逻辑推理和幻觉问题。学术界对LLMs是否具备真正的推理能力存在争议，且缺乏对Transformer模型推理能力根本局限性的形式化理解。
- **核心问题**：本文旨在从形式化和构造性的角度研究纯解码器Transformer的演绎逻辑推理能力，以布尔可满足性问题（SAT）作为具体案例，探究Transformer能否通过CoT解决NP完全问题3-SAT。
- **整体含义**：通过构造性证明和训练实验，展示了Transformer在非均匀计算模型下能够通过回溯和演绎机制解决3-SAT，训练模型可以学习这种推理过程，但长度泛化能力有限，为理解LLMs推理的机理和局限性提供了理论基础。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：证明存在一种解码器Transformer，对任意固定大小的3-SAT实例（最多p个变量、c个子句），可以使用CoT模拟DPLL（Davis–Putnam–Logemann–Loveland）回溯搜索算法，从而决定该实例的可满足性。该构造不依赖于模型大小的均匀性（即参数依赖于问题大小），且CoT长度在最坏情况下为O(p·2^p)，但实际远低于此界。
- **关键技术细节**：
  - **二进制编码**：将子句和当前部分赋值编码为2p维二进制向量E(C)、E(A)等，便于在Transformer中进行并行逻辑操作。
  - **并行逻辑操作（Lemma 4.7）**：满足性检查（A|=F）、冲突检测（F|=¬A）、单元传播（Deduction）均可表示为向量运算，并可通过注意力头和MLP层近似实现（Lemma 4.8）。
  - **饱和注意力近似**：使用饱和注意力（saturated attention）作为理想化模型，并通过缩放因子β的softmax注意力近似，误差可控制。
  - **CoT生成流程**：模型按顺序输出决策（Assume）、推导（Deduce）、回溯（BackTrack）等标记，最终输出SAT或UNSAT，每一步对应DPLL状态转换。
  - **模型架构**：需要L=7层、H=5个注意力头、嵌入维数d_emb=O(p)、参数量O(p²)。
- **算法流程**：输入DIMACS编码的3-SAT公式→通过多层Transformer生成CoT标记序列→在输出层根据优先级决定下一标记（满足则输出SAT，冲突且无决策则输出UNSAT，冲突且有决策则输出[BackTrack]，否则进行单元传播或决策等），直至终止。

### 3. 实验设计：使用数据集/场景、benchmark、对比方法

- **数据集**：
  - 随机3-SAT公式，变量数p从4到20，子句数c介于4.1p到4.4p（接近相变临界点4.26）。
  - 三种采样分布：
    - **Marginal**：成对公式，仅差一个字面量，消除统计差异。
    - **Random**：随机均匀采样。
    - **Skewed**：非均匀极性/变量偏好。
  - 每个变量数有2000个样本，共51个数据集（p=4到20）。
  - 训练集：p∈[6,10]和p∈[11,15]两个范围，每个范围3种分布×500k样本。
- **Benchmark**：无外部基线对比，主要对比编译模型（理论构造的精确实现）与训练模型的表现。
- **对比方法**：
  - 编译模型（PARAT工具实现的理论模型）。
  - 训练模型：LLaMA架构（70M和160M参数），在算法轨迹上训练，评估SAT/UNSAT预测准确率和完整CoT轨迹正确率。

### 4. 资源与算力

- 文中未明确说明使用的GPU型号、数量及训练时长。仅提及模型规模：70M参数（6层，512嵌入，8头）和160M参数（12层，768嵌入，12头），训练5个epochs，使用Adam优化器，余弦学习率衰减（6e-4→6e-5）。未报告具体硬件配置和耗时，因此无法量化算力消耗。

### 5. 实验数量与充分性

- **实验数量**：
  - 编译模型：在全部51个数据集（每个2000样本）上测试，取得100%准确率（Figure 3）。
  - 训练模型：两个模型（70M和160M）在3种分布、2个变量范围上训练，然后在多个测试集上评估（表1、图3、图6），包括同分布内OOD测试和长度泛化测试。
  - 额外实验：考察CoT步数分布（Figure 4）和softmax注意力精度影响（Figure 5）。
- **充分性与公平性**：
  - 实验设计考虑了统计偏差（Marginal数据集消除统计信息），排除了利用c/p比率猜答案的可能。
  - 使用了不同的采样分布评估泛化能力，消融了注意力精度的影响。
  - 训练实验中控制了变量数范围，并进行了分布外测试。
  - 总体实验较为充分，结论可靠，但主要局限在问题规模（≤20变量）和模型大小（≤160M参数）。

### 6. 论文的主要结论与发现

- **存在性证明**：存在解码器Transformer可以在非均匀模型下通过CoT解决3-SAT，理论构造正确。
- **编译模型完美求解**：PARAT实现的模型在所有测试实例上达到100%准确率（Figure 3），验证了理论构造。
- **训练模型能学习推理**：在相同变量数范围内，训练模型在三种分布上均达到接近100%的SAT/UNSAT准确率和较高的完整轨迹正确率（表1），说明模型学会了正确的推理过程。
- **长度泛化有限**：在未见过的变量数（超出训练范围）上，模型性能急剧下降（Figure 3），符合理论预测（参数依赖问题大小），指出现有LLM在逻辑推理长度泛化上的根本局限。
- **注意力误差影响**：当β不足时，模型准确率随变量数增加而下降（Figure 5），表明softmax近似误差是长度泛化困难的来源之一。

### 7. 优点：方法或实验设计上的亮点

- **理论严谨性**：给出构造性证明，明确Transformer参数量与问题大小的关系，并讨论非均匀计算模型的意义。
- **工具创新**：设计PARAT工具，将理论构造编译为可运行的PyTorch模型，便于验证和探索内部行为。
- **实验设计巧妙**：使用Marginal数据集消除统计特征，确保模型必须依赖逻辑推理而非数据偏置；评估了完整轨迹正确率，而不仅仅是最终答案。
- **关联理论与实际**：训练实验表明理论轨迹可被学习，并验证了理论对长度泛化限制的预测，强化了结论的可信度。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **问题规模小**：实验仅限于最多20个变量的3-SAT，未扩展到更大规模（如上百变量），无法评估大规模下的泛化行为。
- **模型规模小**：训练模型仅70M和160M参数，未尝试更大的LLM（如7B+），结论是否适用于大模型尚不明确。
- **非均匀构造限制**：理论构造的参数依赖于最大变量数p，不是完全统一的Transformer，实际LLM可能并非以这种方式运行。
- **训练数据生成成本**：CoT轨迹需要自定义SAT求解器生成，难度随变量数指数增长，限制了实验规模。
- **长度泛化失败原因分析不足**：仅归因于软注意力误差，未深入探讨其他潜在因素（如位置编码、模型容量）。
- **仅考虑3-SAT**：未扩展到其他NP完全问题或更复杂的逻辑推理形式。

（完）
