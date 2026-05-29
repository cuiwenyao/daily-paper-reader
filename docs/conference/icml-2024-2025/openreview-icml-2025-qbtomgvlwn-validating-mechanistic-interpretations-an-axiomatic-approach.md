---
title: "Validating Mechanistic Interpretations: An Axiomatic Approach"
title_zh: 验证机制解释：一种公理方法
authors: "Nils Palumbo, Ravi Mangal, Zifan Wang, Saranya Vijayakumar, Corina S. Pasareanu, Somesh Jha"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qBtomgvLwn"
tags: ["query:ns-xai"]
score: 5.0
evidence: 公理方法验证机制解释
tldr: 本文从程序分析中的抽象解释概念出发，给出了一组公理来正式刻画神经网络的机制解释概念，提供验证的解释标准。在现有知名解释上演示了适用性，为可解释性提供形式化基础，但未直接涉及神经符号或大模型推理。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1775, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 795, \"height\": 916, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 846, \"height\": 993, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1765, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1773, \"height\": 836, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1727, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1059, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1769, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1771, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 868, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 870, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1453, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 737, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 764, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1601, \"height\": 1164, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1760, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qbtomgvlwn/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1793, \"height\": 1136, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qbtomgvlwn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1775, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qbtomgvlwn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1354, \"height\": 1602, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qbtomgvlwn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 1606, \"label\": \"Table\"}]"
motivation: 机制解释概念缺乏正式定义，无法系统验证其正确性。
method: 借鉴抽象解释，提出一组公理描述机制解释的近似语义组合性。
result: 在现有解释上演示公理的有效性，验证了解释的合理性。
conclusion: 公理化为验证机制解释提供严格框架，促进可解释性可信度。
---

## Abstract
Mechanistic interpretability aims to reverse engineer the computation performed by a neural network in terms of its internal components. Although there is a growing body of research on mechanistic interpretation of neural networks, the notion of a *mechanistic interpretation* itself is often ad-hoc. Inspired by the notion of abstract interpretation from the program analysis literature that aims to develop approximate semantics for programs, we give a set of axioms that formally characterize a mechanistic interpretation as a description that approximately captures the semantics of the neural network under analysis in a compositional manner. We demonstrate the applicability of these axioms for validating mechanistic interpretations on an existing, well-known interpretability study as well as on a new case study involving a Transformer-based model trained to solve the well-known 2-SAT problem.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，以下是对给定论文的结构化、深入、客观的中文总结。

### 论文核心总结

- **论文标题**: Validating Mechanistic Interpretations: An Axiomatic Approach (验证机制解释：一种公理方法)
- **核心问题与整体含义**:
    - **研究动机与背景**: 当前神经网络的“机制解释”（Mechanistic Interpretability）研究虽多，但核心概念如“什么是有效的机制解释”却定义模糊，缺乏统一、严格的验证标准。这导致不同研究之间难以比较，解释的可信度也难以评估。该论文旨在解决这一根本性问题。
    - **核心思想**: 借鉴程序分析领域的“抽象解释”（Abstract Interpretation）思想，提出一套公理（Axioms）来形式化地定义和验证一个机制解释。这套公理要求解释不仅要近似网络的整体输入-输出行为，还要在网络的**各个组成模块**上也保持近似，即强调**组合性（Compositionality）**。

### 方法论

- **核心思想**:
    1.  **形式化框架**: 将神经网络视为一个用纯函数式语言`λT`编写的程序，其基本操作包括嵌入、线性层、注意力等。机制解释则是用另一个对人类更友好的语言`λH`编写的程序。验证的核心是证明`λH`程序是`λT`程序的一个有效近似。
    2.  **分解（Decomposition）**: 将神经网络`t`和其解释`h`分别分解成一系列子程序（例如按层或块分解），并要求两者的分解长度一致。
    3.  **抽象（Abstraction, α）与具体化（Concretization, γ）函数**: 引入α函数将网络的真实激活值（实数向量）映射到人类可理解的抽象特征或符号；γ函数则执行反向映射。这些函数是每个机制解释需要具体实现的。

- **关键技术细节: 六条公理**
    - 论文提出了一组核心公理，用以量化评估解释的准确性。对于每个子组件`i`，给定一个输入分布`D`和一个允许的误差阈值`ϵ`，需要检查以下性质：
    - **公理1 (前缀等价)**: `λH`程序的前i个组件的输出，经过α抽象后，应与`λT`网络前i个组件输出的抽象结果一致。这验证了**中间状态**的等效性。
    - **公理2 (组件等价)**: `λH`的第i个组件的输出，应与`λT`网络第i个组件的输出（经α抽象后）一致。这验证了每个**独立步骤**的等效性。
    - **公理3 (前缀可替换性)**: 将`λT`网络的前i个组件替换为`λH`的对应组件（通过γ具体化），网络的最终输出不应改变。这验证了**中间状态替换**对最终结果的影响。
    - **公理4 (组件可替换性)**: 将`λT`网络的第i个组件替换为`λH`的对应组件（通过γ具体化），网络的最终输出不应改变。这验证了**单步替换**对最终结果的影响。
    - **额外公理5 & 6**: 提出了关于解释的可编译性（Mechanistic Derivability）的更强但更非形式化的公理，作为未来工作的目标，本文未进行验证。
- **核心公式与流程**:
    - **验证流程**: 对每个公理，通过统计测试数据集上的违反比例来估计误差`ϵ`。利用二项分布的置信区间（如Clopper-Pearson方法）来衡量估计的可靠性。
    - **关键洞察**: 论文强调，仅验证组件等价（公理2、4）是不够的，因为误差会随着组件数量的增加而**叠加**。前缀等价（公理1、3）的验证是必要的，它能捕捉到这种累积误差。附录中给出了理论证明和模拟实验来支撑这一观点。

### 实验设计

- **数据集与场景**:
    1.  **模加法（Modular Addition）**: 经典案例，来自Nanda等人的论文。模型输入`a b =`，预测`(a+b) mod 113`。这是一个完全反向工程的解释，用于展示公理在已知优秀解释上的适用性。
    2.  **2-SAT问题**: 本文提出的新案例。训练一个只有2层的Transformer模型来解决2-SAT（布尔可满足性问题）的判定（SAT/UNSAT）。为了简化问题，使用了固定的10个子句和最多5个变量。
- **Benchmark与对比方法**:
    - **主要对比**: 将基于本文公理的系统性验证结果，与现有研究中（如Nanda等人）的验证方式进行比较。指出其只提供了类似组件（公理2、4）的证据，但缺少了对组合性（公理1、3）的验证。
    - **消融研究**: 在2-SAT案例中，对比了两种神经元解释：
        - *析取式解释*：一个神经元仅识别“命题可被某个特定赋值集满足”。
        - *决策树解释*：通过决策树学习更复杂的布尔函数，精确模拟神经元的激活模式。
    - **实验充分性与客观性**:
        - **2-SAT数据集**: 生成了100万SAT和100万UNSAT的平衡数据集（60%训练，40%测试）。用于模型分析的另一个数据集为10万SAT和10万UNSAT。
        - 验证了所有核心公理（1-4），并给出了具体的`ϵ`值（如：前缀等价`ϵ≈0.0000374`，前缀可替换`ϵ≈0.0418`等），这些`ϵ`值都是基于95%置信区间的上界。
        - 进行了“注入误差”的实验，以证明仅作组件验证（公理2、4）会忽视误差传播，而前缀验证（公理1、3）能有效捕捉到这一问题。
    - **不足之处**: 实验仅覆盖了两个较小的、面向特定算法任务的模型，其结论向更大、更通用模型（如GPT系列）的泛化性尚待证明。

### 资源与算力

- 论文在2-SAT模型的训练部分明确指出：使用了一块 **NVIDIA A100 GPU**。
- 训练使用了全批次梯度下降，AdamW优化器，进行了 **1000个epoch** 的训练。
- 其他实验的分析和公理验证工作也是在相同的GPU上完成的。
- 模加法实验的具体算力资源未明确给出。

### 主要结论与发现

1.  **公理框架有效**: 提出的公理（1-4）能够为机制解释提供一个**定义清晰、自动化和定量**的验证标准（通过`ϵ`值），填补了该领域缺乏严格验证框架的空白。
2.  **组合性至关重要**: 证明并强调了验证**前缀等价（公理1）和前缀可替换性（公理3）**的必要性。仅验证组件级等价（公理2、4）不足以保证解释的整体正确性，因为组件误差会逐层累积放大。
3.  **成功揭示新模型算法**: 成功运用公理指导对2-SAT模型的分析，逆转了其算法：第一层负责**解析**子句，第二层通过**穷举所有可能变量赋值**的方式来评估可满足性。
4.  **提供量化权衡依据**: 公理提供的`ϵ`值能够量化不同解释（如决策树 vs 析取式）在保真度和可解释性之间的权衡。例如，析取式解释在组件等价上误差更高（`ϵ≈0.309` vs `ϵ≈0.182`），但最终输出替换的误差反而更低（`ϵ≈0.00290` vs `ϵ≈0.0128`），表明其是一个更忠实但内部表示不精确的简化。

### 优点

- **建立严格的形式化基础**: 是目前少数尝试从形式化角度定义和验证机制解释的工作，为该领域提供了急需的理论基础。
- **强调组合性与误差累积**: 敏锐地指出了现有验证工作的主要缺陷——忽视误差的累积效应，并提出了解决方案（前缀公理）。
- **验证成本低**: 公理的验证可以通过统计测试高效完成，不需要昂贵的干预实验（如激活修补），具有很好的实用性。
- **通用性强**: 框架本身不依赖于具体的模型架构或解释语言，可以推广到不同的神经网络和电路分析场景。附录中还给出了扩展到非顺序计算图的方法。
- **指导分析过程**: 展示了公理不仅可用于**事后验证**，还能**指导分析过程**。在2-SAT案例中，当注意力模式不清晰时，公理（特别是替代表可达性）迫使研究者转向分析更核心的MLP通路。

### 不足与局限

- **实验规模有限**: 验证工作只在非常小的、为解决特定算法任务而训练的模型上进行。其在复杂、大规模语言模型（如GPT-2、Llama等）上的有效性、可操作性和计算成本是未来工作的关键挑战。
- **依赖人工设计**: `α`和`γ`函数以及分解方式需要研究人员针对每个模型和解释来设计，这本身就是一项专业且可能很主观的工作，降低了框架的自动化程度。
- **`γ`函数的局限性**: 实现的`γ`函数（例如平均值替换）可能不够精确，会影响替换公理（Axiom 3, 4）的评估结果。论文中也提到了这一点。
- **公理完备性**: 论文将公理5和6（关于可编译性）标记为“非正式”并留作未来工作，这表明当前框架并非完全完备。
- **未处理冗余和并行计算**: 虽然附录中讨论了扩展到电路分析的方法，但主要强调线性分解。对于具有大量并行、冗余子路的网络，如何有效构建和验证解释仍是开放问题。

（完）
