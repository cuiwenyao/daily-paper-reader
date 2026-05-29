---
title: Premise-Augmented Reasoning Chains Improve Error Identification in Math reasoning with LLMs
title_zh: 前提增强推理链改进LLM数学推理中的错误识别
authors: "Sagnik Mukherjee, Abhinav Chinta, Takyoung Kim, Tarun Anoop Sharma, Dilek Hakkani Tur"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4tYckHNVXV"
tags: ["query:ns-xai"]
score: 4.0
evidence: 通过增强前提改进数学推理链中的错误识别
tldr: LLM的链式推理链过长，难以验证步骤正确性。本文提出前提增强推理链，将每个步骤关联到前序步骤的子集作为前提，重构线性推理链，使得错误定位更精准，为数学推理的可解释性评估提供了新工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4tyckhnvxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1629, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4tyckhnvxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1657, \"height\": 922, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1556, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1212, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1744, \"height\": 928, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 820, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 722, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 778, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 777, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 962, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1221, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1218, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1221, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1221, \"height\": 372, \"label\": \"Table\"}]"
motivation: LLM的推理链过长导致错误步骤难以追溯。
method: 将推理链重构为每个步骤标注前提的结构。
result: 在数学推理任务上错误识别准确率显著提升。
conclusion: 前提增强方法提高了推理链的可验证性。
---

## Abstract
Chain-of-Thought (CoT) prompting enhances mathematical reasoning in large language models (LLMs) by enabling detailed step-by-step solutions. However, due to the verbosity of LLMs, the resulting reasoning chains can be long, making it harder to verify the reasoning steps and trace issues resulting from dependencies between the steps that may be farther away in the sequence of steps. Importantly, mathematical reasoning allows each step to be derived from a small set of premises, which are a subset of the preceding steps in the reasoning chain. In this paper, we present a framework that identifies the premises for each step, to improve the evaluation of reasoning. We restructure conventional linear reasoning chains into Premise Augmented Reasoning Chains (PARC) by introducing premise links, resulting in a directed acyclic graph where the nodes are the steps and the edges are the premise links. Through experiments with a PARC-based dataset that we built, namely (Premises and ERrors identification in LLMs), we demonstrate that LLMs can reliably identify premises within complex reasoning chains. In particular, even open-source LLMs achieve 90% recall in premise identification.  We also show that PARC helps to identify errors in reasoning chains more reliably. The accuracy of error identification improves by 6% to 16% absolute when step-by-step verification is carried out in PARC under the premises.
Our findings highlight the utility of premise-centric representations in addressing complex problem-solving tasks and open new avenues for improving the reliability of LLM-based reasoning evaluations.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）通过链式推理（Chain-of-Thought，CoT）在数学推理任务中取得了显著进展，但生成的推理链往往冗长且步骤间依赖关系隐含，导致验证错误步骤和追溯错误来源变得困难。现有评估方法主要关注最终答案的正确性，忽略了对中间推理过程的细粒度检查，且参考无关上下文（distractors）会干扰LLM的验证能力。
- **核心问题**：如何更可靠地识别数学推理链中的错误（包括局部错误和传播错误）？
- **整体含义**：论文提出将线性推理链重构为**前提增强推理链（PARC）**，通过显式标注每个步骤所依赖的前提（即前序步骤的子集），使错误验证更加精准，为提升LLM推理的可解释性和可信度提供了新工具。

## 2. 方法论

### 核心思想
- 将线性推理链（LRC）中的每个步骤与它直接依赖的前序步骤（前提）建立显式链接，形成有向无环图（DAG）结构的PARC。
- 在验证时只基于当前步骤的前提进行判断，排除无关上下文，从而减少干扰，提高错误识别准确率。

### 关键技术细节
1. **前提定义**：对于步骤 \( s_i \)，其前提集 \( P_i \) 是前序步骤的一个最小且充分的子集，满足：
   - **可验证性**：仅凭 \( P_i \) 即可验证 \( s_i \) 的正确性。
   - **最小性**：移除 \( P_i \) 中任何一步都会导致 \( s_i \) 无法验证。
2. **前提提取方法**：
   - **聚合式映射（Aggregative）**：一次性查询LLM，输入当前步骤及之前所有步骤，直接输出前提集。
   - **成对映射（Dyadic）**：逐一判断每个前序步骤是否为当前步骤的前提，复杂度 \( O(n^2) \)。实验表明聚合式更优（更高F1且更高效）。
3. **错误识别流程（Algorithm 1）**：
   - **数学错误检测**：仅检查当前步骤本身是否有计算/代数错误。
   - **逻辑不一致检测**：检查当前步骤是否与前提逻辑一致（前提视为正确）。
   - **累积错误检测**：若步骤本身正确但至少一个前提有误，则标记为累积错误（Accumulation Error），通过DFS遍历依赖图实现。
4. **错误分类扩展**：在原有Native Error（数学错误、逻辑不一致）基础上引入**累积错误**，区分局部正确但继承上游错误的步骤。

## 3. 实验设计

### 数据集
- **PERL（论文构建）**：源自GSM8K、MATH、Orca-Math、MetaMathQA，共607条推理链（203正确、214错误、190合成错误），含2,134步正确、321步数学错误、443步逻辑不一致、741步累积错误。
- **ProcessBench**：人类标注的数学推理步骤错误基准（仅标注到第一个错误步骤）。

### 基准方法
- **基线（Baseline）**：直接使用完整推理链作为上下文，零样本分类步骤错误类型（Correct / Mathematical Error / Logical Inconsistency / Accumulation Error）。
- **本文方法（PARC）**：先提取前提（oracle或模型生成），再基于前提进行逐步验证。

### 对比模型
- **Llama-3.1**: 8B, 70B
- **Qwen-2.5**: 7B, 32B, 72B
- **GPT-4o-mini**, **GPT-4o**
- 所有模型使用Instruct变体，temperature=0。

### 评估指标
- 前提识别：精确率、召回率、F1（特别强调召回率）。
- 错误识别：按步骤的准确率（按链长归一化后平均）。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量及训练时长。
- 仅提及使用**vLLM**进行模型推理，调用**Azure OpenAI**服务（GPT-4o/o1）。实验为推理/评估任务，而非训练，因此算力需求相对可控，但未提供具体量化信息。

## 5. 实验数量与充分性

- **实验覆盖广泛**：
  - 前提识别实验：4个数据集 × 6个模型 × 3种数据拆分（正例、负例、合成负例）。
  - 错误识别实验：同样大规模（含oracle前提、模型前提、Full Context三种设置）。
  - 附加ProcessBench验证（GSM8K和MATH子集）。
- **消融分析充分**：
  - 比较聚合式 vs 成对式前提映射。
  - 对比oracle前提与模型生成前提。
  - 区分真实负例与合成负例，发现合成负例更易识别。
  - 分析各错误类型的准确率（正确、数学错误、逻辑不一致、累积错误）。
- **公平性**：所有实验使用相同提示模板、零样本设置、固定温度；模型均为公开可用指令微调版本；结果按数据集和拆分报告，避免了 cherry-picking。实验设计客观，结论一致。

## 6. 主要结论与发现

1. **LLM能高可靠地识别前提**：开源模型（如Llama 3.1 70B）在前提提取上的召回率超过90%；聚合式映射优于成对式。
2. **前提增强显著提升错误识别准确率**：相比全上下文基线，PARC的准确率绝对提升6%~16%（见表3）。
3. **累积错误最难检测**：但在前提增强下累积错误识别率大幅提高（例如全上下文下只有12%-13%，PARC下达到44%-57%）。
4. **合成负例并不能完全代表真实错误**：模型在合成负例上表现更好，说明依赖人工扰动生成错误的方法可能高估LLM的纠错能力。
5. **Oracle前提与模型生成前提性能接近**：因模型前提提取召回率高，完整端到端流程（模型提取前提+基于前提验证）仍保持较高准确率。

## 7. 优点

- **方法新颖**：将“前提”这一核心概念引入推理链评估，从结构上简化了验证问题，思路清晰且有效。
- **错误分类完善**：新增“累积错误”类别，弥补了传统方法忽略错误传播的不足。
- **数据集贡献**：构建并公开PERL数据集（含前提和错误细粒度标注），为后续研究提供标准测试床。
- **实验严谨**：在多个数据集、多种模型规模、真实/合成负例上反复验证，结论稳健。
- **效率考虑**：聚合式前提提取仅需 \( O(n) \) 次调用，兼顾性能和效率。

## 8. 不足与局限

- **领域局限**：仅针对数学推理，尚未验证在常识推理、符号推理等其他领域的泛化能力。
- **依赖LLM能力**：前提提取和错误验证完全依赖LLM本身，对于小模型（如Llama 3.1 8B）性能有限；模型可能产生偏见（倾向于将步骤标记为正确）。
- **累积错误检测仍受限于前提图质量**：若前提提取有遗漏（尽管召回率高），累积错误可能被误判为正确。
- **计算资源未量化**：论文未提供具体GPU使用量及时间，不利于评估实际部署成本。
- **仅支持英文数学题**：未涉及多语言或跨领域推理。
- **人工验证比例较低**：作者仅检查了10%的PERL注释，可能存在少量标注噪声（虽然报告了低不一致率）。

（完）
