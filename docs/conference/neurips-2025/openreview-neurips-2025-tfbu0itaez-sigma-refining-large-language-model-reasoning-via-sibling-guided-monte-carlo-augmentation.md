---
title: "SIGMA: Refining Large Language Model Reasoning via Sibling-Guided Monte Carlo Augmentation"
title_zh: SIGMA：通过兄弟引导的蒙特卡洛增强优化大语言模型推理
authors: "Yanwei Ren, Haotian Zhang, Fuxiang Wu, Jiayan Qiu, Jiaxing Huang, Baosheng Yu, Liu Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tfbu0ITAez"
tags: ["query:ns-xai"]
score: 6.0
evidence: 利用MCTS数据增强优化LLM推理
tldr: 该论文指出传统MCTS数据增强仅保留最优路径，浪费了兄弟节点中的有用信息。提出SIGMA框架重新利用这些被丢弃的兄弟节点，生成更丰富的推理数据，从而提升LLM的推理性能。实验表明该方法有效提高了推理准确性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有MCTS数据增强丢弃了非最优路径的兄弟节点，造成信息浪费。
method: SIGMA框架保留并重新利用兄弟节点中的部分见解和错误模式，生成高质量链式推理数据。
result: 在推理任务上，SIGMA相比仅保留最优路径的方法显著提升了性能。
conclusion: 充分利用搜索树中的所有节点可以有效增强LLM推理。
---

## Abstract
Enhancing large language models by simply scaling up datasets has begun to yield diminishing returns, shifting the spotlight to data quality. Monte Carlo Tree Search (MCTS) has emerged as a powerful technique for generating high-quality chain-of-thought data, yet conventional approaches typically retain only the top-scoring trajectory from the search tree, discarding sibling nodes that often contain valuable partial insights, recurrent error patterns, and alternative reasoning strategies. This unconditional rejection of non-optimal reasoning branches may waste vast amounts of informative data in the whole search tree. We propose SIGMA (Sibling Guided Monte Carlo Augmentation), a novel framework that reintegrates these discarded sibling nodes to refine LLM reasoning. SIGMA forges semantic links among sibling nodes along each search path and applies a two-stage refinement: a critique model identifies overlooked strengths and weaknesses across the sibling set, and a revision model conducts text-based backpropagation to refine the top-scoring trajectory in light of this comparative feedback. By recovering and amplifying the underutilized but valuable signals from non-optimal reasoning branches, SIGMA substantially improves reasoning trajectories. On the challenging MATH benchmark, our SIGMA-tuned 7B model achieves 54.92\% accuracy using only 30K samples, outperforming state-of-the-art models trained on 590K samples. This result highlights that our sibling-guided optimization not only significantly reduces data usage but also significantly boosts LLM reasoning.

---

## 论文详细总结（自动生成）

# 论文总结：SIGMA: Refining Large Language Model Reasoning via Sibling-Guided Monte Carlo Augmentation

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：传统上，通过扩大数据集规模来提升大语言模型（LLM）的推理能力已逐渐遇到瓶颈（数据质量比数量更重要）。Monte Carlo Tree Search (MCTS) 被用于生成高质量的链式思维（CoT）数据，但现有方法通常只保留搜索树中得分最高的单一路径，而丢弃了所有兄弟节点（sibling nodes）。这些被丢弃的节点中往往包含部分正确的推理步骤、常见的错误模式以及替代推理策略，造成了大量有用信息的浪费。
- **动机**：如何有效利用MCTS搜索树中非最优分支的信息，进一步提升推理数据质量，从而在更少的数据量下达到更优的推理性能。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出 SIGMA (Sibling Guided Monte Carlo Augmentation) 框架，重新整合MCTS中丢弃的兄弟节点，通过语义比较和文本级反馈来优化最优推理路径。
- **关键技术细节**：
  - **MCTS 路径选择**：使用MCTS生成推理树，根据UCT公式选择最高价值的路径 \(T^* = \{p^{(1)}, p^{(2)}, \dots, p^{(D)}\}\)。
  - **兄弟节点引导的损失定义**：在每个深度 \(d\)，将选中的节点 \(p^{(d)}\) 与其兄弟节点集合 \(\{T_s\}_{s \in S(p)}\) 进行比较，定义一个结构化的文本损失 \(\mathcal{L}_{\text{text}} = \Phi(T_p, \{T_s\})\)，输出自然语言形式的对比反馈。
  - **文本梯度计算**：使用一个Critique LLM（文中使用GPT-4o-mini）作为“符号梯度”Oracle，生成自然语言方向的批评（critique）\(G\)，类似于梯度信号。
  - **文本梯度下降（TGD）**：使用一个Revise LLM，根据批评 \(G\) 对当前步骤 \(T_p\) 进行修正，得到改进版本 \(\tilde{T}_p\)。该过程逐步骤迭代，相当于一次坐标下降。
  - **整个流程**：先通过MCTS选出最佳路径，然后逐步骤利用兄弟节点生成批评，再基于批评修正路径，最终得到优化后的推理链。

## 3. 实验设计

- **数据集与基准**：
  - 训练数据：从 MATH 和 GSM8K 数据集中抽取问题，通过MCTS和SIGMA生成训练样本（15K、30K、60K）。
  - 评估基准：**In-domain**: GSM8K, MATH. **Out-of-domain**: CollegeMath, DeepMind Mathematics, OlympiadBench-Math, TheoremQA. 共计6个数学推理基准。
- **对比方法**：与多种大规模数据生成方法对比，包括 MetaMath、WizardMath、MMIQC、MathScale、RefAug、DART-Math、MathFusion 等，覆盖不同数据量（15K–2.3M）。
- **基础模型**：DeepSeekMath-7B（数学专用）、LLaMA3-8B、Mistral-7B-v0.1（通用模型），以及额外在 Qwen2.5-Math-7B 上验证。
- **评估设置**：零样本贪婪解码（温度=0），报告pass@1准确率。

## 4. 资源与算力

- **MCTS生成**：使用 Qwen2.5-Math-7B，在 RTX 4090 上约 42 GPU小时 生成15K样本的完整树。
- **精炼阶段**：使用 GPT-4o-mini（API），对于15K样本，提示词 token 数33.6M，补全 token 数11.4M，API成本 $11.7；60K样本总成本 $47.6。
- **总成本对比**：相比 DART-Math（A100：3840小时，$3456），SIGMA 总成本降低超过30倍（$106.4）。若使用开源 Qwen2.5-7B-Instruct 替换 GPT-4o-mini，总成本降低至约 $70。
- **训练硬件**：4×H100 GPU，DeepSpeed ZeRO 优化，混合精度（FP16），每设备批次8，梯度累积4，序列长度4096，AdamW优化器，余弦学习率衰减，预热3%，3个epoch。

## 5. 实验数量与充分性

- **主实验**：在三个基础模型上，分别使用15K、30K、60K样本训练，在6个基准上测试，与10+种方法对比。
- **消融实验**：包括：
  - 对比未精炼的MCTS最优路径（MCTS-15K）——SIGMA显著提升。
  - 对比使用相同查询但用GPT-4o-mini直接生成CoT（Blackbox-15K）——SIGMA更优。
  - 替换Critique&Revision模型（Qwen2.5-7B-Instruct, Qwen2.5-72B-Instruct, GPT-4o-mini）——结果表明框架对教师模型通用。
- **额外泛化实验**：在大型基座模型 Qwen2.5-Math-7B 上验证，以及常识推理任务（CommonsenseQA, StrategyQA, ARC-Challenge）上的评估。
- **充分性评价**：实验设计较为全面，覆盖多种规模、多种基座、多种对比方法，消融实验控制了数据量、生成方式、教师模型等变量，结果一致性强，支持主要结论。

## 6. 主要结论与发现

- **数据效率极高**：SIGMA-15K 击败所有30K级基线；SIGMA-30K 优于或持平60K级方法。例如，DeepSeekMath-7B 使用30K样本平均准确率48.2%，超过使用590K的DART-Math（49.4%的差距很小但数据量少20倍）。
- **一致性提升**：在三个基座模型上，SIGMA在每个数据量级别均显著优于未精炼的MCTS和黑盒CoT生成。
- **泛化性强**：在非数学推理任务（常识推理）上也取得最佳结果；在不同教师模型下均保持优势。
- **计算与成本效率**：总合成成本低于现有大规模方法数十倍。

## 7. 优点

- **创新性**：首次系统性地利用MCTS中非最优分支（兄弟节点）的信息，提出文本梯度下降优化，形成完整的数据增强流程。
- **数据质量显著提升**：仅用很少的数据量即可达到甚至超越大规模数据集的效果，解决了数据扩展瓶颈。
- **无需额外回滚或外部奖励模型**：完全依赖MCTS树内已有信息，易于集成到现有生成管线。
- **模型无关性**：Critique和Revision模型可替换为不同规模的LLM，框架通用。
- **实验充分**：多维度消融和泛化实验验证了方法的鲁棒性。

## 8. 不足与局限

- **教师模型依赖**：当前主实验使用GPT-4o-mini作为Critique&Revision模型，虽然实验证明了可替换性，但性能仍受教师能力影响。更大的教师模型（如GPT-4）可能会获得更好结果，但未探索。
- **规模局限**：仅对7B/8B模型进行全微调，未尝试更大模型（如13B、70B），结论的泛化性有待验证。
- **领域限制**：主要聚焦数学推理，虽在常识推理上验证，但其他复杂推理领域（如科学、法律、编程）尚未测试。
- **无误差条报告**：主实验结果未报告多次运行的标准差，可能影响对结果稳定性的评估。
- **训练超参数调优**：针对每个模型进行单独学习率搜索，但未报告搜索范围或敏感性分析，可能引入微小的不公平性。
- **MCTS生成参数固定**：使用了固定的树深度（16）、候选数（3）等，未探讨这些参数对最终数据质量的影响。

（完）
