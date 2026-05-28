---
title: "MuSLR: Multimodal Symbolic Logical Reasoning"
title_zh: MuSLR：多模态符号逻辑推理
authors: "Jundong Xu, Hao Fei, Yuhui Zhang, Liangming Pan, Qijun Huang, Qian Liu, Preslav Nakov, Min-Yen Kan, William Yang Wang, Mong-Li Lee, Wynne Hsu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uWEcZkrSkZ"
tags: ["query:ns-xai"]
score: 8.0
evidence: 多模态符号逻辑推理基准
tldr: "该论文提出了MuSLR，首个多模态符号逻辑推理基准，包含1,093个实例，覆盖7个领域。评估了7种视觉语言模型，发现所有模型在多模态符号推理上表现欠佳，GPT-4.1相对最佳。该基准为神经符号系统的评估提供了重要基础。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1399, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1356, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 473, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 741, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1435, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1450, \"height\": 1008, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1224, \"height\": 2025, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-uweczkrskz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uweczkrskz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 678, \"height\": 161, \"label\": \"Table\"}]"
motivation: 多模态符号逻辑推理在自动驾驶等高风险应用中至关重要，但缺乏专门评估基准。
method: 构建基于形式逻辑规则的多模态符号逻辑推理基准MuSLR，包含原子逻辑与组合逻辑。
result: 在7种VLMs上的评估显示，所有模型均难以进行多模态符号推理。
conclusion: 当前VLM在多模态符号逻辑推理上仍有挑战，MuSLR可推动该领域发展。
---

## Abstract
Multimodal symbolic logical reasoning, which aims to deduce new facts from multimodal input via formal logic, is critical in high-stakes applications such as autonomous driving and medical diagnosis, as its rigorous, deterministic reasoning helps prevent serious consequences. To evaluate such capabilities of current state-of-the-art vision language models (VLMs), we introduce the first benchmark MuSLR for multimodal symbolic logical reasoning grounded in formal logical rules. MuSLR comprises 1,093 instances across 7 domains, including 35 atomic symbolic logic and 976 logical combinations, with reasoning depths ranging from 2 to 9. We evaluate 7 state-of-the-art VLMs on MuSLR and find that they all struggle with multimodal symbolic reasoning, with the best model, GPT-4.1, achieving only 46.8%.
Thus, we propose LogiCAM, a modular framework that applies formal logical rules to multimodal inputs, boosting GPT-4.1’s Chain-of-Thought performance by 14.13%, and delivering even larger gains on complex logics such as first-order logic. We also conduct a comprehensive error analysis, showing that around 70% of failures stem from logical misalignment between modalities, offering key insights to guide future improvements.

---

## 论文详细总结（自动生成）

# 多模态符号逻辑推理（MuSLR）论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前大语言模型（LLMs）在纯文本符号逻辑推理上已取得一定进展，但在高风险场景（如自动驾驶、医疗诊断）中，推理需要**同时融合视觉和文本信息**，并遵循形式逻辑规则（如一阶逻辑），以保证结果的严格性、可验证性和确定性。然而，现有工作缺乏对多模态符号逻辑推理能力的标准定义和评估基准。
- **核心问题**：视觉语言模型（VLMs）是否能够从图像和文本的联合输入中，运用形式逻辑规则进行准确的符号推理？当前模型存在哪些关键瓶颈？
- **整体含义**：提出 **MuSLR**（Multimodal Symbolic Logical Reasoning）任务，填补了多模态形式逻辑推理评估的空白，并为推动该领域发展提供了基准和方法基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将多模态输入中的视觉和文本信息通过形式逻辑规则（命题逻辑 PL、一阶逻辑 FOL、非单调逻辑 NM）进行结构化推理，构建了一个包含1,093个实例的基准数据集 MuSLR-Bench，并提出了模块化推理框架 **LogiCAM**。
- **关键技术细节**：
  - **MuSLR-Bench 构建**：
    - 从 COCO、Flickr30k、nocaps、Mimic、RVL_CDIP、ScienceQA、交通报告等来源收集图像。
    - 使用 GPT-4o 提取视觉细节，并搭配从 Wikipedia、医疗报告等检索的文本，形成多模态上下文。
    - 选取 35 种原子符号规则（如 Modus Ponens、Modus Tollens、假言三段论等），组合成推理链（深度 2~9）。
    - 通过词法相似度过滤（Jaccard>0.5 丢弃）和常识合理性过滤（Vera 模型评分<0.5 丢弃）进行自动质检，再经人工标注验证视觉细节和上下文合理性。
  - **LogiCAM 框架**：
    - 基于 GPT-4.1 的模块化分解：
      1. **前提选择器（Premise Selector）**：从图像和文本中提取与当前推理规则最相关的关键前提，减少噪声。
      2. **推理类型识别器（Reasoning Type Identifier）**：判断当前步骤应使用符号推理还是常识启发式推理，优先使用符号逻辑。
      3. **推理器（Reasoner）**：对符号推理应用三段论等规则（如 Modus Ponens），对启发式推理使用常识补充逻辑间隙。
      4. **完成检查（Check for Completion）**：若当前结论足以回答问题则结束，否则将结论追加到上下文并重复迭代。
- **公式/算法流程**（文字说明）：
  - 从初始多模态上下文 `C` 和图像 `I` 中，选择一对 `(ϕ, ψ)`，若可应用形式推理规则（如 `ϕ ∧ (ϕ → χ) ⊢ χ`）则使用符号推理，否则使用常识推理得到新知识 `K`；然后将 `K` 加入上下文，重复直到得到最终答案或达到最大迭代次数。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：MuSLR-Bench，共 1,093 个实例，覆盖 7 个领域（健康、交通、体育、娱乐、社会、科学、金融），包含 35 种原子规则和 976 种组合逻辑，推理深度 2~9。
- **基准（Benchmark）**：MuSLR 本身是首次提出的多模态符号逻辑推理基准，无直接前人基准可供比较。论文将其作为评估框架。
- **对比方法**：
  - **开源 VLM**：Qwen2.5-VL-7B-Instruct、Llava-1.5-7B、InternVL3-8B、Instructblip-Vicuna-13B。
  - **闭源 VLM**：GPT-4o、GPT-4.1、Claude-3.7-Sonnet。
  - 所有模型在 **三样本 Chain-of-Thought（CoT）** 设置下进行评估（temperature=0.0）。
  - 提出 **LogiCAM**（基于 GPT-4.1）作为强基线，并与上述模型对比。
- **评估指标**：
  - **直接答案匹配**（准确率）
  - **推理正确性**：ROUGE-L、BertScore-F1、ROSCOE（逻辑一致性、事实依据、信息量分步评分）

## 4. 资源与算力（若有提及）

论文**未明确说明**训练或评估所使用的 GPU 型号、数量及具体算力。仅提到所有实验均在标准化设置下进行，温度设为 0.0。评估使用了多个闭源模型（通过 API 访问）和开源模型（可能运行在内部集群）。由于篇幅和限制，未提供算力详情。

## 5. 实验数量与充分性

- **主要实验**：报告了 7 种 VLM 在 MuSLR-Bench 上的整体准确率，并按域和逻辑类型细分（表 1）。
- **消融实验**：对 LogiCAM 的三个模块（前提选择器、推理类型识别、推理器）分别移除，测量性能下降（图 8A），验证各模块重要性。
- **深度分析**：绘制不同推理深度（2-3 至 8-9）下的准确率趋势（图 7A），展示模型在长链推理下的退化。
- **误差分析**：随机抽取各模型 100 个错误案例，分类为 6 种错误类型（逻辑规则误用、未补充常识、忽略视觉细节、模态间逻辑对齐失败、启发式捷径、视觉感知错误），并统计分布（图 7B、8B）。
- **推理可追踪性**：使用 ROUGE-L、BertScore、ROSCOE 评估推理步骤质量（图 6）。
- **附加实验**：对比将 Logic-LM（符号求解器）与 VLM 结合的方法（表 2），证明 LogiCAM 更优。
- **充分性评价**：实验覆盖了主流 VLM、多种逻辑类型和多深度，消融和误差分析全面。但未报告多次运行的统计误差棒（受成本限制），且仅在单一基准（MuSLR-Bench）上评估。整体较为充分，但跨基准泛化性未验证。

## 6. 论文的主要结论与发现

- **所有 VLM 均难以进行多模态符号逻辑推理**：最佳模型 GPT-4.1 仅达到 46.8% 准确率。
- **LogiCAM 显著提升性能**：在 GPT-4.1 基础上提升 14.13%，尤其在一阶逻辑（FOL）上提升 48.93%。
- **推理复杂度影响显著**：FOL 最困难（37.04%），NM 相对容易（46.09%）；推理深度增加时性能普遍下降，但 LogiCAM 在深度 8-9 仍保持 54.61%。
- **主要失败原因**：约 70% 的错误来自于**模态间逻辑对齐失败**（无法正确关联视觉与文本前提），这是当前 VLMs 的核心瓶颈。
- **消融实验证实模块必要性**：移除符号推理模块导致最大性能下降（5.14%），启发式推理和前提选择分别导致 3.45% 和 3.27% 下降，说明各模块不可或缺。

## 7. 优点

- **首创性**：首次定义多模态符号逻辑推理任务并构建高质量基准，填补重要空白。
- **系统性**：数据集构建经过自动化（词法相似度、常识合理性）与人工双重质检，确保逻辑正确性和上下文合理性；逻辑类型覆盖广（PL/FOL/NM），深度跨度大（2-9）。
- **模块化框架清晰**：LogiCAM 将复杂推理分解为前提选择、推理类型识别、规则应用、完成检查，可解释性强，且有效提升性能。
- **深入诊断分析**：通过误差类型统计和模态对齐问题分析，为未来研究指明了关键改进方向（如改进跨模态融合、融入逻辑训练目标）。

## 8. 不足与局限

- **基准规模有限**：1,093 个实例虽涵盖多领域，但规模较小，可能不足以充分泛化到更复杂的真实场景。
- **评估成本高**：依赖 GPT-4.1 等闭源模型，可重复性受限；开源模型版本也均为特定尺寸（7B/13B/8B），未测试更大模型（如 70B+）。
- **实验覆盖不够广泛**：仅在单一基准上评估，未在现有视觉逻辑基准（如 LogicVista、VisuLogic）上验证泛化性。未与更多神经符号方法对比。
- **未提供统计误差棒**：因成本未多次运行，无法评估模型性能的稳定性。
- **LogiCAM 依赖强语言模型**：框架中的三个模块均基于 GPT-4.1，若替换为较弱模型性能可能大幅下降；对闭源模型的 API 依赖也限制了实际部署。
- **错误分析依赖手动抽样**：仅抽取每模型 100 个错误案例，抽样可能引入偏差，未采用全覆盖或系统性采样方法。
- **推理步骤评估指标有限**：ROUGE-L、BertScore、ROSCOE 仅提供文本相似度和逻辑一致性评分，缺乏对逻辑链形式正确性的严格验证（如证明定理证明器）。

（完）
