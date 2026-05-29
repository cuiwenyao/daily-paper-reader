---
title: "The First Few Tokens Are All You Need: An Efficient and Effective Unsupervised Prefix Fine-Tuning Method for Reasoning Models"
title_zh: 前几个词就够了：面向推理模型的高效无监督前缀微调方法
authors: "Ke Ji, Jiahao Xu, Tian Liang, Qiuzhi Liu, Zhiwei He, Xiaoyuan Liu, Xingyu Chen, Junying Chen, Benyou Wang, Zhaopeng Tu, Haitao Mi, Dong Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1SCMFCGliM"
tags: ["query:ns-xai"]
score: 4.0
evidence: 无监督前缀微调提升推理模型能力
tldr: "针对提升LLM推理能力需要标注数据或大量采样的问题，本文提出无监督前缀微调UPFT，利用前缀自一致性——不同解轨迹中共享的初始推理步骤——仅训练前几个token即可增强推理。在多个基准上，UPFT性能与拒绝采样微调等监督方法持平，而训练时间减少90%，为高效提升模型推理能力提供了低成本方案。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 638}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 620, \"height\": 525}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1274, \"height\": 560}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 240}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1scmfcglim/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1364, \"height\": 2160}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 879}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 725}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1scmfcglim/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1006, \"height\": 415}]"
motivation: 现有推理增强方法依赖标注数据或昂贵采样，成本高。
method: 利用前缀自一致性，仅对初始8个token进行无监督微调。
result: 在数学推理等任务上达到监督方法同等性能，训练时间大幅缩短。
conclusion: 无监督前缀微调是推理模型训练的实用轻量级替代方案。
---

## Abstract
Improving the reasoning capabilities of large language models (LLMs) typically requires supervised fine-tuning with labeled data or computationally expensive sampling. We introduce Unsupervised Prefix Fine-Tuning (UPFT), which leverages the observation of Prefix Self-Consistency -- the shared initial reasoning steps across diverse solution trajectories -- to enhance LLM reasoning efficiency. By training exclusively on the initial prefix substrings (as few as 8 tokens), UPFT  removes the need for labeled data or exhaustive sampling. Experiments on reasoning benchmarks show that UPFT matches the performance of supervised methods such as Rejection Sampling Fine-Tuning, while reducing training time by 75\% and sampling cost by 99\%. Further analysis reveals that errors tend to appear in later stages of the reasoning process and that prefix-based training preserves the model’s structural knowledge. This work demonstrates how minimal unsupervised fine-tuning can unlock substantial reasoning gains in LLMs, offering a scalable and resource-efficient alternative to conventional approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：提升大语言模型（LLM）的推理能力通常依赖有监督微调（需要大量标注数据）或计算昂贵的采样方法（如拒绝采样、自训练），这些方法资源消耗大、流程复杂。本文旨在探索一种无需标注数据、无需大量采样的轻量级无监督微调方法，以高效提升模型推理能力。
- **核心问题**：如何利用模型自身生成轨迹中的共享前缀信息，在不借助外部监督的情况下实现有效的推理增强。
- **整体含义**：提出无监督前缀微调（UPFT）方法，仅需模型对每个问题进行一次采样，取前若干 token（如8个）进行微调，即可达到与有监督拒绝采样微调（RFT）相当的性能，同时大幅降低训练和采样成本。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：基于观察“前缀自一致性（Prefix Self-Consistency）”，即不同解题轨迹在初始推理步骤上高度一致，而错误往往出现在推理后期。因此，仅学习正确轨迹的开头部分即可引导模型生成更可靠的完整推理。
- **关键技术细节**：
  - 从贝叶斯视角推导，将SFT目标分解为前缀覆盖度和前缀准确率，证明仅对前缀进行学习可以最大化下界。
  - 具体步骤：
    1. 对每个训练问题，从基模型采样一个推理轨迹，仅截取前缀子串 \( r_{<t} \)（如8-32 token）。
    2. 在前缀上使用负对数似然（NLL）损失进行SFT。
    3. 为避免灾难性遗忘，保留少量（如10%）完整轨迹进行“结构调优”（structure tuning），使用任务模板引导模型输出完整答案。
  - 方法无需标签、无需拒绝采样，故适用于无监督场景。
- **算法流程**（文字说明）：
  - 输入：问题集 \( D \)，前缀长度 \( t \)，结构调优比例 \( p\% \)。
  - 对每个问题，从模型采样一个输出，截取前 \( t \) 个 token 作为前缀，加入前缀数据集 \( D_p \)；同时将完整输出加入完整数据集 \( D_f \)（比例为 \( p\% \)）。
  - 对 \( D_p \) 和 \( D_f \) 分别进行SFT（使用相同损失函数），联合优化。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 训练数据：PRM-12K（12K实例）、OMI2（600K）、LIMO（819）、U-Hard（100K，本文新收集的困难问题集）。
  - 测试基准：GSM8K、MATH500、AIME2024、GPQA Diamond（涵盖数学、逻辑、常识推理）。
- **对比方法**：
  - 监督场景：RFT（拒绝采样微调，16次采样+标签过滤）、V-STaR（训练验证器+最佳选择）。
  - 无监督场景：标准SFT（全 token 微调，无过滤）。
- **实验设置**：
  - 骨干模型：Llama-3.1-8B-Instruct、Qwen2.5-Math-7B-Instruct、DeepSeek-R1-Distill-Qwen-7B。
  - 两种采样场景：无监督（每问题1个样本，无过滤）、有监督（每问题16个样本，用真实答案过滤）。
  - 超参数：学习率1e-6或2e-6，batch size 1，梯度累积8步，最大长度4096/16384，epoch 1-3。

## 4. 资源与算力

- **文中未明确说明使用的GPU型号、数量及训练总时长**，仅提供了相对效率指标：
  - 训练时间减少75%以上（与全token SFT相比）。
  - 采样时间减少99%以上（与RFT 16次采样相比）。
  - 训练序列长度缩短82.6%-94.7%，因此可推断其计算资源需求远低于传统方法。
- 作者承诺将开源代码，但未提供具体算力细节。这是一个信息缺失点。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验（无监督）：在4个数据集×3个骨干模型上进行，共20组结果（表1）。
  - 主实验（有监督）：在3个骨干模型上对比RFT、V-STaR、UPFT等，共22组结果（表2）。
  - 消融实验：前缀长度（7种取值）、结构调优比例（6种取值）分别对2个模型进行，共26组（图3）。
  - 额外分析：前缀覆盖度、前缀成功率（图2），已证明现象存在。
- **充分性判断**：实验覆盖了多种模型、数据集、监督/无监督场景，并进行了充分的消融分析。实验设计公平（相同超参数），且结果清晰展示了优势。整体较为充分。

## 6. 论文的主要结论与发现

1. **前缀自一致性现象**：不同轨迹在初始推理步骤上高度一致，错误出现在后期。
2. **UPFT方法有效**：在无监督场景下，UPFT显著优于传统SFT；在有监督场景下，UPFT性能与RFT/V-STaR持平甚至更好，且资源消耗极低。
3. **U-Hard数据集价值**：困难问题能更好发挥前缀学习优势。
4. **结构调优比例最佳为10%**，过多完整轨迹反而导致性能下降。
5. **UPFT可与标签过滤结合**进一步提升精度，同时保持计算优势。

## 7. 优点

- **创新性**：识别并利用前缀自一致性，是首个仅用少量前缀token进行无监督推理增强的方法。
- **效率极高**：相比RFT减少采样成本99%、训练时间75%，适用于资源受限场景。
- **通用性**：适用于不同架构（Llama、Qwen、DeepSeek）和不同数据集，无监督/有监督场景均可。
- **理论支撑**：从贝叶斯视角推导了前缀学习的合理性，提供了严谨的数学解释。
- **实验全面**：覆盖多模型、多数据集、多场景，消融实验完整。

## 8. 不足与局限

- **计算资源未明确**：未公布GPU型号、数量、总时长，可复现性略受影响。
- **骨干模型规模有限**：仅测试7B/8B模型，未在更大规模（如32B、70B）上验证，泛化性待证明。
- **前缀长度依赖启发式选择**：不同模型最优前缀长度不同（8-128 token），缺乏自适应选择策略。
- **仅针对数学推理任务**：未探索在代码、常识推理等领域的有效性。
- **结构调优比例对数据集大小敏感**：小数据集（LIMO）需更高比例（30%），不统一。
- **潜在偏差**：U-Hard数据集由作者自行收集筛选，可能存在选择偏差。

（完）
