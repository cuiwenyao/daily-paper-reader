---
title: "Metastable Dynamics of Chain-of-Thought Reasoning: Provable Benefits of Search, RL and Distillation"
title_zh: 思维链推理的亚稳态动力学：搜索、强化学习与蒸馏的可证明益处
authors: "Juno Kim, Denny Wu, Jason D. Lee, Taiji Suzuki"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=2HJcVtuovs"
tags: ["query:ns-xai"]
score: 9.0
evidence: 对思维链推理动态建模，证明搜索和RL对推理提升的好处
tldr: 本文将思维链生成建模为亚稳态马尔可夫过程，证明易推理步聚形成密集簇而难步聚间边稀疏，从而解释推理中的相变现象，并理论证明推理时搜索、强化学习和蒸馏能够有效提升推理能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-2hjcvtuovs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1298, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2hjcvtuovs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1065, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2hjcvtuovs/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1369, \"height\": 413, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-2hjcvtuovs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2hjcvtuovs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 1207, \"label\": \"Table\"}]"
motivation: 需要从理论上理解推理时计算（如搜索）为何能提升大语言模型推理能力。
method: 将思维链生成视为亚稳态马尔可夫过程，分析易/难推理步聚的聚类特性。
result: 证明了推理时搜索、强化学习和蒸馏在理论上对推理能力的可验证提升。
conclusion: 该框架为理解CoT推理的计算动态提供了理论支撑，并指导了训练策略。
---

## Abstract
A key paradigm to improve the reasoning capabilities of large language models (LLMs) is to allocate more inference-time compute to search against a verifier or reward model. This process can then be utilized to refine the pretrained model or distill its reasoning patterns into more efficient models. In this paper, we study inference-time computation by viewing chain-of-thought (CoT) generation as a metastable Markov process: easy reasoning steps (e.g., algebraic manipulations) form densely connected clusters, while hard reasoning steps (e.g., applying a relevant theorem) create sparse, low-probability edges between clusters, leading to phase transitions at longer timescales. Under this framework, we prove that implementing a search protocol that rewards sparse edges improves CoT by decreasing the expected number of steps to reach different clusters. In contrast, we establish a limit on reasoning capability when the model is restricted to local information of the pretrained graph. We also show that the information gained by search can be utilized to obtain a better reasoning model: (1) the pretrained model can be directly finetuned to favor sparse edges via policy gradient methods, and moreover (2) a compressed \emph{metastable representation} of the reasoning dynamics can be distilled into a smaller, more efficient model.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：思维链推理的亚稳态动力学

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：大语言模型（LLM）的推理能力可通过在推理时分配更多计算资源（如搜索、验证器）大幅提升，但理论上为何这种“推理时计算”有效尚不清晰。现有工作多关注预训练阶段的扩展律，而对推理时计算的收益缺乏严格理论分析。
- **核心问题**：如何从动力学角度建模思维链（CoT）生成，并证明推理时搜索、强化学习（RL）和蒸馏在理论上能够提升推理能力？
- **整体含义**：论文将CoT生成建模为**亚稳态马尔可夫过程**：简单推理步骤形成密集簇，困难推理步骤形成稀疏边。在此框架下，搜索可识别关键稀疏边（困难步骤），进而通过RL微调或蒸馏压缩成更小模型，从而改善击中时间。同时证明：若模型只能访问局部信息，则推理任务难以完成。

## 2. 论文提出的方法论：核心思想、关键技术细节
### 核心思想
- 将状态空间划分为 \(K\) 个密集簇 \(C_1, \ldots, C_K\)，簇内易步骤概率 \(O(1)\)，簇间难步骤概率 \(O(\varepsilon)\)（\(\varepsilon\) 很小）。
- 定义扰动马尔可夫链 \(X^\varepsilon\)，其未扰动链 \(X^0\) 在簇内约化。利用**亚稳态理论**分析击中时间：簇内混合快，簇间转移慢，形成时间尺度分离。

### 关键技术细节
- **预训练模型**：采用线性softmax模型 \(\hat{p}_W(\cdot|x) = \text{softmax}(\langle W, x\rangle)\)，通过交叉熵损失梯度下降学习转移核 \(p^\varepsilon\)。算法1给出两阶段预训练：首先学习所有边，阈值筛除后继续优化，最终误差指数级小。
- **搜索稀疏边（Algorithm 2）**：
  - PRM模式：外循环 \(R = \Theta(K\log K)\) 次，内循环并行 \(N = \Theta(\log K)\) 条轨迹，初始 \(T_0\) 步探索簇，随后监控超出簇的边，收集稀疏边集 \(\hat{E}\) 至外部奖励模型。
  - RL模式：使用PPO-Clip，基于 \(\hat{E}\) 定义优势函数 \(\hat{A}(x,y) = 1_{(x,y)\in\hat{E}}\)，通过符号梯度上升提升稀疏边概率至 \(\varepsilon_{\max}\)。
- **蒸馏（Algorithm 4）**：
  - 通过聚类标签映射 \(\iota: S \to S^\circ\) 将每个状态挂到代表点，收集 \(X^\varepsilon\) 轨迹中的簇间转移数据 \(D_{\text{dist}}\)。
  - 在 \(K \times K\) 的softmax模型上训练，学习元链 \(q^\varepsilon_\circ\)，然后进行时间重缩放（乘以 \(\beta = \Theta(\log(M/\varepsilon))\)）得到最终蒸馏模型 \(\hat{q}_{Z^+}\)。
- **逻辑任务与学习理论下界（Section 5）**：
  - 定义群作用逻辑计算，证明若模型只能访问局部邻居（路径或无搜索），则统计查询维度（SDA）指数级大，无法多项式时间内学习；只有全局搜索才能有效解决。

## 3. 实验设计
- **数据集/场景**：本文为纯理论分析，未使用实际数据集。构建了抽象图模型（状态空间 \(S\)，簇大小 \(M\)，稀疏边参数 \(\varepsilon\)）和逻辑推理任务（群作用、布尔值计算）。
- **Benchmark**：无。比较四种信息访问级别：无预训练、路径-only、局部搜索、全局搜索，证明全局搜索的必要性。
- **对比方法**：论文未运行实际实验，但理论中对比了PRM模式、RL模式、蒸馏模式与无搜索基线的击中时间下界。

## 4. 资源与算力
- **未明确说明**。论文未提供任何GPU型号、训练时长或实际算力开销。仅理论分析了算法复杂度：预训练需 \(T_1 = e^{\Theta(KM^2\varepsilon^{-2})}\)、\(T_2 = e^{\Theta(KM\varepsilon^{-2})}\) 步；搜索复杂度 \(RT_{\max} = e^{\Theta(KM/\varepsilon)}\)；蒸馏需 \(T_{\text{dist}} = e^{\Theta(M^2\varepsilon^{-2})}\) 步。

## 5. 实验数量与充分性
- **无实证实验**。论文所有结论均基于数学证明（定理、推论、注记），未进行任何实际LLM或图模拟验证。理论分析较完整，包括预训练收敛性、搜索一致性、PPO收敛性、蒸馏保真性、SQ复杂度下界等。但缺乏定量数值实验或消融研究，难以评估理论假设在实际场景中的合理性。

## 6. 论文的主要结论与发现
1. **搜索改善击中时间**：通过识别稀疏边并提升其概率，期望击中时间从 \(e^{\Theta(KM/\varepsilon)}\) 降至 \(e^{\Theta(KM/\varepsilon_{\max})}\)。
2. **RL可微调基础模型**：PPO-Clip可将稀疏边概率提升至 \(\varepsilon_{\max}\)，且模型改动量极小（TV距离 \(o(1/M)\)）。
3. **蒸馏可压缩为元链**：蒸馏后的模型 \(\hat{q}_{Z^+}\) 仅关注簇间转移，击中时间与簇数 \(K\) 线性相关，与 \(\varepsilon\) 无关，且保留原始动力学的逃逸概率。
4. **局部信息不足**：若模型只能访问局部邻居或一条路径，逻辑推理任务统计不可学习（SDA指数级大），必须依赖全局搜索。

## 7. 优点
- **理论框架新颖**：首次将亚稳态马尔可夫链理论引入CoT推理分析，严格区分易/难步骤的动态分离，为推理时计算提供直观的数学模型。
- **可证明保证**：对预训练、搜索、RL、蒸馏均给出收敛性、一致性或最优性证明，理论完备。
- **学习理论下界**：提出带额外信息的统计查询维度（SDA），并证明局部搜索不足以解决逻辑推理，从理论上支持“搜索需要足够长”的认知。
- **机制清晰**：将搜索视为识别稀疏边，RL视为重加权，蒸馏视为压缩簇内细节，三个环节逻辑连贯。

## 8. 不足与局限
- **缺乏实证验证**：论文全篇无任何实际实验或模拟，强假设（图结构、线性softmax、簇均匀混合等）在真实LLM中是否成立未经验证。
- **假设过于理想化**：例如稀疏边概率固定为 \(\varepsilon\)、每簇最多 \(n_{\text{out}}\) 个源点、簇内混合时间常数、群作用均匀等，这些在复杂真实推理中难以保证。
- **忽略实际因素**：未考虑搜索的复杂性（如树搜索的广度、回溯）、策略梯度算法在实际中的方差、蒸馏的数据收集效率等问题。
- **仅针对简单路径任务**：逻辑任务采用群作用抽象，但真实推理（如数学证明、常识推理）远更复杂，可能不满足均匀随机性假设。
- **未讨论计算资源权衡**：虽然理论分析了收敛步数，但未考虑实际中的噪声、采样成本、模型容量等限制。

（完）
