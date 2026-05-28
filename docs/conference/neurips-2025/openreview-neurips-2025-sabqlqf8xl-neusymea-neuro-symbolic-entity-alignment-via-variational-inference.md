---
title: "NeuSymEA: Neuro-symbolic Entity Alignment via Variational Inference"
title_zh: NeuSymEA：基于变分推断的神经符号实体对齐
authors: "Shengyuan Chen, Zheng Yuan, Qinggang Zhang, Wen Hua, Jiannong Cao, Xiao Huang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=SAbQLqf8XL"
tags: ["query:ns-xai"]
score: 6.0
evidence: 神经符号实体对齐，结合神经和符号模型
tldr: 实体对齐中符号模型精确但受限于结构异质性，神经模型有效但缺乏可解释性。本文提出NeuSymEA统一框架，将神经模型与符号规则结合在马尔可夫随机场中，通过变分EM算法优化，既保留符号推理的精确性又融合神经模型的鲁棒性，实验证明在多个KG对齐任务上性能优异且更具可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1318, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1301, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sabqlqf8xl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 398, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1461, \"height\": 1017, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 1171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1459, \"height\": 835, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1013, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 664, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sabqlqf8xl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 950, \"height\": 181, \"label\": \"Table\"}]"
motivation: 现有实体对齐方法中，符号模型与神经模型各有优劣，缺乏统一框架同时利用两者优势。
method: 将神经模型与符号规则集成于马尔可夫随机场，使用变分EM算法联合优化。
result: 在多个知识图谱对齐数据集上，NeuSymEA在准确率和鲁棒性上超过纯神经或纯符号方法。
conclusion: 为知识图谱融合提供了兼具精确性和可解释性的神经符号解决方案。
---

## Abstract
Entity alignment (EA) aims to merge two knowledge graphs (KGs) by identifying equivalent entity pairs. Existing methods can be categorized into symbolic and neural models. Symbolic models, while precise, struggle with substructure heterogeneity and sparsity, whereas neural models, although effective, generally lack interpretability and cannot handle uncertainty. We propose NeuSymEA, a unified neuro-symbolic reasoning framework that combines the strengths of both methods to fully exploit the cross-KG structural pattern for robust entity alignment. NeuSymEA models the joint probability of all possible pairs' truth scores in a Markov random field, regulated by a set of rules, and optimizes it with the variational EM algorithm. In the E-step, a neural model parameterizes the truth score distributions and infers missing alignments. In the M-step, the rule weights are updated based on the observed and inferred alignments, handling uncertainty. We introduce an efficient symbolic inference engine driven by logic deduction, enabling reasoning with extended rule lengths. NeuSymEA achieves a significant 7.6\% hit@1 improvement on $DBP15K_{ZH-EN}$ compared with strong baselines and demonstrates robustness in low-resource settings, achieving 73.7\% hit@1 accuracy on $DBP15K_{FR-EN}$ with only 1\% pairs as seed alignments. Codes are released at https://github.com/chensyCN/NeuSymEA-NeurIPS25.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
实体对齐（EA）旨在通过识别不同知识图谱（KG）间的等价实体对来合并图谱。现有方法分为符号模型和神经模型：符号模型（如PARIS）精确但受限于子结构异质性和稀疏性，对低度实体召回率低；神经模型（如GCN、翻译模型）有效但缺乏可解释性，且无法处理不确定性。现有神经符号方法将两者作为独立组件简单叠加，缺乏统一优化目标。为此论文提出**NeuSymEA**，一个统一的神经符号推理框架，通过变分推断将两者有机融合，同时利用符号推理的精确性和神经模型的鲁棒性，实现更鲁棒且可解释的实体对齐。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将所有可能实体对的真值（truth score）的联合概率建模在马尔可夫随机场中，并用一组加权规则约束，通过变分EM算法联合优化神经模型参数和规则权重。
- **关键技术细节**：
  - **变分EM框架**：
    - **E-step**：固定规则权重，用神经模型参数化真值分布，推断缺失对齐。神经模型通过训练拟合符号模型给出的伪标签（当概率 \(p_w(v|v_O) > \delta\) 时视为正样本），并结合观测对齐进行监督学习。
    - **M-step**：固定神经模型，根据观测和推断的对齐更新规则权重。通过贪婪的一对一匹配（避免假阳性）从神经模型中获得高置信伪标签，然后最大化完整数据的对数似然。
  - **高效推理与规则分解**：
    - 通过逻辑演绎将任意长度的长规则分解为多个单位长度的子规则，避免指数级搜索空间。推理时迭代使用单位规则进行消息传递，权重更新简化为更新子关系概率 \(p_{sub}(r \subseteq r')\)，并利用关系独特性 \(\eta(r)\) 量化置信度。
  - **可解释性**：训练后的符号模型可作为解释器，通过广度优先搜索生成支持路径，并提供硬锚点模式（仅用预对齐对）和软锚点模式（加入推断的对）两种解释方式。

### 3. 实验设计
- **数据集**：主要使用DBP15K（三个跨语言对：ZH-EN、JA-EN、FR-EN），包括完整版（含低度实体，更稀疏）和浓缩版（去除低度实体）。额外使用OpenEA和DBP1M评估大规模场景。
- **基准与对比方法**：
  - 神经模型：GCNAlign、BootEA、AlignE、RREA、Dual-AMN、LightEA、PEEA
  - 符号模型：PARIS
  - 神经符号模型：PRASE、EMEA
- **评价指标**：Hit@1、Hit@10、MRR（对符号模型将召回视为Hit@1）。
- **实验场景**：
  - 主实验：在完整版和浓缩版DBP15K上对比。
  - 低资源实验：训练比例从1%到20%。
  - 大规模实验：OpenEA100K和DBP1M上的Hit@1和运行效率。
  - 参数分析：EM迭代次数（1-9）和阈值δ（0.6-0.99）的影响。
  - 可解释性分析：正负样本的规则置信度分布，不同规则长度下的支持规则数量。
  - 消融分析（隐含在EM迭代过程中）：规则推断与神经模型MRR的演化。

### 4. 资源与算力
论文明确给出硬件配置：**NVIDIA GeForce RTX 3090 GPU**，CPU为Intel Xeon Silver 4214R @ 2.40GHz。运行时**约15分钟**，内存消耗**868 MB**，GPU显存使用**4.33 GB**。未说明是否使用多GPU或多机训练，但实验均单GPU完成。

### 5. 实验数量与充分性
- **实验数量**丰富：覆盖3个数据集（各含两种版本）、多种训练比例（4种）、两个大规模KG、参数扫描（迭代×阈值共63组）、可解释性分析等。
- **充分性与公平性**：
  - 对比方法包括近年SOTA（如LightEA、EMEA），且基线与文献结果一致。
  - 使用OpenEA的官方2:1:7划分策略，确保公平比较。
  - 对Dual-AMN、LightEA等采用迭代版本，保证最强基线。
  - 消融分析（EM迭代中的规则与嵌入交互）揭示了组件贡献。
  - 参数分析表明算法对阈值不敏感，收敛快。
- **综合评估**：实验设计系统，涵盖了不同规模、稀疏度、低资源情景，结果统计稳健（图3有误差线）。

### 6. 论文的主要结论与发现
- **性能大幅领先**：NeuSymEA在DBP15K所有语言对上达到SOTA，尤其是在完整版ZH-EN上Hit@1相对最好基线提高7.6%（0.801 vs 0.725）。
- **低资源强鲁棒**：仅用1%种子对齐即可在FR-EN上取得73.7% Hit@1，超越许多模型用20%数据的表现。
- **规则与嵌入协同进化**：EM迭代中规则推断出的伪标签精度高，反过来提升神经模型MRR，收敛迅速。
- **可解释性有效**：正负样本的规则置信度分布显著分离，且软锚点模式能为孤立实体对提供更多支持规则。
- **大规模可扩展**：在OpenEA100K和DBP1M上仍保持高效，神经组件随数据集增大效率提升（GPU利用率高），符号组件支持并行处理。

### 7. 优点
- **统一变分EM框架**：首次将神经和符号模型在概率框架下联合优化，而非简单拼接，保证了目标一致性。
- **逻辑分解规避指数爆炸**：通过单位规则分解与迭代推理，使长规则推理复杂度线性于长度，实用性强。
- **可解释性双模式**：软锚点模式利用推断对齐增强支持，为孤立实体提供多跳解释，填补了现有EA方法缺乏可解释性的空白。
- **鲁棒性突出**：在不同数据集规模和稀疏度下均表现稳定，低资源场景尤其优于所有基线。
- **代码开源**：提供完整代码和配置，便于复现。

### 8. 不足与局限
- **多KG扩展性**：目前仅支持双KG对齐，扩展到多个KG（如循环两两对齐）可能效率低下，需更复杂的优化机制。
- **高精度下假阳性风险**：M-step中贪婪的一对一匹配虽然减少假阳性，但可能漏掉正确对齐，尤其在密集实体区域。
- **规则依赖设定**：规则长度L和阈值δ需人工设定，虽实验表明不敏感，但理论上最优值可能因数据分布而异。
- **实验覆盖有限**：未在更异构、更弱监督（如带噪声的对齐）场景中测试；未与最新的大语言模型驱动EA方法对比。
- **计算开销**：尽管高效，但对于超大规模KG（十亿级实体）仍需进一步优化符号推理的二次复杂度。

（完）
