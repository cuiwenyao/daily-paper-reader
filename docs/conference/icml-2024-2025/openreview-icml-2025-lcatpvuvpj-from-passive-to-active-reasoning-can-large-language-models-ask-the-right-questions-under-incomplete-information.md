---
title: "From Passive to Active Reasoning: Can Large Language Models Ask the Right Questions under Incomplete Information?"
title_zh: 从被动到主动推理：大语言模型能在信息不完整时提出正确问题吗？
authors: "Zhanke Zhou, Xiao Feng, Zhaocheng Zhu, Jiangchao Yao, Sanmi Koyejo, Bo Han"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=LCaTpVuvpj"
tags: ["query:ns-xai"]
score: 5.0
evidence: 大语言模型主动推理基准
tldr: 现有基准主要评估大语言模型的被动推理，即提供所有信息。本文提出AR-Bench，专注于主动推理场景：模型需在不完整信息下主动提问获取证据。涵盖侦探案例、情景谜题和猜数字三类任务。实验揭示主流LLM在主动推理上存在显著不足，为未来研究提供测试平台。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 834, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1772, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1747, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1725, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1772, \"height\": 869, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1769, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1734, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1754, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1751, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lcatpvuvpj/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1502, \"height\": 900, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1776, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 844, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1770, \"height\": 674, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1770, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1747, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 545, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 861, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 838, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 685, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1717, \"height\": 645, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1720, \"height\": 643, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1742, \"height\": 557, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1782, \"height\": 434, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1789, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1787, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 878, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1381, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 870, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 360, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 362, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1783, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 341, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lcatpvuvpj/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1056, \"height\": 325, \"label\": \"Table\"}]"
motivation: 缺乏评估LLM主动推理能力的基准。
method: 构建AR-Bench，包含三类需要主动提问的任务。
result: 主流LLM在主动推理任务上表现不佳。
conclusion: AR-Bench揭示了LLM主动推理的局限性，促进相关研究。
---

## Abstract
While existing benchmarks probe the reasoning abilities of large language models (LLMs) across diverse domains, they predominantly assess passive reasoning, providing models with all the information needed to reach a solution. By contrast, active reasoning—where an LLM must interact with external systems to acquire missing evidence or data—has received little systematic attention. To address this shortfall, we present AR-Bench, a novel benchmark designed explicitly to evaluate an LLM’s active reasoning skills. AR-Bench comprises three task families—detective cases, situation puzzles, and guessing numbers—that together simulate real-world, agentic scenarios and measure performance across commonsense, logical, and symbolic reasoning challenges.
Empirical evaluation on AR-Bench demonstrates that contemporary LLMs exhibit pronounced difficulties with active reasoning: they frequently fail to acquire or leverage the information needed to solve tasks. This gap highlights a stark divergence between their passive and active reasoning abilities. Moreover, ablation studies indicate that even advanced strategies, such as tree-based searching or post-training approaches, yield only modest gains and fall short of the levels required for real-world deployment. 
Collectively, these findings highlight the critical need to advance methodology for active reasoning, e.g., incorporating interactive learning, real-time feedback loops, and environment-aware objectives for training.
The benchmark is publicly available at: https://github.com/tmlr-group/AR-Bench.

---

## 论文详细总结（自动生成）

好的，这是您要求的对给定论文的详细中文总结。

### 论文总结：从被动到主动推理：大语言模型能在信息不完整时提出正确问题吗？

#### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：当前大语言模型（LLMs）的推理能力评估大多集中在“被动推理”（Passive Reasoning）上，即模型接收全部必要信息后直接推导答案。然而，现实世界中的许多任务（如医疗诊断、旅行规划）都涉及“主动推理”（Active Reasoning），即模型必须在信息不完整的情况下，通过主动提问与外部系统交互来获取缺失信息。本文旨在系统性地评估LLMs是否具备有效的主动推理能力。
- **研究动机**：主动推理是实现通用人工智能的关键一环，但现有研究对此关注不足，缺乏专用的评估基准。作者旨在填补这一空白，构建一个专门评估LLMs主动推理能力的基准，并揭示当前模型在此方面的严重短板。
- **整体含义**：当前最先进的LLMs在主动推理任务上表现不佳，与其相对成熟的被动推理能力形成鲜明对比。这表明，要实现可靠的AI智能体应用，必须将研究方向从“被动解答”转向“主动询问”。

#### 2. 论文提出的方法论：AR-Bench基准

- **核心思想**：构建一个包含多轮交互的动态评估环境。模型（玩家）需在仅获得部分信息的条件下，通过与外部信息源（NPCs或规则函数）进行多轮对话，主动提问以收集线索，最终做出正确决策。评估不仅看最终答案，还衡量提问过程的质量。
- **关键技术细节与评估流程**：
    1.  **任务构成**：AR-Bench包含三个子任务，分别测试不同维度的推理：
        - **侦探案件 (DC)**：测试常识推理。模型扮演侦探，通过向五名嫌疑人（由另一个LLM扮演）提问，找出真凶。反馈信息可能复杂且有噪音。
        - **情景谜题 (SP)**：测试逻辑推理。模型需要不断向裁判（LLM）提出是非题，以揭开一个反直觉情景背后的真相。反馈为“是/否/未知”。
        - **猜数字 (GN)**：测试符号推理。模型需要猜测一个有四位的唯一数字。每次猜测后，会收到关于正确数字和位置的符号化反馈。
    2.  **评估指标**：
        - **结果指标**：衡量最终答案的正确性。DC任务使用识别凶手的准确率（Accuracy）；SP任务使用与标准答案的F1分数；GN任务使用数字完全匹配的准确率（Exact Match）。
        - **过程指标**（Process Score）：衡量提问过程的质量。对于DC和SP，通过计算模型提问历史中，能覆盖多少预先定义的“关键问题”来衡量。对于GN，通过评估当前猜测与正确答案的接近程度来衡量。这比仅看最终结果提供了更细粒度的分析。
    3.  **自动化构造**：DC和SP任务的数据集通过一个四阶段的自动流水线生成（核心采样、树状故事扩展、关键问题提取、谜题合成），并由人工验证确保逻辑一致性。GN任务则通过穷举所有四位唯一数字生成。
    4.  **评估实现**：一个Llama-3.1-405B模型充当DC和SP中的信息提供方（NPC/裁判），确保可复现性。GN使用规则函数提供反馈。

#### 3. 实验设计

- **基准（Benchmark）**：AR-Bench，包含6000+个谜题（DC: 500, SP: 500, GN: 5040个）。
- **对比方法**：
    - **LLMs**：Llama-3.1 (8B, 70B, 405B)、Qwen-2.5 (3B, 7B)、QwQ-32B、GPT-4o-mini、GPT-4o。
    - **通用推理方法**：零样本（Zero-shot）、少样本（Few-shot）、指令驱动（Instruction-driven）、思维树（Tree-of-Thoughts, ToT）、监督微调（SFT）、直接偏好优化（DPO）。
    - **高级主动推理方法**：Proactive Chain-of-Thought、Uncertainty-of-Thought (UoT)。
    - **人类基线**：邀请本科生在部分数据上进行评估。
- **数据集/场景**：在AR-Bench的三个子任务（DC, SP, GN）上进行了全面评估。

#### 4. 资源与算力

- 论文未明确提供计算资源的详细信息，如使用的GPU型号、数量及训练时长。仅提到在微调Llama-3.1-8B和70B模型时，分别使用了LoRA和QLoRA技术来减少计算需求，但未说明具体算力投入。

#### 5. 实验数量与充分性

- **实验数量**：非常丰富。论文包含了：
    - **主实验**：在AR-Bench的所有任务上，对比了8种LLMs和6种方法，展示了结果分数（Figures 4, 5）。
    - **过程分析**：展示了提问过程中模型得分的动态变化（Figures 8, 9），验证了早期增益、后期停滞的现象。
    - **消融研究**：探究了模型规模、交互轮数、信息检索与处理分离等的影响（Figures 9, 10, 11）。
    - **方法失败验证**：测试了Proactive CoT和UoT方法的无效性（Figure 6）。
    - **法官可靠性验证**：使用TurtleBenchmark等测试了LLM作为信息提供者的可靠性（Figure 12）。
    - **错误模式分析**：对常见错误进行了分类统计（Table 3）。
    - **案例研究**：展示了具体的正确和错误求解过程（Figure 13）。
- **充分性与公平性**：实验设计较为全面，涵盖了多种模型、方法、任务和维度。通过设置固定交互轮数和相同的初始信息，保证了不同模型间的公平比较。但实验主要集中在合成数据集上，其结论向真实复杂场景的泛化性有待验证。

#### 6. 主要结论与发现

- ****核心发现**：**当前最先进的LLMs在主动推理任务上表现显著不足。例如GPT-4o在GN任务上仅达到35%的准确率，而人类基线则远超模型。
- **具体发现**：
    1.  **性能鸿沟大**：几乎所有现有方法和模型在AR-Bench上表现不佳，与传统被动推理成绩形成巨大反差。
    2.  **提问质量低**：模型在早期回合进步明显，但后期停滞，难以持续提出高质量、有深度的新问题。
    3.  **搜索策略受限**：树搜索方法（ToT）未能带来显著提升，归因于不可靠的验证器（Verifier）和模型自身生成低质量候选问题。
    4.  **常见方法失效**：SFT、DPO、Proactive CoT等方法对主动推理提升甚微。
    5.  **模型规模与轮数扩展效果有限**：更大的模型和更多的交互轮数带来了一些改进，但远不足以完全解决任务。
    6.  **存在特定错误模式**：模型在DC中经常误解时间线，在SP中做出无根据的假设，在GN中反复猜测同一组错误数字。

#### 7. 优点

- **定义清晰**：明确区分并定义了“被动推理”和“主动推理”两个重要概念，为未来研究指明了方向。
- **创新性强**：提出了一个专为评估主动推理而设计的全新基准（AR-Bench），弥补了当前评测体系的空白。
- **评估全面**：不仅提供最终结果指标，还引入了过程指标（Process Score）进行细粒度分析，能更深入地理解模型缺陷。
- **实验充分**：通过大量的对比实验、消融研究和错误分析，系统性地揭示了LLMs在主动推理上的各种局限性，结论具有很强的说服力。
- **公开可用**：基准已开源，降低了社区进行相关研究的门槛。

#### 8. 不足与局限

- **实验环境的模拟性**：实验环境（如固定的交互轮数、模板化的反馈）相对简化，可能无法完全反映真实世界中更复杂、动态的主动推理场景（如自由对话、多元反馈来源）。
- **法官可靠性**：虽然实验验证了LLM法官（Judge）的可靠性，但其仍存在不确定性。未来的工作可以探索更鲁棒的评估方法。
- **数据集偏差**：数据集由特定方法（GPT-4o）自动生成，可能存在未知偏差，其是否完全公平地评估所有模型仍需探讨。
- **应用限制**：论文指出了模型的不足，但并未提出有效的改进方法。AR-Bench的价值目前主要体现在“发现问题”而非“解决问题”上。提出的未来方向（如强化学习）仅在文中作为建议，缺乏实验验证。
- **算力信息缺失**：未披露计算资源的详细信息，使得复现和对比实验结果变得困难。

（完）
