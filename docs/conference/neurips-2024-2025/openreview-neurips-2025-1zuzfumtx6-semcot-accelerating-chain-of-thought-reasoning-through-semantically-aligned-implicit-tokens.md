---
title: "SemCoT: Accelerating Chain-of-Thought Reasoning through Semantically-Aligned Implicit Tokens"
title_zh: SemCoT：通过语义对齐的隐式令牌加速链式推理
authors: "Yinhan He, Wendy Zheng, Yaochen Zhu, Zaiyi Zheng, Lin Su, Sriram Vasudevan, Qi Guo, Liangjie Hong, Jundong Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1ZuzFUMtx6"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过语义对齐隐式令牌加速大模型推理
tldr: 大语言模型链式推理虽强但冗长，隐式推理可加速却常丢失语义对齐。SemCoT通过语义对齐的隐式令牌，在缩短推理长度的同时保持与真实推理的语义一致性，从而加速LLM推理而不牺牲性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 491}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 702}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 486}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 916, \"height\": 460}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 512}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 602}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 602}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 858}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 864}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1427, \"height\": 788}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1427, \"height\": 787}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 767}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1428, \"height\": 790}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1431, \"height\": 796}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 793}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1453, \"height\": 759}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1435, \"height\": 778}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 885}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1468, \"height\": 2049}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1762}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1065, \"height\": 266}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 269}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1514, \"height\": 2080}]"
motivation: 链式推理虽然有效但冗长，隐式推理方法加速却破坏了语义对齐。
method: 引入语义对齐的隐式令牌，在LLM隐藏嵌入中编码推理步骤。
result: 在多种推理任务上显著加速，同时保持或提升推理准确性。
conclusion: 语义对齐的隐式令牌有效平衡了推理速度与语义保真度。
---

## Abstract
Chain-of-Thought (CoT) enhances the performance of Large Language Models (LLMs) on reasoning tasks by encouraging step-by-step solutions. However, the verbosity of CoT reasoning hinders its mass deployment in efficiency-critical applications. Recently, implicit CoT approaches have emerged, which encode reasoning steps within LLM's hidden embeddings (termed ``implicit reasoning'') rather than explicit tokens. This approach accelerates CoT reasoning by reducing the reasoning length and bypassing some LLM components. However, existing implicit CoT methods face two significant challenges: (1) they fail to preserve the semantic alignment between the implicit reasoning (when transformed to natural language) and the ground-truth reasoning, resulting in a significant CoT performance degradation, and (2) they focus on reducing the length of the implicit reasoning; however, they neglect the considerable time cost for an LLM to generate one individual implicit reasoning token. To tackle these challenges, we propose a novel semantically-aligned implicit CoT framework termed **SemCoT**. In particular, for the first challenge, we design a contrastively trained sentence transformer that evaluates semantic alignment between implicit and explicit reasoning, which is used to enforce semantic preservation during implicit reasoning optimization. To address the second challenge, we introduce an efficient implicit reasoning generator by finetuning a lightweight language model using knowledge distillation. This generator is guided by our sentence transformer to distill ground-truth reasoning into semantically aligned implicit reasoning, while also optimizing for accuracy. SemCoT is the first approach that enhances CoT efficiency by jointly optimizing token-level generation speed and preserving semantic alignment with ground-truth reasoning. Extensive experiments demonstrate the superior performance of SemCoT compared to state-of-the-art methods in both efficiency and effectiveness. Our code can be found at https://github.com/YinhanHe123/SemCoT/.

---

## 论文详细总结（自动生成）

# SemCoT：通过语义对齐的隐式令牌加速链式推理——论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：Chain-of-Thought (CoT) 虽然能显著提升大语言模型 (LLM) 的推理能力，但其冗长的显式推理步骤导致推理时间过长，阻碍了在效率敏感场景中的大规模部署。现有隐式 CoT 方法（将推理步骤编码为 LLM 隐藏嵌入）虽然通过缩短推理长度和绕过部分解码组件来加速，但面临两个关键挑战：
  1. **语义对齐缺失**：隐式推理（若转换为自然语言）与真实推理之间的语义一致性无法保持，导致 CoT 性能严重下降。
  2. **生成单个隐式令牌的时间成本被忽略**：现有方法仅关注减少隐式推理的令牌数量，却忽视了 LLM 生成每个隐式令牌本身的高计算开销（尤其在百亿参数模型中，生成一个令牌可能耗时约 0.1 秒）。
- **整体含义**：本文提出 **SemCoT**，旨在**同时优化隐式推理的令牌级生成速度**和**保持与真实推理的语义对齐**，从而在加速 LLM 推理的同时不牺牲性能。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
通过两个步骤实现语义对齐的高效隐式推理：
1. **语义对齐评估**：训练一个定制化的句子变换器（Sentence Transformer），用于衡量隐式推理与真实推理之间的语义相似度。
2. **高效隐式推理生成**：利用轻量级语言模型（Lightweight LM）作为隐式推理生成器，在定制句子变换器的指导下，通过知识蒸馏生成语义对齐的隐式推理，同时优化答案准确性。

### 2.2 关键技术细节
#### 步骤一：隐式推理与真实推理的语义对齐评估
- **动机**：直接比较 LLM 嵌入空间中的向量距离无法可靠衡量语义相似度（因为 LLM 嵌入优化目标为下一令牌预测，且高维空间存在维度灾难）。
- **方法**：设计定制化句子变换器 \( C_\phi \)：
  - **主干**：从目标 LLM 中提取中间五层（已证明具有最佳语言建模能力和跨任务可迁移性）。
  - **池化层**：聚合整个推理序列的令牌嵌入为统一的向量表示。
  - **线性投影层**：将向量映射到低维语义嵌入空间（维度设为 768），便于余弦相似度比较。
- **训练**：使用对比学习：
  - 构建推理对数据集 \( G = \{(R_i, S_i)\} \)，其中 \( R_i \) 为真实推理，\( S_i \) 为由 GPT-4o-mini 生成的语义等价的压缩推理。
  - 损失函数：\( \mathcal{L}_{\text{sim}} = -\frac{1}{|G|} \sum_{(R_i,S_i)\in G} \log \frac{\exp(\text{sim}(e_{R_i}, e_{S_i})/\tau)}{\sum_{j=1}^{|G|}\exp(\text{sim}(e_{R_i}, e_{S_j})/\tau)} \)，最大化正样本对相似度，最小化负样本对相似度。

#### 步骤二：高效隐式推理生成（令牌级优化）
- **动机**：使用轻量级 LM 替代原始 LLM 生成隐式推理，显著降低每个令牌的生成时间。但轻量级 LM 的嵌入空间与 LLM 不匹配，需通过线性投影层对齐。
- **方法**：构建隐式推理生成器 \( I_\psi \)：
  - **基座**：选用与目标 LLM 同源的剪枝/蒸馏轻量模型（如 Sheared-LLaMA-1.3B 对应 Llama-2-7B，mistral-1.1b-testing 对应 Mistral-7B）。
  - **输入**：在查询后拼接 \( k \) 个特殊 `<CoT>` 令牌（\( k \) 为隐式推理长度）。
  - **输出**：收集所有 `<CoT>` 令牌的最后一层隐藏嵌入，通过线性投影层映射到 LLM 的嵌入空间，得到隐式推理 \( Z = I_\psi(Q) \)。
- **训练损失**（总损失 \( \mathcal{L}_{\text{total}} = \lambda \mathcal{L}_{\text{sem}} + (1-\lambda)\mathcal{L}_{\text{pred}} \)）：
  - **答案预测损失** \( \mathcal{L}_{\text{pred}} \)：交叉熵，鼓励 LLM 在给定隐式推理时正确生成答案。
  - **语义对齐损失** \( \mathcal{L}_{\text{sem}} \)：利用已冻结的句子变换器 \( C_\phi \)，最大化隐式推理与真实推理的语义嵌入余弦相似度。
  - 超参数 \( \lambda \) 控制语义对齐与预测准确性的平衡。

#### 3. 训练与推理流程
- **训练**：
  - 第一阶段：训练句子变换器（优化 \( \phi \)），仅更新其线性投影层 \( \phi_{\text{linear}} \)（预热）。
  - 第二阶段：训练隐式推理生成器（优化 \( \psi \)），冻结 \( \phi \)，同样先预热线性投影层 \( \psi_{\text{linear}} \)。
- **推理**：查询与 \( k \) 个 `<CoT>` 令牌拼接后输入轻量生成器，得到隐式推理，再与查询嵌入拼接送入 LLM 生成最终答案。

## 3. 实验设计

### 3.1 数据集
- **数学推理**：GSM8K（7,500 训练/1,000 测试）、SVAMP（700/300）、MultiArith（420/180）
- **常识推理**：CommonsenseQA（9,741/1,140）
- **符号推理**：CoinFlip（20,000/3,330）

### 3.2 评估指标
- **有效性**：答案准确率（Accuracy）
- **效率**：每个查询的平均推理时间（秒）

### 3.3 对比方法（Baselines）
- **Pause**：使用相同的隐式推理令牌替代真实推理，仅微调 LLM（因预训练成本过高，仅实现微调）。
- **ICoT-SI / COCONUT**：渐进编码方法，在微调中逐步用隐式令牌替换显式令牌。
- **CODI**：自蒸馏策略，教师学习显式推理，学生学习隐式推理，同时对齐查询最后一个令牌的嵌入。
- **SoftCoT**：使用小型 LM 生成隐式推理，但未压缩令牌数量，仅训练线性层将小型 LM 的隐式推理映射到 LLM。

### 3.4 模型配置
- **目标 LLM**：Llama-2-7b-chat-hf、Mistral-7B-Instruct-v0.2
- **轻量生成器**：Sheared-LLaMA-1.3B（对应 Llama）、mistral-1.1b-testing（对应 Mistral）
- **隐式令牌数量**：训练时 5 个，推理时 1 个（确保公平比较，避免提供答案本身等干扰）
- **输出嵌入维度**：768
- **优化器**：AdamW，超参数经过调优
- **推理时最大答案令牌数**：30

## 4. 资源与算力

- 论文未明确说明具体使用的 GPU 型号、数量或训练时长。仅在附录 C 提到“所有实验在配备 NVIDIA H100 80GB GPU 的机器上运行，CUDA 12.4”。
- 未提及总训练时间或能耗等信息。由于资源细节不完整，无法评估算力充分性。

## 5. 实验数量与充分性

### 实验组数
- **主实验**：在 2 个 LLM × 5 个数据集共 10 个配置下，对比 5 个基线 + SemCoT，各运行 3 次取均值与标准差（表 1）。
- **消融实验**：3 种变体（去除语义对齐损失、去除句子变换器、使用原 LLM 替代轻量 LM）在 Llama-2 和 Mistral 上对全部 5 个数据集分别进行（图 3、图 6、图 7）。
- **超参数敏感性**：对 \( \lambda \)（0.1~0.9）和隐式令牌数量（1~5）在 SVAMP 上测试（图 4）；附录 D.2 扩展到全部数据集和 LLM（图 8、图 9）。
- **案例分析**：对 SemCoT 和 COCONUT 在 3 个 SVAMP 样本的 20 个语义等价变体上做 PCA 可视化（图 5）；附录 D.3 扩展到 SoftCoT、CODI 等（图 10~17）。

### 充分性与公平性
- **充分性**：覆盖多种推理类型（算术、常识、符号），在两种不同架构的 LLM 上验证，消融和超参数分析较全面，可视化也提供了语义对齐的定性证据。
- **公平性**：各方法使用相同的隐式令牌数量（推理时为 1），统一训练轮次（3 次独立运行取均值和标准差），但未提及是否使用相同的数据分割或种子，可能引入随机性。基线方法按照原论文实现，但部分方法（如 Pause 仅微调阶段）可能存在未完全复现原意的情况。

## 6. 论文的主要结论与发现

1. **效率与有效性兼得**：SemCoT 在几乎所有数据集和 LLM 上均取得最高准确率，同时推理时间接近最快（与 SoftCoT 相当或略快）。相比第二名基线，在部分数据集上准确率提升可达 10% 以上。
2. **语义对齐损失至关重要**：消融实验显示，去除语义对齐损失（SemCoT-NSA）导致准确率大幅下降，表明语义对齐是保持 CoT 性能的关键。
3. **轻量 LM 优于微调原 LLM**：使用轻量 LM 生成隐式推理（SemCoT）比在原 LLM 上微调（SemCoT-NLL）效果更好，原因可能是 LLM 微调导致灾难性遗忘。
4. **隐式令牌越少效果越好**：推理时使用 1 个隐式令牌比使用更多令牌准确率更高，说明隐式推理可以紧凑地编码必要信息。
5. **语义对齐可视化验证**：PCA 显示 SemCoT 生成的隐式推理对于语义等价的查询变体高度聚类，而基线（COCONUT 等）则分散，证明 SemCoT 成功实现了语义对齐。

## 7. 优点

- **问题识别清晰**：明确指出现有隐式 CoT 的两个根本缺陷（语义对齐、单令牌生成成本），并针对性地提出解决方案。
- **方法创新**：提出定制化句子变换器评估 LLM 嵌入空间的语义对齐，避免了直接向量距离的缺陷；利用剪枝/蒸馏轻量 LM 加速生成，并设计线性投影层对齐空间，思路新颖。
- **实验全面**：涵盖多个推理领域、两种不同架构的 LLM，消融和超参数分析细致，案例分析直观验证了语义对齐。
- **开源代码**：提供 GitHub 仓库，便于复现和进一步研究。
- **应用价值**：显著加速 CoT 推理，使先进推理能力更易部署于资源受限或实时场景。

## 8. 不足与局限

- **计算成本前置**：定制句子变换器需要额外的训练开销，对资源有限的环境可能不友好。
- **评估范围有限**：仅测试算术、常识、符号推理，未涉及更专业的长链推理（如法律、医疗）或超长推理任务，泛化性存疑。
- **架构适应性**：仅验证了 Llama-2 和 Mistral 两种架构，其他模型族（如 GPT、PaLM、Gemini）的表现未知。
- **可解释性缺失**：隐式推理为不可读的嵌入，降低了推理过程的人为可解释性，不利于调试和信任。
- **超参数依赖**：训练时使用 5 个隐式令牌，推理时用 1 个，这种不对称设置可能对某些方法不公平（尤其 SoftCoT 原本未压缩令牌数）。
- **资源报告不充分**：未提供具体训练时间、GPU 数量、总能耗等，影响可复现性和效率评估的全面性。
- **潜在偏差风险**：生成语义等价推理的数据由 GPT-4o-mini 产生，可能引入该模型的偏差或错误；对比学习中负样本仅来自同批次，可能不够多样。

（完）
