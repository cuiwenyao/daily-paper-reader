---
title: Concept Attractors in LLMs and their Applications
title_zh: 大语言模型中的概念吸引子及其应用
authors: "Sotirios Panagiotis Chytas, Vikas Singh"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=ZqwyrPXbV9"
tags: ["query:ns-xai"]
score: 5.0
evidence: 通过概念吸引子实现大模型可解释性的免训练方法
tldr: 大语言模型的内部表示通常难以解释。本文发现层间映射可概括为概念吸引子，并基于此开发免训练方法，直接操作吸引子实现语言翻译、幻觉减少等功能。方法在多个任务上匹配甚至超越专门基线，为理解大模型内部运作和提升可解释性提供了高效工具。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 727, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 577, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 828, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 510, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1313, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 445, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 272, \"height\": 287, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zqwyrpxbv9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 642, \"height\": 505, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zqwyrpxbv9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1152, \"height\": 296, \"label\": \"Table\"}]"
motivation: 大模型内部表示难以解释，且现有干预需大量微调。
method: 基于迭代函数系统理论，将层间映射视为向概念吸引子的收缩，设计免训练干预方法。
result: 吸引子干预在翻译、幻觉减少等任务上达到或超越专门基线。
conclusion: 概念吸引子为理解和调控大模型行为提供了简洁且可解释的框架。
---

## Abstract
Large language models (LLMs) often map semantically related prompts to similar internal representations at specific layers, even when their surface forms differ widely. We show that this behavior can be generalized and explained through Iterated Function Systems (IFS), where layers act as contractive mappings toward concept-specific Attractors. We leverage this insight and develop simple, training-free methods that operate directly on these attractors to solve a wide range of practical tasks, including **language translation**, **hallucination reduction**, **guardrailing**, and **synthetic data generation**. Despite their simplicity, these attractor-based interventions match or exceed specialized baselines, offering an efficient alternative to heavy fine-tuning, generalizable in scenarios where baselines underperform.

---

## 论文详细总结（自动生成）

# 论文深度分析：Concept Attractors in LLMs and their Applications

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）内部表示高度复杂且难以解释。现有方法试图通过微调、有监督学习等方式干预模型行为，但计算成本高且需要大量标注数据。同时，已有现象表明语义相近的提示词（prompts）会在模型特定层收敛到相近的隐表示，这种“语义坍缩”缺乏统一的理论解释。
- **整体含义**：论文提出将 LLM 的层层映射过程视为**迭代函数系统（Iterated Function Systems, IFS）**，每一层相当于一个收缩映射，最终将输入推向某个**概念特定的吸引子（Attractor）**。这一视角不仅为坍缩现象提供了数学框架，还引出了**轻量、免训练**的干预方法，可应用于机器遗忘、毒性减少、代码翻译、幻觉抑制和合成数据生成等多个下游任务。
- **背景**：已有文献证实 transformer 模型中存在表示坍缩（belief states、task vectors、fractal structures），但缺乏统一建模。论文试图用 IFS 整合并推广这些发现。

## 2. 论文提出的方法论：核心思想、关键技术、公式或算法流程

### 核心思想
- LLM 的前向传播过程（从输入层到某个中间层）可以用一个 IFS 近似：`HL(p) = F(HL-1(p))`，其中 `F` 是若干收缩映射的 Hutchinson 算子。
- 对于特定概念 C，经过足够多层后，所有相关 prompt 的表示收敛到一个紧致不变集——**概念吸引子 A_C**。
- 实际操作中，用单个仿射映射 `φ_eff(V) = M_eff V + t_eff` 来近似整个复合变换，并最小化预测隐藏状态与实际隐藏状态之间的差异（公式 3）。

### 关键技术细节
- **吸引子估计**：对属于某概念的 N 个样本，取其在指定层（如 layer 24）的隐藏激活向量，计算平均值作为吸引子向量 `a_C`。
- **检测（Guardrailing）**：对于新输入，计算其在该层的表示与 `a_C` 的余弦相似度，若超过阈值 τ 则判定属于该概念，冻结输出。
- **导向（Steering）**：在生成过程中，向隐藏状态添加或减去目标吸引子向量（例如减去毒性吸引子以减少毒性；加上目标语言吸引子实现代码翻译）。
- **幻觉抑制**：在视觉语言模型中，每步生成时动态保持对初始视觉吸引子的关注（将第一时步的视觉吸引子向量加到后续 hidden state 上）。
- **数据生成**：对同一样本使用不同指令得到的表示会收敛到同一个样本吸引子；通过对该吸引子添加小扰动，可生成多样化样本，避免使用高温度采样导致的质量下降。

### 算法流程（文字说明）
1. **离线阶段**：选择目标概念，收集少量样本（例如 5-10 个 prompt），通过单次前向传播获取这些样本在特定层（需预先分析确定）的隐藏激活，取均值得到概念吸引子向量 `a_C`。
2. **在线干预**：
   - 检测：对每个新 prompt，提取同一层激活，计算与 `a_C` 余弦相似度 > τ → 标记为概念相关。
   - 导向：在生成时，在指定层逐 token 加上或减去 `λ * a_diff`，其中 `a_diff` 可以是目标吸引子与当前吸引子的差。
3. **无需训练**：整个过程不涉及梯度更新或模型参数修改。

## 3. 实验设计：数据集、场景与对比方法

| 场景 | 数据集 / 基准 | 对比方法 |
|------|--------------|----------|
| **概念检测/机器遗忘** | TOFU（forget05, forget10） | Gradient Ascent, NPO, ECO |
| **毒性减少** | ParaDetox | ICV, LoRA fine-tuning, In-context Learning |
| **代码翻译（transpiling）** | LeetCode 100 题（Python, Java, C++, JavaScript） | Difference of Means (DM), ICV, RFM, LR |
| **幻觉抑制（VLM）** | CHAIR, POPE on Llava-1.5, InstructBLIP | 其他免训练方法（未列出具体名称，但强调不增加推理时间） |
| **合成数据生成** | BoolQ, AG News；事实性评估用真人/历史人物 | 温度采样（Temperature sampling） |
| **吸引子定性分析** | 虚构世界（Harry Potter, LOTR, Narnia, Star Wars） | 无定量对比，仅用于可视化 |

**评估指标**：Rouge、Toxicity（Detoxify）、模型效用（Utility）、Cutoff 率、o4-judge 评分、CHAIR、POPE、下游模型测试精度等。

## 4. 资源与算力

- 论文明确提到“由于计算限制，我们只在最多 8B 参数的模型上评估”（Llama3.1-8B, Llava-1.5-7B, InstructBLIP-7B等）。
- **未明确说明**使用的具体 GPU 型号、数量、训练时长。由于方法免训练，主要算力消耗为前向传播获取吸引子估计（每个概念只需几次前向）以及干预时的少量额外计算（每步加向量）。作者宣称计算效率高，但未定量报告。
- 建议读者自行估算：Llama3.1-8B 在单张 A100 上推理约需 10-15 GB 显存，单次前向约数百毫秒。

## 5. 实验数量与充分性

- **实验数量**：涵盖 **6 个主要场景**，每个场景有定量结果，部分场景有消融（如 TOFU 中 τ 的调节，毒性中不同融合方式）。代码翻译覆盖 4 种语言的全部方向（4×3=12 对）。合成数据生成用了两个不同规模的下游模型（0.5B, 1.3B）。总体实验量适中。
- **充分性分析**：
  - **优点**：覆盖多个关键应用领域，基线选择较新（NPO, ECO 等 2024 年方法）；用 o4-judge 作为自动评估增加可重复性。
  - **不足**：
    - 仅在 **8B 尺度**模型验证，未测试 13B/70B 或更大的模型。
    - 代码翻译只使用 LeetCode 题目，泛化性未知。
    - 幻觉抑制仅针对 VLM，未对纯 LLM 的语义幻觉做实验。
    - 消融实验较少（如未分析吸引子估计所需样本数的影响，不同层选择的影响）。
    - 对比方法均为免训练或轻量方法，没有与重量级微调方法（如全参数微调）对比（这部分可能不公平，因为论文主打的免训练优势，但应提及适用边界）。
  - **公平性**：对比方法设置合理，评价指标标准，但部分场景下基线选择偏少（如 VLM 幻觉抑制未列具体对比方法名称，仅说“不增加推理时间”）。

## 6. 论文的主要结论与发现

1. **假设成立**：LLM 内部确实存在概念特定的吸引子，且不同概念在**不同层**收敛（如虚构世界在 layer 24，编程语言在 layer 19，自然语言在 layer 27）。
2. **吸引子具有语义意义**：投影到词汇空间后，诱导出的 top tokens 反映概念的本质（包括额外关联如货币符号、拍摄地点等）。
3. **免训练干预有效**：简单的加/减吸引子向量或阈值检测，在多个任务上匹配甚至超越需要训练的基线方法，实现效率与性能的双赢。
4. **迁移适用性**：同一个 IFS 视角可以统一解决看起来不相关的下游问题，证明该框架的通用性。
5. **揭示模型内部结构**：吸引子呈现出**分形结构**（如算术任务中按位数、运算类型聚类），进一步支持 IFS 理论的适用性。

## 7. 优点

- **方法极简**：无需任何训练、无需反向传播、无需保留数据（多种场景），只需一次前向获得吸引子估计。
- **计算高效**：与需要微调的方法相比，几乎零额外成本；与需要多次前向的免训练方法（如对比解码）相比，不增加推理时间（幻觉抑制中每步仅加一个向量）。
- **统一框架**：用单一理论（IFS）解释多个现象，并有效指导工程应用。
- **可解释性**：通过吸引子投影到词汇空间，直观理解模型判断依据。
- **灵活可控**：通过阈值 τ 或缩放因子 λ 可自由调节干预强度，提供精确的 trade-off 控制（例如遗忘与模型效用的平衡）。
- **适用性广**：涵盖安全（guardrailing）、风格控制（毒性减少）、跨语言跨模态（代码翻译、幻觉抑制）、数据增强等关键需求。

## 8. 不足与局限

- **硬件依赖**：需要直接访问模型中间层的隐藏激活，无法通过标准 API（黑盒）实现，限制了在闭源模型上的应用。
- **模型尺度限制**：只在 ≤8B 参数模型上验证，更大模型（如 Llama3.1-70B）的吸引子行为可能不同或需要更复杂的 IFS 建模。
- **概念定义依赖数据**：吸引子估计需要少量但代表性的概念数据，对于稀疏或模糊的概念可能效果不佳。
- **单映射近似可能不够**：当概念内部结构复杂（如存在多个子概念、分形结构）时，单一仿射映射可能无法准确描述，需要多映射 IFS 但论文未深入探索。
- **缺乏对概念层选择的理论指导**：不同概念的最佳操作层不同，需要通过启发式搜索确定，不够自动化。
- **实验覆盖有限**：未测试逻辑推理、长上下文场景；未讨论对模型其他能力（如事实性、安全性）的潜在负面影响；未进行大规模多任务消融。
- **比较范围局限**：代码翻译和毒性减少中仅与轻量基线对比；幻觉抑制中未与 VCD、OPERA 等流行免训练方法显式对比数值（仅提及不增加推理时间），削弱了说服力。
- **可重复性细节不足**：未公开代码和详细超参数设置（论文说代码已提供，但审稿阶段不确定；NeurIPS 2025 版本未附代码链接）。

（完）
