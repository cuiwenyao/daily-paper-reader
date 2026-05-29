---
title: Accelerating Large Language Model Reasoning via Speculative Search
title_zh: 通过推测搜索加速大语言模型推理
authors: "Zhihai Wang, Jie Wang, Jilai Pan, Xilin Xia, Huiling Zhen, Mingxuan Yuan, Jianye HAO, Feng Wu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=oq0t5BXilT"
tags: ["query:ns-xai"]
score: 7.0
evidence: 加速LLM中基于树搜索的推理，提升推理效率
tldr: 本文提出推测搜索框架，利用一个小模型在思维和token层面与大模型协作，高效生成高质量推理步聚，显著加速大语言模型在树搜索推理过程中的推理速度，同时保持推理质量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 829, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 836, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1682, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 802, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 73, \"height\": 70, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oq0t5bxilt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1709, \"height\": 822, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1739, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1736, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1784, \"height\": 1041, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 889, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 889, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 888, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 889, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 872, \"height\": 153, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1740, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 893, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oq0t5bxilt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 873, \"height\": 361, \"label\": \"Table\"}]"
motivation: 基于树搜索的推理方法虽然提升了推理能力，但推理时延过高。
method: 采用小模型与大模型在思维和token层面进行推测协作，优化思维生成。
result: 显著降低了推理时延，同时保持了推理质量。
conclusion: SpecSearch为高效部署推理增强方法提供了实用方案。
---

## Abstract
Tree-search-based reasoning methods have significantly enhanced the reasoning capability of large language models (LLMs) by facilitating the exploration of multiple intermediate reasoning steps, i.e., thoughts. However, these methods suffer from substantial inference latency, as they have to generate numerous reasoning thoughts, severely limiting LLM applicability. To address this challenge, we propose a novel Speculative Search (SpecSearch) framework that significantly accelerates LLM reasoning by optimizing thought generation. Specifically, SpecSearch utilizes a small model to strategically collaborate with a large model at both thought and token levels, efficiently generating high-quality reasoning thoughts. The major pillar of SpecSearch is a novel quality-preserving rejection mechanism, which effectively filters out thoughts whose quality falls below that of the large model's outputs. Moreover, we show that SpecSearch preserves comparable reasoning quality to the large model. Experiments on both the Qwen and Llama models demonstrate that SpecSearch significantly outperforms state-of-the-art approaches, achieving up to 2.12$\times$ speedup with comparable reasoning quality.

---

## 论文详细总结（自动生成）

# 论文总结：Accelerating Large Language Model Reasoning via Speculative Search

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：基于树搜索（Tree-Search-Based, TSB）的推理方法（如 ToT、Beam Search、MCTS）虽然通过探索多个中间推理步骤（thoughts）显著提升了大语言模型（LLM）的推理能力，但带来了巨大的推理延迟（latency）。推理延迟可能增加几个数量级，严重限制了 LLM 在实时应用中的部署。
- **研究动机**：论文观察到在 TSB 推理中，thought 生成占据了超过 91% 的总运行时间（图 1b），是效率瓶颈。同时，小模型能生成高质量 thought（>40% 的 thought 得分超过大模型平均水平），但简单地将低质量 thought 交给大模型修正难以保持推理质量。因此需要一种高效且质量无损的加速方法。
- **整体含义**：论文提出 Speculative Search（SpecSearch）框架，通过小模型与大模型在 thought 和 token 两个层面的推测协作，加速 thought 生成，同时通过质量保持的拒绝机制保证推理质量与使用大模型相当。理论分析和实验验证均表明该方法能够在不明显降低准确率的情况下实现显著加速。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用小模型快速生成多个候选 thought，然后由 thought 评估器（如 PRM）评估其质量，仅拒绝低于大模型质量阈值的 thought，并用大模型（通过 token 级推测解码）修正被拒绝的 thought。整个过程在 thought 级（粗粒度）和 token 级（细粒度）两个层面进行推测，实现高效协作。
- **关键技术细节**：
  - **双层推测 thought 生成器**（Bi-Level Speculative Thought Generator）：
    - **Thought 级草稿**：用小模型并行生成多个 thought。
    - **Thought 级评估**：使用过程奖励模型（PRM）为每个 thought 赋予质量分数。
    - **Thought 级拒绝**：将质量分数低于动态阈值的 thought 标记为需修正。
    - **Token 级修正**：对拒绝的 thought，用大模型（通过无损推测解码）重新生成整个 thought 进行替换。
  - **质量保持的拒绝机制**（Quality-Preserving Rejection Mechanism）：
    - 定义了大模型 thought 生成器的质量 μ_p，并设置要求生成器质量不低于 μ_p。
    - 提出基于步骤阈值的拒绝方法：在每一步设定阈值 β(k)，拒绝所有低于该阈值的 thought。
    - 阈值估计：由于大模型当前步质量未知，利用历史步骤中大模型生成的 thought 质量数据，通过非参数统计方法（如样本均值、置信上限、最大值）和指数移动平均（EMA）估计当前步的大模型质量，作为阈值。
    - 更新公式：β̂(k+1) = θ β̂(k) + (1-θ) Θ(V_p^(k))，其中 θ 是 EMA 权重，Θ 是非参数估计方法。
  - **理论保证**：论文提供定理证明，若阈值 ≥ μ_p 则生成器质量不退化；并给出在质量递减假设下，每一步保持退化解的概率下界，且该下界随草稿样本量 N 增加而趋近于 1。
- **算法流程（文字说明）**：初始化 beam，用大模型生成初始 thought 并评分；设置初始阈值；对于每个推理步骤：用小模型并行草稿多个 thought，评估质量，根据当前阈值拒绝低质量 thought，用大模型修正被拒绝的 thought（并额外生成一个），评估修正后 thought 质量，更新阈值；保留 top-k thought 进入下一步；直至达到最大深度或所有路径终止。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集**：
  - 主要评估：MATH（随机选100题）、GSM8K（随机选100题）。
  - 额外评估：完整 GSM8K（1319题）、AIME、Olympiad Bench、HumanEval（代码生成）。
- **Benchmark**：树搜索推理框架（基于 OpenR），搜索算法为 Beam Search（默认）和 MCTS，评估器为过程奖励模型（PRM），默认使用 MATH-psa，也测试 Math-Shepherd。
- **对比方法**：
  - **AR**：原始 ToT 方法，使用大模型自回归解码生成 thought。
  - **SpS**：先进的 token 级无损推测解码方法（标准推测采样），与大模型结合。
- **模型**：
  - Qwen 系列：Qwen2.5-72B-Instruct（大模型）、Qwen2.5-7B-Instruct（小模型），均 INT4 量化。
  - Llama 系列：Llama3-70B-Instruct（大模型）、Llama3-8B-Instruct（小模型），均 INT4 量化。
- **评估指标**：准确率（Accuracy）和加速比（Speedup，相对于 AR 和 SpS 的延迟比）。

## 4. 资源与算力
- 论文中未明确说明使用的 GPU 型号、数量或训练时长。仅提及实验基于量化模型（INT4），使用 vLLM 库加速，但未提供硬件的详细信息。
- 推断：由于推理任务（特别是树搜索）计算量较大，可能需要多张高端 GPU（如 A100 或 H100）运行，但论文未披露具体配置。

## 5. 实验数量与充分性
- **实验数量**：进行了多组实验，包括：
  - 主实验：在 MATH-100、GSM8K-100 上用 Qwen 和 Llama 对比 AR、SpS。
  - 泛化性实验：在 GSM8K-100 上测试不同搜索算法（Beam Search、MCTS）和不同 PRM（Math-psa、Math-Shepherd）；在 MATH-100 上也有类似实验。
  - 消融实验：在 MATH-50 上评估每个组件（评估模块、拒绝模块的变体）的贡献。
  - 敏感性分析：EMA 权重 θ（0.8~0.95）、小模型大小（7B、3B、1.5B、0.5B）。
  - 额外数据集：完整 GSM8K、AIME、Olympiad Bench、HumanEval。
- **充分性**：实验覆盖了多个数据集、两种主流 LLM 系列、两种搜索算法、多个 PRM、多种小模型尺寸，并设计了消融实验和敏感性分析。实验设计较为全面，结果展示了加速比和准确率的权衡，且与基线方法公平对比（使用相同搜索算法和设置）。不足之处在于缺少与更多近年加速方法（如 SEED）的对比（仅在相关工作中提及），且未在更大规模数据集或更长推理深度上验证。

## 6. 论文的主要结论与发现
- SpecSearch 在保持与原始大模型相当推理质量的同时，显著加速了树搜索推理过程。
  - 在 MATH-100 上使用 Qwen 模型，相对于 AR 加速 3.35×，相对于 SpS 加速 1.72×。
  - 在 GSM8K-100 上使用 Llama 模型，加速比分别为 1.99× 和 1.42×。
- 泛化性良好：与 Beam Search 和 MCTS 兼容，支持不同 PRM，适用于不同小模型。
- 消融实验表明，每个组件（thought 级评估、拒绝机制）对保持质量至关重要。简单替代（如固定阈值、随机拒绝）会导致准确率明显下降（下降 4~8 个点）。
- 理论分析提供了质量保持的条件和概率下界，支持了方法的有效性。

## 7. 优点
- **方法创新**：首次将推测执行（speculative execution）推广到树搜索推理的 thought 层面，而非仅限于 token 级。通过 bi-level 推测，同时利用 thought 结构和 token 级修正，实现高效加速。
- **质量保持**：提出基于 PRM 和动态阈值的拒绝机制，理论上保证质量不退化，实验也验证了准确率几乎不变。
- **通用性**：适用于不同 LLM 架构、搜索算法、评估器，且对小模型尺寸不敏感，易于集成到现有推理框架。
- **实验充分**：在多个数学和代码数据集上验证，进行了消融和敏感性分析，公平比较基线。
- **理论分析**：提供了概率下界定理，增加了方法的可信度。

## 8. 不足与局限
- **实验覆盖**：
  - 未与更多近期加速方法（如 SEED、TreeBon）进行直接性能对比（仅在相关工作中讨论区别）。
  - 仅在数学和代码任务上评估，未扩展到常识推理、科学问答等更广泛领域。
  - 最大推理深度仅设为 50，未测试更深搜索树或更大 beam size 下的扩展性。
- **偏差风险**：
  - 数据集样本量较小（测试集多为 100 题），可能不足以完全反映真实性能波动。
  - PRM 可能被错误 thought 误导（论文案例显示错误 step 仍获高 PRM 分），导致拒绝机制误判。
- **应用限制**：
  - 依赖高性能 PRM 作为 thought 评估器，PRM 的质量直接影响过滤效果，增加了系统复杂性。
  - 需要同时部署大小两个模型以及 PRM，对内存和计算资源有要求。
  - 方法在推理时仍需大模型介入修正低质量 thought，加速比受小模型生成质量和大模型参与比例影响，极端情况下可能退化为纯大模型推理。
- **可重复性**：未公开详细的 GPU 资源信息，复现难度增加。

（完）
