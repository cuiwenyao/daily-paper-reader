---
title: "The First Few Tokens Are All You Need: An Efficient and Effective Unsupervised Prefix Fine-Tuning Method for Reasoning Models"
title_zh: 只需前几个Token：一种高效的无监督前缀微调推理模型方法
authors: "Ke Ji, Jiahao Xu, Tian Liang, Qiuzhi Liu, Zhiwei He, Xiaoyuan Liu, Xingyu Chen, Junying Chen, Benyou Wang, Zhaopeng Tu, Haitao Mi, Dong Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1SCMFCGliM"
tags: ["query:ns-xai"]
score: 6.0
evidence: 无监督前缀微调增强LLM推理
tldr: 该论文提出无监督前缀微调（UPFT），利用推理轨迹中的前缀自一致性，仅用前几个token进行微调即可提升LLM推理能力，无需标注数据或大量采样。实验表明UPFT在推理基准上达到与有监督方法相当的性能，训练时间大幅减少。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 620, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1274, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1364, \"height\": 2160, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 879, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 725, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1006, \"height\": 415, \"label\": \"Table\"}]"
motivation: 现有LLM推理增强需要标注数据或昂贵采样。
method: UPFT仅对推理轨迹的初始前缀子串进行微调，训练前缀自一致性目标。
result: 在推理基准上，UPFT匹配了有监督拒绝采样微调的性能，训练时间显著降低。
conclusion: 前缀自一致性是一种高效的无监督信号，可用于提升LLM推理能力。
---

## Abstract
Improving the reasoning capabilities of large language models (LLMs) typically requires supervised fine-tuning with labeled data or computationally expensive sampling. We introduce Unsupervised Prefix Fine-Tuning (UPFT), which leverages the observation of Prefix Self-Consistency -- the shared initial reasoning steps across diverse solution trajectories -- to enhance LLM reasoning efficiency. By training exclusively on the initial prefix substrings (as few as 8 tokens), UPFT  removes the need for labeled data or exhaustive sampling. Experiments on reasoning benchmarks show that UPFT matches the performance of supervised methods such as Rejection Sampling Fine-Tuning, while reducing training time by 75\% and sampling cost by 99\%. Further analysis reveals that errors tend to appear in later stages of the reasoning process and that prefix-based training preserves the model’s structural knowledge. This work demonstrates how minimal unsupervised fine-tuning can unlock substantial reasoning gains in LLMs, offering a scalable and resource-efficient alternative to conventional approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
当前提升大型语言模型（LLM）推理能力的主流方法依赖监督微调（使用标注数据）或计算昂贵的采样过滤（如拒绝采样微调RFT、自我训练STaR等）。这些方法需要大量标注数据、多轮采样和验证，资源消耗大且难以在无标签场景下应用。论文旨在探索一种**无监督、极低开销**的推理增强方法，仅需模型自身生成的响应前缀即可有效提升推理性能，避开对标注数据和昂贵采样的依赖。

## 2. 论文提出的方法论
### 核心思想：前缀自一致性（Prefix Self-Consistency）
- 观察到：对于同一问题，LLM生成的多条不同推理轨迹（正确或错误）在**初始几步（前缀）高度一致**，而错误主要出现在后续步骤。
- 因此，仅对**原始模型生成的响应前缀**（例如8个token）进行微调，可以高效捕捉正确推理结构，同时避免对完整轨迹进行过滤或验证。

### 关键技术细节
1. **前缀采样**：从基础模型对每个问题只取一次生成（无监督），截取前t个token作为训练数据。
2. **结构微调**：为避免灾难性遗忘，采用**数据拆分策略**：大部分数据（如90%）用前缀训练，少部分（如10%）用完整轨迹训练（仍无标注）。整体目标函数为两部分NLL损失之和。
3. **无需拒绝采样或标签验证**：直接使用模型输出的前缀，不依赖最终答案正确与否。

### 公式/流程（文字说明）
- 对每个输入x，从模型采样前缀r_<t（长度为t）。
- 最大化前缀的对数似然 log p(r_<t|x) 加上少量完整轨迹的对数似然（无标签）。
- 与传统RFT相比，UPFT省去了1(r(k), y)的标签过滤项，训练和采样成本大幅降低。

## 3. 实验设计
### 数据集与基准
- **训练数据集**：PRM-12K（12K实例）、OMI2（600K）、LIMO（819）、**U-Hard**（100K，新构建的困难问题集）。
- **测试基准**：GSM8K、MATH500、AIME2024、GPQA Diamond。
- **场景**：
  - **无监督采样**：每个问题只生成一次，不根据答案正确性过滤。
  - **监督采样**：每个问题生成16次，用标签过滤正确轨迹（用于与RFT对比）。

### 对比方法
- 基线：原始模型（未微调）、常规SFT（无过滤）、RFT（拒绝采样微调）、V-STaR（训练验证器）。
- 主实验：UPFT vs. SFT（无监督），UPFT vs. RFT/V-STaR（监督）。

### 消融实验
- 前缀长度（1～64 token）的影响。
- 结构微调比例（0%～100%）的影响。
- 在PRM-12K数据集上用Llama-3.1-8B和Qwen2.5-Math-7B进行。

## 4. 资源与算力
论文**未明确说明**具体GPU型号、数量或单次训练时长。但提供了以下效率指标：
- UPFT使训练序列长度减少82.6%～94.7%（例如U-Hard样本平均68.2 token vs SFT的393.3 token）。
- 训练时间减少约75%，采样成本减少99%以上（相比于RFT）。
- 在DeepSeek-R1-Distill-Qwen-7B上，UPFT使用5M采样token，而RFT使用318M。

## 5. 实验数量与充分性
### 实验数量
- **主要实验**：在4个训练集（PRM、OMI2、LIMO、U-Hard）和4个测试基准上，覆盖3种不同架构（Llama-3.1-8B、Qwen2.5-Math-7B、DeepSeek-R1-Distill-Qwen-7B），共约12组无监督+监督对比。
- **消融实验**：2组（前缀长度、结构比例）和多模型验证。
- **监督场景**：与RFT、V-STaR比较3个模型。

### 充分性与客观性
- **充分性**：实验覆盖了不同规模数据集（从0.8K到600K）、不同难度（包含高难AIME2024）和不同模型类型（通用、数学专用、长推理模型），对比方法包括主流基线，消融分析关键超参数。
- **客观公平**：UPFT与SFT/RFT使用相同超参数和推理设置，结果报告准确率，无明显偏见。但未报告多次运行的标准差或置信区间，可重复性可接受但统计显著性未展示。

## 6. 主要结论与发现
1. **UPFT在无监督设置下显著优于常规SFT**（例如U-Hard上平均54.5% vs 51.3%）。
2. **UPFT在监督设置下性能匹配甚至超越RFT和V-STaR**，而训练时间减少75%、采样成本减少99%。
3. **前缀自一致性现象成立**：错误主要出现在推理后期，早期前缀高度一致；仅训练前缀即可保留关键推理结构。
4. **U-Hard高难度数据集最大化UPFT潜力**，在AIME2024上提升10个百分点以上。
5. **UPFT对架构通用**：适用于Llama、Qwen、DeepSeek系列，且对长推理模型（DeepSeek-R1）效果显著。

## 7. 优点
- **极低资源需求**：无需标注数据、无需多次采样、训练序列极短，大幅降低算力和时间成本。
- **高数据效率**：仅需512k～5M token即可达到强基线效果。
- **灵活性与通用性**：可适配不同模型、不同难度数据集，且支持与标签验证无缝集成进一步提升性能。
- **理论支撑**：通过贝叶斯下界推导和实验验证前缀覆盖与精度权衡，方法设计有理论依据。
- **新颖性**：首次提出“前缀自一致性”概念，并据此设计无监督微调方法。

## 8. 不足与局限
- **未验证超大模型（如70B+）**：实验仅限7B/8B规模，对更大模型的扩展性未知。
- **前缀长度选择依赖启发式**：最优前缀长度需根据模型手动调整（8/32/128 token），缺乏自适应选择策略。
- **结构微调比例需调优**：不同数据集最佳比例不同（通常10%，LIMO为30%），需额外调参。
- **缺乏统计不确定性报告**：未给出多次运行的标准差或置信区间，结果可靠性有待加强。
- **无监督场景下性能提升有限**：在简单任务（GSM8K）上增益较小，主要改进来自困难任务。
- **未对非数学推理任务验证**：仅聚焦数学基准，其他领域（常识、逻辑、代码）未涉及。

（完）
