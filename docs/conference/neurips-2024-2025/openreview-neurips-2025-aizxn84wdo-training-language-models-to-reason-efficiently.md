---
title: Training Language Models to Reason Efficiently
title_zh: 训练语言模型高效推理
authors: "Daman Arora, Andrea Zanette"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AiZxn84Wdo"
tags: ["query:ns-xai"]
score: 4.0
evidence: 训练大模型高效推理，与可解释性间接相关
tldr: 该论文通过训练大推理模型减少不必要的计算开销，提高推理效率。虽然涉及大模型推理，但核心目标是部署成本优化，而非可解释性或神经符号集成。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1363, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1399, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1280, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 876, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1431, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1297, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1437, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1431, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1438, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1435, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aizxn84wdo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1417, \"height\": 711, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1001, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 525, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1041, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1008, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 990, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1026, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1028, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1007, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 990, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 974, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 938, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1008, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 574, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 570, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1301, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 675, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aizxn84wdo/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 993, \"height\": 343, \"label\": \"Table\"}]"
motivation: 大模型推理成本高，需要降低部署开销。
method: 训练模型在保持性能同时最小化推理中的冗余计算。
result: 在多个推理任务上降低了推理成本，保持了准确率。
conclusion: 高效推理训练是LLM实用化的重要方向，但未涉及可解释性。
---

## Abstract
Scaling model size and training data has led to great advances in the performance of Large Language Models (LLMs). However, the diminishing returns of this approach necessitate alternative methods to improve model capabilities, particularly in tasks requiring advanced reasoning. Large reasoning models, which leverage long chain-of-thoughts, bring unprecedented breakthroughs in  problem-solving capabilities but at a substantial deployment cost associated to longer generations. Reducing inference costs is crucial for the economic feasibility, user experience, and environmental sustainability of these models.

In this work, we propose to train large reasoning models to reason efficiently. Our method incentivizes models to minimize unnecessary computational overhead while largely maintaining accuracy, thereby achieving substantial deployment efficiency gains. It  enables the derivation of a family of reasoning models with varying efficiency levels, controlled via a single hyperparameter. Experiments on two open-weight large reasoning models demonstrate significant reductions in inference cost while preserving most of the accuracy.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义
大语言模型通过扩大模型和数据规模已取得显著进步，但收益递减；而大型推理模型（如 OpenAI o1、DeepSeek-R1）通过生成长链思维（Chain-of-Thought）实现更强的推理能力，代价是推理阶段的巨大计算开销（Attention 的二次复杂度 + KV Cache 的线性增长）。这篇论文关注的核心问题是：**如何在保持高准确率的前提下，显著降低推理模型的计算成本**。其整体意义在于为大规模部署推理模型提供经济可行、用户体验好且环境可持续的方案。

## 2. 论文提出的方法论
**核心思想**：通过强化学习训练模型，在生成正确答案的同时最小化不必要的 token 数量，从而在推理时更高效地“思考”。  
**关键技术细节**：
- 修改奖励函数，增加长度惩罚项：  
  `E[1{y = y*}(1 - α · f(LEN(y)))]`
  - 其中 `y*` 是正确答案，`f` 是标准化后的长度函数（基于 per-prompt 的均值和标准差的 sigmoid 映射），`α ∈ [0,1)` 是控制效率-准确率权衡的超参数。
- 使用在线 RL 优化（PPO + RLOO 优势估计器），无需额外价值网络。
- 每 prompt 采样 8 个回复，根据长度惩罚奖励，通过策略梯度更新模型。

**公式/算法流程**：  
1. 对每个 prompt 采样多个回复，计算每个回复的奖励 `R = 正确性 × (1 - α·f(长度))`。  
2. 使用 RLOO 估计优势：`A(y_i) = R(y_i) - 1/(n-1) Σ_{j≠i} R(y_j)`。  
3. 用 PPO 目标函数更新模型参数（KL 散度正则化）。  
4. 通过调节 α 获得不同效率水平的模型家族。

## 3. 实验设计
- **数据集**：
  - 训练集：Numina Math 的子集（3.2k prompts，含 MATH、cn_k12、AIME、AoPS、Olympiad 等，筛选出有数值答案的问题）。
  - 评估集：GSM8K（小学级，k=1）、MATH500（k=3）、AIME2024（竞赛级，k=10），以及 CommonSenseQA 和 Logical Deduction（来自 BIG-Bench，验证鲁棒性）。
- **基准模型**：DeepSeek-R1-Distill-Qwen-1.5B 和 7B。
- **基线方法**：
  - Generation Cutoff（强制截断 token 上限）
  - Rejection Sampling + SFT（选最短正确回复进行监督微调）
  - DPO（基于最长/最短正确回复对进行偏好优化）
  - O1-Pruner（并发工作，离线 RL 方法）
- **评价指标**：归一化准确率（相对 Distill 模型）和归一化 token 数。
- **超参数**：α 取 0, 0.05, 0.1, 0.2, 0.4；每个配置 3 个随机种子。

## 4. 资源与算力
论文明确说明：
- 1.5B 模型使用 **4 个 GH200 GPU**（1 个低密度节点）。
- 7B 模型使用 **8 个 GH200 GPU**（2 个节点各 4 GPU）。
- 训练约 **20 小时**，共 100 个 RL 步骤（约 200 次梯度更新）。
- 使用 ZeRO Stage 2（1.5B）和 Stage 3 + 激活检查点（7B），精度 bfloat16。
- 代码和模型已公开在 GitHub：https://github.com/Zanette-Labs/efficient-reasoning。

## 5. 实验数量与充分性
- **实验数量**：两个模型规模（1.5B 和 7B）×5 个 α 值 ×3 种子，共约 30 个主要模型；加上多个基线（SFT、DPO、Cutoff、O1-Pruner）和消融实验（advantage normalization、base model 计数任务）。
- **覆盖面**：评估了数学推理（3 个标准数据集）和常识/逻辑推理（2 个额外数据集），验证跨域泛化。
- **公平性**：所有模型在相同温度（0.6）、相同 token 上限（32K）下评估；基线方法经过学习率调优；结果报告平均值和标准差（3 种子）。
- **充分性**：实验设计较为全面，消融分析（如 advantage normalization 的影响、长度惩罚对 base model 的影响）增强了结论的可靠性。但缺少对更大模型（>=30B）的验证，且仅在数学为主的训练集上训练，可能限制泛化。

## 6. 论文的主要结论与发现
- 所提方法能有效在准确率和计算成本间做平滑权衡：通过调整 α 可得到一系列不同效率的模型。
- 例如 7B 模型在 MATH500 上减少 36% token 仅损失 2.2% 准确率；在 GSM8K 上减少 83% token 仅损失 1.7% 准确率；在 AIME2024 上减少 27% token 损失约 4%。
- **难度自适应**：模型对简单问题压缩更多（如 GSM8K），对困难问题保留更长推理（如 AIME），验证了方法能根据问题难度分配推理预算。
- 相比 SFT 和 DPO，在线 RL 训练的模型在相同 token 数下准确率更高。
- 无长度惩罚时（α=0）也有长度减少，原因是当前 RL 实现（如 OpenRLHF）的 RLOO 损失对短序列有偏置；去除偏置后长度不再减少（不损害方法有效性）。
- 压缩后的模型仍比非推理模型（Instruct）更忠实（faithfulness），但随压缩程度增加忠实性有所下降。
- 定性分析显示压缩后的模型减少了回溯、验证、探索等宏行为。

## 7. 优点
- **简单有效**：只需在标准 RL 实现中修改奖励函数（几行代码），即可获得显著效率提升。
- **可控性**：通过单一超参数 α 可在部署时灵活选择效率-准确率折中点。
- **训练高效**：仅需 100 个 RL 步骤（约 20 小时），学术资源即可复现。
- **理论支撑**：在简化假设下证明最优解会输出最短正确回复，并保持 100% 准确率。
- **开源自包含**：代码、模型和实验配置全部公开，可复现性强。
- **分析全面**：不仅报告了精度和 token 数，还分析了忠实性、思维链行为变化、归一化影响等。

## 8. 不足与局限
- **实验规模局限**：仅测试了 1.5B 和 7B 模型，未在更大参数量（>=30B）上验证；训练数据仅来自数学推理，可能不适用于其他领域（尽管在常识/逻辑数据集上验证了鲁棒性，但训练集仍偏数学）。
- **精确控制困难**：α 只能相对控制效率，不能精确指定目标生成长度；针对性问题已被后续工作（Aggarwal & Welleck, 2025）解决。
- **性能损失**：即使 α=0.1 也会引入小幅准确率下降（约 2%），并非完全无损。
- **训练复杂性**：在线 RL 比 SFT 或 DPO 实现更复杂（需要多轮采样、奖励计算），对资源有一定要求。
- **忠实性下降**：随着压缩加剧，模型的忠实程度降低（从 0.622 降至 0.480 左右），可能影响对推理过程的可信度。
- **基线评估局限**：O1-Pruner 仅在 7B 模型上做了对比，且论文未明确给出所有基线超参数的详细调优过程（除学习率外）。
- **统计不确定性**：3 个种子均方根误差在部分设置下较大（如 1.5B AIME 的 token 标准差约 2000），表明训练可能存在不稳定性。

（完）
