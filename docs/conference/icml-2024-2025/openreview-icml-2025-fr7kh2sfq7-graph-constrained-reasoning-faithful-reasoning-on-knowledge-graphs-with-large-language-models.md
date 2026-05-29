---
title: "Graph-constrained Reasoning: Faithful Reasoning on Knowledge Graphs with Large Language Models"
title_zh: 图约束推理：基于知识图谱的忠实大语言模型推理
authors: "Linhao Luo, Zicheng Zhao, Gholamreza Haffari, Yuan-Fang Li, Chen Gong, Shirui Pan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Fr7kH2SFq7"
tags: ["query:ns-xai"]
score: 9.0
evidence: 图约束推理将知识图谱结构与LLM结合实现忠实推理
tldr: 针对大语言模型在推理中存在的知识缺失和幻觉问题，本文提出图约束推理（GCR），将知识图谱的结构化知识与LLM的非结构化推理相结合。GCR通过将图结构融入生成过程，确保推理结果忠实于知识图谱，从而消除幻觉。实验证明该方法在多个知识密集型推理任务上优于现有方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 355, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1498, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 573, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 698, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 684, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1617, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1752, \"height\": 174, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1716, \"height\": 727, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1086, \"height\": 964, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1083, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 787, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1464, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1461, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1082, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 683, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1779, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 748, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1320, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 477, \"height\": 141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 775, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 737, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1778, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 998, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1609, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1610, \"height\": 309, \"label\": \"Table\"}]"
motivation: 现有KG增强方法在知识检索和图遍历上存在困难，LLM推理易产生幻觉。
method: 提出图约束推理（GCR），将知识图谱结构融入LLM生成过程。
result: 在多个知识密集型推理任务上，GCR实现了更忠实且无幻觉的推理。
conclusion: 为融合结构化知识和LLM推理提供了有效范本。
---

## Abstract
Large language models (LLMs) have demonstrated impressive reasoning abilities, but they still struggle with faithful reasoning due to knowledge gaps and hallucinations. To address these issues, knowledge graphs (KGs) have been utilized to enhance LLM reasoning through their structured knowledge. However, existing KG-enhanced methods, either retrieval-based or agent-based, encounter difficulties in accurately retrieving knowledge and efficiently traversing KGs at scale. In this work, we introduce graph-constrained reasoning (GCR), a novel framework that bridges structured knowledge in KGs with unstructured reasoning in LLMs. To eliminate hallucinations, GCR ensures faithful KG-grounded reasoning by integrating KG structure into the LLM decoding process through KG-Trie, a trie-based index that encodes KG reasoning paths. KG-Trie constrains the decoding process, allowing LLMs to directly reason on graphs and generate faithful reasoning paths grounded in KGs. Additionally, GCR leverages a lightweight KG-specialized LLM for graph-constrained reasoning alongside a powerful general LLM for inductive reasoning over multiple reasoning paths, resulting in accurate reasoning with zero reasoning hallucination. Extensive experiments on several KGQA benchmarks demonstrate that GCR achieves state-of-the-art performance and exhibits strong zero-shot generalizability to unseen KGs without additional training.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLM）在推理任务中表现出色，但存在知识缺失和幻觉（hallucination）问题，导致推理过程不可靠。知识图谱（KG）以结构化形式存储大量事实知识，常被用于增强LLM的推理能力。然而，现有的KG增强方法分为两类：（1）检索式方法依赖外部检索器，可能无法准确检索到与图结构相关的知识；（2）智能体式方法需要多次与KG交互，计算成本高、延迟大。更重要的是，现有方法仍然存在严重的幻觉问题（例如，RoG有约33%的推理错误）。因此，亟需一种能够将KG结构化知识与LLM非结构化推理无缝结合、消除幻觉、确保忠实推理的新框架。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：提出图约束推理（Graph-Constrained Reasoning, GCR），将KG结构直接融入LLM的解码过程，使LLM能够生成完全基于KG的推理路径，从而消除幻觉。GCR包含三个主要组件：

- **KG-Trie构建**：将KG中的推理路径（从问题实体出发，通过广度优先搜索BFS获取最多L跳的路径）转换为字符串格式，再用分词器（tokenizer）分词后构建前缀树（Trie）索引。KG-Trie作为结构索引，可在常量时间内限制LLM解码时只能生成有效路径前缀。
- **图约束解码**：使用轻量级KG专用LLM（fine-tuned），在解码过程中引入KG-Trie约束：只有满足KG-Trie中某个前缀的token才被允许生成。这样LLM生成的推理路径必然存在于KG中，从而保证零幻觉。公式上，LLM生成路径的概率为P(wz|q) = Π P(wzi|...) * C(wzi|...)，其中C为约束函数，若当前前缀存在于KG-Trie中则返回1，否则0。在生成有效路径后，LLM再生成假设答案。
- **图归纳推理**：使用通用大语言模型（如ChatGPT、GPT-4o-mini）对KG专用LLM生成的多个推理路径和假设答案进行归纳推理，得出最终答案。采用FiD框架在单次LLM调用中融合多个路径。

关键公式：式(6)给出了图约束解码的概率建模；式(8)是fine-tuning的损失函数（最大化生成正确路径和答案的对数似然）。

## 3. 实验设计：数据集、benchmark、对比方法

**数据集**：
- 主要评测：WebQuestionSP (WebQSP) 和 Complex WebQuestions (CWQ)，使用Freebase作为KG。
- 零样本泛化：FreebaseQA、CommonsenseQA (CSQA，使用ConceptNet作为KG)、MedQA（使用医学KG）。

**对比方法**（共22个基线）：
- LLM推理方法：Qwen2-0.5B/1.5B/7B、Llama-2-7B、Llama-3.1-8B、ChatGPT、GPT-4o-mini、Few-shot、CoT、Self-consistency。
- 图推理方法：GraftNet、NSM、SR+NSM、ReaRev、UniKGQA。
- KG+LLM方法：KD-CoT、EWEK-QA、ToG、EffiQA、RoG、GNN-RAG、GNN-RAG+RA。

**评估指标**：WebQSP和CWQ采用Hit和F1；CSQA和MedQA采用Accuracy。

## 4. 资源与算力

论文附录E明确给出了算力信息：
- 微调（fine-tuning）KG专用LLM时，使用2张A100-80G GPU，每模型训练3个epoch，batch size=4，学习率2e-5，cosine scheduler，warmup ratio 0.03。
- 不同模型的训练时长和显存占用见附录表14：Qwen2-0.5B用时3.47h，显存10G；Llama-3.1-8B用时14.52h，显存85G。
- 测试时的效率分析也基于单张A100-80G GPU。

## 5. 实验数量与充分性

论文进行了大量实验，包括：
- **主实验结果**（表1）：在WebQSP和CWQ两个数据集上与22个基线对比，均达到SOTA。
- **消融实验**（表3）：分析去除KG专用LLM或通用LLM的影响。
- **不同LLM组合分析**（表4）：比较不同规模的KG专用LLM和不同通用LLM的性能。
- **参数分析**（图4、图7）：分析beam size K和路径跳数L的影响。
- **效率分析**（表2）：与检索式和智能体式方法比较运行时间、LLM调用次数、输入tokens等。
- **忠实性分析**（图5）：比较有/无KG约束时的推理忠实率和答案命中率，证明零幻觉。
- **零样本泛化实验**（表6）：在三个新数据集上测试，证明无需额外训练即可迁移到新KG。
- **案例研究**（表5）：展示具体推理路径对比。

实验设计较为全面，覆盖了性能、效率、忠实性、泛化性、参数敏感性和消融，对比基线也较为广泛（22个），整体充分、客观、公平。

## 6. 主要结论与发现

- GCR在WebQSP和CWQ上均取得SOTA性能（WebQSP Hit 92.6%，CWQ Hit 75.8%），显著优于现有KG+LLM方法。
- 通过KG约束，GCR实现了100%的推理忠实率（即所有生成的推理路径均存在于KG中），而移除约束后忠实率大幅下降（WebQSP上62.4%，CWQ上48.1%），证明KG约束有效消除幻觉。
- GCR具有零样本泛化能力：在FreebaseQA、CSQA、MedQA上，直接使用Freebase上训练好的KG专用LLM和对应KG的Trie即可取得优于纯LLM的结果。
- 轻量级KG专用LLM（0.5B）经微调后可超越更大的通用LLM（70B），说明微调的重要性；结合强大的通用LLM能进一步提升性能。
- 效率上，GCR运行时间与检索式方法相当（3.60s），但远快于智能体式方法（ToG 16.14s）；LLM调用次数和输入tokens也较少。

## 7. 优点

- **创新性**：首次将KG结构以前缀树形式融入LLM解码过程，既保证推理忠实性，又实现高效并行探索多条路径。
- **零幻觉**：通过硬约束确保推理路径完全基于KG，从根源上消除幻觉，并提供可验证的忠实性。
- **高效灵活**：KG-Trie可预构建或按需构建，支持批处理（beam search）生成多条路径；结合轻量级专用LLM和通用LLM，兼顾性能和泛化能力。
- **零样本泛化**：在未见过的KG上无需重新训练即可直接应用，展示出良好的迁移能力。
- **实验充分**：对比基线丰富，消融与分析透彻，覆盖性能、效率、忠实性、参数影响等多个维度。

## 8. 不足与局限

- **零幻觉定义范围有限**：论文将零幻觉定义为推理路径完全存在于KG中。但KG本身可能不完整或包含错误事实，因此仍存在“忠实但错误”的潜在风险。检测此类幻觉需跨多个知识源验证，论文未深入探讨。
- **复杂问题的效率挑战**：对于高复杂度的多跳问题，可能需要更大的L（跳数）来构建KG-Trie，导致时间和空间成本显著增加。论文虽提出可结合规划方法分解问题，但未在实验中验证。
- **无关推理路径**：尽管LLM生成路径受KG约束，但路径仍可能与问题无关（如附录F.5案例），导致错误答案。这源于KG不完全或LLM理解偏差，论文指出需进一步提升LLM的路径选择能力。
- **通用LLM的依赖**：最终归纳推理依赖于强大通用LLM（如ChatGPT、GPT-4o-mini），这些模型可能无法免费或本地部署，增加了实际应用成本。
- **实验数据集的局限性**：主要使用英文开源KGQA数据集（Freebase、ConceptNet），未在更大规模工业级KG或中文KG上验证；医学KG规模较小，泛化性能提升有限。

（完）
