---
title: On the Hardness of Probabilistic Neurosymbolic Learning
title_zh: 论概率神经符号学习的难度
authors: "Jaron Maene, Vincent Derkinderen, Luc De Raedt"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=vxPmrxKe0J"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号学习的理论分析与梯度估计器
tldr: 概率神经符号模型的梯度近似通常难以处理。本文证明在训练期间梯度近似变得可行，并提出了WeightME，一个基于模型采样的无偏梯度估计器。理论保证在温和假设下仅需对数级SAT求解器调用。实验表明该估计器对神经符号学习的必要性，为可解释推理提供理论基础。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-vxpmrxke0j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vxpmrxke0j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vxpmrxke0j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vxpmrxke0j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1578, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vxpmrxke0j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1574, \"height\": 641, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-vxpmrxke0j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1527, \"height\": 730, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vxpmrxke0j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1616, \"height\": 617, \"label\": \"Table\"}]"
motivation: 概率神经符号模型的梯度计算复杂度未知，限制了训练可扩展性。
method: 理论证明训练中梯度近似可处理，并提出WeightME无偏估计器。
result: WeightME以对数级SAT调用实现梯度近似，实验验证其必要性。
conclusion: 本研究为神经符号学习的可训练性提供了理论保证和实用估计器。
---

## Abstract
The limitations of purely neural learning have sparked an interest in probabilistic neurosymbolic models, which combine neural networks with probabilistic logical reasoning. As these neurosymbolic models are trained with gradient descent, we study the complexity of differentiating probabilistic reasoning. We prove that although approximating these gradients is intractable in general, it becomes tractable during training. Furthermore, we introduce *WeightME*, an unbiased gradient estimator based on model sampling. Under mild assumptions, WeightME approximates the gradient with probabilistic guarantees using a logarithmic number of calls to a SAT solver. Lastly, we evaluate the necessity of these guarantees on the gradient. Our experiments indicate that the existing biased approximations indeed struggle to optimize even when exact solving is still feasible.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：纯神经网络学习方法存在局限性，概率神经符号模型将神经网络与概率逻辑推理结合，在多个任务中取得先进效果，但概率推理的 #P-hard 性质导致其可扩展性差。论文旨在回答：在神经符号学习的训练过程中，**概率推理的梯度近似是否可行？如何设计高效的梯度估计器？**
- **核心问题**：研究**概率推理（加权模型计数，WMC）的梯度计算复杂度**，证明一般情况下的难处理性，但发现训练中梯度近似变得可行，并提出一种基于模型采样的无偏梯度估计器 WeightME。
- **整体含义**：为概率神经符号学习的可训练性提供理论保证和实用方法，揭示现有近似方法的缺陷，指导未来研究。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将概率推理的梯度计算归约为加权模型计数（WMC）的梯度。利用 **WMC 的分解公式**（定理3.1）：  
  \[
  \frac{\partial \text{WMC}(\phi)}{\partial w(x)} = \text{WMC}(\phi|x) - \text{WMC}(\phi|\neg x)
  \]
  梯度计算复杂度与 WMC 相同（#P-complete）。  
  进一步证明：即使概率意义上的近似（(ε,δ)-近似）也是 NP-hard（定理3.3）。

- **训练期间的可行性**：当神经网络输出接近二值（权重接近0或1）时，梯度近似变得多项式时间可解（定理4.1）。但该可解区域在大型问题上可能难以达到（定理4.3），需要一定比例的概念监督。

- **WeightME 估计器**：基于**加权模型采样**的无偏梯度估计，定义如下：  
  \[
  \frac{\partial \log \text{WMC}(\phi)}{\partial w(x)} = \mathbb{E}_M\left[\frac{\mathbf{1}(x\in M)}{w(x)} - \frac{\mathbf{1}(x\notin M)}{w(\neg x)}\right]
  \]
  其中 \(M\) 是从加权模型分布中采样的模型。  
  WeightME 是**无偏估计**，且在温和假设下（|P(x|φ)-w(x)|>λ）仅需**常数个加权模型样本**即可实现 (ε,δ)-近似（定理5.3）。  
  加权模型采样可通过 SAT oracle 实现，理论调用次数为**对数级**于变量数（基于哈希方法）。

- **算法流程**：
  1. 训练迭代中，获得神经网络输出的权重 \(w\)。
  2. 使用加权模型采样器（如 CMSGen）从满足约束的模型中采样。
  3. 用 WeightME 公式计算梯度，更新网络参数。

## 3. 实验设计：数据集、基准与对比方法

- **数据集与基准**：
  - **模型计数竞赛（MCC）**：取自2021、2022、2023三届竞赛的概率型可被精确求解的实例。
  - **ROAD-R 数据集**：自动驾驶目标检测的逻辑约束公式。
  - 所有基准均为 CNF 公式，权重初始化服从均值0.5的高斯分布。

- **对比方法**（分类详见表1）：
  - **无偏方法**：解释采样（SFE）、IndeCateR、WeightME（本文）。
  - **有偏推断**：乘积 t-norm、Gödel t-norm、MPE、k-最优、均匀模型采样等。
  - **有偏梯度估计**：Straight-Through Estimator、Gumbel-Softmax、I-MLE。
  - **混合方法**：语义增强、Collapsed sampling 等。

## 4. 资源与算力

- **算力信息**：文中仅提到使用 **Intel Xeon E5-2690 CPU** 进行所有实验，未说明 GPU 型号、数量或训练时长。仅提及每个梯度计算的超时限制为5分钟。
- **资源说明**：本文侧重算法复杂度分析，实验主要是评估梯度近似质量与运行时间，未涉及大规模深度学习训练资源，因此未详细报告 GPU 使用情况。

## 5. 实验数量与充分性

- **实验数量**：
  - 梯度质量评估（表2）：在 **MCC 2021/2022/2023 共 274 个实例 + ROAD-R 100 个实例**上，对每种方法计算余弦相似度（均值±标准差）。
  - 运行时间累积图（图3）：在 MCC 全部实例上，比较多种方法的累计求解时间。
  - 优化实验（图4）：选取 **33 个简单 MCC 实例**，让多项式方法优化负对数似然，最高迭代 10000 步，比较最优损失。
  - 附加实验（附录E）：引入 **90% 概念监督**情况下的优化对比。

- **实验充分性**：
  - **比较全面**：涵盖了多种现有近似方法，包括无偏/有偏、多项式/NP-hard、经典/现代方法。
  - **设计公平**：所有近似方法使用相同超时限制，精确梯度由 d4 编译器计算（无超时）。
  - **存在局限**：优化实验仅在简单子集上进行（<1000变量），未在更大规模基准上验证；未包含端到端神经符号学习任务（如 MNIST-addition）中的训练效果。

## 6. 论文的主要结论与发现

- **理论结论**：
  1. 一般情形下，近似 WMC 梯度是 NP-hard。
  2. 训练中当网络收敛到二值输出时，梯度近似变为多项式时间可行。
  3. 概念监督不足以完全缓解近似需求（需要接近全部变量监督）。
  4. WeightME 是首个具有概率保证的无偏梯度估计器，仅需对数级 SAT 调用。

- **实验结论**：
  1. WeightME 在梯度质量（余弦相似度）上优于所有多项式方法，且可扩展至 NP-hard 方法可解的基准。
  2. 多项式近似方法（如 t-norm、Gumbel-Softmax）虽然计算快，但在优化任务中无法稳定收敛。
  3. NP-hard 方法（如 MPE、k-最优）缩放性差，超时严重。
  4. 即使提供 90% 概念监督，多项式方法仍无法在所有实例上优化成功，验证了理论定理。

## 7. 优点

- **理论贡献**：首次系统分析概率神经符号学习梯度近似的计算复杂度，填补理论空白。
- **算法新颖**：提出 WeightME，利用加权模型采样实现无偏、有概率保证的梯度估计，且调用 SAT 求解器次数对数级。
- **实验设计**：使用标准模型计数竞赛基准，对比方法覆盖面广，结果可靠。
- **洞察深刻**：指出现有偏近似方法在可精确求解的问题上仍会失败，强调原则性方法的必要性。

## 8. 不足与局限

- **实验覆盖**：优化实验仅在简单子集上进行，未在更大规模或真实神经符号任务（如视觉推理）中验证 WeightME 的实际训练效果。
- **局限性**：
  - 仅考虑命题逻辑，未涵盖一阶逻辑（虽然后者通常会转化为命题逻辑）。
  - 未考虑 DNF 公式，而 DNF 存在多项式时间 (ε,δ)-近似（已知文献）。
  - WeightME 的实现依赖加权模型采样器（如 CMSGen），其本身是近似算法，可能引入偏差，且理论上仍需要 SAT oracle，门限较高。
- **偏差风险**：多项式近似方法的结果可能受超参数选择影响（如 Gumbel Softmax 的温度 τ），文中仅固定部分参数，未充分调优。
- **应用限制**：实际神经符号学习中，需要频繁计算梯度，而每次梯度计算都需要求解多次加权模型采样，效率仍是瓶颈。

（完）
