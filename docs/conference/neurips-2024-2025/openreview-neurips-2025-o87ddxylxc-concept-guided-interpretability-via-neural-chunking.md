---
title: Concept-Guided Interpretability via Neural Chunking
title_zh: 通过神经组块实现概念引导可解释性
authors: "Shuchen Wu, Stephan Alaniz, Shyamgopal Karthik, Peter Dayan, Eric Schulz, Zeynep Akata"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=o87dDXYLXC"
tags: ["query:ns-xai"]
score: 7.0
evidence: 通过神经分块实现大模型概念级可解释性
tldr: 神经网络常被视为黑箱，本文提出反射假说：网络群体活动反映训练数据规律。借鉴认知科学中的组块化方法，将高维神经活动分割为可解释概念单元。在RNN和LLM上验证，为理解大型神经模型内部推理提供新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1407, \"height\": 709}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 785}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1430, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 931}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 404}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 240}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 817, \"height\": 651}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1365, \"height\": 472}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 709, \"height\": 622}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1414, \"height\": 987}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1378, \"height\": 514}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1357, \"height\": 449}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1392, \"height\": 589}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 359}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1443, \"height\": 367}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1440, \"height\": 362}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1444, \"height\": 368}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1431, \"height\": 808}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 660, \"height\": 557}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1406, \"height\": 1007}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 863, \"height\": 2315}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 864, \"height\": 2315}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 865, \"height\": 2360}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1439, \"height\": 819}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1447, \"height\": 821}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1451, \"height\": 738}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1123, \"height\": 709}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1380, \"height\": 617}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1336, \"height\": 373}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1411, \"height\": 818}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1094, \"height\": 1351}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-o87ddxylxc/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1438, \"height\": 1566}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1407, \"height\": 303}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1248, \"height\": 648}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 567, \"height\": 688}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 883, \"height\": 187}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 145}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1289, \"height\": 223}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-o87ddxylxc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1261, \"height\": 183}]"
motivation: 神经网络内部运作难以理解，缺乏揭示概念层面的解释方法。
method: 基于反射假说，使用认知启发的组块化方法分割神经活动为可解释概念。
result: 在RNN和LLM上证明神经活动模式确实对应训练数据正则性，组块化有效。
conclusion: 神经组块化是可解释大型模型推理的有前景方法。
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

## 1. 论文的核心问题与整体含义（研究动机和背景）

神经网络常被视为“黑箱”，其内部拥有数十亿计的参数和计算单元，使得人们难以理解其内部工作机制和决策过程。现有可解释性方法大多局限于单个神经元或低维投影，但神经元多语义性（polysemantic）普遍存在，且定义好的符号实体数量有限，导致理解高维神经活动极为困难。本文提出一种基于认知科学的新视角：神经网络的高度非线性、高维活动其实反映并“镜像”了训练数据中的结构和规律（称为**反射假说**，Reflection Hypothesis）。借鉴认知心理学中“组块化（chunking）”原理——人类能将高维感知流分割成可重复的有意义单元——本文开发了一套方法，将网络群体活动分割为可解释的概念单元，从而将黑箱逐步转变为可理解的系统。

## 2. 论文提出的方法论

**核心思想**：利用神经网络内部活动对数据规律的映射关系，通过认知启发的组块化方法，从高维神经群体活动中提取可重复、可解释的概念实体（chunk），这些实体对应具体单词、抽象词性标签乃至叙事结构等概念。

**关键技术细节**：

- **离散序列组块化（Discrete Sequence Chunking, DSC）**  
  适用于低维神经网络（如小RNN）。首先对每个神经元的激活值进行聚类，将每个时间步的连续向量转化为离散字符串（每个神经元对应一个聚类索引）。然后对字符串序列应用迭代合并方法，提取频繁出现的子序列作为“组块”词典。算法流程：初始化词典为所有唯一字符串 → 统计相邻字符串对频率，合并频率高于阈值的对 → 更新词典并重新解析序列，直至收敛。

- **神经群体平均（Population Averaging, PA）**  
  适用于高维网络（如LLaMA-3），且已知概念标签（如特定单词）。对于给定概念 s，收集其在训练序列中出现的所有位置索引 V(s)，计算这些位置上隐藏状态的均值向量 \(\bar{h}_{C(s)}\)，并筛选出对概念敏感的子神经元集 C(s)（活动值与均值偏差小于容差 tol）。定义波动半径 Δ = max_j ‖h_{C(s),j} - \(\bar{h}_{C(s)}\)‖₂² / d。测试时，判断一个新隐藏状态向量是否属于组块 B(\(\bar{h}_{C(s)}\), Δ) 内：若 ‖h_{C(s)} - \(\bar{h}_{C(s)}\)‖₂² / d ≤ Δ，则识别为该概念。通过扫描不同容差 tol 选择最优阈值（最大化TPR、最小化FPR）。

- **无监督组块发现（Unsupervised Chunk Discovery, UCD）**  
  适用于无标签场景。学习一个字典矩阵 D ∈ R^{K×d}，使得每个嵌入向量 X_m 与最相似的字典条目距离最小。损失函数为平均最大余弦相似度的负值：L = -1/M ∑_m max_k SIM(D_k, X_m)。在该方法下，可将网络处理过程表示为组块的激活与消失序列，从而简化高维嵌入。

## 3. 实验设计

### 数据集 / 场景
- **合成序列（RNN）**：生成包含周期模式（如ABCD）、带噪声背景（E/F/G）、上下文依赖（CD在ABCD和CDAB中不同），以及分层结构（从字母→词→短语）等多种序列，训练RNN进行下一字符预测。
- **自然语言（LLM）**：使用公开文本（如Emma by Jane Austen、Project Gutenberg语料），以及ROCStories故事数据集、TREC问题分类数据集。
- **叙事结构**：人工构造20个符合特定叙事的训练故事（如“去食品店→买东西→吃→反应”）和13个不符合叙事的控制故事，用于测试抽象模式。

### Benchmark / 对比方法
- **PA vs. SAE（稀疏自编码器）**：在LLaMA-3上对比PA与预训练SAE在概念检测上的真阳性率/假阳性率。
- **三类方法（DSC、PA、UCD）分别在相应场景下评估**，没有进行大规模横向对比，侧重于自身有效性验证。
- **因果干预（嫁接/冻结）**：比较嫁接概念组块后模型生成文本中概念出现概率与控制组（无干预）的差异，并在多个上下文（TREC六个类别）中评价。

### 实验充分性
- 在简单RNN上验证了反射假说、组块化解码、因果嫁接加速迁移学习、上下文相关的额外状态形成、层次结构对应多样组块等。
- 在LLaMA-3、T5、RWKV、Mamba四种不同架构的LLM上用PA提取概念组块，并在高频词列表（top 100）上评估。
- 叙事结构实验训练20+13故事，测试18+15故事。
- 嫁接实验在TREC六个类别各50个prompt上统计概念出现概率。
- UCD训练词典 K=2000，d=4096，在Emma语料上逐层训练，分析了层间组块交互与词性关联。
- 计算了PA与SAE的计算效率对比（见下文算力部分）。

**公平性**：对于PA与SAE的比较，均在同一LLaMA-3、相同测试数据上评估；但SAE的解码方式（取最活跃概念相关神经元的阈值）可能不是最优，存在一定偏差。DSC、PA、UCD三种方法针对不同场景设计，未进行交叉对比，但作者明确说明了各自适用场景。

## 4. 资源与算力

论文在附录I中明确给出了计算资源信息：
- 使用共享内部集群，配备NVIDIA Quadro RTX 6000 GPU。
- LLaMA-3-8B残差流神经活动数据收集：约25 GPU小时。
- SAE神经元数据收集：约5 GPU小时。
- 无监督组块发现（32层）训练：约90 GPU小时。
- 其他探索性/消融实验：约50 GPU小时。
- **总计约170 GPU小时**。

对比PA与SAE的计算成本：PA无需优化和梯度计算，仅需前向传播加少量距离计算；SAE需要多轮前向/反向传播，参数数量大得多（以LLaMA-3为例，SAE潜伏层131072神经元，参数量约10亿，训练每层100 epoch约6-10小时；UCD仅820万参数，每层1-2小时）。PA在CPU上也可快速完成。

## 5. 实验数量与充分性

实验覆盖了多个维度：
1. **简单RNN**：验证反射假说（图2a-d）、解码准确率达100%、因果嫁接、迁移学习、上下文状态、层次结构。
2. **LLM（4种架构）**：提取概念组块并评估TPR/FPR（图4、图5）；对比SAE（图4左）。
3. **叙事结构**：PA提取抽象叙事组块，测试集解码准确率高于控制（图6）。
4. **因果干预**：嫁接/冻结概念组块后的生成效果，量化概念出现概率变化（表1、表3-6）。
5. **UCD**：训练词典，分析层间组块交互与词性关联（图7、图32）。
6. **消融与参数鲁棒性**：UCD对K值敏感性（图30）、容差阈值选择。
7. **计算效率比较**：PA vs. SAE的参数量、训练时间。

总体实验较为全面，在多个模型、多个场景、多个概念类型上验证了方法。但缺少与更多可解释性方法（如Representation Engineering）的系统对比；PA与SAE的比较仅在概念检测任务上，未在因果干预上比较。

## 6. 论文的主要结论与发现

1. **反射假说得到验证**：无论是简单RNN还是大型LLM（LLaMA-3等），神经群体活动模式显著反映了训练数据中的正则性（如重复词语、抽象词性、叙事结构）。
2. **提出三种互补的组块提取方法**：DSC适用于低维神经状态，PA适用于高维且有标签概念，UCD适用于无标签场景，均可提取与概念高度对应的神经活动单元。
3. **组块可被用于因果干预**：通过嫁接（grafting）特定组块到网络隐藏状态，能可控地改变模型生成文本朝向概念相关主题；通过冻结（freezing）组块（设为零），能抑制概念产生。
4. **组块具有多层级概念对应**：从具体单词（cheese、cake）到抽象词性（名词、动词），再到叙事结构（情节模式），神经组块都能反映。
5. **与SAE比较**：PA在概念检测上表现更好，且计算开销低得多；UCD则提供了无监督下的可解释性路径。
6. **计算效率优越**：PA无需训练，UCD参数少、训练快，相比SAE有显著的资源优势。

## 7. 优点

- **认知科学与机器学习交叉创新**：将人类的组块化认知机制引入神经网络可解释性，提供了一种全新的、高层次的解释视角，摆脱了单一神经元或固定符号集的局限性。
- **方法架构无关且互补**：DSC、PA、UCD覆盖了低维/高维、有标签/无标签等各种场景，可直接应用于多种模型（RNN、Transformer、状态空间模型等），无需修改模型结构。
- **强因果验证**：通过嫁接/冻结神经组块直接影响模型输出，为“组块确实编码概念”提供了因果证据，而不仅仅是相关性。
- **实验设计丰富**：从合成数据到自然语言，从具体词到叙事结构，从简单RNN到多种LLM架构，验证了方法的泛化性。
- **计算成本极低**：PA可以CPU运行，UCD仅需单GPU数小时训练，远优于SAE等需要大量算力的方法，利于推广。
- **开源代码**：提供了完整实现和数据集，可复现性强。

## 8. 不足与局限

- **概念编码假定跨语境稳定**：PA方法假设同一概念在不同语境下具有相似的神经活动（取平均），但实际上语境敏感性很强。论文在附录E.7中讨论了介词等抽象词表现不佳，但未系统地处理多义词（如“bank”的两个含义）。
- **与现有方法的系统对比不够充分**：除了与SAE在概念检测上的单维度比较，未与Probing、Representation Engineering、Concept-based解释等方法进行系统对比（特别是因果干预效果上）。
- **PA的容差参数选择依赖验证集**：在训练数据上通过扫描选择最优容差，可能对数据分布变化敏感；虽在测试数据上评估了TPR/FPR，但泛化到全新领域的能力未验证。
- **UCD的可解释性有待加强**：虽然UCD提取的组块可与POS标签关联，但组块本身缺乏语义标签，需要人工解释或后处理。
- **规模扩展实验相对有限**：仅在8B模型上进行了完整实验，虽讨论了对70B+模型的预期计算量，但未实际验证。
- **叙事结构实验规模较小**：仅20+13训练故事和18+15测试故事，统计显著性可能受限。
- **未探索组块之间的动态关系**：论文提到了组块反映概念，但未深入分析组块随时间如何交互组合以产生复杂推理。

（完）
