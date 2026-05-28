---
title: "FlexAC: Towards Flexible Control of Associative Reasoning in Multimodal Large Language Models"
title_zh: FlexAC：面向多模态大模型联想推理的灵活控制
authors: "Shengming Yuan, Xinyu Lyu, Shuailong Wang, Beitao Chen, Jingkuan Song, Lianli Gao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RbGUML7YK6"
tags: ["query:ns-xai"]
score: 6.0
evidence: 灵活控制多模态大模型联想推理以平衡忠实性与创造性
tldr: 多模态大模型在忠实性和创造性之间存在权衡，该论文提出通过修改中间层表示来灵活控制联想推理强度。实验表明该方法能有效调节模型在不同事实性和创造性场景下的表现，为可解释推理提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1427, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1414, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1400, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 684, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 571, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1293, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1302, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1440, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 697, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 877, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1154, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1021, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1361, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1344, \"height\": 137, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1363, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 661, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1421, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1427, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1427, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1420, \"height\": 1547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1444, \"height\": 1444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1442, \"height\": 1444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1397, \"height\": 1889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 221, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 104, \"height\": 102, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 204, \"height\": 182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 199, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 106, \"height\": 100, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1345, \"height\": 168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 100, \"height\": 89, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 206, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 104, \"height\": 103, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 325, \"height\": 221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 101, \"height\": 92, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 315, \"height\": 201, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1278, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbguml7yk6/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1409, \"height\": 983, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1306, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1304, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1173, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbguml7yk6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1355, \"height\": 2114, \"label\": \"Table\"}]"
motivation: 现有方法缺乏灵活调节联想推理强度的能力。
method: 通过修改中层表示来调节联想推理强度。
result: 实现了忠实性与创造性之间的灵活权衡。
conclusion: 为多模态大模型的可控推理提供新方法。
---

## Abstract
Multimodal large language models (MLLMs) face an inherent trade-off between faithfulness and creativity, as different tasks require varying degrees of associative reasoning. However, existing methods lack the flexibility to modulate this reasoning strength, limiting MLLMs' adaptability across factual and creative scenarios. To bridge this gap, we propose equipping MLLMs with mechanisms that enable flexible control over associative reasoning. We begin by investigating the internal mechanisms underlying associative behavior in MLLMs and  find that: (1) middle layers play a pivotal role in shaping model’s associative tendencies,  (2) modifying representations in these layers effectively regulates associative reasoning strength, and  (3) hallucinations can be exploited to derive steering vectors that guide this modulation. Building on these findings, we introduce Flexible Association Control (FlexAC), a lightweight and training-free framework for modulating associative behavior in MLLMs. FlexAC first induces hallucination-guided intermediate representations to encode associative directions. Then, it selects high-association instances to construct effective associative steering vectors, whose strengths are adaptively calibrated to balance creative guidance with output stability. Finally, recognizing the multi-dimensional nature of associative reasoning, FlexAC incorporates task-specific associative vectors derived from a forward pass on a few target-domain samples, enabling models to follow diverse associative directions and better adapt to creative tasks. Notably, our method achieves up to a 5.8× improvement in creativity on Creation-MMBench and a 29\% reduction in hallucination rate on CHAIR, surpassing existing baselines and demonstrating its effectiveness in enabling flexible control over associative reasoning in MLLMs. Our code is available at https://github.com/ylhz/FlexAC.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
多模态大语言模型（MLLMs）在事实性（忠实性）与创造性之间存在固有的权衡：不同任务需要不同程度的联想推理强度。然而，现有方法（如幻觉抑制技术）偏向于提高忠实性但压制了联想能力，而如何增强创造性并实现可控调节尚缺乏探索。论文的核心动机是赋予MLLMs灵活控制联想推理强度的能力，使其能够在事实性任务（如图像描述）和创造性任务（如活动策划、故事创作）之间自适应切换。

## 2. 方法论
### 核心思想
FlexAC是一个轻量级、无需训练的控制框架，通过修改模型中间层的隐藏表示来调节联想推理强度。该方法基于三个关键发现：(1) 联想行为主要在模型的中间层编码；(2) 修改中间层表示可以有效改变联想强度；(3) 幻觉响应可以用于提取引导联想方向的向量。

### 关键技术细节
- **Phase I: 离线控制向量构建**
  - **步骤1：幻觉引导的中间状态**：收集来自同一输入的“真实-幻觉”响应对，提取中间层隐藏状态差异，编码联想方向。
  - **步骤2：实例选择**：选择余弦距离最大的Top-K响应对，平均其差异得到稳定的一般联想向量 $v_l$。
  - **步骤3：方向集成**：进一步从少量目标域样本（通过GPT-4o生成的高联想输出）构建任务特定的联想向量 $v_{\text{task}}$。
- **Phase II: 推理时控制**
  - 将一般向量和任务特定向量注入中间层：$f_{\text{control}} = f_l + \alpha_{\text{gen}} v_{\text{gen}} + \alpha_{\text{task}} v_{\text{task}}$。
  - **Steering Intensity Calibration (SIC)**：自适应缩放控制系数，当当前表示已与目标方向对齐时减弱干预，否则增强。公式：$\alpha = \text{sigmoid}(\max(-\frac{f_l \cdot v_l}{\|f_l\|\|v_l\|}, 0))$。
  - 进一步对调制后的特征进行归一化以保持尺度。

### 公式与算法流程（文字描述）
算法流程：① 在离线阶段，对一批输入数据，通过模糊输入等方式诱导幻觉响应，提取中间层特征差，经Top-K选取后平均得到一般联想向量；② 在线上推理阶段，对于每个输入，计算当前隐藏状态与联想向量的对齐程度，动态调整强度系数 $\alpha$，然后将缩放后的向量加入中间层表示，最后归一化。

## 3. 实验设计
### 数据集与Benchmark
- **幻觉（低联想任务）**：CHAIR（图像描述中物体幻觉率）和POPE（物体级探测）。
- **创造力（高联想任务）**：自行提出的VDAT（视觉发散联想测试，衡量输出名词与图像的无关程度）；以及Creation-MMBench（开放式图像创造性生成）。
- **通用能力**：MME、MMMU、MMStar。

### 对比方法
- VCD（视觉对比解码）、VAF（视觉信号增强）、Ha-DPO（基于偏好优化的幻觉抑制）、Regular（原始模型）。对比在LLaVA-1.5、Qwen-VL、DeepSeek-VL2三个模型上进行。

### 评估指标
CHAIR S、CHAIR I、POPE准确率/F1；VDAT分数（基于CLIP计算的图像-文本不相似度）；Creation-MMBench的VFS（视觉保真度）和Reward（创造力提升相对于基线的比例）。

## 4. 资源与算力
论文在 **8×RTX 4090 GPU** 上进行所有实验。具体训练时长未明确说明，但FlexAC是无需训练的框架，仅在推理时进行向量注入，因此主要开销是推理时间。文中比较了推理运行时，FlexAC仅比原始模型增加微小开销，而VCD因需要双前向传播而耗时显著更高。

## 5. 实验数量与充分性
论文进行了多组实验：
- **主实验**：在幻觉、创造力、通用能力三个方向共约6个benchmark上对比三个模型。
- **消融实验**：层间控制分析（验证中间层最有效）、组件消融（IS、SIC、DI）、Top-K数量敏感性分析、控制层位置选择。
- **用户研究**：验证VDAT指标与人类判断的一致性。
- **附加实验**：扩展了11个通用benchmark（如MM-Vet、MMBench、TextVQA等）以确保泛化能力。
实验设计较为充分，对比方法包括当前主流幻觉抑制和创造力增强方法，覆盖了多个模型架构，消融分析系统。但未在闭源模型（如ChatGPT）上测试，因为需要白盒访问隐藏状态。

## 6. 主要结论与发现
- 中间层是联想行为的关键区域，修改中间层表示可有效调节联想强度。
- 幻觉响应可提取可靠的控制方向。
- FlexAC在幻觉抑制（CHAIR降低29%）和创造力提升（VDAT提高，Creation-MMBench奖励提升5.8倍）上均达到最优，同时保持通用能力。
- 自适应强度校准（SIC）可避免过度干预导致输出质量下降。
- 任务特定向量集成进一步增强了多样创造性任务的表现。

## 7. 优点
- **无需训练**：方法轻量，仅需一次离线向量构造和推理时注入，计算开销小。
- **灵活性**：通过调节控制系数 $\alpha$ 可双向切换（增强忠实性或增强创造性），并支持任务特定方向集成。
- **理论基础**：基于对内部表示的系统分析（特征距离分析、层干预实验），揭示了联想行为的神经机制，方法有明确动机。
- **新评估指标**：提出了VDAT，直接衡量联想推理能力，并经过用户研究验证。
- **全面实验**：在多个模型和benchmark上验证，消融实验充分，扩展了通用能力评估。

## 8. 不足与局限
- **白盒依赖**：需要访问模型中间层的隐藏状态，不适用于黑盒模型（如GPT-4o、Claude等）。
- **通用能力稳定性**：部分通用benchmark上（如MM-Vet）FlexAC-C/P与基线相比略有下降，虽然整体保持可接受范围，但并非在所有任务上都能同时提升。
- **任务特定向量质量依赖GPT-4o**：构建任务特定向量时需要GPT-4o生成高联想样本，存在对第三方模型依赖。
- **安全性风险**：增强联想能力可能增加生成幻觉或错误关联的风险，虽然论文讨论了伦理问题，但实际部署需额外安全措施。
- **实验覆盖**：主要在三个开源模型上测试，未在更大规模模型（如LLaVA-NeXT、VILA等）上验证；数据集集中于COCO/Creation-MMBench，未见长尾或专业领域评估。

（完）
