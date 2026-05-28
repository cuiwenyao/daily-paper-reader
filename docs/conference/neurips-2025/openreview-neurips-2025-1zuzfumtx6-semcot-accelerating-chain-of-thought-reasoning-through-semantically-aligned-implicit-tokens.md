---
title: "SemCoT: Accelerating Chain-of-Thought Reasoning through Semantically-Aligned Implicit Tokens"
title_zh: SemCoT：通过语义对齐的隐式token加速链式推理
authors: "Yinhan He, Wendy Zheng, Yaochen Zhu, Zaiyi Zheng, Lin Su, Sriram Vasudevan, Qi Guo, Liangjie Hong, Jundong Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1ZuzFUMtx6"
tags: ["query:ns-xai"]
score: 4.0
evidence: 语义对齐的隐式token加速链式推理
tldr: 针对链式推理冗长问题，该论文提出语义对齐的隐式推理方法，将推理步骤编码为隐藏嵌入。通过保持隐式表示与自然语言语义对齐，在加速推理的同时保持准确性，实验证明在多个推理任务上有效。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 916, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1427, \"height\": 788, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1427, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 767, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1428, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1431, \"height\": 796, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1453, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1zuzfumtx6/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1435, \"height\": 778, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 885, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1468, \"height\": 2049, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1065, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1zuzfumtx6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1514, \"height\": 2080, \"label\": \"Table\"}]"
motivation: 显式CoT推理冗长影响效率。
method: 使用隐式token编码推理步骤并保持语义对齐。
result: 在加速推理的同时保持准确性。
conclusion: 为高效CoT推理提供了新方案。
---

## Abstract
Chain-of-Thought (CoT) enhances the performance of Large Language Models (LLMs) on reasoning tasks by encouraging step-by-step solutions. However, the verbosity of CoT reasoning hinders its mass deployment in efficiency-critical applications. Recently, implicit CoT approaches have emerged, which encode reasoning steps within LLM's hidden embeddings (termed ``implicit reasoning'') rather than explicit tokens. This approach accelerates CoT reasoning by reducing the reasoning length and bypassing some LLM components. However, existing implicit CoT methods face two significant challenges: (1) they fail to preserve the semantic alignment between the implicit reasoning (when transformed to natural language) and the ground-truth reasoning, resulting in a significant CoT performance degradation, and (2) they focus on reducing the length of the implicit reasoning; however, they neglect the considerable time cost for an LLM to generate one individual implicit reasoning token. To tackle these challenges, we propose a novel semantically-aligned implicit CoT framework termed **SemCoT**. In particular, for the first challenge, we design a contrastively trained sentence transformer that evaluates semantic alignment between implicit and explicit reasoning, which is used to enforce semantic preservation during implicit reasoning optimization. To address the second challenge, we introduce an efficient implicit reasoning generator by finetuning a lightweight language model using knowledge distillation. This generator is guided by our sentence transformer to distill ground-truth reasoning into semantically aligned implicit reasoning, while also optimizing for accuracy. SemCoT is the first approach that enhances CoT efficiency by jointly optimizing token-level generation speed and preserving semantic alignment with ground-truth reasoning. Extensive experiments demonstrate the superior performance of SemCoT compared to state-of-the-art methods in both efficiency and effectiveness. Our code can be found at https://github.com/YinhanHe123/SemCoT/.

---

## 论文详细总结（自动生成）

# 论文总结：SemCoT：通过语义对齐的隐式token加速链式推理

## 1. 论文的核心问题与整体含义（研究动机和背景）

链式推理（Chain-of-Thought, CoT）通过鼓励大语言模型（LLM）生成逐步推理过程来提升复杂推理任务（如数学、常识、符号推理）的性能。然而，显式CoT会产生冗长的推理文本（例如，GPT-4o解决一个小学数学问题可能生成约500个token，耗时21秒以上），严重限制了其在效率敏感场景（如实时应用、移动设备）中的部署。近期出现的隐式CoT方法试图将推理步骤编码为LLM隐藏层中的隐式嵌入（implicit tokens），从而缩短推理长度并跳过部分LLM组件（如unembedding层和tokenization）。但现有方法存在两大显著缺陷：
- **语义对齐缺失**：隐式推理与真实推理（自然语言）之间难以保持语义一致，导致性能大幅下降。
- **单token生成效率低下**：仅关注减少推理token数量，却忽略了生成每个隐式token时LLM本身的高计算成本（如DeepSeek-R1生成一个token约需0.1秒），这对大规模模型尤为突出。

本文提出**SemCoT**框架，旨在通过联合优化token级生成速度和保持与真实推理的语义对齐，实现高效的隐式CoT。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
SemCoT采用两阶段流程：
1. **语义对齐评估**：训练一个定制化的句子变换器（Sentence Transformer），以对比学习方式衡量隐式推理与真实推理之间的语义相似度。
2. **高效隐式推理生成**：通过知识蒸馏微调一个轻量级语言模型（Lightweight LM）作为隐式推理生成器，同时优化语义对齐和答案准确性。

### 关键技术细节

#### 阶段一：隐式 vs. 真实推理语义对齐评估
- **定制句子变换器**：提取LLM中间五层（冻住）作为骨干，添加池化层和线性投影层，将推理文本映射到768维语义嵌入空间。
- **训练数据**：使用GPT-4o-mini将原始推理压缩为“语义对齐的简洁推理”作为正样本对。
- **损失函数**：对比学习损失（InfoNCE）最大化正样本对余弦相似度，最小化负样本对相似度：
  \[
  \mathcal{L}_{sim} = -\frac{1}{|\mathcal{G}|}\sum_{(R_i,S_i)\in\mathcal{G}} \log\frac{\exp(\text{sim}(e_{R_i},e_{S_i})/\tau)}{\sum_{j=1}^{|\mathcal{G}|}\exp(\text{sim}(e_{R_i},e_{S_j})/\tau)}
  \]

#### 阶段二：高效隐式推理生成
- **轻量级生成器**：基于从原始LLM剪枝/蒸馏的轻量LM（如Sheared-LLaMA-1.3B对应LLaMA-2-7B，mistral-1.1b-testing对应Mistral-7B），在其最后一层隐藏嵌入后加线性投影层，映射到LLM的嵌入空间。
- **生成过程**：在查询后追加k个特殊token `<CoT>`，轻量LM处理这些token，收集其最后一层隐藏嵌入，经线性投影得到隐式推理Z。
- **训练目标**：联合优化两个损失：
  - **预测损失** \(\mathcal{L}_{pred}\)：LLM使用隐式推理生成答案的交叉熵损失。
  - **语义对齐损失** \(\mathcal{L}_{sem}\)：利用已训练好的句子变换器计算隐式推理Z与真实推理嵌入之间的余弦相似度（最大化）。
  - 总损失：\(\mathcal{L}_{total} = \lambda \mathcal{L}_{sem} + (1-\lambda)\mathcal{L}_{pred}\)。
- **推理阶段**：将查询与k个`<CoT>` token一起输入轻量生成器，获得隐式推理后拼接至查询嵌入，送入LLM生成最终答案。

## 3. 实验设计

### 数据集与场景
使用五个代表性数据集，覆盖三个语义域：
- **数学推理**：GSM8K（7500/1000）、SVAMP（700/300）、MultiArith（420/180）
- **常识推理**：CommonsenseQA（9741/1140）
- **符号推理**：CoinFlip（20000/3330）

### 对比方法（benchmark）
- **原始CoT**（显式推理，作为性能上界，但未在效率对比表中列出）
- **隐式CoT基线**：Pause（用相同隐式token替代）、ICoT-SI（渐进编码）、COCONUT（渐进融合）、SoftCoT（小型LM生成隐式token）、CODI（自蒸馏）。所有基线均使用一个隐式推理token进行评估。

### 评估指标
- **有效性**：答案准确率（Accuracy）
- **效率**：平均推理时间（wall-clock time），单位为秒。

## 4. 资源与算力

论文在**附录C**中说明：所有实验在多个配备NVIDIA H100 80GB GPU的机器上运行，CUDA 12.4。未明确报告具体GPU数量、训练总时长或能耗。作者提到训练句子变换器和隐式推理生成器均使用AdamW优化器，但未给出训练步数或epochs。总体而言，算力细节较模糊。

## 5. 实验数量与充分性

论文进行了多组实验，总体充分：
- **主实验**（表1）：在2个LLM（LLaMA-2-7B-chat、Mistral-7B-Instruct） × 5个数据集上，对比5个基线方法，重复3次取均值与标准差。
- **消融实验**（图3、图6、图7）：在3个变体（移除语义对齐损失、用余弦相似度替代、用原始LLM微调替代轻量LM）上进行，覆盖所有数据集和LLM。
- **参数敏感性**（图4、图8、图9）：考察λ（0.1-0.9）和隐式token数量（1-5）对性能的影响，在多个数据集上验证。
- **案例研究**（图5、图10-17）：在多个数据集上分析隐式推理的语义聚类效果，与COCONUT、SoftCoT、CODI等对比。

**公平性**：实验设置合理，保证所有方法使用相同隐式token数量（训练5个，测试1个），时间测量采用平均wall-clock time。但基线方法的超参数调优是否充分未详细说明，可能存在潜在不公平。

## 6. 论文的主要结论与发现

1. **SemCoT在几乎所有数据集上取得了最佳准确率**（表1），同时推理时间接近最快（仅略慢于SoftCoT，但准确率显著更高）。
2. **消融实验验证各组件贡献**：移除语义对齐损失导致准确率下降5%-50%以上；用简单余弦相似度替代定制句子变换器也造成性能损失；用原始LLM微调（LoRA）替代轻量LM反而效果更差（可能因灾难性遗忘）。
3. **参数敏感性**：λ=0.5时出现异常波动，表明语义对齐与预测准确需谨慎平衡；隐式token数量增加（1→5）时准确率下降，说明更少的token足以编码推理语义。
4. **案例研究**：SemCoT生成的隐式推理对语义等价的查询变体聚类更紧凑，证明其成功保持了语义对齐。

## 7. 优点

- **问题明确**：精准识别出隐式CoT的两个关键瓶颈（语义对齐缺失、单token生成效率），并针对性地提出解决方案。
- **方法创新**：首次联合优化token级速度与语义对齐；定制句子变换器解决了LLM嵌入空间与自然语言语义可比性的难题；利用轻量LM生成隐式推理既降低计算成本又避免灾难性遗忘。
- **实验全面**：覆盖多种推理类型、多个LLM和多个基线，消融与参数分析完整，案例研究直观展示语义对齐效果。
- **效率与效果俱佳**：在保持高准确率的同时将推理时间缩短至1秒左右，相比原始CoT（可能十几秒）提升显著。

## 8. 不足与局限

- **训练开销**：定制句子变换器需要额外训练和预处理（使用GPT-4o-mini生成压缩推理），部署前有一定成本。
- **实验覆盖有限**：仅测试了两种7B规模的LLM，未扩展到更大规模（如Llama-3-70B）或更小规模（如移动端模型）；仅覆盖数学、常识、符号推理，未涉及复杂多步推理（如GPT-4o的o1类）或开放域任务。
- **效率度量粗糙**：仅用wall-clock time，未考虑FLOPs或内存消耗；轻量LM的推理时间可能依赖硬件，结果迁移性需验证。
- **隐式推理可解释性差**：隐式token作为嵌入向量不直接可读，降低了推理过程的透明度，可能影响可信赖应用。
- **泛化风险**：方法依赖轻量LM与原始LLM的嵌入空间对齐假设（线性可映射），跨架构（如不同tokenizer或预训练语料）的表现未知。
- **公平性存疑**：基线方法的超参数调优是否充分未详述，可能存在对比偏差。

（完）
