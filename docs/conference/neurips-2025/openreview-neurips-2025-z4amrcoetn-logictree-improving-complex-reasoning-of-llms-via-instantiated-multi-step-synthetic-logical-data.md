---
title: "LogicTree: Improving Complex Reasoning of LLMs via Instantiated Multi-step Synthetic Logical Data"
title_zh: LogicTree：通过实例化多步合成逻辑数据提升大模型复杂推理
authors: "Zehao Wang, Lin Yang, Jie Wang, Kehan Wang, Hanzhu Chen, Bin Wang, Jianye HAO, Defu Lian, Bin Li, Enhong Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=z4AMrCOetn"
tags: ["query:ns-xai"]
score: 6.0
evidence: 合成多步逻辑推理数据以提升大模型复杂推理能力
tldr: 大语言模型在复杂逻辑推理上仍显不足。现有数据生成依赖模板，适应性差。本文提出LogicTree，通过迭代搜索适用逻辑规则，高效合成既复杂又具实例化的多步推理数据集。实验表明，使用该数据微调可显著提升LLM在多步逻辑推理任务上的表现。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1140, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1374, \"height\": 143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1403, \"height\": 880, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1366, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1169, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1319, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1369, \"height\": 734, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 1637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1376, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1303, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 1543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1351, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1382, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 493, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1157, \"height\": 948, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1460, \"height\": 804, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1320, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1455, \"height\": 1555, \"label\": \"Table\"}]"
motivation: 大模型在复杂逻辑推理任务上表现不佳，现有合成数据方法缺乏复杂性与实例化。
method: 提出LogicTree框架，迭代搜索逻辑规则以生成多样化多步推理样本。
result: 微调后的LLM在多个推理基准上准确率显著提升。
conclusion: 高质量的合成逻辑数据可有效增强LLM的复杂推理能力。
---

## Abstract
Despite their remarkable performance on various tasks, Large Language Models (LLMs) still struggle with logical reasoning, particularly in complex and multi-step reasoning processes. 
Among various efforts to enhance LLMs' reasoning capabilities, synthesizing large-scale, high-quality logical reasoning datasets has emerged as a promising direction. 
However, existing methods often rely on predefined templates for logical reasoning data generation, limiting their adaptability to real-world scenarios. 
To address the limitation, we propose **LogicTree**, a novel framework for efficiently synthesizing multi-step logical reasoning dataset that excels in both complexity and instantiation.
By iteratively searching for applicable logic rules based on structural pattern matching to perform backward deduction, **LogicTree** constructs multi-step logic trees that capture complex reasoning patterns. 
Furthermore, we employ a two-stage LLM-based approach to instantiate various real-world scenarios for each logic tree, generating consistent real-world reasoning processes that carry contextual significance.   This helps LLMs develop generalizable logical reasoning abilities across diverse scenarios rather than merely memorizing templates.
Experiments on multiple benchmarks demonstrate that our approach achieves an average improvement of 9.4\% in accuracy on complex logical reasoning tasks.

---

## 论文详细总结（自动生成）

# 论文结构化总结：LogicTree

## 1. 核心问题与整体含义（研究动机与背景）
- **问题背景**：大语言模型在复杂多步逻辑推理任务上表现不佳，现有逻辑推理数据合成方法主要依赖预定义模板，生成的数据推理模式简单、步骤浅，且缺乏真实世界场景的实例化，导致模型仅能记忆模板而非习得可泛化的推理能力。
- **研究目标**：提出一种能高效合成**高复杂度**且**强实例化**的多步逻辑推理数据集的框架，使LLM发展出可迁移的逻辑推理能力。

## 2. 方法论
- **核心思想**：基于一阶逻辑规则通过**结构模式匹配的向后演绎**生成多步逻辑树，再利用LLM将树中的符号逻辑实例化为具有上下文意义的自然语言场景和推理过程。
- **关键技术细节**：
  - **逻辑推理树生成**：将公式表示为抽象语法树，通过比较结构模式是否同构来判断规则是否可应用。从随机根公式开始，迭代随机选择叶子节点，搜索适用规则进行向后演绎，扩展子树，直至达到预设迭代次数（深度2~15）。支持命题逻辑和一阶逻辑规则的混合。
  - **两阶段LLM实例化**：
    1. **场景实例化**：将逻辑树所有叶子节点的逻辑符号输入LLM，要求赋予真实世界实体/事件，并保持逻辑关系一致。通过控制主题域（50+主题）保证多样性。
    2. **推理过程翻译**：按深度降序排列内部节点，获得完整符号推理链，再让LLM基于已实例化的场景翻译每一步为自然语言，LLM仅需做符号转换，不涉及自主推理。
  - **后处理**：验证LLM输出的自然语言陈述与原始逻辑表达式是否一致（字符串精确匹配），过滤掉约8.73%的噪声数据。最终构建前提-结论-答案-推理过程的完整实例。
- **算法流程**：见Algorithm 1（主体为循环选叶子、匹配规则、向后演绎）。

## 3. 实验设计
- **合成训练数据**：生成5000棵逻辑树（深度2~15），每棵实例化3个不同场景，共15000条，过滤后得13.8k高质量实例。
- **评测基准**：LogicBench、LogiQA2.0、FOLIO、BBH-Logic（三/五/七对象）、AGIEval（LAST-AR、LAST-LR）、Multi-LogiEval（按推理步数d1-d5分类）。
- **对比方法**：Vanilla（无训练）、PARARULE、LogicAsker、FLD×2。
- **模型与训练设置**：
  - 模型系列：Llama-3.1（8B/70B）、Mistral-v0.3（7B）、Qwen2.5（1.5B/3B/7B）、Deepseek-R1-Distill（Qwen-7B、Llama-8B）。
  - 微调策略：8B以下全微调，70B使用LoRA。
  - 超参数：学习率1e-6（8B）/3e-6（小模型）/2e-5（70B LoRA），上下文长度4096，batch size 128，3个epoch，余弦学习率衰减，warmup比0.03，使用DeepSpeed+BF16+梯度检查点。

## 4. 资源与算力
- 文中未明确说明使用的GPU型号、卡数及具体训练时长。仅在附录B.2中描述了训练配置（DeepSpeed、BF16等），未提供硬件细节。

## 5. 实验数量与充分性
- **实验数量**：大幅实验覆盖多种模型（4个家族、7个尺寸）、6个主基准+Multi-LogiEval（5个深度子集）+泛化实验（Proofwriter、Mathqa、GPQA、Humaneval、Commonsenseqa、MNLI），以及消融实验（3个组件分析+多样性数量实验）+小模型验证+DeepSeek蒸馏模型验证。
- **充分性**：实验设计系统，对比基线充分（包括原子规则和多步模板方法），报告了多次运行的标准差，消融实验清晰验证了各组件贡献。多步推理实验（Figure 2）表明LogicTree在深度增加时优势更明显。泛化实验覆盖逻辑、数学、代码、NLI等多领域，验证了推理能力提升的迁移性。
- **公平性**：所有方法使用相同微调设置和相同数据量（基线数据量是否一致？文中未明确说明，但逻辑上应保持相当）。总体客观公平。

## 6. 主要结论与发现
- LogicTree在所有基线和大多数基准上取得一致且显著提升，平均准确率提升9.4%（Llama-3.1-8B），且在70B模型上仍有2.9%提升。
- 在多步推理（Multi-LogiEval）上优势尤为突出，深度d3-d5提升远优于其他方法。
- 消融实验表明：**实例化真实场景**、**自然语言推理过程**、**场景多样性**三者均不可或缺；仅单一场景甚至导致性能下降（过拟合），多样性收敛于3~4个场景。
- 泛化实验显示LogicTree在数学、代码等推理密集型任务上也有显著提升，而知识记忆型任务提升较小，符合预期。

## 7. 优点
- **方法创新**：结构模式匹配的向后演绎可生成复杂多步逻辑树（集成命题和FOL规则，规则数达190种），突破模板拼接的局限；两阶段LLM实例化有效降低生成错误，保证逻辑一致性。
- **数据质量**：通过LLM自动赋予真实世界语义，而非随机实体，数据具有上下文连贯性；后处理过滤保证高质量。
- **实验全面性**：跨模型、跨规模、跨任务领域的系统评估，消融和泛化实验设计合理，结论可信。
- **实际效果**：在多种LLM上稳定提升，尤其增强多步复杂推理，且计算成本相对可控（生成效率优于基于搜索的方法）。

## 8. 不足与局限
- **不能与其他推理形式融合**：文中明确表示无法与常识推理等结合，限制了综合推理能力的进一步提升。
- **依赖LLM实例化**：虽然采用两阶段策略降低错误，但仍依赖LLM的符号转换能力，且过滤了8.73%数据，说明存在一定不稳定。
- **实验覆盖局限**：主要聚焦形式逻辑和标准化测试，在真实开放域复杂推理上的泛化性尚未充分验证。
- **计算成本说明不足**：未提供具体的GPU型号、训练时间和总算力消耗，可复现性受一定影响。
- **多样性主题选择**：50+主题由人工定义，可能存在覆盖偏差；多样化对性能提升的收敛点为3~4，但最佳数量可能因任务而异。

（完）
