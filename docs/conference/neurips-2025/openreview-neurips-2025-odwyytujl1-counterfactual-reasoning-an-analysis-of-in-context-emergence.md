---
title: "Counterfactual reasoning: an analysis of in-context emergence"
title_zh: 反事实推理：上下文突现分析
authors: "Moritz Miller, Bernhard Schölkopf, Siyuan Guo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=odWYytUjl1"
tags: ["query:ns-xai"]
score: 5.0
evidence: 语言模型中的反事实推理
tldr: 该论文研究语言模型的上下文反事实推理能力，即预测假设场景的后果。在线性回归任务中，模型通过推断未观测的潜在概念并复制上下文噪声来实现反事实预测。证明了语言模型具备反事实推理能力，并给出了理论简化。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 706, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 711, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 712, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 712, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 712, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 706, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1446, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1450, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1447, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1448, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1442, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1453, \"height\": 2208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-odwyytujl1/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1441, \"height\": 817, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-odwyytujl1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 344, \"label\": \"Table\"}]"
motivation: 反事实推理是智能的重要方面，但语言模型是否具备尚不清晰。
method: 设计线性回归任务要求模型进行噪声推理，分析模型预测机制。
result: 表明语言模型能通过推断潜在概念和复制噪声进行反事实推理。
conclusion: 语言模型可通过上下文学习实现反事实推理，具有理论保证。
---

## Abstract
Large-scale neural language models exhibit remarkable performance in in-context learning: the ability to learn and reason about the input context on the fly. This work studies in-context counterfactual reasoning in language models, that is, the ability to predict consequences of a hypothetical scenario. We focus on a well-defined, synthetic linear regression task that requires noise abduction. Accurate prediction is based on (1) inferring an unobserved latent concept and (2) copying contextual noise from factual observations. We show that language models are capable of counterfactual reasoning. Further, we enhance existing identifiability results and reduce counterfactual reasoning for a broad class of functions to a transformation on in-context observations. In Transformers, we find that self-attention, model depth and pre-training data diversity drive performance. Moreover, we provide mechanistic evidence that the latent concept is linearly represented in the residual stream and we introduce designated *noise abduction heads* central to performing counterfactual reasoning. Lastly, our findings extend to counterfactual reasoning under SDE dynamics and reflect that Transformers can perform noise abduction on sequential data, providing preliminary evidence on the potential for counterfactual story generation. Our code is available under *https://github.com/mrtzmllr/iccr*.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：语言模型是否具备在上下文（in-context）中进行反事实推理（counterfactual reasoning）的能力？即能否根据给定的假设情景（“如果...会怎样”）预测其结果？
- **研究背景**：反事实推理是智能体进行原则性思考和快速学习的关键，在因果推断、公平性、个性化医疗等领域有重要应用。现有语言模型在上下文学习（ICL）中表现优异，但其能否进行反事实推理尚不清楚。
- **整体含义**：该工作旨在通过可控的合成任务（线性回归）严格评估语言模型的反事实推理能力，并从理论、机制和实验角度验证其可行性。作者还尝试将该能力扩展到循环时序数据（如Lotka-Volterra捕食者-猎物模型），为反事实故事生成提供初步证据。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 使用因果框架（Pearl的三步法）：**噪声推断（noise abduction）** → **干预（intervention）** → **预测（prediction）**。即，给定事实观测(\(x, y\))，先反推出不可观测的噪声\(u\)，然后对\(X\)进行干预（设定为\(x^{CF}\)），最后用相同的噪声\(u\)和模型\(f\)预测\(y^{CF}\)。
- 利用**可交换性（exchangeability）** 假设：预训练数据来自不同分布的混合，每个序列可通过潜在变量\(\theta\)参数化。模型在推理时计算后验预测分布。

### 关键技术细节
- **任务设定**：合成线性回归任务 \(y = \beta x + u_y\)，其中\(\beta, u_x, u_y\)由潜在变量\(\theta\)生成。输入序列形式：\((x_1, y_1, \ldots, x_n, y_n, z, x^{CF})\)，其中\(z\)指示事实观测的位置，要求预测\(y^{CF}\)。
- **引理1**：对于一大类可逆函数（加性噪声、乘性噪声、指数噪声等），反事实推理可简化为对观测值的变换 \(y^{CF} = h(f(x^{CF}), f(x), y)\)，其中\(h\)由\(T\)和其逆唯一确定。
- **定理1**：在可交换性设定下，\(T\)是反事实可识别的（counterfactually identifiable），即可以从条件联合分布\(P_{X,Y|\theta}\)唯一确定生成机制。
- **模型架构**：主要研究decoder-only GPT-2（标准Transformer），并与LSTM、GRU、Elman RNN对比。分析了注意力层、模型深度、预训练数据多样性的影响。

## 3. 实验设计：数据集、基准、对比方法

### 数据集
- **合成线性回归数据**：潜在变量\(\theta \sim U([-6,6]^E)\)，\(\beta|\theta \sim N(\theta, I_E)\)，噪声\(U|\theta \sim N(\theta, I_E)\)，\(X^{CF} \sim U([-6,6]^E)\)，嵌入维度\(E=5\)。每个序列包含2到50个上下文例子，训练50,000步，batch size 64。
- **循环动态系统（SDE）**：Lotka-Volterra捕食者-猎物模型，使用伊藤随机微分方程（SDE），参数依赖潜在\(\theta\)。时间步从[0,0.5]均匀采样，每个序列20个时间点，预测整个反事实轨迹。

### 基线/对比方法
- 模型架构对比：GPT-2 (12层, 8头, 256维) vs LSTM (2层, 256维) vs GRU (2层, 256维) vs Elman RNN (2层, 256维)。
- 消融实验：
  - 仅MLP vs 仅注意力 (Attention-Only, AO) 不同层数。
  - 固定总注意力头数8，改变深度（1层8头 → 8层1头）。
  - 预训练数据多样性：改变有效支持度（effective support size），比较Uniform vs Normal分布。
  - 非线性和非加性函数扩展（tanh, sigmoid, 乘法噪声）。
  - 与标准上下文学习（仅延续而非反事实）对比。

### 评估指标
- **均方误差 (MSE)**：预测反事实值\(y^{CF}\)与真实值之间的MSE。报告对数尺度下的In-context MSE随上下文例子数量的变化。
- **调整R²**：用于探针实验，评估残差流中潜在变量\(\theta\)的线性编码程度。

## 4. 资源与算力

- 论文提到实验运行在**一张NVIDIA GeForce RTX 3090 GPU**上。
- 每次训练时间在**5分钟到2小时**之间，取决于模型配置和任务。
- 使用AdamW优化器，学习率\(10^{-4}\)，基于PyTorch和Garg等人(2022)的代码库。

## 5. 实验数量与充分性

- **实验数量**：论文进行了大量系统实验：
  - 4种模型架构对比（Transformer, LSTM, GRU, Elman RNN）。
  - 注意力消融：MLP-Only, 2/4/8层AO, 标准Transformer。
  - 深度消融：1层8头、2层4头、4层2头、8层1头（Full和AO）。
  - 数据多样性：两种分布（Uniform/Normal）下5~6种不同支持度。
  - 非线性函数扩展（tanh, sigmoid, 乘法）共3种。
  - 循环SDE系统：4种模型对比，注意力模式分析。
  - 噪声推断头出现分析（1M步训练），以及与非反事实回归对比（1M步）。
- **充分性**：实验设计较为全面，涵盖了架构选择、组件分析、数据多样性、泛化能力、机制解释等多个维度。每个实验通常使用6400条测试序列，报告误差条（bootstrap）。整体上客观、公平，但主要依赖于合成数据。

## 6. 论文的主要结论与发现

1. **语言模型能够进行上下文反事实推理**：GPT-2在合成线性回归任务上达到接近最优的MSE，且随着上下文例子增多误差下降。
2. **自注意力层和模型深度是关键**：纯MLP无法推理，注意力仅模型（AO）可工作；更深的模型（8层1头）优于浅层模型（1层8头）。
3. **预训练数据多样性至关重要**：有效支持度越高，模型泛化越好，包括OOD场景（Uniform训练、Normal测试等）。
4. **潜在概念线性编码在残差流中**：通过线性探针可在第二层后以调整R²>0.9预测潜在\(\theta\)。
5. **发现专门的噪声推断头**：在GPT-2的第七层第六个注意力头中，注意力机制会指向事实观测的\(y_z\)，用于噪声推断。
6. **扩展到循环动态系统**：GPT-2在Lotka-Volterra SDE上达到极低MSE（约0.0025），而RNN误差较高（>0.1），表明Transformer能处理顺序依赖的反事实推理。

## 7. 优点

- **理论扎实**：将反事实推理与可交换性、可识别性理论结合，给出引理1和定理1，使任务有严格数学基础。
- **机制可解释**：通过线性探针、注意力模式可视化、噪声推断头等分析，提供了Transformer内部机制的证据。
- **控制良好的实验**：使用合成数据避免了自然语言评估的歧义，允许精确衡量推理能力。
- **覆盖广泛**：从线性到非线性、加性到乘性、回归到动态系统，逐步扩展，验证了方法的普适性。
- **代码开源**：便于复现和后续研究。

## 8. 不足与局限

- **合成数据局限**：所有实验基于高度简化的合成任务，距离真实自然语言场景（如反事实故事生成）较远，结论的生态效度有限。
- **模型规模小**：仅使用GPT-2级别（12层、256维）的小模型，未在大语言模型上验证。
- **无混淆变量**：假设无未观测混杂，现实世界难以满足。
- **循环SDE实验**：训练仅使用了20个不同的时间序列（动态系统），且采用课程学习，不完全满足可交换性假设。
- **评估指标单一**：仅使用MSE，未考虑不确定性量化或语义合理性。
- **未讨论自然语言基准**：未使用现有反事实推理数据集（如WIQA、COUNTERFACTUAL等）进行评估。

（完）
