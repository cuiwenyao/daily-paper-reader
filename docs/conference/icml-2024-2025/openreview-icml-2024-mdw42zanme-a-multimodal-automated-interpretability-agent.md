---
title: A Multimodal Automated Interpretability Agent
title_zh: 多模态自动化可解释性代理
authors: "Tamar Rott Shaham, Sarah Schwettmann, Franklin Wang, Achyuta Rajaram, Evan Hernandez, Jacob Andreas, Antonio Torralba"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=mDw42ZanmE"
tags: ["query:ns-xai"]
score: 4.0
evidence: 自动化视觉模型的可解释性任务
tldr: 本文介绍MAIA，一个多模态自动可解释性代理系统，它利用预训练视觉语言模型和一系列工具（如输入合成、最大激活样本计算）自动对神经网络子组件进行实验，以解释其行为，减轻了人工分析负担。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 993, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 766, \"height\": 154, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 802, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 744, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 733, \"height\": 157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1579, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 866, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 757, \"height\": 158, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 852, \"height\": 945, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 852, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 826, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 848, \"height\": 206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 855, \"height\": 1081, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1021, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 891, \"height\": 2233, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mdw42zanme/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 670, \"height\": 981, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 126, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1407, \"height\": 832, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1430, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 799, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1185, \"height\": 1723, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mdw42zanme/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 941, \"height\": 214, \"label\": \"Table\"}]"
motivation: 神经网络模型的可解释性任务通常需要大量人工实验。
method: 将预训练视觉语言模型配备工具集，自动迭代实验以解释子组件行为。
result: MAIA能够自动执行特征解释和故障模式发现等任务。
conclusion: 为自动化模型理解和可解释性提供了新范式。
---

## Abstract
This paper describes MAIA, a Multimodal Automated Interpretability Agent. MAIA is a system that uses neural models to automate neural model understanding tasks like feature interpretation and failure mode discovery. It equips a pre-trained vision-language model with a set of tools that support iterative experimentation on subcomponents of other models to explain their behavior. These include tools commonly used by human interpretability researchers: for synthesizing and editing inputs, computing maximally activating exemplars from real-world datasets, and summarizing and describing experimental results. Interpretability experiments proposed by MAIA compose these tools to describe and explain system behavior. We evaluate applications of MAIA to computer vision models. We first characterize MAIA’s ability to describe (neuron-level) features in learned representations of images. Across several trained models and a novel dataset of synthetic vision neurons with paired ground-truth descriptions, MAIA produces descriptions comparable to those generated by expert human experimenters. We then show that MAIA can aid in two additional interpretability tasks: reducing sensitivity to spurious features, and automatically identifying inputs likely to be mis-classified.

---

## 论文详细总结（自动生成）

# 多模态自动化可解释性代理（MAIA）论文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：深度神经网络（尤其是视觉模型）的可解释性通常依赖人工实验，耗费大量时间与资源。现有自动化可解释性方法（如MILAN）仅能生成单次假设，缺乏迭代验证能力，且精度较低。
- **核心问题**：如何构建一个具备灵活实验能力、可自动执行多轮假设检验、并达到与人类专家可比解释质量的自动化可解释性系统？
- **整体含义**：MAIA展示了将大语言模型作为“代理”来驱动工具链、模拟人类可解释性研究者工作流程的可行性，为大规模自动化模型审计与调试提供了新范式。

## 2. 论文提出的方法论

- **核心思想**：利用预训练视觉语言模型（GPT-4V）作为骨干，配备一套可编程的“工具API”，使其能通过编写Python代码来对目标模型的子组件（如单个神经元）进行迭代实验，提出并验证假设，最终生成自然语言解释。
- **关键技术细节**：
  - **System类**：封装待解释的视觉模型（如ResNet-152、DINO、CLIP），提供`neuron(image_list)`方法返回激活值和掩码图像。
  - **Tools类**：包含5类工具：
    - `dataset_exemplars(system)`：在ImageNet验证集上找出15张最高激活的真实图像。
    - `text2image(prompts)`：用Stable Diffusion或DALL·E 3生成合成图像，测试神经元对特定概念的响应。
    - `edit_images(prompts, edits)`：用Instruct-Pix2Pix编辑图像，进行因果干预（如替换物体）。
    - `describe_images` / `summarize_images`：调用独立的GPT-4V实例对图像区域进行无偏描述或总结。
    - `log_experiment`：记录实验结果，供后续推理使用。
  - **工作流程**：MAIA根据用户提示（如“描述layer 4 unit 487的行为”）编写Python函数，调用上述工具，观察输出后更新假设，循环直至结论。每步使用链式推理（chain-of-thought）驱动。
- **算法流程（文字描述）**：
  1. 接收解释任务 → 初始化System和Tools对象。
  2. 生成初始假设列表（如“该神经元可能对草地、狗或红色物体敏感”）。
  3. 编写代码运行实验：例如调用`dataset_exemplars`获得顶部激活图像，再用`summarize_images`总结共同视觉模式。
  4. 根据实验结果更新假设（保留或剔除）。
  5. 设计新实验：如生成“带有狗但无草地的图像”来测试因果关系。
  6. 重复步骤3-5直到假设确认，输出最终描述。

## 3. 实验设计

- **使用的数据集/场景**：
  - **真实神经元**：来自ResNet-152（分类）、DINO-ViT（自监督）、CLIP-RN50（多模态）三个模型，每模型各100个神经元（按层均匀采样）。
  - **合成神经元**：新构建的85个合成神经元，基于Grounding DINO + SAM实现，包含单语义、多语义（OR）和条件（|）三种类型，从MILAN-NOTATIONS数据集提取概念。
  - **下游任务**：
    - **伪相关去除**：Spawrious数据集（四类狗品种与背景错误相关）。
    - **偏差发现**：ImageNet分类器（ResNet-152）的类别logit。
- **基准方法**：
  - **MILAN**（Hernandez et al., 2022）：非交互式，仅用预计算的最大激活样本标注。
  - **CLIP-Dissect**（Oikarinen & Weng, 2022）：基于CLIP匹配激活区域。
  - **人类专家**：8名可解释性研究者使用相同MAIA API手动标注25%的神经元。
  - **随机基线**（伪相关任务）。
- **对比方式**：
  - **预测性评估**（图3）：对每个神经元，用候选标签生成7个正向/7个中性提示，再让LM选择最匹配的提示集，生成图像并测量实际激活值。正向-中性激活差越大说明标签越准确。
  - **合成神经元2AFC测试**：人类裁判比较MAIA、MILAN、专家标签与真实标签的一致性。
  - **消融实验**：移除某些工具（如仅用真实样例、仅用合成图像、更换生成模型）后的性能变化。
  - **下游任务**：在伪相关任务中比较使用MAIA选择特征与ℓ1正则化、随机选择、MILAN特征等的分类准确率。

## 4. 资源与算力

- **文中未明确说明训练或推理所需的GPU数量、型号、时长**。仅提到MAIA基于GPT-4V API（商业服务），工具调用涉及Stable Diffusion v1.5、Instruct-Pix2Pix、DALL·E 3（均为现成模型），未报告计算开销。因此论文在算力透明度上存在不足。

## 5. 实验数量与充分性

- **实验组数**：
  - 真实神经元：3种架构 × 100个神经元 = 300个神经元；其中25%由人类专家标注（共约75个）。
  - 合成神经元：85个（单语义、多语义、条件），每种均评估。
  - 消融实验：3种条件（仅真实样例、仅合成图像、DALL·E vs SD）。
  - 下游任务：两个独立应用（伪相关去除、偏差发现），每个均有完整的对比基线。
  - 额外人类预测实验（附录E）：3种模型，25个神经元，10名受试者。
- **充分性**：
  - 实验覆盖了多种架构（CNN、ViT）、多种评估指标（预测性激活、2AFC、下游准确率）、多项消融。
  - 但仅评估了“神经元描述”这一子任务，未对完整电路或多层组合进行实验；合成神经元的复杂性有限（依赖分割模型能力）；下游应用仅在单数据集上验证。
  - **客观性**：预测性评估中，将不同方法的提示混合后由LM选择，减少主观偏见；2AFC由众包人员完成；人类专家使用完全相同的API与工具，公平性较好。

## 6. 论文的主要结论与发现

1. **MAIA生成的神经元描述在预测激活值上显著优于MILAN**，并接近人类专家水平（图4、表A3）。
2. **在合成神经元上，MAIA标签与真实标签的一致性评分(2AFC)为0.73 vs MILAN 0.27，甚至略高于人类专家（0.53 vs 0.47）**。
3. **消融实验表明，同时使用真实样例和合成图像可达到最佳性能**；使用更高质量的生成模型（DALL·E 3）可进一步提升。
4. **在下游任务中，MAIA能自主识别并去除伪相关特征**（Spawrious上平衡准确率0.837 vs 全模型0.731），且无需接触到平衡数据。
5. **MAIA可自动发现分类器的偏差**（如“flagpole”对高度敏感、“suit”偏向男性）。
6. 当前系统仍存在**确认偏差、工具失败（图像生成/编辑不准确）、小样本过度解读**等不足，需要人类监督。

## 7. 优点

- **创新性**：首次将多模态VLM作为代理，结合真实数据探索与合成数据因果干预，实现迭代式自动化解释。
- **模块化与可扩展性**：System和Tools API设计良好，可轻松替换待解释模型或添加新工具。
- **评估体系完善**：引入“预测性评估”替代传统相关性评分，更接近真实因果预测；构建合成神经元作为可验证基准。
- **实用性**：展示了从单神经元到模型级审计的完整流程，有明确的下游应用价值（去偏、找错）。
- **开放透明**：公开了完整API、示例和部分标注数据，便于复现和扩展。

## 8. 不足与局限

- **依赖商业模型**：GPT-4V、DALL·E 3均为闭源API，成本高且有速率限制；开源替代（LLaVA-Next、Gemini 1.0 Pro）性能不足（附录D3）。
- **工具局限性**：图像生成/编辑模型（SD-v1.5、Instruct-Pix2Pix）经常失败（图8），导致MAIA误判；合成神经元仅能模拟简单概念，无法覆盖低层边缘检测等模式。
- **确认偏差**：MAIA有时因单一高激活样本过早下结论，需要人类干预（图A12）。
- **实验覆盖有限**：仅研究视觉模型的神经元级解释，未测试语言模型或电路级解释；下游应用只在单数据集（Spawrious）上验证。
- **评估局限性**：预测性评估依赖文本到图像生成质量，且LM选择提示可能引入间接偏差；人类专家标注只覆盖25%神经元。
- **算力报告缺失**：未给出任何GPU型号、数量或运行时间，影响可重复性。

（完）
