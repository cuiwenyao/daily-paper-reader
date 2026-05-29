---
title: "From Black-box to Causal-box: Towards Building More Interpretable Models"
title_zh: 从黑箱到因果箱：构建更可解释的模型
authors: "Inwoo Hwang, Yushu Pan, Elias Bareinboim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2w64oCNRFV"
tags: ["query:ns-xai"]
score: 7.0
evidence: 因果可解释性框架用于可解释推理
tldr: 深度学习模型在高风险应用中的可解释性至关重要，但现有模型难以回答反事实查询。本文定义因果可解释性形式化条件，证明黑箱和概念预测器通常不具备该性质，并提出构建因果可解释模型的框架，有助于揭示模型推理过程。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1304, \"height\": 883}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1331, \"height\": 401}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1162, \"height\": 483}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1370, \"height\": 436}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1280, \"height\": 395}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1392, \"height\": 357}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1296, \"height\": 292}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 400, \"height\": 318}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 402, \"height\": 321}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1222, \"height\": 423}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1412, \"height\": 1026}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2w64ocnrfv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 454, \"height\": 377}]"
motivation: 现有模型难以回答反事实查询，缺乏对推理过程的深层解释。
method: 定义因果可解释性，分析黑箱和概念模型不足，设计构建因果可解释模型的方法。
result: 证明常见模型类不满足因果可解释性，新框架可生成满足条件的模型。
conclusion: 因果可解释性为评估和设计可解释模型提供理论基础。
---

## Abstract
Understanding the predictions made by deep learning models remains a central challenge, especially in high-stakes applications. A promising approach is to equip models with the ability to answer counterfactual questions -- hypothetical ``what if?'' scenarios that go beyond the observed data and provide insight into a model reasoning. In this work, we introduce the notion of causal interpretability, which formalizes when counterfactual queries can be evaluated from a specific class of models and observational data. We analyze two common model classes -- blackbox and concept-based predictors -- and show that neither is causally interpretable in general. To address this gap, we develop a framework for building models that are causally interpretable by design. Specifically, we derive a complete graphical criterion that determines whether a given model architecture supports a given counterfactual query. This leads to a fundamental tradeoff between causal interpretability and predictive accuracy, which we characterize by identifying the unique maximal set of features that yields an interpretable model with maximal predictive expressiveness. Experiments corroborate the theoretical findings.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：深度学习模型在医疗、法律等高风险应用中缺乏可解释性，现有模型难以回答反事实问题（如“若某特征改变，预测会如何变化？”）。  
- **背景**：传统黑箱模型（BP）和概念模型（CP）被广泛认为能提供一定解释性，但作者指出它们无法保证对同一反事实查询给出一致答案，即模型类内存在不一致性。  
- **动机**：形式化“因果可解释性”，明确何种模型架构能用观测数据可靠计算反事实，并构建可解释模型。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：引入**因果可解释性**（Definition 2）——如果一个模型类中所有与观测分布一致的模型对某个反事实查询给出相同答案，则称该类是因果可解释的。  
- **关键技术细节**：
  - 定义**增强结构因果模型（ASCM）**：包含生成过程（概念 V、图像 X、预测标签 Ŷ）。
  - **定理1（图准则）**：广义概念模型 Ω<sub>GCP</sub>(T) 对查询 Q(W) 是因果可解释的 **iff** T ⊆ W ∪ ND(W)（即预测所用特征必须是指定变量 W 或其非后代）。
  - **定理2（最大T-容许集唯一性）**：Max-T-Ad(W<sup>⋆</sup>) = ∩<sub>W<sub>i</sub>∈W<sup>⋆</sup></sub> (W<sub>i</sub> ∪ ND(W<sub>i</sub>))，给出了在保持可解释性前提下能使用的最多特征。
  - **定理3（闭式公式）**：当模型因果可解释时，P(Ŷ<sub>w'</sub> | x) = Σ<sub>t</sub> P(Ŷ | w'∩T, t\W) P(t | x)，即反事实可通过两步计算：特征提取器和分类器。
  - **定理4（权衡）**：因果可解释性与预测准确率之间存在根本权衡——特征集越大，可回答的反事实查询越少；反之亦然。

### 3. 实验设计：数据集、场景、对比方法

- **数据集**：
  - **BarMNIST**（合成）：修改的MNIST，包含特征“条（B）”“数字（D）”“颜色（C）”，具有已知因果关系和ground truth反事实。
  - **CelebA**（真实）：人脸属性数据集，标签为“吸引力”，特征包括“微笑”“性别”“颧骨”等。
- **场景**：测试不同特征集 T 下的模型准确率和对反事实（如“若微笑→不微笑，吸引力预测如何变化”）的估计误差。
- **对比方法**：论文主要在同一框架下比较不同 T 选择（如 T={B,D,C} vs. {D,C} vs. {D}等），未与其他XAI方法（如LIME、SHAP）对比，而是强调理论预测与实验的一致性。

### 4. 资源与算力

- **明确信息**：作者在附录B中说明使用**单个NVIDIA A100 GPU**。
- 训练参数：BarMNIST epoch=100，batch size=1024；CelebA epoch=100，batch size=512。
- 未给出总训练时长，但可推断所需算力中等。

### 5. 实验数量与充分性

- **实验数量**：
  - BarMNIST：4种特征集对比（准确率 + 3种反事实查询估计），另在附录增加一种不同图结构的实验。
  - CelebA：定性展示（图7）和定量平均差异（图11-b），以及实例对比（图11-c）。
  - 附录还提供了误差线（5次独立运行）。
- **充分性分析**：
  - 实验设计紧扣理论（验证图准则和唯一最大集），但缺少与其他可解释性方法的直接比较。
  - 合成数据有ground truth，验证充分；真实数据只能定性评估，无法定量验证反事实正确性。
  - 消融实验仅针对特征集大小，未对特征提取器误差或不同学习率等超参数进行系统性消融。
  - 总体而言，实验对于验证理论是充分的，但对于实际应用场景的公平性比较略有不足。

### 6. 论文的主要结论与发现

- 黑箱模型和经典概念模型**均不满足**因果可解释性，无法从观测数据可靠回答反事实。
- 提出**广义概念模型（GCP）** 并使用图准则（T ⊆ W ∪ ND(W)）可确保因果可解释性。
- 存在唯一的**最大T-容许集**，使模型在保持可解释性同时最大化预测能力。
- 因果可解释性与准确率存在**根本权衡**：解释性越强（可回答更多反事实），预测准确率上限越低。
- 实验证实理论：使用非后代特征的模型可正确估计反事实，而包含后代特征的模型估计错误。

### 7. 优点

- **理论创新**：首次严格定义“因果可解释性”，从因果推断角度为模型可解释性提供形式化基础。
- **普适性**：图准则仅需知道目标变量的后代关系，无需完整因果图。
- **闭式公式**：给出可直接计算反事实的表达式，有助于实际实现。
- **揭示反事实不一致性问题**：指出即使预测准确率相同，不同模型可能给出相反反事实答案，警示了现有XAI方法的可靠性。

### 8. 不足与局限

- **实验覆盖有限**：未与其他主流XAI方法（如LIME、SHAP、Concept Bottleneck Models）进行对比实验；仅验证自身模型。
- **依赖概念提取**：实际应用中特征需要高质量标注或准确提取，误差会向下游传播（论文承认但未深入探讨）。
- **真实数据缺少ground truth**：CelebA实验无法定量验证反事实估计正确性，仅作定性展示。
- **假设因果图已知或部分已知**：在复杂任务中获取完整或部分因果关系仍具挑战。
- **仅针对单步干预**：对于嵌套反事实或多步干预未讨论。
- **应用限制**：当前方法仅适用于特征可分解为离散或连续概念的场景，对于端到端回归任务可能不直接适用。

（完）
