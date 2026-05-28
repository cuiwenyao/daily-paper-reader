---
title: "Search and Refine During Think: Facilitating Knowledge Refinement for Improved Retrieval-Augmented Reasoning"
title_zh: 思考中搜索与精炼：促进知识精炼以改进检索增强推理
authors: "Yaorui Shi, Sihang Li, Chang Wu, Zhiyuan Liu, Junfeng Fang, Hengxing Cai, An Zhang, Xiang Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rBlWKIUQey"
tags: ["query:ns-xai"]
score: 6.0
evidence: 通过思维过程中的迭代精炼提升大模型推理能力
tldr: 现有检索增强推理方法常引入噪声信息阻碍准确推理。本文提出AutoRefine，一种强化学习后训练框架，采用“搜索与精炼”范式，在搜索步骤间显式进行知识精炼，使模型迭代过滤、蒸馏和组织证据。实验表明该方法显著提升推理准确性，为提升大模型推理的可解释性和可靠性提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1335, \"height\": 926, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1426, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 823, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 532, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rblwkiuqey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1438, \"height\": 315, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 687, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 652, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1225, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1440, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rblwkiuqey/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1435, \"height\": 1193, \"label\": \"Table\"}]"
motivation: 现有检索增强推理方法常检索到无关或噪声信息，阻碍准确推理。
method: 提出AutoRefine框架，通过强化学习在搜索步骤间引入显式知识精炼步骤，实现迭代过滤与证据组织。
result: 在多个推理基准上，AutoRefine显著提升了推理准确性。
conclusion: AutoRefine的有效性表明，检索增强推理中引入知识精炼是提升性能的关键。
---

## Abstract
Large language models have demonstrated impressive reasoning capabilities but are inherently limited by their knowledge reservoir.
Retrieval-augmented reasoning mitigates this limitation by allowing LLMs to query external resources, but existing methods often retrieve irrelevant or noisy information, hindering accurate reasoning.
In this paper, we propose **AutoRefine**, a reinforcement learning post-training framework that adopts a new "search-and-refine-during-think" paradigm.
AutoRefine introduces explicit knowledge refinement steps between successive search calls, enabling the model to iteratively filter, distill, and organize evidence before generating an answer.
Furthermore, we incorporate tailored retrieval-specific rewards alongside answer correctness rewards using group relative policy optimization.
Experiments on single-hop and multi-hop QA benchmarks demonstrate that AutoRefine significantly outperforms existing approaches, particularly in complex, multi-hop reasoning scenarios.
Detailed analysis shows that AutoRefine issues frequent, higher-quality searches and synthesizes evidence effectively.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在推理方面表现出色，但其内部知识受限于训练语料，无法获取最新或特定领域信息。检索增强生成（RAG）通过引入外部知识库来缓解这一问题，但现有检索增强推理方法存在两个核心局限：(1) **缺乏对检索文档的精炼**——模型直接使用原始检索内容，面对噪音或弱相关内容时容易分心，尤其在多跳推理中早期步骤的干扰会破坏整个推理链；(2) **未充分利用检索特定奖励**——大部分方法仅依靠最终答案的正确性作为奖励信号（结果奖励），缺乏对检索过程本身的直接监督，导致模型难以学会检索更相关或更有信息的文档。
- **整体意义**：为了提升LLM在知识密集型任务中的准确性和可靠性，需要一种能够迭代过滤、蒸馏和组织证据的推理机制，并引入针对性的奖励信号来指导检索过程。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出 **AutoRefine** 框架，采用“search-and-refine-during-think”范式，在每次搜索与下一步思考之间显式插入知识精炼步骤（`<refine>`），促使模型从检索文档中提取关键信息、去除噪音，并据此规划后续搜索或直接生成答案。同时，通过强化学习联合优化结果奖励和检索奖励，提供更细粒度的监督。

- **关键技术细节**：
  - **轨迹生成**：模型生成包含 `<think>`、`<search>`、`<documents>`、`<refine>`、`<answer>` 等特殊标记的序列。模型自主决定搜索次数，直至输出 `<answer>`。
  - **奖励设计**：
    - **结果奖励（Outcome-Based Reward, R_Ans）**：基于最终答案与真实答案的F1分数，取值范围[0,1]。
    - **检索奖励（Retrieval-Specific Reward, R_Ret）**：检查所有 `<refine>` 块拼接后的文本是否包含真实答案的所有成分（cover exact match），若完全包含则R_Ret=1，否则0。
    - **总体奖励**：若答案正确（R_Ans>0），则最终奖励为R_Ans；若答案错误但检索奖励有效（R_Ret>0），则给部分奖励0.1；否则为0。这种非线性组合优先保证答案正确，同时鼓励中间精炼质量。
  - **训练目标**：使用 **Group Relative Policy Optimization (GRPO)** 优化策略。从当前策略采样一组轨迹，计算每个轨迹的标准化优势，优化时掩码掉检索文档的tokens，避免模型因文档内容而过度调整。

- **公式说明**：
  - R_Ans = F1(o_ans, a)  （公式1）
  - R_Ret = I(a ∩ o_refine = a)  （公式2）
  - R_Overall：如上述分段函数（公式3）
  - GRPO目标：最大化包含裁剪和KL散度惩罚的期望（公式4）

## 3. 实验设计

- **数据集与场景**：
  - **单跳QA**：Natural Questions (NQ)、TriviaQA、PopQA。
  - **多跳QA**：HotpotQA、2WikiMultihopQA (2Wiki)、Musique、Bamboogle。
- **评价指标**：主要采用 **Exact Match (EM)**，同时也报告了 F1 和 Cover Exact Match (CEM)。
- **对比方法**：
  - 无检索类：Direct Generation、SFT、R1-like training (R1)。
  - 单跳检索类：Naive RAG。
  - 多跳检索类：Search-o1、IRCoT、ReSearch、Search-R1。
  - 消融中还对比了使用外部精炼器（BART、Qwen2.5-Instruct）变体。
- **训练设置**：使用 NQ 和 HotpotQA 的合并训练集（共169,615样本），检索器为E5-base-v2，知识源为2018年12月的Wikipedia快照，默认每次返回top-3文档。

## 4. 资源与算力

- 训练在 **8张 NVIDIA A100-80GB GPU** 上进行，全参数微调，使用 Fully Sharded Data Parallelism (FSDP)，BFloat16精度。
- 学习率1e-6，训练 **200步**，采用 VeRL 框架进行强化学习，vLLM 进行高效 rollout 生成。
- 每次采样温度1.0，每个rollout最多 **5次搜索调用**，每组5个rollout，每个查询返回文档截断至512 tokens。

## 5. 实验数量与充分性

- **主要实验**：在7个数据集上与多种基线对比（表1），包括Base和Instruct两种模型变体。
- **分析实验**：
  - 搜索行为分析：搜索频率、搜索成功率随训练步数的变化（图4）。
  - 知识精炼有效性：比较search、refine、answer的召回率和token数（图5）。
  - 检索深度影响：不同k（1-7）下的准确率（图6）。
- **消融实验**：
  - 组件消融：去掉检索奖励、同时去掉精炼步骤（表2），并分析对搜索和精炼的影响（图7）。
  - 模型大小消融：Qwen2.5-3B vs 7B（表3）。
  - 外部精炼器对比（表4）。
  - 检索奖励设计消融：不同作用位置（文档vs精炼）、线性vs非线性组合（表8）。
  - 复杂答案场景下的精细奖励对比（表9）。
  - 统计显著性检验：T-test (p≪0.01) 验证与基线的显著差异（表7）。
  - 训练动态可视化（图8）和案例研究（表10）。
- **充分性**：实验覆盖单跳/多跳多种场景、多种基线、多种消融设置，并进行了统计显著性检验，设计全面、客观、公平。

## 6. 主要结论与发现

- **性能提升**：AutoRefine 在7个QA基准上平均准确率比最强的基线 Search-R1/ReSearch 高出 **6.9%**（Base变体）和 **6.0%**（Instruct变体）。
- **多跳优势明显**：在2Wiki上提升21%，在Musique上提升26.7%，在多跳复杂推理场景下表现尤为突出。
- **自适应搜索**：AutoRefine 学会了根据任务复杂度调整搜索次数，多跳问题搜索更多（2.0-2.5次），单跳问题较少（1.2-2.0次）。
- **搜索质量高**：在多跳任务上，AutoRefine的搜索成功率持续提升至50%以上，比基线（30-40%）高出10-15%。
- **精炼有效**：精炼步骤的召回率与搜索步骤对齐，token数仅为文档的1/4（约100-200 tokens），成功保留了关键信息并过滤噪音。
- **鲁棒性强**：在不同检索深度（k=1到7）下均保持稳定增益，尤其在k≥3时增益更明显（最高在k=5时增益0.09）。
- **组件必要性**：同时使用检索奖励和精炼步骤是达到最佳性能的关键，缺一不可（消融后准确率下降6-10个百分点）。

## 7. 优点

- **创新范式**：首次在检索增强推理中显式引入“search-and-refine-during-think”，填补了现有方法缺乏文档精炼的空白。
- **精细奖励**：设计了检索特定奖励，不仅监督最终答案，还直接指导中间精炼步骤的质量，提供更细粒度的学习信号。
- **无需人工标注**：使用GRPO强化学习，不需要预先收集的推理路径，模型自主探索有效策略。
- **实验全面**：在7个数据集、多种基线和详细消融上验证，并进行了统计显著性检验，结果可信。
- **代码开源**：提供完整的开源代码，便于复现和后续研究。

## 8. 不足与局限

- **评价指标局限**：仅使用EM或F1，可能无法捕捉语义正确但表述不同的回答，对长文本或开放式回答不友好。
- **静态检索语料**：使用2018年Wikipedia快照，缺乏最新或时间敏感信息，限制了在实时搜索场景下的实用性。
- **模型规模有限**：实验仅在3B和7B模型上进行，更大模型（如70B）上的效果未知。
- **计算成本较高**：多步搜索和精炼导致训练和推理的开销增大。
- **任务覆盖范围**：仅在QA任务上验证，未在摘要、长文档理解等其他检索增强任务上测试。

（完）
