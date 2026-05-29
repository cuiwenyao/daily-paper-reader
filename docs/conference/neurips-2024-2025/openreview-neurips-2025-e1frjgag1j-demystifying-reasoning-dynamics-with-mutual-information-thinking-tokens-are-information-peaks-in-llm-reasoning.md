---
title: "Demystifying Reasoning Dynamics with Mutual Information: Thinking Tokens are Information Peaks in LLM Reasoning"
title_zh: 用互信息解密推理动态：思维token是LLM推理中的信息峰
authors: "Chen Qian, Dongrui Liu, Haochen Wen, Zhen Bai, Yong Liu, Jing Shao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=E1FrjgaG1J"
tags: ["query:ns-xai"]
score: 8.0
evidence: 通过互信息分析大模型推理过程
tldr: 该论文从信息论视角研究大推理模型的内部推理机制，发现推理过程中互信息在特定生成步骤出现峰值（信息峰），且这些峰值与模型预测误差降低相关。为理解LLM推理提供了可解释性分析方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 434}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1386, \"height\": 520}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1389, \"height\": 598}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1478, \"height\": 720}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 469}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 708, \"height\": 410}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 411}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1455, \"height\": 416}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1310, \"height\": 2300}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1229, \"height\": 2357}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1315, \"height\": 2335}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1242, \"height\": 2368}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1314, \"height\": 2338}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1242, \"height\": 2373}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1316, \"height\": 2335}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1243, \"height\": 2377}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1309, \"height\": 2342}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1210, \"height\": 2344}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1311, \"height\": 2327}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e1frjgag1j/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1234, \"height\": 2360}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 343}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1468, \"height\": 279}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e1frjgag1j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 779, \"height\": 283}]"
motivation: 大推理模型内部推理机制尚不明确，缺乏可解释性工具。
method: 跟踪中间表示与正确答案之间的互信息演变，发现并理论分析信息峰现象。
result: 互信息峰值出现时模型预测误差下降，且峰值与思考token相关。
conclusion: 信息峰为解释LLM推理过程提供了有效的可解释性视角。
---

## Abstract
Large reasoning models (LRMs) have demonstrated impressive capabilities in complex problem-solving, yet their internal reasoning mechanisms remain poorly understood.
In this paper, we investigate the reasoning trajectories of LRMs from an information-theoretic perspective. 
By tracking how mutual information (MI) between intermediate representations and the correct answer evolves during LRM reasoning, we observe an interesting MI peaks phenomenon: the MI at specific generative steps exhibits a sudden and significant increase during LRM's reasoning process. 
We theoretically analyze such phenomenon and show that as MI increases, the probability of model's prediction error decreases.
Furthermore, these MI peaks often correspond to tokens expressing reflection or transition, such as "Hmm", "Wait" and "Therefore," which we term as the thinking tokens.
We then demonstrate that these thinking tokens are crucial for LRM's reasoning performance, while other tokens has minimal impacts.
Building on these analyses, we propose two simple yet effective methods to improve LRM's reasoning performance, by delicately leveraging these thinking tokens.
Overall, our work provides novel insights into the reasoning mechanisms of LRMs and offers practical ways to improve their reasoning capabilities.
The code is available at \url{https://github.com/ChnQ/MI-Peaks}.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Demystifying Reasoning Dynamics with Mutual Information: Thinking Tokens are Information Peaks in LLM Reasoning》的结构化、深入、客观的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题：** 大型推理模型（LRM，如DeepSeek-R1、QwQ）在复杂问题求解上表现卓越，但其内部推理机制仍然是一个“黑箱”。具体而言，每个中间步骤对最终答案的影响程度，以及推理过程中的关键节点，均缺乏有效的分析工具。
*   **研究动机：** 尽管已有工作关注于影响LLM安全与对齐的“关键token”，但在LRM的推理过程中是否存在显著影响最终结果的“关键推理步骤”或“关键中间状态”？本文试图从信息论的角度回答这一问题。
*   **整体含义：** 论文通过引入**互信息（Mutual Information, MI）** 这一信息论工具，动态追踪LRM推理过程中每步中间表示与正确答案之间的信息关联，旨在揭示推理的动态机理，并为改进LRM的推理能力提供理论依据和实用方法。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想：** 在LRM进行多步推理的自回归生成过程中，计算每个生成步骤的**隐层表示** (\(h_t\)) 与**正确答案的标准表示** (\(h_y\)) 之间的**互信息** (\(I(h_t; h_y)\))，从而构建一条随生成步骤变化的MI轨迹。通过分析该轨迹，识别出对推理至关重要的“信息峰”（MI Peaks）以及对应的“思考令牌”（Thinking Tokens）。
*   **关键技术细节：**
    1.  **MI估计：** 由于高维空间中MI计算困难，论文采用**希尔伯特-施密特独立性准则（HSIC）** 作为MI的近似估计量。具体使用高斯核函数。
    2.  **MI峰值的定义：** 基于MI序列的四分位数和四分位距（IQR），将显著高于第三四分位数加1.5倍IQR的步骤定义为MI峰值。
    3.  **思考令牌的识别：** 将MI峰值处的隐层表示通过LM的输出投影矩阵（\(W_{out}\)）和softmax解码，贪心地选取概率最高的token，发现这些token多为“Hmm”、“Wait”、“Therefore”、“So”等表示自我反思、过渡或逻辑推导的词汇，定义其为“思考令牌”。
    4.  **核心理论分析（定理1和2）：** 从理论上证明了**累积互信息**（\(\sum_{j=1}^{T} I(y; h_j | h_{<j})\)）与模型**预测误差** (\(p_e\)) 之间的关系。定理1（下界）表明，误差下界随累积MI增加而降低；定理2（上界）表明，误差上界也随累积MI增加而降低。这两个定理共同说明，提高推理过程中的MI有助于降低模型出错的概率。
    5.  **应用方法一：表示回收（Representation Recycling, RR）：** 在推理过程中，当模型生成一个思考令牌时，将其对应的隐层表示**重新输入同一Transformer层**进行处理，以更充分地利用该高MI表示携带的信息。
    6.  **应用方法二：基于思考令牌的测试时缩放（Thinking Token based Test-time Scaling, TTTS）：** 在额外的token预算下，强制模型在生成完初始输出后，继续以思考令牌（如“So”、“Hmm”）开头产生新的推理步骤，从而引导模型进行更深层次的思考。

### 3. 实验设计：数据集、基准与对比方法

*   **数据集：**
    *   **MI轨迹分析：** 使用MATH数据集的**训练集**（12,000个竞赛级数学题），从中随机抽取100个样本进行观察。
    *   **推理性能评估：** 三个广泛使用的数学推理基准，按难度递增排列：**GSM8K**、**MATH500**、**AIME24**。
    *   **跨域验证：** 额外使用了**GPQA**（研究生级别问答）和**MedQA**（医学问答）数据集。
*   **基准/模型：**
    *   **LRM系列：** DeepSeek-R1-Distill-{Qwen-7B, Llama-8B, Qwen-14B, Qwen-32B, Llama-70B}，以及 **QwQ-32B**。
    *   **非推理LLM对比：** 对应的基础模型或非推理增强模型，如Llama-3.1-8B、Qwen2.5-14B等。
*   **对比方法：**
    *   对于思考令牌的验证，采用**抑制生成特定数量思考令牌** vs **随机抑制相同数量非思考令牌**的消融实验。
    *   对于RR和TTTS方法，主要与**原始LRM**（未进行任何干预）进行对比。
    *   TTTS还隐含了与基线模型中随token预算增加性能变化情况的对比。

### 4. 资源与算力

*   **明确声明：** 论文在附录B中明确指出：“**All experiments are conducted on four NVIDIA A100 GPUs.**” (所有实验均在四张NVIDIA A100 GPU上进行)。
*   **未明确信息：** 论文未提供完整的训练时长、推理总耗时或具体GPU内存消耗等详细算力信息。

### 5. 实验数量与充分性

*   **实验数量：**
    *   **MI轨迹分析：** 在5种LRM和5种对应非推理LLM上进行了MI轨迹可视化（共10个模型 * 100样本）。
    *   **思考令牌抑制实验：** 在两种LRM（Distill-Llama-8B, Distill-Qwen-14B）上，对多个抑制数量进行了测试，并在图5中展示结果。
    *   **RR方法：** 在两种LRM（Distill-Llama-8B和Distill-Qwen-7B）和三个数学基准（GSM8K, MATH500, AIME24）上进行了验证（图6）。
    *   **TTTS方法：** 在Lllama-8B模型上，针对三个基准（GSM8K, MATH500, AIME24）和多种token预算进行了测试（图7）。
    *   **跨域验证：** 在GPQA和MedQA上进行了AOM指标对比（表3）。
*   **充分性与公平性分析：**
    *   **优点：** 实验覆盖了不同规模的LRM模型（7B-70B）和多种难度级别的基准；包含消融实验（抑制token）和与基础模型的对比，设计较为严谨；进行了跨域验证，增强了结论的泛化性。
    *   **不足：** MI轨迹分析仅基于100个样本，样本量相对较小；抑制思考令牌的实验中，抑制数量选择的依据和最优性未详细阐述；仅使用了开源模型，未扩展到闭源最强模型（如OpenAI o1），可能影响结论的广泛性。

### 6. 论文的主要结论与发现

1.  **MI峰值现象：** 在LRM的推理过程中，中间表示与正确答案的MI会呈现出稀疏、非均匀分布的**突然且显著的增长峰值**（MI Peaks）。
2.  **思考令牌的角色：** 这些MI峰值对应的token绝大多数是“思考令牌”，如“Hmm”、“Wait”、“Therefore”。这些令牌在语义上引导模型进行自我反思、逻辑转换或持续推理。
3.  **思考令牌的必要性：** 抑制思考令牌的生成会**严重损害**LRM的推理性能，而随机抑制同等数量的其他令牌几乎无影响，证明了思考令牌的**关键性**。
4.  **理论支持：** 定理1和2从理论上证明了，更高的累积MI与更低的预测误差概率相关，为MI峰值现象的意义提供了坚实的理论基础。
5.  **实用方法有效：** 基于以上洞察提出的 **RR**（表示回收）和 **TTTS**（基于思考令牌的测试时缩放）两种无需训练的方法均能**持续且有效地提升**LRM在数学推理基准上的性能，尤其是在更难的AIME24任务上。

### 7. 优点：方法或实验设计上的亮点

*   **视角新颖：** 首次系统性地将**信息论工具（互信息）** 应用于分析LRM的内部推理动态，为理解“黑箱”提供了全新的、量化视角。
*   **理论结合实践：** 不仅有扎实的理论推导（定理1和2），还将理论洞察转化为实用的、无需额外训练的性能增强方法（RR和TTTS），具有很强的落地价值。
*   **技术与语义发现有趣：** 将抽象的MI峰值与具体的、有语义的“思考令牌”对应起来，直观且令人信服地解释了MI峰值的含义。
*   **实验设计严谨：** 通过“抑制思考令牌”这一因果干预实验，强有力地证明了思考令牌的因果作用，而非仅停留在相关性分析。
*   **方法简单高效：** 提出的RR和TTTS方法极其简单，易于实现，且计算开销小，便于在实际系统中部署。

### 8. 不足与局限

*   **粒度局限：** 主要进行**token级别**的MI分析，未考虑更细的语义单元（如连续短语）或更自然的逻辑步骤划分，可能遗漏部分动态信息。
*   **理论假设：** 理论推导依赖于一些近似和假设（如MI的链式法则应用），且HSIC是对MI的近似估计，可能存在偏差。MI峰值的形成机制仍未从理论上完全阐明。
*   **实验覆盖局限：** 对话数据集、逻辑推理（非数学/知识类）等场景下的泛化性尚未验证。仅评估了开源模型，对闭源模型的适用性未知。
*   **应用限制：** RR方法中触发回收的层（\(l^*\)）和思考令牌列表的设置需要人工经验，最优配置可能因任务而异。TTTS方法仅适用于有额外token预算的场景，且“思考令牌”的筛选过滤规则具有一定主观性。
*   **偏差风险：** 抑制思考令牌时，模型可能产生替代表达（如将“Wait”变为“But wait”），这可能使部分实验结果的解读复杂化。

（完）
