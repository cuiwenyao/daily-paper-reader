---
title: "System-1.5 Reasoning: Traversal in Language and Latent Spaces with Dynamic Shortcuts"
title_zh: System-1.5推理：语言和潜空间中的动态短路遍历
authors: "Xiaoqiang Wang, Suyuchen Wang, Yun Zhu, Bang Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MNduv07wAu"
tags: ["query:ns-xai"]
score: 7.0
evidence: 大语言模型自适应推理框架，提升推理效率
tldr: 链式推理（CoT）赋予LLM系统2式推理但效率低下，而潜空间推理步处理均匀。本文提出System-1.5推理框架，通过潜空间动态短路自适应分配计算资源，在保持推理质量的同时显著提升效率，为大型模型推理技术提供新方向。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mnduv07wau/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mnduv07wau/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mnduv07wau/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 665, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mnduv07wau/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 676, \"height\": 417, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mnduv07wau/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 313, \"label\": \"Table\"}]"
motivation: 现有推理方法要么冗长（CoT）要么均匀分配计算，缺乏适应性。
method: 提出System-1.5推理，在潜空间构建动态短路路径以自适应分配推理步骤计算。
result: 实验表明在多个推理任务上达到与CoT相当精度但推理成本显著降低。
conclusion: 自适应计算分配是可解释大模型推理的重要优化方向。
---

## Abstract
Chain-of-thought (CoT) reasoning enables large language models (LLMs) to move beyond fast System-1 responses and engage in deliberative System-2 reasoning. However, this comes at the cost of significant inefficiency due to verbose intermediate output. Recent latent-space reasoning methods improve efficiency by operating on hidden states without decoding into language, yet they treat all steps uniformly, failing to distinguish critical deductions from auxiliary steps and resulting in suboptimal use of computational resources. In this paper, we propose System-1.5 Reasoning, an adaptive reasoning framework that dynamically allocates computation across reasoning steps through shortcut paths in latent space.Specifically, System-1.5 Reasoning introduces two types of dynamic shortcuts. The model depth shortcut (DS) adaptively reasons along the vertical depth by early exiting non-critical tokens through lightweight adapter branches, while allowing critical tokens to continue through deeper Transformer layers. The step shortcut (SS) reuses hidden states across the decoding steps to skip trivial steps and reason horizontally in latent space. Training System-1.5 Reasoning involves a two-stage self-distillation process: first distilling natural language CoT into latent-space continuous thought, and then distilling full-path System-2 latent reasoning into adaptive shortcut paths (System-1.5 Reasoning).Experiments on reasoning tasks demonstrate the superior performance of our method.
For example, on GSM8K, System-1.5 Reasoning achieves reasoning performance comparable to traditional CoT fine-tuning methods while accelerating inference by over 20× and reducing token generation by 91.0\% on average.

---

## 论文详细总结（自动生成）

# 论文《System-1.5 Reasoning: Traversal in Language and Latent Spaces with Dynamic Shortcuts》中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：链式推理（Chain-of-Thought, CoT）使大语言模型（LLM）具备审慎的 System-2 推理能力，但代价是大量冗余中间 token 生成，导致推理效率极低。近期的潜空间推理方法（如 Coconut、CCoT、pause token）通过直接在隐状态上操作来避免解码为语言，从而提升效率，但它们**对所有推理步骤（关键推导与辅助步骤）一视同仁**，未能按步骤复杂度动态分配计算资源，造成次优的算力利用。
- **核心问题**：如何设计一种框架，使其能根据步骤重要性（简单/关键/琐碎）自适应地在潜空间中以不同计算路径进行推理，从而在保持推理质量的同时显著提升效率？
- **整体含义**：本文提出 **System-1.5 Reasoning** 框架，在潜空间引入两种动态“短路”——深度短路（Depth Shortcut, DS）和步骤短路（Step Shortcut, SS），使模型能像人类思考一样：简单步骤快速处理（System-1），困难步骤深度思考（System-2），琐碎步骤直接跳过。

## 2. 论文提出的方法论
- **核心思想**：在潜空间中，通过两种动态短路自适应地分配垂直方向（模型层深）和水平方向（解码步骤）的计算。
- **关键技术细节**：
  - **深度短路（DS）**：在每个 Transformer 层插入一个轻量级路由-适配器模块（router-adapter）。路由模块（一层 FFN + sigmoid）输出权重 \(w\)，决定当前 token 是经由适配器分支提前退出（计算量少），还是继续通过标准 Transformer 层做深层推理。训练时输出为加权组合；推理时与预设深度退出阈值 \(\lambda_{\text{depth}}\) 比较，实现“早期退出”。
  - **步骤短路（SS）**：将前一步早期退出的隐状态直接复制到当前步的同一层，从而跳过整个解码步骤（水平方向）。避免像标准 Transformer 那样每步从头计算。训练时也采用加权组合；推理时若一步在中间层退出，则其隐状态直接供给下一步。
  - **训练过程：两阶段蒸馏**：
    1. **语言到潜空间对齐**（Language-to-Latent Alignment）：冻结教师 System-2 CoT 模型，提取最后层隐状态作为目标，训练学生 System-2 模型（使用相同的 Transformer 参数）在潜空间中进行推理，损失为 MSE 对齐 + 答案 NLL 损失。该阶段采用 teacher-forcing，避免课程学习式的复杂调度。
    2. **System-2 到 System-1.5 蒸馏**（Shortcut Learning）：冻结第一阶段得到的 Transformer 参数，仅训练各层的路由-适配器模块。利用原子思维分解（Atom-of-Thought）将 CoT 分解为有向无环图，独立节点标为非关键，派生节点标为关键。定义早期退出损失 \(L_{\text{early-exit}}\)，对非关键步骤鼓励在浅层退出（权重 \(e_{l,t}\) 随层数增大），对关键步骤鼓励深入深层。同时保留答案 NLL 损失。总损失为二者加权和。
- **公式核心**：训练时组合隐状态公式（合并 DS 和 SS）：\(h_{l,t} = (g_{l-1}(h_{l-1,t}) + g_l(h_{l,t-1})) \cdot w + f_l(h_{l-1,t})\cdot(1-w)\)，其中 \(w = R_l(h_{l-1,t})\)。

## 3. 实验设计
- **数据集**：
  - **行内（in-domain）**：数学推理使用增强版 GSM8K（约 40 万道题）；常识推理使用 StrategyQA（2780 个多跳是非题，有标注的子问题）。
  - **域外（out-of-domain）**：数学推理的 GSM-HARD（将 GSM8K 中数字换成更大、更不常见的数字，增加难度）。
- **基准（benchmark）**：所有方法均在相应测试集上评估准确率（exact match）。
- **对比方法**：
  - 标准 CoT 微调。
  - **语言空间条件计算**：LITE、LayerSkip（基于早期退出）。
  - **潜空间压缩推理**：iCoT、Coconut、CODI（将 CoT 压缩为连续潜表示）。
  - **潜空间扩展推理**：pause token（插入特殊 token 延迟输出以增加潜计算）。
- **公平性**：为保证公平，分别在 GPT-2 124M 和 LLaMA 3.2 1B 两种骨干网络上实现 System-1.5 与对应基线比较。

## 4. 资源与算力
- **硬件**：单张 NVIDIA RTX A5000（24 GB）GPU。
- **训练时间**：
  - GPT-2 124M 骨干：约 5 小时完成 8 个 epoch。
  - LLaMA 3.2 1B 骨干：约 26 小时完成 8 个 epoch。
- **超参数**：AdamW 优化器，学习率 \(2\times10^{-5}\)，warmup 6%，批次大小 2。默认深度退出阈值 \(\lambda_{\text{depth}}=0.6\)，解码步骤常数 \(\lambda_{\text{step}}=2\)。损失系数 \(\alpha=1.0\)，\(\beta=1.0\)。
- 论文未公开代码和预训练模型，但提供了足够实现细节。

## 5. 实验数量与充分性
- **主要实验**：在 GSM8K、GSM-HARD、StrategyQA 三个数据集上报告了准确率、解码步数、FLOPs 降低率和推理加速比，与 7 种基线（含 CoT）进行全面对比。
- **消融实验**：
  - 不同 System-2 学生（Coconut-System-1.5、CODI-System-1.5）对最终性能的影响。
  - 联合学习（两阶段同时进行）与全参数学习 vs. 两阶段冻结训练。
  - 测试时缩放：调整 \(\lambda_{\text{depth}}\) 和 \(\lambda_{\text{step}}\) 的二维帕累托前沿分析。
- **充分性评估**：实验覆盖了行内和域外场景，多种消融设计，且采用 4 次独立随机种子取平均，结果稳定。对比方法均按官方实现或适配公平比较。整体实验设计科学、客观、公平。

## 6. 论文的主要结论与发现
- **性能与效率**：System-1.5 Reasoning 在 GSM8K 上准确率 46.94%（与 CoT 的 46.67% 持平），推理加速超过 20×，中间 token 生成减少 91.0%；在 StrategyQA 上准确率 48.61%（优于 CoT 的 47.36%），加速达 55.65×。
- **潜空间优势**：相比语言空间早期退出方法，System-1.5 通过步骤短路进一步减少每步 FLOPs（约 1.95×），总体加速高于其他潜空间方法（如 Coconut 约 10×）。
- **直接蒸馏优于课程学习**：语言到潜空间的直接对齐（teacher-forcing）比 Coconut 的渐进式课程学习更有效，因为后者限制了潜表示的灵活性。
- **两阶段训练的必要性**：联合学习或全参数训练会导致优化冲突，降低最终性能；先对齐再冻结主干只训练路由模块效果最佳。
- **可控的测试时缩放**：通过调节深度阈值和步骤常数可灵活权衡性能与计算，且两个维度对性能影响相似，验证了二维自适应设计的必要性。

## 7. 优点
- **创新性**：首次在潜空间同时引入垂直（深度）和水平（步骤）两种动态短路，模拟人类不同复杂度推理，思路新颖。
- **效率显著**：在几乎不损失准确率的前提下，实现 20–55 倍的推理加速，token 生成减少 90% 以上，实用价值高。
- **训练简洁**：两阶段蒸馏采用 teacher-forcing，避免复杂课程调度，训练稳定高效。
- **实验充分**：覆盖多数据集、多基线、多消融，且控制了骨干网络，结果可信。
- **可解释性（部分）**：通过原子思维分解显式地定义步骤关键性，为潜空间推理提供了一定可解释路径。

## 8. 不足与局限
- **缺乏可解释性**：潜空间推理本身不生成中间语言输出，难以直观理解模型内部逻辑，在高风险场景下可能存在问题。
- **评估范围有限**：仅在中等规模基准（GSM8K、StrategyQA）和模型（GPT-2 124M、LLaMA 3.2 1B）上实验，未验证更大模型（如 7B、70B）或更复杂任务（如代码生成、定理证明）上的可扩展性。
- **关键性标注依赖**：步骤关键性标签通过原子思维分解自动生成，可能对复杂或歧义推理不够鲁棒，存在噪声风险。
- **硬件限制**：仅用单 GPU 训练，未能探索分布式或更大批量设置下的表现。
- **未公开代码与数据**：虽然提供了复现细节，但缺乏开源资源可能影响可复现性。
- **潜在偏差**：训练数据（GSM8K augment 和 StrategyQA）的规模和质量对结果有显著影响，模型可能对特定类型的问题偏向性未充分分析。

（完）
