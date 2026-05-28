---
title: "Think Silently, Think Fast: Dynamic Latent Compression of LLM Reasoning Chains"
title_zh: 静默思考，快速回答：LLM推理链的动态潜在压缩
authors: "Wenhui Tan, Jiaze Li, Jianzhong Ju, Zhenbo Luo, Ruihua Song, Jian Luan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AQsko3PPUe"
tags: ["query:ns-xai"]
score: 5.0
evidence: 动态潜在压缩LLM推理链
tldr: 该论文提出压缩潜在推理（CoLaR）框架，通过两阶段训练动态压缩CoT推理链到潜在空间。在微调阶段，增加下一个压缩嵌入预测目标，随机合并连续token嵌入，训练潜在头预测后续嵌入分布。实验表明CoLaR在保持推理质量的同时大幅减少计算开销。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 660, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 660, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 956, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1020, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 689, \"height\": 406, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1496, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1495, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1520, \"height\": 225, \"label\": \"Table\"}]"
motivation: Token级CoT推理链计算昂贵且低效。
method: CoLaR通过在潜在空间中动态压缩连贯token嵌入，并训练潜在头预测下一代嵌入，减少推理步骤。
result: 在推理基准上，CoLaR保持原模型性能的同时显著降低了计算代价。
conclusion: 潜在空间推理压缩是提升LLM推理效率的有效方向。
---

## Abstract
Large Language Models (LLMs) achieve superior performance through Chain-of-Thought (CoT) reasoning, but these token-level reasoning chains are computationally expensive and inefficient.
In this paper, we introduce Compressed Latent Reasoning (CoLaR), a novel framework that dynamically compresses reasoning processes in latent space through a two-stage training approach.
First, during supervised fine-tuning, CoLaR extends beyond next-token prediction by incorporating an auxiliary next compressed embedding prediction objective. This process merges embeddings of consecutive tokens using a compression factor $c$ randomly sampled from a predefined range, and trains a specialized latent head to predict distributions of subsequent compressed embeddings. Second, we enhance CoLaR through reinforcement learning (RL) that leverages the latent head's non-deterministic nature to explore diverse reasoning paths and exploit more compact ones.
This approach enables CoLaR to: i) **perform reasoning at a dense latent level** (i.e., silently), substantially reducing reasoning chain length, and ii) **dynamically adjust reasoning speed** at inference time by simply prompting the desired compression factor.
Extensive experiments across four mathematical reasoning datasets demonstrate that CoLaR achieves 14.1% higher accuracy than latent-based baseline methods at comparable compression ratios, and reduces reasoning chain length by 53.3% with only 4.8% performance degradation compared to explicit CoT method. Moreover, when applied to more challenging mathematical reasoning tasks, our RL-enhanced CoLaR demonstrates performance gains of up to 5.4% while dramatically reducing latent reasoning chain length by 82.8%.
The code and models will be released upon acceptance.

---

## 论文详细总结（自动生成）

# 论文总结：Think Silently, Think Fast: Dynamic Latent Compression of LLM Reasoning Chains

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：大型语言模型（LLM）通过链式思维（Chain-of-Thought, CoT）推理取得了优异性能，但生成的 token 级推理链条计算成本高昂、效率低下，尤其在真实部署场景中会带来严重的服务器负载。
- **背景**：现有提速方法大多在 token 层面操作（如跳过非重要 token、压缩推理步骤），仍受限于稀疏 token 表示。一些工作尝试在连续的潜在空间中进行推理，但要么使用固定长度推理链，要么采用确定性生成方式，缺乏适应性和探索-利用能力。
- **整体含义**：本文提出一种能够动态压缩推理链到潜在空间的框架 CoLaR，在保持推理质量的同时大幅减少计算开销，并引入强化学习进一步探索更优的潜在推理路径。

## 2. 方法论

### 核心思想
- 将连续多个推理 token 的嵌入合并为一个压缩的潜在变量（latent），让模型在更稠密的潜在空间中进行自回归推理。训练分为两个阶段：监督微调（SFT）+ 强化学习（RL）。

### 关键技术细节
- **嵌入压缩模块（Embedding Compress）**：对每 $c$ 个连续推理 token 的嵌入求和并除以 $\sqrt{c}$（保持原始分布方差），得到压缩嵌入 $e_c$。
- **辅助预测目标**：在 SFT 阶段，除了常规的下一 token 预测（对压缩后的推理 token 随机采样一个作为标签），还训练一个**潜在头（Latent Head）** 预测下一个压缩嵌入的概率分布（均值 $\hat{\mu}$ 和标准差 $\hat{\sigma}$），使用负对数似然损失或软 MSE 损失（含熵正则项）。
- **动态压缩因子**：训练时从 $[1, c_{max}]$ 中随机采样压缩因子 $c$，使模型学会适应不同压缩率；推理时可指定 $c$ 动态调整推理速度。
- **强化学习阶段**：基于 GRPO 算法，对同一问题采样多组输出（潜在推理链+答案），根据答案正确性计算组内相对奖励，平均到每个潜在/token 上，鼓励模型探索正确路径并利用更短的推理链。

### 算法流程（文字说明）
1. 输入问题 + 提示（如“Let's think 2×faster:”）；
2. 自回归预测潜在变量：将当前隐藏状态通过潜在头输出分布，采样得到下一个压缩嵌入；
3. 语言头（Language Head）决定何时终止推理（预测答案 token 或结束符）；
4. 训练时：随机采样 $c$，压缩推理链嵌入，同时优化压缩 token 预测损失和潜在嵌入预测损失；
5. RL 阶段：对每个问题生成 $G$ 条完整推理路径，用 GRPO 更新策略。

## 3. 实验设计

### 数据集与场景
- **主要训练/测试**：GSM8k-Aug（38.5 万训练样本）
- **域内评估**：GSM8k（原始测试集）
- **域外泛化**：GSM-Hard、SVAMP、MultiArith（共约 2600 测试样本）
- **更具挑战的数学推理**：MATH（7.5k 训练、5k 测试，覆盖代数、微积分等）
- **规模扩展实验**：GSM-8k、MATH-500、GPQA（科学推理）

### Benchmark 方法
- **CoT**：标准链式思维微调
- **iCoT**：逐步移除推理步骤内化
- **Coconut**：逐步用潜在表示替代 token 推理（固定 6 步）
- **Distill**（复现 CODI）：自蒸馏固定长度潜在推理
- **TokenSkip**：仅对比部分实验（8B 模型上）
- **CoLaR 变体**：去除压缩 token 监督（-OC）、确定性潜在头（-DL）、平均池化（-MP）、NLL 损失（-NLL）

### 对比方法数量
- 主要对比 4 种基线方法，加上多种消融变体。总计约 8 组方法在 4 个数据集上做对比（表 1）；另外在 MATH 上比较 CoT、CoLaR-DL、CoLaR-NLL、CoLaR-RL（表 2）；并在更大模型上（1B/8B）与 TokenSkip 对比（表 3）。

## 4. 资源与算力

- 论文明确提到：使用 8 张 A100 GPU 进行 SFT 训练，总 batch size 256；RL 在单张 A100 上运行，rollout batch size 8，group size 8。
- 训练时长：所有模型最多训练 50 个 epoch 或 12 小时（先到者止）。总计算量未给出具体 GPU 小时数，但相对透明。

## 5. 实验数量与充分性

- **核心实验**：表 1 在 4 个数据集上报告了 5 次独立运行的平均准确率和推理长度（含 95% 置信区间），涉及 CoT、iCoT、Coconut、Distill 以及 CoLaR 两个压缩因子（c=5, c=2）及 4 种消融变体。共计约 8（方法）×4（数据集）= 32 组结果。
- **消融实验**：包括确定性 vs 概率潜在头、有无压缩 token 监督、平均池化 vs 方差缩放、不同损失函数，充分验证各组件贡献。
- **强化学习实验**：在 MATH 上使用两个基础模型（Qwen-1.5B, Llama-1B）比较 CoLaR-DL/NLL/RL，并分析奖励平均、基础模型质量影响。
- **动态压缩因子分析**：图 4、图 5 分别展示训练时随机 c 与固定 c 的对比、以及推广到未见压缩因子的能力。
- **案例分析与层间分析**：图 3 展示潜在变量的可解释性，图 6 分析不同压缩因子下各层激活差异。
- **规模扩展**：表 3 在 1B/8B 模型上验证，与 TokenSkip 对比。

总体而言，实验覆盖了多个维度（准确率、推理长度、泛化、消融、可解释性、缩放性），且报告了统计显著性，设计较为充分、客观。

## 6. 主要结论与发现

- CoLaR 在**同等压缩率**下比现有潜在推理方法准确率提升 14.1%（如 c=5 时平均 Acc. 41.7% vs Coconut 27.6%）。
- 相比显式 CoT，CoLaR-2 仅降低 4.8% 准确率（53.6%→48.8%），但推理链长度减少了 53.3%。
- 在 MATH 上，RL 增强版 CoLaR 准确率最多提升 5.36%，且推理长度降低 82.8%。
- 消融证实：概率潜在头+软 MSE 损失、压缩 token 监督、方差缩放嵌入压缩、动态训练都有益。
- 平均奖励设计（per-token）对缩短推理链至关重要；基础模型质量影响 RL 效果。
- CoLaR 能泛化到未见的压缩因子（如训练于 {1,3,5,7} 可测试于 {2,4,6}）。
- 潜在变量可解释：通过嵌入余弦相似度可检索对应 token 组。

## 7. 优点

- **新颖性**：首次实现**动态可调**压缩率的潜在推理，且通过概率性潜在头引入探索-利用能力。
- **高效性**：大幅减少推理链长度（最高 82.8% 压缩），同时保持甚至提升准确率（在 GPQA 上超过 CoT 教师模型）。
- **全面性**：实验覆盖多个数据集、多种消融、两种基础模型、不同规模；统计报告完善（95% CI）。
- **可解释性**：通过嵌入检索可视化潜在变量含义，使潜在推理过程透明化。
- **实用潜力**：训练时动态采样压缩因子，推理时只需改变提示即可调整速度，部署灵活。

## 8. 不足与局限

- **性能上限**：除 GPQA 外，CoLaR 整体准确率仍略低于显式 CoT（但差距很小），尚未超越。
- **压缩因子限制**：无法泛化到非整数压缩因子（如 c=1.5）或超出训练范围的值，受限于离散 tokenization。
- **计算资源披露**：虽提及 GPU 型号和训练时间约束，但未给出总 GPU 小时数或能耗数据，可复现性略受影响。
- **应用限制**：仅评估数学推理任务，未测试其他领域（如常识推理、代码生成等）。潜在推理的泛化性有待验证。
- **潜在偏见风险**：压缩过程可能放大训练数据中的偏见，论文提及但未做针对性分析。

（完）
