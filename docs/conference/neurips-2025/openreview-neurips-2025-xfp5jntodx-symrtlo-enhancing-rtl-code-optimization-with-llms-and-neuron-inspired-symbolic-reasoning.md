---
title: "SymRTLO: Enhancing RTL Code Optimization with LLMs and Neuron-Inspired Symbolic Reasoning"
title_zh: SymRTLO：利用大语言模型和类神经符号推理增强RTL代码优化
authors: "Yiting Wang, Wanghao Ye, Ping Guo, Yexiao He, Ziyao Wang, Bowei Tian, Shwai He, Guoheng Sun, Zheyu Shen, Sihan Chen, Ankur Srivastava, Qingfu Zhang, Gang Qu, Ang Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XFP5jntOdx"
tags: ["query:ns-xai"]
score: 8.0
evidence: 结合大语言模型与符号推理的神经符号框架用于寄存器传输级代码优化
tldr: 寄存器传输级代码优化对数字电路性能至关重要，但手动重写耗时且易错。现有方法难以处理复杂约束。本文提出SymRTLO，一个神经符号框架，将大语言模型与符号推理结合，用于高效优化RTL代码。实验证明该方法在优化质量和效率上均优于现有方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 714, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 196, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xfp5jntodx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 2070, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 738, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 692, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 680, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 553, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 709, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xfp5jntodx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1441, \"height\": 553, \"label\": \"Table\"}]"
motivation: RTL代码优化耗时且易错，现有方法无法有效处理复杂设计约束。
method: 提出SymRTLO框架，集成大语言模型与符号推理，以神经符号方式优化RTL代码。
result: 在多个RTL设计上，SymRTLO显著提升了代码质量和优化效率。
conclusion: 神经符号结合是解决硬件设计中复杂优化问题的有效途径。
---

## Abstract
Optimizing Register Transfer Level (RTL) code is crucial for improving the efficiency and performance of digital circuits in the early stages of synthesis. Manual rewriting, guided by synthesis feedback, can yield high-quality results but is time-consuming and error-prone. Most existing compiler-based approaches have difficulty handling complex design constraints. Large Language Model (LLM)-based methods have emerged as a promising alternative to address these challenges. However, LLM-based approaches often face difficulties in ensuring alignment between the generated code and the provided prompts. This paper introduces SymRTLO, a neuron-symbolic framework that integrates LLMs with symbolic reasoning for the efficient and effective optimization of RTL code. Our method incorporates a retrieval-augmented system of optimization rules and Abstract Syntax Tree (AST)-based templates, enabling LLM-based rewriting that maintains syntactic correctness while minimizing undesired circuit behaviors. A symbolic module is proposed for analyzing and optimizing finite state machine (FSM) logic, allowing fine-grained state merging and partial specification handling beyond the scope of pattern-based compilers. Furthermore, a fast verification pipeline, combining formal equivalence checks with test-driven validation, further reduces the complexity of verification. Experiments on the RTL-Rewriter benchmark with Synopsys Design Compiler and Yosys show that SymRTLO improves power, performance, and area (PPA) by up to 43.9%, 62.5%, and 51.1%, respectively, compared to the state-of-the-art methods. We will release the code as open source upon the paper's acceptance.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：寄存器传输级（RTL）代码优化是数字电路设计早期阶段的关键环节，直接影响最终芯片的功耗、性能与面积（PPA）。然而，传统的手动优化依赖工程师反复迭代，耗时且易出错；基于编译器的自动优化方法（如 Synopsys DC）依赖预定义启发式规则，难以处理复杂设计约束（如不完整的有限状态机规范、冲突的优化目标）。近年来，大语言模型（LLM）被用于 RTL 代码优化，但面临两大挑战：一是生成代码与优化目标之间的“对齐”不足（LLM 常产生不完整或错误的输出）；二是仍然依赖耗时合成反馈循环，效率低下。
- **整体含义**：本文提出 SymRTLO，一个将 LLM 与符号推理相结合的“神经符号”框架，旨在自动化 RTL 优化，减少对合成工具的迭代依赖，同时保证输出的语法正确性与功能等价性。该工作填补了纯 LLM 方法在代码对齐和结构化优化方面的空白，并为硬件设计自动化领域引入了新的范式。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过神经符号集成，分模块处理数据路径与控制路径的优化。利用检索增强生成（RAG）构建可复用的优化规则库，结合抽象语法树（AST）模板强制 LLM 输出符合语法的优化结果；针对有限状态机（FSM）这类复杂控制流，则让 LLM 动态生成符号化脚本来进行状态合并与部分规格处理。
- **关键技术细节**：
  1. **LLM 调度器**：输入 RTL 代码与优化目标（如低功耗、高性能），识别是否包含 FSM，决定走“数据流优化”还是兼走“控制流优化”路径。
  2. **数据流优化**：
     - **RAG 规则库**：从书籍、设计手册、代码库中提取优化规则，每条规则包含描述、适用目标、类别及“模板编写指导”或抽象描述。利用文本嵌入进行相似度搜索，并通过“肘部法”选择最优阈值，避免冲突规则共选。
     - **AST 模板**：对于有明确模板指导的规则，让 LLM 生成 AST 子树变换模板（如合并嵌套 if-else、常数折叠）。模板通过等价性检查后存入 RAG，实现可复用。模板选择顺序由 LLM 动态决定，并设置反馈循环以处理失败情况。
  3. **控制流优化**：
     - 对于 FSM，传统 AST 模板无法处理部分规格（不完整状态/转换），属 NP 难问题。SymRTLO 让 LLM 将 RTL 代码转化为符号表示（状态集、转移函数、输出），然后调用一个**由 LLM 动态生成的专用最小化脚本**来进行状态合并。脚本基于 Hopcroft 或 Moore 算法的思想，但能处理数据路径约束与不完全指定。
  4. **验证流水线**：两步验证：① LLM 生成测试台进行功能测试（快速筛选）；② 通过 SAT 求解器或时序等价性检查（Yosys+ABC 或 Synopsys Formality）进行形式化等价性验证。

- **算法/公式说明**：采用肘部法确定候选规则阈值 \( i^* = \arg\max_{1 \le i < M} (s_i - s_{i+1}) \)，其中 \( s_i \) 为相似度得分；规则选择条件为 \( \text{sim}(e_{\text{query}}, e_{\text{rule}}) \ge \tau_{\text{elbow}} \)。FSM 形式化表示为 \( M = (Q, \Sigma, \delta, q_0, F) \)，部分指定 FSM 的转移函数扩展为 \( \delta_p: Q \times \Sigma \to 2^Q \)。

## 3. 实验设计：数据集、基准、对比方法

- **数据集与基准**：主要使用 **RTL-Rewriter benchmark**（来自 [46]），该基准包含 11 个短基准（侧重 Wires/Cells 优化）和多个长基准（FSM 与算法案例）。论文还自选了 10 个复杂 FSM 和算法示例（如 sppm_redundancy、subexpression_elim、adder_architecture、vending、fft）。
- **对比方法**：包含多个 LLM 基线：GPT-O1、GPT-4o、GPT-4-Turbo、GPT-3.5-Turbo、GPT-4o-mini；专用开源工具：Verigen（2B/16B）、RTLCoder-DeepSeek；以及现有最先进 LLM 优化方法 RTLRewriter。另外还对比了原始设计以及加了编译器优化（Synopsys DC）后的结果。
- **评价指标**：
  - 功能正确性：pass@k（k=1,5,10）。
  - 电路优化：小规模使用 Wires/Cells（反映底层物理特性）；大规模使用 PPA（功率、延迟、面积）并通过 Synopsys DC Compiler + SSC 库或 Yosys 测量。

## 4. 资源与算力

- 论文未明确说明训练所需的 GPU 型号、数量、训练时长。提到 SymRTLO 使用 GPT-4o 作为基础 LLM，并调用了 OpenAI 的 text-embedding-3-small 进行检索。所有实验均基于 API 调用完成，没有给出本地训练的资源消耗细节。**（因此只能注明“文中未明确说明具体算力需求”）**

## 5. 实验数量与充分性

- **实验组数**：
  - 功能正确性：在 benchmark 上计算 pass@1/5/10，共 1 组对比表（Table 4）。
  - 电路优化：11 个短基准的 Wires/Cells 对比（Table 5）；5 个 FSM 设计的 PPA 对比（Table 6）；5 个算法案例 PPA 对比（Table 7）。
  - 消融实验：移除 AST 模板、移除符号推理、移除目标导向搜索三种设置下平均 PPA 改善（Figure 5），共 3 组。
  - 额外有 PPA 整体改进散点图（Figure 4）以及与编译器组合优化的结果（Table 6/7 下部分）。
- **充分性与公平性**：
  - 覆盖了不同规模电路（小到 3 个 wires，大到 225 万 μm² 面积）。
  - 对比方法涵盖从 GPT-3.5 到 GPT-O1 的多个 LLM，以及专门工具 RTLRewriter、Verigen、RTLCoder，公平性较好。
  - 消融实验证明了各模块不可或缺。
  - **不足**：部分 RTLRewriter 的 PPA 结果无法在相同设置下复现（作者提到使用不同库），因此只进行了部分直接对比；数据集主要来自论文自身选取的 case，缺乏工业界大规模随机测试集。

## 6. 论文的主要结论与发现

- SymRTLO 在功能正确性上显著优于所有对比方法，pass@1 达到 97.5%（第二名 GPT-4o 仅 45.9%），说明其代码对齐能力强。
- 在 Wires/Cells 优化上，SymRTLO 达到 GeoMean 比值 0.63/0.67，超过了 RTLRewriter 的 0.69/0.77。
- 在 FSM 设计上，SymRTLO 相比原始设计平均改进功率 36.2%、延迟 17%、面积 35.7%（带编译器优化）；比 GPT-4o 提升 30%+。
- 在算法级案例上，SymRTLO 平均改进 PPA 约 30%、21%、20%（与 GPT-4o 比）。
- 消融实验表明，AST 模板、符号推理、目标导向搜索三个组件对最终性能均有重要贡献，移除任何一个都会导致明显下降。

## 7. 优点：方法或实验设计上的亮点

1. **方法创新**：首次将神经符号方法系统性地应用于 RTL 优化，同时解决了数据流和控制流的两大难题。
2. **模块化设计**：LLM 调度器、RAG 规则库、AST 模板、符号 FSM 优化、自动化验证五个模块松耦合，便于扩展与调试。
3. **可解释性与结果对齐**：通过 AST 模板和符号脚本强制规则执行，避免了纯 LLM 的随机性，输出可溯源。
4. **高效验证**：两步验证管道（测试台 + 形式化验证）大幅减少手动工作，同时保证功能等价性。
5. **实验全面**：对比了多个 LLM 基线、不同规模电路、有无编译器优化的场景，且做了消融，论证充分。

## 8. 不足与局限

1. **依赖底层 LLM 能力**：框架性能受限于 GPT-4o 等模型的推理和代码生成质量，对于训练数据中极少出现的电路模式可能效果不佳。
2. **规则库维护成本**：优化规则库需要不断更新，以跟上新的设计实践，否则可能过时。
3. **PPA 结果受工具版本影响**：使用 Synopsys DC Compiler 2019 与特定 SSC 库，更换工具或库后绝对数值会变，论文未做跨版本验证。
4. **符号模块扩展性**：虽然能处理不完备 FSM，但面对超大规模 FSM（状态数极大）时，形式化分析的计算开销可能过高。
5. **实验覆盖有限**：主要针对 RTL-Rewriter 基准和自选 case，未在更大规模工业设计（如完整 CPU、SoC）上验证；部分基线（如 RTLRewriter）因资源限制未完全复现其 PPA。
6. **缺少成本讨论**：未报告 API 调用次数、推理时间、总代价等实用化指标，不利于工程评估。

（完）
