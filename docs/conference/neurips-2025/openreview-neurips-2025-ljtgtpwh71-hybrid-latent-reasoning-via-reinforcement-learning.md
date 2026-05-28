---
title: Hybrid Latent Reasoning via Reinforcement Learning
title_zh: 基于强化学习的混合潜在推理
authors: "Zhenrui Yue, Bowen Jin, Huimin Zeng, Honglei Zhuang, Zhen Qin, Jinsung Yoon, Lanyu Shang, Jiawei Han, Dong Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=LjtgTpWH71"
tags: ["query:ns-xai"]
score: 5.0
evidence: 利用强化学习实现LLM混合潜在推理
tldr: 该论文提出混合潜在推理方法，通过强化学习同时利用潜状态和显式链式推理。方法克服了潜在推理与自回归生成的冲突，实验表明在多项推理任务上优于纯CoT和纯潜在推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 726, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1356, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1378, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1453, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1453, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1453, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ljtgtpwh71/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1453, \"height\": 428, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1319, \"height\": 901, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1335, \"height\": 903, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1251, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1116, \"height\": 808, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1087, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1281, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1251, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1107, \"height\": 527, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ljtgtpwh71/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 918, \"height\": 494, \"label\": \"Table\"}]"
motivation: 潜在推理与自回归生成不兼容且依赖CoT训练。
method: 通过强化学习训练混合推理策略。
result: 在推理任务上优于纯CoT和纯潜在推理。
conclusion: 为LLM潜在推理提供了有效方案。
---

## Abstract
Recent advances in large language models (LLMs) have introduced latent reasoning as a promising alternative to autoregressive reasoning. By performing internal computation with hidden states from previous steps, latent reasoning benefit from more informative features rather than sampling a discrete chain-of-thought (CoT) path. Yet latent reasoning approaches are often incompatible with LLMs, as their continuous paradigm conflicts with the discrete nature of autoregressive generation. Moreover, these methods rely on CoT traces for training and thus fail to exploit the inherent reasoning patterns of LLMs. In this work, we explore latent reasoning by leveraging the intrinsic capabilities of LLMs via reinforcement learning (RL). To this end, we introduce hybrid reasoning policy optimization (HRPO), an RL-based hybrid latent reasoning approach that (1) integrates prior hidden states into sampled tokens with a learnable gating mechanism, and (2) initializes training with predominantly token embeddings while progressively incorporating more hidden features. This design maintains LLMs' generative capabilities and incentivizes hybrid reasoning using both discrete and continuous representations. In addition, the hybrid HRPO introduces stochasticity into latent reasoning via token sampling, thereby enabling RL-based optimization without requiring CoT trajectories. Extensive evaluations across diverse benchmarks show that HRPO outperforms prior methods in both knowledge- and reasoning-intensive tasks. Furthermore, HRPO-trained LLMs remain interpretable and exhibit intriguing behaviors like cross-lingual patterns and shorter completion lengths, highlighting the potential of our RL-based approach and offer insights for future work in latent reasoning.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义 (研究动机与背景)

- **研究动机**：大型语言模型(LLM)的潜在推理（latent reasoning）通过利用连续隐藏状态进行内部计算，相比离散的思维链(CoT)能获取更丰富的信息。然而，现有潜在推理方法存在两大局限：(1) 与LLM的离散自回归生成不兼容，直接将隐藏状态作为输入会降低生成质量；(2) 严重依赖CoT轨迹进行训练，未能利用LLM本身固有的推理能力，且训练成本高。
- **核心问题**：如何在不依赖CoT注释的前提下，让LLM自主发展出同时利用离散token和连续潜在表示的混合推理能力，从而提升推理性能和泛化性。
- **整体含义**：提出一种基于强化学习(RL)的混合潜在推理框架——混合推理策略优化(HRPO)，首次使LLM通过RL自主学习混合推理，兼顾了可解释性与生成质量，为潜在推理提供了高效、可扩展的新范式。

---

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过可学习的门控机制，将前一步的隐藏状态逐渐融合到采样token的嵌入中，形成混合输入；并利用强化学习（REINFORCE风格）优化策略，使LLM自主学会在离散和连续表示之间切换，实现混合推理。
- **关键技术细节**：
  - **隐藏状态投影**：为避免隐藏状态与嵌入空间不匹配，首先通过输出概率加权插值将隐藏状态映射到嵌入空间：  
    \[
    h_{t+1} = \frac{W_e^T p_{t+1}}{\|p_{t+1}\|}, \quad p_{t+1} = \text{softmax}\left(\frac{\text{Head}(\hat{h}_t)}{\tau}\right)
    \]  
    其中 \(\tau\) 为温度参数。
  - **门控机制**：仅在推理阶段（<think>...</think>）启用，控制隐藏状态注入比例：  
    \[
    r_t = \sigma(W_a\hat{e}_{t+1}+b_a),\quad i_t = \sigma(W_x\hat{e}_{t+1}+b_x),\quad a_t = \exp(-c\cdot\text{softplus}(\Lambda)\odot r_t)
    \]  
    \[
    e_{t+1} = \begin{cases}
    a_t \odot \hat{e}_{t+1} + \sqrt{1-a_t^2} \odot (i_t \odot h_{t+1}), & t\in\text{think} \\
    \hat{e}_{t+1}, & t\notin\text{think}
    \end{cases}
    \]  
    其中 \(\hat{e}_{t+1}\) 是采样token嵌入，\(\Lambda\) 可学习。初始化时 \(a_t\to 1\)，以token嵌入为主，训练中逐步增加隐藏特征。
  - **HRPO优化**：采用组相对奖励标准化(RLOO风格)，生成 \(g\) 条混合轨迹，计算组内标准化优势，并使用KL散度正则化维持策略多样性。策略梯度目标：  
    \[
    \nabla_\theta J_{\text{HRPO}} = \mathbb{E}\left[\frac{1}{g}\sum_{i=1}^g\frac{1}{|y_i|}\sum_{t=1}^{|y_i|}\nabla_\theta\log\pi_\theta(y_{i,t}|\cdot)\hat{A}_{i,t}\right] - \beta\nabla_\theta D_{\text{KL}}[\pi_\theta\|\pi_{\text{ref}}]
    \]  
    其中 \(\hat{A}_{i,t}\) 通过组内标准化的奖励得到，\(\beta\) 控制KL项权重。
- **算法流程**（文字描述）：
  1. 对每个输入查询，使用当前策略生成 \(g\) 条混合推理轨迹（包含离散token和隐藏状态序列）。
  2. 对每条轨迹，仅根据答案部分的离散token计算二元奖励（正确=1，错误=0）。
  3. 在同一组内标准化奖励获得优势估计。
  4. 在推理跨度内，利用门控机制计算token log概率（依赖于历史token和隐藏状态）。
  5. 使用REINFORCE梯度更新策略参数，同时加入KL散度约束（参考模型基于纯token log概率计算）。
  6. 每个轨迹只用一次梯度更新，保持在线策略。

---

## 3. 实验设计：数据集、基准、对比方法

- **知识密集型任务**（5个数据集）：Natural Questions (NQ)、TriviaQA、HotpotQA、2WikiMultiHopQA (2WikiMQA)、Bamboogle。采用精确匹配(EM)评估，检索顶3维基百科文档。
- **STEM推理任务**（5个数据集）：GSM8k、MATH、MATH500、MMLU-STEM、ARC-Challenge。采用准确率(Accuracy)评估。
- **对比方法**：
  - **基线方法**：直接推理(QA)、思维链(CoT)、RAG、IRCoT、Search-o1（使用7B模型）；SFT、蒸馏CoT（使用QwQ教师）。
  - **强化学习方法**：PPO、GRPO（作为核心对比对象）。
  - **潜在推理方法**（附录中）：Coconut、CODI（使用1.5B Qwen骨干）。
- **骨干模型**：Qwen2.5-Instruct 1.5B和3B（主要实验），部分对比使用7B模型。
- **训练数据**：知识任务使用NQ+HotpotQA训练集；GSM8k用其训练集；MATH系列用MATH训练集；MMLU-ST和ARC-C用相应训练集。

---

## 4. 资源与算力

- 论文在附录A中说明：使用LoRA（秩32， \(\alpha=64\)）和BF16混合精度训练，整个框架可在**单张GPU**上运行。
- **未明确说明**：具体的GPU型号（如A100、V100）、数量（仅1张）、训练总时长（未报告）。但提到使用优化内核（Unsloth）和8-bit AdamW优化器，对计算效率有优化。

---

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：2个骨干模型 × (5个知识任务 + 5个STEM任务) = 20组结果。
  - 对比方法：每个任务对比4~7种基线（包括SFT、PPO、GRPO等），共约80+组对比。
  - 消融实验（附录B）：
    - 不同潜在推理策略（Hidden States、Interpolation vs. HRPO）1组图。
    - 门控初始化 \(r_{\min}\) 对知识/STEM的影响（2个骨干 × 多任务）。
    - 温度 \(\tau\) 敏感性（2个骨干 × 多任务）。
    - 隐藏比率与完成长度动态分析（包括不同 \(r_{\min}\) 和 \(\tau\) 的训练曲线）。
  - 统计显著性检验：附录表9在STEM任务上对1.5B和3B模型做了配对t检验，报告p<0.05的显著性。
- **充分性与公平性**：
  - 实验覆盖了知识检索和数学推理两大领域，任务多样性较高。
  - 对比方法包括最新RL基线（GRPO）和潜在推理方法（Coconut、CODI），设置合理。
  - 使用相同骨干和训练设置，超参数统一。
  - 消融实验系统，揭示了门控设计、初始化等关键因素的作用。
  - 不足：统计显著性仅在部分STEM任务上报告，缺乏知识任务的显著性检验；未在更大模型（≥7B）上验证HRPO本身（仅对比了7B基线）；未见跨数据集泛化测试（如零样本）。

---

## 6. 论文的主要结论与发现

- **性能提升**：HRPO在知识和STEM任务上均超越所有对比方法（SFT、PPO、GRPO、蒸馏CoT、Coconut、CODI），在1.5B和3B骨干上分别达到平均EM 0.337和0.380（知识任务），平均准确率0.617和0.700（STEM任务），甚至匹配或超越部分7B基线。
- **混合推理有效性**：门控机制成功融合离散和连续表示，训练中隐藏比率逐渐增加，完成长度缩短，说明模型学会更高效地利用隐藏状态。
- **稳定训练**：HRPO训练曲线更平滑，收敛更快，且无奖励崩溃现象。
- **涌现模式**：HRPO产出的推理轨迹可读，出现跨语言混合（如中文+英文）、稀有token使用、更紧凑的回答等有趣行为。
- **超参数鲁棒性**：对温度 \(\tau\) 和门控初始化范围 \(r_{\min}\) 相对稳健，但知识任务偏好较小 \(r_{\min}\)（更多隐藏特征），STEM任务则呈双峰偏好。

---

## 7. 优点

- **方法创新**：首次将强化学习用于混合潜在推理，无需CoT注释，减轻了对监督数据的依赖。
- **算法设计**：可学习的门控机制有效解决了离散与连续表示的不兼容性，且逐步注入隐藏特征的设计保持了LLM的生成能力。
- **实验全面**：覆盖知识和数学两大领域，对比方法包括多种RL变体和潜在推理专用方法，消融实验系统。
- **效率与可扩展性**：使用LoRA和单GPU即可训练，计算负担低于多数潜在推理方法（如Coconut的多阶段训练）。
- **可解释性**：混合推理仍产出可读的token轨迹，比纯潜在推理更透明。
- **优异性能**：在紧凑模型（1.5B/3B）上达到甚至超过7B模型的效果。

---

## 8. 不足与局限

- **计算开销**：门控机制和多条轨迹生成增加了额外FLOPs，在线策略限制了数据复用效率。
- **实验范围限制**：仅在Qwen2.5系列1.5B/3B上验证，未在更大模型（7B/70B）或不同架构（Llama、Mistral）上测试，泛化性存疑。
- **超参数敏感**：虽然鲁棒，但门控初始化 \(r_{\min}\) 和温度 \(\tau\) 仍需手动调优，最佳设置因任务而异。
- **统计检验不完整**：知识任务的显著性未报告；STEM任务中部分对比不显著。
- **可解释性折中**：尽管token轨迹可读，但隐藏状态部分的内部计算仍难解释，可能影响故障排查。
- **潜在偏差**：二元奖励仅依赖最终答案正确性，未能区分推理过程质量，可能导致虚假相关。
- **局限说明**：论文自身在结论中坦诚了“额外计算开销、在线策略低效、连续表示透明度不足”等局限，并表示未来工作将尝试简化设计、离线策略及更先进的潜在推理技术。

---

（完）
