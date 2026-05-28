---
title: Shortcuts and Identifiability in Concept-based Models from a Neuro-Symbolic Lens
title_zh: 从神经符号视角看概念模型中的捷径与可识别性
authors: "Samuele Bortolotti, Emanuele Marconato, Paolo Morettin, Andrea Passerini, Stefano Teso"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rdp1dLxyMI"
tags: ["query:ns-xai"]
score: 8.0
evidence: 神经符号视角下概念模型的捷径与可识别性
tldr: 概念模型常因学习低质量概念而出现推理捷径，但识别条件尚不明确。本文从神经符号视角建立概念模型与推理捷径的联系，推导出在推理层固定时识别概念与推理的理论条件，为构建可解释概念模型提供了理论指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1330, \"height\": 197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1248, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1327, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 924, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1435, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 699, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1513, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1436, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1358, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1360, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdp1dlxymi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1432, \"height\": 528, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 681, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 681, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 761, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 682, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 699, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1279, \"height\": 848, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 420, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 962, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 971, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1528, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1498, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1528, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 816, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdp1dlxymi/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 958, \"height\": 280, \"label\": \"Table\"}]"
motivation: 概念模型容易学习低质量概念，导致推理捷径，影响可解释性。
method: 从神经符号视角建立概念模型与推理捷径的联系，推导可识别性条件。
result: 理论推导了在给定推理层下识别概念的必要条件。
conclusion: 该工作为设计可识别且鲁棒的概念模型提供了理论基础。
---

## Abstract
Concept-based Models are neural networks that learn a concept extractor to map inputs to high-level concepts and an inference layer to translate these into predictions. Ensuring these modules produce interpretable concepts and behave reliably in out-of-distribution is crucial, yet the conditions for achieving this remain unclear. We study this problem by establishing a novel connection between Concept-based Models and reasoning shortcuts (RSs), a common issue where models achieve high accuracy by learning low-quality concepts, even when the inference layer is fixed and provided upfront. Specifically, we extend RSs to the more complex setting of Concept-based Models and derive theoretical conditions for identifying both the concepts and the inference layer. Our empirical results highlight the impact of RSs and show that existing methods, even combined with multiple natural mitigation strategies, often fail to meet these conditions in practice.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

概念模型（Concept-based Models, CBMs）通过概念提取器将输入映射为高层概念，再通过推理层将概念转化为预测。这类模型的可解释性和分布外（OOD）鲁棒性高度依赖概念和推理层的质量。然而，即使推理层固定且先验已知，模型仍可能学习到低质量的“推理捷径”（Reasoning Shortcuts, RSs），即用语义错误的概念达到高精度。本文进一步将RSs推广到推理层也被学习的更复杂场景（联合推理捷径，JRSs），并探究在什么条件下CBMs能够识别出具有“预期语义”（intended semantics）的概念和推理层。研究动机是揭示JRSs的存在性、危害性，并为构建可识别且鲁棒的概念模型提供理论基础。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将CBMs视为概念提取器 \(f: \mathbb{R}^n \to \Delta_{\mathcal{C}}\) 和推理层 \(\omega: \Delta_{\mathcal{C}} \to \Delta_{\mathcal{Y}}\) 的组合，并引入从真实概念到学习概念的映射 \(\alpha(g) = \mathbb{E}_{x \sim p^*(X|g)}[f(x)]\) 以及从学习概念到标签的映射 \(\beta(c) = \omega(\mathbf{1}_{\{C=c\}})\)。在标准假设（外推性、确定性知识）下，最大似然训练下的CBMs若能达到最优似然，则满足 \(\beta \circ \alpha = \beta^*\)（真实推理层）。

- **预期语义定义（Definition 3.3）**：存在置换 \(\pi\) 和逐元素可逆变换 \(\psi\)，使得 \(\alpha = \psi \circ P_\pi \circ \text{id}\) 且 \(\beta = \beta^* \circ P_\pi^{-1} \circ \psi^{-1}\)，即学习到的概念与真实概念一一对应（可解缠），推理层反向补偿这些变换。

- **联合推理捷径（JRSs, Definition 3.4）**：达到最优似然但不满足预期语义的CBMs。

- **理论结果**：
  - **定理3.6（非正式）**：给出确定性JRSs数量的计数公式。
  - **推论3.7**：当推理层固定时，JRSs数量退化为传统RSs数量。
  - **定理3.9（可识别性）**：在假设3.8（极值性）下，若确定性JRSs数量为零，则所有达到最优似然的CBMs必然具有预期语义，即概念和推理层可识别。

- **假设3.8（极值性）**：推理层 \(\omega\) 在混合概念分布下的最大标签概率严格小于在单一概念下的最大值。该假设在许多常见架构（如概率逻辑、Deep Symbolic Learning、满足条件的CBNM）中成立。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - **MNIST-Add**：预测两个MNIST数字之和，不含JRSs，作为基准。
  - **MNIST-SumParity**：预测和的奇偶性，含有大量JRSs。
  - **Clevr**（简化版）：2-4个物体，3类标签，含JRSs。
  - **BDD-OIA**：真实自动驾驶数据集，21个二进制概念，4个动作标签。

- **对比方法**：
  - **DPL**（DeepProbLog）：给定先验知识，推理层固定。
  - **CBNM**（Concept Bottleneck Model）：无概念监督，推理层学习。
  - **DSL**（Deep Symbolic Learning）：同时学习概念和符号知识。
  - **SENN**（Self-explainable Neural Networks）：无监督CBMs，含重构惩罚。
  - **DPL\*** 和 **bears\***：变体，分别替换推理为概率逻辑或集成方法。

- **评估指标**：
  - 标签F1（F1(Y)）、概念F1（F1(C)）、概念崩塌度（Cls(C)）、推理层F1（F1(β)）。概念对齐采用匈牙利算法。

- **缓解策略**：
  - 监督策略：概念监督、知识蒸馏、多任务学习。
  - 无监督策略：重构惩罚、熵最大化、对比学习（InfoNCE）。

### 4. 资源与算力

论文在附录A中提到所有实验均使用Python 3.9、PyTorch 1.13，运行于一张A100 GPU上。具体每个实验的epoch数（约50-100）和超参数网格搜索细节有说明，但未给出总GPU小时数。因此，文中明确使用了单张A100 GPU，算力消耗适中。

### 5. 实验数量与充分性

- **主要实验**：在三个合成视觉任务（MNIST-Add、MNIST-SumParity、Clevr）和一个真实任务（BDD-OIA）上进行，覆盖无JRSs、有JRSs、有偏分布等场景。
- **消融实验**：详细分析了不同监督×无监督缓解策略组合对CBNM在MNIST-SumParity和Clevr上的影响（图3、图5、图6），展示概念监督比例从0%到100%的变化。
- **鲁棒性**：每个实验重复5个随机种子，报告均值和标准差。
- **充分性判断**：实验设计较为全面，既验证了理论预测（MNIST-Add无JRSs时模型表现良好），也揭示了在含JRSs的任务中所有方法均失败。消融覆盖了主流缓解方法，结果客观。不足在于真实任务BDD-OIA仅测试了DPL和CBNM，未测试DSL等（因规模限制），且Clevr做了简化处理。

### 6. 论文的主要结论与发现

1. **所有测试CBMs均受JRSs影响**：在MNIST-SumParity和Clevr上，即使标签F1很高（≥90%），概念F1和推理层F1均较低，概念崩塌普遍。
2. **JRSs严重损害OOD行为**：在有偏的MNIST-SumParity中，只有完全监督的CBNM才达到可接受的OOD性能，但推理层仍非预期。
3. **现有缓解策略效果有限**：概念监督能部分改善，但无监督策略（重构、熵、对比学习）单独或组合均不能保证预期语义，仅对比学习能减少概念崩塌。

### 7. 优点

- **理论创新**：首次将推理捷径概念推广到推理层可学习的CBMs，给出了JRSs的严格定义和计数公式，建立了可识别性条件。
- **假设合理**：极值性假设在主流架构中成立，理论结果具有广泛适用性。
- **实验全面**：覆盖多种模型（有/无先验知识、有/无监督）、多个数据集（合成+真实），并系统测试了多种缓解策略。
- **可重复性**：提供开源代码，超参数和实现细节公开。

### 8. 不足与局限

- **假设局限**：理论分析依赖外推性和确定性知识假设，排除了不确定标签/概念的情况，限制了适用范围。
- **实验覆盖**：仅涵盖视觉任务（MNIST、Clevr、BDD-OIA），未涉及自然语言或其他模态；真实任务BDD-OIA仅测试了部分方法。
- **缓解策略有限**：未探索更复杂的约束方法（如稀疏推理层、人机交互、因果去偏）。
- **概念监督成本**：即使有监督，推理层仍可能受混淆因素影响（如概念间的虚假相关），无法完全保证预期语义。
- **算力报告不够详细**：仅提到单张A100，但未给出总GPU小时数。

（完）
