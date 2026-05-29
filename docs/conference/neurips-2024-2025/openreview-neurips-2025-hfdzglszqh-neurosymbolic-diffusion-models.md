---
title: Neurosymbolic Diffusion Models
title_zh: 神经符号扩散模型
authors: "Emile van Krieken, Pasquale Minervini, Edoardo Ponti, Antonio Vergari"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=HfdzglsZQH"
tags: ["query:ns-xai"]
score: 9.0
evidence: 神经符号扩散模型用于可解释推理
tldr: 现有神经符号预测器假设符号条件独立，限制了交互建模和不确定性量化。本文提出神经符号扩散模型（NeSyDMs），通过离散扩散过程建模符号间依赖关系，在保持可扩展性的同时实现符号依赖捕获和不确定性量化，提升了泛化能力。该方法为神经符号集成推理提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-hfdzglszqh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1300, \"height\": 645}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hfdzglszqh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1178, \"height\": 609}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 422}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 456}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 717, \"height\": 307}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 703, \"height\": 273}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 677}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 271}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 288}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 542}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1110, \"height\": 537}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 920, \"height\": 536}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1190, \"height\": 552}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1188, \"height\": 396}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1464, \"height\": 536}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 535}]"
motivation: 标准神经符号预测器假设符号条件独立，导致过自信和分布外泛化差，需建模符号依赖。
method: 提出NeSyDMs，将离散扩散过程融入神经符号框架，每个扩散步复用独立性假设以可扩展地学习符号依赖。
result: 实验表明NeSyDMs有效捕获符号交互和不确定性，提高预测校准度和分布外泛化。
conclusion: 离散扩散是增强神经符号模型表达力和鲁棒性的有效途径。
---

## Abstract
Neurosymbolic (NeSy) predictors combine neural perception with symbolic reasoning to solve tasks like visual reasoning. However, standard NeSy predictors assume conditional independence between the symbols they extract, thus limiting their ability to model interactions and uncertainty --- often leading to overconfident predictions and poor out-of-distribution generalisation. To overcome the limitations of the independence assumption, we introduce _neurosymbolic diffusion models_ (NeSyDMs), a new class of NeSy predictors that use discrete diffusion to model dependencies between symbols. Our approach reuses the independence assumption from NeSy predictors at each step of the diffusion process, enabling scalable learning while capturing symbol dependencies and uncertainty quantification. Across both synthetic and real-world benchmarks — including high-dimensional visual path planning and rule-based autonomous driving — NeSyDMs achieve state-of-the-art accuracy among NeSy predictors and demonstrate strong calibration.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化、深入、客观的中文总结。

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

标准神经符号（NeSy）预测器结合了神经感知与符号推理，但在处理概念（concepts）时普遍假设其在给定输入后**条件独立**。这种简化假设限制了模型对概念间交互和不确定性的建模能力，导致**过度自信的预测**和**分布外（OOD）泛化能力差**，尤其容易陷入“推理捷径”（Reasoning Shortcuts, RS）——模型正确预测输出但学到错误的概念，在推理捷径下无法同时表达关于不同概念的恰当不确定性。

为突破独立假设的局限，本文引入了**神经符号扩散模型（NeSyDMs）**，这是首个将离散扩散模型与符号程序结合以预测概念依赖关系的方法，旨在提升模型的表达力、鲁棒性和校准度。

## 2. 方法论

- **核心思想**：采用**掩码扩散模型（Masked Diffusion Models, MDMs）** 来建模概念间的依赖关系。在扩散过程的每一步，模型**局部地**仍然假设概念条件独立，从而继承经典NeSy的高效推理优点，但**全局上**通过迭代去噪过程捕获依赖关系。
- **模型架构**：
    1.  **概念提取网络（Concept Extractor）**：神经网络 `p_θ(c̃₀ | c_t, x)` 根据部分被掩码的概念（c_t）和输入（x）预测完全去噪的概念（c̃₀）。
    2.  **符号程序 φ**：将预测的概念映射到输出（例如，在视觉路径规划中使用Dijkstra算法计算最短路径y）。
    3.  **输出反向过程**：通过复用概念提取网络并结合程序，定义一个输出扩散过程。模型的变分后验 `q_θ(c₀|y₀,x)` 与扩散模型共享参数，通过约束导向的采样算法（如重新采样满足输出的样本）实现。
- **损失函数**：推导了一个**连续时间负证据下界（NELBO）** `L_{NeSyDM}`，由三部分组成：
    - **概念去噪损失（L_c）**：类似标准MDM损失，要求模型从部分掩码的概念中重建采样的概念。
    - **输出去噪损失（L_y）**：分解为Y个独立的加权模型计数（WMC），每个对应输出的一个维度，独立用RLOO梯度估计器训练。
    - **变分熵（L_{H[q]}）**：最大化变分后验的熵，鼓励模型为一致概念分配均匀概率，避免锁定单一推理捷径。
- **梯度估计与优化**：
    - L_c直接计算；L_y采用**REINFORCE Leave-One-Out (RLOO)** 梯度估计量，避免精确计算#P-hard的WMC，保证了可扩展性。
    - 变分熵采用近似（无条件或一步有条件的熵）。
    - 通过超参数（γ_c, γ_H, γ_y）加权各项损失，并忽略通过变分分布采样的间接梯度以简化优化。
- **推理**：采用**多数投票**策略，从训练好的MDM中采样多个概念，通过程序获得多个输出，选择最频繁的输出作为最终预测。

## 3. 实验设计

- **数据集/场景**：
    - **多位数MNIST加法**（N=4, N=15）：合成任务，测试模型在传统NeSy基准上的可扩展性。
    - **视觉路径规划**（Warcraft地图，网格大小12×12、30×30）：高维组合推理任务，需模型预测网格单元的成本（概念）进而规划最短路径。
    - **RSBench基准**：专门测试推理捷径意识的套件，包括：
        - **MNIST Half / MNIST Even-Odd**：故意构造符号级歧义的合成任务，包含分布外（OOD）测试集。
        - **BDD-OIA**：真实世界自动驾驶任务，从行车记录仪图像中提取概念（如交通灯颜色）并预测可采取动作。
- **基准方法**：
    - **可扩展性对比**：Deep SoftLog, PLIA, Scallop, EXAL, A-NeSI（及其变体A-NeSI+RL），I-MLE。
    - **RS-awareness对比**：标准概率NeSy（PNP_⊥⊥）、语义损失（SL_⊥⊥）、专门设计的RS感知方法BEARS。
- **评价指标**：输出准确率、概念准确率、概念校准误差（ECE），用于评估RS感知程度。

## 4. 资源与算力

论文明确报告了实验资源情况：
- **硬件**：NVIDIA GeForce GTX 1080 Ti 和 GTX 2080 Ti GPU（低端GPU），每项实验使用单个GPU节点；12个CPU核心。
- **训练时长**：每项实验耗时1至17小时不等（取决于任务复杂度）。
- **总算力估计**：完成重复运行和超参数调优，总计约需**600 GPU小时**。

## 5. 实验数量与充分性

- **数量**：进行了**大量实验**，包括：
    - 在3个主要场景（MNIST加法、路径规划、RSBench）上重复10个随机种子。
    - 超参数随机搜索（每项任务约30次采样）。
    - 消融实验：测试损失权重（γ_c, γ_H）、不同多数投票策略、梯度估计方法的影响。
- **充分性与公平性**：
    - **优点**：实验设计较全面，覆盖了可扩展性和RS感知两个维度；对比了多种当前最优的近似和精确NeSy方法；使用统计检验（Mann-Whitney U test）来判定显著性；在RSBench任务中特别关注OOD场景，以评估鲁棒性。
    - **局限性**：RSBench实验仅使用单一网络架构，未在多种架构下验证；变分熵采用了近似估计（无条件熵或一步有条件的熵），可能影响结果精度；未在更复杂的符号程序（如包含递归、循环等）上测试。

## 6. 主要结论与发现

1.  **可扩展性强**：在**30×30**视觉路径规划这一极高难度任务上，NeSyDMs以**97.40%** 的准确率显著超越所有基线（包括SOTA的I-MLE），验证了其在高维推理问题上的实用性和可扩展性。
2.  **RS感知能力突出**：在RSBench上，NeSyDMs（尤其是使用有条件熵的版本）在OOD场景下表现出**显著更强的概念校准**（ECE更低）和**更好的概念准确率**，优于传统独立假设模型，并超越了专门的RS感知方法BEARS。这说明它能有效避免陷入推理捷径。
3.  **性能不牺牲**：在传统NeSy任务（MNIST加法）上，NeSyDMs虽然表达力更强，但性能与现有最优方法（A-NeSI等）相当，未出现性能下降。
4.  **损失权重敏感**：消融研究表明，熵权重（γ_H）和概念去噪权重（γ_c）对校准性能有显著影响，需要仔细调优才能平衡准确率和校准度。

## 7. 优点

- **创新性**：首次将掩码扩散模型引入神经符号领域，巧妙地利用局部独立性假设实现全局依赖建模，解决了长期存在的问题。
- **理论贡献**：证明了非分解联合分布下MDM连续时间损失扩展（附录C），为未来更复杂的MDM架构提供了理论基础。
- **实用性**：采样为基础的梯度估计和推理策略使得模型能够扩展到高维度和复杂程序，同时保持RS意识，这是现有方法难以兼顾的。
- **鲁棒性与校准性**：在OOD场景下显著提升了概念校准性能，对于安全关键应用具有重要意义。

## 8. 不足与局限

- **计算成本较高**：训练和推理需要多次采样（RLOO、重要性重采样、多数投票），比较耗时，对计算资源要求较高。
- **变分熵近似不精确**：由于精确计算条件熵困难，使用了近似（无条件或一步熵），这可能不是最优的，影响了损失函数的理论保证，并在实际中导致性能对超参数敏感。
- **梯度方差问题**：在RLOO采样中，若大部分样本都不符合输出约束，梯度信号会非常弱，影响训练效率。
- **对程序的假设**：L_y的分解要求程序输出能按独立维度处理；若程序结构不允许分解（如非独立输出维度），则需依赖知识编译（可能指数级时间），限制了应用范围。
- **实验覆盖有限**：主要测试了加法和路径规划两种程序类型；在更复杂的程序结构（如循环、递归、条件分支）上的性能尚不清楚；未在多种前端架构下验证RS-aware能力。

（完）
