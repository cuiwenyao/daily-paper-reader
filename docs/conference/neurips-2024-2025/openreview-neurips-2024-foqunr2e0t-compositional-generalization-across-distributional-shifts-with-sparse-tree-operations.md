---
title: Compositional Generalization Across Distributional Shifts with Sparse Tree Operations
title_zh: 基于稀疏树操作的跨分布偏移的组合泛化
authors: "Paul Soulos, Henry Conklin, Mattia Opper, Paul Smolensky, Jianfeng Gao, Roland Fernandez"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=fOQunr2E0T"
tags: ["query:ns-xai"]
score: 9.0
evidence: 统一神经符号系统用于组合泛化
tldr: 混合神经符号方法受限于符号系统的可扩展性。本文提出统一神经符号系统，网络变换同时可解释为布尔运算，无需显式符号计算即可实现类人组合泛化，在分布偏移下保持鲁棒性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 588, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1421, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 661, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1379, \"height\": 771, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1464, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1459, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-foqunr2e0t/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1440, \"height\": 710, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 557, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1219, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1385, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 354, \"height\": 124, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 931, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1217, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-foqunr2e0t/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1341, \"height\": 322, \"label\": \"Table\"}]"
motivation: 现有混合神经符号方法面临可扩展性和灵活性瓶颈。
method: 设计统一神经符号网络，使变换同时具有布尔运算解释。
result: 在组合泛化基准上优于现有混合方法，且对分布偏移稳健。
conclusion: 统一神经符号系统能有效结合神经的可学习性与符号的泛化性。
---

## Abstract
Neural networks continue to struggle with compositional generalization, and this issue is exacerbated by a lack of massive pre-training. One successful approach for developing neural systems which exhibit human-like compositional generalization is $\textit{hybrid}$ neurosymbolic techniques. However, these techniques run into the core issues that plague symbolic approaches to AI: scalability and flexibility. The reason for this failure is that at their core, hybrid neurosymbolic models perform symbolic computation and relegate the scalable and flexible neural computation to parameterizing a symbolic system. We investigate a $\textit{unified}$ neurosymbolic system where transformations in the network can be interpreted simultaneously as both symbolic and neural computation. We extend a unified neurosymbolic architecture called the Differentiable Tree Machine in two central ways. First, we significantly increase the model’s efficiency through the use of sparse vector representations of symbolic structures. Second, we enable its application beyond the restricted set of tree2tree problems to the more general class of seq2seq problems. The improved model retains its prior generalization capabilities and, since there is a fully neural path through the network, avoids the pitfalls of other neurosymbolic techniques that elevate symbolic computation over neural computation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：神经网络难以实现组合泛化（compositional generalization），尤其在缺乏大规模预训练时表现更差。人类可以将语言分解为已知部分并理解新结构，而深度学习模型在面对新单词、新上下文、新递归深度时容易失败。
- **现有方法局限**：
  - 纯神经网络（Transformer/LSTM）在样本效率和鲁棒泛化上不足。
  - 混合神经符号方法（hybrid neurosymbolic）将符号计算作为核心，神经模块仅用于参数化，导致可扩展性差和灵活性低（brittle）。
- **本文目标**：构建一个**统一神经符号系统**（unified neurosymbolic），使网络中的变换同时具有符号计算和神经计算解释，避免混合方法的弊端，同时提升效率和泛化能力。

## 2. 方法论：核心思想、关键技术与流程
### 2.1 核心思想
- **Sparse Coordinate Trees (SCT)**：一种稀疏向量空间中的二叉树表示方法。将树结构编码为（索引、值）元组，索引表示树中的位置（基于Gorn地址，二进制编码左右分支），值向量表示节点内容。仅存储非零节点，内存使用与填充节点数成线性，大幅降低传统TPR的指数级内存开销。
- **可微树操作**：定义三个基础操作：`left`（取左子树）、`right`（取右子树）、`cons`（合并左、右子树为新树，可插入新根节点值）。这些操作通过位偏移（bit-shifting）和索引直接实现，无需预计算大型线性变换，效率极高。
- **加权混合**：每个时间步，模型输出三个操作的加权平均，实现可微的程序选择。结果经过剪枝（pruning）保持稀疏。

### 2.2 Sparse Differentiable Tree Machine (sDTM)
- 架构包含三个组件：**Agent**（Transformer编码器）、**Interpreter**（执行树操作）、**Memory**（存储中间树）。
- Agent对内存中的每棵树进行**多头注意力池化（PMA）**，结合位置编码（将二进制索引转换为−1和+1表示），生成固定维度的表示输入Transformer，然后输出操作权重、树参数和新根节点值。
- **关键改进**：
  - 用SCT代替TPR，内存和参数大幅减少（参数从72M降至1M）。
  - 用PMA代替线性变换池化，提升对树结构信息的利用。
  - 引入**树剪枝**：只保留top‑k节点（按值大小），进一步控制稀疏性。
  - 添加**词汇正则化**：对词嵌入加高斯噪声，增强词汇泛化。
- **处理序列输入/输出**：
  - seq2tree：输入每个token作为单节点树，通过`cons`操作自底向上合并。
  - seq2seq：输出序列转换为**左对齐均匀深度树（LAUD）**，所有非叶节点用特殊标记`<NT>`填充。

### 2.3 公式与流程
- 一步操作：  
  \( O(\vec{w}, \vec{T}, s) = w_L \cdot \text{left}(T_L) + w_R \cdot \text{right}(T_R) + w_C \cdot (\text{cons}(T_{CL}, T_{CR}) + s \otimes r_1) \)  
  其中 \(\vec{w}\) 是操作权重，\(\vec{T}\) 是选中的树参数，\(s\) 是新根节点值。
- 整个程序由Agent迭代生成执行步骤，每步写回Memory，最后输出Memory最后一槽。

## 3. 实验设计
### 3.1 数据集与场景
- **Active↔Logical**：树到树任务，主动语态与逻辑形式互译。测试IID、零样本词汇、结构泛化。
- **FOR2LAM**：树到树程序翻译（命令式→函数式）。测试IID和零样本词汇（变量x→z）。
- **GeoQuery**：自然语言到SQL（seq2tree）。测试IID、长度、模板、TMCD分布偏移。
- **SCAN**：合成seq2seq任务。测试IID、1-shot词汇、0-shot词汇、长度、模板、MCD（最大复合散度）。

### 3.2 基准方法
- **标准Transformer**（Vaswani et al.）
- **相对通用Transformer (RU-Transformer)**（Csordás et al.）
- **NQG**（Shaw et al.）：混合神经符号模型，诱导准同步上下文无关文法。
- 原始**DTM**（Soulos et al.）：仅用于Active↔Logical和SCAN（对比效率）。

### 3.3 评估指标
- 每个数据集按最佳精确匹配准确率报告（5个随机种子取最佳）。

## 4. 资源与算力
- 文中提到：所有sDTM实验可在**NVIDIA V100 16GB GPU**上运行；部分种子使用**80GB H100 GPU**（非必须）。
- 未明确报告总训练时长或具体GPU数量，但提及单个NQG运行需要42小时+，sDTM相对更快（相对速度提升约2.5~13倍）。
- 附录指出：在内部集群上运行，初步实验较多但不计入最终结果。

## 5. 实验数量与充分性
- **实验组数**：在4个数据集上共测试了多种分布偏移（共10余种测试场景），每个场景5个种子。
- **消融实验**：包含对剪枝（k=1024 vs 无）、池化方式（PMA vs 线性变换）、词汇正则化（有/无）、输出树结构（解析树 vs LAUD）的对比。
- **充分性**：实验覆盖了广泛的泛化挑战（IID、词汇、结构/长度、模板、MCD），对比了纯神经、混合神经符号和统一神经符号三类方法。但GeoQuery数据集较小（训练~500样本），所有方法精度都不高，可能影响结论的鲁棒性。此外，报告最佳种子而非平均，方差较大（见附录表格），可能高估实际性能。

## 6. 主要结论与发现
- **sDTM在多种分布偏移下表现最均衡**：在Active↔Logical和FOR2LAM上完美或大幅领先；在SCAN上除MCD外表现优异；但在GeoQuery上弱于Transformer。
- **零样本词汇泛化**：sDTM是唯一能在SCAN和FOR2LAM上实现高准确率的模型（得益于内容-结构分离）。
- **效率和可扩展性**：sDTM参数减少约70倍，内存减少5倍以上，速度提升2.5~13倍，可处理深度更大的树（FOR2LAM），原始DTM无法处理。
- **统一神经符号方法优于混合方法**：相比NQG，sDTM更灵活（能处理更大词汇和更深结构），且避免了符号核心的脆弱性。
- **局限性**：sDTM在MCD和模板偏移下表现不佳，在极小数据集GeoQuery上未超越Transformer，且训练不稳定（高方差）。

## 7. 优点
1. **创新性**：提出SCT表示和位偏移操作，压缩树表示同时保留可微性，理论优雅且实用。
2. **全面实验**：评估多种分布偏移，揭示模型在不同泛化维度上的强弱，而非单一指标。
3. **效率提升**：从参数、内存、速度三方面大幅改进，使统一神经符号方法可拓展到seq2seq任务。
4. **可解释性**：操作具有明确符号语义（left/right/cons），便于分析模型行为。
5. **零样本词汇泛化能力**：这是其他模型几乎做不到的，展示了结构-内容分解的价值。

## 8. 不足与局限
1. **实验充分性**：
   - 报告“最佳运行”而非均值，方差较大（如SCAN parse trees IID仅0.80±0.39），可能夸大实际能力。
   - GeoQuery上所有方法均未显著超越Transformer，sDTM甚至更差，说明在极小数据集上难以学习组合解。
   - 未在更大规模或真实文本语料上测试，泛化性存疑。
2. **方法局限**：
   - 依赖预定义的二叉树操作，对于非树结构或更复杂的数据流仍需转换，可能损失信息。
   - 零样本词汇泛化要求嵌入向量固定且初始化合适，否则失败（如SCAN无噪声时准确率为0）。
   - 训练不稳定，部分随机种子陷入差解（局部最优化）。
3. **对比公平性**：
   - NQG基于预训练BERT嵌入，而sDTM从头训练，比较时可能不绝对公平。
   - 未与大型预训练模型（如T5）对比，尽管论文解释是避免预训练干扰。
4. **扩展性局限**：
   - 剪枝超参数k需手动设定，影响性能与内存的权衡。
   - 树深度增加时仍需足够内存（k=2048），未能完全解决指数级增长问题。
5. **应用限制**：当前主要面向合成或结构化数据集，对自然语言中的非线性组合、歧义处理尚待验证。

（完）
