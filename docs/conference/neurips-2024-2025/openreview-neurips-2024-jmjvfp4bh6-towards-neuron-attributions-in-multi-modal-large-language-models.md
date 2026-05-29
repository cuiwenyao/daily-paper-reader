---
title: Towards Neuron Attributions in Multi-Modal Large Language Models
title_zh: 迈向多模态大语言模型的神经元归因
authors: "Junfeng Fang, Zac Bi, Ruipeng Wang, Houcheng Jiang, Yuan Gao, Kun Wang, An Zhang, Jie Shi, Xiang Wang, Tat-Seng Chua"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=jMJVFP4BH6"
tags: ["query:ns-xai"]
score: 9.0
evidence: 多模态大语言模型神经元归因可解释性方法
tldr: 针对多模态大语言模型（MLLM）内部机制解释困难的问题，本文提出神经元归因方法NAM，通过归因分析揭示神经元学习到的模态特定语义知识，并发现跨模态不变性等有趣性质。实验表明，NAM有效解释多模态模型行为，为提升MLLM可解释性提供了关键工具。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-jmjvfp4bh6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jmjvfp4bh6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jmjvfp4bh6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 427, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 1109, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 813, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 676, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1420, \"height\": 760, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1459, \"height\": 817, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1248, \"height\": 942, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jmjvfp4bh6/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1245, \"height\": 961, \"label\": \"Table\"}]"
motivation: 现有神经元归因方法主要针对文本LLM，多模态场景下神经元知识归属不明。
method: 提出NAM方法，利用梯度回传和模态特征映射对MLLM神经元进行归因。
result: 成功识别出多模态神经元，并发现跨模态不变性等新现象。
conclusion: 神经元归因是理解多模态模型内部知识结构的有力手段，对构建可信MLLM至关重要。
---

## Abstract
As Large Language Models (LLMs) demonstrate impressive capabilities, demystifying their internal mechanisms becomes increasingly vital. Neuron attribution, which attributes LLM outputs to specific neurons to reveal the semantic properties they learn, has emerged as a key interpretability approach. However, while neuron attribution has made significant progress in deciphering text-only LLMs, its application to Multimodal LLMs (MLLMs) remains less explored. To address this gap, we propose a novel Neuron Attribution method tailored for MLLMs, termed NAM. Specifically, NAM not only reveals the modality-specific semantic knowledge learned by neurons within MLLMs, but also highlights several intriguing properties of neurons, such as cross-modal invariance and semantic sensitivity. These properties collectively elucidate the inner workings mechanism of MLLMs, providing a deeper understanding of how MLLMs process and generate multi-modal content. Through theoretical analysis and empirical validation, we demonstrate the efficacy of NAM and the valuable insights it offers. Furthermore, leveraging NAM, we introduce a multi-modal knowledge editing paradigm, underscoring the practical significance of our approach for downstream applications of MLLMs.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- 论文聚焦于**多模态大语言模型（MLLM）的内部可解释性**问题。
- 现有神经元归因方法主要针对纯文本LLM，直接迁移到MLLM面临三大挑战：
  1. **语义噪声**：生成的图像包含目标语义（如狗）之外的干扰元素（如草坪），导致归因不准确。
  2. **低效性**：梯度/因果归因需要大量前向/反向传播，MLLM的多模块结构进一步加剧计算开销。
  3. **神经元混杂**：同一语义下，文本生成神经元（T-neuron）和图像生成神经元（I-neuron）分布不同，归因结果冲突。
- 论文提出**NAM（Neuron Attribution for MLLMs）**，旨在揭示MLLM中神经元学习的**模态特定语义知识**，并发现跨模态不变性等性质，为模型理解、编辑和可信应用提供基础。

### 2. 论文提出的方法论
- **核心思想**：分模态归因，解耦文本和图像通路；利用激活而非梯度实现高效计算；通过图像分割排除语义噪声。
- **关键技术细节**：
  - **图像归因（I-Neuron）**：
    - Step1：使用EVA02分割出目标语义区域，再用Diffuser-Interpreter将图像区域归因到最后一层表示h<sup>L</sup>，得到重要性向量R。
    - Step2：将h<sup>L</sup>展开为各层FFN输出之和，定义神经元u<sub>k</sub><sup>l</sup>的直接贡献s<sub>k</sub><sup>l</sup> = a<sub>k</sub><sup>l</sup> (W<sub>out</sub><sup>l</sup>)<sub>k</sub> R<sup>⊤</sup>，再结合激活值a<sub>k</sub><sup>l</sup>的归一化最大值得最终分数ŝ<sub>k</sub><sup>l</sup>。
  - **文本归因（T-Neuron）**：
    - 类似地，将输出y展开并利用W<sub>u</sub>投影到词汇空间，定义神经元对输出词p的贡献c<sub>k,p</sub><sup>l</sup> = a<sub>k</sub><sup>l</sup> (W<sub>u</sub>)<sub>p</sub> (W<sub>out</sub><sup>l</sup>)<sub>k</sub>，并通过最大语义筛选得到s<sub>k</sub><sup>l</sup>。
  - **图像编辑应用**：通过扰动I-neuron的权重矩阵列，使h<sup>L</sup>从原语义转向目标语义，实现训练自由图像编辑。
- **公式**（文字说明）：使用残差流展开和加权最大函数，避免梯度计算，兼顾直接和间接贡献。

### 3. 实验设计
- **数据集**：COCO（80个物体类别，每张图像5个标题），随机选取1000张图像用于分布分析，500张用于属性验证。
- **Benchmark**：目标模型为GILL和NExT-GPT；对比方法含三大类共6种：
  - 激活类：AcT（仅激活值）、AcU（激活×输出词投影）
  - 梯度类：GraD（梯度）、GraT（梯度×激活）、GraI（梯度积分）
  - 因果类：CE（扰动后输出变化）
- **评估指标**：语义相关性用CLIPScore、BERTScore、MoverScore、BLEURT；跨样本不变性用10次重复试验的重叠比例；特异性用Top-500神经元中专属神经元数量及对其他语义的敏感度阈值；图像编辑用编辑前后h<sup>L</sup>的ℓ2范数变化。
- **实验数量**：三个研究问题（RQ1分布、RQ2性质、RQ3图像编辑），每个问题包含多组定量和定性结果；消融实验通过对比AcT、AcU实现；额外在NExT-GPT上重复验证。

### 4. 资源与算力
- 文中明确提到使用**Quadro RTX 6000（24GB）**、**40GB A100**、**80GB H100**作为计算设备。
- 未说明具体训练/推理时长或GPU数量，仅提及“代表性消费级GPU和数据中心GPU”。

### 5. 实验数量与充分性
- 实验覆盖分布分析、三种神经元属性验证、图像编辑任务，**较为全面**。
- 在COCO数据集上对GILL和NExT-GPT两个模型均做了测试，**保证了跨模型泛化**。
- 对比了6种基线，覆盖主要归因类别，**对比公平**。
- 消融实验隐含在AcT/AcU对比中，验证了直接贡献与间接贡献互补的有效性。
- 局限：仅涉及图像和文本模态，未扩展到视频、音频；仅两个模型；依赖外部分段（EVA02）和归因工具（Diffuser-Interpreter）。

### 6. 论文的主要结论与发现
- **分布特征**：T/I神经元主要分布在中间及高层，且部分重叠但显著区分，证明神经元具有模态特异性。
- **语义相关性**：NAM识别的神经元与目标语义的匹配度显著高于基线方法（CLIPScore等指标领先）。
- **跨样本不变性**：NAM在10次重复中识别稳定神经元，平均不变性比基线高16.83%。
- **语义特异性**：NAM识别的神经元对特定语义敏感，而对其他语义响应低。
- **图像编辑应用**：NAM定位的I-neuron进行编辑所需扰动比基线平均少40.2%，比最好基线少15%，验证了归因的有效性和实用性。

### 7. 优点
- **创新性**：首次系统提出针对MLLM的神经元归因方法，解决语义噪声、低效、模态混杂三大难题。
- **高效性**：仅依赖激活值，无需梯度或多次前向传播，计算成本低。
- **可解释性**：揭示了跨模态不变性、语义特异性等有趣现象，加深对MLLM工作机制的理解。
- **实用性**：成功用于知识编辑（图像编辑），且扰动小、效果好。
- **可迁移性**：方法设计不限于图像-文本，可推广至其他模态（如音频、视频）的归因。

### 8. 不足与局限
- **模态覆盖不足**：实验仅验证文本和图像模态，未涉及音频、视频等。
- **模型种类有限**：仅测试GILL和NExT-GPT，未覆盖更多主流MLLM（如LLaVA、MiniGPT-4等）。
- **依赖外部工具**：图像分割和扩散模型归因依赖EVA02和Diffuser-Interpreter，这些工具可能引入误差或限制应用场景。
- **偏倚风险**：未讨论归因结果可能因数据集、提示词或模型变体而偏移；图像编辑部分仅定性展示，缺乏定量评估（如生成质量、语义保真度）。
- **理论证明不足**：对间接贡献的启发式优化（取最大值）缺乏严格理论解释。

（完）
