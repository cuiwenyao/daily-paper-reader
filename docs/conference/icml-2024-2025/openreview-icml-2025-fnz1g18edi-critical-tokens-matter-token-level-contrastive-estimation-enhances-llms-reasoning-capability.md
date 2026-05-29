---
title: "Critical Tokens Matter: Token-Level Contrastive Estimation Enhances LLM’s Reasoning Capability"
title_zh: 关键令牌的重要性：令牌级对比估计增强大语言模型推理能力
authors: "Zicheng Lin, Tian Liang, Jiahao Xu, Qiuzhi Liu, Xing Wang, Ruilin Luo, Chufan Shi, Siheng Li, Yujiu Yang, Zhaopeng Tu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fnz1g18EdI"
tags: ["query:ns-xai"]
score: 6.0
evidence: 令牌级分析增强大模型推理能力
tldr: 本文提出关键令牌概念，即推理路径中对错误结果有显著影响的令牌。通过展开采样和对比学习识别并替换关键令牌，在GSM8K和MATH500等数据集上显著提升模型准确率。提供了一种高效定位关键令牌的方法，可解释性提升有限。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fnz1g18edi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnz1g18edi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 693, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnz1g18edi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnz1g18edi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 763, \"height\": 545, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1251, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1498, \"height\": 700, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 559, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1166, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1095, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnz1g18edi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 660, \"height\": 273, \"label\": \"Table\"}]"
motivation: 大模型数学推理中的部分令牌对错误结果起关键作用，但现有方法难以识别。
method: 提出关键令牌定义与识别框架，使用展开采样和对比估计。
result: 在多个数学推理数据集上替换关键令牌后准确率显著提升。
conclusion: 识别关键令牌有助于提升大模型推理性能，但可解释性贡献较间接。
---

## Abstract
Mathematical reasoning tasks pose significant challenges for large language models (LLMs) because they require precise logical deduction and sequence analysis. In this work, we introduce the concept of critical tokens -- elements within reasoning trajectories that significantly influence incorrect outcomes. We present a novel framework for identifying these tokens through rollout sampling and demonstrate their substantial divergence from traditional error tokens. Through extensive experiments on datasets such as GSM8K and MATH500, we show that identifying and replacing critical tokens significantly improves model accuracy. We propose an efficient methodology for pinpointing these tokens in large-scale datasets using contrastive estimation and extend this framework to enhance model training processes with direct preference optimization (DPO). Experimental results on GSM8K and MATH500 benchmarks with the widely used models Llama-3 (8B and 70B) and Deepseek-math (7B) demonstrate the effectiveness of the proposed approach, cDPO. Our results underscore the potential of leveraging critical tokens to reduce errors in reasoning tasks, advancing the development of AI systems capable of robust logical deduction.

---

## 论文详细总结（自动生成）

以下是基于给定论文的详细中文总结，按照要求的要点组织。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在数学推理任务中常因逻辑错误而失败，但现有研究多关注句子或步骤级误差，缺乏对令牌（token）级别的系统性分析。作者发现，某些特定令牌在错误推理轨迹中扮演“关键角色”，一旦替换即可显著提升正确率。
- **整体含义**：引入 **关键令牌（critical tokens）** 概念，即那些在错误轨迹中对最终错误结果有决定性影响的令牌。论文证明关键令牌与人工标注的错误令牌显著不同，并基于此改进直接偏好优化（DPO），提升模型数学推理能力。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过对比估计高效识别关键令牌，并在DPO中对其施加额外惩罚，从而更好区分正负样本。
- **关键技术细节**：
  - **关键令牌的识别（展开采样）**：对每个令牌进行64次展开采样，计算正确率，将首个正确率为0且后续所有令牌正确率均低于5%的令牌标记为关键令牌。
  - **对比估计（CE）**：训练两个模型——正面模型（基于正确轨迹）和负面模型（基于高频错误轨迹）。对每个错误轨迹中的令牌，计算对比得分：
    \[
    \log s_t = (1+\beta)\log P_p(y_t|x,y_{<t}) - \beta\log P_n(y_t|x,y_{<t}) - \log Z
    \]
    得分越低，表示该令牌在正确模型中可能性低、在负面模型中可能性高，即越可能为关键令牌。
  - **cDPO（关键令牌直接偏好优化）**：将DPO扩展至令牌级别，仅修改负面示例的奖励函数：
    \[
    \phi_s(x,y,s) = \gamma\sum_{t=1}^T (1 - s_t) \log\frac{\pi_\theta(y_t|x,y_{<t})}{\pi_{\text{ref}}(y_t|x,y_{<t})}
    \]
    损失函数为：
    \[
    \ell_{\text{cDPO}} = -\sum_{i=1}^M \log\sigma\big(\phi(x_i,y_i^p) - \phi_s(x_i,y_i^n,s_i^n)\big)
    \]
    通过加权 \(1-s_t\) 降低关键令牌的生成概率。

### 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：GSM8K和MATH500（MATH的子集，难度分布与完整测试集一致）。
- **评估方式**：使用少样本提示（GSM8K 8-shot，MATH500 4-shot），温度固定为0进行准确率测试；部分实验采用不同温度下的Pass@1平均。
- **对比方法**：
  - Baseline（基座模型）
  - +SFT（在正确轨迹上监督微调）
  - +DPO（分别基于基座模型和SFT模型启动）
  - +TokenDPO（带前向KL约束的令牌级DPO）
  - +RPO（增加额外NLL损失的DPO变体）
  - +cDPO（本文方法）
- **模型**：Llama-3-8B-base、Llama-3-70B-base、DeepSeek-math-7B-base；额外在Qwen-2.5-7B/32B上验证。

### 4. 资源与算力

- **文中未明确说明**所使用的GPU型号、数量及具体训练时长。
- 仅提及：所有模型使用LoRA适配器训练；正负模型训练1 epoch（学习率3e-4）；偏好优化训练3 epoch（学习率2e-5，cDPO使用4e-5）。
- 效率分析提到：对比估计的推理成本仅为展开采样的0.002%（以GSM8K为例），但实际硬件配置未披露。

### 5. 实验数量与充分性

- **实验组数**：主要结果涵盖3种模型、2个数据集、6种对比方法；另外包括：
  - 学习曲线分析（DPO、RPO、cDPO的log概率变化）
  - 温度采样实验（0～1.5共7个温度×10次采样）
  - 对比因子β的消融实验（9个值）
  - 在Qwen-2.5模型上的额外验证（2种规模）
- **充分性评价**：整体实验设计全面，覆盖了不同模型规模、多种基线、消融分析和可解释性曲线；使用了显著性检验（p<0.005），结果稳定可靠。但实验领域仅限于数学推理，未在其他任务上验证泛化性。

### 6. 论文的主要结论与发现

- 关键令牌真实存在，且与人工标注的错误令牌有高比例不一致（GSM8K 65%，MATH500 87%）。
- 替换关键令牌可显著提升准确率（Pass@1从0%提升至约30%，Pass@64超过90%）。
- 对比估计高效且与展开采样结果高度一致（AUC 0.77–0.84）。
- cDPO在所有模型和数据集上均超越DPO、TokenDPO、RPO等强基线，平均精度提升2–3个百分点。
- cDPO能更好分离正负样本的log概率：提升正确序列概率的同时降低错误序列概率。

### 7. 优点

- **概念创新**：首次提出“关键令牌”并实证其价值，为令牌级分析提供新视角。
- **方法高效**：对比估计仅需0.002%的计算成本即可近似展开采样结果，适合大规模数据。
- **改进清晰**：cDPO直接利用关键令牌修正DPO的缺陷，简单有效且无需额外人类标注。
- **实验充分**：包含多模型、多数据集、多基线、多温度、消融及扩展验证，结论稳健。

### 8. 不足与局限

- **实验覆盖不足**：仅涉及数学推理任务，未在常识推理、代码生成等场景验证泛化性。
- **计算资源未详述**：硬件配置和训练总时间缺失，影响复现和效率评估。
- **模型容量限制**：所有实验使用LoRA微调，未比较全参数微调的效果，可能低估了关键令牌方法的上限。
- **调参依赖**：对比因子β需手动选择（最优约1.5–1.75），不同任务可能需要重新调整。
- **忽略正确轨迹中的关键令牌**：论文有意避免对正确令牌做类似处理，但理论上正确轨迹中也存在对最终答案影响大的令牌，未来可探索对称处理。
- **安全性/偏差讨论**：作者声明数学任务无伦理风险，但方法本身未讨论对非数学任务的潜在负面影响。

（完）
