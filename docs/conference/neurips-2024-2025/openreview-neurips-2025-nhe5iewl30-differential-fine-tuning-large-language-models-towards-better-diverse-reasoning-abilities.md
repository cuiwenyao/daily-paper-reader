---
title: Differential Fine-Tuning Large Language Models Towards Better Diverse Reasoning Abilities
title_zh: 面向多样化推理能力的大语言模型区分性微调
authors: "Xiaosong Yuan, Chen Shen, Shaotian Yan, kaiyuan liu, Xiaofeng Zhang, Sinan Fan, Qingyi Meng, Liang Xie, Wenxiao Wang, Renchu Guan, Ying Wang, Jieping Ye"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=NhE5IeWl30"
tags: ["query:ns-xai"]
score: 7.0
evidence: 微调LLM以提升多样化推理能力
tldr: 监督微调可增强LLM的多种推理能力，但多任务联合训练会产生冲突。本文提出区分性微调框架，通过分析任务差异缓解冲突，实现比单任务SFT更优的推理性能，为提升LLM多面推理能力提供新方法。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1405, \"height\": 420}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1416, \"height\": 872}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 323}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1418, \"height\": 1171}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1419, \"height\": 1165}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 1156}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1421, \"height\": 1178}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 641, \"height\": 300}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 589}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 785}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 701, \"height\": 210}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1128, \"height\": 920}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 472}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 599, \"height\": 193}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 926, \"height\": 380}]"
motivation: 监督微调多任务联合训练引入冲突，损害推理能力。
method: 提出区分性微调框架，分析任务差异并缓解冲突。
result: 在多个推理任务上超越单任务SFT性能。
conclusion: 区分性微调有效提升LLM多样化推理能力。
---

## Abstract
Reasoning abilities of large language models (LLMs) require explicit derivations compared to general question-answering, supervised fine-tuning (SFT) can empower multiple reasoning abilities in LLMs via learning from various datasets. However, neither training the datasets jointly (mix-up) nor continually can maintain the performance of single-dataset SFT, sometimes better while sometimes even worse, illustrating vanilla SFT can not only facilitate reasoning abilities but also introduce conflicts. In this paper, we propose a novel framework to mitigate the conflicts and preserve benefits among different reasoning tasks, and even surpass each task's single dataset SFT performance. We start by exploring the differences between reasoning fine-tuned and base LLMs by analyzing their parameter variations during model inference, and we discover that each reasoning capability has exclusive parameters that benefit itself more evidently than others. In contrast, the overlapped parameters of tasks can bring benefits or conflicts. Inspired by the findings, we propose to update the exclusive and overlapped parameters according to specific reasoning task combinations differentially, thereby avoiding unnecessary conflicts while maintaining benefits. Consistent improvements in mix-up and continual SFT experiments demonstrate that the proposed SFT strategy can achieve better performance on various LLMs (Llama3-8B, Mistral-7B, and Qwen2.5-14B) and diverse reasoning tasks with fewer conflicts, showing the superiority and generality of our analysis findings and the proposed approach.

---

## 论文详细总结（自动生成）

## 论文总结：面向多样化推理能力的大语言模型区分性微调

### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大语言模型通过监督微调（SFT）可以增强多种推理能力（如数学、代码、逻辑、常识），但混合多个数据集（mix-up）或顺序训练（continual）时，会出现性能互损或冲突，即单任务SFT表现更好，多任务联合时有时更好、有时更差。
- **核心问题**：如何缓解不同推理任务之间的冲突，同时保留任务间的相互增益，实现比单任务SFT更优的多面推理能力。
- **背景**：先前工作关注通用能力的冲突，且认为所有冲突都是有害的，但本文发现推理能力间存在有益的共享参数和有害的冲突参数。

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：每个推理能力都有专属的“delta-scale行”（参数敏感区域），不同任务的重叠参数可能带来增益或冲突。通过区分性地更新这些参数，可以避免冲突并保留增益。
- **关键技术细节**：
  - **delta-scale行分析**：对于每个线性层，计算微调模型与基座模型在同一输入下的输出差值的平方均值（式3），得到每个输出维度（对应权重矩阵的行）的敏感度分数。分数高的行即为该任务的关键参数。
  - **混合微调（Mix-up SFT）**：取所有任务关键参数集合的并集（式4），只更新这些参数，冻结其他参数。
  - **连续微调（Continual SFT）**：对于当前任务，取其关键参数与先前任务关键参数并集的差集（式5），只更新这些差异参数，冻结其他参数。
- **算法流程**（文字说明）：
  1. 对每个推理任务，用其训练数据分别在基座模型和对应的微调模型上进行前向，计算每个线性层的delta-scale行分数。
  2. 取每层分数最高的C行（本文默认100行）作为该任务的关键参数索引。
  3. 混合场景：冻结不在所有任务关键参数并集中的参数，用混合数据训练。
  4. 连续场景：冻结当前任务关键参数与历史任务关键参数并集之外的参数，用当前任务数据训练。

### 3. 实验设计
- **数据集**：数学（MathInstruct等）、代码（Code Bagel Hermes等）、逻辑（LogiCoT）、常识（CommonsenseQA等）。每个任务采样20,000条训练数据。
- **基准与评估指标**：
  - 数学：GSM8k（0-shot accuracy）
  - 代码：xGLUE（pass rate）
  - 逻辑：LogiQA2（0-shot accuracy）
  - 常识：CSQA（0-shot accuracy）
  - 多任务性能指标：平均目标准确率（ATA）
- **对比方法**：vanilla SFT（单任务、混合、连续）、DMT（双阶段混合微调）、CoBa（收敛均衡器）、HFT（半冻结连续微调）、LoTA（彩票票适配）、逆DiFT（反冻结实验）
- **实验场景**：混合微调（两两任务组合）、连续微调（两两任务顺序）、多任务混合（三任务、四任务）、不同连续顺序。

### 4. 资源与算力
- **资源说明**：
  - delta-scale行分析：1张NVIDIA A100 GPU，7B/8B模型约30GB显存、900秒；14B模型约62GB、1200秒。
  - 微调训练：8张A100服务器（可同时进行全部实验）。
- 文中未明确说明单次训练时长，但提到使用DeepSpeed Zero2、固定batch size和max length，利用GPU高效训练。

### 5. 实验数量与充分性
- **实验数量**：包含3种基座模型（Llama3-8B、Mistral-7B、Qwen2.5-14B），多种任务组合（两两、三任务、四任务），混合和连续两种设置，以及多种对比基线（vanilla SFT, DMT, CoBa, HFT, LoTA, 逆DiFT），共计几十组实验。
- **充分性与客观性**：
  - 实验覆盖了不同架构、不同规模模型，验证了通用性。
  - 所有超参数统一（学习率2e-5, batch size 256等），使用相同随机种子，保证公平。
  - 消融实验（不同数量delta-scale行、逆DiFT）验证了方法的必要性。
  - 局限性：在7B/8B和14B上验证，未在30B+模型上测试；连续学习场景中无法完全解决灾难性遗忘。

### 6. 主要结论与发现
- **主要结论**：提出的DiFT策略在混合和连续微调中均能提升多推理任务的平均性能（ATA），优于vanilla SFT和多个基线方法。
- **核心发现**：
  - 不同推理任务存在专属的关键参数（delta-scale行），这些行对任务贡献大，且对不同输入稳定。
  - 任务间重叠参数可能导致冲突或增益，数学与代码共享较多增益，逻辑与常识冲突较大。
  - 混合微调中，DiFT能同时提升或保持各任务性能；连续微调中，DiFT能缓解性能下降，保留更多历史知识。
  - 逆DiFT实验证明关键参数不可替代，验证了分析的正确性。

### 7. 优点
- **方法创新**：首次从参数敏感度角度区分任务专属和共享参数，提出细粒度的参数级选择性微调策略。
- **实验全面**：覆盖多种模型、任务、场景，并与多个SOTA基线对比，消融实验充分。
- **通用性**：方法适用于base模型和instruct模型，且在不同规模（7B~14B）上一致有效。
- **计算开销可控**：delta-scale行分析只需少量样本和短时间，微调阶段仅冻结部分参数，不影响整体训练效率。

### 8. 不足与局限
- **理论支撑不足**：论文未提供delta-scale行有效性的理论证明，依赖实验验证。
- **模型规模局限**：仅测试7B/8B和14B模型，未在30B+大模型上验证，可能影响结论的可推广性。
- **连续学习问题**：DiFT能缓解冲突但无法解决灾难性遗忘（catastrophic forgetting），在连续微调场景中性能仍显著低于单任务SFT。
- **计算成本**：微调阶段仍为全参数训练，与PEFT方法（如LoRA）相比，时间与内存成本更高（但性能更优）。
- **评估指标单一**：主要使用0-shot准确率和pass rate，未深入分析推理过程质量或泛化能力。

（完）
