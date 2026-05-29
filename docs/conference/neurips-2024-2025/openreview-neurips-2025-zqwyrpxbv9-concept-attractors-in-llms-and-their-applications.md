---
title: Concept Attractors in LLMs and their Applications
title_zh: LLM中的概念吸引子及其应用
authors: "Sotirios Panagiotis Chytas, Vikas Singh"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=ZqwyrPXbV9"
tags: ["query:ns-xai"]
score: 8.0
evidence: 概念吸引子解释LLM内部并支持实际应用
tldr: LLM内部表示与概念的关系尚待阐明。本文证明层可视为压缩映射，将不同表面形式的相似语义收敛到概念吸引子。基于此提出无需训练的方法，直接操作吸引子实现翻译、幻觉减少、护栏和合成数据生成，效果媲美专用基线。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 727, \"height\": 429}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 577, \"height\": 569}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 828, \"height\": 216}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 215}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 259}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 359}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 228}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 510, \"height\": 404}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1313, \"height\": 283}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 449}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 445, \"height\": 277}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zqwyrpxbv9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 272, \"height\": 287}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zqwyrpxbv9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 642, \"height\": 505}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zqwyrpxbv9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1152, \"height\": 296}]"
motivation: LLM语义相关的内部表示聚类现象缺乏统一解释。
method: 提出概念吸引子理论，将层视为压缩映射，并开发基于吸引子的无需训练干预方法。
result: 在翻译、幻觉减少等任务上，吸引子方法达到或超越专用基线。
conclusion: 概念吸引子为理解LLM内部表示和设计轻量干预提供了新框架。
---

## Abstract
Large language models (LLMs) often map semantically related prompts to similar internal representations at specific layers, even when their surface forms differ widely. We show that this behavior can be generalized and explained through Iterated Function Systems (IFS), where layers act as contractive mappings toward concept-specific Attractors. We leverage this insight and develop simple, training-free methods that operate directly on these attractors to solve a wide range of practical tasks, including **language translation**, **hallucination reduction**, **guardrailing**, and **synthetic data generation**. Despite their simplicity, these attractor-based interventions match or exceed specialized baselines, offering an efficient alternative to heavy fine-tuning, generalizable in scenarios where baselines underperform.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：大型语言模型（LLM）中，语义相关的提示（prompt）即使表面形式差异巨大，其内部表示在特定层也会收敛到相似区域。这一现象缺乏统一的理论解释，且现有工作多局限于小模型或特定场景。
- **整体含义**：论文将该现象推广为**概念吸引子（Concept Attractors）** 理论，将LLM的层视为迭代函数系统（Iterated Function Systems, IFS）中的压缩映射，语义相似的输入被映射到概念特定的吸引子集。基于这一视角，作者提出了**无需训练、直接操作吸引子**的轻量方法，可解决翻译、幻觉减少、护栏（guardrailing）、合成数据生成等多种实际任务，效果媲美甚至超越需要大量微调或保留数据的专用基线。

## 2. 方法论

- **核心思想**：LLM的前向传播过程可被建模为一个IFS。对于每个概念C，存在一个层 \(l_C\)，在该层提示的表示高度聚集，形成概念吸引子 \(A^C_l\)。该吸引子是一个压缩映射的不变集。
- **关键技术细节**：
  - **吸引子估计**：对属于某概念的一组提示，取其在特定层的隐藏表示向量的平均值作为该概念吸引子的估计（概念向量）。
  - **Collage定理近似**：将LLM对某概念的整体变换近似为单张仿射压缩映射 \(\phi_{\text{eff}}(V) = M_{\text{eff}}V + t_{\text{eff}}\)，通过最小化预测状态与LLM真实状态的距离来求解参数，且要求矩阵是压缩的（算子范数<1）。
  - **干预方法**：
    - **概念检测/护栏**：计算生成过程中当前表示与存储的吸引子的余弦相似度，若超过阈值 \(\tau\) 则拦截输出。
    - **遍历（steering）**：在目标层将当前隐藏状态加上或减去目标吸引子向量，引导生成朝向/远离该概念。
    - **视觉吸引子保持**：在视觉-语言模型中，每个生成步添加初始视觉吸引子以缓解幻觉。
    - **数据生成**：通过扰动样本对应吸引子的估计值，产生多样化的合成样本，替代需要多提示或高温度的采样。
- **算法流程**（以护栏为例）：
    1. 获取需遗忘概念的一组提示，在层 \(l_C\) 收集隐藏表示，平均得到吸引子向量。
    2. 推理时，对每个生成输出，计算其同一层表示与吸引子向量的余弦相似度。
    3. 若相似度 > \(\tau\)，则拦截输出并替换为预设拒绝消息。

## 3. 实验设计

- **数据集/场景**：
  - **Machine Unlearning**：TOFU基准（虚构作者遗忘），包括forget05、forget10三个难度版本。
  - **毒性降低**：ParaDetox数据集（平行去毒化文本）。
  - **代码翻译（transpiler）**：LeetCode 100道题的Python、Java、C++、JavaScript四语言解法。
  - **VLM幻觉减少**：使用Llava-1.5和InstructBLIP两个视觉-语言模型，评估指标CHAIR（生成式幻觉）和POPE（判别式问题）。
  - **合成数据生成**：BoolQ和AG新闻分类数据集（各仅取100样本作为生成种子），以及人物事实生成（随机名人/历史人物）。
- **对比方法**：
  - **Unlearning**：Gradient Ascent, NPO（负偏好优化）, ECO（嵌入干扰）。
  - **毒性降低**：ICV（上下文向量），LoRA微调，上下文学习（In-Context Learning），以及DM（均值差异）、RFM、LR等。
  - **代码翻译**：DM, ICV, RFM, LR。
  - **VLM幻觉**：多个无需训练的方法（如VCD等）。
  - **数据生成**：传统的温度（Temperature）采样。
- **评估指标**：Toxicity评分, ROUGE-L, 模型Utility（通用问答能力）, 遗忘Cutoff率/ROUGE, o4-judge评分（代码翻译质量、事实性准确率）, CHAIR, POPE, 下游分类准确率（合成数据训练小模型后测试）。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提及模型实验在8B参数规模的LLM（Llama3.1-8B）上进行，并推测该方法可推广至更大模型。所有方法均为训练-free，仅需前向传播获取激活值，计算开销较低。但作者未披露具体的GPU小时数或集群配置。

## 5. 实验数量与充分性

- **实验组数较多**：覆盖**5大类任务**，每个任务内包含多个数据集（如TOFU有三个版本）和多个对比方法（每个任务至少3-4个基线）。例如：
  - Unlearning实验报告了不同阈值下的Utility vs Cutoff曲线，并与多个基线比较。
  - 毒性降低展示了toxicity和ROUGE两个指标的分布。
  - 代码翻译展示了所有12种语言对的表现。
  - VLM幻觉分别在两个模型上测试CHAIR和POPE。
  - 合成数据评估了两种小模型（Qwen2.5-0.5B, GPTNeo-1.3B）的训练效果以及事实性准确率。
- **充分性评估**：实验覆盖面较广，涵盖了LLM主流的应用挑战。对比方法选择合理，包括训练-free和需训练的方法。并且论文提供了消融实验（如不同阈值的控制）。但部分实验（如毒性降低）仅在一个数据集上验证，且未报告多次运行的统计误差（除分布图外）。总体而言，实验设计较为充分，但可进一步增强统计显著性。

## 6. 主要结论与发现

- LLM内部表示的收敛现象可统一由**IFS框架**解释，不同概念在不同层形成吸引子。
- 基于吸引子的**无需训练干预方法**在多项任务上达到或超越需要大量微调/保留数据的基线，且提供更灵活的控制（如阈值 \(\tau\)）。
- 具体发现：
  - 在TOFU遗忘任务中，即使是最难的forget10版本，在保持模型通用能力的同时可实现>90%的切断率。
  - 毒性降低：仅减去毒性吸引子即可显著降低毒性，且文本质量（ROUGE）保持良好。
  - 代码翻译：无需任何示例或指令，仅通过切换到目标语言吸引子即可实现高质量跨语言代码翻译。
  - VLM幻觉：持续注入视觉吸引子可有效减少物体幻觉，且不损害判别能力。
  - 合成数据：扰动吸引子生成的数据比高温度采样数据在事实性和下游任务上均更优（绝对提升>20%的事实准确率）。

## 7. 优点

- **理论统一性**：用IFS观点统一解释了LLM内部表示收敛现象，并与现有工作（如任务向量、信念状态）形成呼应。
- **方法轻量且无需训练**：所有下游任务只需一次前向传播获取吸引子，无需微调或保留数据，计算高效。
- **任务覆盖广泛**：从安全（unlearning/guardrailing）、可控生成（toxicity/steering）、跨模态（VLM）到数据增强，展示了方法的通用性。
- **实践效果好**：在多项任务上匹配甚至超越更重量的基线，且通过阈值可灵活调节性能-实用性权衡。
- **新颖视角**：将视觉幻觉归因于从视觉吸引子漂移回到纯文本吸引子，并给出简单修正策略。

## 8. 不足与局限

- **需要内部激活访问**：方法要求直接获取LLM中间层的隐藏状态，无法通过标准API实现，限制了在闭源模型上的应用。
- **模型规模局限**：实验仅在8B以内模型上验证，更大模型（如70B）是否保持吸引子特性尚未验证。
- **概念定义依赖于数据**：吸引子估计的好坏依赖于所选提示的代表性，且单一概念可能对应多个子吸引子（如不同语言风格、数学任务），如何自动发现层次结构未深入讨论。
- **实验统计性可加强**：部分实验未报告多次重复结果的标准差，且某些场景仅使用单一数据集（如ParaDetox），泛化性需更多验证。
- **阈值 \(\tau\) 选取需人工调整**：虽然提供了权衡旋钮，但最优选择需要验证集，且在开放域场景中可能不鲁棒。
- **理论分析深度有限**：虽然借用IFS框架，但并未严格证明LLM层定义真正的压缩映射，仅给出启发式近似和Collage定理的类比。

（完）
