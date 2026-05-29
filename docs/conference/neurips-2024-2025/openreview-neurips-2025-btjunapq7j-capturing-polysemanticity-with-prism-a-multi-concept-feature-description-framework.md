---
title: "Capturing Polysemanticity with PRISM: A Multi-Concept Feature Description Framework"
title_zh: 使用PRISM捕获多语义：一个多概念特征描述框架
authors: "Laura Kopf, Nils Feldhus, Kirill Bykov, Philine Lou Bommer, Anna Hedström, Marina MC Höhne, Oliver Eberle"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=btJUnAPQ7j"
tags: ["query:ns-xai"]
score: 8.0
evidence: 多概念特征描述用于LLM可解释性
tldr: 现有神经元描述假设单语义，限制了可解释性。本文提出PRISM框架，识别并评分神经元中的多概念特征，突破单语义限制。实验证明PRISM能更全面地捕获模型内部编码的多重语义，增强了特征描述的忠实性和表达能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 381}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 377}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1328, \"height\": 526}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 504}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 998}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1456, \"height\": 614}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 460}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1046, \"height\": 862}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1049, \"height\": 858}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 859, \"height\": 605}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1329, \"height\": 1063}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btjunapq7j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1399, \"height\": 440}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 319}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1478, \"height\": 707}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1138, \"height\": 315}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1421, \"height\": 317}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 249}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1238, \"height\": 261}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1041, \"height\": 331}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 447}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1483, \"height\": 2347}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btjunapq7j/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1485, \"height\": 2214}]"
motivation: 神经元同时编码多概念（多语义性），现有方法假设单语义导致描述不充分。
method: 提出PRISM框架，对神经网络特征进行多概念识别与评分。
result: PRISM成功捕获了神经元中的多语义概念，提高了可解释性描述的覆盖度。
conclusion: 考虑多语义性可大幅提升自动可解释性工具的效果。
---

## Abstract
Automated interpretability research aims to identify concepts encoded in neural network features to enhance human understanding of model behavior. Within the context of large language models (LLMs) for natural language processing (NLP), current automated neuron-level feature description methods face two key challenges: limited robustness and the assumption that each neuron encodes a single concept (monosemanticity), despite increasing evidence of polysemanticity. This assumption restricts the expressiveness of feature descriptions and limits their ability to capture the full range of behaviors encoded in model internals. To address this, we introduce Polysemantic FeatuRe Identification and Scoring Method (PRISM), a novel framework specifically designed to capture the complexity of features in LLMs. Unlike approaches that assign a single description per neuron, common in many automated interpretability methods in NLP, PRISM produces more nuanced descriptions that account for both monosemantic and polysemantic behavior. We apply PRISM to LLMs and, through extensive benchmarking against existing methods, demonstrate that our approach produces more accurate and faithful feature descriptions, improving both overall description quality (via a description score) and the ability to capture distinct concepts when polysemanticity is present (via a polysemanticity score).

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：当前针对大语言模型（LLM）神经元的自动可解释性方法存在两个关键缺陷：一是鲁棒性有限，二是普遍假设每个神经元只编码单一概念（单语义性，monosemanticity）。然而，越来越多的证据表明神经元往往表现出多语义性（polysemanticity），即一个特征同时编码多个语义上不同的概念。这种单语义假设严重限制了特征描述的丰富性和表达能力，无法全面反映模型内部的实际行为。
- **研究背景**：随着LLM在软件开发、医疗诊断等领域的广泛应用，模型内部决策过程的不透明性成为重要挑战。机械可解释性、结构化解释等方法虽试图理解模型内部结构，但大多仍基于单概念描述范式。稀疏自编码器（SAE）虽然可以提取更离散的特征，但许多SAE特征仍然编码多概念。因此，需要一种能够捕获多概念的特征描述框架。
- **论文目标与含义**：本文提出的PRISM（Polysemantic FeatuRe Identification and Scoring Method）框架，旨在捕获特征的多概念复杂性，生成更准确、更忠实于激活分布的多概念描述，从而提升LLM可解释性的粒度与可靠性。该研究为自动可解释性领域提供了新的方法论基础，推动了对模型内部表征的系统性理解。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：PRISM不假设特征仅对应单一概念，而是通过聚类和LLM生成多个自然语言描述，每个描述代表一个语义簇。同时，设计了描述评分（Description Score）和多语义性评分（Polysemanticity Score）来量化描述质量与特征的多语义程度。
- **关键技术细节**：
  1. **百分位数采样**：对于给定特征（神经元或SAE特征），从语料库中抽取激活值位于99th至100th百分位数的文本片段，步长为1e-05，共1000个高激活片段。这比直接取top-k更能捕获广泛的概念模式。
  2. **概念聚类**：使用句子嵌入模型（gte-Qwen2-1.5B-instruct）将高激活文本编码，然后通过K-Means聚类（固定k=5）将文本划分为5个簇，每个簇代表一个潜在概念。当簇高度相似时，低多语义性评分会反映单语义性。
  3. **簇标记**：对每个簇取激活值最高的20个文本，用LLM（Gemini 1.5 Pro）生成简洁的自然语言摘要作为描述。提示词中通过方括号高亮高激活词，指导模型关注共同模式。
- **评估公式**（文字说明）：
  - **描述评分**：使用C**OSY**方法，比较目标概念文本（由LLM基于特征描述生成）与随机控制文本（从Cosmopedia中采样）在该特征上的激活分布。计算AUROC（区分能力）和MAD（标准化均值激活差异）。MAD报告正向比例（激活均值大于控制均值的特征百分比）。
  - **多语义性评分**：将每个特征的5个描述用同一句子嵌入模型编码，计算两两余弦相似度，取平均。相似度越低表示多语义性越强（概念越分散）。
- **形式化定义**：特征描述函数ϕ将特征映射到描述子集（允许空集和全集），支持单概念和多概念。PRISM输出的描述数为k（默认5），每个描述对应一个簇。

### 3. 实验设计：使用了哪些数据集/场景，其benchmark是什么，对比了哪些方法

- **数据集**：主要使用C4 CORPUS英文子集作为激活提取语料；控制集为Cosmopedia随机子集；目标概念文本由LLM根据描述生成。
- **场景与模型**：评估覆盖四种预训练LLM：
  - GPT-2 XL（MLP神经元）
  - Llama 3.1 8B Instruct（MLP神经元）
  - GPT-2 Small（残差流SAE特征）
  - Gemma Scope（残差流SAE特征）
  每个模型选取三个层（早期、中期、晚期），每层随机选择20个特征（共60个特征，仅GPT-2 Small SAE有59个）。
- **Benchmark与对比方法**：
  - MaxAct：取top-5激活样本，用相同LLM生成描述。
  - GPT-Explain：基于模拟激活的方法。
  - Transluce-Explain：针对Llama 3.1 8B Instruct的神经描述。
  - Neuronpedia：提供SAE特征描述。
  - Output-Centric：基于输出的特征描述方法。
- **实验类型**：
  - **主基准实验**：比较各方法的AUROC和MAD（PRISM报告max和mean两种聚合方式）。
  - **消融实验**：改变聚类数k（1,3,5,10）；替换描述生成LLM（Qwen3 32B、Phi-4、DeepSeek R1）；替换评估生成LLM。
  - **健全性检查**：随机化句子/描述以验证忠实性；按激活百分位区间分析；分析相对激活比率。
  - **输出中心评估**：使用Faithfulness指标（FADE框架）评估因果影响。
  - **人类评估**：7名参与者对8个特征的5个簇进行标记和多语义性评分，与PRISM评分对比。

### 4. 资源与算力

- **明确说明**：附录A.4中写道“All experiments were conducted using a single NVIDIA A100 80GB GPU. The description procedure takes approximately 9 minutes per feature, including percentile sampling, clustering, and the generation of 5 descriptions. For evaluation, the generation of 10 sentences per feature requires roughly 3 minutes.”
- 因此每层20个特征，3层共60个特征，每个模型约需9×60=540分钟（描述生成）加3×60=180分钟（评估），总计约12小时/模型。未提及使用多GPU或分布式训练。

### 5. 实验数量与充分性

- **实验数量**：主基准涉及4种模型×3层×20特征×多方法对比；消融实验包括聚类大小（5种）、描述生成LLM（4种）、评估LLM（4种）；健全性检查4项；输出中心评估1项；人类评估8个特征×7名参与者。总计实验组数十组，统计量丰富。
- **充分性与客观性**：实验设计较为全面，覆盖不同架构（GPT-2 vs Llama）和特征类型（原始神经元 vs SAE特征），评估指标多维（AUROC、MAD、Faithfulness、余弦相似度、人类评分）。消融实验验证了鲁棒性，健全性检查排除了随机性解释。人类评估提供了定性支持。但是，每层仅20个特征（总计60个）样本量较小，可能存在随机波动；且不同方法特征数不同（有些方法无法为所有模型提供描述），导致比较并非完全一致。总体而言，实验设计相对公平且系统。

### 6. 论文的主要结论与发现

- **PRISM的优越性**：PRISM（max）在所有模型和特征类型上取得了最高的AUROC和MAD，显著优于现有单概念方法。例如GPT-2 XL上AUROC达0.85，MAD达91.67%。
- **多概念描述提高了忠实性**：相比单概念描述，PRISM的多概念描述能更好地区分目标概念与控制样本，且激活差异更显著。
- **跨层模式**：中间层通常更容易解释（AUROC峰值），但多语义性没有一致的层间趋势。Gemma Scope SAE特征表现出最高的单语义性（高余弦相似度）。
- **概念空间多样性**：通过元聚类发现特征描述涵盖句法、语义、语用等多个层面，甚至出现如“李斯特菌污染”等特定领域概念，表明模型内部表征的异构性。
- **与人类判断一致**：人类评估中，PRISM的多语义性评分与人类对概念多样性的评级高度对齐（低PRISM分对应低人类相似性分，高PRISM分对应高人类评分）。

### 7. 优点：方法或实验设计上的亮点

- **多概念假设突破**：首次在自动可解释性中系统处理多语义性，即不预设单概念，而是通过聚类自动发现多个语义簇。
- **双维评分体系**：同时提供描述质量（AUROC/MAD）和多语义性（余弦相似度），使得评估更全面。
- **细粒度采样策略**：采用分位数区间采样（99th-100th百分位数，步长1e-05）而非简单top-k，能捕获更广泛的概念模式。
- **健壮性验证充分**：通过替换LLM、改变聚类数、随机化控制等多种消融和健全性检查，证明框架的鲁棒性。
- **与人类主观评估结合**：设计了人类标注实验，不仅验证了自动评分的一致性，还提供了定性见解。
- **开源**：代码已公开。

### 8. 不足与局限

- **聚类数固定**：默认k=5，可能无法覆盖特征的所有概念，或过度分割。作者在消融中承认存在精度与覆盖的权衡。
- **语言局限性**：描述仅限于自然语言表达的概念，难以捕捉复杂句法结构、算法概念或非语言模式。
- **评估依赖LLM**：描述生成和评估均依赖外部LLM（Gemini 1.5 Pro），可能引入模型偏见或不忠实问题。虽然进行了健全性检查，但完全避免仍有困难。
- **数据覆盖有限**：maximally activating corpus examples可能限制了对稀有模式或分布外概念的覆盖。
- **样本量较小**：每层仅20个特征（总计60个），可能不足以代表广泛的特征行为。
- **参数化度量MAD敏感性**：MAD对异常值敏感，尤其在激活分布呈重尾的NLP场景中，论文通过结合AUROC来缓解。
- **未探索自适应聚类数**：固定k可能不适用于所有特征，未来可考虑动态确定簇数。

（完）
