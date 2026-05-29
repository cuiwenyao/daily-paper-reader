---
title: Agent Instructs Large Language Models to be General Zero-Shot Reasoners
title_zh: 智能体指导大语言模型成为通用零样本推理器
authors: "Nicholas Crispino, Kyle Montgomery, Fankun Zeng, Dawn Song, Chenguang Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=zMwFvxr6CV"
tags: ["query:ns-xai"]
score: 8.0
evidence: 通过自主智能体生成指令提升大语言模型的零样本推理能力
tldr: 针对大语言模型零样本推理能力有限的问题，提出一个自主智能体为每个任务生成单条指令，显著提升多个模型在生成、分类和推理任务上的零样本性能。该方法通用性强，有效释放了大语言模型的推理潜力。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1765, \"height\": 1262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 900, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1593, \"height\": 1161, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 840, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 826, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 807, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 804, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 837, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 790, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1666, \"height\": 298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1718, \"height\": 1811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1706, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 872, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1717, \"height\": 1172, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1714, \"height\": 1173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1708, \"height\": 1149, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1711, \"height\": 1001, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1686, \"height\": 1346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1705, \"height\": 1228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1702, \"height\": 1250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1705, \"height\": 1401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1693, \"height\": 1021, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1712, \"height\": 1231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1707, \"height\": 961, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1708, \"height\": 1335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1725, \"height\": 937, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1716, \"height\": 1028, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1696, \"height\": 1370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1701, \"height\": 1462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1688, \"height\": 1372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1721, \"height\": 1211, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1722, \"height\": 1195, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 1707, \"height\": 1437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 1697, \"height\": 1204, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1709, \"height\": 1475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1692, \"height\": 800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 1703, \"height\": 1695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 1697, \"height\": 1045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 1712, \"height\": 1195, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 1701, \"height\": 1406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 1694, \"height\": 1701, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 1700, \"height\": 1155, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 1759, \"height\": 1467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-046.webp\", \"caption\": \"\", \"page\": 0, \"index\": 46, \"width\": 1702, \"height\": 1169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-047.webp\", \"caption\": \"\", \"page\": 0, \"index\": 47, \"width\": 1710, \"height\": 1025, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-048.webp\", \"caption\": \"\", \"page\": 0, \"index\": 48, \"width\": 1701, \"height\": 1166, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-049.webp\", \"caption\": \"\", \"page\": 0, \"index\": 49, \"width\": 1705, \"height\": 1155, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-050.webp\", \"caption\": \"\", \"page\": 0, \"index\": 50, \"width\": 1702, \"height\": 1734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-051.webp\", \"caption\": \"\", \"page\": 0, \"index\": 51, \"width\": 1685, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-052.webp\", \"caption\": \"\", \"page\": 0, \"index\": 52, \"width\": 1707, \"height\": 1038, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-053.webp\", \"caption\": \"\", \"page\": 0, \"index\": 53, \"width\": 1704, \"height\": 1538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-054.webp\", \"caption\": \"\", \"page\": 0, \"index\": 54, \"width\": 1715, \"height\": 1928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-055.webp\", \"caption\": \"\", \"page\": 0, \"index\": 55, \"width\": 1727, \"height\": 1154, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmwfvxr6cv/fig-056.webp\", \"caption\": \"\", \"page\": 0, \"index\": 56, \"width\": 1711, \"height\": 1243, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 709, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1720, \"height\": 2319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1787, \"height\": 1829, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1777, \"height\": 2385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1778, \"height\": 2366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1772, \"height\": 2355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1781, \"height\": 769, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1773, \"height\": 1563, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1012, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 925, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 859, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1778, \"height\": 996, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1779, \"height\": 2203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1774, \"height\": 2362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 814, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmwfvxr6cv/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1449, \"height\": 134, \"label\": \"Table\"}]"
motivation: 大语言模型的零样本推理能力有待提升。
method: 构建一个自主智能体为每个任务生成一组指令以引导推理过程。
result: 在多种任务上显著提高了不同大语言模型的零样本推理能力。
conclusion: 该智能体方法有效增强了大语言模型的通用零样本推理能力。
---

## Abstract
We introduce a method to improve the zero-shot reasoning abilities of large language models on general language understanding tasks. Specifically, we build an autonomous agent to instruct the reasoning process of large language models. To enable this, our agent only needs to generate a single set of instructions for each task. These instructions turn out to be extremely effective for improving the reasoning process of different large language models across all task instances. We show this approach further unleashes the zero-shot reasoning abilities of large language models to more tasks. We study the performance of our method on a wide set of datasets spanning generation, classification, and reasoning. We show that our method generalizes to most tasks and obtains state-of-the-art zero-shot performance on 20 of the 29 datasets that we evaluate. For instance, our method boosts the performance of state-of-the-art large language models by a large margin, including Vicuna-13b, Llama-2-70b-chat, and GPT-3.5 Turbo. Compared to zero-shot chain of thought, our improvement in reasoning is striking. With our method, Llama-2-70b-chat outperforms zero-shot GPT-3.5 Turbo significantly.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型在复杂推理任务上展现了零样本推理能力，但在通用语言理解任务（如生成、分类）上的零样本推理能力仍然有限。传统的零样本思维链方法使用固定的“Let‘s think step by step”提示，缺乏任务特异性，导致在多样化任务上表现不佳。
- **整体含义**：作者提出通过构建一个自主智能体（Agent）为每个任务生成一组任务特定的指令，将这些指令注入零样本思维链推理过程，从而提升大语言模型在广泛任务上的零样本推理能力。该方法类似于知识蒸馏（教师-学生范式），其中智能体（教师）生成指令，较小的语言模型（学生）遵循指令进行推理。

## 2. 方法论

### 核心思想
- 解耦指令生成与推理过程：智能体仅需为每个任务运行一次，生成一组任务特定的指令；这些指令随后被用于所有任务实例和所有推理模型。
- 智能体基于ReAct框架（Yao et al., 2023b），使用GPT-4作为默认智能体，具备两种动作：（a）通过搜索网页获取任务相关信息（利用Bing搜索和向量数据库）；（b）输出最终指令。
- 推理阶段：将智能体生成的指令作为前缀，附加到每个测试实例前，引导语言模型进行逐步推理，最后通过答案提取提示获得最终输出。

### 关键技术细节
1. **指令生成流程**：
   - 输入：任务名称、少量无标签的输入示例、可能的输出标签（分类任务）或任务类型（生成任务）。
   - 智能体通过Thought-Action-Observation循环，查询网络知识，逐步构建步骤式指令。
   - 最终输出一组清晰、任务特定的指令（例如对IMDB情感分类，指令包括“分析语言、语气，确定正面或负面”）。
2. **推理提示**：
   - 推理提取提示：将指令与测试实例拼接，要求模型“根据指令生成解释，并以正确答案结尾”。
   - 答案提取提示：针对生成、分类（非多选）、分类（多选）分别设计不同的答案提取格式。
3. **特异性与通用性**：同一组指令可跨不同语言模型（Vicuna, Llama-2, GPT-3.5 Turbo）和所有实例使用。

## 3. 实验设计

### 使用的数据集与场景
- 数据集：29个数据集（53个子集），涵盖HELM核心场景（如BoolQ, CivilComments, CNN/Daily Mail, IMDB, NarrativeQA, NaturalQuestions, NewsQA等）以及Kojima et al. (2022)的推理数据集（如AddSub, AQuA, GSM8K, Coin Flip, Last Letter Concatenation, MultiArith, SVAMP等）。
- 任务类型：生成、分类、推理（部分数据集同时属于多个类别）。

### Benchmark与对比方法
- 对比标准零样本（Zero-Shot）和零样本思维链（Zero-Shot CoT）。
- 额外对比：ReAct（直接在GPT-4上运行）、少样本（Few-Shot）、自一致性（Self-Consistency）。
- 消融实验：去除指令、去除输入示例、去除标签描述、使用GPT-3.5 Turbo替代GPT-4生成指令；比较直接提供原始任务信息与合成指令的效果。
- 模型：Vicuna-13b, Llama-2-7b-chat, Llama-2-13b-chat, Llama-2-70b-chat, GPT-3.5 Turbo。
- 评估指标：根据任务选择EM、QEM、QPEM、F1、ROUGE-2、RR@10、NDCG@10。

## 4. 资源与算力

- **硬件**：使用2个节点，每个节点配备8×NVIDIA RTX A6000 GPU，用于运行Vicuna和Llama-2-chat模型。Llama-2-70b-chat使用NF4量化以适配单GPU，NaturalQuestions（open-book）等长序列任务使用2个GPU/worker。
- **算力消耗**：论文未明确给出总训练时长或具体GPU小时数（因为使用的是预训练模型，仅进行推理）。指令生成阶段：每个数据集平均约7000个token（GPT-4），成本低于1美元。推理阶段：每个模型对所有数据集运行一次。
- **不足**：未详细报告总推理成本或运行时间，但强调AgentInstruct相比直接使用ReAct（每实例运行）成本低约100倍。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要结果：在29个数据集（53个子集）上比较零样本、零样本CoT和AgentInstruct，覆盖5个模型。
  - 消融实验：4组（去除指令、去除示例、去除标签、换智能体模型）在3个代表性数据集（AddSub, IMDB, NarrativeQA）上进行。
  - 敏感性分析：对推理提取提示和答案提取提示的多种变体测试（表3），以及指令位置格式测试（附录D.3）。
  - 模型规模：在Llama-2-7b/13b/70b上对比三种方法。
  - 错误分析：手动分析75个错误样本（每个数据集25个），分类错误类型。
  - 对比少样本和自一致性：在3个数据集上比较。
  - 上下文长度压缩测试：在3个数据集上测试不同最大长度。
- **充分性与公平性**：
  - 实验覆盖全面，包含多种任务类型和模型大小，消融和敏感性分析充分。
  - 使用HELM标准实现和默认参数，确保基准公平。
  - 注意：所有实验为单次运行（一次指令生成+一次推理），可能存在随机性，但论文提及使用温度0.0（除摘要任务）以增强确定性；提示敏感性分析表明性能稳定。
  - 客观性：误差类型分析详细，未回避失败案例；对比方法包括强基线（ReAct, 少样本, 自一致性）。

## 6. 主要结论与发现

1. **性能提升显著**：AgentInstruct在所有三个主模型（Vicuna-13b, Llama-2-70b-chat, GPT-3.5 Turbo）上平均提升17.8%（vs.零样本）和6.5%（vs.零样本CoT）。在推理任务上提升尤为突出（+10.5%）。
2. **达到SOTA**：在29个数据集中，20个数据集的最佳零样本性能由AgentInstruct取得。
3. **跨模型迁移性**：同一组指令可有效指导不同模型，且Llama-2-70b-chat+AgentInstruct超越零样本GPT-3.5 Turbo（平均+10.2%）。
4. **指令合成比原始信息更重要**：直接将相同数据集信息拼接到零样本CoT中效果不佳，而合成后的指令显著提升性能。
5. **成本效益**：AgentInstruct（GPT-4生成指令+GPT-3.5 Turbo推理）在AddSub上达到与GPT-4零样本CoT相当的性能，但成本更低；相比ReAct（每实例运行），成本降低约100倍。
6. **局限性识别**：错误主要来自推理错误（32%）、答案歧义（22.7%）、无效标签（14.7%）等；摘要任务表现未提升。

## 7. 优点

- **方法简洁高效**：仅需一次指令生成即可服务于整个任务和多种模型，避免了每实例运行智能体的高昂成本。
- **通用性强**：适用于生成、分类和推理等多种任务，且在不同模型间可迁移。
- **可解释性**：生成的任务特定指令以自然语言步骤呈现，便于人类理解和审计推理过程。
- **知识蒸馏有效**：利用强大模型（GPT-4）生成指令，蒸馏给较弱模型，提升其推理能力。
- **实验设计规范**：使用HELM标准框架，覆盖全面，消融和敏感性分析细致，错误分析深入。

## 8. 不足与局限

- **智能体知识覆盖不完整**：部分数据集（如AddSub, AQuA, Coin Flip等）的Web搜索未返回有用信息，此时指令可能仅依赖模型自身知识（表14）。
- **单次运行偏差**：每项实验仅运行一次，未报告多次重复的统计结果（如置信区间），可能受随机性影响。
- **上下文长度限制**：长输入任务（如NarrativeQA）在截断上下文后性能急剧下降（图18），提示方法对上下文长度敏感。
- **摘要任务效果不佳**：AgentInstruct在CNN/Daily Mail和XSUM上未超越零样本，甚至下降，可能与答案提取提示导致摘要重写有关。
- **依赖GPT-4**：使用较弱模型（GPT-3.5 Turbo）作为智能体无法生成连贯指令（需改用单轮提示），限制了方法的普及性。
- **语言与领域限制**：仅评估英文数据集，未测试多语言或低资源场景；智能体指令可能隐含来自网络的偏见。
- **非事实性风险**：尽管提升了安全基准（TruthfulQA, CivilComments），但仍存在非事实性输出，且错误分析中12%为“不事实”。

（完）
