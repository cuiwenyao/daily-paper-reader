---
title: "DLoFT: Gradient-Decoupled Fine-Tuning for Generalizable Long Chain-of-Thought Reasoning"
title_zh: DLoFT：梯度解耦微调实现泛化性长链思维推理
authors: "Sitong Wu, Haoru Tan, Jingyao Li, Shaofeng Zhang, XIAOJUAN QI, Bei Yu, Jiaya Jia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5ZDT1dxojA"
tags: ["query:ns-xai"]
score: 8.0
evidence: 长链思维推理增强可解释性
tldr: 针对长链思维（LongCoT）微调中模型过度拟合任务特定知识导致泛化差的问题，本文提出梯度解耦微调算法DLoFT，通过解耦特征提取与推理步骤，使模型学习通用推理能力。在多个推理基准上，DLoFT在分布外场景显著优于标准微调，为构建可解释且鲁棒的推理模型提供了新方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1368, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 407, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1429, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1332, \"height\": 978, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1337, \"height\": 565, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1041, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1092, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1036, \"height\": 194, \"label\": \"Table\"}]"
motivation: 标准LongCoT微调模型容易过拟合任务特定知识，导致分布外性能下降。
method: 提出梯度解耦算法，将特征提取与推理步骤的梯度分离，防止推理内容对特征表示的过度依赖。
result: DLoFT在数学推理等任务上分布外准确率提升显著，且保持分布内性能。
conclusion: 梯度解耦微调可有效增强长链思维推理的泛化性，推动可解释推理模型的发展。
---

## Abstract
Long chain-of-thought (LongCoT) has emerged as a powerful reasoning paradigm for enabling large language models (LLMs) to solve complex tasks through a systematic and thorough thinking phase.
Although supervised fine-tuning (SFT) on high-quality LongCoT traces has proven effective to activate LongCoT abilities, we find that models trained in this way tend to overfit problem-specific knowledge and heuristics, leading to degraded out-of-distribution performance.
To address this issue, we propose a Decoupled LongCoT Fine-Tuning (DLoFT) algorithm, which enables the model to learn generalizable LongCoT reasoning abilities while preventing overfitting to the reasoning content with problem-specific information.
The key idea is to decouple the gradient into two orthogonal components: 1) a paradigm-relevant gradient corresponding to the general LongCoT paradigm and 2) a content-relevant gradient reflecting the problem-specific information, where only the former gradient is used to update model parameters.
Specifically, by leveraging the unique two-phase composition (thinking and solution) of the LongCoT response, our gradient decoupling mechanism isolates the content-relevant gradient via a projection operation and separates the paradigm-relevant gradient through orthogonalization.
Our DLoFT ensures the model concentrate on internalizing the LongCoT paradigm rather than memorizing problem-specific knowledge and heuristics.
Extensive experiments demonstrate that our DLoFT significantly improves the generalization behavior of LongCoT abilities compared to SFT while maintaining strong in-distribution performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：长链思维（LongCoT）推理通过让模型在生成最终答案前进行系统性思考（反思、纠错、探索等）显著提升了LLM处理复杂任务的能力。目前主流方法是用高质量LongCoT数据进行监督微调（SFT）来激活这一能力，但实验发现SFT容易过度拟合训练数据中的问题特定知识和启发式（如数学竞赛题中的特定解题技巧），导致模型在分布外（out-of-distribution）新领域（如工程、经济、文学）上推理性能严重下降。
- **背景**：构建覆盖全面知识的大型LongCoT数据集成本高昂且不现实，因此亟需一种能使模型学习通用推理范式而非记忆特定领域知识的训练算法。

## 2. 论文提出的方法论

### 核心思想
- **梯度解耦**：将全响应的梯度分解为两个正交分量：①**范式相关梯度**（对应通用LongCoT推理范式）和②**内容相关梯度**（对应问题特定知识和启发式）。仅使用范式相关梯度更新模型参数，避免过拟合。

### 关键技术细节
- **利用LongCoT响应的两阶段结构**：LongCoT响应分为“思考阶段”（包含推理范式和问题内容）和“解决方案阶段”（仅包含问题内容）。这一结构自然支持解耦。
- **算法流程（文字说明）**：
    1. **计算全响应梯度g_full**：对完整LongCoT响应（思考阶段+解决方案）计算负对数似然（NLL）损失的梯度。
    2. **计算参考梯度g_ref**：仅对解决方案部分计算NLL损失的梯度，该梯度仅反映问题特定信息。
    3. **解耦内容相关梯度g_con**：将g_full投影到g_ref方向上，得到g_con = (⟨g_full,g_ref⟩/‖g_ref‖²) * g_ref。
    4. **解耦范式相关梯度g_par**：通过正交化获得g_par = g_full - g_con。
    5. **参数更新**：仅用g_par更新模型参数 θ ← θ - η·g_par。

### 公式说明
- 算法中核心操作为投影和正交化，均为轻量级向量运算，计算开销极小。

## 3. 实验设计

### 使用的数据集与场景
- **混合领域数据集**：s1K（含数学、编程、科学、谜题，共1000条高质量LongCoT数据，由Gemini Flash Thinking生成）。
- **单领域数据集**：
    - 数学：OpenR1-Math-5K（从220K中采样5K）
    - 编程：OpenThoughts-Code-5K（从114K中采样5K）
    - 医学：Medical-o1-5K（从原数据集中采样5K）
- **基准测试（Benchmark）**：
    - 数学：AIME24、MATH-500、OlympiadBench
    - 编程：LiveCodeBench (v2)
    - 医学：MedQA
    - 其他17个领域（物理、化学、生物、计算机、机械、电子、通信、天文、地理、土木、农业、经济、历史、法律、文学、哲学、社会学）均使用SuperGPQA对应子集。

### 对比方法
- **主要基线**：标准SFT（监督微调）。
- **扩展对比**：在RL冷启动阶段，将SFT冷启动与DLoFT冷启动进行对比，后续均使用GRPO算法进行强化学习。

### 模型
- 通用LLM：Qwen2.5-Instruct (7B/32B)
- 领域特定LLM：Qwen2.5-Math-7B-Instruct、Qwen2.5-Coder-7B-Instruct、Meditron-7B

## 4. 资源与算力

- **文中说明**：论文在附录A.4“效率分析”中比较了DLoFT与SFT的单步训练时间和GPU内存占用（使用Qwen2.5-7B-Instruct和s1K数据集）。结果显示DLoFT单步耗时约6.8分钟（SFT为6.2分钟），GPU内存约70,684 MB（SFT为69,986 MB），开销增加极小。
- **未明确信息**：文中未明确说明使用的具体GPU型号（如A100 80GB还是其他）、节点数量、总训练时长（如每个实验多少小时）等细节。作者在“局限性”部分指出受限于计算资源，无法进行更大规模验证。

## 5. 实验数量与充分性

### 实验数量
- **主要对比**：图3展示在17个领域上对通用LLM（7B/32B）进行性能对比，共覆盖20个领域（含数学、编程、医学的子领域）。图4展示在3个领域特定模型上分别进行in-domain和out-domain数据训练，共6组对比实验。
- **消融实验**：
    - 投影操作有效性（表1）
    - 梯度解耦机制有效性：对比仅用g_con和仅用g_par更新（表2）
    - 权重衰减正则化效果（表3）
    - 效率分析（表4）
- **RL冷启动实验**：在图4中，每个设置下都包含SFT/RL和DLoFT/RL的对比，共计多组。

### 充分性评价
- **充分**：实验覆盖了通用和领域特定模型、多种数据场景（单领域/混合领域、in-domain/out-domain）、多种基准测试（20个领域），以及消融验证各设计组件的必要性。结果客观呈现了性能变化（相对增益/损失），且所有实验均采用相同种子和训练设置，对比公平。
- **不足**：所有实验仅在7B和32B规模上进行，未在更大模型（如70B、671B）上验证；仅使用GRPO作为RL算法，未对比其他RL方法；未在更长的训练周期（如超过10 epoch）测试过拟合动态。但作者已承认实验规模有限这一局限。

## 6. 论文的主要结论与发现

1. **DLoFT显著提升泛化性**：相比SFT，在分布外领域平均提升+16.4分（7B模型）和+16.4分（32B模型），在分布内领域也提升+11.5分和+8.9分。
2. **缓解过拟合问题**：SFT在训练后期分布外准确率持续下降，而DLoFT保持稳定上升，且更快习得LongCoT行为（思考、反思等）。
3. **作为RL冷启动更优**：DLoFT冷启动可消除对领域内数据的依赖（使用其他领域数据也能取得接近in-domain的性能），并且为后续RL提供更强基础，放大RL收益（例如在医学模型上，RL+DLoFT比RL+SFT多提升1.3分）。
4. **领域特定模型受益显著**：在数学、编程、医学模型中，无论使用in-domain还是out-domain数据训练，DLoFT均优于SFT，表明其解耦机制有效滤除了领域特定干扰。

## 7. 优点

- **方法创新性**：首次利用LongCoT响应的两阶段结构进行梯度解耦，将推理范式与领域知识分离，思路简洁且物理意义清晰。
- **计算高效**：解耦操作仅为轻量级向量运算，额外开销极小（约10%时间、1%内存），易于替代现有SFT流程。
- **实用性强**：能有效降低对大规模、高质量领域内LongCoT数据的依赖，尤其适用于数据稀缺或隐私敏感领域（如医疗），降低数据采集和标注成本。
- **扩展性好**：可作为任何LLM（通用/领域特定）的微调方法，并能直接与后续RL训练结合，适用面广。
- **实验设计严谨**：消融实验验证了每个组件的必要性（投影、解耦机制），排除了权重衰减等常见正则化手段的干扰，结果可信。

## 8. 不足与局限

1. **实验规模有限**：仅在7B/32B模型上验证，未探索更大模型（如70B、671B）上的表现和泛化规律；作者承认受限于计算资源，未来需在更大规模上验证。
2. **依赖数据格式**：方法假设LongCoT响应具有明确的两阶段结构（思考+解决方案），对于非严格两阶段或格式不标准的LongCoT数据，解耦效果可能下降。
3. **对比方法单一**：仅与标准SFT对比，未与更复杂的正则化方法（如标签平滑、对抗训练、数据增强等）进行比较；RL阶段仅使用GRPO，未探索其他RL算法。
4. **领域覆盖不足**：虽然测试了20个领域，但主要集中于STEM，人文社科领域数据量和任务类型有限，泛化结论可能受限。
5. **潜在风险**：作者提及该方法可能被滥用于不人道目的（如监控、独裁控制），需注意伦理规制。

（完）
