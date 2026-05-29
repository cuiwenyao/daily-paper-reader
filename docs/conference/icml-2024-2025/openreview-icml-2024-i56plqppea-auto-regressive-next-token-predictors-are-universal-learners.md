---
title: Auto-Regressive Next-Token Predictors are Universal Learners
title_zh: 自回归下一词元预测器是通用学习器
authors: eran malach
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=i56plqPpEa"
tags: ["query:ns-xai"]
score: 7.0
evidence: 理论框架表明思维链使自回归模型能够逼近任意图灵可计算函数
tldr: 该工作从理论上证明即使简单的线性下一词元预测器，通过思维链训练也能逼近任意图灵机可计算的函数。引入“长度复杂度”衡量思维链序列所需的中间词元数量，为理解大语言模型的推理能力提供了理论基石。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-i56plqppea/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 708, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-i56plqppea/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-i56plqppea/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1676, \"height\": 398, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-i56plqppea/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 784, \"height\": 724, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-i56plqppea/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 902, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-i56plqppea/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1674, \"height\": 901, \"label\": \"Table\"}]"
motivation: 理解自回归模型在简单下一词元预测任务中为何能涌现推理能力。
method: 提出长度复杂度概念，分析思维链序列所需中间词元数。
result: 证明了线性模型通过思维链可实现通用计算。
conclusion: 为大型语言模型的推理能力提供了理论解释。
---

## Abstract
Large language models display remarkable capabilities in logical and mathematical reasoning, allowing them to solve complex tasks. Interestingly, these abilities emerge in networks trained on the simple task of next-token prediction. In this work, we present a theoretical framework for studying auto-regressive next-token predictors. We demonstrate that even simple models such as linear next-token predictors, trained on Chain-of-Thought (CoT) data, can approximate any function efficiently computed by a Turing machine. We introduce a new complexity measure---length complexity---which measures the number of intermediate tokens in a CoT sequence required to approximate some target function, and analyze the interplay between length complexity and other notions of complexity. Finally, we show experimentally that simple next-token predictors, such as linear networks and shallow Multi-Layer Perceptrons (MLPs), display non-trivial performance on text generation and arithmetic tasks. Our results demonstrate that the power of today's LLMs can be attributed, to a great extent, to the auto-regressive next-token training scheme, and not necessarily to a particular choice of architecture.

---

## 论文详细总结（自动生成）

# 自回归下一词元预测器是通用学习器：详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLMs）在逻辑推理和数学任务上展现出惊人能力，但这些能力仅通过简单的“下一词元预测（next-token prediction）”目标训练而涌现。作者质疑：这些模型仅仅是“高级自动补全”系统，还是真正在执行新型逻辑推理？论文旨在从理论层面解释自回归训练范式（尤其是结合思维链 CoT）为何能赋予模型强大的计算能力。
- **整体含义**：论文证明，即使是极为简单的模型（如线性下一词元预测器），只要在合适的思维链数据上训练，就能逼近任意图灵机可计算的函数。这一结果暗示：当今 LLMs 的强大能力很大程度上归功于自回归下一词元训练方案，而非特定架构（如 Transformer）。同时，论文引入新的复杂度度量——长度复杂度（length complexity），用于衡量思维链所需中间词元的数量，揭示了学习复杂度与思维链长度之间的权衡关系。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 区分“经典监督学习”与“自回归学习（AR learning）”。在经典监督学习中，学习者仅获得输入-标签对，无法访问内部计算；而在自回归学习中，通过思维链（CoT），中间计算步骤同时作为输入和标签出现，极大简化了学习任务。
- 定义 **AR可学习性（AR Learnability）**：若存在一个算法，能从有限样本中以高概率找到下一词元预测器，且预测错误率低于某个阈值，则称该类是 AR 可学习的。
- 关键定理（非正式）：对于任意可由图灵机有效计算的函数 \( f \)，存在一个数据集 \( D \)，使得在 \( D \) 上训练一个（线性）下一词元预测器，能逼近 \( f \)。

### 关键技术细节
- **线性 AR 假设类**：定义词典 \( D \)，嵌入函数 \( \psi \)，对于每个时间步 \( t \)，线性预测器 \( h_W(x, z) = \arg\max_{d \in D} \langle W_d, \psi([x, z]) \rangle \)。该类可通过 SGD 等算法高效学习。
- **线性阈值电路的逼近**：证明线性 AR 函数可以计算任意线性阈值电路。由于任何图灵可计算函数都能由多项式大小的线性阈值电路实现，因此线性 AR 函数可以计算任意图灵可计算函数。
- **长度复杂度**：定义为实现某个函数类所需的最少中间词元数。论文以奇偶学习问题（parity learning）为例，展示不同假设类对长度复杂度的影响。例如，线性 AR 模型可以用 \( O(\log n) \) 的中间词元计算任意奇偶函数；而使用更复杂的假设类（如 \( k \) 阶奇偶类）可将长度复杂度降至 \( \Theta(n/k) \)，但会增加样本/计算复杂度。
- **理论证明结构**：将 AR 学习分解为多个时间步的 PAC 学习问题，证明若每个子类是 PAC 可学习的，则整体 AR 类也是可学习的。然后通过构建线性阈值电路的模拟，证明线性 AR 模型能实现通用计算。

## 3. 实验设计：数据集、场景、基准与方法对比

### 数据集与场景
- **TinyStories 文本生成**：使用 Eldan & Li (2023) 的 TinyStories 数据集（简单词汇的短故事）。训练一个线性模型，上下文长度 64，嵌入维度 256，参数量约 162M。评估生成文本的语法、创造性、一致性和情节合理性。
- **4 位数乘法任务**：训练一个浅层 MLP（无注意力机制），参数量 775M。使用定制分词（单数字、乘号、加号、等号，以及两位数字乘积的标记），展开完整乘法算法（思维链序列长度 307）。数据集：所有 4 位数对随机分割，75% 训练，25% 验证，训练 100M 序列（307M 词元）。

### 基准与对比方法
- TinyStories：对比 GPT-4、小型 Transformer（TS-33M、TS-1M）的评分。使用 GPT-4 对 50 个生成样例打分（语法、创造性、一致性、情节），同时用 LanguageTool 检查语法错误。
- 乘法任务：对比 GPT-3.5、GPT-4 以及 Goat-7B（一个微调的 Transformer，参数量 7B）。评估指标：整数精确匹配准确率和逐位准确率。

## 4. 资源与算力

- **TinyStories 线性模型**：在单张 A100 GPU 上训练 5.5 小时。
- **乘法 MLP 模型**：在单张 A100 GPU 上训练 17 小时，处理 100M 序列（307M 词元）。
- 论文明确说明了 GPU 型号、数量和训练时长，算力信息充分。

## 5. 实验数量与充分性

- **数量**：
  - TinyStories 实验：对 50 个提示生成故事，由 GPT-4 按四个维度各评分（每维度 1-10），并报告语法错误率（5 次生成取平均）。
  - 乘法实验：使用 1000 个验证样本评估精确匹配和逐位准确率，同时对比多个模型。
- **充分性**：
  - TinyStories 实验虽规模不大，但足以证明线性模型能产生语法基本正确的文本，与 GPT-4 评分对比提供了定性参考。但未进行消融实验（如不同嵌入维度、不同上下文长度）。
  - 乘法实验对比了 GPT-3.5、GPT-4 和 Goat-7B，结果清晰表明 MLP 可达与大型 Transformer 相当的准确率（96.9% 精确匹配）。但未对该 MLP 本身进行消融（如去掉 ReLU、改变深度）。总体而言，实验设计针对理论验证目标足够，但并非全面系统性的消融研究。

## 6. 论文的主要结论与发现

- 线性下一词元预测器结合思维链（CoT）训练，可以逼近任意图灵可计算函数，且该类是高效可学习的（通过 PAC 学习的子类归约）。
- 引入长度复杂度概念，揭示了样本/计算复杂度与思维链长度之间的权衡：增加思维链长度可降低样本复杂度，反之亦然。奇偶学习问题中，线性 AR 模型只需 \( O(\log n) \) 中间词元，远优于先前工作的 \( O(n) \)。
- 实验验证：线性模型在 TinyStories 上能生成连贯故事（虽不如大型 Transformer），浅层 MLP 在 4 位数乘法任务上持平甚至超越 GPT-4 和 Goat-7B，证明架构并非关键因素，关键在于自回归训练和高质量的思维链数据。

## 7. 优点（方法或实验设计亮点）

- **理论贡献**：为自回归学习提供了严格的 PAC 学习框架，首次证明线性 AR 模型的通用计算能力，并引入长度复杂度这一新颖概念，开启了新的理论研究维度。
- **实验结果具有说服力**：用极为简单的模型（线性网络、无注意力的 MLP）在文本生成和算术任务上取得与大型模型竞争的性能，强化了“训练范式比架构更重要”的论点。
- **理论实验结合紧密**：理论结果（线性 AR 可计算任意函数）在实验中通过乘法任务得到直接验证（MLP 学习乘法算法），形成闭环。
- **对变体的讨论**：不仅分析了线性类，还扩展到更复杂的假设类（如 k 阶奇偶类），展示了不同复杂度度量间的权衡。

## 8. 不足与局限

- **实验覆盖有限**：仅验证了文本生成和 4 位数乘法两个场景，未在更广泛的任务（如推理、代码、翻译）上测试简单的非 Transformer 模型。
- **消融实验不足**：未系统研究不同模型大小、不同 CoT 长度、不同分词方案对性能的影响，也未与同类架构（如线性变压器、RNN 等）进行对比。
- **训练数据假设强**：理论需要“合适的思维链数据集”，现实中获取此类高质量长链数据可能困难且昂贵。论文未讨论数据标注成本或自动生成方法的可行性。
- **长度复杂度的实际测量**：长度复杂度在理论中定义明确，但在实验中并未直接测量或验证（如奇偶学习实验未做），仅理论分析。
- **架构局限性**：虽然线性 AR 模型理论上通用，但实际训练可能收敛缓慢或需要极大数据集。实验中 MLP 虽小但训练 17 小时，参数量 775M 对简单模型而言并不算小。
- **潜在偏差风险**：TinyStories 的 GPT-4 评估可能存在偏见（GPT-4 可能偏好与自身生成风格相近的内容）；乘法任务使用定制分词可能引入先验知识，其他模型（GPT）未使用相同分词，对比不完全公平。

（完）
