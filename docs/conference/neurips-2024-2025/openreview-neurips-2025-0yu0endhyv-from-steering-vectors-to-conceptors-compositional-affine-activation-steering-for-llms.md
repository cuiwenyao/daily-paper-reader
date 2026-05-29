---
title: "From Steering Vectors to Conceptors: Compositional Affine Activation Steering for LLMs"
title_zh: 从引导向量到概念器：LLM的复合仿射激活引导
authors: "Steven Abreu, Joris Postmus, Alexander Müller, Jeremias Lino Ferrao, Ilija Lichkovski, Kurt Felix Michalak, Guillaume Pourcel, Alice S. Dauphin"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=0Yu0eNdHyV"
tags: ["query:ns-xai"]
score: 7.0
evidence: 通过概念器实现LLM可解释的激活引导
tldr: 大语言模型的内部表示控制和理解是核心挑战。本文将概念器理论与激活引导结合，推导出最优仿射引导函数，提供可解释的软投影矩阵控制内部状态。布尔运算实现复合多目标引导，性能优于加法引导。为模型可解释性和可控性提供原理性框架。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1307, \"height\": 489}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 355, \"height\": 431}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 426}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 907, \"height\": 479}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1004, \"height\": 278}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 514, \"height\": 451}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0yu0endhyv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 258}]"
motivation: LLM内部表示难以精确解释和控制，缺乏可解释的引导机制。
method: 结合概念器理论推导最优仿射激活引导函数，通过软投影矩阵实现可解释状态控制。
result: 在上下文学习和对齐任务上优于加法引导，支持复合目标组合。
conclusion: 概念器框架为可解释大模型推理控制提供理论基础。
---

## Abstract
Controlling and understanding the internal representations of large language models (LLMs) remain central challenges. We combine conceptor theory with activation steering to develop a principled framework for provably optimal affine steering of LLM activations. Conceptors compress sets of activation vectors and act as soft projection matrices, enabling precise and interpretable control over internal states. Our framework derives optimal steering functions from first principles and consistently outperforms additive steering across in-context learning tasks and alignment-relevant behavior. We further demonstrate how Boolean operations over conceptors allow for compositional steering toward multiple objectives, yielding better performance than traditional vector combination methods. Together, these results establish conceptor-based steering as a powerful tool for both controlling LLM behavior and gaining insight into their internal mechanisms. We will release our code and data as part of a flexible open-source library for activation steering.

---

## 论文详细总结（自动生成）

# 从引导向量到概念器：LLM的复合仿射激活引导——论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）内部表示难以精确解释和控制，现有的控制方法（如RLHF、微调、提示工程）存在计算成本高、泛化差或结果不一致等问题。
- **研究动机**：激活引导（Activation Steering, AS）作为一种轻量级推理时干预方法，通过修改内部激活来控制模型行为，但已有方法（如加法引导向量）主要依赖经验操作，缺乏理论根基，且只能进行简单向量平移，无法捕捉激活的协方差结构。
- **整体含义**：本文旨在将概念器理论（Conceptor Theory）引入激活引导，推导出理论上最优的仿射引导函数，提供可解释的软投影矩阵，实现更精确、可组合的LLM行为控制，同时为模型可解释性提供新视角。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 利用概念器（conceptor）作为**软投影矩阵**，对LLM隐藏层激活进行线性/仿射变换，而非简单的向量加法。
- 概念器基于激活向量的二阶统计量（协方差矩阵）构建，能够压缩一组激活向量的“模式”，并保留其主方向与方差信息，几何上相当于一个高维椭球体。
- 通过**布尔运算**（AND、OR、NOT）组合多个概念器，实现复合多目标引导，无需重新训练。

### 关键技术细节
1. **线性引导函数（Conceptor）**：
   - 优化目标：最小化对已体现目标概念的表示的变化，同时将其他表示向目标概念引导，加入正则化项（孔径参数ε）。
   - 闭式解：`C = Σ_c (Σ_c + ε²I)⁻¹`，其中Σ_c为概念c的**二阶矩矩阵**。C是半正定矩阵，特征值在[0,1)之间。
   - 性质：对激活进行软投影，激活若已位于概念区域内则变化小，否则被拉向该区域。

2. **仿射引导函数**：
   - 形式：`f(x) = Cx + b`，其中b = μ_c - Cμ_c，μ_c为概念c的均值向量。
   - 等价于：`f(x) = C(x - μ_c) + μ_c`，即先中心化再投影再恢复均值。
   - 推导出最优解：`C = Σ_c (Σ_c + 2ε²I)⁻¹`（注意与线性概念器公式中的分母差异）。

3. **残差概念器（Residual Steering）**：
   - 实际应用时使用 `C + I` 替代 `C`，使所有成分增益至少为1，概念相关模式被适度放大（增益∈[1,2]），符合Transformer的残差更新归纳偏置，避免信息丢失。

4. **布尔运算**：
   - **OR**：通过合并协方差矩阵实现（`C₁ ∨ C₂`）。
   - **NOT**：`¬C = I - C`。
   - **AND**：由德摩根定律导出（`C₁ ∧ C₂ = ¬(¬C₁ ∨ ¬C₂)`）。
   - 这些运算允许将多个单一概念的概念器组合成复合引导函数，性能优于向量平均等传统方法。

## 3. 实验设计：数据集、场景、对比方法

### 实验场景
1. **函数引导（Function Steering）**：在GPT-J（6B）和GPT-NeoX（20B）上测试六种上下文学习任务：反义词、现在-过去时、英法翻译、单数-复数、国家-首都、首字母大写。
2. **复合函数引导**：使用GPT-4o生成三种复合任务（英法&反义词、英法&大写、单复数&大写），比较直接计算复合概念器 vs. 布尔组合单个概念器 vs. 加法向量均值组合。
3. **复杂行为引导**：在Qwen 2.5-1.5B Instruct和Mamba 2.8B（SSM架构）上测试“与其他AI协调”任务（来自Perez et al., 2022），包括多选题和开放式生成。

### 对比方法
- **加法引导向量**（Additive Steering）：基于均值向量或对比均值差（contrastive activation addition）。
- **均值中心化加法引导**（Mean-Centered Addition）。
- **LoRA适配器**：在相同位置上训练全秩LoRA（作为线性引导的等效表达力对照）。
- **标准概念器**（线性/仿射）、**对比概念器**（利用布尔运算结合正负例概念器）。

### 评估指标
- 函数任务：准确率（正确输出比例）。
- 复杂行为：改进的准确率（相对于无引导基线）以及LLM裁判（GPT-4.1-mini）评分的开放生成质量。

## 4. 资源与算力

论文中**未明确说明**使用的GPU型号、数量及总训练/推理时长。仅提及实验在GPT-J 6B、GPT-NeoX 20B、Mamba 2.8B、Qwen 1.5B上运行，LoRA训练使用了“至少10倍于概念器的计算量”。未提供具体硬件配置或预算。

## 5. 实验数量与充分性

- **数量**：涵盖3种主要实验设置（函数引导、复合引导、复杂行为引导），每种设置包含多个子任务（函数任务6个，复合任务3个，行为任务2个模型×2种评估方式）。每个函数任务重复5次取平均。
- **充分性**：
  - 在多个模型家族（Transformer、SSM）上验证，增强了泛化性。
  - 进行了超参数网格搜索（孔径ε、强度φ、层位置），并报告最佳结果。
  - 对复合引导，既比较了“直接计算复合概念器”的基线，也比较了布尔组合与向量平均，设计合理。
  - 但存在不足：① 复杂行为任务中，开放式生成的结果（图5b）显示概念器不如加法向量，作者归因于超参数搜索不充分（仅探索了50%的层），说明实验覆盖不完全；② 未在更大模型（如70B）或更多样化的安全任务上测试；③ 未提供统计显著性检验或误差线（仅提到将补全）。

## 6. 论文的主要结论与发现

1. **概念器引导在函数任务上全面优于加法引导**：在GPT-J和GPT-NeoX的所有六个任务、几乎所有层上，概念器准确率更高（例如反义词任务：概念器52% vs 加法20%）。
2. **仿射概念器相比线性概念器提升有限**：最大提升约5%（如国家-首都任务81.6%→85.3%），但均值中心化对加法引导的提升更显著。
3. **布尔组合优于向量平均**：在复合函数任务中，AND组合的概念器准确率超过直接计算的复合概念器，更远超向量平均组合。
4. **在复杂行为（协调AI）上，概念器在多选题评估中优于对比向量，但在开放式生成中逊色**，提示需要更精细的超参数调优。
5. **LoRA训练尽管计算量更大，但未超越概念器性能**，表明概念器在参数效率上具有优势。
6. **概念器提供内在可解释性**：通过捕捉激活的协方差结构，其软投影机制能够自适应地影响激活，无需额外的分类器或自适应模块。

## 7. 优点

- **理论严谨**：从优化目标出发推导出闭式解，建立概念器与激活引导间的严格联系，弥补了加法引导缺乏理论基础的缺陷。
- **方法新颖且实用**：将概念器理论（原用于RNN控制）引入LLM解释与控制领域，并扩展了残差应用和布尔组合操作，操作简单（只需计算协方差矩阵），无需额外训练。
- **实验设计全面**：覆盖多种模型架构和任务类型，特别是包括SSM（Mamba）和指令微调模型，验证方法的通用性。
- **可解释性贡献**：概念器作为软投影矩阵，能揭示哪些激活方向被保留或衰减，有助于理解LLM内部表示的组织方式。
- **开放科学**：承诺开源代码和库，提升可复现性。

## 8. 不足与局限

- **计算复杂度**：概念器需要计算D×D协方差矩阵并求逆（D为隐藏维度），对于大型模型（如Llama 70B）可能内存开销较大；正则化参数ε和强度φ需要更多超参数调优。
- **实验覆盖有限**：
  - 仅测试了少量模型（最大20B参数），未在70B/100B+规模上验证。
  - 复杂行为任务仅使用单一安全相关任务，且开放式生成结果不佳，表明方法在该设定下可能不稳健。
  - 未评估对模型其他能力（如语言质量、推理能力）的副作用。
- **偏差风险**：概念器可能放大训练数据中存在的偏见，作者承认需进行公平性审计但未实际执行。
- **缺乏与更多SOTA方法的对比**：未与近年其他理论引导方法（如LEACE、功能向量）直接比较，也未进行消融实验分析每个组件（如残差项）的贡献。
- **开放生成的局限性**：复杂行为引导的开放式评估仅使用单层调优（图5b），而概念器在更广泛层上的性能可能更好，但尚未充分探索。
- **可复现性细节不足**：未披露具体硬件和超参数搜索的完整范围（如ε的网格），LoRA训练的具体配置也未完全给出。

（完）
