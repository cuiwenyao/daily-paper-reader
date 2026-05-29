---
title: "CodeIO: Condensing Reasoning Patterns via Code Input-Output Prediction"
title_zh: CodeIO：通过代码输入输出预测凝聚推理模式
authors: "Junlong Li, Daya Guo, Dejian Yang, Runxin Xu, Yu Wu, Junxian He"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=feIaF6vYFl"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过代码输入输出预测提升LLM推理能力
tldr: LLM在多种推理任务上性能受限，CodeI/O通过将代码转化为输入输出预测格式，提取通用推理基元并用自然语言链式思维训练模型，显著提升了模型在逻辑规划、状态空间搜索等推理任务上的表现。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1775, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1681, \"height\": 1087, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 736, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 761, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 764, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 733, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-feiaf6vyfl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1600, \"height\": 403, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1636, \"height\": 1632, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1682, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1649, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 765, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 730, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1393, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1679, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1659, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-feiaf6vyfl/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1697, \"height\": 2064, \"label\": \"Table\"}]"
motivation: LLM在多样化推理任务上数据稀疏且碎片化，性能提升困难。
method: 将代码转化为输入输出预测任务，生成链式思维推理解释并训练模型。
result: 在多项推理任务上取得性能提升。
conclusion: CodeI/O通过代码推理模式凝聚增强了LLM的通用推理能力。
---

## Abstract
Reasoning is a fundamental capability of Large Language Models. While prior research predominantly focuses on enhancing narrow skills like math or code generation, improving performance on many other reasoning tasks remains challenging due to sparse and fragmented training data. To address this issue, we propose CodeI/O, a novel approach that systematically condenses diverse reasoning patterns inherently embedded in contextually-grounded codes, through transforming the original code into a code input-output prediction format. By training models to predict inputs/outputs given code and test cases entirely in natural language as Chain-of-Thought (CoT) rationales, we expose them to universal reasoning primitives—like logic flow planning, state-space searching, decision tree traversal, and modular decomposition—while decoupling structured reasoning from code-specific syntax and preserving procedural rigor. Experimental results demonstrate CodeI/O leads to consistent improvements across symbolic, scientific, logic, math & numerical, and commonsense reasoning tasks. By matching the existing ground-truth outputs or re-executing the code with predicted inputs, we can verify each prediction and further enhance the CoTs through multi-turn revision, resulting in CodeI/O++ and achieving higher performance. Our data and models will be publicly available.

---

## 论文详细总结（自动生成）

好的，以下是对该论文的详细中文总结。

---

### 论文详细中文总结：CodeI/O: 通过代码输入输出预测凝聚推理模式

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在数学和代码生成等特定推理任务上取得了显著进展，但在逻辑推理、科学推理、符号推理等更广泛的推理任务上表现不佳。这主要是因为训练这些任务所需的结构化、多样化、高推理密度的数据通常是稀疏且零散的。
- **研究背景**：现有的方法往往专注于提升单一技能（如数学或代码），但这些技能的数据容易获取且结构清晰。相比之下，许多其他推理领域缺乏类似的高质量训练数据。
- **核心动机**：作者认为，真实世界的代码程序天然蕴含了大量的、跨场景的、多样化的推理模式（如逻辑流规划、状态空间搜索、决策树遍历、模块化分解）。如果能有效利用这些代码中的推理模式，并将其泛化，就能提升LLM的通用推理能力。
- **整体含义**：这篇论文提出了一种名为`CodeI/O`的方法，旨在通过将代码转化为“输入-输出预测”任务，并训练模型用自然语言链式思维（CoT）来推导答案，从而挖掘并“凝聚”代码中蕴含的通用推理模式，最终提升模型在多种非代码推理任务上的能力。

#### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将代码作为推理模式的“宝库”，通过设计一个精巧的数据构建和训练流程，将代码的“结构化推理”与“代码语法”解耦，让模型学到更通用的推理方法。
- **关键技术细节**：
    1.  **数据构建流水线**：
        - **收集原始代码**：从多个来源收集了约81万份Python代码文件，包括内部预训练语料库、高质量教育代码集（如PythonEdu的子集）以及在线编程平台的数据，以确保代码覆盖算法、数学、科学、逻辑谜题等多种推理场景。
        - **转换为统一格式**：使用强大的LLM（DeepSeek-V2.5）将原始代码重构为可执行的统一格式，包含：一个主入口函数、输入/输出描述、一个输入生成器（用于按规则生成测试输入）和一个描述函数功能的查询。
        - **收集输入-输出对**：执行输入生成器，产生多个输入样本，再执行代码得到对应的输出，从而形成（输入， 输出）对。
        - **生成CoT反应**：将函数、查询、参考代码以及给定输入或输出作为提示，再次使用DeepSeek-V2.5生成用于预测输入或输出的自然语言CoT推理过程，作为最终的训练数据（`CodeI/O`数据集）。
        - **多轮修正**：利用代码的可验证性，对预测错误的CoT反应进行反馈（告知预测错误，并可选地提供执行后的反馈），让模型再次尝试生成正确的推理。将第一轮错误的反馈和第二次成功/失败的反应拼接成更长的训练样本，形成增强版数据集`CodeI/O++`。
        - **最终结果**：从约45万个代码文件中，生成了约350万个训练样本，其中输入预测和输出预测各占约50%。

    2.  **训练策略**：采用两阶段训练策略，这是在持续预训练（continual pre-training）中常用的方法。
        - **第一阶段**：在`CodeI/O`或`CodeI/O++`数据集上训练，旨在强化模型作为通用推理的基础模型。
        - **第二阶段**：在通用的指令微调（instruction-tuning）数据集上训练，使模型能够适应各种下游任务，遵循不同的指令。这种分离训练方式避免了数据分布严重偏斜（因为`CodeI/O`数据量远大于指令微调数据）导致模型无法很好地学习指令跟随。

#### 3. 实验设计：使用了哪些数据集/场景、benchmark、对比了哪些方法

- **基础模型**：选择四种参数规模（7B到30B）和架构各异的先进基础模型作为基座，包括Qwen 2.5 7B Coder, DeepSeek Coder v2 Lite 16B (MoE), LLaMA 3.1 8B, 和 Gemma 2 27B。
- **评估基准**：模型在14个不同的推理基准上进行评估，涵盖多个领域：
    - 符号推理：BBH， BBH-ZH
    - 科学推理：GPQA， MMLU-STEM
    - 逻辑推理：ZebraLogic， KorBench
    - 数学与数值推理：GSM8K， MATH， DROP
    - 常识推理：WinoGrande
    - 代码理解与执行：CRUXEval， LeetCode-O （作者自建）， LiveBench （仅推理子集）
- **对比方法**：主要对比了在“第一阶段”使用不同数据集的性能，包括：
    - **单阶段基线**：直接在指令微调数据上训练。
    - **WebInstruct**：来自互联网的大量指令微调数据集。
    - **OpenMathInstruct-2**：专注于数学推理的数据集。
    - **OpenCoder-SFT-Stage-1**：从代码数据中合成的问题-答案对数据集。
    - **PythonEdu**：高质量原始代码文件，使用标准语言建模损失进行训练。
- **评估方式**：所有评估均采用零样本（zero-shot）贪婪解码（除BBH采用3样本少样本设置）。报告了每个基准上的具体得分和平均得分。

#### 4. 资源与算力

- **未明确说明**：论文在正文、实验设置及附录中均未明确提及具体使用了多少GPU型号、数量或总训练时长。仅给出了学习率（如1e-5）、批量大小（1024）和训练步数（第一阶段1个epoch，第二阶段700步）等超参数设置。考虑到使用了四个不同大小的模型进行训练和评估，且未提供具体优化器参数（如AdamW），可以推测其计算量是相当大的，但作者未披露详细信息。

#### 5. 实验数量与充分性：实验是否充分、客观、公平？

- **实验数量丰富**：进行了大量的实验以验证方法的有效性：
    - **主实验**：在四种不同大小的模型上，每个模型对比了多种基线方法（共6-8种配置）和两个版本的`CodeI/O`，在14个基准上进行了评估，总共产生了数百组结果。
    - **消融实验**：研究输入预测/输出预测的单独效果、拒绝采样的影响、使用不同模型（DeepSeek-V2.5 vs. Qwen/Mixtral）合成数据的效果、数据来源的贡献、数据格式的影响、以及两阶段训练的必要性。
    - **缩放性分析**：分析了训练数据量（样本数量和每个样本的IO对数量）对性能的影响。
    - **数据泄露分析**：严格使用13-gram重叠检测来评估测试集泄露问题，并通过在无泄露子集上重新计算增益来证明结论的可靠性。
- **实验充分且客观**：
    - 对比了多种强基线方法，覆盖了不同领域的生成数据集。
    - 控制了比较的公平性，例如将某些大型数据集（如WebInstruct、OpenMathInstruct-2）子采样到与`CodeI/O`数据量一致（3.5M）。
    - 采用了严格的数据泄露检测，并验证了性能提升不是由泄露导致的。
    - 实验结果表1中清晰地展示了不同方法在每个基准上的具体得分和变化（用绿色/红色标记提升/下降），非常直观。

#### 6. 论文的主要结论与发现

1.  **`CodeI/O` 有效提升通用推理能力**：在具有挑战性的推理任务（逻辑、科学、符号、常识等）上，`CodeI/O`普遍优于单阶段训练基线和其他强基线方法，甚至在数学任务上也保持了竞争力。
2.  **`CodeI/O++` 进一步提升性能**：通过利用代码执行反馈进行多轮修正，`CodeI/O++`在`CodeI/O`的基础上带来了一致且显著的性能提升，且几乎没有在个别任务上造成性能下降。
3.  **性能提升源于任务设计而非数据量或模型**：
    - 对比在原始代码（PythonEdu）上进行的语言建模训练，`CodeI/O`在任务设计上的优势明显，证明结构化的预测任务比直接学习代码本身更重要。
    - 即使使用相同的教师模型（DeepSeek-V2.5）重新生成WebInstruct数据，其效果仍不及`CodeI/O`，说明代码数据的多样性优于其他领域的数据。
4.  **两阶段训练策略至关重要**：将`CodeI/O`训练与指令微调分开进行，比混合训练效果更好。这为如何将此类大规模的、针对推理的训练数据融入整体训练流程提供了指导。
5.  **代码的多样性和可验证性是关键**：仅使用一半的`CodeI/O`数据或仅进行输入/输出预测，性能都会有所下降，证明了数据和任务设计的平衡性。

#### 7. 优点：方法或实验设计上的亮点

- **创新的任务设计**：将传统的代码输入输出预测任务改造成一个学习通用推理的工具。这种方法巧妙地捕捉了代码中的逻辑严谨性和多样性，同时去除了代码语法带来的干扰，使得学到的推理模式可以迁移到其他领域。
- **高可扩展性**：数据构建流程高度自动化，可以从庞大的代码库中高效生成大量训练样本。
- **可验证性**：利用代码的可执行特性，可以自动验证模型预测的正确性，并用于多轮修正，从而产生更高质量的训练数据（`CodeI/O++`）。
- **全面的实验设计**：实验覆盖了多个模型家族、规模、以及广泛的推理基准。进行了深入的消融研究和数据泄露分析，使得结论具有很强的说服力和鲁棒性。
- **客观的报告**：报告中不仅展示了平均性能提升，还诚实地展示了在某些基准上的微小下降或持平，强调了其提升的“平衡性”和“通用性”，而非只挑最好的一面。

#### 8. 不足与局限

- **计算成本问题**：数据构建依赖一个大型LLM（DeepSeek-V2.5）进行代码重构、CoT生成和多轮修正，计算成本很高。论文未提供具体的“教师模型”使用成本或总算力预算，这对资源有限的团队可能是一个障碍。
- **代码依赖偏差**：方法高度依赖“结构良好的、可执行的、包含复杂推理模式”的Python代码。对于一些没有良好代码表示或难以结构化的推理任务（如纯空间推理、某些常识推理），其迁移效果可能有限。
- **合成数据的潜在风险**：训练数据全部由另一个LLM合成本质上是一种知识蒸馏。模型的推理能力上限可能受限于“教师模型”（DeepSeek-V2.5）。如果教师模型在某些推理模式上存在偏误或不足，学生模型也会继承这些缺陷。
- **实验局限**：
    - 实验报告中所有模型都用了同样的数据量（3.5M）进行比较，但对于大型模型（如27B的Gemma 2）来说，这可能不是最优选择，他们可能能从更大的数据集中获益更多。
    - 虽然在多轮修正中，第二次修正效果不明显，但未能深入分析原因（如模型在原地打转、缺乏新知识注入等），也没有提出解决方案。
    - 对“输入生成器”的质量没有进行额外分析。如果输入生成器产生的输入模式过于单一或无法覆盖某些复杂的推理分支，训练出的模型可能会在处理这些分支时表现不佳。

（完）
