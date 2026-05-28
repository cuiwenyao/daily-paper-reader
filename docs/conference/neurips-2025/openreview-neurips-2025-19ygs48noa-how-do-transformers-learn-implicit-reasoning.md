---
title: How do Transformers Learn Implicit Reasoning?
title_zh: Transformer如何学习隐式推理？
authors: "Jiaran Ye, Zijun Yao, Zhidian Huang, Liangming Pan, Jinxin Liu, Yushi Bai, Amy Xin, Liu Weichuan, Xiaoyin Che, Lei Hou, Juanzi Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=19ygs48nOa"
tags: ["query:ns-xai"]
score: 8.0
evidence: 在受控符号环境中研究大型语言模型如何学习隐式推理
tldr: 大型语言模型隐式推理机制尚不明确。本文在受控符号环境中从头训练Transformer，发现隐式推理经历记忆、分布内泛化、跨分布泛化三个阶段，并揭示第二跳泛化依赖于查询级暴露于特定组合结构。引入两种诊断工具帮助解释模型行为。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1299, \"height\": 824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1372, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 407, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1298, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1074, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1297, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 696, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1443, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1223, \"height\": 694, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1440, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 581, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1429, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-19ygs48noa/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 796, \"height\": 515, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1126, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 873, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-19ygs48noa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1007, \"height\": 651, \"label\": \"Table\"}]"
motivation: 理解LLM隐式推理的内部机制对于可解释性至关重要。
method: 在受控符号环境中从头训练Transformer，并分析其推理行为发展轨迹。
result: 发现训练过程呈现三阶段，且特定组合结构对泛化关键。
conclusion: 该研究为理解LLM推理提供了机制层面的解释。
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

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）能够在无需显式输出中间步骤的情况下进行隐式多跳推理，但其内部机制尚不明确。本文旨在回答“Transformer如何学习并执行隐式推理”。
- **背景**：
  - 现有研究主要分为两类：一是基于预训练LLM的分析，但训练数据不透明，难以区分真实推理与记忆；二是使用符号数据集从头训练，但缺乏细粒度控制和行为分辨率。
  - 已有工作发现原子事实的双重失败（单跳可解但多跳失败）、泛化需要过拟合（grokking）等现象，但对隐式推理的发育轨迹和内部表示缺乏系统理解。
- **整体含义**：通过受控符号环境揭示隐式推理的三阶段发展、查询级依赖以及表示几何规律，从而为LLM推理的可解释性和透明度提供理论基础。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在完全可控的符号环境中训练Transformer（GPT-2），通过精确定义的原子三元组和组合查询，隔离不同训练信号的影响，并利用新型诊断工具分析内部表示。
- **关键技术细节**：
  - **符号数据集构建**：
    - 原子三元组形式为 `(e1, r1) → e2`，分为ID（分布内）和OOD（分布外）子集。
    - 2跳查询形式为 `(e1, r1, r2) → e3`，要求模型隐式穿越中间实体 e2。
    - 训练配置（基配置）包含所有原子三元组和 Train-II（ID-ID 组合）查询；测试集覆盖 Test-II、Test-OI、Test-IO、Test-OO。
    - 通过选择性移除特定三元组或限制组合方式构建消融变体（如仅Train-II、第二跳消融、ID/OOD比例变化等）。
  - **诊断工具**：
    - **Cross-Query Semantic Patching（跨查询语义补丁）**：将源查询的中间层隐藏状态（r1 位置）插入目标查询的相同位置，若目标输出改变为源查询的路径，则证明该隐藏状态携带可迁移的中间实体语义信息。用于定位中间实体表示发生的层和位置。
    - **Cosine-based Representational Lens（基于余弦的表示透镜）**：提取同一中间实体在不同查询中的隐藏状态（r1 位置，层5），计算余弦相似度并观察聚类结构。定义 ID Cohesion（ID派生表示与质心的平均余弦相似度）和 OOD Alignment（OOD派生表示与ID质心的平均余弦相似度）作为量化指标。
- **公式/算法流程（文字说明）**：
  - 训练时，模型接收序列 `[e1, r1, r2]` → 预测 e3。由于因果掩码，r1 位置隐藏状态 h5_r1 同时影响原子查询 `(e1, r1)` 的输出和2跳查询中后续步骤的处理。
  - 补丁过程：选择一个源查询（如 `(eA, r1, r2)`），提取其层5、r1位置的隐藏向量。将该向量替换到目标查询（如 `(eX, r6, r7)`）的相同位置，然后前向传播。若模型输出变为 `r7(r1(eA))` 而非 `r7(r6(eX))`，则判定补丁成功，表示向量编码了中间实体。
  - 聚类分析：对于每个中间实体，收集所有相关查询的 h5_r1，计算 pairwise 余弦距离并 MDS 可视化，同时计算 Cohesion 和 Alignment 指标。

### 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **数据集**：
  - 自定义符号数据集，包含 2000 个实体，200 个关系，40000 个原子三元组（ID 38000，OOD 2000），273600 个 Train-II 查询，测试集每种类型 3000 个。
  - 扩展3跳场景：实体1000，关系100，原子三元组 10000（ID 8000，OOD 2000），Train-III 120000，测试集每种类型 1000。
- **场景与benchmark**：
  - 基配置（Base）：全部三元组+Train-II → 评估 Test-II, Test-OI, Test-OO, Test-IO。
  - 消融场景：仅 Train-II、Train-II+ID三元组、第二跳消融、不同ID/OOD比例（0.8/0.2, 0.5/0.5, 0.3/0.7）、ID三元组完全移除、解码偏好实验（移除ID三元组但保留OOD和Train-II）。
  - 大模型扩展：Qwen2.5-1.5B 在基配置上训练。
- **对比方法**：
  - 主要为不同训练配置之间的消融对比（有无ID三元组、第二跳暴露与否、ID/OOD比例等），作为自身行为的对照。
  - 未与其他隐式推理方法（如 CoT 蒸馏、连续潜在空间推理）进行直接比较，因为该工作聚焦于内部机制发现而非性能提升。

### 4. 资源与算力

- **GPU 型号**：NVIDIA RTX 3090。
- **数量**：未明确说明单卡或多卡，推测单卡或少数（多个实验并行）。
- **训练时长**：基配置训练最大延长至3周（确保跨分布泛化稳定）。
- **其他细节**：批大小1024，采用 AdamW 优化器，学习率 1e-4，2000步预热，权重衰减0.1。训练步数数百万至千万（取决于消融配置）。论文未报告总 GPU 小时数，但资源开销较高。

### 5. 实验数量与充分性

- **实验数量**：涵盖大量配置和诊断，主要包括：
  - 基配置完整动态追踪（三阶段）
  - 2跳必要成分消融（仅Train-II vs +ID三元组）
  - 第二跳查询级依赖消融（多种方式）
  - ID/OOD比例消融（3种）
  - 完全移除ID三元组验证
  - 解码偏好实验
  - 3跳扩展
  - 大模型扩展（Qwen2.5-1.5B）
  - 跨查询语义补丁（4个阶段× 2个数据源）
  - 余弦表示聚类可视化与量化
- **充分性与公平性**：
  - **充分**：实验设计精细，逐步隔离变量，能够回答核心机制问题；行为学与机械论分析相互印证，形成闭环解释。
  - **局限性**：未报告多次运行的统计误差条（作者声明计算成本过高），结果可能存在随机波动。消融仅覆盖2跳主要场景，3跳和大模型分析较初步。未与其他潜在隐式推理学习方法比较，但本研究性质使其不必要对比。
  - **客观**：实验逻辑清晰，结论有充足证据支持，消融一致验证假设。

### 6. 论文的主要结论与发现

1. **隐式推理呈现三阶段发育轨迹**：
   - Phase I（记忆）：快速拟合训练数据，无泛化。
   - Phase II（分布内泛化）：在ID-ID组合上泛化（类似于grokking）。
   - Phase III（跨分布泛化）：将OOD三元组作为第一跳仍能正确推理（第二跳必须为ID）。
2. **原子三元组对ID泛化非必需但加速学习**：仅用Train-II查询即可泛化ID组合，加入ID三元组能显著提前泛化。
3. **第二跳泛化需要查询级暴露**：模型必须见过某个三元组作为第二跳出现在训练查询中才能泛化；仅作为原子事实或第一跳出现不够。
4. **中间实体表示在余弦空间中聚类是成功推理的内部基础**：ID Cohesion 和 OOD Alignment 指标与行为泛化高度同步。聚类出现之前模型无法正确推理。
5. **第一跳OOD泛化是ID表示对齐的副产品**：ID三元组约束了 r1 位置表示形成一个可解码子空间，OOD派生表示被“拉”入该子空间，并非真正的组合性泛化。第二跳OOD无法泛化源于缺乏类似的表示锚定。
6. **3跳场景一致支持上述规律**：仅当第一跳为OOD时泛化，更深位置失败。
7. **大模型（Qwen2.5-1.5B）重现三阶段，但Phase III更不稳定，且ID Cohesion与Test-II解耦**，表明第二阶段瓶颈可能在第二跳执行层。

### 7. 优点：方法或实验设计上的亮点

- **细粒度控制**：符号环境支持精确移除特定三元组或限制组合角色，能够隔离每个训练信号的作用，这是预训练LLM难以做到的。
- **新颖诊断工具**：
  - 跨查询语义补丁比传统因果补丁更语义化，能够证明隐藏状态的可迁移性而非仅因果影响。
  - 余弦透镜不依赖可解码性假设，直接揭示几何一致性，避免了显式探测的局限性。
- **行为-机制闭环**：通过三阶段动态发现表示聚类，然后反过来用聚类解释所有行为现象（如加速、第二跳难泛化、第一跳OOD泛化本质），形成完整因果链条。
- **扩展验证**：在更大模型和3跳场景中验证了主要结论，提高了普适性。
- **清晰的可视化**：MDS投影和余弦相似度曲线直观展示表示演变。

### 8. 不足与局限

- **实验限制**：
  - 符号环境与现实LLM的知识基差异巨大（实体数少、关系简单），结论到真实场景的推广需谨慎。
  - 未提供统计误差棒（作者声明计算成本），结果鲁棒性存疑。
  - 大模型实验中Phase III不稳定，未深入优化；第二跳瓶颈在大型模型上的确切原因尚未完全明确。
- **方法局限**：
  - 诊断工具依赖于已知中间实体的位置（通过补丁确定），对于更复杂推理可能不易定位。
  - 余弦透镜仅使用单层（层5），同一中间实体在其他层也可能有不同表示模式。
- **应用限制**：
  - 工作聚焦于理解机制，并未提出可提升LLM隐式推理能力的实用方法。
  - 未讨论负社会影响或潜在滥用风险（但符号数据集本身无害）。
- **可复现性**：论文提供了代码库链接（GitHub），但未在正文中给出开源许可说明，需检查补充材料。

（完）
