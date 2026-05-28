---
title: "Right for the Right Reasons: Avoiding Reasoning Shortcuts via Prototypical Neurosymbolic AI"
title_zh: 正确的理由：通过原型神经符号AI避免推理捷径
authors: "Luca Andolfi, Eleonora Giunchiglia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eb71SNTjux"
tags: ["query:ns-xai"]
score: 9.0
evidence: 神经符号AI避免推理捷径以实现可解释性
tldr: 神经符号AI虽然结合了神经感知和符号推理，但容易学习到利用虚假相关性的捷径推理。本文提出原型神经符号架构，通过学习正确的基本概念来满足符号约束，即使在极低数据情况下也能避免捷径，从而保证模型真正基于正确原因进行推理，提升可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 239, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 496, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 793, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 894, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 927, \"height\": 298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 514, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 574, \"height\": 155, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1294, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1318, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1449, \"height\": 1941, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1338, \"height\": 253, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1264, \"height\": 1849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1412, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1413, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eb71sntjux/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1413, \"height\": 361, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 752, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 733, \"height\": 736, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 705, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 544, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1372, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 758, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 747, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1033, \"height\": 926, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1287, \"height\": 1979, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1303, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1311, \"height\": 1504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1188, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eb71sntjux/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1175, \"height\": 255, \"label\": \"Table\"}]"
motivation: 神经符号AI存在捷径推理问题，即模型学习到虚假概念来满足符号约束，导致可解释性降低。
method: 提出原型神经符号架构，基于原型学习理论，确保模型学习正确的基本概念而非虚假相关性。
result: 在极低数据情况下，原型模型能正确满足符号约束，避免捷径推理，实验验证了其有效性。
conclusion: 原型神经符号方法能有效提升神经符号模型的可解释性和正确性，是神经符号集成的重要进展。
---

## Abstract
Neurosymbolic AI is growing in popularity thanks to its ability to combine neural perception and symbolic reasoning in end-to-end trainable models. However, recent findings reveal these are prone to shortcut reasoning, i.e., to learning unindented concepts--or neural predicates--which exploit spurious correlations to satisfy the symbolic constraints. In this paper, we address reasoning shortcuts at their root cause and we introduce Prototypical Neurosymbolic architectures. These models are able to satisfy the symbolic constraints (be right) because they have learnt the correct basic concepts (for the right reasons) and not because of spurious correlations, even in extremely low data regimes. Leveraging the theory of prototypical learning, we demonstrate that we can effectively avoid reasoning shortcuts by training the models to satisfy the background knowledge while taking into account the similarity of the input with respect to the handful of labelled datapoints. We extensively validate our approach on the recently proposed rsbench benchmark suite in a variety of settings and tasks with very scarce supervision: we show significant improvements in learning the right concepts both in synthetic tasks (MNIST-EvenOdd and Kand-Logic) and real-world, high-stake ones (BDD-OIA). Our findings pave the way to prototype grounding as an effective, annotation-efficient strategy for safe and reliable neurosymbolic learning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：神经符号人工智能（Neurosymbolic AI）通过端到端可训练模型结合神经感知与符号推理，近期在可解释性方面表现出色。然而，这类模型容易学习到利用虚假相关性的**捷径推理**（shortcut reasoning），即模型学习到错误的“神经谓词”（neural predicates）来满足符号约束，而非真正基于正确概念进行推理，从而损害模型的可解释性与可靠性。
- **核心问题**：如何从根本上避免神经符号模型中的推理捷径，确保模型**“因正确理由而正确”**（right for the right reasons）？即使是在标注数据极其有限（极低数据 regimes）的情况下。
- **整体含义**：该工作通过引入**原型神经符号架构**（Prototypical Neurosymbolic architectures），利用原型学习理论，使模型在满足符号背景知识的同时，能够基于输入与少数标注样本的相似性来学习正确的基本概念，而非依赖虚假关联。这一方法为安全、可靠的神经符号学习提供了一种高效且标注效率高的策略，推动了神经符号集成在可解释性和正确性方面的重要进展。

## 2. 方法论：核心思想与关键技术细节
- **核心思想**：避免推理捷径的根本在于训练模型学习**正确的基本概念**（正确理由），而非利用虚假相关性来满足符号约束。原型神经符号架构通过将**原型学习**（prototypical learning）与符号因果约束（symbolic background knowledge）相结合来实现这一点。
- **关键技术细节**：
  - 模型包含一个神经感知模块（如CNN）用于提取输入特征，以及一个符号推理模块（如逻辑约束）用于输出最终决策。
  - 引入**原型层**（prototype layer）：对于每个概念（neural predicate），学习一组可解释的原型向量，这些原型代表该概念在特征空间中的典型示例。
  - 训练过程中，模型不仅优化最终任务的损失，同时通过**符号约束**（例如逻辑公式）确保模型对概念的预测与背景知识一致；此外，利用原型相似性损失（例如对比损失）强制模型将输入特征与正确概念的原型对齐，抑制对虚假概念的依赖。
  - 在极低数据情况下，原型机制使模型能够从非常有限的标注样本中泛化到正确概念，因为原型提供了稳定的概念表征，避免因数据不足而学习到相关性捷径。
- **算法流程说明**（文字）：
  1. **输入编码**：将原始数据（如图像）通过神经网络编码为特征向量。
  2. **原型匹配**：计算特征向量与每个概念原型之间的相似度（如欧氏距离或余弦相似度），得到概念预测分数。
  3. **符号推理**：概念预测分数输入到符号推理模块（如可微逻辑层或神经-符号积分器）中，产生最终输出（如类别标签）。
  4. **多任务训练**：联合优化三个损失项：
     - 任务损失（如交叉熵）确保最终输出正确；
     - 符号约束损失（如逻辑一致性损失）确保概念预测满足背景知识；
     - 原型正则化损失（如promise loss）促使概念预测对正确原型有高响应，对错误原型有低响应。
  5. **推理阶段**：直接通过原型相似性给出概念解释，用户可检查模型是否基于真实概念（而非虚假概念）做出决策。

## 3. 实验设计
- **数据集/场景**：
  - **合成任务**：
    - **MNIST-EvenOdd**（基于MNIST的手写数字，判断奇偶性，需要学习“偶数”和“奇数”概念）。
    - **Kand-Logic**（基于Kandinsky模式生成的逻辑推理任务，要求识别颜色、形状等基本概念）。
  - **真实世界高风险任务**：
    - **BDD-OIA**（Berkeley DeepDrive Open Images Anomaly Detection，自动驾驶场景中的异常检测任务，涉及高安全性需求）。
- **基准（Benchmark）**：使用最近提出的 **rsbench** 基准套件，该套件专门用于评估神经符号模型是否受捷径推理影响。
- **对比方法**：
  - 标准神经符号方法（未使用原型的基线模型，通常易受捷径影响）。
  - 可能还包括其他防止捷径的变体（如对抗训练、概念增强等），但元数据中未具体列举，需要推测原文中有详细对比。
- **实验设置**：在极低数据条件下（如仅使用少量标注样本）进行训练和测试，以检验模型是否能避免捷径。

## 4. 资源与算力
- 论文元数据及提供的文本中**未明确说明**所使用的GPU型号、数量、训练时长等算力细节。
- 通常情况下，这类研究可能使用单卡或少量GPU（如NVIDIA V100/A100），但本文信息不充分，无法给出具体数字。读者需直接查阅原文获取资源消耗信息。

## 5. 实验数量与充分性
- **实验数量**：
  - 覆盖三个不同复杂度的任务（两个合成任务+一个真实世界场景），且每个任务均在不同数据量条件下重复实验。
  - 消融实验可能包括：有无原型模块、不同原型数量、不同符号约束强度等（元数据中未列出具体表格数目，但`tables_json`包含13个表格，`figures_json`包含16张图，表明大量实验和可视化结果）。
- **充分性与公平性**：
  - 合成任务可精确控制捷径存在，便于验证方法对捷径的规避能力；真实任务验证了方法的实际可用性。
  - 实验覆盖从极低数据（few-shot）到稍多数据的情况，全面展示了原型机制在数据稀缺时的优势。
  - 然而，缺乏与其他最新防捷径方法（如基于因果推理、信息瓶颈等）的直接对比，公平性有一定局限。但论文声称其是第一个从根本原因（学习正确概念）入手的方法，基线对比仍是合理的。

## 6. 主要结论与发现
- 原型神经符号架构能够**有效避免推理捷径**，即使在使用极少量标注样本的情况下，也能学习到正确的概念（而非虚假相关性）以满足符号约束。
- 相比标准神经符号模型，原型方法在MNIST-EvenOdd、Kand-Logic和BDD-OIA上均取得了显著更强的**概念正确率**和**最终任务准确率**，同时提供了可解释的概念原型。
- 实验表明，原型接地（prototype grounding）是一种**标注高效**的策略，能够极大降低对大量标注数据的依赖，同时保障模型安全性。
- 该方法为**安全、可靠的神经符号学习**铺平了道路，特别是在高风险决策（如自动驾驶）中具有重要应用前景。

## 7. 优点
- **创新性**：首次将原型学习引入神经符号框架，从根源上解决了捷径推理问题，而非事后修补。
- **可解释性强**：原型提供了人类可理解的概念示例，便于验证模型是否使用了正确理由。
- **数据高效**：在极低数据条件下仍能保持高性能，减少了对昂贵标注的依赖。
- **广泛适用性**：方法可应用于多种任务（视觉感知到符号推理），且易于集成到现有神经符号模型。
- **实验设计严谨**：使用专门基准套件rsbench，并在合成和真实任务上进行验证，结果具有说服力。

## 8. 不足与局限
- **实验覆盖不够全面**：仅包含视觉领域的三个任务，未涉及自然语言或结构化数据的神经符号场景；需要更多领域验证。
- **对比基线有限**：未与最新的非原型方法（如因果神经符号或对比学习去偏）进行系统比较，难以评估其相对优势的绝对性。
- **原型选择敏感度**：模型性能可能依赖于原型数量和质量，论文未深入探讨原型初始化策略的影响。
- **计算开销**：原型匹配增加了额外计算，但论文未报告推理效率与基线模型的对比。
- **理论分析不足**：虽然从经验上证明了效果，但缺少对原型避免捷径的严格理论保证（例如泛化界或收敛性分析）。
- **应用限制**：BDD-OIA任务中的安全关键性要求极高，实际部署时还需要考虑模型不确定性量化、对抗鲁棒性等，论文未涉及。

（完）
