---
title: Who Reasons in the Large Language Models?
title_zh: 大语言模型中谁在推理？
authors: "Jie Shao, Jianxin Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XIqlxqNDCL"
tags: ["query:ns-xai"]
score: 8.0
evidence: 诊断工具Stethoscope定位LLM推理模块
tldr: 该论文提出Stethoscope诊断套件，通过实验证据表明大语言模型的推理能力主要归因于多头自注意力中的输出投影层。这一发现挑战了推理能力分布式的观点，为模型设计和可解释性提供了重要见解。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1360, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1162, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 672, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1160, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1008, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xiqlxqndcl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 748, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xiqlxqndcl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 697, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xiqlxqndcl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 696, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xiqlxqndcl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xiqlxqndcl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1161, \"height\": 443, \"label\": \"Table\"}]"
motivation: 缺乏对LLM推理能力来源的清晰认识。
method: 开发Stethoscope诊断工具分析内部模块。
result: 证明推理能力主要来自输出投影层。
conclusion: 揭示了LLM推理能力的关键位置。
---

## Abstract
Despite the impressive performance of large language models (LLMs), the process of endowing them with new capabilities---such as mathematical reasoning---remains largely empirical and opaque. A critical open question is whether reasoning abilities stem from the entire model, specific modules, or are merely artifacts of overfitting. In this work, we hypothesize that the reasoning capabilities in well-trained LLMs are primarily attributed to the output projection module (o_proj) in the Transformer’s multi-head self-attention (MHSA) module. To support this hypothesis, we introduce Stethoscope for Networks (SfN), a suite of diagnostic tools designed to probe and analyze the internal behaviors of LLMs. Using SfN, we provide both circumstantial and empirical evidence suggesting that o_proj plays a central role in enabling reasoning, whereas other modules contribute more to fluent dialogue. These findings offer a new perspective on LLM interpretability and open avenues for more targeted training strategies, potentially enabling more efficient and specialized LLMs.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义
- **研究动机**：尽管大语言模型（LLM）在数学推理等任务上取得了显著成功，但其能力的来源仍是一个“黑箱”。关键问题在于：推理能力是来自整个模型、特定模块，还是仅仅源于过拟合？解答这一问题对指导未来LLM研究至关重要。
- **整体含义**：论文旨在定位LLM推理能力的关键组件，为模型可解释性和高效训练提供新视角。

#### 2. 方法论：Stethoscope for Networks (SfN)
- **核心思想**：通过多角度诊断工具，比较基座模型（弱推理）与推理增强模型（强推理）之间的差异，从而定位推理能力的来源。
- **关键技术细节**：
  - **Delta听诊器**：计算基座模型A与推理模型B各模块权重的L2范数差`||wX(B)-wX(A)||`和相对变化分布，发现o_proj变化最大且呈双峰分布。
  - **Merge听诊器**：将推理模型B的特定模块（如o_proj）替换到基座模型A中，观察合并后模型的推理表现。仅替换o_proj能正确推理复杂数学题，而替换其他模块则导致退化。
  - **Freeze听诊器**：在微调时冻结大部分模块，仅训练o_proj和LayerNorm等。结果表明，仅调o_proj+LN即可达到接近全参数微调的推理性能，且训练更快、更稳定。
  - **Destruction听诊器**：通过置零、重初始化或整层删除等方式破坏指定模块，观察对话能力退化程度。o_proj被破坏后对话仍保持流畅（Level III），而MLP等模块被破坏后输出崩溃。
- **公式/算法**：论文给出了Transformer中MHSA和MLP的数学形式（式1），但SfN本身是诊断框架，无新公式。

#### 3. 实验设计
- **数据集/场景**：
  - **推理基准**：AIME 2024（数学竞赛题）、Math 500、GPQA Diamond。
  - **对话评估**：自行设定的四类输出等级（Level I~IV），用于定性分析。
  - **微调数据集**：s1K（1000个高质量推理轨迹），来自s1论文。
- **Benchmark**：对比了不同模块替换策略、不同冻结微调策略，以及全参数微调基线。
- **对比方法**：
  - 基座模型：Qwen2.5-Math-1.5B/7B、Qwen2.5-14B/32B-Instruct、Llama-3.1-8B、Llama-3.3-70B。
  - 推理模型：DeepSeek-R1-Distill-Qwen-1.5B/7B/14B/32B/70B、DeepSeek-R1-Distill-Llama-8B/70B。
  - 微调基线：遵循s1的“Budget Forcing Wait×2”设置。

#### 4. 资源与算力
- **GPU型号**：NVIDIA A100 (40GB/80GB)。
- **数量与时长**：
  - 1.5B~14B模型：单张A100，推理/可视化。
  - 32B~70B模型：8张A100集群。训练约6小时，测试约2小时。
- **框架**：Transformers、vLLM（推理）、DeepSpeed ZeRO Stage 3（训练）、lm-evaluation-harness（评估）。

#### 5. 实验数量与充分性
- **实验组数**：涵盖5种模型尺寸（1.5B,7B,8B,14B,32B,70B），每种尺寸下均进行了Delta听诊器可视化；Merge听诊器在1.5B和更大尺寸上尝试；Freeze听诊器在14B和32B上执行4种不同冻结策略（F1~F4）；Destruction听诊器在32B上测试3种破坏方法×8模块。此外附录补充了7B/8B/70B结果。
- **充分性**：实验覆盖多种架构（Qwen、Llama）和参数规模，使用多种诊断方法交叉验证，结论一致。但定性对话评估（Level分类）依赖主观观察，缺乏统计显著性检验。

#### 6. 主要结论与发现
- **核心结论**：输出投影（o_proj）是LLM推理能力的关键模块，而其他模块（如MLP、q/k/v_proj）主要贡献于对话流畅性。
- **具体发现**：
  - Delta听诊器揭示o_proj权重变化最大且分布呈双峰，与其他模块的单峰分布显著不同。
  - Merge听诊器显示仅替换o_proj即可使合并模型在AIME上从0.067提升至0.200（1.5B模型），并产生正确推理过程。
  - Freeze听诊器表明仅微调o_proj+LN（3.2B参数）即可达到与全参数微调（32.8B参数）近似的推理性能（AIME 0.367 vs 0.367），且训练速度提高3倍以上。
  - Destruction听诊器发现破坏o_proj后对话仍能维持Level III，而破坏MLP或q/k_proj则导致输出崩溃。

#### 7. 优点
- **方法新颖**：提出“听诊器”诊断框架，通过反向工程（合并、破坏）定位能力来源，远离传统的注意力可视化或参数探测。
- **实验设计巧妙**：Merge听诊器无需额外训练即可验证假设，Freeze听诊器直接证明o_proj的充分性。
- **实际意义强**：发现推理能力可定位到少量参数，可大幅降低微调成本，并支持“输出投影插件”的模块化设计（如一个o_proj用于推理，另一个用于领域迁移）。
- **结论可靠**：多种互不依赖的独立实验（Delta、Merge、Freeze、Destruction）均指向同一结论，置信度高。

#### 8. 不足与局限
- **模型泛化性**：实验主要基于Qwen和Llama系列，以及DeepSeek-R1蒸馏变体，可能不推广到其他架构（如MoE、RWKV）或通过RL而非SFT训练的推理模型。
- **定性评估的主观性**：对话能力分级（Level I~IV）依赖人工判断，缺乏量化指标和统计检验。
- **理论缺失**：论文未提供o_proj为何能主导推理的理论解释（如梯度流动或信息瓶颈），仅给出经验证据。
- **实验规模限制**：Freeze实验中，仅调o_proj+LN在32B上未完全达到全参数微调水平（Math 500: 0.890 vs 0.906），且超参数未经系统调优。
- **Destruction局限**：仅测试了单个数据集上的对话样例，且破坏层限制在中间层（5-30），早/晚层破坏导致全部失败，未探索层依赖规律。

（完）
