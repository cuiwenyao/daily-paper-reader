---
title: "SPEX: Scaling Feature Interaction Explanations for LLMs"
title_zh: SPEX：为大语言模型扩展特征交互解释
authors: "Justin Singh Kang, Landon Butler, Abhineet Agarwal, Yigit Efe Erginbas, Ramtin Pedarsani, Bin Yu, Kannan Ramchandran"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pRlKbAwczl"
tags: ["query:ns-xai"]
score: 7.0
evidence: 为大语言模型扩展特征交互解释
tldr: 大语言模型中特征交互的解释方法难以扩展到长输入。本文提出SPEX，一种模型无关的交互归因算法，利用稀疏傅里叶变换高效识别重要交互，支持长达1000个token的输入。实验表明其在多个长文本数据集上有效，为LLM可解释性提供了规模化工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1740, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1760, \"height\": 1178, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 801, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1752, \"height\": 1047, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1758, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1633, \"height\": 998, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1412, \"height\": 1434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1580, \"height\": 1457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-prlkbawczl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1394, \"height\": 388, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-prlkbawczl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1384, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-prlkbawczl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1519, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-prlkbawczl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 615, \"label\": \"Table\"}]"
motivation: 现有特征交互解释方法限于短输入，无法满足LLM长上下文需求。
method: SPEX结合稀疏傅里叶变换和信道解码算法，高效识别重要交互。
result: 在三个长文本数据集上，SPEX有效扩展了交互归因规模。
conclusion: SPEX提供了可扩展的LLM特征交互解释方法。
---

## Abstract
Large language models (LLMs) have revolutionized machine learning due to their ability to capture complex interactions between input features. Popular post-hoc explanation methods like SHAP provide *marginal* feature attributions, while their extensions to interaction importances only scale to small input lengths ($\approx 20$). We propose *Spectral Explainer* (SPEX), a model-agnostic interaction attribution algorithm that efficiently scales to large input lengths ($\approx 1000)$. SPEX exploits underlying natural sparsity among interactions—common in real-world data—and applies a sparse Fourier transform using a channel decoding algorithm to efficiently identify important interactions. We perform experiments across three difficult long-context datasets that require LLMs to utilize interactions between inputs to complete the task. For large inputs, SPEX outperforms marginal attribution methods by up to 20\% in terms of faithfully reconstructing LLM outputs. Further, SPEX successfully identifies key features and interactions that strongly influence model output. For one of our datasets, *HotpotQA*, SPEX provides interactions that align with human annotations. Finally, we use our model-agnostic approach to generate explanations to demonstrate abstract reasoning in closed-source  LLMs (*GPT-4o mini*) and  compositional reasoning in vision-language models.

---

## 论文详细总结（自动生成）

# SPEX：为大语言模型扩展特征交互解释——论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：大语言模型（LLM）依赖输入特征之间的复杂交互来完成推理，但现有的模型无关解释方法存在两大局限性：
  - 边际归因方法（如SHAP、LIME）只能给出单个特征的重要性，无法捕捉特征间的交互（例如“never fails”这个双重否定结构在情感分析中是关键，但SHAP错误地将正面归因于“never”和“fails”两个词）。
  - 交互归因方法（如Faith-Shap、Shapley-Taylor）虽然能建模交互，但计算复杂度为$O(n^d)$，只能处理输入长度$n\approx 20$，无法扩展到LLM的长上下文（$n\approx 1000$）。
- **整体含义**：论文旨在提出一种可扩展的交互归因算法，使模型解释能够处理长输入，从而增强对高价值应用（如医疗诊断、蛋白质设计）中LLM决策的信任，并辅助调试和模型改进。

## 2. 论文提出的方法论：核心思想、关键技术细节、流程
- **核心思想**：利用LLM输出通常由少量稀疏交互驱动的天然稀疏性，将交互搜索转化为稀疏傅里叶变换问题，并借助信道解码算法高效识别重要交互。
- **关键技术细节**：
  - **傅里叶变换视角**：将LLM的“值函数”$f(m)$（$m$为掩码模式）表示为傅里叶级数$f(m)=\sum_k (-1)^{\langle m,k\rangle}F(k)$，其中$k$代表特征子集（交互），$F(k)$为傅里叶系数。目标是寻找少量重要$k$并估计$\hat{F}(k)$，构建低复杂度代理函数$\hat{f}$。
  - **利用稀疏性**：实证表明深度学习的值函数是稀疏且低度的（重要交互的$|k|\ll n$）。
  - **掩码设计**：通过BCH码（一种代数信道编码）构造掩码模式。利用**混叠性质**和**平移性质**，将搜索交互空间等效为在噪声信道中解码消息。具体地，使用随机线性矩阵$M_c$和BCH奇偶校验矩阵$P$生成掩码，总采样数约为$C\cdot 2^b \cdot t\log(n)$（$C=3$，$b=8$，$t=5$）。
  - **消息传递算法**：构建二分图（观测节点与变量节点），通过Berlekamp-Massey算法（硬解码或软解码，如Chase解码）从混叠后的观测中解码出重要$k$，并更新$\hat{F}(k)$，迭代直至收敛。
- **算法流程**：三步：
  1. **掩码生成与模型推理**：根据参数确定掩码集，查询LLM输出（或对数概率等标量值）。
  2. **学习代理函数**：对采样数据做快速傅里叶变换，通过消息传递解码出重要$k$及其系数，得到$\hat{f}$。
  3. **提取交互归因**：利用$\hat{f}$的傅里叶系数转换为常见的交互归因分数（如Shapley值、Banzhaf交互指数）。

## 3. 实验设计：数据集、场景、Benchmark、对比方法
- **数据集**：
  - **Sentiment**：IMDb电影评论（增补SST），词级特征，情感二分类。输入长度$n$从8到2047。
  - **HotpotQA**：多文档多跳问答，句子级特征，答案需从2-3个句子推理。$n$从8到127。
  - **DROP**：离散推理阅读理解，单词级特征，涉及计数、排序等。$n$从32到1023。
- **场景**：每个任务要求LLM必须利用特征交互才能正确回答。
- **Benchmark/指标**：
  - **忠诚度 (Faithfulness)**：$R^2=1-\frac{\|\hat{f}-f\|^2}{\|f-\bar{f}\|^2}$，在10,000个随机掩码上评估。
  - **Top-r移除 (Removal)**：移除对$\hat{f}$贡献最大的$r$个特征后，测量模型输出变化。
  - **恢复率@r (Recovery Rate@r)**：在HotpotQA上，评估算法找出的交互与人工标注句子的重叠比例。
- **对比方法**：
  - 边际归因：LIME、SHAP、Banzhaf。
  - 交互归因：Faith-Shap、Faith-Banzhaf、Shapley-Taylor（可计算时）。
  - 所有方法均使用相同训练掩码数进行比较。

## 4. 资源与算力
- 论文提到实验在 **Nvidia L40S GPU 和 A100 GPU** 上运行。
- 未明确说明使用的GPU数量、总训练时长或推理次数，仅提及对每个数据样本查询LLM的次数由掩码数量决定（如Sentiment中$n=1024-2047$时约43,008次查询）。
- 点评：算力细节不透明，难以复现成本，但考虑到LLM推理开销，整体计算量仍较大。

## 5. 实验数量与充分性
- **实验数量**：
  - 三个数据集（Sentiment、HotpotQA、DROP）覆盖分类、多跳问答、离散推理任务。
  - 每个数据集按$n$划分多个区间（如Sentiment有8个区间，HotpotQA有4个区间）。
  - 对比了4种边际归因和3种交互归因，并在不同$n$下运行可计算方法。
  - 进行了超参数消融（$b=4,6,8,10$；$C=1,2,3,4$；$t=1-6$），见附录B.5.1。
  - 额外案例研究：封闭源LLM（GPT-4o mini）的抽象推理错误调试；视觉语言模型（LLaVA-NeXT-Mistral-7B）的视觉问答。
- **充分性与公平性**：
  - 实验设计较为全面，忠诚度和移除任务覆盖不同$n$区间，且与最强基线（如高阶Faith-Banzhaf）比较。
  - 方法比较中，交互归因方法因复杂度限制无法在大$n$下运行，SPEX是唯一能覆盖所有$n$的交互方法。
  - 消融实验验证了默认参数（$b=8, C=3, t=5$）的合理性。
  - 潜在不足：未在所有基线均能运行的所有$n$下比较（例如SHAP在某些大$n$下忠诚度极低）；恢复率实验仅在HotpotQA上且针对$r=10$，未系统研究不同$r$的影响。

## 6. 论文的主要结论与发现
- **忠诚度**：SPEX在所有三个数据集上忠诚度优于所有边际归因方法（最高提升约20%），并与可运行的高阶交互归因（如Faith-Banzhaf 4阶）相当。
- **计算效率**：SPEX的运行时间随$n$增长几乎不变（因掩码数仅对数增长），而高阶交互归因方法呈指数增长，在$n>128$时已无法计算。
- **特征移除**：SPEX在HotpotQA和DROP上移除任务表现优于所有基线；在Sentiment上与2阶交互方法竞争。
- **交互恢复**：在HotpotQA上，SPEX以更少的训练掩码获得最高交互恢复率（+6.2%~+9.2%），并成功识别出人工标注的三个关键句子。
- **案例研究**：
  - **调试错误**：对于修改后的“电车难题”，GPT-4o mini和Llama-3.2-3B均频繁答错。SPEX揭示了误导模型的关键交互（如“pulling lever”与“trolley”的负交互），而SHAP仅给出片面的边际归因。
  - **视觉问答**：在“狗玩篮球”图像中，SPEX识别出“狗”和“篮球”图像块之间的正交互（表明模型理解了“玩”的动作），而SHAP只归因于单个对象。
- 结论：SPEX是第一个能在$n\approx 1000$规模下有效计算特征交互归因的模型无关方法，兼具忠诚度和可解释性。

## 7. 优点：方法或实验设计上的亮点
- **理论创新**：将交互归因问题转化为稀疏傅里叶变换，并利用信道编码（BCH码）实现高效搜索，避免穷举所有$O(n^d)$交互。
- **模型无关**：适用于任何黑盒模型（包括封闭源LLM、视觉语言模型）。
- **计算可扩展**：掩码数量仅随$n$对数增长（$O(2^b t \log n)$，$b$固定），且可并行推理。
- **实验设计扎实**：采用多数据集、多指标、多基线对比，并包含消融研究和案例应用，验证了方法在不同场景下的有效性和实用性。
- **可解释性强**：能提供具体的有意义交互（如“never fails”双重否定、“Summer in Brazil & Rio Carnival”等），便于人类理解模型行为。

## 8. 不足与局限
- **对稀疏性的依赖**：算法假设值函数的傅里叶表示是稀疏的，若真实交互不稀疏（例如所有特征重要性相当），SPEX可能失效，论文未充分讨论这种情况。
- **样本量仍可能偏高**：尽管减少了对$n$的依赖，但对于$n=1000$仍需约43,000次模型推理（$b=8$），当推理成本极高时（如大型LLM或蛋白质模型）仍可能难以承受。
- **交互解释的局限性**：从大量交互中人工筛选关键交互仍需手动解析，可视化工具不足；论文未深入探讨如何自动提炼简洁、易于理解的解释。
- **非自适应采样**：掩码模式预先确定，未根据模型反馈动态调整，可能浪费部分样本。论文提及未来工作可考虑自适应算法。
- **实验范围**：
  - 视觉问答仅使用了一个简单图像例子，缺乏定量评估。
  - 仅测试了最大$n\approx 2000$，未探索更长上下文（如整个书籍）。
  - 未系统评估在不同模型架构（如编码器-only、解码器-only）上的通用性（虽然提及了蛋白质语言模型）。
- **公平性风险**：解释方法可能被过度信赖或误用，论文虽在Impact Statement中提及避免过度解释，但未具体讨论偏差风险评估。

（完）
