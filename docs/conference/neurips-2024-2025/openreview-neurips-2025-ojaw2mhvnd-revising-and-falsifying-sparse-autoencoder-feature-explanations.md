---
title: Revising and Falsifying Sparse Autoencoder Feature Explanations
title_zh: 修正与证伪稀疏自编码器特征解释
authors: "George Ma, Samuel Pfrommer, Somayeh Sojoudi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OJAW2mHVND"
tags: ["query:ns-xai"]
score: 7.0
evidence: 改进稀疏自编码器特征解释以增强LLM可解释性
tldr: 针对稀疏自编码器（SAE）解释过于宽泛且未考虑多义性的问题，提出基于相似性的难负例采样策略和结构化组件化解释格式。实验证明，该方法能更有效地证伪解释，生成更精确的特征描述，推动了大模型机械可解释性研究的前进。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 698}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1413, \"height\": 523}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 843, \"height\": 551}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 520}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1415, \"height\": 580}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 1738}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1424, \"height\": 1139}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 986}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1446, \"height\": 1107}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1440, \"height\": 1295}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1438, \"height\": 312}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1442, \"height\": 270}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1427, \"height\": 747}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1417, \"height\": 596}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1416, \"height\": 528}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1444, \"height\": 397}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1445, \"height\": 400}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ojaw2mhvnd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 200}]"
motivation: 当前SAE特征解释过于宽泛且忽略多义性，难以准确反映模型内部机制。
method: 提出基于相似性的难负例采样策略以及组件化解释格式，以增强解释的可证伪性和精确性。
result: 新方法生成的特征解释更精准，并能有效识别和修正原始解释中的错误。
conclusion: 该方法提升了可解释性研究的严谨性，为理解LLM内部概念提供了更可靠的工具。
---

## Abstract
Mechanistic interpretability research seeks to reverse-engineer large language models (LLMs) by uncovering the internal representations of concepts within their activations. Sparse Autoencoders (SAEs) have emerged as a valuable tool for disentangling polysemantic neurons into more monosemantic, interpretable features. However, recent work on automatic explanation generation for these features has faced challenges: explanations tend to be overly broad and fail to take polysemanticity into consideration. This work addresses these limitations by introducing a similarity-based strategy for sourcing close negative sentences that more effectively falsify generated explanations. Additionally, we propose a structured, component-based format for feature explanations and a tree-based, iterative explanation method that refines explanations. We demonstrate that our structured format and tree-based explainer improve explanation quality, while our similarity-based evaluation strategy exposes biases in existing interpretability methods. We also analyze the evolution of feature complexity and polysemanticity across LLM layers, offering new insights into information content within LLMs' residual streams.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：大型语言模型（LLM）的机械可解释性研究致力于逆向工程模型内部概念表征。稀疏自编码器（SAE）能够将多义性神经元分解为更单语义、可解释的特征，但现有自动解释生成方法存在两个关键缺陷：一是生成的解释过于宽泛（例如，对“not all”神经元仅概括为“激活于‘not’”，忽略上下文依赖）；二是未能考虑特征的多义性（一个特征可能对应多个不同概念）。
- **整体含义**：本文旨在通过更严格的负例采样、结构化解释格式和迭代优化方法，提升SAE特征解释的精确性和可证伪性，从而推动LLM机械可解释性研究的严谨性。作者还通过跨层分析揭示特征复杂度和多义性的演化规律。

## 2. 方法论

### 核心思想
- 提出三种互补的技术改进：①基于语义相似性的难负例采样（替代随机采样）以更有效证伪宽泛解释；②组件化结构化解释格式（JSON列表，每个组件包含描述和强度值）以显式建模多义性；③树状迭代解释生成（基于TAP算法）通过评估-反馈循环逐步精炼解释。

### 关键技术细节
- **相似性难负例采样**：使用预训练Sentence Transformer（如Sentence-BERT）计算句子嵌入，选择与top-activating句子平均余弦相似度最高但无真实特征激活的句子作为负例。这能暴露解释的假阳性（过于宽泛的解释会在这些语义相似句子中错误激活）。
- **结构化解释**：每个解释为列表`[{"activates_on": 字符串, "strength": 整数0-5}]`。模拟时，对每个组件分别使用模拟器预测token激活，按`strength`缩放后取各组件在各token的最大值作为最终预测，保证排列不变性。
- **树状解释生成（Algorithm 1）**：
  - 初始化：用单次explainer生成w个根节点解释。
  - 迭代（最多d轮）：
    1. 评估与反馈：对每个叶节点解释，使用模拟器预测验证集激活，计算与真实激活的皮尔逊相关系数；构造反馈消息（包含得分和最低分句子的真实/预测激活）。
    2. 分支：对每个叶节点，结合反馈和祖先对话历史，使用链式思维提示生成b个子解释。
    3. 剪枝：保留验证得分最高的w个叶节点。
  - 终止后，返回所有迭代中验证得分最高的解释。
- **整体特征（Holistic features）**：为每个token定义一个补充值`\tilde{f}(t)_i = (1/n) * (sum of f over all tokens - sum of f over all except token i)`，反映该token对特征总表达的因果贡献。实验中尝试将整体激活作为额外信号提供给explainer，但未带来提升。

## 3. 实验设计

- **数据集**：使用Pile语料库的未版权子集（pile-uncopyrighted），从中抽取100,000个句子，每条句子截断为32个token。
- **基准模型与SAE**：
  - 主语模型：Gemma-2-9B、Llama-3.1-8B、GPT-2 Small。
  - 预训练SAE：Gemma Scope（16k宽度）、Llama Scope（32k宽度）、GPT-2 SAE（32k宽度）。
  - 每层取前50个SAE特征进行分析。
- **对比方法**：
  - 解释生成方式：单次（one-shot）vs. 树状（tree-based）。
  - 解释格式：非结构化（单句字符串）vs. 结构化（JSON组件列表）。
  - 负例采样策略：随机 vs. 相似性（以及各自的非激活变体）。
  - 是否包含训练负例（top-activating句子 + 额外负例作为输入）和整体特征（holistic features）。
- **评估指标**：
  - 皮尔逊相关系数：模拟激活与真实激活在测试集（10个top-activating + 10个负例）上的相关性。
  - 假阳性率：模拟激活在负例句子上的正激活（>1）数量。
- **模拟器**：Gemma-2-27B-it（4-bit量化），使用“all-at-once”方法（Bills et al.）一次性预测所有token激活，通过两层级KV缓存加速（系统prompt+few-shot打底，再缓存解释）。

## 4. 资源与算力

- 文中未明确给出总训练/推理时长，但指出：
  - 树状解释生成每个特征约需 **1.5分钟**（硬件为40GB A100 GPU + 32 CPU核心）。
  - 模拟器使用Gemma-2-27B-it（4-bit量化）在单张A100上运行。
  - 所有计算在Jetstream2云平台（印第安纳大学）通过ACCESS分配完成。
- 未说明总实验数量对应的总GPU小时数。

## 5. 实验数量与充分性

- **实验组数**：主要对比四种负例策略（图3）、四种解释方法组合（one-shot/tree × 非结构化/结构化，及含训练负例/整体特征的两个扩展，共8种配置，图4/表1）、三层模型（Gemma-2-9B、Llama-3.1-8B、GPT-2 Small）、多层分析（每层50个特征，覆盖所有层的一定间隔）。此外，还有复杂度/多义性分析（图5、图16-18）以及结构化解释规则数热力图（图17-18）。
- **充分性与公平性**：
  - 实验覆盖三个不同规模、不同家族的语言模型，增强了结论的泛化性。
  - 所有对比使用相同的数据拆分、同样的模拟器（Gemma-2-27B-it），避免因模拟器差异导致偏差。
  - 消融实验包括是否包含训练负例、是否使用整体特征，结果均为负，表明这些设计未改善性能，这是诚实的报告。
  - 置信区间（90%或80%）和误差线在图中标注，统计严谨。
  - 不足：仅使用了Pile一个数据集（尽管是常见基准）；每层只取50个特征，可能不足以代表全部分布；实验设置中top-activating句子固定为10句，未测试不同数量。

## 6. 主要结论与发现

1. **相似性负例更有效**：基于语义相似性的难负例采样在两种解释器（one-shot和tree）下均产生更高的假阳性率（图3、图15），说明它们能更好地暴露解释的宽泛性和精度不足，而随机负例低估了假阳性。
2. **树状解释生成优于单次**：无论非结构化还是结构化格式，树状方法在所有三个模型中均显著提高相关系数（图4/表1），相对提升16-22%。
3. **结构化解释在单次场景下有益**：单次explainer中，结构化格式比非结构化格式提升5-9%相关系数；但在树状explainer中，差异不显著，推测是因为树状方法已能通过迭代将多义性打包进单个字符串。
4. **训练负例和整体特征无增益**：在两种解释器中加入训练集负例或整体激活信号均未带来性能提升，说明LLM仍难以直接利用上下文信息修正解释。
5. **特征复杂度跨层演化**：Gemma-2和Llama-3.1在中间层达到最高复杂度（图5左），GPT-2趋于平稳；多义性（所需规则数达到90%最大得分）在Gemma和Llama中随层数增加（从约1.5到2.0以上），GPT-2始终较低（图5右）。
6. **揭示召回偏差**：现有自动解释方法偏向召回（宽泛解释获得高分），相似性负例有效暴露了此偏差。

## 7. 优点

- **方法创新性**：①首次将语义相似性用于SAE解释的难负例采样，提升了评估的精确性；②提出结构化组件化解释格式，显式建模多义性；③将TAP（Tree of Attacks with Pruning）从对抗攻击迁移到可解释性任务，成为有效的迭代解释精炼框架。
- **实验设计全面**：覆盖多种模型、多种解释配置、消融实验完整，统计显著性和置信区间呈现充分。
- **实践价值**：提供了开源代码和预计算负例缓存，便于复现和扩展。
- **洞察性发现**：通过跨层分析特征复杂度和多义性，为理解LLM内部信息组织提供新的实证证据（中间层抽象程度高、深层多义性增加等）。

## 8. 不足与局限

- **计算成本高**：树状解释每个特征约1.5分钟，大规模分析（如数百万特征）不可行；且依赖大型模拟器（Gemma-2-27B），可能成为瓶颈。
- **依赖top-activating句子的偏差**：主要基于最高激活的句子，可能遗漏低频但重要的激活模式，导致解释不完整。
- **SAE本身局限**：SAE分解的是表征结构而非真实计算机制，即使解释精确，也不能保证理解模型的底层推理过程。
- **实验覆盖有限**：仅使用Pile一个数据集、三个模型（均为开源，且规模相对有限），未在更大模型（如70B+）或不同架构（如Mixture of Experts）上验证。
- **模拟器和解释器模型单一**：所有解释生成使用Llama 4 Scout（未在文本中明确但附录A指出），模拟器固定为Gemma-2-27B；不同模型可能产生不同结果，存在模型偏差风险。
- **树状方法超参数敏感性**：论文使用固定超参数（初始节点3、深度2、分支因子2、宽度2），未系统探索不同设置对性能的影响。
- **负例采样仅基于语义相似性**：未考虑句法结构、语境等更精细的负例挖掘方法。

（完）
