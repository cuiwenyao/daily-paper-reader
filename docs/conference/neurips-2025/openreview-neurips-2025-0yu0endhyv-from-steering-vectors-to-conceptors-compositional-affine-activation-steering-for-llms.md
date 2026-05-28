---
title: "From Steering Vectors to Conceptors: Compositional Affine Activation Steering for LLMs"
title_zh: 从操纵向量到概念器：LLM的组合仿射激活操控
authors: "Steven Abreu, Joris Postmus, Alexander Müller, Jeremias Lino Ferrao, Ilija Lichkovski, Kurt Felix Michalak, Guillaume Pourcel, Alice S. Dauphin"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=0Yu0eNdHyV"
tags: ["query:ns-xai"]
score: 8.0
evidence: 基于概念器的激活操控实现可解释控制
tldr: 该论文将概念器理论与激活操控结合，提出可证明最优的仿射激活操控框架，用于控制和理解LLM内部表示。概念器作为软投影矩阵，可精确操控激活状态。布尔运算允许组合式多目标操控，在多种任务上优于加法操控。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1307, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 355, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 907, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1004, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 514, \"height\": 451, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0yu0endhyv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 258, \"label\": \"Table\"}]"
motivation: LLM内部表示的控制和理解仍然具有挑战。
method: 结合概念器理论推导最优仿射操控函数，并通过布尔运算实现组合操控。
result: 在上下文学习和对齐行为任务上，该方法一致优于加法操控，且支持组合目标。
conclusion: 概念器提供了一种可解释且可组合的LLM激活操控方法。
---

## Abstract
Controlling and understanding the internal representations of large language models (LLMs) remain central challenges. We combine conceptor theory with activation steering to develop a principled framework for provably optimal affine steering of LLM activations. Conceptors compress sets of activation vectors and act as soft projection matrices, enabling precise and interpretable control over internal states. Our framework derives optimal steering functions from first principles and consistently outperforms additive steering across in-context learning tasks and alignment-relevant behavior. We further demonstrate how Boolean operations over conceptors allow for compositional steering toward multiple objectives, yielding better performance than traditional vector combination methods. Together, these results establish conceptor-based steering as a powerful tool for both controlling LLM behavior and gaining insight into their internal mechanisms. We will release our code and data as part of a flexible open-source library for activation steering.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的内部表示难以理解和控制。现有方法（如RLHF、微调、提示工程）存在计算成本高、泛化差或不稳定等问题。激活操控（Activation Steering, AS）作为一种轻量替代方案，通过在推理时修改中间激活来引导模型行为，但早期加法操控（additive steering）缺乏理论支撑且表达能力有限。
- **研究动机**：需要一种更通用、有理论保证的激活操控框架，能够捕捉激活向量的协方差结构，实现更精确和可解释的控制，并支持多目标组合。
- **整体含义**：将概念器理论（conceptor theory）引入LLM激活操控，推导出最优线性/仿射操控函数，并通过布尔运算实现组合式操控，在多个任务上超越传统加法方法，同时保持可解释性和计算效率。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用概念器（conceptor）作为软投影矩阵，对LLM的隐藏层激活进行线性变换（而非单纯平移），从而更精细地调整表示空间。概念器通过激活的二阶矩（协方差结构）学习，能够自适应地保留或抑制不同方向的分量。
- **关键技术细节**：
  - **线性操控函数**：$f_c(H(s)) = CH(s)$，其中 $C$ 是概念器矩阵，通过优化目标 $\min_C \mathbb{E}[\|H_c - CH_c\|^2] + \varepsilon^2\|C\|_F^2$ 得到闭式解 $C = \tilde{\Sigma}_c (\tilde{\Sigma}_c + \varepsilon^2 I)^{-1}$，其中 $\tilde{\Sigma}_c$ 是概念条件二阶矩。$C$ 是半正定矩阵，特征值在 $[0,1)$ 之间，称为“软投影”。
  - **仿射操控函数**：进一步加入平移项 $b$，得到 $f_c(x) = Cx + b$，其中 $b = \mu_c - C\mu_c$，等价于 $f_c(x) = C(x-\mu_c) + \mu_c$。优化目标类似，但使用协方差矩阵 $\Sigma_c$。
  - **残差操控**：将概念器以残差形式应用 $f_c(x) = (C+I)x$，使所有方向增益至少为1，避免信息丢失，同时符合Transformer的残差更新偏置。
  - **布尔组合**：利用概念器的布尔运算（OR、NOT、AND）组合多个概念器，例如 $C_1 \lor C_2$ 通过相加协方差矩阵实现，$¬C = I-C$。这些操作可以自然地合成复合操控目标，优于简单的向量平均。
- **与加法操控的几何差异**：加法操控对所有激活施加固定平移；概念器则在概念相关方向上拉伸/压缩，在无关方向上保持，实现自适应非线性效果（见图1）。

## 3. 实验设计：数据集、基准、对比方法

- **数据集/场景**：
  - **函数向量任务**（Todd et al., 2024）：6种上下文学习任务——antonyms, present-past, English-French, singular-plural, country-capital, capitalize。数据集由示例对组成，用于评估操纵后模型能否正确完成函数映射。
  - **复合函数任务**（自建，使用GPT-4o生成）：3种组合函数——English-French & antonyms, English-French & capitalize, singular-plural & capitalize。
  - **复杂行为任务**（Perez et al., 2022的“Coordinate with other AIs”）：测试模型是否同意与另一AI合作（可能偏离人类利益），用于评估对齐相关行为。
- **Benchmark与对比方法**：
  - **基线**：加法操控（contrastive activation addition）及其均值中心化变体；对比向量（constrastive vector）。
  - **概念器变体**：线性概念器、仿射概念器、对比概念器（利用NOT操作）。
  - **额外对比**：全秩LoRA适配器（同等表达力但计算成本高10倍以上）。
- **模型**：
  - GPT-J (6B), GPT-NeoX (20B) （函数任务）
  - Qwen 2.5-1.5B Instruct, Mamba 2.8B （复杂行为任务）

## 4. 资源与算力

- 论文正文和摘要中未明确列出具体的GPU型号、数量或训练时长。作者在Checklist中声称“提供了计算资源信息”（包括硬件规格、内存、执行时间），但主要文本中没有出现这些数据。推测这些细节在附录中，但根据提供的文本片段，附录部分未完整包含该信息。
- **结论**：资源与算力信息仅在“论文核对清单”中提及，实际正文未公开具体数值，无法准确总结。建议查阅完整论文的附录部分获取详实数据。

## 5. 实验数量与充分性

- **实验组数**：
  - 函数任务：6个任务 × 2个模型 × 5次随机种子重复 = 60组核心结果，另加超参数扫参（层数和强度φ）。
  - 复合函数任务：3个复合函数，比较直接概念器、AND组合概念器、直接加法向量、平均加法向量。
  - 复杂行为任务：2个模型，分别进行多选题和开放生成评估，各比较3种方法（标准概念器、对比概念器、对比向量）。
  - 消融实验：仿射 vs. 线性概念器对比；均值中心化加法 vs. 普通加法对比；LoRA对比。
- **充分性评估**：
  - **优点**：实验覆盖多种模型架构（Transformer和SSM）、多种任务类型（语言函数、复合逻辑、对齐行为），且进行了多次重复，结果有统计意义。
  - **不足**：
    - 未在更大模型（如70B）上验证，结论推广性有限。
    - 复杂行为任务中开放生成结果不佳，作者承认超参数搜索粗糙（仅扫描<50%层），因此该场景下的对比不够充分。
    - 未进行长文本/多轮对话或多语言测试，任务多样性有待扩展。
    - 未报告多次重复的标准差或置信区间（仅在Checklist中提及“会包含误差棒”）。
  - **整体公平性**：对比方法均采用各自最优超参数，代码将开源，实验可复现。但没有进行多组随机种子下的统计显著性检验。

## 6. 论文的主要结论与发现

1. **概念器操控在所有函数任务上一致优于加法操控**，在6个任务中准确率提升显著（例如antonyms从20.54%→52.14%，country-capital从32.04%→81.62%）。
2. **布尔组合（AND）比向量平均更有效地合成复合函数**，在所有复合任务上均优于直接组合的加法向量。
3. **仿射概念器（含平移）在部分任务上略有提升**（如country-capital从81.62%→85.32%），但改进幅度有限。
4. **在复杂行为控制中，概念器在多选题上优于对比向量**，但开放生成上表现不佳，表明仍存在挑战。
5. **残差概念器（C+I）符合Transformer偏置，可保留信息并放大相关信号**，但实验未直接与其他概念器变体对比。
6. **概念器比LoRA更高效（无需梯度更新），且性能相当或更好**。

## 7. 优点：方法或实验设计上的亮点

- **理论严谨性**：从第一原理推导出最优线性/仿射操控函数的闭式解，具有凸优化保证，非启发式。
- **可解释性**：概念器是半正定矩阵，特征值反映方向重要性，支持可视化（高维椭球体），易于分析模型内部。
- **组合性**：布尔运算提供严谨的逻辑组合机制，优于简单的向量加法，且可理解。
- **自适应性**：概念器对已在目标区域内的激活改变小，对外部激活改变大，无需额外分类器。
- **高效性**：相比LoRA，概念器计算仅涉及矩阵乘法，无需反向传播，适合推理时快速干预。
- **跨架构验证**：在Transformer（GPT-J, Qwen）和状态空间模型（Mamba）上均有效，表明方法具有一定通用性。

## 8. 不足与局限

- **计算开销**：概念器需要存储和计算D²参数（D为隐藏维度），比加法操控的D参数更重，且需要计算协方差矩阵并进行矩阵求逆（虽然可以离线完成）。
- **数据需求**：需要足够多的正例样本来估计二阶矩，在小样本场景下可能不稳定。
- **超参数敏感**：孔径参数ε和强度φ需要细致调优，且不同层的最佳值不同。
- **实验覆盖有限**：
  - 模型规模最大为20B，未测试更大LLM。
  - 仅使用单轮任务，未涉及多轮对话或长序列生成。
  - 未验证多语言或多概念场景，布尔组合仅在三种复合函数上测试。
  - 复杂行为的开放生成结果不理想，说明方法在开放域控制上仍有瓶颈。
- **公平性与安全风险**：作者指出概念器可能放大训练数据中的偏见，也可能被用于恶意操控输出，需要额外审计和对策。
- **消融不足**：未系统分析残差概念器与其他变体的优劣；未与更先进的操控方法（如适应式操控、熵操控）对比。

（完）
