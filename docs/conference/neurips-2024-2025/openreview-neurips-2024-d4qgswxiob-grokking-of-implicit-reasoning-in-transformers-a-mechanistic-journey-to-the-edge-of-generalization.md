---
title: "Grokking of Implicit Reasoning in Transformers: A Mechanistic Journey to the Edge of Generalization"
title_zh: Transformer隐式推理的Grokking：通向泛化边缘的机制之旅
authors: "Boshi Wang, Xiang Yue, Yu Su, Huan Sun"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=D4QgSWxiOb"
tags: ["query:ns-xai"]
score: 8.0
evidence: 对Transformer隐式推理的机制性可解释研究
tldr: 该论文发现Transformer只能通过grokking（过拟合后的泛化）学习隐式推理，并深入分析了内部机制。揭示了模型在组合与比较推理上的泛化差异，为大神经模型的可解释推理提供了机制性洞见。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1300, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1220, \"height\": 673, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1132, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1416, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1112, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 1320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1383, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1321, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1323, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1318, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 856, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 850, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 852, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1378, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-d4qgswxiob/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 852, \"height\": 686, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-d4qgswxiob/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1429, \"height\": 182, \"label\": \"Table\"}]"
motivation: 语言模型在隐式推理上存在困难，其学习机制不清楚。
method: 通过扩展训练至过拟合后研究grokking现象，并进行机制分析实验。
result: Transformer能学习隐式推理但需要grokking，且组合推理无法系统泛化。
conclusion: 揭示了隐式推理的机制性条件，对可解释推理有重要贡献。
---

## Abstract
We study whether transformers can learn to *implicitly* reason over parametric knowledge, a skill that even the most capable language models struggle with. Focusing on two representative reasoning types, composition and comparison, we consistently find that transformers *can* learn implicit reasoning, but only through *grokking*, i.e., extended training far beyond overfitting. The levels of generalization also vary across reasoning types: when faced with out-of-distribution examples, transformers fail to systematically generalize for composition but succeed for comparison. We delve into the model's internals throughout training, conducting analytical experiments that reveal: 1) the mechanism behind grokking, such as the formation of the generalizing circuit and its relation to the relative efficiency of generalizing and memorizing circuits, and 2) the connection between systematicity and the configuration of the generalizing circuit. Our findings guide data and training setup to better induce implicit reasoning and suggest potential improvements to the transformer architecture, such as encouraging cross-layer knowledge sharing. Furthermore, we demonstrate that for a challenging reasoning task with a large search space, GPT-4-Turbo and Gemini-1.5-Pro based on non-parametric memory fail badly regardless of prompting styles or retrieval augmentation, while a fully grokked transformer can achieve near-perfect accuracy, showcasing the power of parametric memory for complex reasoning.

---

## 论文详细总结（自动生成）

# 论文《Grokking of Implicit Reasoning in Transformers》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（如 GPT-4）在隐式推理（implicit reasoning）方面存在显著缺陷。它们虽然能够记忆大量事实，但在需要组合知识（如“Barack 的妻子是 Michelle，Michelle 出生于 1964 年”→推出“Barack 的妻子出生于 1964 年”）或比较属性（如比较两人年龄）时，即使知道所有原子事实，也常常无法正确推理。这种失败被称为“组成性差距”（compositionality gap）。论文旨在探究：Transformer 是否能够通过参数化记忆（parametric memory）学会隐式推理？如果能，是何时、如何发生的？是否存在根本性的架构限制？
- **整体含义**：论文首次在知识推理任务中观察到“grokking”现象（即过拟合后突然泛化），并通过机制性分析揭示了 Transformer 在隐式推理中泛化的内部电路及其局限性。研究表明，数据分布（而非数据规模）是决定泛化速度的关键；并解释了为何组合（composition）无法系统泛化而比较（comparison）可以。此外，论文还展示了参数化记忆在复杂推理（大搜索空间）中的巨大潜力，远超当前最强 LLM（GPT-4-Turbo、Gemini-1.5-Pro）基于非参数化记忆（上下文或检索增强）的能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将推理概念化为归纳和应用推理规则。构造合成数据集，包含“原子事实”（atomic facts）和“推理事实”（inferred facts，由原子事实通过规则推导得出）。训练 Transformer 从零开始预测推理事实的尾实体，测试其在分布内（ID）和分布外（OOD）的泛化能力。通过操控训练数据中推理事实与原子事实的比例（ϕ）以及数据规模，研究 grokking 的产生条件。
- **关键技术细节**：
  - **任务设计**：
    - **组合任务（Composition）**：两跳推理规则：\((h, r_1, b) \land (b, r_2, t) \Rightarrow (h, r_1, r_2, t)\)。原子事实构成知识图谱（|E| 个实体、200 种关系，每个实体 20 个关系）。ID 和 OOD 原子事实按 95%:5% 划分。
    - **比较任务（Comparison）**：基于属性值比较：\((e_1, a, v_1) \land (e_2, a, v_2) \land v_1 < v_2 \Rightarrow (a, e_1, e_2, a_<)\) 等。|E|=1000，|A|=20 属性，|V|=20 值。
  - **模型与优化**：标准 GPT-2 式 decoder-only Transformer：8 层，768 隐藏维度，12 注意力头。优化器 AdamW，lr=1e-4，batch size=512，weight decay=0.1，2000 warm-up steps。训练远超过拟合点（通常数十万步）。
  - **分析技术**：
    - **Logit Lens**：将隐藏状态乘以输出嵌入矩阵，解码为词汇概率。
    - **Causal Tracing**：通过扰动输入（替换同类型 token）并测量对目标状态的影响，量化因果强度。识别出关键电路节点（如层、位置）。
- **公式**：无显式公式；规则以逻辑式表示（见上文）。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - **合成数据集**：随机生成知识图谱/属性值表，用于组合和比较任务。ID 和 OOD 原子事实按比例划分。训练集包含所有 ID 原子事实 + 随机一部分 ID 推理事实（比例 ϕ 变化）。测试集包括 ID 推理事实（泛化）和 OOD 推理事实（系统泛化）。
  - **复杂推理任务**：比较任务的变体，引入对称性和传递性规则，构造需要多步搜索的 OOD 查询。训练集包含 ID 原子事实、ID-ID 比较、以及少量 ID-OOD 比较。测试集为 OOD 实体之间的可推导比较，需要利用 ID 桥接实体。
- **Benchmark**：没有标准 benchmark，论文自行构建。对比方法包括：
  - **非参数化记忆模型**：GPT-4-Turbo 和 Gemini-1.5-Pro，使用直接回答（Direct）和链式思维（CoT）提示，以及检索增强（+R）——将事实放入上下文或检索两跳邻居。
  - **参数化记忆模型**：完全 grokked 的 Transformer（同一架构但经过充分训练）。
- **对比指标**：准确率（Accuracy）。对于复杂推理任务，还报告了无提示下随机基线 33.3%（三分类）。

## 4. 资源与算力

- 论文在附录 A 中说明：所有模型训练在 NVIDIA A6000 和 A100 GPU 上进行，单次最长 96 小时。
- 未明确报告 GPU 数量、总计算量（如 FLOPs）或单次运行的具体 GPU 小时数。但提到“所有模型训练运行持续最多 96 小时”，暗示算力消耗较大（因为需要长训练步数以观察 grokking）。
- 代码和数据已开源（https://github.com/OSU-NLP-Group/GrokkedTransformer），可复现。

## 5. 实验数量与充分性

- **实验组数**：主实验覆盖多个 ϕ 值（3.6、5.4、7.2、9.0、12.6、18.0）和不同数据规模（|E| 从 2K 到 10K），并针对模型规模（8层/768维、24层/1024维、36层/1280维）、tokenization（单 token vs 多 token）、weight decay、参数共享（Universal Transformer 式）等进行了消融和鲁棒性实验。在复杂推理任务中对比了 4 种 LLM 设置（+ 直接/CoT/R/+R）。共约 15-20 组独立训练曲线（每个条件至少一次，部分有重复）。
- **充分性**：实验设计系统、控制变量严格，覆盖了核心因素（数据比例、数据规模、模型规模、正则化、架构变体）。观察到的模式（如 ϕ 与 grokking 速度正相关、数据规模无影响）稳健。但论文未报告多次随机种子的误差条（仅基于固定种子），但指出初步结果表明结果对随机性高度稳健。总体而言，实验对于支持其核心结论是充分的。
- **公平性**：对比 LLM 时，论文使用了标准提示和检索增强，尽可能公平。但 LLM 是黑盒，可能对提示形式敏感，论文未进行大规模提示调优。

## 6. 论文的主要结论与发现

- **Transformer 可以学会隐式推理，但仅通过 grokking**：在组合和比较任务中，模型都需要在训练准确率饱和后继续训练很长时间才能获得高泛化性能（ID 测试）。OOD 泛化方面，组合任务完全失败（准确率始终为 0%）；比较任务则成功实现系统泛化（OOD 准确率达到与 ID 相当的水平）。
- **数据分布（推理事实/原子事实比例 ϕ）决定泛化速度，而非数据规模**：ϕ 越高，grokking 越快；固定 ϕ 时，数据规模（|E|）增大不影响相对速度。这修正了先前基于“关键数据量”的解释。
- **机制性解释**：
  - **组合任务**：模型形成“记忆电路”（直接映射 (h,r1,r2)→t）和“泛化电路”（分离存储两跳事实，桥接实体在中间层）。由于泛化电路更高效（所需存储容量随 ϕ 增长慢），优化最终从记忆转向泛化。但泛化电路中上层只存储训练中作为第二跳出现的原子事实，因此 OOD 事实（从未作为第二跳出现）无法访问，导致系统泛化失败。
  - **比较任务**：模型形成并行电路，两个属性值在较低层并行检索，然后在上层比较并选择标签。原子事实仅存储在较低层，ID 和 OOD 事实以相同方式访问，因此能够系统泛化。
- **参数化记忆的威力**：在复杂推理任务（大搜索空间）上，GPT-4-Turbo 和 Gemini-1.5-Pro 无论直接回答、CoT 还是检索增强，准确率均低于 40%（随机基线 33.3%），且 CoT 中大多数推理路径有错误或得出“无法决定”。而完全 grokked 的 Transformer 达到 99.3% 准确率，并通过归纳推理隐式推断出了 OOD 实体的属性值。

## 7. 优点

- **创新性与洞察**：首次在知识推理场景中系统研究 grokking，并揭示数据分布（而非数据量）的决定性作用；通过机制分析区分了组合和比较任务的电路差异，解释了系统泛化能力的来源。
- **方法论严谨**：使用合成数据，完全控制事实和规则，进行干净的评价。结合 logit lens 和 causal tracing 对模型内部进行细粒度分析，提供了扎实的因果证据。
- **对比实验全面**：覆盖了多个因素（比例、规模、正则化、架构变体、tokenization），结论稳健。
- **实践启示**：提出鼓励跨层知识共享的架构改进（如参数共享），并展示了参数化记忆在复杂推理中的优势，对 LLM 未来的设计有指导意义。
- **可复现性**：开源代码和数据，附录详细描述了训练和分析细节。

## 8. 不足与局限

- **任务抽象性**：使用合成的、简化的推理任务，与现实世界中语言模型面临的自然语言推理存在差距。论文承认这一点，但认为控制性研究是必要的。
- **未涉及多跳、循环推理**：论文只研究了两种类型的推理（两跳组合和属性比较），未探索更复杂的多跳或递归推理。
- **未探索显式推理（如 CoT）对隐式推理的影响**：论文研究隐式推理本身，但指出显式 verbalization 可能有助于教模型隐式推理，这一方向未深入。
- **仅使用一种优化器（AdamW）**：未测试 SGD 或其他优化器下的 grokking 行为。
- **对 LLM 的对比实验可能不充分**：对 GPT-4-Turbo 和 Gemini-1.5-Pro 的提示工程简单，未进行系统调优，可能无法充分发挥其能力。论文也指出 LLM 的表现可能受提示影响。
- **资源计算未精确报告**：GPU 使用时间和数量细节不足，不利于完全复现。
- **缺少多次运行误差分析**：尽管认为结果稳健，但未提供标准差或置信区间，削弱了统计显著性。

（完）
