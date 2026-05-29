---
title: Training Large Language Models to Reason Efficiently
title_zh: 训练大语言模型高效推理
authors: "Daman Arora, Andrea Zanette"
date: 2025-01-24
pdf: "https://openreview.net/pdf?id=hSAlC1SgcY"
tags: ["query:ns-xai"]
score: 6.0
evidence: 关注提升大语言模型的推理效率
tldr: 针对大语言模型推理时计算开销大的问题，提出一种训练方法使模型在达到目标精度时使用更少的测试时计算资源。该方法在保持推理性能的同时显著节省计算成本，有助于实现更高效的大模型推理。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1798, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1784, \"height\": 982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1790, \"height\": 972, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 804, \"height\": 836, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 777, \"height\": 1176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hsalc1sgcy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1613, \"height\": 1534, \"label\": \"Figure\"}]"
motivation: 大语言模型推理时计算开销大，但效率同样重要。
method: 提出一种提高推理效率的训练技术，减少测试时计算量。
result: 在达到相同精度时大幅减少了计算开销。
conclusion: 该方法在保证推理性能的同时提升了计算效率。
---

## Abstract
Training Large language models to perform advanced reasoning has endowed them with new capabilities to solve complex problems. These models spend additional compute at test time  to tackle problems that require careful reasoning.	
However, it is equally important that these model reason efficiently, i.e., that they solve the task at hand by utilizing the least possible amount of compute at test time.
In this paper we introduce a new technique to improve the reasoning efficiency of reasoning models, one that leads to a substantial saving in terms of compute to reach a target level of accuracy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型通过扩展模型大小和训练数据取得显著进步，但回报递减。前沿推理模型（如 OpenAI o1、DeepSeek-R1）通过长思维链在复杂推理任务上实现突破，但推理时生成大量 tokens 导致高昂部署成本（注意力机制 O(n²) 复杂度、KV缓存线性增长）。
- **核心问题**：如何降低推理模型的计算开销，同时尽可能保持准确率，以提升经济可行性、用户体验和环境可持续性。
- **目标**：训练模型根据任务复杂度动态分配推理计算量，对于简单问题使用简短推理，对于困难问题投入更多计算，从而在保持准确性的前提下最小化不必要的推理成本。

## 2. 论文提出的方法论

### 核心思想
- 使用强化学习（RL）训练模型，在奖励函数中引入长度惩罚，鼓励模型产生正确但更短的响应。
- 通过单个超参数 α 控制效率-准确率权衡，α=0 时退化为标准 RL 准确率目标，α 增大则惩罚更强。

### 关键技术细节
- **目标函数**：  
  \[
  \mathbb{E}\left[ \mathbf{1}\{z = z^*\} \left(1 - \alpha f(\text{LEN}(z))\right) \right]
  \]
  其中 \(f\) 使用 sigmoid 进行软裁剪，并针对每个 prompt 进行长度归一化（减去正确响应的平均长度，除以标准差），确保长响应不会被过度惩罚。
- **优化方法**：使用 PPO with RLOO（REINFORCE Leave One Out）优势估计器，避免额外的值网络。每个 prompt 采样 n 个响应（实验中 n=8），优势估计为：
  \[
  A(y_i, x) = R(y_i, x) - \frac{1}{n-1} \sum_{j\neq i} R(y_j, x)
  \]
  其中 \(R\) 为带长度惩罚的奖励。
- **重要设计**：不进行优势归一化。消融实验表明，标准化优势会导致长度下降过快、准确率急剧下降（图5）。
- **算法流程**：对于每个 prompt，从当前策略采样多个响应，计算每个响应的奖励（正确性 + 长度惩罚），使用 RLOO 估计优势，然后通过 PPO 更新模型参数。

## 3. 实验设计

### 使用的数据集
- **训练集**：从 Numina Math 数据集中选取 3.2k 提示（包含 MATH、cn_k12、AIME、AoPS、Olympiad 子集），仅保留有数值答案的问题。
- **测试集**（按难度递增）：
  - **GSM8K**：小学级数学题，评估时 k=1。
  - **MATH500**：标准数学基准，评估时 k=3。
  - **AIME 2024**：竞赛级数学题，仅 30 题，评估时 k=10。

### 对比的基线方法
1. **Generation Cutoff**：在 vLLM 生成时施加最大 token 限制（8K/16K/20K/24K/32K），超限则得分为 0。
2. **Rejection Sampling + SFT**：从原始模型生成 8 个响应，选取最短的正确响应进行监督微调（SFT）。
3. **DPO**：使用最长和最短的正确响应构成偏好对，进行直接偏好优化。

### Benchmark
- 主要指标：准确率（pass@k）和平均生成 token 数（推理成本）。
- 实验使用 DeepSeek-R1-Distill-Qwen-1.5B 和 DeepSeek-R1-Distill-Qwen-7B 两个开源推理模型作为基础。

## 4. 资源与算力

- **硬件**：
  - 1.5B 模型：4 块 GH200 GPU（1 个低密度节点）。
  - 7B 模型：8 块 GH200 GPU（2 个低密度节点，每节点 4 GPU）。
- **软件**：基于 OpenRLHF 框架，使用 ZeRO Stage 2（1.5B）或 Stage 3 + 激活检查点（7B），精度 bfloat16。
- **训练设置**：
  - 总迭代数：100 RL 迭代（约 200 个梯度更新）。
  - 每迭代：32 个 prompt，每个 prompt 生成 8 个响应，全局 batch size 128。
  - 学习率：1.5B 为 5e-6，7B 为 2e-6；优化器 Adam。
  - vLLM 最大上下文 32K，生成温度 1。
- **论文未明确说明总训练时间**，但指出仅需 100 迭代即可达到有效结果，计算成本相对较低。

## 5. 实验数量与充分性

- **主要实验**：对 1.5B 和 7B 模型分别训练了 5 个 α 值（0, 0.05, 0.1, 0.2, 0.4），在 3 个测试集上评估准确率和 token 数。共 5×2×3 = 30 个主要结果点（图2、图3、附录图6）。
- **消融实验**：比较优势归一化 vs 不归一化（图5），展示了训练动态（图4），以及定性示例（附录A）。
- **实验充分性**：覆盖了从简单（GSM8K）到极难（AIME）的多个难度级别，对比了简单截断、SFT、DPO 等基线。实验设计客观，使用相同训练集和评估方式，温度、token 限制等超参数一致。但仅聚焦于数学推理领域，未涵盖其他推理任务（如编程、科学推理）。

## 6. 论文的主要结论与发现

- **方法有效**：提出的 RL 训练能平滑地实现准确率与推理成本之间的权衡。例如：
  - 7B 模型在 MATH 上，α=0.1 时 token 减少 30%，准确率仅降 1%。
  - 在 AIME 上，α=0.2 时 token 减少 30%，准确率降 2%。
  - 在 GSM8K 上，α=0.2 时 token 减少高达 77%（与 α=0 相比），准确率基本维持。
- **模型学会动态适应**：简单问题（如 1+1）能快速回答，困难问题投入更多计算。
- **即使 α=0（无长度惩罚）**，长度也有所减少，可能是因为这些蒸馏模型未经过 RL 训练。
- **SFT 和 DPO 基线效果不佳**，甚至不如简单的生成截断基线。
- **优势归一化会破坏训练**，导致长度和准确率均快速下降。

## 7. 优点

- **方法简单高效**：仅需在标准 RL 奖励函数中增加长度惩罚（少量代码修改），且只需约 100 RL 迭代即可完成训练，计算资源需求相对较低。
- **可调性**：通过单一超参数 α 控制效率-准确率权衡，能生成一系列不同效率级别的模型。
- **动态推理**：模型能根据问题难度自适应调整推理长度，无需外部控制器。
- **正交兼容**：与系统级优化（如投机解码、vLLM）和模型级优化（剪枝、量化）可结合使用。
- **定性示例直观**：展示了“1+1”问题的回答长度从数百 token 减少到几十 token。

## 8. 不足与局限

- **复杂性**：RL 训练流程比 SFT 或 DPO 更复杂，需要多步采样和优势估计，可能增加工程实现难度。
- **缺乏精确长度控制**：超参数 α 无法精确指定目标 token 数，可能不适合对延迟有严格要求的应用。
- **领域局限性**：实验仅针对数学推理任务，未评估在编程、科学推理、通用问答等领域的泛化能力。
- **基础模型依赖**：以 DeepSeek-R1-Distill 系列为起点，对其他推理模型（如 QwQ、Kimi k1.5）的通用性未验证。
- **性能陷阱**：α=0.4 时准确率下降显著，表明过强的长度惩罚可能损害模型的有效学习。
- **训练资源需求**：虽然迭代数少，但 7B 模型仍需 8 块 GH200 GPU，对一般研究团队仍有门槛。

（完）
