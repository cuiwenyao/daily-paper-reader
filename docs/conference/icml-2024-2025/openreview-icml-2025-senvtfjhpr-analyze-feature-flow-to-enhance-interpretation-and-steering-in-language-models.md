---
title: Analyze Feature Flow to Enhance Interpretation and Steering in Language Models
title_zh: 分析特征流以增强语言模型的解释和引导
authors: "Daniil Laptev, Nikita Balagansky, Yaroslav Aksenov, Daniil Gavrilov"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=SENVTfjHPr"
tags: ["query:ns-xai"]
score: 7.0
evidence: 特征流分析用于大模型可解释性和引导
tldr: 本文提出一种新方法，利用余弦相似度无数据地映射稀疏自编码器发现的特征在大语言模型各层的流动，生成特征演化流图，实现细粒度可解释性。并展示如何通过放大或抑制选定特征来直接引导模型行为，实现主题控制。为增强大模型可解释性和可控性提供了实用工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1253, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1583, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 842, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 841, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 647, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 842, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 834, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 841, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1598, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 855, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1737, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1665, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1752, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1500, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1319, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1686, \"height\": 1270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1406, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1398, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1306, \"height\": 264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1510, \"height\": 1040, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-senvtfjhpr/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1405, \"height\": 689, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-senvtfjhpr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 736, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-senvtfjhpr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-senvtfjhpr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1757, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-senvtfjhpr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1326, \"height\": 540, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-senvtfjhpr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1720, \"height\": 1853, \"label\": \"Table\"}]"
motivation: 大模型内部特征跨层变化难以追踪，限制了解释和引导能力。
method: 使用余弦相似度无数据地跨层映射稀疏自编码器特征，得到特征流图。
result: 成功生成特征演化图，并通过特征放大/抑制实现模型行为引导。
conclusion: 跨层特征映射为提升大模型可解释性和可控性提供了有效途径。
---

## Abstract
We introduce a new approach to systematically map features discovered by sparse autoencoder across consecutive layers of large language models, extending earlier work that examined inter-layer feature links. By using a data-free cosine similarity technique, we trace how specific features persist, transform, or first appear at each stage. This method yields granular flow graphs of feature evolution, enabling fine-grained interpretability and mechanistic insights into model computations. Crucially, we demonstrate how these cross-layer feature maps facilitate direct steering of model behavior by amplifying or suppressing chosen features, achieving targeted thematic control in text generation. Together, our findings highlight the utility of a causal, cross-layer interpretability framework that not only clarifies how features develop through forward passes but also provides new means for transparent manipulation of large language models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLMs）内部的特征如何跨层演化、传播、转换？如何利用这种跨层特征流动实现模型的细粒度解释和可控生成？
- **背景与动机**：现有稀疏自编码器（SAE）方法能够从单层隐藏状态中提取可解释的线性特征（monosemantic features），但多数工作仅分析单层或残差流，忽视了特征在多层之间的演化过程。理解特征如何从低层（如词法）演变为高层（如语义概念）对于模型可解释性和精确引导至关重要。
- **整体含义**：本文提出一种无数据的余弦相似度方法，跨层匹配SAE特征，构建特征流图（flow graph），揭示特征的“出生”、“传播”、“转换”模式。并首次展示如何利用这些流图进行多层的模型行为引导（steering），实现对生成内容主题的有意控制。

## 2. 论文提出的方法论

### 核心思想
- 利用预训练的SAE解码器权重（即特征嵌入向量），计算连续层之间对应模块（残差流、MLP输出、注意力输出）的余弦相似度，找到特征之间的对应关系。
- 通过向前/向后逐层匹配，构建特征从初始层到最终层的演化路径，形成流图。
- 基于流图，在多个层上同时放大或抑制相关特征，实现更鲁棒的模型引导。

### 关键技术细节
- **特征匹配**：给定位置A的特征嵌入f（解码器矩阵的列向量），在位置B的SAE解码器矩阵中找到余弦相似度最大的列作为匹配特征。
  - 定义映射 \( T_{A \to B} = I_{x>0}(\text{top}_k(W_{\text{dec}}^{(A)\top} W_{\text{dec}}^{(B)})) \)，通常取k=1（一对一匹配）。
- **单层溯源**：对于残差流特征 \( R_L \)，计算其与前一层残差 \( R_{L-1} \)、MLP输出M、注意力输出A的相似度 \( s(R), s(M), s(A) \)，根据值高低判断特征来源：
  - A) 高 \( s(R) \) 且低 \( s(M), s(A) \)：特征从上一残差流直接传播。
  - B) 高 \( s(R) \) 且高 \( s(M) \) 或 \( s(A) \)：特征被模块处理过。
  - C) 低 \( s(R) \) 但高 \( s(M) \) 或 \( s(A) \)：特征由模块新生成（newborn）。
  - D) 全部低：无法解释。
- **长程流图**：逐层短程匹配并组合，得到跨多层的演化路径。
- **模型引导**：通过修改隐藏状态来放大或抑制特征： \( h \leftarrow h + (r-1)(a \cdot V^\top) \)，其中r为缩放系数，a为特征激活强度，V为特征嵌入矩阵。
  - 去激活：r=0（移除特征）。
  - 激活：r>1（放大特征）。
  - 多层引导：在流图涉及的所有层上同时施加小扰动（线性/指数衰减缩放），避免单层大扰动破坏分布。

### 算法流程（文字描述）
1. 选定一个目标特征（如第24层残差中的某个特征）。
2. 后向匹配：计算该特征与前一残差层、MLP、注意力的余弦相似度，找到最高相似度的前驱特征。
3. 若前驱特征存在，则继续向前追溯，直到初始层。
4. 将所有匹配路径组合成有向图（流图），节点为SAE特征，边表示余弦相似度超过阈值。
5. 在引导时，根据流图选择多个层的相关特征，同时施加缩放操作。

## 3. 实验设计

### 数据集
- **FineWeb**：通用英语文本。
- **TinyStories**：短篇合成故事（简单语言）。
- **AutoMathText**：数学相关文本。
- **PythonGithubCode**：纯Python代码（分布偏移）。
- 每个数据集随机采样250个样本，每个样本随机选5个token（除BOS外）。

### 基准模型与SAE
- 主模型：**Gemma 2 2B**。
- SAE：**Gemma Scope**（JumpReLU激活，字典大小16k），训练于残差流和MLP输出。
- 额外训练：自己训练的**注意力输出SAE**（每层，遵循Gemma Scope训练流程）。
- 验证实验：**LLama Scope**（Llama-3.1-8B上的SAE包，TopK激活后转JumpReLU）。

### 对比方法
- **特征前身识别**：比较余弦相似度匹配与Pearson相关系数匹配（数据驱动）。
- **去激活实验**：
  - 随机（从top-5候选随机选一个）
  - 排列匹配（Balagansky et al. 2024）
  - top-1余弦相似度（本文）
  - top-5余弦相似度（需五个全部失活才算前驱失活）
  - 穷举搜索（逐个测试所有活跃前驱，取最佳）
- **引导实验**：
  - 单层引导 vs 累积引导（从第0层到当前层）
  - 三种缩放策略：常数、线性衰减、指数衰减
  - 不同缩放系数r（0, -2, -4, ..., -64）
  - 不同初始特征集：仅初始特征 vs 流图扩展后的特征

### 评估指标
- **特征去激活**：成功率（前驱失活后目标特征激活值降为0的比例）、激活变化（1 - 新激活值/旧激活值）。
- **模型引导**：
  - 行为分数（Behavioral）：GPT-4o-mini判断生成文本是否包含目标主题（0-5分）。
  - 连贯性分数（Coherence）：文本语法和语言质量（0-5分）。
  - 去激活最终指标：（1 - Behavioral）× Coherence；激活最终指标：Behavioral × Coherence。

## 4. 资源与算力

论文**未明确说明**训练或实验所用的GPU型号、数量、训练时长等具体算力信息。仅提及“我们按照Gemma Scope训练流程训练了注意力SAE”，但未给出训练开销。因此，论文在资源报告方面存在不足。

## 5. 实验数量与充分性

### 实验数量
- **特征前身识别实验**：在4个数据集、所有层（25层）上进行，每层采样约350个特征，统计8种源组分布。结果以百分比图呈现。
- **去激活实验**：选取3层（6,12,18），每层35个文本×5 token×25特征，共约13106个特征。比较4种匹配方法，并额外比较了不同缩放系数r（7种值）。
- **引导实验**：
  - 去激活主题“科学概念与实体”：涉及10个初始特征（表2），比较单层vs累积、r从0到-64，每层计算分数。
  - 激活主题（愤怒/心理健康/婚礼/宗教）：每个主题1个初始特征，比较4种引导策略。
  - 额外激活主题“研究方法论”：10个初始特征，选择子流图，单层vs累积。
- **消融实验**：比较余弦与Pearson匹配（附录C.4）、比较不同k值的top-k匹配（附录F）、比较不同组合权重的过渡矩阵（附录F）。

### 实验充分性与公平性
- **覆盖度**：多种数据集（自然语言、代码、数学）、多种模型（Gemma、LLama、Pythia、GPT-2 in discuss）、多种匹配方法、多种引导参数。较为全面。
- **客观性**：使用第三方评估（GPT-4o-mini）打分，但可能存在偏差。对于“From nowhere”组占比较高（40-60%），论文承认可能是匹配误差或稀疏激活导致。
- **公平性**：与基线方法（随机、排列、Pearson）比较，结果显示余弦方法优于随机，与Pearson相当。穷举搜索实验证明余弦方法达到了最优性能的73%（而穷举为83%），说明仍有提升空间。
- **局限性**：注意力SAE的训练质量可能低于残差SAE，导致注意力相关组检测率低。在LLama Scope上验证了相似模式，但未做引导实验。

## 6. 论文的主要结论与发现

1. **余弦相似度是激活相关性的良好代理**：无数据的余弦匹配与数据驱动的Pearson匹配性能相近，且对分布偏移（如Python代码）更鲁棒。
2. **特征演化呈现阶段性**：模型可划分为[0-5]层（高熵、不确定）、[6-15]层（稳定演化）、[16-25]层（残差传播为主，新特征减少）。后期层“From RES”组比例上升。
3. **流图揭示了机制性的计算路径**：MLP和注意力模块负责引入新特征或修改特征，残差流作为主要通信渠道。存在线性电路行为，如“From MLP”组对去激活更敏感。
4. **多层引导优于单层引导**：在多个层上施加小尺度扰动比单层大扰动更有效，尤其当缩放系数r较小时。累积引导降低了超参数敏感性，且能保持生成文本的连贯性。
5. **首次实现基于跨层SAE特征的模型引导**：通过流图发现初始特征在早期层的前驱，可以在不影响其他能力的前提下控制主题生成。

## 7. 优点

- **无数据方法**：仅依赖SAE权重，无需收集激活数据，计算高效且适用于分布偏移场景。
- **可解释性**：流图直观展示了特征的语义演化，例如“伦敦”特征在早期层关联“时尚”，解释了单层引导产生意外主题的原因。
- **因果验证**：通过去激活实验验证了匹配的有效性（成功率65%+），并揭示了不同源组（纯残差、残差+MLP等）的不同因果特性。
- **引导实用性强**：首次实现多层SAE特征引导，并提供多种缩放策略，可平衡行为控制和文本质量。
- **跨模型验证**：在Gemma 2 2B和Llama-3.1-8B（LLama Scope）上均获得一致结果，表明方法的泛化性。

## 8. 不足与局限

- **注意力SAE质量较低**：自己训练的注意力SAE可能未充分捕捉注意力输出特征，导致“From ATT”组检测率低（Gemma数据中仅~5%，而LLama Scope中~25%）。这可能影响流图的完整性。
- **忽略跨token交互**：当前方法仅分析单token位置的隐藏状态，未考虑注意力机制中token间的交互（如头模式、组合电路），导致部分特征无法解释（“From nowhere”组占比较高）。
- **线性假设局限**：方法基于线性表示假设，但Engels et al. (2025)指出部分特征并非一维线性。可能遗漏更复杂的特征结构。
- **评估偏差**：行为评分依赖GPT-4o-mini，其判断可能受训练前偏见影响。且仅使用单一LLM作为评判者，缺乏多轮交叉验证。
- **缺乏大规模算力报告**：未提供训练和推理的计算成本，不利于复现和能耗评估。
- **引导实验范围有限**：仅测试了少数主题（4个激活+2个去激活），且初始特征选择依赖Neuronpedia解释，可能存在主观性。
- **未探讨负向引导（如模型越狱）**：论文在Impact statement中提到了双重用途风险，但未在实验中评估引导方法被滥用的可能性。

（完）
