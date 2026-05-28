---
title: "SCOUT: Teaching Pre-trained Language Models to Enhance Reasoning via Flow Chain-of-Thought"
title_zh: SCOUT：通过流式链式思维教授预训练语言模型增强推理
authors: "Guanghao Li, Wenhao Jiang, Mingfeng Chen, Yan Li, Hao Yu, Shuting Dong, Tao Ren, Ming Tang, Chun Yuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eXckZbaYma"
tags: ["query:ns-xai"]
score: 7.0
evidence: 大模型的递归推理范式
tldr: 针对链式思维提示中中间步骤限制扩展性的问题，本文提出流式链式思维（Flow CoT），将递归推理建模为隐认知状态的渐进轨迹，无需显式CoT监督即可提升推理性能。实验表明Flow CoT在多个推理任务上优于标准CoT方法，并提供了一种新的可扩展推理框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1303, \"height\": 809, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1345, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 495, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 653, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-exckzbayma/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 742, \"height\": 519, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 865, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1001, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1365, \"height\": 132, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 805, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-exckzbayma/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1031, \"height\": 725, \"label\": \"Table\"}]"
motivation: 标准CoT依赖中间步骤，限制了可扩展性和泛化能力。
method: 提出Flow CoT，将递归推理建模为隐状态的渐进演化轨迹。
result: 在多个推理基准上优于标准CoT，且无需显式推理步骤。
conclusion: Flow CoT提供了一种无需显式监督的递归推理新范式。
---

## Abstract
Chain-of-Thought (CoT) prompting improves the reasoning performance of large language models (LLMs) by encouraging step-by-step thinking. However, CoT-based methods depend on  intermediate reasoning steps, which limits scalability and generalization. Recent work explores recursive reasoning, where LLMs reuse internal layers across iterations to refine latent representations without explicit CoT supervision. While promising, these approaches often require costly pretraining and lack a principled framework for how reasoning should evolve across iterations.
We address this gap by introducing **Flow Chain-of-Thought (Flow CoT)**, a reasoning paradigm that models recursive inference as a progressive trajectory of latent cognitive states. Flow CoT frames each iteration as a distinct cognitive stage—deepening reasoning across iterations without relying on manual supervision. To realize  this, we propose **SCOUT** (*Stepwise Cognitive Optimization Using Teachers*), a lightweight fine-tuning framework that enables Flow CoT-style reasoning without the need for pretraining. SCOUT uses progressive distillation to align each iteration with a teacher of appropriate capacity, and a cross-attention-based retrospective module that integrates outputs from previous iterations while preserving the model’s original computation flow.
Experiments across eight reasoning benchmarks show that SCOUT consistently improves both accuracy and explanation quality, achieving up to 1.8\% gains under fine-tuning. Qualitative analyses further reveal that SCOUT enables progressively deeper reasoning across iterations—refining both belief formation and explanation granularity. These results not only validate the effectiveness of SCOUT, but also demonstrate the practical viability of Flow CoT as a scalable framework for enhancing reasoning in LLMs.

---

## 论文详细总结（自动生成）

# SCOUT：通过流式链式思维教授预训练语言模型增强推理——论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题背景**：链式思维（CoT）提示通过生成中间推理步骤提升了大语言模型（LLM）的推理能力，但严重依赖人工标注的中间步骤，限制了可扩展性和跨领域泛化能力。
- **现有递归推理的不足**：近期工作探索递归推理（循环使用内部层迭代细化隐表示），但通常需要昂贵的预训练，且缺乏一个理论框架来描述推理应如何随迭代演化——各迭代被视为黑盒重复，忽略了认知状态的渐进性。
- **论文目标**：提出一种新的推理范式 **Flow CoT**（流式链式思维），将递归推理建模为隐认知状态的渐进轨迹；并设计轻量级微调框架 **SCOUT**，无需额外预训练即可赋予LLM Flow CoT能力，从而在不依赖显式CoT监督的前提下提升推理性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：Flow CoT将每次递归迭代视为一个不同的认知阶段，推理深度随迭代自然加深，而非简单的重复。SCOUT通过**渐进蒸馏**和**回顾推理模块**实现这一范式。
- **关键技术细节**：
  - **模型分解**：将预训练LLM分解为头部块（`f_head`）、递归块（`f_θ`）和尾部块（`f_tail`）。输入编码一次，隐状态经T步递归更新，最后解码输出。
  - **渐进蒸馏**：
    - 每一步的隐状态`z^(t)`被解码，并由一个**容量匹配的教师模型**提供软目标`q^(t)`。早期步骤使用较小教师（如1.5B），后期使用更强教师（如7B），避免早期过正则化，确保学习信号与模型当前能力对齐。
    - 蒸馏损失为KL散度与可选的硬标签交叉熵之和（α=0.5）。
  - **回顾推理模块**：
    - 引入轻量级**交叉注意力**机制，将前一步的隐状态`z^(t-1)`作为外部记忆，当前步通过自注意力处理原始输入`z^(0)`，并通过交叉注意力选择性整合前一步信息。这保持了预训练模型的数据流，同时实现步间连贯推理。
  - **训练与推理**：
    - 训练时对各步损失加权求和（等权λ_t=1/3），通过端到端反向传播学习逐步认知精化。
    - 推理时迭代T步，最终解码`z^(T)`输出。
- **公式说明**：
  - 初始状态：`z^(0) = f_head(x)`
  - 第一步递归：`z^(1) = f_θ(z^(0))`
  - 后续步骤：`z^(t) = f_θ( H(z^(0), z^(t-1)) )`，其中`H`为历史整合函数（跨注意力实现）。

## 3. 实验设计：数据集、基准、对比方法
- **数据集与场景**：
  - 训练数据：混合五个指令微调数据集：Alpaca GPT-4、Alpaca CoT、WikiQA、CodeAlpaca、MathInstruct。
  - 评估基准：**8个推理任务**，涵盖四类：
    - 常识QA：ARC-easy、ARC-challenge、OpenBookQA、TruthfulQA
    - 多步推理：GSM8K、MMLU
    - 阅读理解/对话：CoQA、GLUE
    - 代码生成：MBPP
- **对比方法**：
  - **SFT**：标准监督微调，仅最终输出损失。
  - **DSFT**：使用Qwen2.5-7B软目标蒸馏，无递归。
  - **R-SFT**：递归框架+硬标签监督。
  - **R-Distill-EQ**：递归+固定7B教师，等权损失。
  - **R-Distill-WT**：递归+固定7B教师，递增权重（λ1=0.2, λ2=0.3, λ3=0.5）。
  - **R-SCOUT**：反向教师顺序（7B→3B→1.5B），作为控制实验。
- **学生模型**：Qwen2.5-0.5B；教师模型：Qwen2.5-1.5B、3B、7B（分别对应迭代1、2、3）。

## 4. 资源与算力
- **文中明确提及**：
  - 硬件：1块 NVIDIA H20 NVLink GPU（96 GB），搭配双插槽服务器（20核 Intel Xeon Platinum 8457C，200 GB RAM）。
  - 训练配置：使用torch本机梯度累积模拟全局batch size 128，训练2个epoch，学习率2e-5，bf16精度。
  - 新引入参数（如交叉注意力投影）的学习率设为2倍（4e-5）。
  - 未说明训练总时间或具体GPU小时数，但指出是轻量级微调。

## 5. 实验数量与充分性
- **主要实验**：完整对比了6种基准方法在8个评估指标上的性能（Table 1），涵盖不同迭代次数（Iter=1,2,3）。
- **消融实验**：
  - **回顾机制消融**（Table 2）：对比6种历史整合策略（Init、Add、CatProj、Gate、ModInj、XAttn）在3次迭代下的平均准确率，证明Cross-attention唯一稳定提升。
  - **结构划分消融**（Appendix B.2，Table 5）：比较两种层分配策略（Case 1 和 Case 2）对性能的影响，验证将更多深层放入头部和递归块更优。
  - **单次渐进蒸馏实验**（Appendix B.1，Table 4）：无递归情况下顺序蒸馏，作为对照。
  - **数据集级详细结果**（Appendix B.3，Table 6）：每个回顾模块在8个任务上的逐迭代分数。
- **定性分析**：Figure 4（token概率热力图）和Figure 5（推理文本演化）展示认知逐步精化。
- **充分性与公平性**：实验设计较为全面，对比了统一监督、固定教师、渐进教师等多种策略，控制变量清晰。评估使用标准框架（lm-evaluation-harness），基准均为公开数据集。但未报告多次运行的误差条（除Figure 3的KL散度外），仅使用固定验证集，统计显著性稍弱。

## 6. 主要结论与发现
- **SCOUT显著优于所有基线**：在T=3时平均准确率比SFT提升+1.81%，且呈单调递增趋势（+0.23→+1.05→+1.81），而其他递归方法（如R-Distill-EQ）后期停滞或退化。
- **渐进蒸馏优于统一蒸馏**：容量递增的教师匹配能避免早期过正则化和后期欠训练；反向顺序（R-SCOUT）导致后期性能崩塌。
- **Cross-attention回顾机制最有效**：唯一在所有迭代上稳定提升的集成方式，其他简单融合（加性、门控等）随深度增加性能下降。
- **推理质量逐步提升**：定性分析显示SCOUT在token置信度和解释清晰度上均随迭代改善，体现了认知渐进性。

## 7. 优点
- **无需预训练**：SCOUT仅通过微调即可赋予LLM多步递归推理能力，降低计算成本和部署门槛。
- **理论驱动的设计**：Flow CoT提供了递归推理的认知渐进框架，SCOUT的渐进蒸馏和回顾模块与此框架紧密契合。
- **模块化与兼容性**：回顾模块仅添加浅层交叉注意力，不影响预训练模型原始数据流，易于集成到标准微调管线。
- **广泛的实验验证**：覆盖8个多样化的推理基准，包括常识、数学、阅读、代码，结果一致提升。
- **直观的定性证据**：通过概率热图和推理文本演化可视化认知精化过程，增强方法可信度。

## 8. 不足与局限
- **固定迭代步数**：当前使用固定的T=3，无法自适应任务复杂度；未来可探索动态提前终止或自适应步数。
- **教师模型手动选择**：教师大小和顺序需人工设定，未实现自动化或自适应选择，可能对特定任务非最优。
- **资源报告不完整**：未提供总训练GPU小时数或能量消耗，难以评估实际计算成本。
- **统计显著性不足**：主要结果未报告多次运行的标准差或置信区间，仅单次运行（尽管使用固定分割），可能影响结果可靠性。
- **模型规模有限**：学生模型仅为0.5B，未测试在更大模型（如7B）上的有效性，泛化性待验证。
- **未涉及安全与偏见**：未系统分析渐进蒸馏可能引入教师偏差或放大有害内容的风险，尽管在影响声明中提及。
- **局限性自我承认**：作者在Conclusion中明确指出固定T和手动选择教师的限制，并建议未来探索RL驱动的动态控制。

（完）
