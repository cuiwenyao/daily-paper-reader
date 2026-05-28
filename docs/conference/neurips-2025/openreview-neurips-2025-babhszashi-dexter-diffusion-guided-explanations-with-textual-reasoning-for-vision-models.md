---
title: "DEXTER: Diffusion-Guided EXplanations with TExtual Reasoning for Vision Models"
title_zh: "DEXTER: 扩散引导的视觉模型文本推理解释"
authors: "Simone Carnemolla, Matteo Pennisi, Sarinda Samarasinghe, Giovanni Bellitto, Simone Palazzo, Daniela Giordano, Mubarak Shah, Concetto Spampinato"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=baBhSzaSHI"
tags: ["query:ns-xai"]
score: 4.0
evidence: 使用大语言模型生成视觉模型的文本解释
tldr: 针对视觉模型解释缺乏训练数据的问题，提出DEXTER框架，融合扩散模型与大语言模型，通过优化文本提示合成类条件图像，并生成自然语言报告描述分类器的决策模式和偏见。实验表明无需真实标签即可获得可读解释，增强了模型透明度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 728, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 882, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 1273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1316, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1288, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 700, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1015, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1014, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 688, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 702, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-babhszashi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 700, \"height\": 469, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 885, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1318, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1315, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 886, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 877, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1132, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 671, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 560, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 665, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 851, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 757, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1457, \"height\": 2194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-babhszashi/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 290, \"label\": \"Table\"}]"
motivation: 现有视觉模型解释方法依赖训练数据或目标标签，缺乏通用性。
method: 利用扩散模型和大语言模型，通过文本提示优化合成图像，再生成文本解释。
result: 在无训练数据条件下成功生成有意义的分类决策解释。
conclusion: DEXTER提供了一种数据自由的视觉模型解释方案，可推广到多种分类器。
---

## Abstract
Understanding and explaining the behavior of machine learning models is essential for building transparent and trustworthy AI systems. We introduce DEXTER, a data-free framework that employs 
diffusion models and large language models to generate global, textual explanations of visual classifiers. DEXTER operates by optimizing text prompts to synthesize class-conditional images that strongly activate a target classifier. These synthetic samples are then used to elicit detailed natural language reports that describe class-specific decision patterns and biases. Unlike prior work, DEXTER enables natural language explanation 
about a classifier's decision process without access to training data or ground-truth labels. We demonstrate DEXTER's flexibility across three tasks—activation maximization, slice discovery and debiasing, and bias explanation—each illustrating its ability to uncover the internal mechanisms of visual classifiers. Quantitative and qualitative evaluations, including a user study, show that DEXTER produces accurate, interpretable outputs. Experiments on ImageNet, Waterbirds, CelebA, and FairFaces confirm that DEXTER outperforms existing approaches in global model explanation and class-level bias reporting. Code is available at https://github.com/perceivelab/dexter.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义

**研究动机**：深度视觉分类器（例如 ImageNet 训练的 CNN）的决策过程缺乏透明度，常常依赖背景纹理、光照等伪相关特征（spurious correlations）做出预测，而非真正的目标语义特征。现有的可解释性方法（如 GradCAM、Integrated Gradients）多提供局部归因解释，需要训练数据且难以提供人类可理解的全局推理模式；激活最大化（Activation Maximization）生成的图像往往抽象难懂；自然语言解释（NLE）方法通常依赖标注数据或预训练的视觉-语言映射。

**核心问题**：如何在**无需训练数据或真实标签**的情况下，系统性地揭示视觉分类器的全局决策模式、偏见和内部表征，并以**人类可读的文本形式**呈现？

**整体含义**：DEXTER 框架结合扩散模型（Stable Diffusion）与大语言模型（LLM），通过优化文本提示（prompt）生成类条件图像来最大化目标分类器的激活，再借助 LLM 对图像进行推理，生成可解释的全局文本报告。该方法完全无数据依赖，适用于激活最大化、切片发现与去偏、偏见解释三个任务，提高了模型透明度和可信度。

## 2. 论文提出的方法论

### 核心思想
- 利用**可学习的软提示（soft prompt）** 引导 BERT 填充掩码令牌，生成离散的硬提示（hard prompt）。
- 硬提示通过翻译矩阵映射到 CLIP 词表，输入 Stable Diffusion 生成图像，图像损失（激活最大化损失）反向传播更新软提示。
- 生成的图像被正确分类后，使用视觉-语言模型（VLM，如 GPT-4o mini）生成描述，再汇聚为文本偏见报告。

### 关键技术细节
1. **文本管线**：
   - 固定文本 + N 个 `[MASK]` 令牌，拼接可学习的软提示 `p`（P 个向量，维度 d=768）。
   - BERT 输出掩码位置的 logits，经 Gumbel-Softmax 得到离散令牌。
   - 使用翻译矩阵 `M`（BERT→CLIP 词表）将令牌映射到 CLIP 词表，保证 Stable Diffusion 可理解。

2. **视觉管线**：
   - 生成的文本提示经 CLIP 文本编码器得到嵌入 `e`，输入 Stable Diffusion 生成图像。
   - 图像经目标视觉分类器 `f` 计算选定的 K 个神经元的激活值 `n`。
   - 激活最大化损失 `L_act`：对于特征神经元用负值，对于类神经元用负对数。

3. **辅助掩码伪标签预测**：
   - 为每个掩码位置维护伪标签 `y_i` 和参考损失 `L_i`，跟踪历史聚合损失。
   - 添加交叉熵损失 `L_mask` 帮助伪标签与激活模式对齐，防止随机波动。

4. **整体损失**：
   \[
   L = \sum_{k=1}^K l_{act}(n_k) - \sum_{i=1}^N \log s_{i, y_i}
   \]

### 算法流程（文字说明）
1. 初始化软提示 `p`。
2. 循环迭代（如 5000 步）：
   - 将 `p` 与固定文本及掩码令牌输入 BERT。
   - 获得掩码 logits，通过 Gumbel-Softmax 得到预测令牌，映射到 CLIP 词表。
   - 计算 CLIP 文本嵌入，生成图像。
   - 计算分类器激活损失和辅助损失，更新 `p`。
3. 训练结束后，用最终提示生成多个图像（如 100 张），仅保留正确分类的样本。
4. 使用 VLM 对图像进行描述，再汇总为偏见报告。

## 3. 实验设计

### 数据集
- **SalientImageNet**：30 个类别（15 个含伪相关特征，15 个为真相关特征），用于视觉解释和激活最大化评估。
- **Waterbirds**：水鸟/陆地鸟分类，背景与标签存在伪相关，用于切片发现。
- **CelebA**：20 万面部图像，40 个二元属性，用于切片发现和去偏。
- **FairFaces**：10 万面部图像，平衡种族、性别、年龄，用于偏见文本解释评估。

### Benchmark
- **视觉解释**：对比 DiffExplainer、GAN 类方法（Yosinski et al.、Mahendran and Vedaldi、Nguyen et al.）。
- **切片发现与去偏**：对比 ERM、LfF、GEORGE、JTT、CNC、DRO、LADDER、DRO-B2T（Bias-to-Text）。
- **偏见解释**：与基于训练集生成的报告（相同流水线）比较，采用 STS、G-eval、人类 MOS 等指标。

### 对比方法
- DiffExplainer（最新扩散解释方法）
- GradCAM（归因基线）
- B2T、LADDER 等偏见发现方法
- 多种激活最大化方法

## 4. 资源与算力

论文明确指出：
- 硬件：3 块 H100 GPU。
- 半精度（half-precision）训练。
- 每个类别的提示优化约 10 分钟。
- 生成 100 张图像及最终偏见报告约 15 秒（无需反向传播）。
- 未提供总训练时长，但指出适用于离线全局审计。

## 5. 实验数量与充分性

- **三大任务**：激活最大化、切片发现与去偏、偏见解释。
- **多个数据集**：SalientImageNet（30 类）、Waterbirds、CelebA、FairFaces，覆盖了 4 个常用可解释性/公平性数据集。
- **消融实验**：
  - 比较四种提示策略（Baseline、ChatGPT、DiffExplainer、DEXTER）。
  - 单字 vs. 多字提示；有无辅助损失 `L_mask`；软提示数量 P 的影响。
  - 偏见传播与 LLM 幻觉评估：注入对抗性初始提示、将报告中的视觉线索加入生成提示检查激活提升。
- **用户研究**：100 名 MTurk 工作者，评估视觉解释对齐性和报告质量。
- **统计验证**：卡方检验（p=0.032）、TOST 检验（MOS LLM vs. MOS humans p<0.05）、配对 t 检验和 Wilcoxon 检验（幻觉评估均显著）。

**充分性评定**：实验设计较全面，覆盖了多个任务、数据集和对比方法，并提供了统计显著性和误差棒。但切片发现任务仅在 Waterbirds 和 CelebA 上测试，对更多模型架构（如 ViT、AlexNet、ResNet50 等）仅在偏见分析部分进行了定性展示。

## 6. 论文的主要结论与发现

1. **无数据全局解释可行**：DEXTER 在不使用训练数据或标签的情况下，成功生成与分类器行为高度一致的文本报告。
2. **激活最大化优于现有方法**：在 SalientImageNet 上，DEXTER 的激活得分（75.43）显著高于 DiffExplainer（39.83）和 ChatGPT 描述（59.87）。
3. **切片发现去偏性能领先**：在 CelebA 最差切片准确率上 DEXTER 达到 91.3%，超过所有对比方法；在 Waterbirds 上相当（90.5%）。
4. **偏见报告与人类及训练数据一致**：STS 达 0.90，人类 MOS 4.01，G-eval 一致性 4.19，证明报告可读且忠实。
5. **鲁棒性良好**：注入偏见初始提示仍能恢复正确特征，报告提取的视觉线索可提升分类器激活 16.33 个百分点。

## 7. 优点

- **无数据依赖**：仅需目标分类器即可工作，适用于数据不可见或隐私敏感场景。
- **多任务泛化**：统一框架处理激活最大化、切片发现、偏见解释。
- **可解释性强**：输出自然语言报告，比纯视觉解释更易理解。
- **设计巧妙**：使用 Gumbel-Softmax + 翻译矩阵实现端到端可微；辅助伪标签损失加速收敛并提高稳定性。
- **评估严谨**：包括人类用户研究、LLM 辅助评分、统计检验、幻觉鲁棒性验证。

## 8. 不足与局限

- **计算成本**：每类优化约 10 分钟，对大规模类别（如 ImageNet-1000）可能耗时较长，仅适用于离线审计。
- **依赖外部模型**：依赖 Stable Diffusion 和 GPT-4o mini，存在 NSFW 内容或 LLM 幻觉风险（论文通过安全检查器和幻觉分析部分缓解）。
- **实验覆盖有限**：切片发现仅测试了两个数据集；对不同架构（CNN、ViT）的偏见分析多为定性。
- **未探索多模态模型**：论文指出未来工作扩展至多模态模型，当前仅处理视觉分类器。
- **标准偏差较大**：部分实验（如 Table 3）标准差较高，因不同类别激活难度差异大。

（完）
