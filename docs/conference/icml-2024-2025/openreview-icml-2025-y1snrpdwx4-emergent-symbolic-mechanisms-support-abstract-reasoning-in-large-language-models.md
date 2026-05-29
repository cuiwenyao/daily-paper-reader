---
title: Emergent Symbolic Mechanisms Support Abstract Reasoning in Large Language Models
title_zh: 涌现的符号机制支持大语言模型的抽象推理
authors: "Yukang Yang, Declan Iain Campbell, Kaixuan Huang, Mengdi Wang, Jonathan D. Cohen, Taylor Whittington Webb"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=y1SnRPDWx4"
tags: ["query:ns-xai"]
score: 9.0
evidence: 识别出大语言模型中支持抽象推理的涌现符号机制
tldr: 针对大语言模型推理能力是否依赖结构化机制的争论，该研究揭示了LLM内部涌现的符号架构：早期层符号抽象头将输入转换为抽象变量，中间层符号归纳头进行序列归纳，后期层检索头完成推理。这一发现表明符号机制是LLM抽象推理的基础，为神经符号集成提供了实证支持。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1326, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1641, \"height\": 1019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1658, \"height\": 918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1680, \"height\": 1006, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 1587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1421, \"height\": 1587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1420, \"height\": 1585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1677, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1170, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1178, \"height\": 1238, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1726, \"height\": 871, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1728, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1471, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1471, \"height\": 965, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1678, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1288, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1463, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1738, \"height\": 2172, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1170, \"height\": 2177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1738, \"height\": 1619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1735, \"height\": 2173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1741, \"height\": 1076, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1824, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1751, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1287, \"height\": 571, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1252, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 979, \"height\": 164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 810, \"height\": 746, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 621, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 796, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 894, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 885, \"height\": 166, \"label\": \"Table\"}]"
motivation: 探讨大语言模型抽象推理能力是否依赖结构化符号机制。
method: 通过内部机制分析识别出符号抽象头、符号归纳头和检索头三种计算单元。
result: 发现符号架构支撑了模型的抽象推理能力。
conclusion: 为神经符号集成和可解释推理提供了重要依据。
---

## Abstract
Many recent studies have found evidence for emergent reasoning capabilities in large language models (LLMs), but debate persists concerning the robustness of these capabilities, and the extent to which they depend on structured reasoning mechanisms. To shed light on these issues, we study the internal mechanisms that support abstract reasoning in LLMs. We identify an emergent symbolic architecture that implements abstract reasoning via a series of three computations. In early layers, *symbol abstraction heads* convert input tokens to abstract variables based on the relations between those tokens. In intermediate layers, *symbolic induction heads* perform sequence induction over these abstract variables. Finally, in later layers, *retrieval heads* predict the next token by retrieving the value associated with the predicted abstract variable. These results point toward a resolution of the longstanding debate between symbolic and neural network approaches, suggesting that emergent reasoning in neural networks depends on the emergence of symbolic mechanisms.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）是否真的具备结构化、类人的抽象推理能力，还是仅仅通过统计近似模仿训练数据？其内部是否存在类似符号系统的机制？
- **背景**：学术界对LLM推理能力存在激烈争论。一方面，有研究展示LLM在类比推理、规则归纳等任务上表现惊人；另一方面，批评者认为这不过是“随机鹦鹉”或近似检索。传统符号AI认为人类推理依赖符号处理，而连接主义（神经网络）是否也能涌现符号机制是长期争论焦点。
- **整体含义**：论文通过揭示LLM内部涌现的三阶段符号架构——符号抽象头、符号归纳头、检索头——提供了一个融合神经与符号方法的视角，表明神经网络可以通过学习自发发展出符号处理机制，从而支持抽象推理。这为理解LLM能力的本质及神经符号集成提供了关键证据。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
提出一个**三阶段涌现符号架构**，模型通过以下三步完成抽象推理：
1. **符号抽象**：早期层注意力头将输入token转化为抽象变量（符号），基于token间的关系（如相同/不同），且变量表示与具体token无关。
2. **符号归纳**：中间层注意力头对抽象变量序列进行归纳，预测下一个变量。
3. **检索**：后期层注意力头根据预测的抽象变量，检索对应的具体token（值），完成最终输出。

### 关键技术细节
- **因果中介分析（Causal Mediation Analysis, CMA）**：设计两种条件，分别隔离对抽象变量和具体token的表征。通过将激活从一种上下文“补丁”到另一种，计算因果中介分数，判断每个注意力头/层的作用。公式（Algorithm 1）：  
  \( s = \left[ f(c^*_1)[y_{c^*_1}] - f(c^*_1)[y_{c_1}] \right] - \left[ f(c_1)[y_{c^*_1}] - f(c_1)[y_{c_1}] \right] \)，其中 \(f(c)\) 是模型在上下文 \(c\) 上输出下一个token的logits，\(y_{c_1}\) 是 \(c_1\) 的正确输出，\(y_{c^*_1}\) 是补丁后预期的输出。
- **注意力分析**：直接观察识别出的注意力头的注意力模式是否符合假设（如符号抽象头应关注同一例子中相同变量的位置）。
- **表征相似性分析（RSA）**：计算注意力头输出的成对相似性矩阵，与理论预测的抽象变量相似矩阵或token相似矩阵进行相关分析。
- **解码分析**：训练线性分类器，从注意力头输出中解码抽象变量（A/B），并在不同token集上测试泛化，以验证抽象变量的不变性。
- **消融实验**：逐步移除识别出的头部，观察模型概率下降，并与控制组（替换为同层最低分头部）和随机基线对比。

## 3. 实验设计：使用了哪些数据集/场景、benchmark、对比了哪些方法

### 任务/数据集
1. **代数规则归纳（Identity Rules）**：ABA 或 ABB 规则，两/多轮上下文示例，待完成第三个例子。token 完全随机，避免统计模式。
2. **字母字符串类比（Letter String Analogies）**：后继或前驱关系。例如 [i j k] → [i j l]（后继），[j k l] → [i k l]（前驱）。
3. **言语类比（Verbal Analogies）**：同义或反义关系。例如 impoverished: poor / lazy: idle（同义），rich: poor / energetic: idle（反义）。

### 模型
- GPT-2（Small/Medium/Large/XL）
- Gemma-2（2B/9B/27B）
- Qwen2.5（7B/14B/32B/72B）
- Llama-3.1（8B/70B）
共13个模型。

### 对比方法
- 与标准归纳头（Olsson et al., 2022）的对比：计算前缀匹配分数与符号归纳头分数的相关性。
- 与函数向量（Todd et al., 2024）的对比：计算平均间接效应（AIE）与符号归纳头/抽象头分数的相关性。

### 性能测量
- 准确率（任务完成率）。
- 因果中介分数（用于定位关键头部）。
- 注意力模式可视化。
- RSA相关系数。
- 消融后正确概率。

## 4. 资源与算力（若未明确说明也指出）

- **明确信息**：实验基于TransformerLens和HuggingFace库。Llama-3.1 70B和Qwen2.5 72B使用两张NVIDIA H100 80G GPU；其他较小模型使用单张H100 GPU。模型权重以bfloat16加载。
- **未说明**：具体训练时长、总GPU小时数、实验重复次数等未提供。但因果中介分析、注意力计算等属于推理/分析，并非训练新模型，算力需求相对有限。

## 5. 实验数量与充分性

- **实验轮次/数量**：
  - 主要因果中介分析：代数任务（200个prompt，两个规则版本），字母类比（100个prompt each），言语类比（100个prompt each）。
  - 注意力模式分析：ABA和ABB各1378个prompt。
  - RSA：40组token集，对每个头部类型的关键组件（query/key/value/output）均做分析。
  - 消融实验：40个prompt，逐步消融，对比控制组和随机基线（10次随机种子）。
  - 解码分析：训练集200、验证集100、测试集200（token完全不重叠）。
  - 跨任务相关性分析。
- **充分性**：
  - 多种任务（简单规则→复杂类比）覆盖不同抽象水平。
  - 多个模型家族和规模，验证普适性。
  - 多种分析方法（因果、注意力、表征、消融、解码）互相印证。
  - 统计严格：置换检验控制家族错误率（\(p<0.05\)）。
- **客观性**：实验设计包括正反两种因果方向（双向补丁），控制条件（token vs 抽象），以及随机/控制基线，方法客观。但仅使用代码实现，未涉及人类实验。

## 6. 论文的主要结论与发现

1. **涌现符号架构的存在**：在Gemma-2、Qwen2.5、Llama-3.1（不包括GPT-2）中，稳定识别出三个阶段的因果相关头部：早期符号抽象头 → 中间符号归纳头 → 后期检索头。
2. **符号抽象头的功能**：将输入token转换为与具体token无关的抽象变量表示，基于关系（如相同/不同）。RSA确认其输出更像抽象变量而非token。
3. **符号归纳头的功能**：在抽象变量序列上进行归纳，预测下一个变量。注意力模式显示它们关注以前实例中同一变量出现的位置。它们与标准归纳头几乎不重叠（r=0.11），但与函数向量高度相关（r=0.86）。
4. **检索头的功能**：根据预测的抽象变量，检索对应的具体token。注意力模式显示它们关注同一例子中对应位置的值。
5. **性能与机制的关联**：表现好的模型（如Llama-3.1 70B）均具有显著的三阶段头部；表现差的GPT-2系列缺乏符号抽象头，尤其对ABB规则没有有效头部。
6. **更复杂任务的可推广性**：字母字符串类比和言语类比中也观察到同样的三阶段架构，说明该机制具有通用性。
7. **函数向量的本质**：符号归纳头实质上是函数向量的载体，同时符号抽象头也参与函数向量计算（在前两个例子中）。
8. **错误分析**：错误试次中，符号抽象头和符号归纳头的抽象变量表征较弱（RSA相关系数更低），进一步验证了这些机制的重要性。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次系统揭示支撑LLM抽象推理的完整神经符号架构，并给出具体头部定位和功能说明。
- **因果分析严谨**：设计了双重因果条件（抽象变量 vs. 具体token的分离），并使用置换检验控制多重比较。
- **多维度验证**：结合因果、行为（注意力）、表征（RSA）、必要性（消融）和泛化性（解码）多种手段，证据链完整。
- **跨任务、跨模型泛化**：在三个不同任务、四个模型家族、13个不同规模的模型上验证，结论具有普适性。
- **与已有理论的整合**：明确将符号归纳头与函数向量、归纳头联系，统一了相关文献发现。
- **可解释性强**：注意力模式可视化清晰展示了每一步的机制，便于理解。

## 8. 不足与局限

### 实验覆盖
- **任务复杂性有限**：主要使用相对简单的规则归纳（ABA/ABB）、字母/言语类比。复杂数学推理、规划等任务未测试，符号机制是否完全适用未知。
- **GPT-2的例外**：GPT-2系列未发现符号抽象头，且性能较差，说明该机制可能与模型规模/训练数据有关，但文中未深入解释为何GPT-2无法涌现。
- **只有一个模型家族（Llama-3.1 70B）做了完整机制分析**，其他模型仅给出头部数量统计，未做注意力/RSA等详细验证，可能遗漏某些模型的变体机制。

### 偏差风险
- **符号机制的“纯度”**：RSA显示头部输出同时含有抽象变量和token信息，并非完全符号化。虽然解码分析存在不变性子空间，但机制可能只是近似符号。
- **因果中介分析的局限性**：仅交换了最终例子中的token或变量，未测试更复杂的反事实（如同时改变多个变量），可能遗漏交互作用。
- **消融实验中控制组的选取**：用同一层最低分头部替换，但最低分头部也可能参与其他功能，控制组可能不够纯净。

### 应用限制
- 该分析依赖大量计算资源（因果分析需遍历所有头部），对超大模型（如>100B）可能难以扩展。
- 机制仅针对特定类型的抽象关系（同/不同、后继/前驱、同义/反义）。对于需要组合推理或多步思维链的任务，可能还需其他机制补充。
- 未与人类脑机制建立直接联系，结论对认知科学的启示尚属间接。

（完）
