---
title: Neuro-Symbolic Temporal Point Processes
title_zh: 神经符号时序点过程
authors: "Yang Yang, Chao Yang, Boyang Li, Yinghao Fu, Shuang Li"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=HDrXBr26UI"
tags: ["query:ns-xai"]
score: 9.0
evidence: 神经符号规则归纳用于事件解释
tldr: 本文提出一个神经符号规则归纳框架，在时间点过程模型中高效发现紧凑的时间逻辑规则以解释不规则事件。采用端到端可微学习，将谓词和规则表示为向量嵌入，通过梯度下降学习规则组合，并结合顺序覆盖算法提升效率。为神经符号在可解释时序建模中提供新方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-hdrxbr26ui/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1502, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hdrxbr26ui/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 771, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hdrxbr26ui/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 770, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hdrxbr26ui/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 653, \"height\": 632, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 791, \"height\": 587, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 902, \"height\": 725, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 844, \"height\": 482, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 888, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 743, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 899, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1158, \"height\": 942, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-hdrxbr26ui/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 844, \"height\": 292, \"label\": \"Table\"}]"
motivation: 现有方法难以高效发现紧凑的时序逻辑规则来解释不规则事件。
method: 提出神经符号框架，用向量嵌入表示谓词和规则，通过梯度下降学习规则权重。
result: 端到端学习时序规则，实验证明高效且能发现紧凑的可解释规则。
conclusion: 神经符号融合有效提升不规则事件的可解释性建模。
---

## Abstract
Our goal is to $\textit{efficiently}$ discover a compact set of temporal logic rules to explain irregular events of interest. We introduce a neural-symbolic rule induction framework within the temporal point process model. The negative log-likelihood is the loss that guides the learning, where the explanatory logic rules and their weights are learned end-to-end in a $\textit{differentiable}$ way. Specifically, predicates and logic rules are represented as $\textit{vector embeddings}$, where the predicate embeddings are fixed and the rule embeddings are trained via gradient descent to obtain the most appropriate compositional representations of the predicate embeddings. To make the rule learning process more efficient and flexible, we adopt a $\textit{sequential covering algorithm}$, which progressively adds rules to the model and removes the event sequences that have been explained until all event sequences have been covered. All the found rules will be fed back to the models for a final rule embedding and weight refinement. Our approach showcases notable efficiency and accuracy across synthetic and real datasets, surpassing state-of-the-art baselines by a wide margin in terms of efficiency.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：如何从带有时间戳的不规则事件序列中，高效且自动地发现**紧凑、可解释的时序逻辑规则**，从而解释目标事件（如患者健康突变、异常交易）的发生机制。
- **背景动机**：  
  - 传统参数化时序点过程（如Hawkes过程）可解释性强但灵活性不足。  
  - 神经TPP（如RMTPP、Transformer Hawkes）表达力强但属于黑箱模型，在高风险场景（医疗、金融）中缺乏透明度。  
  - 已有可解释TPP方法（如TELLER）假设规则预先给定或使用不可微规则学习，效率低且难以扩展。  
- **整体目标**：在保证可解释性的同时提升模型灵活性和学习效率，实现**端到端可微的时序规则归纳**。

## 2. 方法论

### 核心思想
- 提出**神经符号时序点过程（NS-TPP）**，将规则学习转化为**规则向量嵌入**的学习过程。
- 规则嵌入作为可学习的“滤波器”，通过与固定的谓词嵌入计算相似度，自动选择谓词和时序关系组合成布尔逻辑规则（Horn规则）。
- 所有参数（规则嵌入、规则权重、基项）通过**负对数似然损失函数**进行梯度下降优化。

### 关键技术细节
- **谓词嵌入**：每个谓词（事件类型）固定为d维向量，可通过预训练或人工指定（如one-hot）。同时设置哑谓词嵌入（零向量）以支持变长规则。
- **规则嵌入**：每个规则对应一个L×d的矩阵Qf，L为最大规则长度，每个行向量q_l作为槽位等待填充谓词。
- **规则选择机制**：  
  - 相似度分数：`W = softmax(Qf Kᵀ / τ)`，K为谓词嵌入矩阵，τ为温度参数。  
  - 通过Gumbel-max采样选择最佳匹配谓词索引，增加随机性避免陷入次优解。  
  - 允许选择哑谓词（索引0）使规则长度小于L。
- **神经符号特征构建**：  
  - **静态特征**：选取的谓词在历史中是否出现过（事实v=1/0），乘以对应相似度分数，再通过**最小值函数（soft-min近似）**替代乘积以保证数值稳定。  
  - **时序关系特征**：类似地，在谓词对之间学习关系类型（Before/Equal/After/None），同样通过相似度选择并整合事实。  
  - 最终特征为静态部分与时序部分的**软逻辑与**。
- **强度函数**：  
  `λ*(t) = b₀ + Σ γ_f · φ_f(H_t-)`，b₀为基项，γ_f为规则权重，φ_f为神经符号特征。
- **顺序覆盖算法**：  
  - 从空规则集开始，每次只学习一条规则（单规则模型）。  
  - 当规则收敛后，移除已被该规则解释的事件序列，继续学习下一条。  
  - 直到无新规则加入（或权重低于阈值），最后将所有规则放入完整模型进行联合微调。  
  - 优点：无需预设规则数量，分治策略降低学习复杂度。

### 公式与算法流程（文字说明）
1. 固定谓词嵌入矩阵K。  
2. 对每条规则初始化规则嵌入Qf（L×d）。  
3. 前向：计算W = softmax(Qf Kᵀ/τ)，Gumbel采样得到最佳匹配谓词索引，查询历史事实，计算φ_f。  
4. 构建强度函数并计算负对数似然。  
5. 反向传播更新Qf、γ_f、b₀。  
6. 收敛后，移除被解释序列，重复步骤2~5。  
7. 所有规则找到后，联合优化全部参数。

## 3. 实验设计

### 数据集与场景
- **合成数据**：  
  - 使用30个谓词（X1~X30），分3个规则组（Group1~3），每组包含1~3条规则，规则权重0.40~1.20。  
  - 每个样本只满足一个规则（或仅受基项影响）。  
  - 样本规模：5000、10000、20000个。共9个数据集（3组×3规模）。
- **真实数据**：  
  - **Car-Following**：460小时驾驶数据，5个驾驶行为谓词，10042个序列。目标：挖掘跟车模式规则。  
  - **LowUrine**：MIMIC-IV中4074名ICU脓毒症患者，29个生理指标。目标：发现导致尿量异常（预警脓毒症休克）的时序规则。

### 基准方法（Benchmark）
- **神经黑箱模型**：THP、RMTPP、ERPP、GCH、LG-NPP、GM-NLF。  
- **逻辑可解释模型**：TELLER、CLUSTER、CLNN。  
- 对比维度：规则学习准确率、学习时间、规则权重MAE、事件预测MAE。

### 评估指标
- **规则准确率**：严格匹配，要求规则完全等于真实规则（含时序关系）。  
- **学习时间**（秒，对数归一化显示）。  
- **规则权重MAE**。  
- **事件时间预测MAE**。

## 4. 资源与算力

- 文中**未明确指定GPU型号、数量或训练时长**。  
- 所有实验运行于**Linux服务器，Intel Xeon Gold 6248R CPU @ 3.00GHz，30Gi内存**。  
- 作者说明由于模型参数规模小，CPU比GPU更高效，因此NS-TPP在CPU上执行。基线方法除TELLER外均使用GPU。  
- 编程环境：Python 3.9.12, PyTorch 2.0.1。  
- 算力开销相对较小，训练速度是主要优势之一（比TELLER快约112倍）。

## 5. 实验数量与充分性

- **合成实验**：9个数据集（3组×3样本量），每个配置重复10次；对比TELLER和CLUSTER时使用4次运行取最优。  
- **规则准确率实验**：展示了不同重复次数（1~4次）下的性能，以及不同规模的比较。  
- **权重估计MAE**：在图4中展示。  
- **规则实例展示**：在表2、附录A展示了合成数据具体学习到的规则。  
- **事件预测实验**：合成数据（Group-3，20000样本）和两个真实数据集上对比11种基线。  
- **真实数据规则展示**：表4列出了Car-Following和LowUrine的关键规则，并附录F提供了医学文献佐证。  
- **充分性评价**：实验覆盖了多种数据规模、多种基线、规则学习与预测任务；准确性计算标准严格（完全匹配），对比公平。但缺少消融实验（如去掉覆盖算法、改变温度参数等）及对噪声鲁棒性的系统分析。

## 6. 主要结论与发现

1. **效率大幅提升**：NS-TPP相比SOTA（TELLER, CLUSTER）平均快112倍，同时准确率从49%提升至93%。  
2. **规则学习准确**：在合成数据上能精确恢复所有真实规则及权重（权重MAE低）。真实数据中找到与医学文献一致的规则，如LowUrine规则涉及乳酸、呼吸率、镁离子等。  
3. **预测性能领先**：在事件时间预测任务上，NS-TPP在所有数据集上MAE均低于基线模型（包括神经黑箱和逻辑模型）。  
4. **端到端可微有效**：将符号规则归纳转化为嵌入学习，使规则发现变得可微且高效，无需预先指定规则数量。

## 7. 优点

- **兼顾可解释性与灵活性**：通过固定谓词嵌入保持语义可解释，通过可学习规则嵌入实现灵活组合。  
- **高效的自适应规则发现**：顺序覆盖算法分治学习，免去预设规则数，降低搜索空间。  
- **鲁棒性**：使用嵌入表示和softmin函数，对输入噪声有一定容忍度；Gumbel采样增加探索性。  
- **与注意力机制类比**：特征构建类似严格的注意力，但使用乘法和最小值运算模拟逻辑与，设计巧妙。  
- **实验验证充分**：在多个难度的合成数据和真实场景下均表现优异，尤其速度优势突出。  
- **实用价值**：学到规则可直接用于临床决策支持（如脓毒症预警）或自动驾驶行为解释。

## 8. 不足与局限

- **谓词嵌入依赖先验知识**：当前方法要求预设或预训练谓词嵌入，可能限制在谓词含义未知时的应用。虽可随机初始化，但会影响规则解释性。  
- **规则长度上限L**：预设最大长度，长于L的规则无法学习，需依靠哑谓词填充，但可能引入冗余。  
- **温度参数τ需手动调节**：影响softmax逼近硬选择的精度，文中未讨论调参影响。  
- **合成数据假设简化**：每个样本只满足一个规则，与实际多规则共存场景有差距；未测试规则重叠或冲突的情况。  
- **真实数据验证有限**：仅测试两个领域，且LowUrine数据集样本量较小（4074患者），规则泛化性待更多验证。  
- **缺少消融实验**：未系统分析各组件（如覆盖算法、Gumbel采样、softmin替代）对最终性能的贡献。  
- **未考虑复杂时序关系**：规则仅支持两两谓词间的简单时序关系（Before/After/Equal/None），无法表达非二元或绝对时间约束。  
- **计算资源细节不详**：未报告具体训练时长、GPU型号等，难以复现资源消耗。

（完）
