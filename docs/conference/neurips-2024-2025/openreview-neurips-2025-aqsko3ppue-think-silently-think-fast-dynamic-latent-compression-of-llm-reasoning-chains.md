---
title: "Think Silently, Think Fast: Dynamic Latent Compression of LLM Reasoning Chains"
title_zh: 静思快想：大语言模型推理链的动态潜在压缩
authors: "Wenhui Tan, Jiaze Li, Jianzhong Ju, Zhenbo Luo, Ruihua Song, Jian Luan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AQsko3PPUe"
tags: ["query:ns-xai"]
score: 7.0
evidence: 压缩潜在推理链提升LLM推理效率
tldr: 大语言模型的思维链推理耗时且计算昂贵。本文提出压缩潜在推理（CoLaR），在潜在空间动态压缩推理过程，通过辅助预测压缩嵌入目标训练。实验表明在保持性能的同时大幅降低推理成本，为高效LLM推理提供新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 357}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 429}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 603}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 660, \"height\": 390}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 660, \"height\": 389}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 956, \"height\": 559}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1020, \"height\": 382}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 689, \"height\": 406}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1496, \"height\": 518}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1495, \"height\": 335}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1520, \"height\": 225}]"
motivation: CoT推理计算开销大，效率低。
method: 提出CoLaR，在潜在空间动态压缩推理链，结合辅助压缩嵌入预测。
result: 压缩后推理大幅降低开销，性能保持。
conclusion: 潜在压缩是提升LLM推理效率的有效途径。
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

## 论文详细中文总结

### 1. 核心问题与整体含义
- **研究动机**：大语言模型（LLM）通过思维链（CoT）推理取得优异性能，但生成冗长的 token 级推理链计算开销巨大，影响效率与可扩展性。
- **核心问题**：如何在保持推理质量的同时，大幅降低推理链长度和计算成本。
- **整体贡献**：提出压缩潜在推理（Compressed Latent Reasoning，CoLaR）框架，在潜在空间动态压缩推理过程，实现“静思快想”——用更少、更密集的潜在变量代替长 token 序列，并通过强化学习进一步优化。

### 2. 方法论：核心思想与关键技术
- **核心思想**：将多个连续推理 token 的嵌入压缩为一个潜在变量，让 LLM 在这种压缩表示上进行自回归推理。
- **两阶段训练架构**：
  - **监督微调（SFT）阶段**：
    - 在每个训练步随机采样压缩因子 $c$（范围 $[1, c_{max}]$）。
    - **嵌入压缩模块**：将 $c$ 个连续推理 token 的嵌入向量求和并缩放 $1/\sqrt{c}$（避免分布偏移）。
    - **辅助压缩嵌入预测目标**：训练一个 **潜在头（Latent Head）** 从 LLM 隐藏状态预测下一个压缩嵌入的概率分布（均值和方差），输出服从高斯分布。
    - **语言建模目标**：预测被压缩的推理 token（每组随机采样一个 token 作为标签）和答案 token。
    - 总损失 = 语言建模损失 + 潜在损失（采用软MSE损失或负对数似然损失）。
  - **强化学习（RL）阶段**：
    - 利用潜在头的概率性质，为同一问题采样 $G$ 个不同的潜在推理链及答案。
    - 采用 **GRPO 算法**，根据答案正确性计算组内归一化奖励，并平均到每个 token/潜在单元上。
    - 无 KL 正则项（参考 DAPO），鼓励模型探索更多正确路径并利用更简洁的路径。
- **推理阶段**：通过设置提示词中的压缩因子（如 “Let’s think 2×faster:”），动态调整推理速度；潜在头自动生成压缩嵌入，语言头决定何时终止推理。

### 3. 实验设计
- **数据集**：
  - 主要训练/评估：GSM8k-Aug（~385k 训练样本）。
  - 域外泛化测试：GSM-Hard、SVAMP、MultiArith（均为小学数学级别）。
  - 挑战性数据集：MATH（代数、微积分等 7.5k 训练 / 5k 测试）。
- **基准方法**：CoT、iCoT（内部化思维链）、Coconut（潜在token替换）、Distill（CODI复现版）。
- **评价指标**：准确率（Acc.%）和推理链长度（#L，平均 token/潜在数量）。
- **对比设置**：在四个小学数据集上比较，在 MATH 上额外进行 RL 实验，并扩展至 8B 模型对比 TokenSkip。

### 4. 资源与算力（文中说明）
- **GPU 型号与数量**：SFT 阶段使用 **8 块 A100 GPU**（分布式数据并行）；RL 阶段使用 **1 块 A100 GPU**。
- **批次大小**：SFT 总 batch size = 256；RL rollout batch size = 8，优化 batch size = 4，组大小 $G=8$。
- **训练时长**：最长 50 个 epoch 或 12 小时（先到为准）。
- **优化器**：AdamW，SFT 学习率 1e-4，RL 学习率 1e-6，权重衰减 1e-2。

### 5. 实验数量与充分性
- **主要实验**：表1 在四个数据集上对比 CoLaR（c=2 和 c=5）与 4 种基线，每个结果报告 5 次不同随机种子的平均值和 95% 置信区间。
- **消融实验**：对比确定型潜在头（DL）、无压缩 token 监督（OC）、均值池化压缩（MP）、NLL 损失（NLL），共 4 种变体，验证各组件贡献。
- **RL 实验**：表2 在 MATH 上用两种基座模型（DeepSeek-R1-Distill-Qwen-1.5B 和 Llama-3.2-1B-Instruct）验证 RL 效果，并分析平均奖励设计。
- **扩展实验**：表3 在 1B/8B 模型上对比 CoLaR 与 TokenSkip，涵盖 GSM-8k、MATH-500、GPQA。
- **动态压缩因子分析**：图4 对比随机训练 vs 单一因子训练；图5 泛化到未见过因子。
- **案例与层分析**：图3 示例解释，图6 层间激活变化。
- **充分性评价**：实验覆盖多个数据集、多种模型规模、消融与超参分析，统计严谨，对比公平（统一初始化、训练时间限制等），结论可靠。

### 6. 主要结论与发现
- **效率提升显著**：CoLaR（压缩因子5）相比 Coconut 准确率提高 14.1%，且推理链更短（4.57 vs 6.00）。
- **性能保持**：CoLaR（压缩因子2）相对显式 CoT 仅下降 4.8% 准确率，但推理链缩短 53.3%。
- **RL 进一步优化**：在 MATH 上，RL（GRPO）使准确率最高提升 5.36%，同时推理链长度减少 82.8%。
- **泛化能力强**：域外数据集（MultiArith）上 CoLaR 性能接近显式 CoT，优于其他潜在方法。
- **动态压缩有效**：训练时随机采样压缩因子可提升泛化能力，模型能适应未见的中间因子。

### 7. 优点
- **机制创新**：首次实现动态压缩的潜在推理，训练时随机压缩因子带来鲁棒性，推理时可灵活调整速度。
- **概率潜在头**：支持强化学习的探索-利用平衡，这是先前潜在方法不具备的。
- **高效计算**：SFT 阶段可完全并行化训练潜在头；推理时潜在链长度远短于 token 链。
- **实验严谨**：多数据集、多次运行、置信区间报告、充分消融、代码承诺开放。
- **可解释性**：通过嵌入相似度检索将潜在变量映射回 token，使得“潜在思维链”透明化。

### 8. 不足与局限
- **性能上限**：在大多数基准上 CoLaR 准确率未超越显式 CoT（仅在 GPQA 上超过），仍有提升空间。
- **泛化限制**：不能处理非整数压缩因子（如 c=1.5）或超过训练最大值的因子，源于离散 token 化约束。
- **潜在偏见放大**：推理压缩可能放大模型固有偏见，需谨慎监控下游应用。
- **仅测试数学推理**：方法对其他类型推理任务（如常识、多步推理）的有效性尚未验证。
- **计算资源**：RL 阶段需要多组采样，虽推理效率高但训练开销仍较大。

（完）
