---
title: "T1: Advancing Language Model Reasoning through Reinforcement Learning and Inference Scaling"
title_zh: T1：通过强化学习和推理扩展提升语言模型推理能力
authors: "Zhenyu Hou, Xin Lv, Rui Lu, Jiajie Zhang, Yujiang Li, Zijun Yao, Juanzi Li, Jie Tang, Yuxiao Dong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=tnxONP8zTE"
tags: ["query:ns-xai"]
score: 8.0
evidence: 使用强化学习和推理扩展提升大语言模型推理能力
tldr: 针对现有大语言模型推理主要依赖模仿学习且测试时扩展不足的问题，提出T1方法，通过过采样增加采样多样性并结合合成思维链数据进行强化学习训练。实验表明T1在多种推理任务上实现了有效的推理扩展，为语言模型推理能力的提升提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 681, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1746, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 741, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 738, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1765, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1761, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1135, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tnxonp8zte/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 549, \"height\": 411, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-tnxonp8zte/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 916, \"height\": 751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tnxonp8zte/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tnxonp8zte/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 265, \"label\": \"Table\"}]"
motivation: 现有方法依赖模仿学习，难以实现有效的测试时推理扩展。
method: 采用过采样增强采样多样性，结合合成思维链数据进行强化学习训练。
result: 在多个推理基准上展现了显著的推理扩展效果。
conclusion: T1为语言模型推理能力的可扩展训练提供了有效方案。
---

## Abstract
Large language models (LLMs) have demonstrated remarkable capabilities in complex reasoning tasks. However, existing approaches mainly rely on imitation learning and struggle to achieve effective test-time scaling. While reinforcement learning (RL) holds promise for enabling self-exploration, recent attempts yield modest improvements in complex reasoning. In this paper, we present T1 to scale RL by encouraging exploration and understand inference scaling. We first initialize the LLM using synthesized chain-of-thought data that integrates trial-and-error and self-verification. To scale RL training, we promote increased sampling diversity through over-sampling. We demonstrate that T1 with open LLMs as its base exhibits inference scaling behavior and achieves superior performance on challenging math reasoning benchmarks. More importantly, we present a simple strategy to examine inference scaling, where increased inference budgets directly lead to T1’s better performance without any additional verification. The model weights and training data are publicly available at https://github.com/THUDM/T1.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在复杂推理任务中表现出色，但现有方法主要依赖**模仿学习**（如SFT），难以实现有效的**测试时扩展**（test-time scaling）。虽然强化学习（RL）有望通过自我探索提升推理能力，但近期尝试在复杂推理任务上改进有限，且缺乏可扩展性。
- **研究背景**：经典的思维链（CoT）方法虽能增强推理，但多数工作聚焦于选取正确推理步骤，忽略试错和验证过程。同时，现有的测试时扩展多依赖重复采样和外部验证器（如Best-of-N），未能从根本上提升模型自身的推理能力。
- **整体目标**：提出**T1**框架，通过**鼓励探索的RL训练**来扩大搜索空间，实现**训练时扩展**（scaling RL training）和**推理时扩展**（inference scaling），使得更长的生成直接带来更好性能，无需额外验证。

## 2. 论文提出的方法论

### 核心思想
通过扩大LLM的推理搜索空间并鼓励多样化的推理轨迹，同时施加适当惩罚以维持训练稳定性，从而规模化强化学习训练，并引发模型的推理扩展行为。

### 关键技术细节
1. **初始化策略模型**（SFT阶段）：
   - 不使用仅包含正确步骤的CoT数据，而是使用**合成CoT数据**，其中包含试错（trial-and-error）和自验证（self-verification）过程。
   - 具体构造：对每个问题生成多个尝试，由LLM识别错误并反思原因，对正确尝试进行验证，最终整合成包含完整思考过程的CoT，再由LLM根据抽象模式重写为最终训练数据。
2. **RL训练中鼓励探索**：
   - **过采样**：对每个prompt采样大量响应（K=64），并使用高温度（τ>1）增加多样性，避免陷入固定模式。
   - **辅助熵奖励**：在RL损失中加入token级熵奖励，鼓励生成多样token。
   - **去中心化的KL正则化**：对KL散度进行归一化（减去除自身外的均值），并使用指数移动平均（EMA）动态更新参考模型，避免参考模型滞后，促进RL扩展。
3. **惩罚异常模式**：
   - 对重复、过长（超过最大长度）、垃圾文本（混合语言、乱码）等响应给予负奖励（-1），防止训练崩溃。
   - 规则检测 + 基于困惑度的过滤。

### 关键公式（文字说明）
- 使用REINFORCE风格优化，奖励为正确性（1或0），并通过leave-one-out策略进行奖励归一化。
- 损失函数包含标准RL损失和熵奖励项：`L = L_RL - α * H(π)`，其中`H`为token级熵。
- KL归一化：对每个prompt的K个响应，计算各自与参考模型的KL，然后减去除自身外的均值，再用于奖励调整。
- 参考模型参数通过EMA更新：`θ_ref(t) = α * θ_ref(t-1) + (1-α) * θ(t)`。

## 3. 实验设计

### 数据集与场景
- **训练数据**：来自MATH-train和NuminaMath，经过过滤（去除噪声标签和过于简单问题）得到约30k条用于RL训练，12k条用于SFT。
- **评估基准**：
  - **MATH500**（数学竞赛级）
  - **AIME2024**（美国数学邀请赛，30题）
  - **Omni-MATH-500**（奥林匹克级数学）
  - **GPQA**（研究生级科学问答，用于测试跨域泛化）

### 对比方法
- 闭源模型：GPT-4o、Claude-3.5-sonnet、o1-preview、QwQ-32B-preview
- 开源模型：Llama-3.3-70B-Instruct、Qwen2.5-Math-7B-Instruct、GLM-4-9B-chat、Qwen2.5-14B-Instruct、Qwen2.5-32B-Instruct
- 基线：T1-SFT（无RL）、T1（+RL）在不同基座模型（GLM-4-9B、Qwen2.5-14B、Qwen2.5-32B）上的表现。

### 主要结果（表1）
- T1 (Qwen2.5-32B) 在 MATH500 上达到 92.4%，超过 QwQ-32B-preview (90.6%)。
- 在 AIME 上达到 50.6%，与 QwQ-32B-preview 持平（50.0%）。
- 在 Omni-MATH-500 上 49.6%，优于所有对比模型。
- 在 GPQA 上 56.1%，也优于多个基线，显示跨域泛化能力。

## 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量、训练时长。
- 训练细节：
  - SFT：3个epoch，学习率1e-5，余弦衰减。
  - RL：每次prompt采样64个响应，每32个prompt进行一次梯度更新；学习率1.5e-6，KL系数2e-4。
  - 最大生成长度：GLM-4-9B和Qwen2.5-14B设为10,240 token；Qwen2.5-32B设为16,384 token。
- **结论**：论文未披露计算资源详情，因此无法评估训练的实际算力成本。

## 5. 实验数量与充分性

### 实验数量
- **主实验**：表1展示了在4个数据集上，T1与多种基线模型的对比，共约30组结果。
- **消融实验**：
  - **采样数量K的影响**：图3、图4展示了K=4/16/64时响应长度、准确率、KL-奖励关系的变化。
  - **温度的影响**：表2对比了不同温度（0.9~1.3）及min-p采样对MATH500、AIME、Omni-MATH-500的影响。
  - **惩罚机制的效果**：表3展示了是否施加惩罚对“过长比例”和准确率的影响。
- **推理扩展分析**：图6、图7、图8分别展示了截断不同长度后准确率随token数变化、不同训练步数下的扩展行为、以及推理模式分析。

### 充分性与公平性
- **充分性**：消融实验覆盖了关键超参数（K、温度、惩罚），并对推理扩展进行了系统测量。实验数量虽不算庞大，但针对核心问题（RL可扩展性、推理扩展）设计了清晰的对比。
- **客观与公平**：与多种主流开源/闭源模型在同一基准上比较，且使用统一的贪婪采样评估（Pass@1）。消融实验中控制变量合理。
- **不足**：未与更多近期RL方法（如VinePPO、DeepSeekMath等）在相同设置下对比；GPQA作为OOD任务仅作为补充，未深入研究跨域迁移能力。

## 6. 论文的主要结论与发现

1. **RL训练可扩展性**：通过过采样、高温度、熵奖励和动态KL归一化，T1的RL训练能够有效提升模型推理能力，且更大K（64）带来更快、更好的收敛。
2. **推理扩展行为**：T1在推理时，随着生成token数增加（更长思考），准确率持续提升，无需外部验证器。这一行为随RL训练步数增加而更加显著。
3. **反思与验证能力**：长响应中包含了更多“反思”、“尝试不同方法”、“验证”等模式，这些是提升推理质量的关键步骤。
4. **跨域泛化**：在数学领域训练后，T1在GPQA（科学问答）上也取得了提升，表明学到的推理能力有一定通用性。
5. **惩罚机制的重要性**：不施加惩罚会导致训练不稳定（生成过长、重复文本），而惩罚可使训练稳定收敛。

## 7. 优点

- **方法创新**：将试错和自验证过程融入SFT初始数据，区别于以往只聚焦正确步骤的方法，有效扩大初始搜索空间。
- **探索策略系统化**：高K采样、高温度、熵奖励、去中心KL归一化、EMA参考模型等多管齐下，使RL训练可扩展。
- **推理扩展测量方法简洁有效**：通过截断响应长度并结合摘要模型生成答案，直接观察思考长度与性能的关系，无需额外奖励模型。
- **公开代码和数据**：模型权重和训练数据已开源，便于复现和进一步研究。
- **实验设计清晰**：消融实验针对关键设计因素逐一验证，推理扩展分析图展示了显著的scale趋势。

## 8. 不足与局限

- **任务覆盖有限**：主要针对数学推理，虽然GPQA有提升但只是辅助验证，未在其他领域（如代码、逻辑推理）系统评估。
- **计算成本未说明**：论文未给出训练所用GPU型号、数量、时间，难以评估方法的实际可重复性和资源要求。
- **RL训练敏感度**：温度、K值等需要精细调参，且高温度可能增加不稳定性；在无惩罚情况下训练容易崩溃。
- **推理扩展测量假设较强**：通过截断模拟不同思考长度，但实际中模型可能依赖整个序列进行推理，截断可能破坏完整性；摘要模型也可能引入偏差。
- **对比不全面**：未与最新的开源RL推理方法（如DeepSeekMath-RL、VinePPO等）在同等条件下比较；与闭源模型（o1）只引用结果，未在同一评估标准下复现。
- **可能存在的偏差**：训练数据主要来自数学竞赛，模型可能偏向于寻找形式化解法，在开放域或常识推理上效果未知。

（完）
