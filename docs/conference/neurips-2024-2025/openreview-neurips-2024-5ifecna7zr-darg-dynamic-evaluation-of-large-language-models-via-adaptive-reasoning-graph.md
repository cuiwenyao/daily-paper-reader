---
title: "DARG: Dynamic Evaluation of Large Language Models via Adaptive Reasoning Graph"
title_zh: DARG：通过自适应推理图动态评估大语言模型
authors: "Zhehao Zhang, Jiaao Chen, Diyi Yang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=5IFeCNA7zR"
tags: ["query:ns-xai"]
score: 6.0
evidence: 自适应推理图用于LLM评估，关联LLM推理能力
tldr: 静态基准测试存在数据污染和适应性问题。本文提出DARG，通过提取推理图并扰动生成新测试数据，动态评估LLM推理能力。方法可控制复杂度，有助于更全面理解LLM推理泛化。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 590, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1359, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 474, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 553, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1356, \"height\": 991, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1295, \"height\": 1515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1019, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1395, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1404, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1295, \"height\": 1515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1442, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1442, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1073, \"height\": 986, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1085, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-5ifecna7zr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1443, \"height\": 894, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1436, \"height\": 999, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1295, \"height\": 1504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1295, \"height\": 1515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1295, \"height\": 1515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 571, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-5ifecna7zr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1268, \"height\": 263, \"label\": \"Table\"}]"
motivation: 静态基准测试有局限性，需动态评估LLM推理。
method: 提取推理图并扰动生成新测试数据。
result: 生成的测试样本具有不同复杂度，有效评估LLM推理。
conclusion: DARG提供动态评估框架，推动LLM推理研究。
---

## Abstract
The current paradigm of evaluating Large Language Models (LLMs) through static benchmarks comes with significant limitations, such as vulnerability to data contamination and a lack of adaptability to the evolving capabilities of LLMs. Therefore, evaluation methods that can adapt and generate evaluation data with controlled complexity are urgently needed. In this work, we introduce Dynamic Evaluation of LLMs via Adaptive Reasoning Graph Evolvement (DARG) to dynamically extend current benchmarks with controlled complexity and diversity. Specifically, we first extract the reasoning graphs of data points in current benchmarks and then perturb the reasoning graphs to generate novel testing data. Such newly generated test samples can have different levels of complexity while maintaining linguistic diversity similar to the original benchmarks. We further use a code-augmented LLM to ensure the label correctness of newly generated data. We apply our DARG framework to diverse reasoning tasks in four domains with 15 state-of-the-art LLMs. Experimental results show that almost all LLMs experience a performance decrease with increased complexity and certain LLMs exhibit significant drops. Additionally, we find that LLMs exhibit more biases when being evaluated via the data generated by DARG with higher complexity levels. These observations provide useful insights into how to dynamically and adaptively evaluate LLMs.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：当前大语言模型（LLM）的评估主要依赖静态基准数据集（如GSM8K、BBQ等），但这些基准存在两大缺陷：
  1. **数据污染**：LLM训练语料可能与测试集重叠，导致模型“记忆”而非真正推理，误导对其能力的判断。
  2. **静态性**：基准的复杂度固定，无法随LLM能力的快速提升而动态调整，难以区分模型真实水平与过拟合表现。
- **研究背景**：已有尝试包括模板生成（DyVal）、LLM直接改写（DyVal 2、Benchmark Self-Evolving），但存在生成样本缺乏语言多样性、标签不稳定或可控性差等问题。因此，亟需一种能动态生成可控复杂度、保持语言多样性且标签可靠的评估方法。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出 **DARG（Dynamic Evaluation via Adaptive Reasoning Graph）** 框架，通过提取原始数据点背后的**推理图**（Reasoning Graph），基于图结构进行细粒度扰动（如增加深度、宽度、数值复杂度），再将扰动后的图解码为自然语言问题，最后用代码增强的LLM验证标签正确性，从而生成新的测试样本。
- **关键技术细节**：
  - **推理图定义**：有向无环图，节点表示基本推理单元（如数字、人物、动作），边表示算子或关系（如加减、属性关联）。复杂度通过图的深度、宽度以及节点属性（如数值位数）量化。
  - **图构建**：利用LLM（如GPT-4 Turbo）通过上下文示例（ICL）从原始数据中提取推理图。为防止LLM错误，采用**规则函数**基于图结构计算标签，并与原始标签比对；不一致则重新提示LLM（高温度）。
  - **图扰动**：基于规则函数，对推理图进行系统修改：增加数值位数（节点值）、在图的最长路径上拆分节点以增加深度、在非最长路径上增加节点以增加宽度。修改后直接计算新标签，不引入LLM噪声。
  - **图到文本解码**：使用LLM将扰动后的推理图转换为自然语言问题，以原始数据（图-文本对）为上下文示例，保持语言风格一致。
  - **标签验证**：使用代码增强的LLM代理（如GPT-4 + Python解释器）生成代码执行问题，若输出与图计算标签一致则接受；否则迭代修正。
- **算法流程**（文字描述）：
  1. 输入原始数据点 (x, y) 和复杂度约束 Ω。
  2. 使用LLM+ICL构建推理图 G₀；通过规则函数计算标签 l̂，若 l̂ ≠ y 则重复提示直到一致。
  3. 根据 Ω 对 G₀ 进行图扰动得到新图 Ĝ；计算新标签 ŷ。
  4. 使用LLM+ICL将 Ĝ 解码为文本 x*；通过代码增强LLM计算答案 A*，若 A* ≠ ŷ 则迭代修正。
  5. 输出新的数据点 (x̂, ŷ)。

### 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集与场景**：
  - **数学推理**：GSM8K（小学数学词问题）
  - **社会推理**：BBQ（偏倚评估，涉及9个受保护群体，含歧义/无歧义上下文）
  - **空间推理**：BBH Navigate（判断是否回到起点）
  - **符号推理**：BBH Dyck Languages（预测闭合括号序列）
- **基准**：原始数据集上的性能作为基线。
- **对比方法**：未直接与DyVal等生成方法对比（因为DARG是评估框架而非模型），主要对比**不同LLM自身**在不同复杂度下的性能变化，以及不同提示策略（Chain-of-Thought CoT、Least-to-Most LtM）。
- **评估LLM**：共15个SOTA模型，涵盖：
  - 开源解码器模型：Phi-3-mini、Mistral-7B、Llama-3-8B/70B、Command R+
  - MoE模型：Mixtral 8×7B/8×22B、WizardLM-2-8×22B
  - 数学专用模型：DeepSeekMath-7B
  - 闭源模型：GPT-4 Turbo、GPT-4o、Gemini-1.5 Pro/Flash、Claude-3 Opus

### 4. 资源与算力（文中提及）

- **API使用**：Azure OpenAI（gpt-4-1106、gpt-35-turbo-1106）、Lepton AI（Mistral/Mixtral系列）、Groq（Llama 3）、Google API（Gemini）、Anthropic API（Claude-3 Opus）。本地使用一台Nvidia A100 40G GPU、12核CPU。
- **微调**：使用LitGPT + LoRA，精度bf16，每模型约16G GPU内存，学习率0.0003，epochs=5。
- **总成本**：约1000美元。
- **耗时**：未明确报告总训练时长，但提供了实验配置细节。

### 5. 实验数量与充分性

- **实验数量**：
  - GSM8K：在每个复杂度维度（数值、深度、宽度）的4个梯度上，各采样500个数据点进行评估，共3×4×15=180组模型-复杂度组合（含原始）。
  - BBQ：600个数据点，4个宽度梯度，涉及7个代表性模型，6个指标（准确率、偏倚分数、回避率）。
  - BBH Navigate：250个数据点，4个深度梯度，所有6个模型。
  - BBH Dyck Languages：250个数据点，4个输入深度梯度和2个标签深度梯度。
  - 消融实验：人评（GSM8K 92.5%正确率）、微调实验（Mistral-7B和Llama2-7B对比原训练数据与DARG生成数据）。
  - 错误分析：每个复杂度级别20个案例共240例，分类统计。
  - 额外实验（附录E）：使用LLaMA 3.1-8B/70B/405B比较图构建和图解码成功率。
- **充分性**：实验覆盖了四个不同推理领域，多种模型类型（规模、架构），使用了两种提示策略，并包含了人为验证和微调验证，整体较充分。但每个领域仅选一个数据集，可能不足以代表该领域全貌。

### 6. 论文的主要结论与发现

1. **性能普遍下降**：所有15个LLM在GSM8K上随复杂度增加（数值、深度、宽度）准确率均显著下降，如Claude-3 Opus在深度+4时下降54.2%。
2. **模型鲁棒性差异**：
   - 大模型（如Llama-3-70B）比小模型更抗干扰；MoE模型（Mixtral 8×22B）比同参数量非MoE模型更鲁棒。
   - 闭源模型（GPT-4 Turbo、Gemini-1.5 Pro）在数学推理中表现较好，但在社会推理中表现出更高的“回避率”（倾向于回答“无法确定”），可能是过度对齐所致。
3. **偏倚加剧**：在BBQ上，复杂度增加导致偏倚分数上升，且闭源模型对受保护群体内容过度敏感。
4. **错误类型分布**：数值复杂度增加导致计算错误增多；深度/宽度增加导致推理错误增多。
5. **空间推理确认偏差**：在BBH Navigate中，许多模型在正例（“回到起点”）上准确率急剧下降，而在负例上相对稳定，暗示存在确认偏差。
6. **符号推理长度敏感**：输入或输出括号数增加时，多数模型准确率下降，但GPT-4 Turbo和Mixtral 8×22B在输入+4、+8时反而上升，随后下降。
7. **DARG数据可提升微调效果**：使用DARG生成的数据微调后，Mistral-7B和Llama2-7B在GSM8K上优于使用等量原始训练数据微调。

### 7. 优点（方法或实验设计亮点）

- **可控复杂度与语言多样性兼得**：通过规则扰动推理图保证复杂度可控，同时用LLM解码保持自然语言风格，克服了模板生成（DyVal）语言生硬的问题。
- **标签正确性保障**：采用代码增强LLM进行验证，而非单纯依赖LLM自我修正，人评显示验证后正确率达92.5%，远高于自修正（37.5%）。
- **通用性强**：推理图定义可扩展至多种推理任务（数学、社会、空间、符号），为动态评估提供统一框架。
- **评估维度全面**：引入CIARR指标（复杂度诱导准确率保持率）量化鲁棒性，并从多个复杂度维度（深度、宽度、数值）分析，错误类型分析提供深入见解。
- **实际应用价值**：DARG不仅能生成测试数据，还能生成训练数据用于提升模型能力。

### 8. 不足与局限

1. **任务覆盖有限**：仅针对推理任务，每个领域只选一个代表性数据集，未验证在自然语言理解、生成等其他任务上的适用性。
2. **依赖闭源LLM**：当前图构建和图解码主要依赖GPT-4 Turbo，附录E显示开源模型（如LLaMA 3.1-70B/405B）在图构建方面接近，但图解码成功率（52~58%）仍低于GPT-4 Turbo（90%），且小模型（8B）几乎无法完成。若无法使用闭源模型，方法推广受限。
3. **复杂度扰动单一**：论文每次只扰动一个维度，未系统研究多维联合扰动的影响。
4. **计算成本**：生成数据需要多次LLM调用（图构建、解码、验证），总成本约1000美元，对低成本场景可能过高。
5. **偏见风险**：方法本身可能放大数据中原有偏见（如BBQ中增加负属性给保护群体），虽用于评估但需谨慎使用生成数据。
6. **标签验证依赖代码可解性**：对于无法用代码解决的推理任务（如开放生成），验证模块难以直接应用。

（完）
