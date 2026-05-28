---
title: "From Black-box to Causal-box: Towards Building More Interpretable Models"
title_zh: 从黑箱到因果箱：构建更可解释的模型
authors: "Inwoo Hwang, Yushu Pan, Elias Bareinboim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2w64oCNRFV"
tags: ["query:ns-xai"]
score: 8.0
evidence: 用于深度模型的因果可解释性框架
tldr: 深度模型预测难以用反事实解释来理解。本文提出因果可解释性概念，并开发框架构建可回答反事实问题的模型。该框架超越了黑箱和概念预测器，使模型能够对假设情景进行推理。实验表明因果可解释模型在多个高保真场景中提供更可靠的洞察，提升了模型透明度与可信度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1304, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1331, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1162, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1370, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1280, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1392, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1296, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 400, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 402, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1222, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2w64ocnrfv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1412, \"height\": 1026, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2w64ocnrfv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 454, \"height\": 377, \"label\": \"Table\"}]"
motivation: 现有黑箱和概念预测器无法提供因果层面的反事实解释。
method: 形式化因果可解释性，并构建模型使其能够回答反事实查询。
result: 因果可解释模型在多个场景下提供了比传统方法更可靠的解释。
conclusion: 因果可解释框架是构建透明可信深度模型的重要方向。
---

## Abstract
Understanding the predictions made by deep learning models remains a central challenge, especially in high-stakes applications. A promising approach is to equip models with the ability to answer counterfactual questions -- hypothetical ``what if?'' scenarios that go beyond the observed data and provide insight into a model reasoning. In this work, we introduce the notion of causal interpretability, which formalizes when counterfactual queries can be evaluated from a specific class of models and observational data. We analyze two common model classes -- blackbox and concept-based predictors -- and show that neither is causally interpretable in general. To address this gap, we develop a framework for building models that are causally interpretable by design. Specifically, we derive a complete graphical criterion that determines whether a given model architecture supports a given counterfactual query. This leads to a fundamental tradeoff between causal interpretability and predictive accuracy, which we characterize by identifying the unique maximal set of features that yields an interpretable model with maximal predictive expressiveness. Experiments corroborate the theoretical findings.

---

## 论文详细总结（自动生成）

# 论文总结：From Black-box to Causal-box: Towards Building More Interpretable Models

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：深度学习模型在图像识别、自然语言处理等领域表现卓越，但本质上是“黑箱”，缺乏可解释性。在高风险场景（如医疗、法律）中，理解模型为何做出某一决策与其准确率同等重要。
- **背景问题**：现有工作尝试通过后验解释（如LIME、SHAP）或内在可解释模型（如概念瓶颈模型）来提升透明度，但这些方法无法可靠地回答反事实问题（counterfactual queries），例如“如果该患者服用另一种药物，诊断结果会如何？”。
- **核心贡献**：本文首次形式化定义了**因果可解释性**（causal interpretability），即模型类是否能够从观测数据中一致地计算出反事实查询。作者证明了黑箱模型和概念预测器（concept-based predictors）通常不具备因果可解释性，并提出了一种系统性框架，用于构建**因果可解释模型**，并揭示了因果可解释性与预测准确率之间的根本性权衡。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用结构因果模型（SCM）对数据生成过程建模，定义**增强SCM（ASCM）** 来描述特征V、图像X和预测标签Ŷ之间的关系。因果可解释性要求模型类中的所有成员在观测分布一致的情况下，对给定反事实查询输出相同结果。
- **关键技术细节**：
  - **图形化准则（Theorem 1）**：对于一组用作预测的特征T，模型类Ω_{GCP}(T)关于查询Q(W)是因果可解释的 **当且仅当** T ⊆ W ∪ ND(W)（其中ND(W)是W的非后代）。
  - **最大T-可容许集（Theorem 2）**：对于多个查询W⋆，存在唯一的**最大T-可容许集** Max-T-Ad(W⋆) = ∩_{Wi∈W⋆} (Wi ∪ ND(Wi))，使用该特征集可在保持可解释性的前提下最大化预测表现。
  - **闭式解（Theorem 3）**：若模型是因果可解释的，则反事实查询可表示为 P(Ŷ_{w'} | x) = Σ_t P(Ŷ | w'∩T, t\W) P(t | x)，即可通过特征提取器和分类器直接计算。
  - **权衡定理（Theorem 4）**：使用更多特征（T增大）会减少可回答的反事实查询集合；要求更多查询（W⋆增大）会降低最大可容许特征集的大小。
- **算法流程**（文字说明）：
  1. 给定因果图（至少知道目标W的后代变量），确定W及其非后代特征。
  2. 计算最大T-可容许集（取所有查询对应的W∪ND(W)的交集）。
  3. 训练特征提取器P(T|X)和分类器P(Ŷ|T)，其中T⊆Max-T-Ad。
  4. 在推理时，对于反事实输入w'，使用公式 P(Ŷ_{w'}|x) = Σ_t P(Ŷ|w'∩T, t\W) P(t|x) 计算反事实预测。

## 3. 实验设计：数据集、基准、对比方法
- **合成数据集**：**BarMNIST**（基于MNIST修改，加入颜色和条形特征），特征包括“条”(B)、“数字”(D)、“颜色”(C)，因果关系为D→B，D与C相关。标签由所有特征和噪声生成。
  - 对比不同特征集：T={B,D,C}、{B,D}、{D,C}、{D}。
  - 评估指标：预测准确率、反事实估计误差（与真实SCM计算的真值对比）。
- **真实数据集**：**CelebA**（人脸属性数据集），预测标签为“吸引力”，反事实查询“如果微笑，吸引力会如何变化？”
  - 利用常识：微笑→颧骨、张嘴等后代变量。选择非后代特征（微笑、性别）作为可解释模型的特征集。
  - 对比方法：使用后代特征（如颧骨、张嘴）的基线模型。
  - 由于真实世界无法获得反事实真值，仅在定性上和人口统计差异上进行比较。
- **额外实验**（附录B.3）：
  - 另一个合成图结构：预测数字D，特征B→C→D，查询改变条(B)。对比使用后代特征C的基线 vs 只使用B的可解释模型。

## 4. 资源与算力
- 论文在附录B.2中说明：所有实验在**单个NVIDIA A100 GPU**上运行。
- 训练细节：BarMNIST使用ResNet18特征提取器+三层MLP分类器，批量大小1024，100 epoch，Adam lr=0.0003。CelebA使用ResNet34特征提取器+线性分类器，批量大小512，100 epoch，SGD lr=0.001。
- **未明确说明**：每个实验的GPU数量、总训练时长、超参数搜索细节等，资源消耗信息较有限。

## 5. 实验数量与充分性
- **实验数量**：
  - BarMNIST上：对比4种特征集，报告准确率和两个反事实查询（改变数字、改变颜色）的估计误差，并给出误差棒（5次独立运行）。
  - CelebA上：定性展示了2个实例+人口统计平均差异（附录B.3），对比了2个基线。
  - 额外实验：另一个合成图（1组对比）。
- **充分性评估**：
  - 优点：合成实验能验证理论（有真值），结果一致支持定理（非可解释模型估计误差大，可解释模型估计准确）。
  - 不足：真实数据集（CelebA）仅有定性展示，缺乏定量指标（无法计算真实反事实）。未进行消融实验（如不同特征选择对准确率的影响量化）。实验场景有限，仅两个合成+一个真实数据集。未与其他可解释性方法（如CBM、CEM）进行端到端对比。

## 6. 论文的主要结论与发现
- **核心发现1**：黑箱模型（Ω_BP）对任何W⊆V都不具有因果可解释性（命题1）。
- **核心发现2**：概念预测器（Ω_CP）通常也不具备因果可解释性，因为若使用后代变量作为预测特征，反事实答案不唯一。
- **核心发现3**：通过约束预测特征集为W∪ND(W)，可以保证因果可解释性；存在唯一的最大特征集Max-T-Ad，用于平衡可解释性和预测能力。
- **核心发现4**：因果可解释性与准确率之间存在本质权衡：特征越多，可解释查询越少；要求更多查询，最大特征集越小。
- **实证结论**：合成实验验证了理论的正确性；在CelebA上，可解释模型给出的反事实预测符合常识（微笑增加吸引力），而基线模型给出不一致、不可靠的结果。

## 7. 优点
- **理论贡献强大**：给出了完整的图形化判别准则（充要条件），并且推导出唯一的最大特征集和闭式解，使方法可直接应用于实践。
- **形式化定义清晰**：首次将“因果可解释性”概念与因果推断中的可识别性联系起来，为XAI提供了理论根基。
- **实验设计合理**：合成实验使用真实SCM生成数据，可以精确计算反事实真值，从而客观验证方法正确性；实验误差棒显示统计稳定性。
- **实用性强**：要求仅知道查询变量的后代（而非完整因果图），降低了因果知识获取的难度；闭式解便于工程实现。

## 8. 不足与局限
- **对因果图的依赖依然存在**：尽管只需后代信息，但获取这些关系仍可能困难或存在争议，尤其在高维度真实场景。
- **概念估计误差**：公式P(T|X)由训练所得特征提取器估计，若概念预测不准，反事实估计将出现偏差。论文未系统研究估计误差的影响。
- **真实场景验证受限**：CelebA实验无法获取反事实真值，只能依赖常识推理，说服力有限。缺乏用户研究或与人类判断一致性的定量评估。
- **实验覆盖不全面**：仅测试了二值特征和简单因果结构；未涉及多值/连续特征、更复杂的图；未与现有可解释性模型（如CBM、CEM、NBDT）进行直接性能比较。
- **未讨论负向社会影响**：虽然论文讨论了应用价值，但未提及模型被滥用（如错误解释导致决策误导）的风险或公平性问题。

（完）
