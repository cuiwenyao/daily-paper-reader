---
title: "Capturing Polysemanticity with PRISM: A Multi-Concept Feature Description Framework"
title_zh: 使用PRISM捕捉多义性：多概念特征描述框架
authors: "Laura Kopf, Nils Feldhus, Kirill Bykov, Philine Lou Bommer, Anna Hedström, Marina MC Höhne, Oliver Eberle"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=btJUnAPQ7j"
tags: ["query:ns-xai"]
score: 8.0
evidence: 大模型可解释性方法，通过多概念特征描述
tldr: 当前自动可解释性方法假设每个神经元编码单一概念，忽略了多义性。PRISM提出多概念特征识别与评分框架，能够为LLM内部每个神经单元发现并评分多个可能概念，从而更全面地描述模型行为。实验表明该方法在概念覆盖率和描述准确性上优于现有方法，为理解大模型内部表示提供了更丰富的可解释性工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1328, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 998, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1456, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1046, \"height\": 862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1049, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 859, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1329, \"height\": 1063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1399, \"height\": 440, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1478, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1138, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1421, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1238, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1041, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1483, \"height\": 2347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1485, \"height\": 2214, \"label\": \"Table\"}]"
motivation: 现有神经元特征描述方法假设单义性，但实际神经元多为多义，限制了可解释性。
method: PRISM通过多概念识别与评分，为每个神经元发现多个概念并分配置信度分数。
result: 在LLM内表示上，PRISM相比单概念方法覆盖更多概念且描述更准确。
conclusion: PRISM为深度模型的可解释性提供了更丰富、更真实的特征描述手段。
---

## Abstract
Automated interpretability research aims to identify concepts encoded in neural network features to enhance human understanding of model behavior. Within the context of large language models (LLMs) for natural language processing (NLP), current automated neuron-level feature description methods face two key challenges: limited robustness and the assumption that each neuron encodes a single concept (monosemanticity), despite increasing evidence of polysemanticity. This assumption restricts the expressiveness of feature descriptions and limits their ability to capture the full range of behaviors encoded in model internals. To address this, we introduce Polysemantic FeatuRe Identification and Scoring Method (PRISM), a novel framework specifically designed to capture the complexity of features in LLMs. Unlike approaches that assign a single description per neuron, common in many automated interpretability methods in NLP, PRISM produces more nuanced descriptions that account for both monosemantic and polysemantic behavior. We apply PRISM to LLMs and, through extensive benchmarking against existing methods, demonstrate that our approach produces more accurate and faithful feature descriptions, improving both overall description quality (via a description score) and the ability to capture distinct concepts when polysemanticity is present (via a polysemanticity score).

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有自动可解释性方法（如 GPT-Explain、Transluce-Explain 等）通常假设每个神经元或特征编码**单一概念**（单义性，monosemanticity）。然而，越来越多证据表明 LLM 内部特征往往表现出**多义性**（polysemanticity），即一个特征可响应多个语义不同的概念。当前方法只能给出单条描述，限制了表达力，无法全面刻画特征行为。
- **动机**：为了更真实、更全面地理解模型内部表示，需要一种能够**捕捉多义性**的特征描述框架，同时提供量化指标来评估描述质量与多义程度。
- **贡献**：提出 **PRISM**（Polysemantic FeatuRe Identification and Scoring Method），首次实现多概念特征描述，并引入**描述评分**（Description Scoring）和**多义性评分**（Polysemanticity Scoring）两个度量。

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：不再为每个特征生成单一描述，而是通过聚类发现多个激活模式，为每个模式独立生成文本描述，从而覆盖多义性。
- **算法流程（三步，对应图2）**：
  1. **Percentile Sampling**（百分位采样）：对给定特征，从语料中提取所有文本片段激活值，取 99–100 百分位区间，每 1e-5 步长采样一个片段，共约 1000 个高激活样本。
  2. **Concept Clustering**（概念聚类）：将高激活样本用句子嵌入模型（gte-Qwen2-1.5B-instruct）编码，然后用 **K-Means**（k=5）聚类，得到 5 个簇，每个簇代表一个潜在概念。
  3. **Cluster Labeling**（簇标签生成）：对每个簇，选取激活值最高的 **20** 个句子，用 LLM（默认 Gemini 1.5 Pro）生成简洁的自然语言描述，作为该特征的一个概念描述。
- **多义性评分**：将 5 个簇描述用相同句子嵌入模型编码，计算两两余弦相似度，取均值。值越低表示多义性越高（概念越分散）。
- **描述评分**：借鉴 CoSy 方法，对每个概念描述，由 LLM 生成 10 个概念相关样本（X₁）和随机控制样本（X₀，1000 个），计算特征激活的 **AUROC**（区分能力）和 **MAD**（均值激活差标准化，报告正比例）。得分越高描述越准确。
- **公式**：AUROC 基于 Mann-Whitney U 统计；MAD 为 (mean(X₁)-mean(X₀))/std(X₀)。

### 3. 实验设计
- **数据集**：C4 Corpus 英文训练子集，文本截断或填充至 512 tokens。
- **模型与特征类型**：
  - GPT-2 XL（MLP 神经元，层 0/20/40）
  - Llama 3.1 8B Instruct（MLP 神经元，层 0/20/30）
  - GPT-2 Small（残差流 SAE 特征，层 0/5/10）
  - Gemma Scope（残差流 SAE 特征，层 0/10/20）
- **对比方法**：MaxAct、GPT-Explain、Transluce-Explain、Neuronpedia、Output-Centric。
- **基准指标**：AUROC（含 95% 置信区间）、MAD（正比例）。
- **额外评估**：输出中心性 Faithfulness（基于 FADE），人类评估（7 名参与者，8 个特征，11 点相似度评分）。

### 4. 资源与算力
- **GPU**：单个 **NVIDIA A100 80GB**。
- **时间成本**：每个特征描述生成约 **9 分钟**（含采样、聚类、5 条描述生成），评估约 **3 分钟**（生成概念样本+计算 AUROC/MAD）。
- **未提及**：总训练时长、多 GPU 并行情况未说明。

### 5. 实验数量与充分性
- **实验数量**：主基准（表1）覆盖 4 个模型 × 3 层，每层 20 个随机特征（仅 GPT-2 Small SAE 59 个），共约 239 个特征。消融实验包括：簇数量 k（k=1,3,5,10）、文本生成器替换（Qwen3 32B, Phi-4, DeepSeek R1，描述生成和评估各一组）。健全性检查：随机句子、随机描述、百分位区间分析、相对激活分析。人类评估：8 个特征。
- **充分性与公平性**：实验设计较为全面，涵盖不同模型架构（GPT-2 vs Llama）、不同特征类型（原始神经元 vs SAE）、多个层次。对比方法均使用公开描述，评估过程统一。但仅使用英文数据，可能限制泛化性。特征选择随机，但数量偏少（每层 20 个），可能存在采样偏差。

### 6. 主要结论与发现
- PRISM（取 **max**，即最佳匹配描述）在 **AUROC 和 MAD** 上**一致优于**所有对比方法（GPT-2 XL 上 AUROC 0.85 vs GPT-Explain 0.64；Llama 上 0.71 vs Transluce-Explain 0.59）。
- **中间层**通常更易解释（AUROC 最高），但多义性无一致层趋势。
- **SAE 特征**（Gemma Scope）并不一定比原始神经元更单义；甚至在某些层上 PRISM 得分低于 Neuronpedia，表明输出空间对齐可能补充优势。
- **人类评估**与 PRISM 多义性评分高度一致，验证了框架的语义有效性。
- **概念空间聚类**（图4）可自动归纳出语法、语义、领域等层次，表明模型表示具有丰富结构。

### 7. 优点
- **首次系统性处理多义性**：打破单概念假设，更真实反映特征行为。
- **双评分体系**：同时量化描述质量（AUROC/MAD）和多义程度（余弦相似度）。
- **广泛的基准测试**：覆盖多种模型、特征类型，对比多个基线，结果可靠。
- **健全性检查**：随机化实验验证描述忠实性，排除 LLM 幻觉。
- **人类评估**：直接比较人机评分，增强可信度。
- **可解释性分析工具**：概念空间可视化和元聚类，便于大规模理解模型内部。

### 8. 不足与局限
- **语言限制**：描述局限于自然语言可表达的概念，无法覆盖图结构、算法操作等抽象模式。
- **固定簇数 k=5**：可能遗漏或过度分割概念，不能保证覆盖所有重要模式。
- **MAD 对离群值敏感**：激活分布常为重尾，AUROC 补充但仍有局限。
- **依赖 LLM 生成样本**：评估中概念样本由 LLM 生成，可能引入偏差或遗漏罕见模式。
- **仅英文数据集**：未验证跨语言泛化性。
- **计算成本较高**：每个特征需要 9+3 分钟，大规模应用（如全模型特征）资源需求大。
- **特征选择随机且数量有限**（每层 20 个），可能未充分代表模型内部分布。

（完）
