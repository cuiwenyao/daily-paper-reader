---
title: "Right for the Right Reasons: Avoiding Reasoning Shortcuts via Prototypical Neurosymbolic AI"
title_zh: 正确理由：通过原型神经符号AI避免推理捷径
authors: "Luca Andolfi, Eleonora Giunchiglia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eb71SNTjux"
tags: ["query:ns-xai"]
score: 9.0
evidence: 原型神经符号AI避免推理捷径
tldr: 神经符号AI易通过虚假相关满足符号约束（推理捷径）。本文提出原型神经符号架构，利用原型学习理论确保模型学到正确基本概念，即使在极低数据下也能基于正确理由推理。从根源上解决可解释性缺失问题，使神经符号集成更可信。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 239, \"height\": 337}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 496, \"height\": 348}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 793, \"height\": 248}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 894, \"height\": 297}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 927, \"height\": 298}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 357}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 514, \"height\": 327}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 574, \"height\": 155}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1294, \"height\": 401}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1318, \"height\": 416}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1449, \"height\": 1941}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1338, \"height\": 253}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1264, \"height\": 1849}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1412, \"height\": 736}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1413, \"height\": 733}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1413, \"height\": 361}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 752}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 733, \"height\": 736}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 705, \"height\": 573}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 544, \"height\": 258}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1372, \"height\": 492}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 758, \"height\": 286}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 747, \"height\": 257}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1033, \"height\": 926}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1287, \"height\": 1979}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1303, \"height\": 596}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1311, \"height\": 1504}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1188, \"height\": 374}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1175, \"height\": 255}]"
motivation: 神经符号模型常利用虚假相关满足约束，未能学到正确概念。
method: 引入原型学习理论，构建原型神经符号架构，强制模型学习因果正确的概念表示。
result: 在低数据场景下有效避免捷径推理，保持高准确率且且概念学习正确。
conclusion: 原型方法显著提升神经符号模型的可解释性和鲁棒性。
---

## Abstract
Neurosymbolic AI is growing in popularity thanks to its ability to combine neural perception and symbolic reasoning in end-to-end trainable models. However, recent findings reveal these are prone to shortcut reasoning, i.e., to learning unindented concepts--or neural predicates--which exploit spurious correlations to satisfy the symbolic constraints. In this paper, we address reasoning shortcuts at their root cause and we introduce Prototypical Neurosymbolic architectures. These models are able to satisfy the symbolic constraints (be right) because they have learnt the correct basic concepts (for the right reasons) and not because of spurious correlations, even in extremely low data regimes. Leveraging the theory of prototypical learning, we demonstrate that we can effectively avoid reasoning shortcuts by training the models to satisfy the background knowledge while taking into account the similarity of the input with respect to the handful of labelled datapoints. We extensively validate our approach on the recently proposed rsbench benchmark suite in a variety of settings and tasks with very scarce supervision: we show significant improvements in learning the right concepts both in synthetic tasks (MNIST-EvenOdd and Kand-Logic) and real-world, high-stake ones (BDD-OIA). Our findings pave the way to prototype grounding as an effective, annotation-efficient strategy for safe and reliable neurosymbolic learning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：神经符号AI（NeSy）模型虽然能结合神经网络感知与符号推理进行端到端训练，但近年研究发现它们极易陷入**推理捷径**（reasoning shortcuts）。即模型学习到的是利用虚假相关（spurious correlations）来满足符号约束的神经谓词，而非真正意图的概念。这导致模型虽然输出正确标签（be right），但学习的原因却是错误的（wrong reasons）。
- **背景**：现有缓解策略存在实际权衡：密集标注成本高（如[29]要求每个概念所有数据点都标注）；无监督方法（如联合重构损失、香农熵）仅在有限场景有效，在rs-bench的挑战性场景中失败。
- **本文目标**：从根源上解决推理捷径，提出**原型神经符号架构**，使模型在极低标注数据下也能学到正确的概念，从而实现“基于正确理由的正确判断”。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 在每次权重更新时，同时考虑两个可能正交的因素：
  1. **满足背景知识与可用标注**（NeSy方法自然做到）
  2. **输入与少量标注数据的相似性**（原型网络提供）
- 通过原型网络锚定概念表示，即使只有极少标注示例，也能避免模型利用虚假相关满足约束。

### 关键技术细节
1. **原型提取器**（prototype extractor）：为每组互斥概念（如数字0-9）训练一个嵌入函数 \(f^i_\theta: \mathbb{R}^d \to \mathbb{R}^{m_i}\)，通过支持集计算每个概念的原型（centroid）：
   \[
   c_c = \frac{1}{|\hat{S}_c|} \sum_{x \in \hat{S}_c} f^i_\theta(x)
   \]
2. **距离度量**：使用平方欧氏距离，属于Bregman散度族，允许对未标记类别的原型进行有意义初始化。
3. **概念分布**：基于softmax计算：
   \[
   p_\theta(c|x, c\in[h_i]) = \frac{\exp(-\|z_i - c_c\|_2^2)}{\sum_{c'\in[h_i]}\exp(-\|z_i - c_{c'}\|_2^2)}
   \]
4. **未标记类别原型初始化**：若某个概念完全没有标注数据，则利用已知原型信息，通过高斯噪声初始化其原型，确保落在已知原型所张成的超球内（概率99%），避免原型坍塌。
5. **训练过程**（算法1）：每轮训练从支持集中随机采样子集计算原型，对查询集计算原型损失（软max交叉熵），同时对所有未标注数据计算NeSy损失（如语义损失）。两部分损失加和更新参数。

### 理论结果
- **定理4.1**：原型NeSy模型中，嵌入 \(z_i\) 的梯度更新包含两项：约束违反程度（\(\partial L_{\text{NeSy}}/\partial y_c\)）和嵌入与每个原型的接近程度（\(y_c\)）。标准NN的更新则仅依赖NeSy损失，无法利用相似性。
- **推论4.2**：使用语义损失时，梯度更新进一步将嵌入拉向各原型，修正概率 \(y_c\) 与基于知识约束的后验期望之差。
- **命题5.1**：在理想化假设下（可分离嵌入空间），原型NeSy模型允许的确定性推理捷径数量与“每个概念至少一个标注数据”情况下的数量相同，即大幅减少捷径。

## 3. 实验设计

### 数据集与场景
- **合成任务**：
  - **MNIST-EvenOdd**：MNIST数字加法变体，只有偶数+偶数或奇数+奇数对，测试时出现未见过组合。训练集6720样本，验证1920，测试960。
  - **Kand-Logic**：基于康定斯基图案，三个几何原语（形状+颜色）需推断模式（全同形状或全同颜色）。训练4000，验证/测试各1000。
- **真实世界高价值任务**：
  - **BDD-OIA**：自动驾驶行为决策，需从21个概念（如红灯、行人）中推理正确行为（前进、停止等）。约22.5k帧，每帧使用Faster-RCNN提取2048维特征。数据极不平衡且标签有噪声。

### Benchmark
- 使用**rs-bench**基准套件，该套件专门设计用于测试推理捷径。

### 对比方法
- **基线NeSy模型**：DeepProbLog (DPL)、Logic Tensor Networks (LTN)、Semantic Loss (SL)、Coherent by Construction Networks (CCN+)。
- **原型集成**：在各基线基础上加入原型提取器（记为+PNet）。
- **其他缓解策略**（来自[29]）：
  - R：重构损失
  - H：香农熵正则化
  - C：部分概念密集标注（标注“4”和“9”所有出现）
  - C(S)⋆：利用原型支持集做概念监督（数据增强后）
  - Pre⋆：在支持集上预训练骨干网络
- 所有实验使用10个随机种子（0,128,256,512,1024,2048,4096,8192,16384,32768）报告均值与标准差。

## 4. 资源与算力

- **硬件**：Intel Xeon CPU E5-2620 v3 @ 2.40GHz（24核48线程），4块NVidia TITAN Xp GPU（12GB GDDR5X, 3840 CUDA Cores）。
- **软件**：Ubuntu 20.04.5 LTS, CUDA 12.2, Python 3.20, PyTorch 1.13.0。
- **训练时长**：论文中未明确给出每个实验的具体运行时间或总计算量。仅提及epoch数（MNIST-EvenOdd和Kand-Logic为10，BDD-OIA为40）以及其他超参数。因此，无法量化总计算资源消耗。

## 5. 实验数量与充分性

### 实验组数
- **RQ1**（能否避免推理捷径）：对三个数据集，每个数据集3个NeSy模型×原型变体，共约9个主要实验；加上各基线（预训练、数据增强等），表格8/10/11/12涉及大量变体。
- **RQ2**（与其他缓解策略对比）：在MNIST-EvenOdd上对R、H、C及其组合共12种设置，每个设置3个模型，共约36个实验。
- **RQ3**（对未标注数据比例鲁棒性）：10个不同未标注比例（10%~100%步长10%），两种系列（PNet vs. Pre⋆+C(S)⋆），共20条曲线，每条曲线包含10个种子。
- **RQ4**（未标注类别影响）：在MNIST-EvenOdd上逐步隐藏1~8个数字类别（共9类），在Kand-Logic上隐藏1~2个概念，每个设置5次随机，共约50+实验。
- **RQ5**（原型初始化影响）：不同p值（0.2, 0.5, 0.99），不同隐藏类别数量，共3×9=27组。

### 充分性评价
- **充分**：覆盖了合成和真实任务，对比了多种基线、缓解策略、消融条件，使用多随机种子保证统计稳定性。
- **公平**：与现有最佳缓解策略（R+H+C等）在相同设置下比较，并控制标签数量（支持集相同）。
- **局限**：未在更大规模或不同领域（如NLP）验证；理论分析依赖理想化假设（[A1],[A2],[A3]）；仅考虑特定几种NeSy模型。

## 6. 主要结论与发现

1. **原型NeSy模型能有效避免推理捷径**：
   - MNIST-EvenOdd：仅一个标注每类，概念F1从<5%提升至>95%，概念坍塌降至0%。
   - Kand-Logic：概念F1从~25%提升至94%，标签准确率显著提升。
   - BDD-OIA：概念F1从0.08提升至0.16，概念坍塌从0.82降至0.35。
2. **显著优于其他缓解策略**：
   - 在MNIST-EvenOdd上，原型方法（+PNet）在所有指标上达到或超过R+H+C组合（需要密集概念标注），且无需额外密集标注。
3. **鲁棒性**：
   - 即使未标注数据比例从10%到100%变化，原型NeSy模型保持稳定高F1(C)和零概念坍塌；标准模型则波动大、坍塌严重。
4. **对未标注类别容忍度高**：
   - 即使多个类别完全无标注（如隐藏8个数字类），原型方法仍能得到远优于基线的概念学习。
5. **初始化策略重要性**：
   - 使用高概率p=0.99的超球初始化比低p值显著更好，避免原型坍塌。

## 7. 优点

- **方法新颖**：首次将原型网络与神经符号AI结合，从根源上解决推理捷径，而非事后缓解。
- **理论扎实**：推导了嵌入更新公式，刻画了原型如何同时考虑约束满足和相似性；分析了确定性捷径数量减少的理论保证。
- **实验全面**：覆盖合成和真实高风险任务，对比多种主流缓解策略，包含大量消融实验和鲁棒性分析。
- **低标注成本**：只需每类一个标注即可有效避免捷径，远低于密集标注方案。
- **可解释性**：原型提供了概念级别的理解，提升模型透明度和可信度。

## 8. 不足与局限

- **理论假设**：命题5.1依赖于可分离嵌入等理想假设，实际数据中可能不严格成立，导致实际捷径数可能高于理论值。
- **实验覆盖有限**：
  - 仅在图像领域（MNIST、Kandinsky、自动驾驶）测试，未涉及文本、表格或更多样化的NeSy应用。
  - 仅评估了三种典型NeSy模型（DPL, LTN, SL）和CCN+，未覆盖其他范式如Neural Programmer等。
- **未提供计算成本量化**：尽管描述了硬件，但未报告训练时间或总能耗，读者难以评估效率。
- **BDD-OIA性能仍有限**：虽然改进明显，但概念F1仅0.16，仍很低，说明真实世界噪声、不平衡、标签错误挑战巨大。
- **原型初始化对未知类别敏感**：当未知类别过多（>4个）时性能下降，需要至少2个已知类别来稳定计算。
- **无理论保证泛化**：原型方法依赖支持集代表性，若训练分布与测试分布差异过大，效果可能退化。

（完）
