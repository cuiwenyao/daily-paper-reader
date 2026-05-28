---
title: Neurosymbolic Diffusion Models
title_zh: 神经符号扩散模型
authors: "Emile van Krieken, Pasquale Minervini, Edoardo Ponti, Antonio Vergari"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=HfdzglsZQH"
tags: ["query:ns-xai"]
score: 9.0
evidence: 神经符号预测器，融合神经感知与符号推理
tldr: 标准神经符号预测器假设符号间条件独立，限制了交互建模与不确定性估计。本文提出神经符号扩散模型（NeSyDMs），利用离散扩散过程在每一步复用独立性假设，却整体捕获符号依赖关系，从而实现可扩展学习与不确定性量化。在视觉推理等任务上，NeSyDMs在分布外泛化与校准方面表现优异。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-hfdzglszqh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1300, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hfdzglszqh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1178, \"height\": 609, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 717, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 703, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 677, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1110, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 920, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1190, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1188, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1464, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hfdzglszqh/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 535, \"label\": \"Table\"}]"
motivation: 现有神经符号预测器因符号独立假设导致交互建模不足和过自信预测。
method: 提出NeSyDMs，在扩散过程的每一步复用独立性假设，整体建模符号依赖。
result: 在视觉推理任务上改善了分布外泛化和不确定性估计。
conclusion: NeSyDMs是一种新的神经符号方法，有效处理符号间依赖，提升预测可靠性。
---

## Abstract
Neurosymbolic (NeSy) predictors combine neural perception with symbolic reasoning to solve tasks like visual reasoning. However, standard NeSy predictors assume conditional independence between the symbols they extract, thus limiting their ability to model interactions and uncertainty --- often leading to overconfident predictions and poor out-of-distribution generalisation. To overcome the limitations of the independence assumption, we introduce _neurosymbolic diffusion models_ (NeSyDMs), a new class of NeSy predictors that use discrete diffusion to model dependencies between symbols. Our approach reuses the independence assumption from NeSy predictors at each step of the diffusion process, enabling scalable learning while capturing symbol dependencies and uncertainty quantification. Across both synthetic and real-world benchmarks — including high-dimensional visual path planning and rule-based autonomous driving — NeSyDMs achieve state-of-the-art accuracy among NeSy predictors and demonstrate strong calibration.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：神经符号预测器（NeSy predictors）通过神经感知提取高层符号（概念），再经符号程序推理得到输出。然而，绝大多数现有 NeSy 方法在概念之间假设**条件独立性**，即 \( p_\theta(c|x) = \prod_{i} p_\theta(c_i|x) \)。这一假设虽然使概率推理高效（加权模型计数），但也导致模型无法捕捉符号间的依赖关系和不确定性，容易产生**过自信预测**和**分布外泛化差**，并易受**推理捷径**（reasoning shortcuts）影响——模型能正确预测输出但学到错误的概念。
- **解决方向**：论文提出**神经符号扩散模型（NeSyDMs）**，通过**离散扩散过程**建模概念间的依赖，同时保留每一步扩散中的局部条件独立性，从而兼顾**可扩展学习**与**全局依赖捕获**，并显式量化不确定性。

## 2. 方法论

### 2.1 核心思想
- 采用**掩码扩散模型（Masked Diffusion Models, MDMs）** 作为基础，将其扩展到神经符号场景：
  - 定义连续时间正向过程 \( q(c_t|c_0) \)，逐步将概念向量 \( c_0 \) 的维度掩码为特殊占位符 \( m \)。
  - 学习逆向过程 \( p_\theta(c_s|c_t, x) \)，通过条件独立的去掩码模型 \( p_\theta(\tilde{c}_0|c_t,x) \) 和符号程序 \( \phi \) 逐渐恢复概念和输出。
  - 模型同时处理概念 \( c \) 和输出 \( y \) 的扩散，概念为隐变量，输出由程序 \( \phi \) 从概念计算得到。

### 2.2 关键技术细节

- **模型定义**：
  - 概念逆向过程：\( p_\theta(c_s|c_t,x) = \sum_{\tilde{c}_0} p_\theta(\tilde{c}_0|c_t,x) q(c_s|c_t,c_0=\tilde{c}_0) \)
  - 输出逆向过程：\( p_\theta(y_s|c_s,y_t,x) = \sum_{\tilde{c}_0} p_\theta(\tilde{c}_0|c_s,x) q(y_s|y_t,\phi_{y_t}(\tilde{c}_0)) \)
- **损失函数**：导出连续时间负对数似然下界（NELBO）：
  \[
  \mathcal{L}_{\text{NeSyDMs}} = \mathbb{E}_{t,c_0,c_t}\left[ \frac{\alpha'_t}{1-\alpha_t}\sum_{i\in M_{c_t}} \log p_\theta(\tilde{c}_{0,i}=c_{0,i}|c_t,x) \right] \\
  + \mathbb{E}_{t,c_0,c_t}\left[ \alpha'_t \sum_{i=1}^Y \log \sum_{\tilde{c}_0} p_\theta(\tilde{c}_0|c_t,x) \mathbf{1}[\phi(\tilde{c}_0)_i = y_{0,i}] \right] \\
  - H[q_\theta(c_0|y_0,x)]
  \]
  包括概念去噪损失 \( \mathcal{L}_c \)、输出去噪损失 \( \mathcal{L}_y \) 和变分熵 \( \mathcal{L}_{H[q]} \)。
- **变分后验**：使用受输出约束的概念去掩码模型 \( q_\theta(\tilde{c}_0|c_t,y_0,x) \propto p_\theta(\tilde{c}_0|c_t,x) r_\beta(\tilde{c}_0|y_0) \)，通过自归一化重要性采样近似。
- **梯度估计**：输出损失使用 **REINFORCE Leave-One-Out (RLOO)** 无偏梯度估计器；变分熵采用两步近似（条件1步熵或无条件1步熵）。实际训练中忽略从变分分布采样的间接梯度。
- **推理**：采用多数投票策略——从训练好的 MDM 中采样多个概念，分别运行程序，取最频繁输出。

### 2.3 算法流程（文字说明）
1. 对每个输入-输出对 \((x,y_0)\)，从变分分布 \( q_\theta(c_0|x,y_0) \) 采样概念 \( c_0 \)。
2. 采样时间 \( t \sim U(0,1) \)，根据正向过程 \( q(c_t|c_0) \) 获得部分掩码概念 \( c_t \)。
3. 从去掩码模型 \( p_\theta(\tilde{c}_0|x,c_t) \) 采样 \( S \) 个样本 \( \tilde{c}_0^{(j)} \)。
4. 分别计算梯度：概念损失梯度 \( g_c \)、输出损失梯度 \( g_y \)（RLOO估计）、变分熵梯度 \( g_H \)。
5. 加权求和：\( g = \gamma_c g_c + \gamma_y g_y + \gamma_H g_H \)，更新模型参数。

## 3. 实验设计

### 3.1 数据集与场景
| 任务 | 描述 | 基准来源 |
|------|------|----------|
| 多位数MNIST加法 | 输入两个 \( N \) 位数字的MNIST图像，输出数字和（\( N=4,15 \)） | 传统NeSy基准 |
| 视觉路径规划 | 预测网格细胞代价，用Dijkstra找最短路径（网格大小 \( 12\times12, 30\times30 \)） | 复杂组合推理 |
| RSBench（MNIST Half, MNIST Even-Odd, BDD-OIA） | 合成/真实场景的推理捷径检测：半MNIST、偶奇MNIST、自动驾驶行为决策 | [56] RSBench |

### 3.2 对比方法
- **MNIST加法**：Deep SoftLog, PLIA, Scallop, EXAL, A-NeSI
- **路径规划**：I-MLE, EXAL, A-NeSI, A-NeSI+RL
- **RSBench**：PNP⊥, SL⊥, BEARS (RS-aware ensemble)

### 3.3 实验设置
- 每个实验重复10个不同随机种子。
- 统计显著性使用单侧 Mann-Whitney U 检验（显著性水平0.05）。
- 模型架构与基线一致，使用相同数据集预处理和网络结构（LeNet, ResNet18变体, MLP等）。

## 4. 资源与算力
- **GPU**：NVIDIA GeForce GTX 1080 Ti 和 GTX 2080 Ti（每节点一张低端GPU）。
- **CPU**：12核，但非瓶颈。
- **训练时长**：每个实验1-17小时（取决于任务），总计约需600 GPU小时（包括调参和重复运行）。
- **框架**：PyTorch，优化器RAdam（MNIST加法用Adam）。

## 5. 实验数量与充分性
- **实验数量**：覆盖5个任务（MNIST加法×2，路径规划×2，RSBench×3），每个任务10次运行，总约50组主实验。
- **消融实验**：
  - 损失权重 \( \gamma_c, \gamma_H \) 的影响（MNIST Half上系统评估）。
  - 多数投票策略比较（程序-真值模式、边缘模式等）。
  - 条件熵 vs 无条件熵在RSBench上的对比。
- **公平性**：匹配基线实验设置（相同数据集、网络、评价指标）；重新计算基线指标修复代码错误。统计检验确认差异显著性；超参数在验证集上调优。
- **充分性**：实验覆盖可扩展性（RQ1）和RS-awareness（RQ2），综合性强。

## 6. 主要结论与发现
1. **可扩展性**：在视觉路径规划 \( 30\times30 \) 任务上，NeSyDMs 准确率达 **97.40%**，显著优于所有基线（包括I-MLE的93.7%），且方差更低。
2. **多位数加法**：表现与状态近似的A-NeSI相当（\( N=15: 77.29\% \) vs \( 77.1\% \)），未因表达性增加而牺牲性能。
3. **RS-awareness**：在RSBench上，NeSyDMs 实现了最佳概念校准（ECE）和概念准确率，尤其在条件熵版本下OOD性能显著提升；在BDD-OIA上，输出F1优于BEARS，校准大幅改善。
4. **局部独立性足以捕获全局依赖**：理论证明扩散模型每一步的条件独立性可以编码全局符号依赖，实验验证了模型能够有效表达不确定性。

## 7. 优点
- **理论贡献**：将MDM的NELBO扩展到非因式分解分布（Theorem C.1），并推导NeSyDMs的NELBO，保证优化有界。
- **方法创新**：首次将离散扩散模型与神经符号预测器结合，在保持局部独立性的同时实现全局依赖性建模，兼具可扩展性和不确定性量化。
- **实验全面**：覆盖从简单合成到高维真实场景，对比多种基线和消融，统计检验严格。
- **可复现**：公开代码，提供所有超参数和算法伪代码。
- **校准性能**：在推理捷径敏感任务上实现低ECE，提高模型可靠性。

## 8. 不足与局限
- **变分熵近似有偏**：条件/无条件1步熵是启发式近似，未完全最大化真后验熵，可能限制RS-awareness。
- **梯度估计依赖输出可分解性**：输出损失 \( \mathcal{L}_y \) 分解为各维度独立WMC，RLOO在概念全不匹配时无信号；当程序输出不可分解或概率很低时，梯度估计会失败。
- **超参数敏感**：损失权重 \( \gamma_H \) 和 \( \gamma_c \) 需要仔细调优（尤其在MNIST Half上），不同任务最佳值差异大。
- **推理效率**：多数投票需要多次采样，对高维概念成本高（虽然仍比精确推理可行）。
- **扩展方向**：未探索其他离散扩散模型（如均匀噪声）或混合连续-符号模型；当前方法仅针对掩码扩散。
- **社会影响**：虽旨在提高可靠性，但作为通用方法，可能被用于过分自信决策的虚假可信度（论文已讨论较少直接风险）。

（完）
