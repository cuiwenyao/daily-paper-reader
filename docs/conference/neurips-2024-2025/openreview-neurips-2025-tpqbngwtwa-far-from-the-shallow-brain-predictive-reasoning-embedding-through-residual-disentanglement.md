---
title: "Far from the Shallow: Brain-Predictive Reasoning Embedding through Residual Disentanglement"
title_zh: 远离浅层：通过残差解缠得到大脑预测性的推理嵌入
authors: "Linyang He, Tianjun Zhong, Richard Antonello, Gavin Mischler, Micah Goldblum, Nima Mesgarani"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tPqBnGwTwa"
tags: ["query:ns-xai"]
score: 5.0
evidence: 分析LLM中的推理表示用于大脑编码
tldr: 针对LLM表示高度纠缠导致大脑编码偏向浅层语言特征的问题，提出残差解缠方法，从模型内部表示中分离出推理相关的成分。该方法首先探测LM以识别特征，然后通过残差逐步剥离浅层信息。实验证明，解缠后的推理表示能更好地预测大脑对复杂推理任务的响应，为神经符号可解释性提供了跨学科视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 901, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1298, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 578, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tpqbngwtwa/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1441, \"height\": 1626, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-tpqbngwtwa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1165, \"height\": 487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tpqbngwtwa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tpqbngwtwa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1120, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tpqbngwtwa/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1291, \"height\": 656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tpqbngwtwa/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 639, \"height\": 235, \"label\": \"Table\"}]"
motivation: LLM表示高度纠缠，妨碍了大脑编码中对推理等高层次过程的分离。
method: 提出残差解缠方法，通过逐步剥离浅层语言特征来提取推理相关表示。
result: 解缠后的推理表示在预测脑响应方面优于原始表示，特别是在高级推理区域。
conclusion: 残差解缠可有效隔离推理相关表示，促进认知科学和AI可解释性交叉研究。
---

## Abstract
Understanding how the human brain progresses from processing simple linguistic inputs to performing high-level reasoning is a fundamental challenge in neuroscience. While modern large language models (LLMs) are increasingly used to model neural responses to language, their internal representations are highly "entangled," mixing information about lexicon, syntax, meaning, and reasoning. This entanglement biases conventional brain encoding analyses toward linguistically shallow features (e.g., lexicon and syntax), making it difficult to isolate the neural substrates of cognitively deeper processes. Here, we introduce a residual disentanglement method that computationally isolates these components. By first probing an LM to identify feature-specific layers, our method iteratively regresses out lower-level representations to produce four nearly orthogonal embeddings for lexicon, syntax, meaning, and, critically, reasoning. We used these disentangled embeddings to model intracranial (ECoG) brain recordings from neurosurgical patients listening to natural speech. We show that: 1) This isolated reasoning embedding exhibits unique predictive power, accounting for variance in neural activity not explained by other linguistic features and even extending to the recruitment of visual regions beyond classical language areas. 2) The neural signature for reasoning is temporally distinct, peaking later (~350-400ms) than signals related to lexicon, syntax, and meaning, consistent with its position atop a processing hierarchy. 3) Standard, non-disentangled LLM embeddings can be misleading, as their predictive success is primarily attributable to linguistically shallow features, masking the more subtle contributions of deeper cognitive processing. Our work provides compelling neural evidence for an abstract reasoning computation during language comprehension and offers a robust framework for mapping distinct cognitive functions from artificial models to the human brain.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
**研究动机**：理解人脑从简单语言输入到高级推理的神经计算机制是神经科学的基本挑战。现代大语言模型（LLM）常被用于建模语言相关的神经响应，但其内部表示高度“纠缠”，混合了词汇、句法、语义和推理信息。这种纠缠导致传统的脑编码分析偏向于词汇、句法等浅层特征，难以分离出推理等更深层认知过程的神经基础。

**整体含义**：论文通过提出残差解缠方法，从LLM表示中分离出推理特异性成分，并将其用于预测颅内脑电（ECoG）记录，证明了存在与抽象推理对应的神经信号，且具有独特的时间动态和空间分布。

## 2. 方法论
**核心思想**：利用LLM层次结构中不同特征的涌现顺序，通过逐步回归去除低层特征，获得近似正交的特征特异性嵌入，从而孤立出推理表示。

**关键技术细节**：
- **层定位**：使用最小对探测（minimal pair probing）分别在句法（BLiMP）、语义（COMPS-BASE）和推理（COMPS-WUGS-DIST）数据集上训练逻辑回归分类器，确定各特征在LLM中首次饱和的层：词法层L_l = 0，句法层L_s（Qwen2.5-14B中为第6层），语义层L_m（第20层），推理层L_r（第30层）。
- **残差嵌入构造**：
  - 词法嵌入E_l = H_0（第0层隐藏状态）。
  - 句法残差E_s = H_s - g_l(H_l)，其中g_l是从词法层预测句法层的岭回归。
  - 语义残差E_m = H_m - g_s(H_s)，其中g_s是从句法层预测语义层的岭回归。
  - 推理残差E_r = H_r - g_m(H_m)，其中g_m是从语义层预测推理层的岭回归。
- **训练岭回归**：利用同一播客系列的16集转录（共16万token）训练回归模型，避免过拟合。

**公式文字说明**：每一步回归使用岭回归最小化预测误差，得到残差表示。通过对各残差进行矩阵级和token级正交性验证，证明它们近似正交且保留了各自特征的信息。

## 3. 实验设计
**数据集**：
- 探测数据集：BLiMP（67种句法最小对）、COMPS（语义与推理）、ProntoQA（多步演绎推理）、WinoGrande（常识推理）。
- 脑电数据集：Podcast ECoG（9名参与者，1330个电极，听30分钟故事，高伽马带70-200Hz）。
- 扩展语料：同一播客的16集转录用于训练回归。

**基准与方法对比**：
- 对比方法：原始LLM全嵌入（未解缠）vs. 解缠后的四个特征嵌入（词法、句法、语义、推理）。
- 评估指标：皮尔逊相关，并结合词汇率基线（词起始和音节率）和Fisher z变换后的零分布检验（Bonferroni校正）。
- 消融实验：验证解缠前后特征正交性、特征探测准确率、脑编码时空模式。

## 4. 资源与算力
论文附录G明确报告：
- 隐藏状态提取：4×NVIDIA L40 GPU，约40分钟，GPU内存约4×30GB。
- 层探测：1×NVIDIA L40 GPU；BLiMP 26个范式平均2.2分钟/个；COMPS-BASE约1h47min；COMPS-WUGS-DIST约1h。
- 残差构建：CPU（Scikit-learn），每个岭回归<10分钟。
- 脑编码：CPU，全实验约5小时。
- 总体可在配备1×L40 GPU + 30GB RAM的工作站上复现。

## 5. 实验数量与充分性
**实验数量**：
- 跨17个Qwen模型（1.8B~14B，多个版本）验证特征层次顺序，仅Qwen-1.8B有微异。
- 在三种推理基准（COMPS-WUGS-DIST、ProntoQA、WinoGrande）上验证推理饱和层一致性。
- 残差验证：矩阵正交性证明、token级余弦相似度计算、特征探测准确率（含BoW基线）。
- 脑编码：分析峰值相关、时间动态（±2s窗口）、空间分布（MNI坐标）、区域对比（IFG、STG、SFG、视觉皮层）、电极重叠、偏侧化。

**充分性与公平性**：
- 实验设计完整，覆盖探测-解缠-编码全流程；使用多种对比和统计检验（Welch t检验、FDR校正、零分布）。
- 方法公开（代码将发布），数据集均为公开许可。
- 但在主要脑编码实验中仅使用了Qwen2.5-14B一个模型，虽已验证跨模型探测一致性，但未做跨模型脑编码对比，可能存在偏差。

## 6. 主要结论与发现
1. **推理嵌入具有独特预测能力**：解释其他特征未覆盖的神经活动方差，并扩展至视觉皮层等非经典语言区。
2. **推理神经信号时间分化**：推理峰值约350-400ms，晚于词法、句法和语义，符合处理层级顶端位置。
3. **原始LLM嵌入具有误导性**：预测成功主要来自浅层特征，解缠后才能显露推理贡献。
4. **浅层特征主导但覆盖窄**：词法和句法相关高但电极少，语义和推理覆盖更广但相关略低。
5. **推理涉及更广泛皮层**：包括额上回和视觉皮层，提示多模态认知整合。
6. **层次涌现结构稳健**：几乎所有Qwen模型均遵循词法→句法→语义→推理的涌现顺序。

## 7. 优点
- **方法论创新**：首次将残差解缠应用于LLM特征分离，提出系统性的层定位+残差构造流程。
- **验证充分**：从正交性（矩阵级、token级）、特征探测准确率、BoW基线对比等多角度证明解缠有效性。
- **神经解释性**：结合高时间分辨率的ECoG数据，揭示推理独立的时空神经特征，为认知层级理论提供直接证据。
- **跨模型一致性检验**：覆盖多个规模与版本的Qwen模型，增强方法稳健性。
- **代码公开与可复现**：详细记录计算资源与步骤，促进后续研究。

## 8. 不足与局限
- **ECoG空间覆盖有限**：额叶等推理关键区域采样不足，未来可结合fMRI等互补模态。
- **推理类型局限**：仅测试演绎推理、属性继承和常识推理，缺乏归纳推理、类比推理等。
- **主模型单一**：脑编码实验仅使用Qwen2.5-14B，未验证其它LLM的解缠效果对脑预测的一致性。
- **更深层作用未探明**：推理饱和后的更深层（30层后）可能编码更抽象表示，论文未深入分析。
- **线性回归假设**：残差构造依赖线性岭回归，可能遗漏非线性相互关系。
- **词汇率协变量控制**：仅控制词起始和音节率，未精细建模声学特征差异。

（完）
