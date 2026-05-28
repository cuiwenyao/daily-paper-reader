---
title: "Two Experts Are All You Need for Steering Thinking: Reinforcing Cognitive Effort in MoE Reasoning Models Without Additional Training"
title_zh: 只需两位专家：无需额外训练即可引导MoE推理模型的认知努力
authors: "Mengru Wang, Xingyu Chen, Yue Wang, Zhiwei He, Jiahao Xu, Tian Liang, Qiuzhi Liu, Yunzhi Yao, Wenxuan Wang, Ruotian Ma, Haitao Mi, Ningyu Zhang, Zhaopeng Tu, Xiaolong Li, Dong Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=x7fCiuCCAu"
tags: ["query:ns-xai"]
score: 6.0
evidence: 提升MoE大模型推理深度与效率
tldr: 针对MoE推理模型普遍存在的过思考和欠思考问题，本文提出RICE方法，在推理阶段通过nPMI识别认知专家并引导模型调用合适专家，从而在不增加训练的情况下提升推理深度与效率。实验表明该方法有效缓解了认知低效问题，为大型推理模型的高效推理提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-x7fciuccau/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1301, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x7fciuccau/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 724, \"height\": 491, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1096, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1078, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1003, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1278, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1036, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 659, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 741, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 997, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1192, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 907, \"height\": 655, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1203, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1030, \"height\": 337, \"label\": \"Table\"}]"
motivation: 现有MoE推理模型存在认知低效（过思考和欠思考）问题，制约了推理质量。
method: 提出RICE，基于nPMI识别认知专家，在推理时动态引导模型调用特定专家。
result: 在多个推理基准上显著提升推理深度与效率，同时降低认知浪费。
conclusion: RICE是一种轻量级、无需训练的推理增强方法，适用于MoE结构的大模型。
---

## Abstract
Mixture-of-Experts (MoE) architectures within Large Reasoning Models (LRMs) have achieved impressive reasoning capabilities by selectively activating experts to facilitate structured cognitive processes. Despite notable advances, existing reasoning models often suffer from cognitive inefficiencies like overthinking and underthinking. To address these limitations, we introduce a novel inference-time steering methodology called Reinforcing Cognitive Experts (RICE), designed to improve reasoning depth and efficiency without additional training or complex heuristics. Leveraging normalized Pointwise Mutual Information (nPMI), we systematically identify specialized experts, termed cognitive experts that orchestrate meta-level reasoning operations characterized by tokens like <think>. Empirical evaluations with leading MoE-based LRMs (DeepSeek-R1 and Qwen3-235B) on rigorous quantitative and scientific reasoning benchmarks (AIME and GPQA Diamond) demonstrate noticeable and consistent improvements in reasoning accuracy, cognitive efficiency, and cross-domain generalization. Crucially, our lightweight approach substantially outperforms prevalent reasoning-steering techniques, such as prompt design and decoding constraints, while preserving the model's general instruction-following skills. These results highlight reinforcing cognitive experts as a promising, practical, and interpretable direction to enhance cognitive efficiency within advanced reasoning models.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将根据提供的论文内容，按照您的要求生成结构化、深入、客观的中文总结。

---

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：基于 MoE（混合专家）架构的大型推理模型（LRM），如 DeepSeek-R1 和 Qwen3-235B，虽然通过稀疏激活专家展现出卓越的推理能力，但仍普遍存在**认知低效**问题，主要表现为**“过度思考”**（overthinking，生成过多无关或重复的推理步骤）和**“欠思考”**（underthinking，推理浅尝辄止，过早给出答案）。现有解决方案（如偏好优化、解码惩罚）通常需要额外训练或复杂启发式规则。
- **整体含义**：本文提出一种新颖的**推理时引导方法**——**RICE**（Reinforcing Cognitive Experts），旨在不进行额外训练的情况下，通过识别并强化 MoE 模型中与推理过程高度相关的“认知专家”，来提升推理的深度与效率。这种方法为理解和控制 MoE 模型的内部认知机制提供了新视角。

#### 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：利用**归一化点互信息（nPMI）** 量化每个专家（Expert）的激活与特定“思考标记”（如 `<think>` 等）之间的共现强度。那些与思考标记高度共现的专家被认为是“认知专家”，负责元层面的推理操作。在推理时，通过放大这些认知专家的输出权重，可以增强模型的推理能力。
- **关键技术细节**：
    1.  **识别认知专家**：
        - 定义一组思考标记集合 Π = {`<think>`， `</think>`， `Alternatively`}。
        - 对于每个专家 $E_i$，计算其综合 nPMI 得分：$nPMI_{E_i} = c_{<think>} \cdot nPMI(<think>, E_i) + c_{</think>} \cdot nPMI(</think>, E_i) + c_{Alternatively} \cdot nPMI(Alternatively, E_i)$。其中 $c_{<think>} = 1$， $c_{</think>} = -1$， $c_{Alternatively} = -1$，这样设计是为了优先选择**启动**而非**终止**或**切换**推理的专家。
        - 选择得分最高的 $l$ 个专家构成认知专家集 $P$。
    2.  **推理时引导（Steering）**：
        - 在模型前向传播过程中，当门控函数为某个 token 选中的专家子集 $S$ 中的专家 $E_i$ 属于认知专家集 $P$ 时，将其原始权重 $w_i$ 乘以一个引导乘数 `β`（steering multiplier），即 $w_i = w_i \cdot \beta$。对于 $S$ 中不属于 $P$ 的专家，权重保持不变。
- **算法流程（文字描述）**：
    1.  用一个小的数据集（如 AIME24）进行一次前向传播，记录每个 token 选中的专家。
    2.  基于公式 (4) 和 (5) 计算每个专家与思考标记（如 `<think>`）的 nPMI 值。
    3.  根据公式 (6) 计算每个专家的综合 nPMI 得分，并排序，选取 top-l 专家作为认知专家。
    4.  在后续推理任务中，当模型推理时，识别被门控选中的专家是否在认知专家集中，并将这些专家的权重乘以 `β`（或不进行权重归一化，直接放大）。

#### 3. 实验设计：数据集、基准与对比方法
- **数据集与基准**：
    - **数学推理**：AIME 2024 和 AIME 2025（美国数学邀请赛，高难度）。
    - **跨领域科学推理**：GPQA Diamond（包含物理、化学、生物学问题）。
    - **通用指令遵循能力**：ArenaHard（500个挑战性用户查询的子集）。
- **核心对比方法（基线）**：
    - **自身基线**：未做任何干预的原始模型（Vanilla DeepSeek-R1 / Qwen3-235B）。
    - **Prompt 工程**：在 `<think>` token 之前或之后添加引导性提示词。
    - **解码约束**：惩罚`</think>`标记（名为 TIP_t），以防止模型过早停止思考。
    - **随机专家**：随机选择两个专家进行增强，作为对照消融。

#### 4. 资源与算力
- 论文明确指出，**DeepSeek-R1 (671B) 的实验在 16 块 NVIDIA H20 GPU 上**进行，使用的推理引擎为 `vllm==0.7.0`。
- **Qwen3-235B-A22B 的实验**使用了更新的 `vllm==0.8.5`。
- **无额外训练**：本文方法的核心优势在于无需训练，专家识别仅需一次前向传播，因此算力消耗主要集中在推理阶段，而非训练阶段。论文未提及具体推理时长，但强调其“轻量级”特性。

#### 5. 实验数量与充分性
- **实验数量**：较为充分。主要包括：
    -   **性能验证**：在 AIME24/25 和 GPQA 四个子域上，报告了 DeepSeek-R1 和 Qwen3-235B 的准确率和 token 数（表4、5、7、12、13）。
    -   **消融研究**：探讨了认知专家数量（Top1-5）和引导乘数 β（2-512）的影响（表3）。
    -   **跨域迁移**：将在 Math、Physics、Chemistry、Biology 等不同领域识别的专家互相测试其在其他领域的泛化能力（表5）。
    -   **通用能力影响**：在 ArenaHard 上测试增强专家对指令遵循能力的影响（表6）。
    -   **与其他方法对比**：与 prompt 和解码约束方法在 AIME 基准上对比（表7）。
    -   **Pass@k 实验**：评估在采样策略下的性能（表11）。
- **充分性与公平性**：
    -   **充分**：实验设计覆盖了性能、效率、泛化性和副作用等多个维度，验证了方法的核心主张。包含了随机基线和多种超参数设置，消融分析较为透彻。
    -   **客观公平**：使用了公开的、高难度基准测试（AIME, GPQA），并且与主流的推理增强方法（prompt, decoding constraints）进行了直接对比，结论具有说服力。论文也诚实地报告了某些领域（如物理）性能略有下降的情况。
    -   **局限**：实验仅基于两种 MoE 模型（DeepSeek-R1, Qwen3-235B），未来需要更多架构的验证。此外，实验未报告多次重复运行的误差棒，结果的统计显著性有待进一步确认。

#### 6. 论文的主要结论与发现
1.  **存在认知专家**：MoE 模型中确实存在与思考标记（如 `<think>`）高度相关的“认知专家”。不同科学领域的认知专家既有共享部分，也有特有部分，表明模型存在通用和专用的推理模块。
2.  **仅增强两个认知专家即可显著提升推理性能**：在 AIME24 上，通过增强排名前 2 的认知专家，并将引导乘数 β 设为 4、32、64 或 128，DeepSeek-R1 的准确率从 73.3% 提升至 83.3%，同时减少了平均思考步数和 token 消耗，提高了推理效率。
3.  **强大的跨域泛化能力**：从数学领域识别的认知专家能有效提升物理、化学等不同领域的推理准确率，表现出良好的可迁移性。
4.  **无有害副作用**：增强认知专家不仅没有损害模型的通用指令遵循能力（ArenaHard 得分保持甚至略升），还可能通过“更深入的思考”带来积极影响。
5.  **优于现有方法**：RICE 方法在 AIME 基准上平均准确率（78.7%）显著优于 Prompt 工程（75.0%）和解码约束（76.7%）等现有推理引导技术。

#### 7. 优点：方法与实验设计的亮点
-   **方法亮点**：
    -   **轻量级与零训练**：仅需一次前向传播识别专家，推理时仅修改权重，计算开销极低，易于部署。
    -   **可解释性强**：识别出的认知专家具有明确的语义关联（与思考标记共现），使模型的推理过程更加透明。
    -   **高效聚焦**：不仅提升准确率，还能减少 token 使用，实现“思考更少、更好”的目标。
    -   **即插即用**：适用于现有的 MoE 推理模型，无需修改模型结构或重新训练。
-   **实验设计亮点**：
    -   **多维评估**：不仅关注最终准确率，还深度分析了推理效率（Tokens, Thought数）和跨域泛化能力。
    -   **充分消融**：通过调整专家数量和引导强度，揭示了方法的鲁棒性和最佳配置，同时使用随机专家作为基线，证明了方法的有效性非偶然。
    -   **副作用验证**：特意评估了增强认知专家对通用任务（ArenaHard）的影响，体现了严谨性。

#### 8. 不足与局限
-   **模型架构局限性**：验证仅局限于 DeepSeek-R1 和 Qwen3-235B 两种 MoE 模型，结论是否适用于其他 MoE 架构（如 OLMoE、Llama 4 MoE）或其他非 MoE 的推理模型尚不明确。
-   **识别方法局限性**：nPMI 方法可能无法完全捕捉所有复杂的推理交互，例如那些不直接通过特定标记词表达的专家协同行为。可能存在更精妙的识别指标。
-   **超参数敏感性**：引导乘数 β 和选中的专家数量 l 需要手动调整。虽然论文指出 β 在一定范围内（如 4-128）表现稳健，但在更大或更小的值时性能会急剧下降，表明其存在一个“最佳区间”。
-   **实验鲁棒性报告不足**：论文未报告多次实验结果的标准差或置信区间，无法评估结果的统计可靠性。
-   **缺乏更广泛任务覆盖**：主要聚焦于数学和科学推理，其在代码生成、逻辑推理、常识问答等任务上的表现尚待探索。

（完）
