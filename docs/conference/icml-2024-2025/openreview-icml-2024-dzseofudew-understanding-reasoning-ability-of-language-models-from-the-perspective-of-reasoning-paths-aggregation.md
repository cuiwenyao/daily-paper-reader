---
title: Understanding Reasoning Ability of Language Models From the Perspective of Reasoning Paths Aggregation
title_zh: 从推理路径聚合视角理解语言模型的推理能力
authors: "Xinyi Wang, Alfonso Amayuelas, Kexun Zhang, Liangming Pan, Wenhu Chen, William Yang Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=dZsEOFUDew"
tags: ["query:ns-xai"]
score: 6.0
evidence: 通过路径聚合理解语言模型推理
tldr: 语言模型如何通过下一词预测获得推理能力仍不明确。本文提出推理路径聚合视角，将模型视为聚合预训练中观察到的间接推理路径，并通过知识图谱上的随机游走形式化。分析表明LM分布等价于相关随机游走路径的加权和，为理解推理涌现提供新解释。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1773, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 709, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 712, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1676, \"height\": 835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dzseofudew/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1679, \"height\": 782, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-dzseofudew/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-dzseofudew/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-dzseofudew/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 442, \"label\": \"Table\"}]"
motivation: 需要理解预训练语言模型如何获得推理能力。
method: 将推理路径形式化为知识图谱上的随机游走，分析路径聚合。
result: 发现LM分布与随机游走路径加权和相关，解释推理涌现。
conclusion: 推理路径聚合视角有效解释LM的推理能力来源。
---

## Abstract
Pre-trained language models (LMs) are able to perform complex reasoning without explicit fine-tuning. To understand how pre-training with a next-token prediction objective contributes to the emergence of such reasoning capability, we propose that we can view an LM as deriving new conclusions by aggregating indirect reasoning paths seen at pre-training time. We found this perspective effective in two important cases of reasoning: logic reasoning with knowledge graphs (KGs) and chain-of-thought (CoT) reasoning. More specifically, we formalize the reasoning paths as random walk paths on the knowledge/reasoning graphs. Analyses of learned LM distributions suggest that a weighted sum of relevant random walk path probabilities is a reasonable way to explain how LMs reason. Experiments and analysis on multiple KG and CoT datasets reveal the effect of training on random walk paths and suggest that augmenting unlabeled random walk reasoning paths can improve real-world multi-step reasoning performance.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：预训练语言模型（LMs）通过“下一个词预测”目标进行大规模预训练后，展现出强大的复杂推理能力（如逻辑推理、数学推理等），但其背后的机制尚不明确。本文试图解释这种推理能力是如何从预训练中涌现的。
- **整体含义**：作者提出一种“推理路径聚合”视角，认为LM在推理时实际上是在聚合预训练阶段观察到的间接推理路径（即文本中连接两个概念的多步论证）。通过将推理路径形式化为知识图或推理图上的随机游走路径，可以解释LM如何从已知事实推导出新结论。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- LM的推理能力可以理解为对预训练数据中随机游走路径的加权聚合。预训练语料可以被视为在概念/知识图上进行随机游走生成的自然语言序列，LM通过下一词预测目标隐式地学习了这种路径的权重分布。

### 2.2 关键技术细节
- **逻辑推理场景（知识图谱推理）**：
  - 将知识图谱中的三元组（实体1，关系，实体2）转化为三词句子。
  - 在知识图谱上执行均匀随机游走，生成预训练语料（最大路径长度 Lmax）。
  - 训练一个从头初始化的GPT-2小模型，使用下一词预测损失。
  - 测试时，给定(e1, r)预测e2，将LM输出分布与路径排序算法（PRA）的加权聚合分布进行KL散度对比。
  - 加权聚合分布定义为：对每条逻辑规则h（例如[e1, r1, e3; e3, r2, e2]），计算规则概率P(e2|e1, h)，并乘以可学习的权重w_r(h)，然后对所有规则求和取softmax。
  - 通过KL散度上界证明：KL[Pw, PLM] ≤ KL[Pw(h|r), PLM(h|e1, r)]，说明KL散度反映了LM学习逻辑规则重要性的程度。

- **思维链推理场景（数学推理等）**：
  - 利用已有CoT训练数据（问题+多步推理步骤+答案），构建潜在推理图：将每个推理步骤的隐藏状态（通过LM编码后平均得到）进行K-means聚类，聚类中心作为图的节点。
  - 在推理图上执行随机游走（算法1）：随机选择当前节点中的某个CoT步骤，然后随机选择该步骤后的连续m个步骤加入路径，直到路径长度达到Lmax。
  - 先用生成的随机游走路径对预训练LM进行继续预训练（M步），然后再用原始标注数据进行监督微调（SFT，N-M步）。

## 3. 实验设计：使用的数据集、Benchmark、对比方法

### 3.1 逻辑推理实验
- **数据集**：Countries（2个关系，227实体，使用最难版本S3）、UMLS（49关系，135实体）、Kinship、NELL-995、FB15K-237（后三个仅用于准确率分析）。
- **Benchmark**：测试集为未见过的三元组（e1, r, e2），评估LM预测e2的准确率（argmax）。
- **对比方法**：
  - 加权聚合分布Pw（可学习规则权重，通过逻辑回归优化）。
  - 未加权聚合分布Ps（所有规则权重为1）。
  - 参考分布P*（正确答案均匀分布）、均匀分布Pu用于锚定KL值。

### 3.2 思维链推理实验
- **数据集**：三个数学推理数据集（GSM8K、AQUA、SVAMP），一个多跳QA数据集StrategyQA，一个逻辑推理数据集LogicalDeduction（使用GPT-4生成CoT）。
- **Benchmark**：测试准确率。
- **对比方法**：监督微调（SFT）基线（相同总步数N=2500）。在多个开源LM上评估：Gemma 2B、Yi 6B、Llama 2 (7B, 13B)。
- **消融实验**：
  - 随机游走训练步数M（0, 200, 500, 1000）。
  - 聚类节点数K（0, 10, 50, 100, 200）。
  - 随机游走路径长度Lmax对准确率的影响。

## 4. 资源与算力

- **逻辑推理**：训练一个随机初始化的GPT-2（124M参数），使用一个24G Titan GPU，batch size 16，学习率5e-4，AdamW优化器。未明确说明训练时长。
- **思维链推理**：使用LoRA参数高效微调（8 bits），部署在40G A100 GPU上，batch size 16，学习率2e-4，AdamW优化器。总训练步数2500步（其中M=500随机游走步，2000步SFT）。未明确说明模型总训练时长，但标注了“计算资源限制”。

## 5. 实验数量与充分性

- **逻辑推理**：在5个KG数据集上测试了LM准确率随预训练路径长度（1~20）的变化；在Countries和UMLS上计算了KL散度热力图（不同Lmax和Nmax组合）；比较了LM、加权聚合、未加权聚合三种方法。
- **思维链推理**：在5个数据集上评估了4个不同规模的LM（共20组对比实验），且每个数据集都报告了准确率。包含消融实验（M、K的6组+路径长度5组）以及潜在推理图模式分析。
- **充分性**：实验覆盖了逻辑推理和数学/多跳/逻辑推理两大类场景，多种模型规模（2B~13B），并进行了消融。但依赖LoRA微调，未在更大规模或全参数训练下验证；KL散度分析仅限于两个较小KG；聚类K值选择（100）可能仅对小数据集有效。

## 6. 论文的主要结论与发现

1. **LM分布与加权随机游走聚合高度相似**：KL [Pw, PLM] 通常小于 KL [Ps, PLM]，说明LM隐式学习了不同逻辑规则的重要性权重。
2. **存在最佳预训练路径长度**：逻辑推理和CoT推理中，过长路径会引入噪声导致准确率下降，过短则无法提供足够推理信息。
3. **未标注随机游走路径可提升推理性能**：在5个CoT数据集上，随机游走继续预训练+微调一致优于纯监督微调（平均提升约2-4个百分点）。
4. **LM可泛化到更长推理长度**：在Countries上，即使预训练路径<3，LM仍能达成一定准确率。
5. **潜在推理图结构可解释**：聚类后发现的节点模式（如GSM8K中先计算基线量再除法/乘法，StrategyQA中先分解问题再比较）符合直觉。

## 7. 优点

- **理论清晰**：提供了一种形式化的概率解释（路径聚合）来理解LM推理涌现，连接了经典路径排序算法（PRA）与现代LM。
- **方法创新**：将随机游走思想从知识图谱推广到CoT文本，通过聚类构建潜在推理图并生成未标注训练数据，无需额外标注。
- **实验设计系统**：从简单可控的KG逻辑推理逐步过渡到复杂的CoT数学/多跳推理，验证了假设的普适性。
- **消融充分**：对随机游走步数、聚类数、路径长度均进行详细消融，揭示了最优设置。
- **开源代码**：提供代码仓库便于复现和扩展。

## 8. 不足与局限

- **实验规模有限**：逻辑推理使用小KG（Entities<250）；CoT推理仅使用小模型（2B~13B）和LoRA微调，未在大规模全参数预训练场景下验证。
- **数据集局限性**：仅测试数学、多跳QA和逻辑推理三类，未涵盖更广泛的常识推理、科学推理等。
- **潜在偏差风险**：随机游走方法本质上是对训练集中路径的上采样，可能放大原始数据中的噪声或偏差。
- **理论推导不足**：KL散度上界依赖“LM有效学习随机游走数据分布”的假设，但实际中LM可能学到更复杂的模式。
- **计算资源说明不充分**：未给出具体训练时间、GPU小时数等，影响可复制性。
- **应用限制**：聚类节点数K对结果敏感，且需要原始CoT数据中的步骤级切分，可能不适用于无CoT标注的语料。

（完）
