---
title: Scaling Code-Assisted Chain-of-Thoughts and Instructions for Model Reasoning
title_zh: 扩展代码辅助思维链与指令以增强模型推理
authors: "Honglin Lin, Qizhi Pei, Zhuoshi Pan, Yu Li, Xin Gao, Juntao Li, Conghui He, Lijun Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=b7bOWd3kUL"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过代码辅助思维链扩展大模型推理
tldr: 不相关
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1151, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1263, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1307, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1282, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1352, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b7bowd3kul/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 68, \"height\": 100, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-b7bowd3kul/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 1108, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b7bowd3kul/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b7bowd3kul/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1161, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b7bowd3kul/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1444, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b7bowd3kul/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1009, \"height\": 344, \"label\": \"Table\"}]"
motivation: 不相关。
method: 不相关。
result: 不相关。
conclusion: 不相关。
---

## Abstract
Reasoning capability is pivotal for Large Language Models (LLMs) to solve complex tasks, yet achieving reliable and scalable reasoning remains challenging. While Chain-of-Thought (CoT) prompting has become a mainstream approach, existing methods often suffer from uncontrolled generation, insufficient quality, and limited diversity in reasoning paths. 
Recent efforts leverage code to enhance CoT by grounding reasoning in executable steps, but such methods are typically constrained to predefined mathematical problems, hindering scalability and generalizability. 
In this work, we propose \texttt{Caco} (Code-Assisted Chain-of-ThOught), a novel framework that automates the synthesis of high-quality, verifiable, and diverse instruction-CoT reasoning data through code-driven augmentation. Unlike prior work, \texttt{Caco} first fine-tunes a code-based CoT generator on existing math and programming solutions in a unified code format, then scales the data generation to a large amount of diverse reasoning traces. Crucially, we introduce automated validation via code execution and rule-based filtering to ensure logical correctness and structural diversity, followed by reverse-engineering filtered outputs into natural language instructions and language CoTs to enrich task adaptability. This closed-loop process enables fully automated, scalable synthesis of reasoning data with guaranteed executability. 
Experiments on our created \texttt{Caco}-1.3M dataset demonstrate that \texttt{Caco}-trained models achieve strong competitive performance on mathematical reasoning benchmarks, outperforming existing strong baselines. Further analysis reveals that \texttt{Caco}’s code-anchored verification and instruction diversity contribute to superior generalization across unseen tasks. Our work establishes a paradigm for building self-sustaining, trustworthy reasoning systems without human intervention.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的推理能力是实现复杂任务的关键，但现有 Chain-of-Thought（CoT）方法存在三大缺陷：
  - **不可验证性**：自然语言推理步骤不可执行，错误会累积。
  - **可扩展性差**：高质量 CoT 数据依赖人工标注，难以规模化。
  - **多样性不足**：生成的推理路径单一，泛化能力受限。
- **研究背景**：已有工作尝试使用代码辅助推理（如 PoT、PAL、MathCoder），但通常局限于预定义的数学问题，缺乏通用性和可扩展性。
- **整体含义**：本文提出 **Caco（Code-Assisted Chain-of-ThOught）**，一种通过代码驱动的增强方法自动合成高质量、可验证、多样化的指令-CoT 推理数据，实现无需人工干预的闭环推理数据生成，从而提升 LLM 在数学推理及更广泛领域的能力。

## 2. 论文提出的方法论

### 核心思想
利用代码的**可执行性**和**形式化结构**，通过三个关键步骤实现推理数据的自动规模化合成：
1. **统一代码 CoT 表示**：将数学和算法问题的解决方案转化为标准化的可执行 Python 程序。
2. **代码 CoT 生成与扩展**：训练专用的代码生成模型（CodeGen）大量采样新的推理代码，并通过执行和规则过滤保证质量。
3. **指令反转与自然语言 CoT 生成**：将验证后的代码反向翻译为自然语言问题，再生成对应的自然语言 CoT，并执行双重一致性验证。

### 关键技术细节
- **统一代码 CoT**：
  - 从 MATH、DeepScaleR、BigMath 等数据集中收集数学问题，从 Kodcode 数据集中收集算法问题。
  - 将所有解决方案转换为标准 Python 模板：定义 `input` 字典，调用函数，赋值给 `output`，打印结果。
  - 经过可执行性、效率、代码长度、AST 分析、输出一致性等严格过滤，得到 146K 高质量种子代码 CoT（122K 数学 + 24K 算法）。
- **代码 CoT 扩展（CodeGen）**：
  - 在种子代码 CoT 上无监督微调 Qwen2.5-Coder-7B 作为 CodeGen，仅使用代码文本，不包含问题上下文，以学习推理模式空间。
  - 通过温度采样生成约 5.3M 候选代码 CoT，过滤后保留约 4.6M 可执行且结构正确的程序。
  - 支持两种增强模式：
    - **问题级增强**：同一逻辑模板反向翻译为不同场景的问题。
    - **模式级增强**：CodeGen 探索新的推理结构（如分解、替代策略）。
- **指令反转与语言 CoT 生成**：
  - **两阶段生成**：① 使用 Qwen3-8B 从代码反向生成自然语言问题；② 将生成的问题重新输入 LLM 生成自然语言 CoT（强制独立推理，防止懒惰模式）。
  - **双重验证**：
    - 答案一致性：执行代码的输出与语言 CoT 的最终答案比较，不匹配则丢弃。
    - CoT 一致性：判断语言 CoT 与代码 CoT 的逻辑是否一致（使用 Prompt 7），不匹配则丢弃。
  - 最终得到 **Caco-1.3M** 数据集（约 130 万已验证的指令-答案对）。

## 3. 实验设计

| 要素 | 说明 |
|------|------|
| **数据集/场景** | 数学推理：MATH、GSM8K、CollegeMath、DeepMind-Mathematics、OlympiadBench-Math、TheoremQA；额外泛化：AGIEval、AIME24、HumanEval+、ARC-c、BBH、KorBench、科学推理（MegaScience）。 |
| **基准（benchmark）** | 6个标准数学推理基准 + 多个跨领域基准。 |
| **对比方法** | 数据增强方法：MetaMath、MMIQC、NuminaMath、MathFusion、RFT、DART-Math；指令/RL模型：LLaMA3-7B-Instruct、Qwen2.5-Math-Instruct、DeepSeekMath-7B-RL。 |
| **基础模型** | DeepSeekMath-7B、Qwen2.5-Math-7B、LLaMA3-8B，覆盖数学专用和通用模型。 |
| **评估方式** | Zero-shot 设置，greedy decoding，Pass@1 准确率。 |

## 4. 资源与算力

- **数据生成阶段**（单台 8×A100 80GB）：
  - 统一代码 CoT：2 小时（339K 样本）
  - 扩展代码 CoT：8 小时（5.3M 样本）
  - 问题反转：5 小时（4.6M 样本）
  - 答案生成：40 小时（4.6M 样本）
  - **总耗时约 55 小时** 生成 1.3M 验证样本。
- **模型训练**：使用 8 张 NVIDIA A100 GPU，采用 LLaMA Factory 框架，训练 3 epoch，batch size 128，学习率 5e-6，cosine 衰减，warm-up 0.03，最大序列长度 4096。
- **统一代码 CoT 生成**使用 Qwen2.5-72B-Instruct（部署在 4 A100）。
- **问题反转与答案生成**使用 Qwen3-8B。
- **评估**使用 Qwen3-32B 进行可解性、正确性和一致性检查。

## 5. 实验数量与充分性

- **主实验**（表 1）：3 个基础模型 × 2 种数据规模（596K、1.3M），对比 7-8 种基线方法，在 6 个数学基准上全面报告。
- **消融与分析**：
  - 数据多样性分析（t-SNE 分布、KMeans 聚类，图 4）。
  - 数据可扩展性分析（图 5c）：数据量从 109K → 300K → 596K → 1.3M，性能持续提升。
  - 验证机制消融（图 5a、5b）：对比有/无验证的数据质量和下游性能。
  - 跨领域泛化（表 2、表 3）：评估在 AGIEval、AIME24、HumanEval+、ARC-c、BBH、KorBench、科学推理（MegaScience）上的表现。
  - 控制实验（附录 C 表 4）：区分 Caco 与教师知识蒸馏和 STaR 自改进，证明 Caco 的增益来自代码驱动的多样性增强。
- **充分性评价**：实验覆盖了数学推理主流基准、多种基础模型、不同数据规模、关键组件消融、跨领域泛化，且对比了多个强基线。但未报告多次运行的误差棒（No），统计显著性未量化，这在严格性上略有不足。

## 6. 论文的主要结论与发现

1. **Caco 数据显著提升数学推理性能**：在 Qwen2.5-Math-7B 上，Caco-1.3M 达到平均 67.7% 准确率，超越所有对比方法（如 DART-Math 54.5%，MathFusion 59.8%），并接近/超过指令微调模型（Qwen2.5-Math-Instruct 63.6%）。
2. **代码验证和多样性是关键**：消融实验证实，验证机制大幅提高了数据正确率（从 88% 到 93%），下游性能提升 1 个百分点（表 5b）。多样性分析显示 Caco 数据覆盖了比原始种子更广泛的嵌入空间。
3. **可扩展性强**：随着数据量从 109K 增加到 1.3M，性能持续提升，尤其在通用模型 LLaMA3-8B 上提升显著（从 46.7 到 57.3）。
4. **跨领域泛化能力**：Caco 模型在非数学任务（逻辑推理、代码、科学问答）上也取得显著提升，表明方法具有通用性。例如，在 MegaScience 科学推理上，Caco 扩展数据使 LLaMA 平均准确率从 59.0 提升到 63.4。

## 7. 优点

- **完全自动化**：从种子代码到数据生成、验证、反转，无需人工标注，构建可自我维持的推理系统。
- **可验证性**：通过代码执行进行严格验证，确保推理步骤的正确性，减少幻觉。
- **高可扩展性**：利用预训练 CodeGen 模型大规模采样，可生成百万级高质量数据。
- **多样性**：模式级和问题级增强共同保证了推理路径和问题表述的丰富性，有利于泛化。
- **跨领域框架**：核心思想（代码抽象逻辑 → 采样 → 反转验证）可适用于任何具有符号/程序性结构的领域（如科学推理、逻辑谜题）。
- **开源友好**：论文提供了完整代码和数据集链接（GitHub、Hugging Face），使用的模型均为开源，便于复现。

## 8. 不足与局限

- **问题类型受限**：生成的数据仍受限于种子数据中定义的模板和问题类型，对于高度创新或非常规的问题，可能无法生成合理的代码 CoT，导致分布偏差。
- **反向翻译丢失细节**：从代码转换回自然语言时，可能简化或丢失某些上下文细节，使最终问题不够丰富。
- **代码仅用于过滤**：生成的代码 CoT 并未直接用于训练，而是作为验证工具，潜在地浪费了代码中的结构化逻辑信息。论文承认未来可探索将代码直接融入训练。
- **应用范围当前有限**：主要针对数学和算法推理，虽然展示了科学推理的初步结果，但扩展到更广泛的领域（如逻辑谜题、STEM 综合分析）仍需额外工作。
- **统计显著性未报告**：实验未给出误差棒或置信区间，无法判断结果是否统计显著，这对对比性结论的可靠性有一定影响。
- **计算成本**：虽然生成 1.3M 数据仅需 55h / 8 GPU，但训练 CodeGen 和多次验证仍需要相当的算力，对于资源有限的团队可能门槛较高。

（完）
