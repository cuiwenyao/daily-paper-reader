---
title: Improving Neural Logic Machines via Failure Reflection
title_zh: 通过失败反思改进神经逻辑机器
authors: "Zhiming Li, Yushi Cao, YAN ZHENG, Xu Liu, Bozhi Wu, Tianlin Li, Xiufeng Xu, Junzhe Jiang, Yon Shin Teo, Shang-Wei Lin, Yang Liu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=JObct1zyTb"
tags: ["query:ns-xai"]
score: 9.0
evidence: 通过失败反思改进神经逻辑机器的神经符号推理
tldr: 神经逻辑机器（NLM）是有效的神经符号推理模型，但训练中会重复犯错。本文提出失败反思引导正则化器（FRGR），动态识别错误根因并施加惩罚，显著提升了NLM在推理和决策任务上的泛化能力，为神经符号学习提供了更稳定的训练方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 442, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 805, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1779, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1740, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1776, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1778, \"height\": 1135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1739, \"height\": 846, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1539, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1762, \"height\": 326, \"label\": \"Table\"}]"
motivation: 神经逻辑机器在训练中重复相同错误，导致次优性能。
method: 提出FRGR框架，动态识别并惩罚重复错误。
result: 在多种推理任务上性能显著提升，泛化能力增强。
conclusion: 失败反思正则化有效提升了神经符号模型的训练效率。
---

## Abstract
Reasoning is a fundamental ability towards artificial general intelligence (AGI). Fueled by the success of deep learning, the neural logic machines models (NLMs) have introduced novel neural-symbolic structures and demonstrate great performance and generalization on reasoning and decision-making tasks. However, the original training approaches of the NLMs are still far from perfect, the models would repeat similar mistakes during the training process which leads to sub-optimal performance. To mitigate this issue, we present a novel framework named Failure Reflection Guided Regularizer (FRGR). FRGR first dynamically identifies and summarizes the root cause if the model repeats similar mistakes during training. Then it penalizes the model if it makes similar mistakes in future training iterations. In this way, the model is expected to avoid repeating errors of similar root causes and converge faster to a better-performed optimum. Experimental results on multiple relational reasoning and decision-making tasks demonstrate the effectiveness of FRGR in improving performance, generalization, training efficiency, and data efficiency.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将根据您的要求，对《Improving Neural Logic Machines via Failure Reflection》这篇论文进行结构化、深入、客观的总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：神经逻辑机器模型（NLMs，如 NLM 和 DLM）在训练过程中会反复犯下相似的错误，导致模型陷入次优的局部最优解，训练损失震荡，性能不佳。
*   **研究背景**：神经符号 AI 是通向通用人工智能的重要方向。NLMs 通过引入归纳偏置实现了优异的推理和决策性能。然而，现有 NLM 的训练方式（基于交叉熵损失或REINFORCE）无法有效识别并阻止模型重复犯下由相同根因（例如，反复使用某个错误的子程序）导致的错误。
*   **整体含义**：本文旨在通过一种新的正则化方法，主动监测并惩罚模型的“错误重复”行为，从而提升 NLM 的训练效率和最终性能。这为优化神经符号学习模型提供了一种新颖且有效的思路。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：**失败反思引导正则化器 (FRGR)**。其核心是：动态地从模型的历史错误行为中挖掘出导致重复失败的“根因子程序”，并在后续训练中，如果模型再次触发该根因，则施加惩罚。
*   **关键技术细节（三部分）**：
    1.  **根因挖掘 (Root Cause Mining)**：
        *   **程序提取器 (Program Extractor)**：将 NLMs 的神经权重转化为可解释的符号化程序表示（`ω`）。对于 NLM，通过提取每个 MLP 模块中连接输出神经元的最大输入权重的索引来近似表示程序；对于 DLM，则提取模糊逻辑运算符的权重索引。
        *   **历史程序队列 (History Program Queue, Q)**：当模型在训练批次上犯错时，将当前提取的符号程序表示 `ω` 入队，形成一个包含失败历史的队列。
        *   **根因近似**：采用 Apriori 算法对历史程序队列进行频繁项集挖掘，找出那些在所有失败程序表示中频繁共同出现的神经元连接索引集合。这个频繁项集即被视为导致失败的“根因子程序” `ρ`。
    2.  **重复正则化 (Repetition Regularization, ReReg)**：
        *   **重复度计算**：计算当前模型程序表示 `ω` 与根因子程序 `ρ` 的交集 `ϕ`。
        *   **惩罚**：对交集中的权重索引施加 L1 正则化，鼓励这些神经元权重趋近于零，从而抑制模型再次使用该子程序。
        *   **公式**：
            *   重复度：`ϕ = {θ_(b,d,x,y) : (b,d,x,y) ∈ ω ∩ ρ}`
            *   正则化损失：`L_ReReg(θ) = Σ∥ϕ_j∥₁`
            *   总损失：`L(θ) = L_CLS + β * L_ReReg`，其中 `β` 为调节系数。
    3.  **算法流程（以关系推理为例）**：
        *   在每个训练步骤，用标准损失训练模型。
        *   若模型预测错误，提取程序表示并入队。
        *   每 m 步，用 Apriori 更新根因 `ρ`。
        *   计算 `L_ReReg` 并加入总损失，反向传播更新参数。

### 3. 实验设计

*   **数据集与场景**：
    1.  **关系推理**：
        *   **族谱推理 (Family Tree Reasoning)**：任务包括 `HasFather`, `HasSister`, `IsGrandparent`, `IsUncle`, `IsMGUncle`。输入为基本亲属关系，输出为推理出的高级关系。
        *   **通用图推理 (General Graph Reasoning)**：任务包括 `1/2-OutDegree`, `4/6-Connectivity`。输入为 `HasEdge` 关系，输出为节点属性或连通性。
    2.  **强化学习 (Reinforcement Learning)**：
        *   **Sorting**：学习交换元素以排序数组。
        *   **Path**：在图中寻找路径。
        *   **Blocks World**：通过移动积木达到目标状态。
*   **Benchmark**：遵循之前工作（Dong et al., 2018; Zimmer et al., 2023）的评估设置，测试：
    *   **性能 (Performance)**：在训练集相同规模的数据上测试。
    *   **泛化 (Generalization)**：在更大规模的数据上测试（如族谱从20人扩展到100人，图从10节点扩展到20节点）。
    *   **训练效率**：达到最优验证集成功率所需的训练轮数（Epochs）。
*   **对比方法**：
    *   **基线模型**：原始 NLM (Neural Logic Machines) 和 DLM (Differentiable Logic Machines)。
    *   **实验组**：在 NLM 和 DLM 基础上应用 FRGR。
*   **设置**：实验在 **数据丰富** 和 **数据稀缺** 两种设置下进行。数据稀缺场景下训练数据量仅为数据丰富场景的 1/500。

### 4. 资源与算力

*   论文在附录 C 中明确说明了硬件配置：**一台服务器**，配备 **48 核 Intel Xeon Silver 4214 CPU**，**4 块 NVIDIA Quadro RTX 8000 GPU**（共48GB显存），以及 **252GB RAM**。
*   **训练时长**：文中未给出具体的总训练时长。但通过“Epochs”指标可以推断，不同任务的训练复杂度差异很大，复杂任务（如 `6-Connectivity`）需要数百个Epoch，而简单任务仅需十几个。由于使用GPU，训练时间应是可接受的。

### 5. 实验数量与充分性

*   **实验数量**：充分且广泛。
    *   在关系推理上，覆盖了 **5个族谱任务** 和 **4个图推理任务**，共计9个任务。
    *   在强化学习上，覆盖了 **3个环境**。
    *   每个任务都在数据丰富和数据稀缺两种设置下进行评估。
    *   进行了 **动机验证实验**：可视化训练过程中的“一元原子比率 (UAR)”和损失曲线，直观展示了错误重复问题及 FRGR 的缓解效果。
    *   进行了 **超参数分析**：分析了正则化系数 `β` 和历史队列大小 `τ` 对性能的影响。
    *   针对DLM的RL任务，论文坦言无法复现原论文结果，因此未在该设置下对比。
*   **充分性与公平性**：
    *   实验对比了最先进的基线，并严格遵循了原模型的训练设置和网络结构。
    *   评估指标（成功率、毕业率、训练轮数）客观且全面。
    *   在数据稀缺设置下的实验验证了方法的鲁棒性和数据效率。
    *   缺少消融实验，例如只使用程序提取或只使用正则化的贡献。另外，超参数分析仅在一个任务上完成，略显单一。

### 6. 论文的主要结论与发现

*   **FRGR 能显著提升 NLMs 的性能、泛化能力、训练效率和数据效率**。在大多数任务上，FRGR 都能帮助模型更快收敛，达到更高或相同的成功率，并展现出更强的泛化能力（尤其是在数据稀缺时）。
*   **FRGR 有效抑制了模型重复使用错误根因子程序的行为**。通过分析 UAR，发现训练过程中模型会持续依赖错误的子程序（如不必要的一元谓词），而 FRGR 能有效降低这种依赖，将模型从错误局部最优中“拉”出来。
*   **FRGR 在数据稀缺场景下效果尤为显著**。在训练数据极度匮乏时，基线模型性能下降严重，而 FRGR 能维持甚至提升性能，证明了其高数据效率。
*   **对简单任务的影响**：对于已经能轻松达到 100% 性能的简单任务，FRGR 可能稍微增加收敛所需的轮数（训练效率轻微下降），但能获得更简洁、无冗余的程序表示。

### 7. 优点

*   **创新性强**：首次提出利用模型历史错误根因来指导学习过程的思路，而不是简单地依赖梯度和损失函数。这为神经符号学习乃至更广泛的深度学习模型优化提供了新视角。
*   **方法论清晰且有效**：FRGR 框架设计精巧，将神经网络的权重转化为可解释的符号表示，并通过频繁项集挖掘自动化地提炼“根因”，逻辑自洽，可解释性强。
*   **实验扎实**：覆盖了多种任务类型（关系推理、强化学习）和数据场景（丰富、稀缺），实验设计全面，结果有力证明了方法的有效性。
*   **实用性强**：能同时提升多个维度的性能（性能、泛化、训练效率、数据效率），且实现不复杂，易于集成到已有的 NLM 模型中。

### 8. 不足与局限

*   **适用范围较窄**：论文的方法主要针对具有明确模块化结构的神经逻辑机器模型（NLM/DLM）。如何将“根因挖掘”和“重复惩罚”的思想推广到其他类型的神经网络（如 Transformer）或其他领域仍有待探索。
*   **计算开销**：程序提取和频繁项集挖掘（Apriori）会引入额外的计算开销。虽然论文中提到每 m 步才执行一次，且在简单任务上影响不大，但在大规模模型或实时性要求高的场景下可能成为瓶颈。
*   **对简单任务的负面效应**：对于已经能完美学习的简单任务，额外的正则化反而可能导致收敛速度变慢，尽管最终性能不受影响。这表明方法需要针对任务难度自适应调整。
*   **根因定义的局限性**：当前通过Apriori发现的“根因”是统计意义上的共现模式，可能会将偶然的、非因果性的模式也标记为根因，导致误惩罚。文中缺乏对根因因果性的验证。
*   **强化学习部分的局限性**：论文未能成功复现 DLM 在强化学习任务上的基线结果，因此 FRGR 在该设置下的对比仅限于 NLM，其有效性在 DLM 上未得到验证。
*   **缺乏消融实验**：没有独立分析程序提取、历史队列和正则化项中各个组件对最终结果的贡献。

（完）
