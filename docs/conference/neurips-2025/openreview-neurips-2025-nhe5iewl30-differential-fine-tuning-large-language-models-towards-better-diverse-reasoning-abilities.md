---
title: Differential Fine-Tuning Large Language Models Towards Better Diverse Reasoning Abilities
title_zh: 差分微调大语言模型以提升多样化推理能力
authors: "Xiaosong Yuan, Chen Shen, Shaotian Yan, kaiyuan liu, Xiaofeng Zhang, Sinan Fan, Qingyi Meng, Liang Xie, Wenxiao Wang, Renchu Guan, Ying Wang, Jieping Ye"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=NhE5IeWl30"
tags: ["query:ns-xai"]
score: 6.0
evidence: 微调LLM以提升多样化推理能力
tldr: 监督微调（SFT）可以增强LLM的多种推理能力，但混合或连续训练常导致性能冲突。本文提出差分微调框架，通过识别不同推理任务间的差异并分别优化，既保留各任务优势又避免冲突，在多个推理基准上超过单任务SFT效果，为LLM多任务推理训练提供新思路。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1405, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1416, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1418, \"height\": 1171, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1419, \"height\": 1165, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 1156, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1421, \"height\": 1178, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhe5iewl30/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 641, \"height\": 300, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 589, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 785, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 701, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1128, \"height\": 920, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 599, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhe5iewl30/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 926, \"height\": 380, \"label\": \"Table\"}]"
motivation: 现有SFT在多推理任务联合训练时出现性能冲突，难以同时保持各任务的最佳性能。
method: 提出差分微调框架，先分析推理任务差异，再分别优化以减少冲突并保留优势。
result: 在多个推理数据集上，差分微调模型性能超过单任务SFT和混合训练，且不引入冲突。
conclusion: 有效解决了多任务推理微调中的冲突问题，提升了LLM的多样化推理能力。
---

## Abstract
Reasoning abilities of large language models (LLMs) require explicit derivations compared to general question-answering, supervised fine-tuning (SFT) can empower multiple reasoning abilities in LLMs via learning from various datasets. However, neither training the datasets jointly (mix-up) nor continually can maintain the performance of single-dataset SFT, sometimes better while sometimes even worse, illustrating vanilla SFT can not only facilitate reasoning abilities but also introduce conflicts. In this paper, we propose a novel framework to mitigate the conflicts and preserve benefits among different reasoning tasks, and even surpass each task's single dataset SFT performance. We start by exploring the differences between reasoning fine-tuned and base LLMs by analyzing their parameter variations during model inference, and we discover that each reasoning capability has exclusive parameters that benefit itself more evidently than others. In contrast, the overlapped parameters of tasks can bring benefits or conflicts. Inspired by the findings, we propose to update the exclusive and overlapped parameters according to specific reasoning task combinations differentially, thereby avoiding unnecessary conflicts while maintaining benefits. Consistent improvements in mix-up and continual SFT experiments demonstrate that the proposed SFT strategy can achieve better performance on various LLMs (Llama3-8B, Mistral-7B, and Qwen2.5-14B) and diverse reasoning tasks with fewer conflicts, showing the superiority and generality of our analysis findings and the proposed approach.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLM）的推理能力（如数学、代码、逻辑、常识推理）通常需要通过监督微调（SFT）从不同数据集中习得。然而，当将多个推理数据集进行混合（mix-up）或连续（continual）微调时，模型性能往往无法同时保持各个单任务的最佳表现，甚至出现显著下降，表明推理任务间既存在相互增益，也存在冲突。现有方法（如HFT、LoTA、CoBa等）虽试图缓解冲突，但忽略了任务间关系的全貌（有益、有害、中性）。本文旨在深入分析推理微调中参数变化的内在规律，并提出一种差分微调框架（DiFT），以保留任务间益处、缓解冲突，从而提升LLM的多样化推理能力。

## 2. 方法论

### 核心思想
论文发现：每个推理能力（如数学、代码等）对应模型参数中**一部分特定行（row）**，这些行对相应任务敏感（称为“delta-scale rows”）；不同任务的重叠参数可能带来增益或冲突。基于此，DiFT在混合微调时仅更新所有目标任务关键参数的**并集**，在连续微调时仅更新当前任务关键参数与历史任务关键参数的**差集**，从而避免干扰历史能力。

### 关键技术细节
- **Delta-scale Row分析**：定义一个指标 `s_k`，衡量某个线性层权重矩阵第k行对模型输出的影响。具体地，对于同一输入，计算微调模型与基座模型在该层输出差异的均方L2范数，作为该行的重要度评分。
- **混合微调（Mix-up SFT）**：对所有任务的关键行取并集（`DSR_union`），冻结其余参数，仅更新这些关键行对应的权重。
- **连续微调（Continual SFT）**：对每个新任务，计算其关键行与之前所有任务关键行的差集（`DSR_diff`），仅更新这部分参数，保留历史任务参数不变。

### 公式/算法流程（文字说明）
1. 对每个推理任务，使用其微调模型和基座模型，采样N个数据点，前向传播并计算每层的delta-scale scores，取前C个高分行作为该任务的关键行集合（DSR_k）。
2. **混合微调**：计算所有任务DSR的并集，基座模型仅更新并集中的参数，其余冻结。
3. **连续微调**：对第k个任务，计算DSR_k与之前所有任务DSR并集的差集，在前一阶段模型上仅更新差集中的参数，其余冻结。

## 3. 实验设计

### 数据集与场景
- **训练数据**：从MathInstruct（数学）、Code Bagel Hermes（代码）、LogiCoT（逻辑推理）、CommonsenseQA+CoS-e+OpenBookQA+SocialIQA+StrategyQA+WorldTree（常识推理）中各采样20000条。
- **评估基准**：
  - 数学：GSM8k（0-shot accuracy）
  - 代码：CodeXGlue（pass rate）
  - 逻辑：LogiQA2（0-shot accuracy）
  - 常识：CommonsenseQA（0-shot accuracy）
  - 通用：MMLU（作为对照）
- **场景**：两种设置——混合微调（2~4个任务组合）和连续微调（2任务序列）。
- **对比方法**：
  - 混合微调：Dual-stage Mixed Fine-tuning (DMT)、CoBa、DiFT
  - 连续微调：HFT、LoTA、DiFT
- **模型**：Llama3-8B-base、Mistral-7B-base、Qwen2.5-14B-base（部分实验包含置信区间）。
- **消融实验**：逆DiFT（交换冻结位置）、不同数量delta-scale rows（20,50,100,200）、不同连续学习顺序、与LoRA对比。

## 4. 资源与算力

论文附录A明确说明：
- **Delta-scale行分析**：在1块NVIDIA A100 GPU上运行，7B/8B模型使用约30GB显存，耗时约900秒；14B模型使用约62GB显存，耗时约1200秒。
- **微调实验**：使用8块A100服务器（一台服务器即可完成所有实验），超参数统一（learning rate=2e-5, batch size=256, max length=2048, weight decay=0.1, warm-up ratio=0.03, 梯度裁剪1.0），采用DeepSpeed ZeRO-2。

## 5. 实验数量与充分性

论文做了大量实验，包括：
- 4种单任务（4组Vanilla SFT）
- 6种两两混合（Mix-Math-Code等）
- 4种混合+DiFT + 与DMT、CoBa对比
- 3种连续（Continual-Math-Code等）+ DiFT + 与HFT、LoTA对比
- 逆DiFT消融（1组）
- 不同delta-scale行数量消融（4个取值）
- 不同连续顺序实验（2组逆序）
- 与LoRA对比（3组）
- 在Qwen2.5-14B上重复部分实验（含置信区间）
- 在Instruct模型上额外评估（表6）
综上，实验覆盖了不同模型、不同任务组合、不同设置、多种对比方法，充分且公平。但未在30B以上模型上验证，也缺乏理论证明。

## 6. 主要结论与发现

1. **推理任务间存在普遍的双向益处与冲突**：如数学与代码混合微调能互相提升，而逻辑与常识混合则冲突明显；连续微调中灾难性遗忘与冲突并存。
2. **每个推理能力对应模型中一组特定的参数行（delta-scale rows）**，且不同任务的行分布有独特性和稳定性。
3. **DiFT通过选择性更新参数能有效保留益处、缓解冲突**，在多数任务组合上超过单任务SFT和现有baseline，尤其在连续微调中显著提升历史任务保留能力。
4. 方法在3种不同模型上均表现一致，证实了通用性和可扩展性。

## 7. 优点

- **创新性分析**：首次通过delta-scale row分析定位推理任务的关键参数，揭示了任务间参数重叠与冲突的微观机制。
- **方法简洁有效**：无需额外计算损失或梯度近似，仅需一次前向分析即可制定冻结策略。
- **实验全面**：覆盖多种任务组合、多种模型、多种基线，并包含消融和逆实验验证。
- **实用性强**：在有限数据（每任务2万条）下即可超越Instruct模型部分能力，表明对特定推理场景有直接应用价值。

## 8. 不足与局限

- **缺乏理论证明**：论文未从理论上证明delta-scale rows与推理能力的因果性，仅基于经验观察。
- **规模受限**：仅在7B/8B和14B模型上实验，未在30B/70B以上大模型验证，可能影响结论的泛化性。
- **连续微调中灾难性遗忘未完全解决**：虽然DiFT能缓解冲突，但对记忆衰减的改善有限（尤其在Llama3-8B上），论文也坦陈这是未来挑战。
- **分析依赖模型规模**：delta-scale rows的稳定性可能在小规模模型或不同架构上有所变化。
- **成本未全面评估**：虽然分析成本较低，但DiFT的微调时间与全参数微调相当（仅调整梯度更新位置），未对比与LoRA等参数高效方法的效率优势。

（完）
