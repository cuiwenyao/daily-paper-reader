---
title: Concept-Guided Interpretability via Neural Chunking
title_zh: 通过神经分块实现概念引导的可解释性
authors: "Shuchen Wu, Stephan Alaniz, Shyamgopal Karthik, Peter Dayan, Eric Schulz, Zeynep Akata"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=o87dDXYLXC"
tags: ["query:ns-xai"]
score: 7.0
evidence: 提出基于神经分块的概念引导可解释性方法，应用于大语言模型
tldr: 神经网络内部活动常被认为难以理解。本文提出反射假说：神经网络群体活动反映训练数据规律。基于此，借鉴认知科学中的分块方法，将高维神经动力学分割为对应概念的可解释单元，并在RNN和LLM上验证有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1407, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1430, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 931, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 817, \"height\": 651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1365, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 709, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1414, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1378, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1357, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1392, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1443, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1440, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1444, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1431, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 660, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1406, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 863, \"height\": 2315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 864, \"height\": 2315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 865, \"height\": 2360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1439, \"height\": 819, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1447, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1451, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1123, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1380, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1336, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1411, \"height\": 818, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1094, \"height\": 1351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1438, \"height\": 1566, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1407, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1248, \"height\": 648, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 567, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 883, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1289, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1261, \"height\": 183, \"label\": \"Table\"}]"
motivation: 神经网络黑箱特性阻碍了对其内部工作机制的理解。
method: 利用认知科学中的分块方法将神经活动分割为对应概念的可解释单元。
result: 在RNN和LLM上验证了反射假说，并成功提取可解释概念。
conclusion: 提供了一种揭示神经网络内部概念表示的新视角。
---

## Abstract
Neural networks are often described as 
black boxes, reflecting the significant challenge of understanding their internal workings and interactions. We propose a different perspective that challenges the prevailing view: rather than being inscrutable, neural networks exhibit patterns in their raw population activity that mirror regularities in the training data. We refer to this as the \textit{Reflection Hypothesis} and provide evidence for this phenomenon in both simple recurrent neural networks (RNNs) and complex large language models (LLMs).
Building on this insight, we propose to leverage cognitively-inspired methods of \textit{chunking} to segment high-dimensional neural population dynamics into interpretable units that reflect underlying concepts.
We propose three methods to extract these emerging entities, complementing each other based on label availability and neural data dimensionality. Discrete sequence chunking (DSC) creates a dictionary of entities in a lower-dimensional neural space; population averaging (PA) extracts recurring entities that correspond to known labels; and unsupervised chunk discovery (UCD) can be used when labels are absent. 
We demonstrate the effectiveness of these methods in extracting entities across varying model sizes, ranging from inducing compositionality in RNNs to uncovering recurring neural population states in large language models with diverse architectures, and illustrate their advantage to other interpretability methods. 
Throughout, we observe a robust correspondence between the extracted entities and concrete or abstract concepts in the sequence. Artificially inducing the extracted entities in neural populations effectively alters the network's generation of associated concepts.
Our work points to a new direction for interpretability, one that harnesses both cognitive principles and the structure of naturalistic data to reveal the hidden computations of complex learning systems, gradually transforming them from black boxes into systems we can begin to understand.

Implementation and code are publicly available at _https://github.com/swu32/Chunk-Interpretability_

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：神经网络常被视为“黑箱”，其内部高维神经活动难以理解。现有可解释性方法多聚焦于单个神经元或低维投影，但神经元往往是多语义的，且高维群体活动中蕴含的结构信息被忽视。
- **研究动机**：人类认知能够从感知流中自动分割出重复的模式（“分块”），形成概念实体。受此启发，作者提出**反射假说**：神经网络内部神经群体活动会反映训练数据中的结构化规律，因此可以借鉴认知分块原则来提取可解释的概念单元。
- **整体含义**：本文开辟了基于认知原理的神经可解释性新方向，通过将高维神经动力学分割为概念对应的“块”，将黑箱逐步转化为可理解的系统，并提供了因果干预手段。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：假设神经网络隐藏层活动存在重复出现的模式（chunks），这些模式与输入序列中的概念（具体词、抽象标签、叙事结构）一一对应。通过三种互补方法从神经活动中提取这些块。

- **关键技术细节**：

  - **离散序列分块（DSC）**：
    - 适用于隐藏维度 d 较小的情况（如简单RNN）。
    - 步骤：①对每个神经元的活动进行聚类，将神经活动向量转化为离散符号字符串；②使用类似文本压缩的迭代合并算法，从符号序列中提取频繁出现的“字符串组合”作为块字典。
    - 输出：一个符号化的神经轨迹解析结果和对应的块词汇表。

  - **神经群体平均（PA）**：
    - 适用于大模型（如LLaMA-3）且已知概念标签（如“cheese”出现的位置）。
    - 步骤：①对概念出现位置的隐藏状态取平均，得到原型向量 \(\bar{h}_{C(s)}\)；②通过公差阈值选择对该概念稳定响应的神经元子集 \(C(s)\)；③计算波动半径 \(\Delta\)，定义块为一个闭球 \(B(\bar{h}_{C(s)}, \Delta)\)。
    - 用信号检测指标（TPR/FPR）评估块的质量，并自动选择最优公差阈值。

  - **无监督分块发现（UCD）**：
    - 适用于无标签数据，直接从嵌入空间学习块字典。
    - 优化目标：最小化每个嵌入与其最相似字典项之间的负余弦相似度，即 \(\mathcal{L} = -\frac{1}{M}\sum_{m}\max_k \text{SIM}(D_k, X_m)\)。
    - 学习完成后，每个嵌入由单个块表示，实现离散化解析。

- **因果干预**：通过**嫁接**（将神经群体替换为提取的块原型）和**冻结**（将支持块的活动置零）来可控地改变网络行为。

### 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集与场景**：
  - **简单RNN**：合成序列（包含反复出现的模式ABCD、带噪声的嵌入、层级结构词汇），验证反射假说和因果嫁接对组合学习的影响。
  - **大语言模型**：
    - 主要模型：LLaMA-3-8B（主模型），T5-small、RWKV-169M、Mamba-130M作为跨架构验证。
    - 文本数据：Emma（简·奥斯汀）、ROCStories（故事）、TREC问题分类数据集（6类上下文）。
    - 抽象概念：20个叙事结构一致的故事 vs. 13个不一致故事，用于提取叙事模式块。

- **Benchmark**：无单独设立的标准基准，主要与**稀疏自编码器（SAE）**在概念预测任务上对比（图4）。PA在预测特定概念（如“cheese”）上优于SAE选出的最相关神经元。

- **对比方法**：SAE（来自EleutherAI/sparsify）；此外与未扰动的控制组对比因果干预效果。

### 4. 资源与算力

- **硬件**：内部集群，配备NVIDIA Quadro RTX 6000 GPU。
- **具体耗时**：
  - 采集LLaMA-3-8B残差流数据：约25 GPU小时。
  - SAE神经元采集：约5 GPU小时。
  - 无监督分块学习（32层）：约90 GPU小时。
  - 探索性/消融实验：约50 GPU小时。
  - **总估算**：约170 GPU小时。
- **说明**：论文明确提供了上述数据，算力开销合理，尤其PA方法在CPU上即可快速完成。

### 5. 实验数量与充分性

- **实验数量**：
  - RNN部分：多种合成序列（ABCD周期性、稀疏嵌入、随机噪声、层级结构），包含因果嫁接、组合学习、上下文区分、层级深度分析。
  - LLM部分：多架构（LLaMA-3, T5, RWKV, Mamba），多种概念（具体词如“cheese”“cake”，高频词top 100，抽象叙事结构，POS标签），因果干预（嫁接/冻结）在TREC数据集上量化。
  - 对比实验：PA vs. SAE（图4）；UCD超参数K的消融（500~8000，图30）；不同层级嫁接效果（表1）。
- **充分性与公平性**：
  - 覆盖了从小规模RNN到大规模LLM的多个模型，验证了方法通用性。
  - 对比SAE时，使用相同的训练/测试数据，指标为TPR/FPR，公平。
  - 因果干预设置了控制组（无干预），并统计了概念出现概率变化。
  - 不足之处：没有与其他概念发现方法（如ConceptSHAP、TCAV）比较；SAE对比仅针对概念预测，未比较因果干预效果。

### 6. 论文的主要结论与发现

1. **反射假说成立**：神经网络（RNN和LLM）的神经群体活动确实反映了训练数据中的规律性模式，且在不同架构中表现一致。
2. **分块方法有效提取概念编码**：DSC、PA、UCD三种方法均能从神经轨迹中提取出与具体词、抽象标签、叙事结构对应的块，且PA在概念预测上优于SAE。
3. **因果干预可行**：嫁接和冻结神经块能显著改变网络生成的相关概念概率，且早期层嫁接效果最好。
4. **跨架构泛化**：PA在LLaMA-3、T5、RWKV、Mamba上均能提取高质量概念块。
5. **抽象结构编码**：PA可以提取叙事模式的神经块，区分结构一致与非一致故事。

### 7. 优点

- **认知启发**：将人类分块认知原理引入神经网络可解释性，视角新颖。
- **方法简洁高效**：PA无需训练，基于平均和距离计算；UCD仅需单层优化，计算量远小于SAE（对比：SAE每个层需10⁸参数+数十GPU小时，UCD仅需数小时）。
- **跨模型通用**：适用于不同架构（RNN、Transformer、状态空间模型），无需修改模型。
- **因果验证**：不仅发现关联，还通过嫁接/冻结展示了因果作用，增强了可解释性的可信度。
- **支持抽象概念**：能提取名词、介词、叙事模式、POS标签等不同层次的概念。

### 8. 不足与局限

- **上下文敏感性未充分处理**：对于多义词（如“bank”）或高度依赖上下文的词（如介词），PA的平均原型可能模糊，导致识别效果下降（论文承认此局限，表6显示“if”“at”等词嫁接效果差）。
- **无监督方法UCD的超参数K需手动设定**：虽然实验显示对K不敏感，但缺乏自动选择机制。
- **跨层交互未分析**：当前方法逐层独立处理，未建模层间块的关系或信息流动。
- **对比范围有限**：仅与SAE进行了部分对比，未与概念激活向量（TCAV）、概念瓶颈等方法全面比较。
- **可解释性的粒度**：提取的块仍是向量形式，其语义解释需人工关联（如与POS标签匹配），尚未实现自动化语义标注。
- **规模扩展性**：对70B以上模型的计算量估算仅给出理论值，未实际验证。

（完）
