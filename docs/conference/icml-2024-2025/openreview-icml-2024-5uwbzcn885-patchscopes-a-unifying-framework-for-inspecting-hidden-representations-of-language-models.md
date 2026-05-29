---
title: "Patchscopes: A Unifying Framework for Inspecting Hidden Representations of Language Models"
title_zh: Patchscopes：检查语言模型隐藏表示的统一框架
authors: "Asma Ghandeharioun, Avi Caciularu, Adam Pearce, Lucas Dixon, Mor Geva"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=5uwBzcn885"
tags: ["query:ns-xai"]
score: 8.0
evidence: 检查LLM隐藏表示，解释内部推理
tldr: 本文提出Patchscopes框架，利用大语言模型自身的能力，通过将隐藏表示投影到词汇空间并进行干预，以自然语言解释其内部计算和表征，统一了多种先前的可解释性方法，并克服了早期层表示难以解释的局限。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 843, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1378, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1467, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1734, \"height\": 2138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1736, \"height\": 2191, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1602, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1601, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1233, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1238, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5uwbzcn885/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 878, \"height\": 671, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 698, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 829, \"height\": 641, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1767, \"height\": 846, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1506, \"height\": 830, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1687, \"height\": 2065, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1692, \"height\": 2126, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-5uwbzcn885/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 904, \"height\": 458, \"label\": \"Table\"}]"
motivation: 理解大语言模型的内部表示有助于解释其行为并验证与人类价值观的一致性。
method: 利用模型自身将隐藏表示投影到词汇空间并干预计算，以自然语言解释表示。
result: 该框架能够回答关于LLM计算的广泛问题，并统一了多种可解释性方法。
conclusion: Patchscopes为分析LLM内部表征提供了强大且统一的工具。
---

## Abstract
Understanding the internal representations of large language models (LLMs) can help explain models' behavior and verify their alignment with human values. Given the capabilities of LLMs in generating human-understandable text, we propose leveraging the model itself to explain its internal representations in natural language. We introduce a framework called Patchscopes and show how it can be used to answer a wide range of questions about an LLM's computation. We show that many prior interpretability methods based on projecting representations into the vocabulary space and intervening on the LLM computation can be viewed as instances of this framework. Moreover, several of their shortcomings such as failure in inspecting early layers or lack of expressivity can be mitigated by Patchscopes. Beyond unifying prior inspection techniques, Patchscopes also opens up *new* possibilities such as using a more capable model to explain the representations of a smaller model, and multihop reasoning error correction.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

理解大语言模型（LLM）的隐藏表示对于解释模型行为和验证其与人类价值观对齐至关重要。然而，现有可解释性方法（如投影到词汇空间的 Logit Lens、Tuned Lens，以及训练线性探针、因果干预等）存在三大缺陷：

- **早期层失效**：词汇空间投影方法在模型底层精度极差，输出难以解读。
- **表达力不足**：探针仅能输出预定义类别的概率，缺乏高质量的自然语言解释。
- **依赖训练数据**：探针和部分映射函数需要监督训练，难以扩展到开放类别或未知场景。

本文提出 **Patchscopes**——一个统一的模块化框架，利用语言模型自身的文本生成能力“翻译”其隐藏表示中的信息，从而克服上述局限，并开启新的应用（如跨模型解释、多步推理纠错）。

## 2. 方法论：核心思想、关键技术细节

### 2.1 框架定义
Patchscopes 的核心操作是将**源模型**（M）在某层 `l`、某位置 `i` 的隐藏表示 `h_l^i`（来自源提示 S）进行可选变换 `f` 后，**修补（patching）**到**目标模型**（M*）的推理过程中（目标层 `l*`、目标位置 `i*`，目标提示 T），然后从该层继续前向传播，生成文本输出。

形式化地，一个 Patchscope 由五元组 `(T, i*, f, M*, l*)` 定义，源侧由 `(S, i, M, l)` 确定。其中 `f` 可以是恒等、线性/仿射映射（可学）或更复杂的函数。

### 2.2 关键配置与创新
- **Token Identity Patchscope（§4.1）**：使用 `"tok1→tok1; tok2→tok2; ...; tokk"` 的少样本提示作为 T，将源层 `l` 的表示修补到目标同层 `l*=l`，利用模型自身的解码能力估计下一个 token 预测。**无需训练数据**。
- **Zero-Shot Feature Extraction Patchscope（§4.2）**：使用关系自然语言描述作为 T（如 `"The largest city in x"`），将主体的表示修补到占位符 `x` 的位置，生成开放式的属性值。**无需训练数据**。
- **Entity Description Patchscope（§4.3）**：使用 `"subject1: description1, ..., subjectk: descriptionk, x"` 作为 T，沿早期层逐层修补，可视化实体名称的逐步解析过程。
- **Cross-Model Patchscope（§4.4）**：当 M* 是 M 的更大版本时，学习仿射映射 `f` 将表示转移到更强模型中，提高解码质量。
- **CoT Patchscope（§5）**：将多步推理问题分解，将第一步推理结果（中间实体）的表示修补到第二步推理的适当位置，纠正合成错误。

## 3. 实验设计

### 3.1 数据集与场景
| 实验场景 | 数据集 | 模型 | 评估指标 |
|---------|--------|------|---------|
| 下一个 token 预测估计（§4.1） | Pile 评估集（2000 样本） | LLaMA2 13B, Vicuna 13B, Pythia 12B, GPT-J 6B | Precision@1, Surprisal |
| 属性提取（§4.2） | Hernandez et al. (2023b) 常识/事实知识（1453 数据点，5 常识+7 事实任务） | GPT-J 6B | 平均准确率 |
| 实体解析（§4.3） | PopQA（200 流行 + 200 稀有实体） | Vicuna 7B/13B, Pythia 6.9B/12B | RougeL, Rouge1, Sentence-BERT |
| 跨模型修补（§4.4） | 同上 | Vicuna 7B→13B, Pythia 6.9B→12B | Precision@1, Surprisal, RougeL |
| 多跳推理纠错（§5） | 基于 Hernandez 数据合成的 1104 个多跳查询，筛选 46 个有效样本 | Vicuna 13B | 准确率（ω2 出现在生成中） |

### 3.2 对比方法
- **下一个 token 预测**：Logit Lens、Tuned Lens（仿射映射，需训练）。
- **属性提取**：逻辑回归探针（需训练）。
- **实体解析**：无可比基线（首次实现自然语言描述）。
- **多跳推理**：Vanilla 直接生成、Chain-of-Thought（CoT）提示 "Let's think step by step."。

## 4. 资源与算力

文中说明所有实验使用 **A100 80GB GPU**（GPT-J 实验使用 A100 40GB GPU）。**未明确提及 GPU 数量、训练时长或总计算量**。因此无法给出具体算力消耗数值，但可推断实验规模适中（基于多个中等规模模型）。

## 5. 实验数量与充分性

- 共涉及 **4 个主要实验场景**，每个场景包含多层/多模型/多评估指标的细致比较。
- 消融分析充分：
  - 不同 token identity 提示的鲁棒性（附录 B.3，Fig.5）。
  - 源层与目标层组合对性能的影响（热图，Fig.7, Fig.10-12）。
  - 跨模型修补中仿射映射的效能。
- 统计检验：属性提取实验中使用了 **配对 t 检验 + Bonferroni 校正**，显著优于探针的任务明确标出（p < 1e-5）。
- 部分任务数据点较少（6/12 任务 <40 样本），但作者已排除低于 15 样本的任务，探针使用三层交叉验证，尽量保证公平。
- 实验覆盖多种模型家族（LLaMA, Vicuna, GPT-J, Pythia），不同尺寸（6B~13B），结论较具泛化性。

综合评价：实验设计客观、对比公平，消融和统计支持充分，但受限数据量小的任务可能存在方差偏高的风险。

## 6. 主要结论与发现

1. **Token Identity Patchscope** 在所有模型中从第 10 层起稳定优于 Logit Lens 和 Tuned Lens，最高提升达 98%（层 18-22），且无需训练。
2. **Zero-Shot Feature Extraction Patchscope** 在 12 个属性提取任务中，**6 个显著优于线性探针**，5 个持平，仅 1 个稍差；尤其早期层表现突出，证明不依赖原始上下文仍可解码丰富属性。
3. **Entity Resolution Patchscope** 首次以自然语言可视化实体名称的逐步解析过程（如 "Alexander the Great" 经过 "Great Britain" → "the Great Depression" → "Alexander the Great"）；流行实体比稀有实体更早、更准确被解析。
4. **跨模型修补** 可行：用更大模型（Vicuna 13B）解释较小模型（7B）的表示，能提升描述质量（RougeL 提高）；但若较小模型已表现更好（如 Pythia 6.9B 比 12B 好），跨模型修补无优势。
5. **多跳推理纠错**：CoT Patchscope 准确率 50%，远超 vanilla（19.57%）和 CoT 提示（35.71%），证明通过操纵内部表示可直接修复合成推理错误。

## 7. 优点（方法与实验亮点）

- **统一性强**：将 Logit Lens、Tuned Lens、Future Lens、因果追踪、注意力剔除等看似不同的方法纳入同一框架，便于理解与改进。
- **免训练/少依赖**：多数新配置无需额外训练数据或探针，减轻了标注成本和过拟合风险。
- **表达力强**：直接生成自然语言解释，比硬性的概率输出或单个 token 更丰富、更可理解。
- **早期层突破**：实体解析实验证明 Patchscope 能揭示早期层的信息，完美填补现有方法在底层失效的空白。
- **跨模型能力**：开创性地用更强模型解释较弱模型，为模型蒸馏和协作解释提供新思路。
- **实用性**：多跳推理纠错展示了直接修复内部计算错误的潜力，并非简单提示工程。

## 8. 不足与局限

- **架构局限**：实验仅基于自回归 Transformer 模型，框架在其他架构（如编码器-解码器、非 Transformer）上的有效性尚待验证。
- **数据限制**：属性提取和多跳推理任务的数据点较少（尤其多跳仅 46 个），降低统计稳健性；稀有实体实验结果离散度大。
- **占位符污染**：在实体解析和多跳实验中，当修补后层数较深时，占位符 `x` 的残留表示可能干扰生成（附录 D.3 举例），需探索更好的占位符或屏蔽机制。
- **映射函数设计**：跨模型修补中当前仅评估了仿射映射，更复杂函数（如非线性或注意力调整）未探索。
- **多跳纠错的前提知识**：CoT Patchscope 需要知道查询的分解结构才能选择正确的修补位置，实际应用难以自动获得；与 CoT 直接对比时，CoT 使用了更多步骤计算，Patchscope 只需一次推理（若位置已知），对比条件不完全等价。
- **泛化性**：框架依赖于模型自身的解码质量。若目标模型表达能力本身不足（如 Pythia 较小版本较好时），跨模型修补效果不佳。
- **计算开销**：Patchscope 需要在修补后继续前向计算，相比直接投影到输出层多出部分开销，但文未给出量化比较。

（完）
