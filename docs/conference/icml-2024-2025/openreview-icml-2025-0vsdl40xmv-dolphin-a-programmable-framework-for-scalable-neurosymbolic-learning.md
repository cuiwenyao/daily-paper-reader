---
title: "DOLPHIN: A Programmable Framework for Scalable Neurosymbolic Learning"
title_zh: DOLPHIN：一个可扩展的神经符号学习可编程框架
authors: "Aaditya Naik, Jason Liu, Claire Wang, Amish Sethi, Saikat Dutta, Mayur Naik, Eric Wong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=0VSDl40xMv"
tags: ["query:ns-xai"]
score: 9.0
evidence: 可扩展的神经符号学习框架
tldr: 神经符号学习面临复杂程序和大量数据的扩展挑战。本文提出DOLPHIN框架，在Python中支持神经符号程序，将符号推理放在CPU、概率计算和梯度传播放在GPU。在13个跨文本、图像、视频的基准测试上，DOLPHIN在复杂任务上达到最先进精度，而现有框架未能收敛。这显著推动了神经符号协同的实际应用。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 810, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 741, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 765, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 882, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 898, \"height\": 1135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0vsdl40xmv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1497, \"height\": 898, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1764, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 739, \"height\": 675, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1254, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1143, \"height\": 567, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 866, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 682, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0vsdl40xmv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1107, \"height\": 325, \"label\": \"Table\"}]"
motivation: 现有神经符号学习框架难以扩展到复杂符号程序和大数据集。
method: DOLPHIN采用Python编程，CPU执行符号推理，GPU执行概率计算和梯度传播。
result: 在多个复杂基准上达到最先进精度，远超现有框架。
conclusion: DOLPHIN实现了高效可扩展的神经符号学习，适用于多模态数据。
---

## Abstract
Neurosymbolic learning enables the integration of symbolic reasoning with deep learning but faces significant challenges in scaling to complex symbolic programs, large datasets, or both. We introduce DOLPHIN, a framework that tackles these challenges by supporting neurosymbolic programs in Python, executing complex symbolic reasoning on the CPU while vectorizing probabilistic computations and gradient propagation on the GPU. Across 13 benchmarks spanning tasks over text, image, and video data, with symbolic reasoning features like recursion and blackbox functions, DOLPHIN converges to state-of-the-art accuracies on the more complex benchmarks while existing frameworks such as Scallop, ISED, and IndeCateR+ fail to converge within the time limit. On simpler benchmarks, DOLPHIN matches their performance, while achieving these results 1.71x to 62x faster than the baselines. Overall, DOLPHIN advances the scalability of neurosymbolic frameworks, achieving state-of-the-art efficiency and convergence on difficult benchmarks where existing frameworks struggle. The code is published at https://github.com/Dolphin-NeSy/Dolphin.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：深度学习在图像分类、语音识别等任务上取得了巨大成功，但在需要结构化推理、逻辑和规划的任务中仍然不可靠。神经符号学习（Neurosymbolic Learning）旨在融合符号推理与深度学习，以同时发挥两者优势。
- **现有挑战**：现有神经符号框架（如 Scallop、DeepProbLog、Logic Tensor Networks）面临严重的**可扩展性瓶颈**——当符号程序复杂度高、数据集规模大时，训练时间指数增长，甚至内存溢出（OOM）。具体表现为：
  - 纯GPU框架（如LTN）因符号数量爆炸导致GPU内存耗尽。
  - 基于CPU的框架（如Scallop）缺乏批量化计算，随着问题复杂度增加，训练时间急剧增加。
- **整体含义**：神经符号学习要实际落地，必须解决复杂程序和大数据下的高效训练问题。DOLPHIN 通过将符号推理（L）保留在CPU、概率计算（P）向量化在GPU上，实现灵活性与可扩展性的平衡。

## 2. 方法论

### 核心思想
DOLPHIN 将神经符号程序拆分为：
- **符号计算（L）**：在CPU上执行，支持任意Python对象和黑盒函数（如递归、eval）。
- **概率计算（P）**：在GPU上以张量形式批量化处理，保持端到端可微性。

### 关键技术细节
1. **抽象类型**：
   - `Symbol`：任意Python对象（如数字、坐标）。
   - `Tag`：概率张量（如logits）。
   - `Distribution`：符号到标签的映射，是程序的基本数据类型。
2. **核心操作原语**（共5个）：
   - `APPLY`：对多个分布应用用户定义函数，组合所有符号组合并计算标签（map-reduce模式）。
   - `FILTER`：根据条件筛选符号。
   - `APPLY_IF`：条件性APPLY。
   - `UNION`：合并两个分布。
   - `GET_PROBS`：提取最终概率用于损失计算。
3. **可插拔的半环证明（Provenances）**：
   - **DAMP**（Differentiable Add-Mult Probabilities）：假设输入独立，用乘积/和计算概率，高效但精度有限。
   - **DTKP-AM**（Differentiable Top-K Proofs with Add-Mult）：追踪每个符号最多k个证明，每个证明由输入符号索引表示，最终通过加-乘近似加权模型计数（WMC）。支持GPU向量化。
4. **梯度传播**：所有标签操作基于PyTorch张量，自动记录计算图，实现端到端可微。
5. **递归与循环**：通过递归调用原语（如`UNION`合并结果）实现，或直接在用户自定义函数内实现控制流。

## 3. 实验设计

### 数据集与基准任务（共5大类13个变体）
| 任务 | 变体 | 数据类型 |
|------|------|----------|
| MNIST SumN | N=5,10,15 | 图像（手写数字求和） |
| Hand-Written Formula (HWF) | 公式长度≤7,≤15,≤19 | 图像（含数字和运算符） |
| PathFinder | 图像尺寸32,128,256 | 图像（点和曲线连接路径） |
| CLUTRR | 推理链长度≤3,≤4 | 文本（亲属关系推理） |
| Mugen | 视频-文本对齐：1K/5K样本 | 视频+文本 |

### 对比方法
- **Scallop**（CPU最优的神经符号框架）
- **Logic Tensor Networks (LTN)**（GPU逻辑约束编译）
- **ISED**（基于采样的梯度近似）
- **IndeCateR+**（基于采样的框架）

### 实验设置
- 每个方法运行3次，报告平均最佳精度和训练时间。
- 软超时：10小时。
- 对于CLUTRR，使用A100 GPU（40GB）；其余使用RTX 2080 Ti（11GB）+ Intel Xeon Gold 6248 CPU + 768GB RAM。

## 4. 资源与算力

- **GPU型号与数量**：主要使用NVIDIA GeForce RTX 2080 Ti（11GB）4块；CLUTRR任务使用NVIDIA A100（40GB）单卡。
- **CPU**：两个20核Intel Xeon Gold 6248（2.50 GHz）。
- **内存**：768GB RAM。
- **训练时长**：
  - 简单任务（SumN-5）：DOLPHIN 约54秒；Scallop约924秒。
  - 复杂任务（HWF-19）：DOLPHIN 约4.5小时；Scallop超10小时。
  - 最大任务（Path-256）：DOLPHIN 约5.5小时；Scallop超10小时。
- 文中未明确报告总GPU小时数，但给出了每任务训练时间表。

## 5. 实验数量与充分性

- **实验组数**：共13个基准任务变体，覆盖图像、文本、视频三种模态，每个任务均与至少两种基线对比（Scallop + 部分任务额外对比LTN、ISED、IndeCateR+）。
- **消融实验**：
  - 对比DAMP与DTKP-AM两种证明的精度和训练时间（图9）。
  - 针对DTKP-AM，探究不同K值（1,3,5,7）对精度和运行时间的影响（附录D.3）。
- **充分性评价**：
  - 实验覆盖全面，包含简单到极端复杂的任务，验证了DOLPHIN在多种情况下稳定收敛。
  - 对比方法均为当时最先进的通用神经符号框架，公平性强。
  - 超时设置合理（10小时），避免了无限等待。
  - 多次运行取平均，降低随机影响。
  - 不过，未与DeepProbLog等老框架在某些任务上比较（但Scallop已被证明更优），且未包含大规模语言模型的神经符号应用（如视觉问答NS-CL等），但这属于应用领域限制，不影响方法评估。

## 6. 主要结论与发现

1. **可扩展性显著提升**：DOLPHIN在13个基准上均能收敛，而Scallop等基线在5个复杂任务上10小时内无法收敛。
2. **训练速度快**：简单任务加速1.71~62倍，平均13.95倍。
3. **精度达到或超越SOTA**：在复杂变体（HWF-19、Path-256、Mugen-5K）上，DOLPHIN的精度远高于基线（如HWF-19高出20%，Path-256高出33%）。在CLUTRR上稍低于Scallop（可能因Scallop的DTKP-WMC更精确）。
4. **证明选择的重要性**：
   - DAMP适用于概率独立且组合简单的情况（如SumN）。
   - DTKP-AM适用于需要跟踪多证明路径的复杂符号程序（如HWF）。
5. **灵活性与易用性**：DOLPHIN作为PyTorch库，用户可用标准Python编写符号程序，无需学习新语言。

## 7. 优点

- **创新性结合**：首次提出将符号推理(CPU)与概率计算(GPU)解耦，同时保持端到端可微分，兼顾速度与灵活性。
- **可插拔证明**：提供两种向量化证明（DAMP和DTKP-AM），并允许用户自定义扩展，像超参数一样调优。
- **完整的实验验证**：涵盖多模态、多复杂度任务，与多种SOTA框架公平对比，证据充分。
- **代码开源**：提供完整实现，利于复现和社区贡献。
- **支持黑盒函数**：允许在符号部分使用任意Python代码，如`eval()`、递归、正则等，极大增强了表达力。

## 8. 不足与局限

- **批处理编程要求**：用户需要以批处理方式编写程序，对不熟悉批处理编程的新手有一定门槛（论文承认）。
- **生成模型支持缺失**：当前主要适用于判别模型（分类器），未研究如何与因果语言模型等生成模型集成。
- **非确定性符号程序不支持**：无法处理例如随机性路径选择等非确定性推理。
- **WMC近似可能丢失信息**：DTKP-AM使用加-乘近似替代精确加权模型计数，可能导致概率估计上界偏差，但在实验中未见明显影响。
- **部分任务精度略低**：在CLUTRR上精度略低于Scallop，可能因Scallop的精确WMC提供更准确的梯度信号。
- **未与所有基线在所有任务上对比**：例如LTN无法编写HWF程序，ISED/IndeCateR+不支持递归任务，导致对比不完全。这属于任务兼容性问题，但可能影响绝对排名。
- **实验计算资源配置未详细说明A100显卡数量**，仅提到每个实验使用单个A100，但多卡并行训练效果未讨论。

（完）
