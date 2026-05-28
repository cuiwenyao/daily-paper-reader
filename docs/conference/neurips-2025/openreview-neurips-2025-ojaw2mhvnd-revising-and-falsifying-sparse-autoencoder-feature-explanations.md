---
title: Revising and Falsifying Sparse Autoencoder Feature Explanations
title_zh: 修正与证伪稀疏自编码器特征解释
authors: "George Ma, Samuel Pfrommer, Somayeh Sojoudi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OJAW2mHVND"
tags: ["query:ns-xai"]
score: 7.0
evidence: 改进稀疏自编码器特征解释以增强LLM可解释性
tldr: 稀疏自编码器（SAE）常用于LLM可解释性，但其自动生成的特征解释过于宽泛且未考虑多义性。本文提出基于相似性的负样本选取策略和组件化解释格式，有效质控生成的解释，提高其精确性和可验证性。实验表明新方法能更有效地发现特征中的多义性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 698, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1413, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 843, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1415, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 1738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1424, \"height\": 1139, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 986, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1446, \"height\": 1107, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1440, \"height\": 1295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1438, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1442, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1427, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1417, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1416, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1444, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ojaw2mhvnd/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1445, \"height\": 400, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ojaw2mhvnd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 200, \"label\": \"Table\"}]"
motivation: 现有SAE特征解释方法生成过于宽泛的解释，且无法处理多义性，影响可解释性质量。
method: 引入基于相似性的难负样本选取和组件化解释格式，以更有效地证伪和精化特征解释。
result: 在多个LLM上，新方法生成的解释更精确，能揭示更多多义性特征，且可证伪性更强。
conclusion: 为SAE特征解释的自动生成与评估提供了更可靠的方案，推进了LLM可解释性研究。
---

## Abstract
Mechanistic interpretability research seeks to reverse-engineer large language models (LLMs) by uncovering the internal representations of concepts within their activations. Sparse Autoencoders (SAEs) have emerged as a valuable tool for disentangling polysemantic neurons into more monosemantic, interpretable features. However, recent work on automatic explanation generation for these features has faced challenges: explanations tend to be overly broad and fail to take polysemanticity into consideration. This work addresses these limitations by introducing a similarity-based strategy for sourcing close negative sentences that more effectively falsify generated explanations. Additionally, we propose a structured, component-based format for feature explanations and a tree-based, iterative explanation method that refines explanations. We demonstrate that our structured format and tree-based explainer improve explanation quality, while our similarity-based evaluation strategy exposes biases in existing interpretability methods. We also analyze the evolution of feature complexity and polysemanticity across LLM layers, offering new insights into information content within LLMs' residual streams.

---

## 论文详细总结（自动生成）

# 论文《Revising and Falsifying Sparse Autoencoder Feature Explanations》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLM）的机制可解释性旨在逆向工程其内部表示。稀疏自编码器（SAE）被广泛用于将多义性神经元分解为更单义的、可解释的特征。然而，现有自动生成特征解释的方法（如Bills et al.）存在两个主要问题：生成的解释过于宽泛（缺乏精确性），且未能考虑特征的多义性（polysemanticity）。
- **核心问题**：如何构建更精确、可证伪的特征解释，并揭示现有方法的偏差（尤其是“召回率偏差”）。
- **整体含义**：本文提出一套改进方案，包括相似度驱动的负样本选取策略、结构化的组件式解释格式以及基于树的迭代解释精化方法，旨在提升解释的质量、精确性和可证伪性。

## 2. 论文提出的方法论

### 2.1 核心思想
- 引入**语义相似性**来选取难负样本（close negatives），替代传统随机采样，以更有效地揭露过于宽泛的解释。
- 提出**结构化解释格式**：将解释表示为JSON对象列表，每个对象包含`activates_on`（字符串描述）和`strength`（0-5整数），对应一个单义概念。模拟时对各组件分别预测激活值，按强度加权后取最大值合并。
- 提出**基于树的迭代解释生成方法**（Tree-based Explainer）：借鉴Tree of Attacks with Pruning（TAP）方法，通过迭代评估、反馈、分支和剪枝来逐步精化解。

### 2.2 关键技术细节
- **特征模拟**：遵循Bills et al.的“all-at-once”方法，使用gemma-2-27b-it模型本地运行，采用双层键值缓存提升效率。
- **互补句子选取**：四种策略：
  1. 随机采样（Random）
  2. 随机非激活（Random non-activating）
  3. 语义相似性（Similarity-based）：使用预训练Sentence Transformer计算句子嵌入，选择与top激活句子最相似的句子。
  4. 语义相似性非激活（Similarity-based non-activating）
- **整体特征（Holistic features）**：定义为`~f(t)_i = (1/n)(1_n^T f(t) - 1_{n-1}^T f(t_{-i}))`，衡量某个token对特征总表达的贡献。用于补充特征记录。

### 2.3 算法流程（Tree-based Explainer，Algorithm 1）
1. 初始化：调用一次性解释器生成w个初始解释作为叶节点。
2. 循环迭代d次：
   - 评估：对每个叶节点，用模拟器预测激活值，计算与真实激活的皮尔逊相关系数，构造反馈消息（包括得分和最低分句子的预测与真实激活）。
   - 分支：对每个叶节点，使用思维链提示生成b个子解释。
   - 剪枝：保留得分最高的w个叶节点。
   - 若最高得分超过阈值τ，提前终止。
3. 返回所有迭代中验证集得分最高的解释。

## 3. 实验设计

### 3.1 数据集与场景
- **数据集**：Pile数据库中无版权子集（Pile Uncopyrighted），约100,000个句子，每个句子切分为32个token。
- **目标语言模型**：Gemma-2-9B、Llama-3.1-8B、GPT-2 Small。
- **SAE**：Gemma scope（16k维度）、Llama scope和GPT-2 SAE（32k维度）。
- **评估指标**：皮尔逊相关系数（与Bills et al.一致）、假阳性率。

### 3.2 Benchmark与对比方法
- **解释生成方法**：
  - 一次性解释器（One-shot，基线）
  - 树状解释器（Tree，本文）
- **解释格式**：
  - 非结构化（Unstructured，基线）
  - 结构化（Structured，本文）
- **训练数据组成**：
  - 仅top激活句子
  - 添加训练负样本
  - 添加整体特征
- **互补句子选取**：四种策略对比（随机、随机非激活、相似性、相似性非激活）

### 3.3 消融实验
- 结构化 vs 非结构化；一次性 vs 树状；是否包含负样本；是否包含整体特征。
- 分析不同层数下特征复杂度和多义性的变化。

## 4. 资源与算力

- 文中明确指出：树状解释器每个特征约需**1.5分钟**（在40GB A100 GPU实例上，32 CPU核心）。
- 模拟使用gemma-2-27b-it模型，采用4-bit量化，运行在单张Nvidia A100（40GB）上。
- 实验使用了Jetstream2云计算资源（访问项目CIS240843）。
- 未提供总训练时长或总GPU小时数，仅给出了每特征的时间成本。

## 5. 实验数量与充分性

- **实验规模**：
  - 每个目标模型分析8个均匀分布的层（含首尾层），每层取前50个SAE特征。
  - 共涉及3个模型 × 8层 × 50特征 = 1200个特征的分析。
- **对比方法**：在3个模型上重复了所有主要对比（图4/表1），包括一次性 vs 树状、结构化 vs 非结构化等。
- **消融实验**：全面对比了训练负样本、整体特征、多条规则的影响（图17-18）。
- **统计显著性**：报告了90%置信区间（图4）和80%置信区间（图5），但未明确说明p值或重复次数。
- **公平性与客观性**：实验设计较为系统，但仅局限于3个开源LLM和一类SAE，未涵盖更大范围模型或SAE变体；受限于50个特征/层，可能存在采样偏差。

## 6. 论文的主要结论与发现

1. **相似性负样本更有效**：语义相似的非激活句子比随机采样产生更高的假阳性率，能更有效地揭露解释的召回率偏差。
2. **结构化解释格式提升一次性解释质量**：在一次性解释器中，结构化相比非结构化平均提升5.8%-9.2%（3个模型）。
3. **树状解释器稳定提升**：树状解释器在非结构化格式上相对一次性解释器提升16.4%-21.6%；在结构化格式下，树状解释器无额外增益，推测其迭代过程已隐式处理了多义性。
4. **整体特征和训练负样本未带来增益**：所有模型下均未观察到显著改进，提示LLM仍难以利用上下文信息。
5. **特征复杂度与多义性随层数变化**：Gemma 2和Llama 3.1在中层达到复杂度峰值，多义性从浅层到深层递增；GPT-2则较为平稳。

## 7. 优点

- **方法创新性**：
  - 基于语义相似性的难负样本选取是新颖且自然的改进，直接弥补了现有工作忽略精确性的短板。
  - 结构化解释格式将多义性显式建模为多个组件，便于定量分析特征复杂度。
  - 树状迭代精化机制借鉴了安全领域的TAP技术，并成功迁移到可解释性任务。
- **实验全面性**：在3个不同规模/架构的LLM上测试，覆盖8层，比较了多种解释生成策略和负样本策略，消融实验完整。
- **可复现性**：提供了开源代码和详细提示模板（附录A），鼓励后续研究。
- **实用性**：改进后的解释更精确，便于对SAE特征进行大规模自动分析，例如跨层多义性趋势的研究。

## 8. 不足与局限

- **计算成本较高**：树状解释器每特征约1.5分钟，在数千特征规模下可能难以承受。
- **实验覆盖有限**：
  - 仅测试了3个开源LLM（Gemma 2 9B, Llama 3.1 8B, GPT-2 Small），未包含更大或更小的模型。
  - SAE仅使用了固定宽度（16k/32k），未探索不同稀疏性/宽度的影响。
  - 仅分析每层前50个特征，可能遗漏重要或稀有模式。
- **评估指标单一**：主要依赖皮尔逊相关系数，虽为标准做法，但该指标可能无法完全反映解释的语义合理性。
- **反馈循环的局限性**：训练负样本和整体特征未带来提升，说明当前LLM模拟器/解释器尚无法有效利用复杂上下文，这可能是未来改进方向。
- **解释质量的主观性**：复杂度评分依赖LLM法官（gemma-2-27b-it），可能引入模型偏好；多义性度量基于阈值设定（90%最大得分），有一定随意性。
- **可泛化性风险**：相似性负样本选取依赖Sentence Transformer的质量，若其与目标特征分布不一致，可能失效。

（完）
