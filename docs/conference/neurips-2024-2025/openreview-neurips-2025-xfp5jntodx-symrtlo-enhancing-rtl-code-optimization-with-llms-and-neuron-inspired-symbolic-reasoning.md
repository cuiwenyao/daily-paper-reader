---
title: "SymRTLO: Enhancing RTL Code Optimization with LLMs and Neuron-Inspired Symbolic Reasoning"
title_zh: SymRTLO：利用LLM和神经元启发的符号推理增强RTL代码优化
authors: "Yiting Wang, Wanghao Ye, Ping Guo, Yexiao He, Ziyao Wang, Bowei Tian, Shwai He, Guoheng Sun, Zheyu Shen, Sihan Chen, Ankur Srivastava, Qingfu Zhang, Gang Qu, Ang Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XFP5jntOdx"
tags: ["query:ns-xai"]
score: 6.0
evidence: 将LLM与符号推理相结合
tldr: 该论文提出SymRTLO框架，将大语言模型与符号推理相结合，用于寄存器传输级代码优化。通过神经符号协同，在硬件设计领域实现了高效优化，展示了神经符号集成在非传统任务中的可迁移性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 462}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 714, \"height\": 383}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 196}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 390}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 327}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 2070}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 738, \"height\": 121}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 420}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 150}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 492}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 600}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 692, \"height\": 295}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 565}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 680}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 553}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 431}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 709}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1441, \"height\": 553}]"
motivation: 现有LLM方法生成的RTL代码难以与提示对齐，且编译器方法处理复杂约束困难。
method: 提出神经符号框架SymRTLO，集成LLM与符号推理来优化RTL代码。
result: 在RTL优化任务上有效提升了代码质量与对齐性。
conclusion: 神经符号协同可有效应用于硬件设计优化，拓展了该范式的应用场景。
---

## Abstract
Optimizing Register Transfer Level (RTL) code is crucial for improving the efficiency and performance of digital circuits in the early stages of synthesis. Manual rewriting, guided by synthesis feedback, can yield high-quality results but is time-consuming and error-prone. Most existing compiler-based approaches have difficulty handling complex design constraints. Large Language Model (LLM)-based methods have emerged as a promising alternative to address these challenges. However, LLM-based approaches often face difficulties in ensuring alignment between the generated code and the provided prompts. This paper introduces SymRTLO, a neuron-symbolic framework that integrates LLMs with symbolic reasoning for the efficient and effective optimization of RTL code. Our method incorporates a retrieval-augmented system of optimization rules and Abstract Syntax Tree (AST)-based templates, enabling LLM-based rewriting that maintains syntactic correctness while minimizing undesired circuit behaviors. A symbolic module is proposed for analyzing and optimizing finite state machine (FSM) logic, allowing fine-grained state merging and partial specification handling beyond the scope of pattern-based compilers. Furthermore, a fast verification pipeline, combining formal equivalence checks with test-driven validation, further reduces the complexity of verification. Experiments on the RTL-Rewriter benchmark with Synopsys Design Compiler and Yosys show that SymRTLO improves power, performance, and area (PPA) by up to 43.9%, 62.5%, and 51.1%, respectively, compared to the state-of-the-art methods. We will release the code as open source upon the paper's acceptance.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将基于您提供的论文内容，对《SymRTLO : Enhancing RTL Code Optimization with LLMs and Neuron-Inspired Symbolic Reasoning》一文进行结构化、深入且客观的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：寄存器传输级（RTL）代码优化是提升数字电路性能的关键早期步骤，但传统方法面临严峻挑战。手动优化依赖专家经验且耗时易错；传统编译器方法（如EDA工具）受限于预定义启发式规则，难以处理复杂或不规则的设计约束。
*   **研究动机**：大语言模型（LLM）的出现为自动生成RTL代码带来新范式，但其直接应用于优化时存在核心缺陷——生成的代码难以严格与设定的优化目标对齐（alignment problem），导致输出不可靠、不可解释。现有LLM方法（如RTLRewriter）仍需依赖多轮合成反馈循环，效率低下且效果不佳。
*   **整体含义**：本文提出**神经符号（neuron-symbolic）集成**的思路，将LLM强大的生成能力与符号推理（Symbolic Reasoning）的逻辑严谨性和可解释性相结合，旨在实现一个更高效、精确且可解释的RTL代码优化框架。这代表了将符号AI与LLM结合解决特定领域工程难题的前沿尝试。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：**SymRTLO**框架将RTL优化任务分解为数据通路径优化和控制流优化，并分别采用不同的神经符号策略处理。通过LLM提取和检索优化规则，利用抽象语法树（AST）模板和符号生成脚本强制代码与规则对齐，并自动进行等价性验证。
*   **关键技术细节**：
    1.  **LLM调度器（Dispatcher）**：首先分析输入RTL代码和用户指定的优化目标（如低功耗、高性能），判断电路是否包含有限状态机（FSM），从而决定是否启用控制流优化。
    2.  **数据流优化**：
        *   **检索增强生成（RAG）系统**：从各种来源（书籍、手册、代码库）提取优化规则，并构建一个**优化库**。每条规则都关联了其优化目标（功耗、面积等）和类别。
        *   **AST模板系统**：对于可以形式化的规则，LLM被提示生成**基于AST的模板**。这些模板定义了目标节点类型和转换规则（如合并嵌套if-else、常数折叠）。这确保了LLM的改写在结构上是正确且对齐的。
        *   **目标导向规则选择**：采用**肘部法则**分析候选规则与查询的相似度得分，动态选择最相关的规则子集，这有助于**平衡冲突的优化目标**（如面积优化 vs. 时序优化）。
        *   **反馈循环**：如果模板应用后验证失败，LLM可以重新选择模板并调整策略，增强了鲁棒性。
    3.  **控制流优化（FSM优化）**：
        *   **符号系统生成**：不是使用通用脚本，而是提示LLM为每个`FSM`动态生成一个专门的**符号表示**和**优化脚本**。该脚本针对该FSM的具体结构（状态、转换、输出约束）执行状态合并等算法，从而处理编译器难以处理的**部分指定FSM**和**数据路径约束**。
    4.  **验证与最终优化**：
        *   **初始过滤**：LLM自动生成测试平台进行功能测试，快速过滤无效改写。
        *   **形式化验证**：对于通过初测的设计，使用SAT求解器（Yosys+ABC）或顺序等价性检查工具（Synopsys Formality）进行**形式化等价验证**，确保最终输出与原始设计的完全功能等价。

### 3. 实验设计：使用的数据集/场景、Benchmark、对比方法

*   **评估基准与场景**：
    *   **功能性正确性**：在`RTL-Rewriter`基准上评估`pass@k`指标。
    *   **电路优化性能**：使用`RTL-Rewriter`基准中的11个短基准（侧重线网和单元优化）和10个复杂FSM及算法实例（侧重PPA优化，即功耗、性能、面积）。同时，与`RTLRewriter`论文报告的结果进行了直接比较。
*   **对比方法**：
    *   **商业LLM**：GPT-O1, GPT-4o, GPT-4-Turbo, GPT-3.5-Turbo, GPT-4o-mini。
    *   **开源LLM工具**：VeriGen, RTL-Coder-DeepSeek。
    *   **编译器基线**：使用Yosys和Synopsys DC Compiler的标准优化流程。
*   **评估指标**：
    *   `pass@k`：衡量功能正确性。
    *   **线网与单元数**：用于评估短基准。
    *   **PPA**：功耗（mW）、时序（ns）、面积（μm²），使用Synopsys DC Compiler评估。

### 4. 资源与算力

*   **明确说明**：论文中**未明确说明**实验所消耗的具体算力（如GPU型号、数量、训练时长）。
*   **可推断的信息**：
    *   主要的LLM是**GPT-4o**，通过OpenAI的API调用，算力由OpenAI提供。
    *   规则提取和AST处理使用了**Pyverilog**（Python库），对算力要求不高。
    *   PPA评估使用的是商业工具**Synopsys DC Compiler**，算力消耗取决于设计规模。
    *   作者提到“为了保持Token预算公平”，SymRTLO（基于GPT-4o）平均消耗约7728个token，其他模型（如GPT-4o）消耗约775个token/次。这暗示了推理成本，但未提及训练成本。

### 5. 实验数量与充分性

*   **实验数量**：论文进行了多组实验，包括：
    1.  在11个短基准上的线网/单元数对比。
    2.  在5个FSM设计上的PPA对比。
    3.  在5个算法/复杂设计上的PPA对比。
    4.  消融实验（去除AST模板、符号推理、目标搜索）。
    5.  结合编译器优化后的PPA对比。
*   **充分性与客观性评价**：
    *   **充分**：实验覆盖了功能正确性、数据流/控制流优化、与多种LLM和编译器方法的对比，并且包含了关键的消融研究来验证各模块贡献。结果具有统计意义（如GeoMean）。
    *   **客观公平**：
        *   基准和对比方法是领域内常用的或前沿的（RTLRewriter）。
        *   为了保证公平，对token预算进行了说明。
        *   与RTLRewriter方法进行了直接对比（尽管对方未开源所有代码，但作者尽力对齐了基准场景）。
        *   缺陷：实验未包含对极大规模工业级电路的测试，只在“工业级规模”的基准上进行。

### 6. 论文的主要结论与发现

*   **主要结论**：**SymRTLO**通过集成LLM和符号推理，在RTL代码优化上显著优于所有基线方法，包括纯LLM方法和传统编译器方法。
*   **具体发现**：
    *   **功能性**：`pass@1`达到97.5%，远超其他LLM，证明其能生成高度对齐的优化代码，大幅减少合成迭代。
    *   **PPA提升**：相比最先进方法（SOTA），在功耗、性能和面积上分别最多提升 **43.9%**、**62.5%** 和 **51.1%**。在RTLRewriter基准上，线网和单元数的几何平均值达到 **0.63** 和 **0.67**，优于SOTA。
    *   **FSM优化**：在FSM设计中，效果显著优于GPT-O1和RTLRewriter，能有效对齐状态减少算法。
    *   **冲突解决**：通过目标导向规则选择和AST模板，有效解决了不同优化目标之间的冲突。
    *   **消融实验**：证明了AST模板、符号推理和目标导向搜索这三个核心组件缺一不可。

### 7. 优点：方法或实验设计上的亮点

*   **方法创新**：**神经符号集成**解决硬件设计中的对齐问题是其最大亮点。将抽象的优化规则（RAG）与具体的结构化约束（AST模板）和动态生成的符号脚本（FSM）相结合，设计精巧。
*   **解决实际问题**：直面并解决了LLM优化中的三大核心挑战：1）规则泛化与检索；2）代码-提示对齐；3）优化目标冲突。
*   **自动化程度高**：从规则提取、模板生成、FSM优化到验证的全流程都实现了高度自动化，极大减少了对人类专家和反复合成调用的依赖。
*   **实验设计合理**：消融实验设计清晰，验证了每个模块的必要性。与多种方法对比，且考虑了编译器优化后的性能，使结论更坚固。
*   **可解释性**：符号系统（AST模板、FSM符号表示）的引入使得优化过程比黑盒LLM更具可解释性。

### 8. 不足与局限

*   **对LLM的依赖性**：整个框架的性能高度依赖于底层LLM（作者选用了GPT-4o）的能力。如果LLM在生成符号脚本或AST模板时出现偏差，可能会影响最终效果。
*   **规则库的维护**：优化规则库需要持续维护和扩展以跟上硬件设计的发展，这是一个长期成本。
*   **可扩展性瓶颈**：符号推理模块在处理超大规模或有复杂控制流的状态机时，可能面临形式化分析的计算瓶颈（NP-完全问题）。
*   **PPA评估依赖工具**：最终的PPA结果高度依赖于所使用合成工具（Synopsys DC、Yosys）的版本和库，不同环境的结果可能不一致。
*   **实验覆盖有限**：虽然在学术基准上表现出色，但论文并未涵盖最极端的工业级大型设计，其对部分新型或高度专业化电路模式的泛化能力尚未得到充分验证。
*   **算力未公开**：未公开详细的计算资源消耗（如GPU型号、时长），这为复现和评估其实用性带来一定困难。

（完）
