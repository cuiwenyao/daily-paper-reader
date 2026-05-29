---
title: Understanding Chain-of-Thought in LLMs through Information Theory
title_zh: 通过信息论理解大语言模型的思维链
authors: "Jean-Francois Ton, Muhammad Faaiz Taufiq, Yang Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=IjOWms0hrf"
tags: ["query:ns-xai"]
score: 8.0
evidence: 信息论方法评估大模型思维链推理
tldr: 本文从信息论角度形式化大语言模型的思维链推理，通过量化每一步的信息增益来识别推理失败，无需标注数据。在简易算术任务上验证了有效性，为理解大模型推理过程提供新视角。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 796, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1654, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 554, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1031, \"height\": 2095, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1044, \"height\": 2096, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1042, \"height\": 2091, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 888, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 886, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 889, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 441, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1714, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1024, \"height\": 239, \"label\": \"Table\"}]"
motivation: 现有思维链评估需要标注数据或无法准确识别中间步骤错误。
method: 提出信息论框架，量化每步信息增益以检测失败模式。
result: 无需标注数据即可准确识别推理失败，降低假阳性率。
conclusion: 信息增益是评估思维链的有效指标，有助于提升大模型推理可解释性。
---

## Abstract
Large Language Models (LLMs) have shown impressive performance in complex reasoning tasks through the use of Chain-of-Thought (CoT) reasoning, allowing models to break down problems into manageable sub-tasks. However, existing CoT evaluation techniques either require annotated CoT data or fall short of accurately assessing intermediate reasoning steps, leading to high rates of false positives. In this paper, we formalize CoT reasoning in LLMs through an information-theoretic lens. Specifically, our framework quantifies the `information gain' at each reasoning step, enabling the identification of failure modes in LLMs without the need for expensive annotated datasets. We demonstrate the efficacy of our approach through extensive experiments on toy arithmetic, GSM8K and PRM800k datasets, where it significantly outperforms existing outcome-based methods by providing more accurate insights into model performance on individual tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：通过信息论理解大语言模型的思维链

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）在复杂推理任务中表现出色，尤其是通过思维链（Chain-of-Thought, CoT）将问题分解为中间子任务。然而，现有的 CoT 评估方法要么需要昂贵的人工标注（如过程监督），要么仅依赖最终答案的正确性（如结果奖励模型、Math-Shepherd），这会导致高假阳性率——尤其在中间步骤正确但最终答案错误，或中间步骤错误但最终答案正确的场景下，无法准确识别推理失败的位置。
- **研究动机**：避免对中间步骤的标注依赖，同时能够提供比最终结果更精细的步骤级评估，从而揭示模型的真实推理能力与失败模式。
- **整体含义**：论文从信息论视角形式化 CoT 推理，通过量化每一步对预测最终正确答案的“信息增益”来识别模型在何处出错。该方法无需步骤级标注，仅需 prompt 和正确答案数据即可实现。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程

### 核心思想
- 每个正确的推理步骤应提供有助于预测最终正确答案（Y）的信息。如果某一步骤没有增加对 Y 的预测信息（即信息增益为0或负），则表明该步骤可能是错误的或无关的。
- 通过条件互信息定义信息增益：\( I(Y; X^M_j \mid X^M_{j-1}) \)，其中 \( X^M_j \) 是模型在第 j 步的输出（累积的 CoT 状态），\( X^M_{j-1} \) 是上一状态。

### 关键技术细节
1. **任务分解与形式化**：
   - 定义初始状态 \( X_0 \)（如问题中的数值）和任务序列 \( \lambda = \lambda_1 \circ \cdots \circ \lambda_T \)（如加法、乘法等子任务）。
   - 构建更新规则 \( X_t = \Lambda(X_{t-1}, \lambda_t) \)，递归生成中间状态。
   - 引入“原始任务”（primitive tasks）和“不可识别性”（unidentifiability）概念：若模型训练数据中不包含某子任务，则该任务对模型是不可识别的，后续步骤无法提供有效信息。

2. **信息增益估计**：
   - 利用公式：\( I(Y; X^M_j \mid X^M_{j-1}) = E[\log p(Y \mid X^M_j)] - E[\log p(Y \mid X^M_{j-1})] \)。
   - 实际计算时，训练一个“监督模型”（supervisor model，如 GPT-2 或 Llama-3-8B）来近似 \( p(Y \mid X^M_t) \)。通过比较交叉熵损失的变化来估计信息增益：
     \[
     \text{信息增益} \approx \text{CE Loss}(Y, g_{\text{sup}}(X^M_{j-1})) - \text{CE Loss}(Y, g_{\text{sup}}(X^M_j))
     \]
   - 对于单样本检测，采用类似公式：\( \log p(Y \mid X^M_j) - \log p(Y \mid X^M_{j-1}) \)，若为负则表明该步未提供有用信息。

3. **检测不可识别子任务**：
   - 定理：若在第 k 步遇到不可识别的子任务，则对于所有 \( j \geq k \)，有 \( Y \perp\!\!\!\perp X^M_j \mid X^M_{j-1} \)，即信息增益为0。因此，通过观测信息增益的骤降可定位错误步骤。

### 算法流程（文字描述）
1. 收集 prompt 和正确最终答案 \( D_\lambda = \{(x_0^i, y^i)\} \)。
2. 对于每个 prompt，让目标 LLM 生成 CoT 序列 \( X^M_0, X^M_1, \ldots, X^M_T \)。
3. 训练一个监督模型 g_sup，输入为部分 CoT（\( X^M_t \)），输出预测 Y 的分布。
4. 计算每个步骤 j 的样本级或聚合级信息增益：
   - 对每个样本：计算 \( \text{IG}_j = \log p(Y \mid X^M_j) - \log p(Y \mid X^M_{j-1}) \)。
   - 对数据集：计算平均交叉熵损失差。
5. 若 \( \text{IG}_j < 0 \) 或接近0，则标记步骤 j 为可疑错误步骤。

## 3. 实验设计

### 数据集与场景
1. **玩具数据（Toy Arithmetic）**：设计 5 个步骤的整数向量变换（交换、累积和、反向累积和、排序乘法、差值计算），人为在特定步骤引入错误（随机噪声或特定条件触发），生成 5 个不同的“LLM”模型（LLM 1~5），每个模型仅在编号对应的步骤上有概率出错。
2. **Llama-3-8B 算术运算**：使用真实模型 Llama-3-8B，在数字对 (x,y) 上执行“3x”“2y”“3x+2y”三步计算。步骤 1 和 2 正确率高（80%,98%），步骤 3 正确率低（42%），且错误与数值大小相关。
3. **GSM8K 控制实验**：使用 GPT-4 生成 CoT，故意将“乘法”步骤全部改为错误，并引入“减法”与错误答案的伪相关（即只有包含乘法和减法的 CoT 才出错）。控制数据集使得乘法和减法总是同时出现，导致 ORM 无法区分。
4. **PRM800K 数据集**：来自 OpenAI 的 Math 数据集，包含人工标注的每步标签（+1正确，-1错误，0中性）。使用该数据评估方法在自然错误上的表现。

### 对比基线
- **Outcome Reward Model (ORM)**：训练分类器，根据部分 CoT 预测最终答案正确的概率。
- **Math-Shepherd (MS)**：使用同一模型作为 completer，从当前步骤开始生成多条补全，统计其中得到正确最终答案的比例。

### Benchmark 与评估指标
- **聚合级**：显示每步的信息增益/正确概率/正确完成比例的热力图。
- **样本级**：使用 ACC（准确率）、TPR（真正率）、FPR（假正率）评估步骤级别错误检测效果。

## 4. 资源与算力

- 论文未明确提及训练 supervisor model 和进行实验所使用的具体 GPU 型号、数量或总训练时长。
- 仅提到在玩具数据中使用 GPT-2 作为 supervisor，在 Llama-3-8B 和 GSM8K 实验中使用 Llama-3-8B 作为 supervisor（LoRA 微调），在 PRM800K 实验中使用 GPT-2 SFT。
- 未提供详细的算力消耗报告。

## 5. 实验数量与充分性

- **实验组数**：总共涉及 4 个主要实验（玩具数据、Llama-3-8B 算术、GSM8K 控制、PRM800K），每个实验均包含方法（IG）与两个基线的对比。玩具数据中设计了 5 个不同的 LLM 模拟，每个 LLM 评估聚合级和样本级性能。样本级检测给出了 ACC、TPR、FPR 等表格。
- **充分性**：实验覆盖了从简单受控场景到复杂真实场景过渡，且针对基线的弱点（伪相关、依赖输入特征）设计了专门的对照组（如 LLM 3 的条件错误、GSM8K 中的混淆设计），证明本方法在基线失败的场景下仍有效。PRM800K 实验验证了在自然错误数据上的泛化性。
- **客观性**：对比方法均采用公开可复现的实现，且实验设定公平（如 MS 使用相同模型作为 completer，不引入更强的 verifier）。但未进行消融实验（如不同 supervisor 模型大小的影响、信息增益阈值敏感性），且缺少与其他基于过程监督方法（如 PRM）的直接量化对比（仅定性比较）。

## 6. 论文的主要结论与发现

- **信息增益可以准确识别错误的 CoT 步骤**：在玩具数据中，IG 能始终定位到被故意引入错误的步骤，而 ORM 和 MS 在 LLM 3（条件错误）中失败。
- **优于现有方法**：在样本级检测中，IG 的 ACC 和 TPR 显著高于 ORM 和 MS，FPR 更低。例如在 Llama-3-8B 实验中，IG 的 ACC=0.51, TPR=1.0, FPR=0.02；ORM 的 FPR=0.07，MS 的 FPR=0.86。
- **无需标注中间步骤**：仅需正确最终答案，即可获得步骤级错误定位。
- **适用于非链式推理（如回溯、自纠正）**：论文声称框架可自然扩展至 O1/R1 风格的探索性推理，并通过 PRM800K 实验验证——被标注为负面的步骤信息增益低，正面的步骤信息增益高。

## 7. 优点

1. **无监督方式**：无需人力标注中间步骤，大大降低了成本，易于扩展。
2. **理论基础扎实**：建立在信息论（条件互信息）和任务可识别性形式化上，提供了严格的理论保证（定理证明）。
3. **更强的鲁棒性**：可应对基线方法无法处理的伪相关和输入依赖错误，如 ORM 在使用输入数值即可判断最终正确性时失效，IG 则不受影响。
4. **灵活扩展**：不仅适用于线性 CoT，也适用于复杂的探索性推理，并且可以推广到数学之外的领域（如 Blocks World、常识问答）。
5. **样本级和聚合级双重粒度**：既可用于数据集层面推测哪些子任务困难，也可用于单个 prompt 的错误步骤诊断。

## 8. 不足与局限

1. **需额外训练 supervisor 模型**：虽然避免了步骤级标注，但仍需训练一个模型来估计 p(Y | X^M_t)，这本身也是计算开销，且 supervisor 的性能影响最终检测效果。
2. **步骤划分需人工定义**：方法仍需将模型输出划分成步骤，并区分不同子任务（如加法、乘法）。该步骤依赖一定的手动规则或解析，可能不够通用。
3. **实验覆盖有限**：未对 supervisor 模型的规模和训练数据量进行消融，也未比较不同信息增益阈值的影响。此外，仅在数学/算术数据集上验证，缺乏在逻辑、常识等领域的大规模实验。
4. **未与过程监督（PRM）直接对比**：虽然定性说明了 PRM 需要标注，但未实验在相同资源条件下 IG 与 PRM 的性能差异。
5. **理论假设可能受限**：Assumption 3.1 假设不可识别的步骤之后所有步骤均无信息增益，但在实际中，模型可能通过自纠正恢复，这时后续步骤仍可能有信息增益，虽然论文声称框架能处理，但理论推导未明确涵盖纠错场景。
6. **算力信息缺失**：未提供 GPU 型号、训练时长等，不利于复现和成本评估。

（完）
