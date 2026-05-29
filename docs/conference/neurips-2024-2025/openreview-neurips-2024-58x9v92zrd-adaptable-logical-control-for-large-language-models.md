---
title: Adaptable Logical Control for Large Language Models
title_zh: 大语言模型的可适配逻辑控制
authors: "Honghua Zhang, Po-Nien Kung, Masahiro Yoshida, Guy Van den Broeck, Nanyun Peng"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=58X9v92zRd"
tags: ["query:ns-xai"]
score: 9.0
evidence: 神经符号框架实现大模型生成的逻辑约束控制
tldr: 大模型生成难以严格遵循逻辑约束。Ctrl-G提出神经符号框架，将任意商用LLM与隐马尔可夫模型结合，以确定性有限自动机形式表示逻辑约束并引导生成。在文本编辑任务中，即使使用较小模型也超越GPT-4。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 534, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1291, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1336, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-58x9v92zrd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1372, \"height\": 495, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-58x9v92zrd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1277, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-58x9v92zrd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-58x9v92zrd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1392, \"height\": 672, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-58x9v92zrd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1010, \"height\": 673, \"label\": \"Table\"}]"
motivation: 大模型生成时难以可靠遵循逻辑约束。
method: 构建神经符号框架，将LLM与HMM结合，用确定性有限自动机表示约束并引导生成。
result: "在逻辑约束文本生成任务中，TULU2-7B+HMM超越GPT-4，准确率提升超30%。"
conclusion: 神经符号控制框架为LLM生成提供可解释且高效的约束遵循能力。
---

## Abstract
Despite the success of Large Language Models (LLMs) on various tasks following human instructions, controlling model generation to follow strict constraints at inference time poses a persistent challenge. In this paper, we introduce Ctrl-G, a neuro-symbolic framework that enables tractable and adaptable control of LLM generation to follow logical constraints reliably. Ctrl-G combines any production-ready LLM with a Hidden Markov Model (HMM), guiding LLM outputs to adhere to logical constraints represented as deterministic finite automata. We show that Ctrl-G, when a TULU2-7B model is coupled with a 2B-parameter HMM, outperforms GPT4 in text editing: on the task of generating text insertions/continuations following logical constraints, our approach achieves over 30% higher satisfaction rate in human evaluation. When applied to medium-size language models (e.g., GPT2-large), Ctrl-G also beats its counterparts on standard benchmarks by large margins. Additionally, as a proof-of-concept study, we use Ctrl-G to assist LLM reasoning on the GSM benchmark, foreshadowing the application of Ctrl-G, as well as other constrained generation approaches, beyond traditional language generation tasks.

---

## 论文详细总结（自动生成）

# 基于论文《Adaptable Logical Control for Large Language Models》的详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在遵循人类指令方面虽然表现出色，但在推理时严格遵循逻辑约束（如包含特定关键词、控制字数、避免不当内容等）仍然非常困难。现有方法要么无法保证约束满足（如辅助分类器方法），要么计算成本过高（如搜索式解码），要么仅能处理单一类型的约束（如GeLaTo仅处理关键词包含）。
- **研究背景**：许多实际应用（如文本编辑、内容审核、受控生成）要求模型在生成时可靠地遵守逻辑规则。传统方法包括：
  - 搜索式解码（如NeuroLogic A*esque）：搜索空间指数增长，缩放性差。
  - 训练辅助分类器（如FUDGE、NADO）：需要为每个新约束重新训练，且不保证满足。
  - 近似推理（如顺序蒙特卡洛）：方差高，收敛无保证。
  - GeLaTo框架：仅支持关键词包含约束，且仅对小规模模型（~0.1B）有效。
- **整体含义**：本文提出Ctrl-G，一个神经符号框架，通过将LLM与隐马尔可夫模型（HMM）结合，并以确定性有限自动机（DFA）表示逻辑约束，实现可靠的、可适配的推理时约束控制，适用于任意生产级LLM。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

### 核心思想
- **神经符号融合**：使用白盒概率模型（HMM）近似黑盒LLM，通过高效地计算HMM在DFA约束下的条件概率，来指导LLM的逐token生成。
- **三步流程**：
  1. **蒸馏**：从目标LLM中采样大量序列，训练一个HMM作为其白盒近似（最小化KL散度）。
  2. **约束规范**：将用户指定的逻辑约束编译为一个确定性有限自动机（DFA）。
  3. **推理**：在每次生成token时，计算HMM条件下后缀满足约束的概率，并用该概率重新加权LLM的原始分布，然后采样下一个token。

### 关键技术细节
- **DFA表示**：任意逻辑约束（如关键词包含、字数范围、逻辑与/或/非）均可表示为DFA。例如，包含短语“gets cold”的约束可用三状态DFA表示。DFA可以通过KMP算法、逻辑组合（交集、并集、补集）等方式高效构建。
- **高效边际概率计算**：利用HMM的马尔可夫性质和DFA的状态转移，推导出递推公式（公式4），可在O(n·m·h²)时间内计算给定部分序列时最终满足约束的概率，其中n为最大序列长度，m为DFA边数，h为HMM隐藏状态数。
- **算法流程**（Algorithm 1）：
  - 预处理：从后向前递推计算每个时间步t、每个HMM隐藏状态z_t、每个DFA状态s_t下的满足概率。
  - 生成：初始化DFA状态，逐token进行：计算HMM的边际概率，乘以LLM的下一个token概率，采样，更新DFA状态。

### 关键公式
- 生成分布：`p_ctrl-g(xt | x<t, α) ∝ plm(xt | x<t) · phmm(α | xt, x<t)`
- 其中`phmm(α | xt, x<t)`通过HMM和DFA的联合动态规划计算。

## 3. 实验设计：数据集、场景、基准与对比方法

### 数据集与场景
- **CommonGen（常识生成）**：给定3-5个概念（关键词），生成包含所有概念的合理句子。测试集包含dev和test，并扩展至6-9个关键词（CommonGen+）。
- **文本填充（Text Infilling）**：基于ROC Stories语料库，构造四种掩码比例（13%、21%、32%、40%）的测试集，要求模型填充缺失片段，并保持故事连贯性。
- **交互式文本编辑**：从CoAuthor数据集中提取800个故事，构建续写（continuation）和插入（insertion）两类任务，并叠加以下约束组合：
  - 无约束（None）
  - 仅关键词（Keyphrase）
  - 仅字数（Word Count）
  - 关键词+字数（K&W）
  共8个设置，每个设置100个测试例子。

### 对比方法
- **CommonGen**：FUDGE、NADO、NeuroLogic A*esque、GeLaTo。其中GeLaTo与Ctrl-G使用相同的基座模型GPT2-large。
- **文本填充**：ILM（监督训练的GPT2-small），Ctrl-G使用相同基座模型（无监督）。
- **文本编辑**：TULU2-7B（仅指令提示）、GPT3.5、GPT4、以及基于TULU2-7B的指令微调版本（使用1000训练样本）。Ctrl-G使用TULU2-7B作为基座模型，结合2B参数的HMM。

### 评价指标
- 自动指标：BLEU-4、ROUGE-L、CIDEr、SPICE（CommonGen）；BLEU-4、ROUGE-L（文本填充）；约束满足率（Constraint success rate）。
- 人工评价（文本编辑）：三位标注员对流畅性（Q1）、一致性（Q2）、整体质量（Q3）按1-5分评分，同时计算总体满意度（质量>3且约束满足的比例）。标注员之间Kendall系数为0.449，中等一致性。

## 4. 资源与算力

- **硬件**：所有实验在NVIDIA A100 GPU（80GB内存）上运行。
- **HMM蒸馏**：
  - 对于GPT2-large（~0.8B）：采样4M例子，训练40次EM步，每步100K例子。
  - 对于TULU2-7B：采样5M例子，训练一个隐藏状态数为32768的HMM（约2B参数）。
- **运行时开销**：生成每token的时间，对于HMM规模32768、DFA大小~900时，额外时间约0.01-0.02秒，随序列长度基本恒定（图5）。整体时间复杂度为O(n·m·h²)。
- **论文未明确说明总训练时长**，但给出了算法复杂度分析和实验中的时间测量。

## 5. 实验数量与充分性

- **实验数量**：涵盖三个主要基准（CommonGen及其扩展、文本填充、文本编辑）、多个子设置（监督/无监督、不同掩码比、不同约束组合）、消融（不同HMM规模：4096 vs 32768）、泛化性测试（6-9个关键词）、对抗性测试（GSM推理辅助）。总体实验数量较多。
- **充分性判断**：
  - **CommonGen**：与主流方法公平对比，报告了dev和test结果，且基线使用相同基座模型（GeLaTo）或公开结果。充分。
  - **文本填充**：仅与ILM对比（监督方法），缺乏与其他非监督方法的对比，略显不足；但证明了在无监督下的竞争力。
  - **文本编辑**：与GPT-3.5/4、TULU2对比，人工评价设计合理，但仅进行了8组设置，每设置100例，样本量中等。
  - **GSM**：仅作为概念验证，实验不充分，未详细消融和分析。
  - **消融实验**：缺少对HMM质量（如不同隐藏状态数）对性能影响的系统分析；缺少与纯逻辑过滤（如Guidance）的对比（论文在3.3节定性讨论了区别，但未定量实验）。
- **客观性与公平性**：基线生成时均采用128次采样取最高概率，控制相同随机种子。人工评价使用盲审（标注员不知道约束要求）。总体公平。

## 6. 论文的主要结论与发现

- **Ctrl-G实现了100%的约束满足率**，在所有设置的自动和人工评价中均未出现违反约束的情况。
- **生成质量高**：在CommonGen上，Ctrl-G在BLEU-4、ROUGE-L、CIDEr、SPICE上均超越所有基线；在文本填充上，无监督的Ctrl-G接近甚至超越监督训练的ILM（尤其是高掩码比例时）。
- **在文本编辑中超越GPT-4**：当存在约束时，Ctrl-G（TULU2-7B+HMM）的总体满意度比GPT-4高30%以上；即使在无约束的插入任务中，质量也与GPT-4持平。
- **泛化能力强**：约束复杂度增加时，GPT-4质量下降，而Ctrl-G保持稳定；可轻松处理6-9个关键词约束。
- **运行时效率高**：比搜索解码快两个数量级，且额外开销随序列长度恒定。
- **可适配任意逻辑约束**：由于DFA的通用性，Ctrl-G可处理关键词、字数、顺序、逻辑组合等多种约束，无需重新训练HMM。

## 7. 优点

- **硬约束保证**：通过HMM+DFA的精确推理，确保生成文本严格满足逻辑约束，这是大多数现有方法无法实现的。
- **一次蒸馏，多次使用**：HMM蒸馏后，可应用于任意DFA约束，无需为每个新约束重新训练。
- **与LLM解耦**：可插拔式设计，兼容任何自回归LLM（如GPT2、Llama、TULU2），不修改原始模型参数。
- **高效算法**：利用HMM和DFA的马尔可夫性质，时间复杂度O(n m h²)，可通过GPU并行加速；实际运行时间远快于搜索式方法。
- **文本插入任务中的独特优势**：通过将后缀作为DFA约束的一部分，HMM自动引导生成与后续上下文一致的文本，解决了纯自回归模型难以处理插入的难题。
- **开源与复现**：代码和模型检查点已公开。

## 8. 不足与局限

- **HMM蒸馏成本高**：对于大规模LLM（如7B），需要采样数百万例子训练一个2B参数的HMM，计算资源消耗大。
- **约束表达力受限**：DFA只能表达正则语言（即等价于正则表达式），对于更复杂的上下文相关约束（如语法、语义角色、数字计算）难以直接编码。
- **近似误差**：HMM是LLM的近似，当HMM与LLM分布不一致时，引导可能产生次优输出。论文未系统研究近似误差对下游任务的影响。
- **人工评价样本量有限**：文本编辑实验中每设置仅100例，且标注员之间一致性为中等（0.449），可能存在评价偏差。
- **GSM实验不充分**：仅针对293个例子进行了单一约束（必须包含所有数字），提升仅3.4%，缺乏消融或对比其他控制方法，说服力较弱。
- **缺乏与最新可约束生成框架的对比**：如Guidance（基于正则的过滤）只做了定性讨论，未进行定量实验；也未与SGLang等结构化生成工具对比。
- **未讨论安全与公平性**：虽然可控制生成内容，但未分析可能被滥用生成恶意文本的风险，也未讨论对不同群体输出的偏差。
- **时间复杂度依赖DFA规模**：当DFA边数m很大（例如约束复杂的顺序组合）时，计算开销仍可能成为瓶颈。

（完）
