---
title: Hierarchical Planning for Complex Tasks with Knowledge Graph-RAG and Symbolic Verification
title_zh: 基于知识图谱RAG和符号验证的复杂任务分层规划
authors: "Flavio Petruzzellis, Cristina Cornelio, Pietro Lio"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vfqdJy12Kk"
tags: ["query:ns-xai"]
score: 8.0
evidence: 结合知识图谱RAG和符号验证的神经符号规划
tldr: 大语言模型在复杂长程规划中常失败。本文提出一种神经符号方法，将知识图谱检索增强生成（RAG）与符号验证相结合，用于分层任务分解。方法将复杂任务逐步分解为可执行原子动作序列，并通过符号验证确保正确性。实验表明该方案显著提升了规划可靠性与任务完成率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vfqdjy12kk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1752, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vfqdjy12kk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vfqdjy12kk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vfqdjy12kk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vfqdjy12kk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 799, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 547, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 549, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1468, \"height\": 720, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1068, \"height\": 720, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1767, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1524, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1766, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1242, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1764, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1765, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1767, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1765, \"height\": 416, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1765, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1586, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1762, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1766, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1767, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vfqdjy12kk/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1767, \"height\": 381, \"label\": \"Table\"}]"
motivation: LLM在复杂长程规划中能力不足，需要外部知识与结构化分解。
method: 结合知识图谱RAG进行分层规划，并嵌入符号验证确保形式正确性。
result: 在复杂任务上显著提升了规划成功率和可靠性。
conclusion: 神经符号方法有效增强了LLM的规划能力与形式保证。
---

## Abstract
Large Language Models (LLMs) have shown promise as robotic planners but often struggle with long-horizon and complex tasks, especially in specialized environments requiring external knowledge. While hierarchical planning and Retrieval-Augmented Generation (RAG) address some of these challenges, they remain insufficient on their own and a deeper integration is required for achieving more reliable systems. To this end, we propose a neuro-symbolic approach that enhances LLMs-based planners with Knowledge Graph-based RAG for hierarchical plan generation. This method decomposes complex tasks into manageable subtasks, further expanded into executable atomic action sequences. To ensure formal correctness and proper decomposition, we integrate a Symbolic Validator, which also functions as a failure detector by aligning expected and observed world states. Our evaluation against baseline methods demonstrates the consistent significant advantages of integrating hierarchical planning, symbolic verification, and RAG across tasks of varying complexity and different LLMs. Additionally, our experimental setup and novel metrics not only validate our approach for complex planning but also serve as a tool for assessing LLMs' reasoning and compositional capabilities. Code available at https://github.com/corneliocristina/HVR.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在机器人规划中展现出潜力，但在复杂、长程任务中表现不佳，尤其在需要外部专业知识的领域（如医疗、交通、家居服务）中。单纯的分层规划（Hierarchical Planning）或检索增强生成（RAG）各自存在局限，需要更深入的整合。
- **核心问题**：如何提升LLM在复杂任务中的规划可靠性，使其能分解任务、检索相关知识，并保证生成计划的形式正确性与执行可行性？
- **整体含义**：本文提出一种神经符号方法（HVR），将知识图谱RAG、分层规划和符号验证三者有机融合，旨在克服LLM的幻觉和推理薄弱问题，为机器人规划提供更可靠、可验证的解决方案。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用知识图谱RAG为LLM提供与环境状态相关的上下文，通过分层规划将复杂任务分解为宏动作（macro actions）和原子动作序列（atomic actions），并引入符号验证器确保计划的逻辑正确性，同时作为执行时的故障检测器。
- **关键技术细节**：
  - **本体与动态知识图谱**：基于OntoThor本体描述厨房环境，包含对象类、属性、关系；执行时结合实时实例形成知识图谱G，记录状态变化。
  - **知识图谱RAG（R）**：根据任务描述，使用LLM选择相关对象子集，从G中检索其状态、属性和位置信息，作为生成计划的上下文。
  - **分层计划生成（H）**：
    - 宏观计划（M-plan）：LLM根据任务描述和检索到的上下文生成宏动作序列（如“拿起瓶子”、“倒酒”）。
    - 原子动作块（AA-block）：每个宏动作进一步展开为原子动作序列（如导航、抓取、放置）。使用动作映射器μ将LLM输出的动作字符串匹配到预定义动作集A。
  - **符号验证与纠正（V）**：
    - 启发式修正：自动插入缺失的导航步骤。
    - 符号验证：使用自定义的PDDL验证器检查计划步骤的可行性，返回具体错误信息。
    - LLM基于错误的反馈进行纠正：宏动作层面调整前提/效果条件；原子动作层面修改动作序列。
    - 运行时对齐：将场景图（视觉观察）与预期状态对比，检测执行失败。
  - **宏动作库与知识迁移**：成功执行的宏动作可存入库中，供后续任务复用，并支持跨机器人聚类与抽象。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **场景与任务**：基于AI2Thor 3D仿真器厨房环境，使用OntoThor本体。设计了12个任务，分为中等复杂度（6个，步数≤20）和高复杂度（6个，步数>20且涉及更多对象）。任务涵盖“倒酒”、“做咖啡”、“煎蛋”、“沙拉制作”等。
- **Benchmark**：没有直接采用已有benchmark，而是基于RECOVER（Cornelio & Diab, 2024）的任务扩展新增两个复杂任务（T11、T12），并复制T5为T5bis（开放目标 vs 固定目标）。
- **对比方法**：
  - HVR（本文完整方法）
  - HV：分层规划+符号验证，无RAG（提供完整KG）
  - HR：分层规划+RAG，无符号验证
  - VR：符号验证+RAG，无分层规划
  - R：仅RAG
  - LLM：仅LLM，提供完整KG
- **LLM选择**：Phi-3-mini-4k-instruct（小型开源）和Gemini-1.5-flash（大型闭源），均为免费可复现。

## 4. 资源与算力

- **文中未明确说明使用的GPU型号、数量、训练时长**。实验部分提到“使用预训练冻结LLM”，未涉及微调，仅通过提示和推理进行规划。因此算力需求主要来自LLM推理和符号验证，但作者未提供具体计算资源信息。

## 5. 实验数量与充分性

- **实验数量**：对12个任务，采用6种方法（HVR, HV, HR, VR, R, LLM），分别使用2种LLM（Phi-3、Gemini），共计约144个实验（12×6×2），每个任务至少运行一次。
- **消融实验**：通过HV、HR、VR、R、LLM系统性地消融了分层规划、RAG、符号验证三个组件。
- **充分性与公平性**：任务覆盖中等和高复杂度；指标包括计划正确性（PC）、执行成功（ES）、长度偏差（LD）、计划验证（EPV、MPV、AABV），多维度评估。此外，对比了T5 vs T5bis（目标明确 vs 开放目标）。实验设计较全面，但未在真实机器人上验证，仅仿真。
- **潜在偏差**：所有任务均在单一厨房场景（AI2Thor）上评估，泛化到其他环境（如工厂、手术室）尚未验证。

## 6. 主要结论与发现

- HVR在所有任务中显著优于所有基线；对于小LLM（Phi-3），RAG贡献更大；对于大LLM（Gemini），分层规划贡献更突出。三者结合达到最佳性能。
- LLM生成的计划往往偏长（比最短计划多100%～200%步数），通过符号验证和纠正可提升正确性但增加步骤。
- 计划正确性与形式验证强相关，说明符号验证有效提升计划质量。
- 在执行阶段，即使计划完全正确，模拟器执行成功率为95%，反映当前仿真器在复杂任务中的局限性。
- LLM在定义明确的目标任务上表现更好，在开放目标（如“加热水”）上表现较差。

## 7. 优点

- **创新性**：首次将知识图谱RAG、分层规划和符号验证深度整合，形成端到端神经符号规划框架。
- **可解释性与可靠性**：符号验证提供形式化保证，并能作为故障检测器，增强安全性。
- **可迁移性**：宏动作库支持知识复用与跨机器人共享，减少重复生成。
- **评估全面**：设计了新指标（PC、ES、LD、EPV、MPV、AABV）消融分析完整，覆盖计划生成、执行、最小性、验证等多维度。
- **可复现性**：使用免费LLM，代码开源。

## 8. 不足与局限

- **仿真环境局限**：仅基于AI2Thor厨房场景，真实世界动态、传感器噪声、物理约束未考虑，实际部署可能面临挑战。
- **动作空间固定**：原子动作集A预定义，无法自适应新增动作类型，依赖领域专家。
- **计算开销**：分层+验证+多次纠正导致规划时间较长（Gemini-1.5-flash平均3285秒，后改用Gemini-2.0-flash降至682秒），实时性不足。
- **线性计划假设**：仅支持全序计划，不支持并行或部分顺序计划，限制了多机器人协作效率。
- **错误纠正独立**：各层级错误纠正未考虑跨层依赖，可能遗漏全局最优修正。
- **未测试大型专用模型**：仅对比了Gemini-1.5-flash和Phi-3，更先进模型（如GPT-4）未纳入，尽管作者声称方法通用。

（完）
