---
title: "Soft Reasoning: Navigating Solution Spaces in Large Language Models through Controlled Embedding Exploration"
title_zh: 软推理：通过受控嵌入探索导航大语言模型解空间
authors: "Qinglin Zhu, Runcong Zhao, Hanqi Yan, Yulan He, Yudong Chen, Lin Gui"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4gWE7CMOlH"
tags: ["query:ns-xai"]
score: 6.0
evidence: 通过嵌入搜索改进LLM推理
tldr: 大语言模型在复杂推理任务中表现不佳。本文提出Soft Reasoning框架，通过扰动首token嵌入并结合贝叶斯优化进行引导式搜索，在不依赖启发式搜索的情况下提升推理准确性和一致性。实验证明该方法计算量小、可扩展，是一种模型无关的推理增强方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1691, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1545, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 735, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 734, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 851, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 684, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4gwe7cmolh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 862, \"height\": 650, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1472, \"height\": 1035, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 847, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 823, \"height\": 416, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 864, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 863, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 844, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 849, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 852, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1767, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1770, \"height\": 1063, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4gwe7cmolh/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1767, \"height\": 955, \"label\": \"Table\"}]"
motivation: LLM在复杂推理中缺乏多样性且搜索效率低。
method: Soft Reasoning结合嵌入扰动与贝叶斯优化，优化首token嵌入引导生成。
result: 该方法提高了推理正确性，计算开销小且具可扩展性。
conclusion: Soft Reasoning是一种高效、模型无关的LLM推理增强方法。
---

## Abstract
Large Language Models (LLMs) struggle with complex reasoning due to limited diversity and inefficient search. We propose Soft Reasoning, an embedding-based search framework that optimises the embedding of the first token to guide generation. It combines (1) embedding perturbation for controlled exploration and (2) Bayesian optimisation to refine embeddings via a verifier-guided objective, balancing exploration and exploitation. This approach improves reasoning accuracy and coherence while avoiding reliance on heuristic search. Experiments demonstrate superior correctness with minimal computation, making it a scalable, model-agnostic solution.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大语言模型（LLMs）在简单推理任务上表现良好，但在复杂推理中仍面临两个关键挑战：（1）通过温度缩放提升生成多样性时，往往不加区分地放大低概率token，引入噪声而非有意义的探索；（2）现有的规划与搜索方法（如思维链、树搜索）依赖启发式策略和表面提示变化，搜索效率低且无法直接调整模型内部表征，容易陷入“随机追逐”。
- **整体含义**：需要一种更可控、更高效的解空间导航方法，在不依赖启发式搜索的前提下，直接优化模型的内在表示以引导生成，提升推理准确性与一致性。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：Soft Reasoning 是一种基于嵌入的搜索框架，通过扰动首 token 的嵌入向量并结合贝叶斯优化，在嵌入空间中引导生成过程，实现受控探索与利用。
- **关键技术细节**：
  - **嵌入扰动（Embedding Perturbation）**：对通过贪心解码生成的首 token 的嵌入向量 z，添加高斯噪声 ε ~ N(0, I)，得到扰动嵌入 x_i = z + σ ε_i。每个 x_i 被映射为特殊 token 并作为首 token，后续 token 通过贪心解码完全确定，实现从嵌入到输出的确定性映射。
  - **目标函数**：f(x) = r_verifier(y) + r_coherence(y)，其中 r_verifier 为二元正确性指示（基于验证器的最终输出），r_coherence 为基于 token 概率的连贯性得分（log 概率和），两者按自然层级关系联合优化。
  - **贝叶斯优化（Bayesian Optimisation）**：采用高斯过程作为先验，以期望改进（Expected Improvement, EI）为采集函数，根据历史观察（注入-奖励对）迭代选择下一个采样点，平衡探索与利用。使用自适应 EI 处理验证器噪声，并通过随机投影降维（低维空间 d=50）解决高维嵌入空间的维度诅咒问题。
  - **维度约简**：利用随机矩阵 A ∈ R^{D×d} 将高维问题映射到低维空间 g(u) = f(Au)，优化后再映射回原始空间。
- **算法流程**：初始化扰动嵌入 → 生成多个答案 → 验证器评估（多生成策略）→ 更新高斯过程后验 → 计算 EI → 选择下一个采样点 → 迭代直至收敛或达到最大迭代次数（实验中最多4次）。

## 3. 实验设计
- **数据集**：GSM8K（数学推理）、GSM-Hard（复杂数学）、SVAMP（数学应用题）、StrategyQA（常识推理）。针对 Qwen2-70B 额外使用 AIME-2024。
- **模型**：LLaMA3-8B-Instruct、Qwen2-7B-Instruct、Qwen2-70B-Instruct、Mistral-8B-Instruct。
- **基线方法**：CoT Prompting（零样本/少样本）、Self-Consistency 解码（温度 τ=0.4/0.6/0.8）、FIRE（首 token 温度30）、CoT-Decoding（首 token top-k 采样）、RAP（蒙特卡洛树搜索）。额外对比了可训练前缀评分器和约束微调。
- **设置**：零样本和少样本（1/2/4/8-shot）；每个配置重复5次不同随机种子；收敛阈值ϵ=0.01；最大迭代 K=4；采样数k=5。

## 4. 资源与算力
- 文中未明确说明 GPU 型号、数量或训练时长。但提到了使用 King's College London 的计算资源（CREATE 集群）。效率对比中报告了推理时间（例如 GSM8K 上 Soft Reasoning 23.15 min vs RAP 184.52 min）及内存使用（中间激活 KV cache 等）。因此缺乏具体算力配置细节。

## 5. 实验数量与充分性
- **实验数量**：全面。包括4个模型 × 4个数据集 × 零样本与少样本 × 多种基线方法，共数百组实验。此外进行了多项消融（目标函数组件、采集函数、优化 token 数量、降维维度、特殊 token 位置、验证策略）和覆盖分析、收敛性分析、神经元激活分析。
- **充分性**：较充分。覆盖了主流模型、多样任务、多维度消融，统计上报告了均值和标准差（5次重复）。但未在所有模型上进行 AIME 测试，且 Qwen2-70B 实验结果仅列于附录。对比方法中 RAP 需要分解示例，仅在少样本下比较是合理的。未公平对比部分方法的训练成本（如 Prefix Scorer 需训练）。

## 6. 主要结论与发现
- Soft Reasoning 在几乎所有任务和模型上优于所有基线，零样本平均提升 GSM8K 5%、GSM-Hard 3%。
- **覆盖分析**：正确答案的覆盖概率显著提高，如 LLaMA3-8B 零样本 GSM8K 达 91.8% vs FIRE 84.5%、CoT-Decoding 85.3%。
- **神经元激活分析**：方法增加了 MLP 层神经元激活率 3-4%，且关键脑神经（与正确性相关）激活率随迭代上升，表明系统性地找到并强化了正确推理路径。
- **效率**：与 RAP 相比，输入 token 仅消耗 6.19%，输出 token 63.28%，推理时间 14.3%，同时准确率更高。
- **消融表明**：验证器得分和连贯性项均不可或缺；EI 采集函数优于 PI 和 UCB；优化首 token 最好（多 token 优化导致性能下降）。
- **验证器比较**：多生成策略（Multi-Generate）验证准确率最高，约为 87.6% (GSM8K)，而单判断约 75.9%。

## 7. 优点
- **方法创新性**：将嵌入扰动与贝叶斯优化结合，直接操纵首 token 表征实现受控探索，避免了温度缩放的无差别性和提示依赖的搜索低效。
- **模型无关性**：无需访问模型内部参数或额外训练，可无缝集成到主流 LLM。
- **高效性**：迭代次数极少（多数问题 1-2 步收敛），计算开销远低于 RAP 等树搜索方法。
- **理论支撑**：提供了贝叶斯优化的理论保证（定理 A.1、A.2），并设计了自适应 EI 应对验证器噪声。
- **实验详尽**：包含大量消融实验、覆盖分析、神经元层面分析，深入解释了方法为何有效。

## 8. 不足与局限
- **验证器依赖**：使用同一模型作为验证器时，其反馈可能不可靠，影响优化效果。尽管设计了噪声自适应机制，但实验仅在自验证场景下测试，缺少外部强验证器的对比。
- **优化范围局限**：仅优化首 token 嵌入，扩展到多 token 时性能反而下降（表5），限制了可能的高阶搜索能力。作者也承认此局限并作为未来工作。
- **降维潜在信息损失**：随机投影至 d=50 虽稳定，但可能丢失部分方向信息；不同维度实验显示 d=50 最佳，但未对更大维度深度分析。
- **解释性不足**：嵌入扰动如何具体影响推理链尚缺乏直观解释，作者也提及可解释性为未来方向。
- **公平对比**：对于需要额外训练的基线（如前缀评分器）仅比较了无训练版本，未在同等训练条件下对比。
- **数据集覆盖**：主要评估数学和常识推理，未涉及科学、符号推理或长文本推理；模型规模方面最大 70B，未在更大模型（如 130B+）上验证。
- **实验重复性细节**：计算资源细节不充分，可能影响复现。

（完）
