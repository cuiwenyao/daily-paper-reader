---
title: An Analysis for Reasoning Bias of Language Models with Small Initialization
title_zh: 小初始化下语言模型推理偏差的分析
authors: "Junjie Yao, Zhongwang Zhang, Zhi-Qin John Xu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4HQaMUYWAT"
tags: ["query:ns-xai"]
score: 4.0
evidence: 初始化尺度导致LLM推理偏差的分析
tldr: 本文研究参数初始化尺度对LLM训练行为的影响，发现小初始化尺度使模型偏向推理任务，大初始化尺度偏向记忆任务。通过实数据集和锚函数验证了这种推理偏差，并分析了嵌入空间和自注意力机制的作用。该发现为理解LLM推理能力提供新视角。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 837, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1722, \"height\": 639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1576, \"height\": 852, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1732, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1764, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1755, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 835, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1735, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1762, \"height\": 827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1653, \"height\": 2099, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1768, \"height\": 911, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1779, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1767, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1690, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1510, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4hqamuywat/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1596, \"height\": 1568, \"label\": \"Figure\"}]"
motivation: 参数初始化尺度对LLM任务偏好的影响尚不明确。
method: 通过控制初始化尺度并设计锚函数，分析模型在推理与记忆任务上的表现差异。
result: 小初始化促进推理任务偏好，大初始化促进记忆任务偏好。
conclusion: 初始化尺度是塑造LLM学习偏见的关键因素。
---

## Abstract
Transformer-based Large Language Models (LLMs) have revolutionized Natural Language Processing by demonstrating exceptional performance across diverse tasks. This study investigates the impact of the parameter initialization scale on the training behavior and task preferences of LLMs. We discover that smaller initialization scales encourage models to favor reasoning tasks, whereas larger initialization scales lead to a preference for memorization tasks. We validate this reasoning bias via real datasets and meticulously designed anchor functions. Further analysis of initial training dynamics suggests that specific model components, particularly the embedding space and self-attention mechanisms, play pivotal roles in shaping these learning biases. We provide a theoretical framework from the perspective of model training dynamics to explain these phenomena. Additionally, experiments on real-world language tasks corroborate our theoretical insights. This work enhances our understanding of how initialization strategies influence LLM performance on reasoning tasks and offers valuable guidelines for training models.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：参数初始化尺度如何影响语言模型（LLM）的训练行为与任务偏好？特别关注“小初始化”是否导致模型偏向推理任务，而“大初始化”偏向记忆任务。
- **背景**：LLM在自然语言处理中表现卓越，但其是否真正学习到逻辑规则还是仅模仿数据模式存在争议。已有研究表明小初始化会导致“神经元凝聚”现象，促进低复杂度拟合，从而可能使模型学习内在规则（推理）。但缺乏对Transformer结构下具体机制的理论分析。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：小初始化使得模型参数在早期处于“低秩”或“线性化”状态，嵌入空间和自注意力机制对推理任务（其标签分布有结构）比对记忆任务（标签随机）更敏感，导致推理任务损失下降更快。
- **关键技术细节**：
  - **合成任务设计**：使用“锚函数”（anchor function）构造包含推理和记忆两种映射的数据集。推理映射：标签为键与锚的连续加和；记忆映射：标签为键-锚对的随机采样。
  - **模型**：GPT-2（解码器Transformer，2层，1头），以及简化的Emb-MLP（嵌入层+2层MLP）。
  - **初始化尺度**：参数 \( W_{i,j} \sim \mathcal{N}(0, (d_1^{-\gamma})^2) \)，其中 \(\gamma>0.5\) 为小初始化（本文主要研究 \(\gamma=0.8\)），\(\gamma=0.3\) 为大初始化。
  - **理论分析**：
    - 导出嵌入向量梯度流的极限形式（Proposition 1、2、3），证明其依赖于标签分布 \(P_s\)。
    - 对于记忆锚点，\(P_s\) 为均匀分布；对于推理锚点，\(P_s\) 随锚点值偏移，导致嵌入向量更快分化。
    - 分析第一自注意力模块：小初始化下注意力矩阵接近平均算子，且 \(W^V\) 的主要奇异向量与推理锚点嵌入对齐，从而突出推理信息。
    - 给出嵌入空间结构的近似表达式（Theorem 1），与实验一致。

### 3. 实验设计：数据集 / 场景、基准、对比方法

- **合成数据集**：自构造的锚函数数据集（\(L=9\)，\(q=2\)，\(Z=\{21,...,120\}\)，\(A_{\text{mem}}=\{1,...,10\}\)，\(A_{\text{rsn}}=\{11,...,20\}\)，\(M=\{(11,13),(13,11)\}\)，共20万样本）。训练集 \(D_{\text{train}} = D_{\text{mem}} \cup D_{\text{rsn,train}}\)，测试集 \(D_{\text{rsn,test}}\) 仅含掩码组合。
- **真实语言任务**：PrOntoQA（推理问答，含思维链）与 TinyStories（儿童故事，记忆型）混合数据集，各5000序列，共1万样本。
- **基准/对比**：三种初始化尺度（\(\gamma=0.3,0.5,0.8\)）对比。评估指标：交叉熵损失、预测准确率；以及嵌入余弦相似度、注意力矩阵特性、\(\Delta L\)（TinyStories与PrOntoQA损失的相对差）。
- **额外消融**：移除层归一化、不同学习率（\(10^{-5}\)~\(5\times10^{-4}\)）等。

### 4. 资源与算力

- **未明确说明**：论文未提及GPU型号、数量、训练时长等具体算力信息。仅提到训练Transformer模型1000个epoch，batch size=100，Emb-MLP训练1000个epoch。GPT-2在真实任务上训练200个epoch。但未给出硬件细节。

### 5. 实验数量与充分性

- **实验组数**：
  - 合成数据：3种初始化尺度 × (Transformer + Emb-MLP) = 6组主要实验，每组记录损失、准确率、嵌入相似度等。
  - 真实语言任务：3种初始化尺度 × GPT-2，监测损失动态和嵌入空间。
  - 消融实验：移除LayerNorm、变化学习率、不同标签分布的记忆任务对比。
  - 理论验证：余弦相似度对比（实验 vs 理论公式）覆盖多个推理锚点。
- **充分性**：实验设计较为系统，从简化模型到完整Transformer，从合成数据到真实数据，并提供了理论预言与数值验证。但也存在局限（见后），如未在大规模模型上验证，且仅考察了GPT-2（小版本）。

### 6. 论文的主要结论与发现

- **主要结论**：小初始化尺度（\(\gamma>0.5\)）使语言模型在训练早期就表现出强烈的推理偏好，而大初始化（\(\gamma=0.3\)）则偏向纯粹的记忆化。
- **发现**：
  - 推理锚点的嵌入向量在早期具有层次结构（余弦相似度随数值差递减），而记忆锚点嵌入保持高相似度，难以区分。
  - 第一自注意力层在小初始化下近似为平均算子，且 \(W^V\) 的主要奇异向量捕获推理锚点信息，有助于后续信息传播。
  - 标签分布的结构差异是驱动嵌入分化的根本原因：推理标签随锚点偏移，记忆标签均匀随机。
  - 真实语言任务（PrOntoQA vs TinyStories）也观察到类似现象：小初始化下推理任务损失下降更快，嵌入区分度更高。

### 7. 优点：方法或实验设计上的亮点

- **创新性**：将初始化尺度与任务偏好（推理 vs 记忆）联系起来，从训练动力学角度给出理论解释，而非仅经验观察。
- **理论深度**：推导了嵌入向量的梯度流，证明了标签分布对嵌入结构的关键影响，并给出了近似解析形式（Theorem 1）。
- **实验设计**：巧妙使用锚函数构造可控的合成任务，隔离推理与记忆机制；同时用真实数据集验证，增强普适性。
- **机制分析**：细致拆解了Transformer各模块（嵌入层、第一/第二注意力层）在小初始化下的行为，逻辑清晰。

### 8. 不足与局限

- **实验覆盖**：模型规模较小（GPT-2，2层，嵌入维度200）；未验证在LLaMA、GPT-3等大模型上是否成立。结论在工程上可能受模型尺寸影响。
- **偏差风险**：合成任务过于理想化，真实语言任务中的“推理”与“记忆”界限模糊，实验中的推理偏好可能部分源于数据分布差异而非纯粹的能力。
- **理论假设**：部分证明假设 \(\sigma'(0)=1\) 且网络宽度趋于无穷，实际有限宽度下结论可能渐变；W^V的偏好现象仅给出特殊条件下的推导（Theorem 2），一般性有待加强。
- **应用限制**：论文未讨论小初始化是否会导致训练不稳定（如损失尖峰）或收敛慢；且仅对比了三种初始化尺度，未见对连续\(\gamma\)的扫描。
- **资源信息缺失**：未报告计算成本，不利于复现与工程应用评估。

（完）
