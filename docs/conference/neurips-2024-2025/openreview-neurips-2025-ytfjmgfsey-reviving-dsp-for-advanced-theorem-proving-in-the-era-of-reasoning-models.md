---
title: Reviving DSP for Advanced Theorem Proving in the Era of Reasoning Models
title_zh: 在推理模型时代复兴DSP用于高级定理证明
authors: "Chenrui Cao, Liangcheng Song, Zenan Li, Xinyi Le, Xian Zhang, HUI XUE, Fan Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=yTFJmGFsEy"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号协同用于定理证明
tldr: 该论文提出DSP+框架，通过精细的神经符号增强三个阶段：用推理模型生成自然语言子目标，符号地细化草图，并集成策略步证明器。实验表明无需训练即可达到与大规模RL训练模型相当的性能，彰显了神经符号协同的强大能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1302, \"height\": 402}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1373, \"height\": 604}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 433}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 668, \"height\": 433}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 670, \"height\": 433}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 668, \"height\": 396}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 669, \"height\": 397}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1373, \"height\": 673}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 668, \"height\": 431}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 668, \"height\": 399}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 672, \"height\": 435}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 679, \"height\": 339}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1373, \"height\": 695}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1443, \"height\": 756}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 1488}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 685, \"height\": 344}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1044, \"height\": 260}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1395, \"height\": 1953}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1371, \"height\": 297}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 740, \"height\": 498}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 625, \"height\": 311}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 649, \"height\": 256}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1454, \"height\": 2313}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1443, \"height\": 756}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1414, \"height\": 956}]"
motivation: 现有定理证明依赖大规模RL训练，成本高昂。
method: 改进Draft-Sketch-Prove框架，增加分阶段神经符号增强。
result: 无训练条件下与顶尖RL训练模型性能相当。
conclusion: 神经符号协调可大幅降低定理证明的训练开销。
---

## Abstract
Recent advancements, such as DeepSeek-Prover-V2-671B and Kimina-Prover-Preview-72B, demonstrate a prevailing trend in leveraging reinforcement learning (RL)-based large-scale training for automated theorem proving. Surprisingly, we discover that even without any training, careful neuro-symbolic coordination of existing off-the-shelf reasoning models and tactic step provers can achieve comparable performance. This paper introduces DSP+, an improved version of the Draft, Sketch, and Prove framework, featuring a fine-grained and integrated neuro-symbolic enhancement for each phase: (1) In the draft phase, we prompt reasoning models to generate concise natural-language subgoals to benefit the sketch phase, removing thinking tokens and references to human-written proofs; (2) In the sketch phase, subgoals are autoformalized with hypotheses to benefit the proving phase, and sketch lines containing syntactic errors are masked according to predefined rules; (3) In the proving phase, we tightly integrate symbolic search methods like Aesop with step provers to establish proofs for the sketch subgoals. Experimental results show that, without any additional model training or fine-tuning, DSP+ solves 80.7%, 32.8%, and 24 out of 644 problems from miniF2F, ProofNet, and PutnamBench, respectively, while requiring fewer budgets compared to state-of-the-arts. DSP+ proves imo_2019_p1, an IMO problem in miniF2F that is not solved by any prior work. Additionally, DSP+ generates proof patterns comprehensible by human experts, facilitating the identification of formalization errors; For example, eight wrongly formalized statements in miniF2F are discovered. Our results highlight the potential of classical reasoning patterns besides the RL-based training. All components will be open-sourced.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：当前自动化定理证明（ATP）的主流趋势是依赖大规模强化学习（RL）训练，如 DeepSeek-Prover-V2、Kimina-Prover-Preview 等模型，需要大量计算资源和人类标注。本文探索是否可能在**不进行任何额外训练或微调**的情况下，仅通过精细协调现有的现成推理模型（如 QwQ-32B、DeepSeek-R1）和策略步证明器（如 BFS-Prover），达到与顶尖 RL 训练模型相当的性能。
- **整体含义**：研究表明传统的神经符号协同方法（如 Draft-Sketch-Prove 框架）在推理模型时代被严重低估。通过精心设计的跨阶段优化，无需大规模 RL 训练即可实现高水平定理证明，为 ATP 社区提供了一条高效、低成本的互补路径，并有助于发现并修正形式化数据集中的错误。

### 论文提出的方法论

- **核心思想**：在经典 DSP 框架基础上进行**细粒度、集成化的神经符号增强**，每个阶段都引入特定优化，且各阶段之间协同考虑（而非独立处理）。
- **关键技术细节**：
  - **起草阶段（Draft）**：使用推理模型（如 QwQ-32B、DeepSeek-R1）生成**简洁的自然语言子目标**（去除思考 token 和人类证明参考），聚焦关键公式，避免“中间丢失”问题，为后续草图阶段提供清晰输入。
  - **草图阶段（Sketch）**：将自然语言子目标**自动形式化**为 Lean 4 中的 `have` 语句层级结构，每个子目标显式标注所需的假设（如 `prove_with [h2]`）。对于语法错误的行，采用**错误行掩码**：将错误节点及其子树替换为 `sorry`，保留其他正确部分，避免重新执行整个草图阶段。
  - **证明阶段（Prove）**：紧密集成**符号搜索方法（如 Aesop）**与**策略步证明器**（如 BFS-Prover）。Aesop 进行树搜索，BFS-Prover 为每个节点生成候选策略，并利用长度归一化评分启发式；同时包含常见符号策略（linarith, simp 等）。每个子目标的证明预算拆分为仅使用提示假设和使用全部假设两种尝试。
- **算法流程**：形式化语句 → 起草模型（推理模型）生成简洁草案 → 草图模型（如 DeepSeek-V3）生成带假设标注的草图 → 错误掩码 → 对每个 `prove_with` 或 `sorry` 子目标，使用 Aesop+BFS-Prover 联合搜索证明 → 所有子目标完成后验证整体证明。支持多次尝试（pass@k）和集成设置（不同模型组合）。

### 实验设计

- **数据集 / 场景**：
  - **miniF2F**：244 个测试问题（高中竞赛数学，含 AMC、AIME、IMO）。用于主要精度对比和消融。
  - **ProofNet**：186 个测试问题（本科数学分析、代数、拓扑）。
  - **PutnamBench**：644 个 Lean 4 问题（Putnam 竞赛）。
  - 额外使用 **ProverBench**（新基准，减轻数据污染风险）。
- **基准（Benchmark）**：通过与 DeepSeek-Prover-V2、Kimina-Prover-Preview、BFS-Prover、Goedel-Prover、STP、InternLM2.5-StepProver 等进行对比。
- **对比方法**：包括整证明生成（Goedel-Prover、STP、Kimina-Prover、DeepSeek-Prover-V2）和树搜索方法（InternLM2.5-StepProver、BFS-Prover 等）。对比指标为 pass@k 精度和推理 token 数。
- **默认设置**：起草模型=QwQ-32B（温度0.6, top-p 0.95, max_tokens 32,768），草图模型=DeepSeek-V3-0324（温度0.7），证明模型=BFS-Prover-7B（温度1.1, max_tokens 64, n=8）。树搜索参数：束宽4，树大小限制64，每个子目标最多8次尝试，超时2400秒。工作流尝试次数通常为128或1024。
- **消融实验**：成分消融（移除起草原、草图、证明中的某些组件）、格式消融（简洁 vs 无格式）、草图优化消融（假设标注 vs 无标注；错误掩码 vs 无掩码）、不同起草/草图模型对比、有无人类证明影响、不同证明模型（仅符号策略 vs 带证明器）。这些实验覆盖 miniF2F-test，图/表展示随工作流尝试次数的变化曲线。

### 资源与算力

- **BFS-Prover-7B**：部署在 **8×40GB A100 GPU** 上，每 GPU 一个模型实例，使用 vLLM。未明确给出训练/推理的总 GPU 小时数，仅说明推理过程中每个子目标平均采样约1500次/尝试。
- **其他模型**（QwQ-32B、DeepSeek-V3、DeepSeek-R1、GPT-4o 等）：通过 **Microsoft Azure AI Foundry API** 调用，未详细说明具体算力分配。
- 树搜索在 **96 核 CPU** 上运行（Azure 云）。
- **未提及**任何模型训练所需的算力（因本文无训练）。

### 实验数量与充分性

- **主要实验**：在 miniF2F-test 上进行了 6 种不同模型组合的集成实验（表2），每种组合覆盖 pass@1024 或 pass@128。核心结果（表1）列出多个方法的精度。额外在 ProofNet、PutnamBench 上报告精度。
- **消融实验**：至少 6 组（图3、4、5、6、7、10），每组包含多条曲线，验证不同组件、格式、模型的影响。
- **公平性**：所有对比方法采用公开的最佳结果，且注明样本预算（pass@k）和推理 token 统计（表3）。DSP+ 在相等或更低预算下与前沿模型相比。但未报告统计显著性（如误差条）因计算成本过高。
- **充分性**：实验覆盖多个基准、多种配置、消融全面，结果一致支持结论。但未在更多领域（如计算机科学证明、电路验证）测试，存在泛化局限。

### 论文的主要结论与发现

- DSP+ 在**无需任何额外训练**的情况下，于 miniF2F-test 达到 80.7% 精度（使用 DeepSeek-R1 起草），与 Kimina-Prover-Preview-72B（80.7% @ 8192 次）并列，且消耗更少推理 token（4.4k+12k vs 10k×8192）。集成设置可达 83.6%，接近 DeepSeek-Prover-V2-671B（88.9%）。
- DSP+ 成功证明 **imo_2019_p1**，这是所有先前方法均未解决的问题。
- 通过分析 DSP+ 的证明过程，发现了 **8 个 miniF2F 形式化错误**（如对数定义域不一致），展示了方法在数据集质量控制方面的辅助价值。
- 核心结论：**神经符号协调比大规模 RL 训练更具 token 效率和可解释性**，是传统 ATP 路线在推理模型时代的复兴。

### 优点

- **高效低资源**：完全利用现成模型，无需训练或微调，推理 token 数远低于 RL 训练模型，特别适合资源受限场景。
- **可解释性强**：生成具有人类可理解的 `have` 语句层级的证明，便于复查和发现形式化错误。
- **模块化与灵活性**：各阶段模型可独立替换，支持集成多种模型组合，易于集成新模型或新策略。
- **鲁棒性**：对起草模型、草图模型、不同格式均有较好适应性（消融显示多种配置有效）。
- **发现数据集错误**：自动识别形式化错误，对数据集质量提升有贡献。

### 不足与局限

- **设计空间未充分探索**：默认配置并非最优，且集成设置中模型组合的选择基于早期试验，缺乏系统化优化。存在进一步调优空间（如搜索预算分配、模型组合策略）。
- **失败案例**：起草阶段可能产生不正确的直觉（如 IMO 难题），草图阶段难以处理需要函数图形、除法定义域等复杂形式化，证明阶段对某些“显然但难形式化”的陈述（如 π > 3.1415）处理困难。Lean 版本差异也影响结果。
- **实验覆盖有限**：仅在数学竞赛和本科数学基准上验证，未扩展到**计算机科学、电路验证、并发程序验证**等更广泛的 ATP 应用领域。存在过拟合风险。
- **未报告统计显著性**：因计算成本过高，无法提供误差条或置信区间，结果可能受随机性和超参数影响。
- **依赖特定推理模型**：性能高度依赖推理模型的质量（如 QwQ-32B、DeepSeek-R1），若这些模型被更新或禁用，方法可能失效。同时，推理模型的“思考 token”增加了推理成本（尽管仍低于 RL 训练模型）。
- **可扩展性**：当前框架需要针对每个问题执行多次工作流尝试，对于大规模问题集（如 PutnamBench 的 644 题）可能需要大量计算时间（文中未明确总运行时间）。

（完）
