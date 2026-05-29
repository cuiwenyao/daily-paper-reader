---
title: How do Transformers Learn Implicit Reasoning?
title_zh: Transformer如何学习隐式推理？
authors: "Jiaran Ye, Zijun Yao, Zhidian Huang, Liangming Pan, Jinxin Liu, Yushi Bai, Amy Xin, Liu Weichuan, Xiaoyin Che, Lei Hou, Juanzi Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=19ygs48nOa"
tags: ["query:ns-xai"]
score: 7.0
evidence: 研究Transformer在符号环境中学习隐式推理的方式
tldr: LLM能否进行隐式多跳推理的机制尚不明确。本文在受控符号环境中从零训练Transformer，发现其隐式推理能力呈现记忆、分布内泛化、跨分布泛化三阶段。分析表明训练原子三元组可加速学习，且第二跳泛化依赖于查询级组合结构暴露。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1299, \"height\": 824}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 434}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1372, \"height\": 457}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 407, \"height\": 531}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 521}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 512}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1298, \"height\": 743}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1074, \"height\": 629}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1297, \"height\": 757}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 696, \"height\": 450}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1443, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1223, \"height\": 694}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1440, \"height\": 522}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 581, \"height\": 546}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1429, \"height\": 474}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 796, \"height\": 515}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1126, \"height\": 219}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 873, \"height\": 497}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1007, \"height\": 651}]"
motivation: 理解LLM隐式推理的涌现机制至关重要。
method: 在受控符号环境中从零训练Transformer，分析其推理轨迹并引入诊断工具。
result: 揭示了隐式推理的三阶段发展轨迹及关键依赖因素。
conclusion: 符号环境下的训练为理解LLM推理提供了洞见。
---

## Abstract
Recent work suggests that large language models (LLMs) can perform multi-hop reasoning implicitly---producing correct answers without explicitly verbalizing intermediate steps---but the underlying mechanisms remain poorly understood.
In this paper, we study how such implicit reasoning emerges by training transformers from scratch in a controlled symbolic environment.
Our analysis reveals a three-stage developmental trajectory: early memorization, followed by in-distribution generalization, and eventually cross-distribution generalization.
We find that training with atomic triples is not necessary but accelerates learning, and that second-hop generalization relies on query-level exposure to specific compositional structures.
To interpret these behaviors, we introduce two diagnostic tools: cross-query semantic patching, which identifies semantically reusable intermediate representations, and a cosine-based representational lens, which reveals that successful reasoning correlates with the cosine-base clustering in hidden space.
This clustering phenomenon in turn provides a coherent explanation for the behavioral dynamics observed across training, linking representational structure to reasoning capability. 
These findings provide new insights into the interpretability of implicit multi-hop reasoning in LLMs, helping to clarify how complex reasoning processes unfold internally and offering pathways to enhance the transparency of such models.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大型语言模型（LLM）能够执行隐式多跳推理（即不显式输出中间步骤就得到正确答案），但其内部机制尚不清楚。现有研究多基于预训练LLM，缺乏对训练数据的精确控制，难以区分真正的推理与记忆。
- **研究动机**：为了理解隐式推理在Transformer中的涌现过程，需要在受控环境中从零训练模型，并通过细粒度的行为分析和内部表征诊断来揭示其发展轨迹。这有助于提升LLM推理的可解释性和透明度。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：在符号化环境中构造原子三元组（事实）和两跳组合查询，通过控制训练数据的组成（区分分布内ID与分布外OOD），观察模型在不同阶段的行为变化，并借助新的诊断工具分析内部表征。
- **关键技术细节**：
    - **符号数据集**：包含2000个实体、200个关系，生成40000个原子三元组（形式如 `(e1, r1) → e2`），将原子三元组随机分为ID（95%）和OOD（5%）。两跳查询为 `(e1, r1, r2) → e3`，训练数据（Train-II）仅使用ID-ID连接。
    - **模型**：使用8层GPT-2（隐藏维度768，12注意力头），从零训练。优化器为AdamW，学习率1e-4，batch size 1024，训练至多3周。
    - **诊断工具**：
        - **跨查询语义补丁（Cross-Query Semantic Patching）**：将源查询中某层某位置的隐藏向量插入同位置的目标查询，观察目标输出是否转向源查询的桥接实体路径，从而定位中间实体表征的位置（发现主要位于 `r1` 位置的第5层）。
        - **余弦表示透镜（Cosine-based Representational Lens）**：对共享同一桥接实体的不同查询，提取该位置隐藏向量并计算余弦相似度，定义“ID聚集度”和“OOD对齐度”两个指标，量化内部表征的几何规整性。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **数据集/场景**：
    - 主要使用自构符号数据集，包含ID/OOD原子三元组和Train-II、Test-II、Test-OI等多种两跳查询类型。还扩展到三跳场景（附录C）。
    - 多种训练配置消融：基础配置（含所有原子三元组和Train-II）、仅Train-II配置、第二跳缺失配置、不同ID/OOD比例配置（0.8/0.2、0.5/0.5、0.3/0.7）等。
- **基准**：没有与外部模型对比，主要进行内部行为分析和机制验证。部分结果与Wang et al. [2024]（Grokking of implicit reasoning）的工作进行对比，指出发现了第三阶段（跨分布泛化）。
- **对比方法**：主要是不同训练配置之间的消融对比（例如是否包含ID原子三元组、第二跳暴露与否），以及不同大小模型（GPT-2 small vs Qwen2.5-1.5B）的扩展验证。

## 4. 资源与算力
- 文中在附录G明确说明：
    - GPU型号：NVIDIA RTX 3090（未说明具体数量，推测使用单卡或多卡但未明确）。
    - 训练时长：最长至3周以确保跨分布泛化稳定。
    - 其他细节：batch size 1024，2000步warm-up，weight decay 0.1。
- 未提及具体GPU数量、总计算量或能耗。对于更大模型（Qwen2.5-1.5B）的训练细节未详细给出GPU资源。

## 5. 实验数量与充分性
- **实验组数**：较多，涵盖：
    - 基础配置下的三阶段动态观察（图2）。
    - ID原子三元组必要性消融（图3a vs 3b）。
    - 第二跳泛化失败验证（图6b及附录D.1、D.2）。
    - 第二跳暴露频率与准确率关系（附录D.2）。
    - 三跳扩展实验（附录C）。
    - 跨分布泛化与ID/OOD比例消融（附录H）。
    - 解码偏好实验（附录E）。
    - 更大模型Qwen2.5-1.5B验证（附录G.2）。
    - 跨查询语义补丁在各阶段和来源的详细结果（附录F）。
    - 其他支持性消融（附录I、J）。
- **充分性评价**：
    - 优点：实验设计系统，覆盖了行为、表征、消融等维度，且扩展到3跳和更大模型以验证一般性。
    - 不足：未报告多次运行的误差线（作者承认由于计算成本过高未做），部分实验（如下游任务泛化）未涉及；符号环境与真实文本环境的差距可能影响外部有效性。

## 6. 论文的主要结论与发现
- **三阶段发展轨迹**：隐式推理在训练中依次经历记忆（Phase I）、分布内泛化（Phase II）、跨分布泛化（Phase III）。
- **ID原子三元组的作用**：对分布内泛化并非必需，但可显著加速泛化进程。
- **第二跳泛化依赖查询级匹配**：模型必须看到特定组合结构才能泛化到对应第二跳；仅暴露原子三元组（作为第一跳或独立事实）不够。
- **内部机制**：成功推理的模型在中间实体表征（`r1` 位置第5层）上呈现余弦空间聚类。ID内部实体聚类与Test-II性能同步，OOD实体与ID聚类对齐则对应Test-OI性能。显式可解码性（通过logit lens）与推理能力并不一致。
- **第一跳OOD泛化的本质**：看似的第一跳OOD泛化实际是ID三元组强迫对齐表征空间的副产品，并非真正的跨分布推理；第二跳无法OOD泛化正是由于缺乏这种表征锚定。
- **三跳场景验证**：同一模式在更深的推理中成立，仅第一跳可OOD泛化。

## 7. 优点：方法或实验设计亮点
- **受控符号环境**：允许精确操纵训练数据，区分记忆、泛化与推理，克服了预训练LLM数据不透明的问题。
- **新颖的诊断工具**：跨查询语义补丁能更确切地定位因果相关表征；余弦表示透镜提供了非解码的几何视角，解释了行为与表征之间的联系。
- **从行为到机制的闭环分析**：先发现行为现象，再挖掘内部机制，最后用机制解释行为，逻辑完整。
- **扩展验证**：在三跳和更大模型上复现核心结果，增强结论的可迁移性。
- **消融实验设计精细**：如仅Train-II训练、第二跳缺失、ID/OOD比例变化等，有效隔离变量。

## 8. 不足与局限
- **实验覆盖**：
    - 未报告误差线，缺少多次运行的统计分析，可能影响结果可靠性。
    - 仅在符号数据集上验证，与真实语言任务（如常识推理、数学推理）的差距较大，结论的泛化性需要更多实证。
    - 未探索不同模型架构（如非GPT式、编码器-解码器）的影响。
- **偏差风险**：
    - 默认ID/OOD比例为95/5，且Train-II与ID三元组比例为7.2:1，这些参数选择可能对结果敏感（作者虽解释为模拟真实语料，但未做广泛敏感性分析）。
    - 对“OOD”的定义仅基于三元组在训练中是否出现在组合查询中，与真实分布漂移概念有差异。
- **应用限制**：
    - 更大模型（Qwen2.5-1.5B）在Phase III表现出不稳定性，表明跨分布泛化可能随规模增加而更脆弱。
    - 隐式推理的内部机制（余弦聚类）可能无法直接用于解释CoT等显式推理场景。
- **其他**：
    - 未讨论负面社会影响或更广泛的伦理考虑。

（完）
