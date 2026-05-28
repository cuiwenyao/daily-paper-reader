---
title: Reviving DSP for Advanced Theorem Proving in the Era of Reasoning Models
title_zh: 复兴DSP：推理模型时代的高级定理证明方法
authors: "Chenrui Cao, Liangcheng Song, Zenan Li, Xinyi Le, Xian Zhang, HUI XUE, Fan Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=yTFJmGFsEy"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号协同用于定理证明
tldr: 自动化定理证明通常依赖大规模强化学习训练，而本文发现无需训练，通过精心设计的神经符号协同即可达到可比性能。DSP+框架在草稿、草图、证明三阶段分别增强：使用推理模型生成自然语言子目标，借助符号证明器验证，通过聚焦相关上下文和重放验证实现高效证明，在多个基准上超越许多训练方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1302, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1373, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 668, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 670, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 668, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 669, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1373, \"height\": 673, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 668, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 668, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 672, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 679, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1373, \"height\": 695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ytfjmgfsey/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1443, \"height\": 756, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 1488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 685, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1044, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1395, \"height\": 1953, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1371, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 740, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 625, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 649, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1454, \"height\": 2313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1443, \"height\": 756, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ytfjmgfsey/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1414, \"height\": 956, \"label\": \"Table\"}]"
motivation: 现有定理证明依赖大规模训练，本文探索是否可以通过神经符号协同无需训练达到可比性能。
method: 提出DSP+框架，在草稿、草图、证明阶段分别进行神经符号增强，协调推理模型与符号证明器。
result: DSP+在多个定理证明基准上实现了与大规模训练方法相当甚至更优的性能，且无需额外训练。
conclusion: 证明了精心设计的神经符号协同可以替代大规模训练，为定理证明提供了高效新方向。
---

## Abstract
Recent advancements, such as DeepSeek-Prover-V2-671B and Kimina-Prover-Preview-72B, demonstrate a prevailing trend in leveraging reinforcement learning (RL)-based large-scale training for automated theorem proving. Surprisingly, we discover that even without any training, careful neuro-symbolic coordination of existing off-the-shelf reasoning models and tactic step provers can achieve comparable performance. This paper introduces DSP+, an improved version of the Draft, Sketch, and Prove framework, featuring a fine-grained and integrated neuro-symbolic enhancement for each phase: (1) In the draft phase, we prompt reasoning models to generate concise natural-language subgoals to benefit the sketch phase, removing thinking tokens and references to human-written proofs; (2) In the sketch phase, subgoals are autoformalized with hypotheses to benefit the proving phase, and sketch lines containing syntactic errors are masked according to predefined rules; (3) In the proving phase, we tightly integrate symbolic search methods like Aesop with step provers to establish proofs for the sketch subgoals. Experimental results show that, without any additional model training or fine-tuning, DSP+ solves 80.7%, 32.8%, and 24 out of 644 problems from miniF2F, ProofNet, and PutnamBench, respectively, while requiring fewer budgets compared to state-of-the-arts. DSP+ proves imo_2019_p1, an IMO problem in miniF2F that is not solved by any prior work. Additionally, DSP+ generates proof patterns comprehensible by human experts, facilitating the identification of formalization errors; For example, eight wrongly formalized statements in miniF2F are discovered. Our results highlight the potential of classical reasoning patterns besides the RL-based training. All components will be open-sourced.

---

## 论文详细总结（自动生成）

# 论文总结：Reviving DSP for Advanced Theorem Proving in the Era of Reasoning Models

## 1. 核心问题与整体含义（研究动机和背景）

- **自动化定理证明（ATP）** 是人工智能的核心挑战之一，近期以 DeepSeek-Prover-V2 和 Kimina-Prover-Preview 为代表的工作普遍采用基于强化学习（RL）的大规模训练策略，投入大量计算资源和人工数据标注，在 miniF2F 等基准上取得了显著进展。
- **本文的核心动机**是挑战这一主流趋势：是否可以在**不进行任何额外训练或微调**的情况下，通过精心设计的神经符号协同（neuro-symbolic coordination），利用现有现成的推理模型和步骤证明器，达到可与大规模训练方法相媲美的定理证明性能？
- **研究含义**：作者发现答案是肯定的。通过复兴并大幅改进经典的 Draft, Sketch, Prove（DSP）框架，提出 DSP+，在多个权威基准上实现了与DeepSeek-Prover-V2-671B、Kimina-Prover-Preview-72B 等最新模型相当甚至更优的结果，且推理时使用的 token 更少、无需训练开销。这为定理证明领域提供了一条高效、互补的路径，表明“经典模式”的潜力被低估了。

## 2. 方法论：核心思想、关键技术细节

### 2.1 整体框架：DSP+ 三阶段神经符号增强

DSP+ 包含三个阶段，每个阶段都进行了细粒度的神经符号协调，不同于原版 DSP 的粗粒度独立设计：

1. **草稿阶段（Draft Phase）**  
   - **输入**：直接给定形式化陈述（formal statement）。  
   - **方法**：使用**推理模型**（如 QwQ-32B、DeepSeek-R1）生成证明草稿。  
   - **关键增强**：
     - 过滤掉模型内部思考 token（`<think>`...`</think>`），只保留简洁的自然语言步骤（每步一个公式，无解释）。  
     - 提示模型输出**仅包含关键公式的简洁步骤**，以避免“lost in the middle”效应。
   - **效果**：推理模型比非推理模型生成更简洁、更准确的草稿，平均答案 token 数更低但思考 token 数更高。

2. **草图阶段（Sketch Phase）**  
   - **输入**：自然语言草稿。  
   - **方法**：使用**草图模型**（如 DeepSeek-V3-0324）将草稿自动形式化（autoformalization），生成形式化语言（Lean 4）的子目标层次结构，但省略子目标的证明细节。  
   - **关键增强**：
     - **显式假设规范**：要求模型为每个子目标明确指定可能需要的支持假设，格式如 `prove_with[h1, h2]`，这有助于证明阶段聚焦于相关上下文，避免杂乱假设干扰。  
     - **错误行掩码（Error Line Masking）**：对于自动解析 Lean 代码中出现的语法错误，自动删除错误节点及其子树（可选择用 `sorry` 替换），保留尽量多的正确代码行，避免重新执行草图阶段。
   - **效果**：显式假设和错误行掩码均显著提升准确率和样本效率。

3. **证明阶段（Proving Phase）**  
   - **输入**：带有 `prove_with` 或 `sorry` 占位符的形式化草图。  
   - **方法**：紧密集成**符号搜索**（Aesop [43]）和**步骤证明器**（如 BFS-Prover [4]），自动搜索并填充每个子目标的证明。  
   - **关键增强**：
     - **内置集成**：通过 Lean Copilot 框架将步骤证明器直接嵌入 Aesop 的内部搜索逻辑，避免了传统状态到定理转换或外部解析的繁琐过程。  
     - **树搜索**：配置 beam width = 4（从 8 个采样 tactic 中选择）、树大小限制 64、每个子目标最多 8 次搜索尝试。  
     - **双重策略**：分两次尝试，一次仅使用假设提示的假设，另一次使用所有可用假设，任一成功则视为成功。
   - **效果**：符号搜索与步骤证明器的结合大幅增强了解能力，仅使用常见 tactic 时准确率大幅下降（47.5% vs 74.2%）。

### 2.2 实现细节

- **形式化语言**：Lean 4（v4.17.0-rc1），使用 Mathlib4 库。  
- **默认模型组合**：QwQ-32B（草稿）、DeepSeek-V3-0324（草图）、BFS-Prover-7B（证明）。  
- **集成设置（Ensemble）**：在默认组合基础上，使用不同模型组合（如 QwQ-QwQ-BFS、R1-V3-BFS）依次尝试，直到证明成功或超时，可累计提升准确率。  
- **模块化与效率**：提供 vLLM 服务，各阶段通过缓冲区流水线处理，支持结果复用。

## 3. 实验设计

### 3.1 基准测试（Benchmarks）

| 基准 | 规模 | 内容 |
|------|------|------|
| **miniF2F** [12] | 244 测试题 | 高中数学竞赛问题（AMC、AIME、IMO） |
| **ProofNet** [46] | 186 测试题（全 371 题） | 本科级定理证明（分析、代数、拓扑等） |
| **PutnamBench** [47] | 644 题（Lean 4 子集） | Putnam 数学竞赛题（1962–2023） |

### 3.2 对比方法

涵盖领域内所有顶级方法：

- **整体证明生成**：Goedel-Prover-7B、STP-7B、Kimina-Prover-Preview（7B/72B）、DeepSeek-Prover-V2（7B/671B）、Leanabell-Prover-7B 等。  
- **树搜索**：InternLM2.5-StepProver-7B、DeepSeek-Prover-V1.5-RL-7B + RMaxTS、HunyuanProver-7B、BFS-Prover-7B。  
- **混合方法**：原版 DSP（Minerva-540B、Isabelle）、DSP（GPT-4o、Isabelle）。  
- **闭源模型**：OpenAI o3-mini、Gemini 2.5 Pro、GPT-4o 等（部分仅在 PutmanBench 上有数据）。

### 3.3 消融实验与进一步分析

- **组件消融**：比较完整 DSP+ 与移除草稿、草图或证明组件的变体（图 3）。  
- **草稿模型对比**：QwQ-32B、DeepSeek-R1、GPT-4o、DeepSeek-V3-0324 和无草稿（图 6）。  
- **草图模型对比**：DeepSeek-V3-0324、QwQ-32B、GPT-4o、Qwen2.5-32B-Instruct（图 7）。  
- **草图优化消融**：去除错误行掩码、去除假设规范（图 5）。  
- **草稿格式对比**：是否要求简洁步骤（图 4）。  
- **人类非正式证明的影响**：是否提供人类非正式证明（图 10）。  
- **多样性分析**：不同配置对求解问题集合的互补性（表 2）。  
- **效率分析**：推理 token 消耗对比（表 3）。  
- **案例研究**：包括 Jensen 不等式应用、Putnam 实分析问题、IMO 2019 问题（附录 H、J）。  
- **错误发现**：使用 DSP+ 找出 miniF2F 中 8 个错误形式化问题（附录 F）。

## 4. 资源与算力

- **推理模型**：QwQ-32B、DeepSeek-V3-0324 等通过 Microsoft Azure AI Foundry 的 API 调用。  
- **步骤证明器**：BFS-Prover-7B 部署在 **8 × 40GB A100 GPU** 上，每个 GPU 一个模型，使用 vLLM。  
- **树搜索**：在 **96 核 CPU**（Azure 平台）上执行，每次证明搜索限制 2400 秒。  
- **总计算开销**：论文未明确给出训练时长（因为无训练），推理 token 方面：DSP+ 默认设置平均每 pass 约 12K（草稿）+ 6.3K（草图）+ 0.8K（证明）token。  
- **对比方法**：DeepSeek-Prover-V2-671B 每 pass 约 6.75K token，但需 8192 pass；Kimina-Prover-Preview-72B 每 pass 约 10K token，也需 8192 pass。因此 DSP+ 在准确率相同时总 token 消耗更低。

## 5. 实验数量与充分性

- **数量**：论文在 3 个主要基准上评测，进行了大量消融实验（组件消融、模型消融、优化策略消融、格式对比、人工证明影响等），每个实验给出不同 workflow 尝试次数（1、8、32、128、1024）下的累计通过数曲线和 pass@k 准确率。  
- **充分性**：
  - **客观性**：对比方法均采用公开报告的结果（或复现），且在同一搜索预算下比较（如 pass@1024、pass@8192 等），较为公平。  
  - **统计学显著性**：作者承认由于计算成本未提供误差条或置信区间，但通过多个 pass 和曲线图显示趋势，具有一定可靠性。  
  - **覆盖范围**：涵盖了高中数学竞赛（miniF2F）、本科数学（ProofNet）、顶尖竞赛（PutnamBench）以及 IMO 子集，领域覆盖较广。但缺少在其他证明助手（如 Coq、Isabelle）上的验证。  
  - **消融全面性**：对三个阶段的每个主要设计决策都进行了消融，包括是否使用推理模型、是否使用步骤证明器、是否使用假设规范、是否使用错误掩码等，充分揭示了各部分的贡献。

## 6. 主要结论与发现

1. **性能与 SOTA 训练模型相当**：DSP+ 在 miniF2F-test 上达到 80.7%（默认）和 83.6%（集成），与 Kimina-Prover-Preview-72B（80.7%）持平，接近 DeepSeek-Prover-V2-671B（88.9%），并超越所有其他方法，且无需任何训练。
2. **发现首次解决的 IMO 问题**：DSP+ 成功证明了 **imo_2019_p1**，这是 miniF2F 中此前没有任何方法解决的问题。
3. **发现基准形式化错误**：通过分析 DSP+ 的不一致行为，识别出 **miniF2F 中 8 个错误形式化的问题**，为社区提供了修正依据。
4. **推理效率高**：在相同准确率下，DSP+ 使用的总推理 token 远少于 Kimina-Prover-Preview（例如 4.4K + 12K vs 10K，且 pass 数少 8 倍），表明其高 token 效率。
5. **模型协同与互补性**：不同模型组合的集成设置可以覆盖更多问题，表明各模型彼此互补。
6. **方法可解释性强**：生成的证明遵循人类证明风格（层级子目标，易理解），便于人工审查和调试。
7. **神经符号协同的关键作用**：每个阶段的优化（简洁草稿、假设规范、错误掩码、树搜索集成）都带来显著提升，而移除任一环节都会导致性能大幅下降。

## 7. 优点

- **无需训练、即插即用**：不依赖 RL 训练的流程，降低了进入门槛和计算成本。  
- **模块化与灵活组合**：草稿、草图、证明模型可灵活替换，支持集成多种模型，易于适配未来更强模型。  
- **高效推理**：通过 pipeline 和缓冲机制复用结果，token 消耗远低于许多训练方法。  
- **强可解释性**：生成的证明结构化、层次化，便于人工验证和调试，还能用于发现数据集错误。  
- **广泛的 Benchmark 覆盖**：在高中数学、本科数学、竞赛数学三个难度级别上都取得竞争力的结果。  
- **严格的消融与分析**：全面评估了各设计选择的影响，结论可信度高。  
- **开源友好**：提供完整代码和结果，利于复现与扩展。

## 8. 不足与局限

- **设计空间未充分探索**：作者承认未找到最优默认配置（如草稿模型 QwQ vs R1 性能接近，但指令遵循不同），集成方案也未完全优化 token 效率与准确率的平衡。  
- **失败案例分析**：在附录 E 中列出了多类失败：草稿阶段的“创新性”不足（复杂 IMO 问题）、草图阶段的形式化困难（如对数除法、函数定义域与人类直觉不符）、证明阶段对“显然”但形式化困难的问题（如证明 π > 3.1415）。  
- **Lean 版本敏感性**：不同 Lean 版本（如 v4.9.0 vs v4.17.0）会导致某些证明失败（如 `rfl` 行为差异），增加了可迁移性挑战。  
- **步骤证明器依赖**：目前仅集成 BFS-Prover，未测试其他步骤证明器（如 InternLM2.5-StepProver），未来计划扩展。  
- **缺乏跨系统验证**：仅在 Lean 4 上实现，未在 Isabelle、Coq 等上验证，通用性待考察。  
- **未提供统计误差**：由于实验成本未报告误差条，使得部分定量比较的稳健性不够明确。  
- **对推理模型的指令遵循能力要求高**：例如 DeepSeek-R1 在草图阶段偶尔不遵循格式要求，限制了其作为草图模型的适用性。

（完）
