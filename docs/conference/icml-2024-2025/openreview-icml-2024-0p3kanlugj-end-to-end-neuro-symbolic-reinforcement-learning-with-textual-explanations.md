---
title: End-to-End Neuro-Symbolic Reinforcement Learning with Textual Explanations
title_zh: 端到端神经符号强化学习与文本解释
authors: "Lirui Luo, Guoxi Zhang, Hongming Xu, Yaodong Yang, Cong Fang, Qing Li"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=0P3kaNluGj"
tags: ["query:ns-xai"]
score: 9.0
evidence: 端到端神经符号强化学习与文本解释
tldr: 神经符号强化学习虽具有可解释性，但难以高效学习结构化状态且解释性差。本文提出端到端框架，蒸馏视觉基础模型为高效感知模块，在策略学习中联合优化结构化状态与符号策略，并设计GPT提示管道生成文本解释。实验表明该方法在可解释性和任务性能上均显著提升。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1569, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 766, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 689, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1742, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 719, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 1589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1670, \"height\": 1451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0p3kanlugj/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1708, \"height\": 2120, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1773, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 846, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1772, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1478, \"height\": 1095, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 724, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 632, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 814, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1085, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 843, \"height\": 142, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1675, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 945, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1108, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 593, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1462, \"height\": 142, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 578, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0p3kanlugj/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 444, \"height\": 140, \"label\": \"Table\"}]"
motivation: 现有神经符号强化学习方法无法高效利用奖励信号细化结构化状态，且解释需专业知识。
method: 蒸馏视觉基础模型为感知模块，联合学习结构化状态与符号策略，并使用GPT生成文本解释。
result: 在多个视觉任务上，方法实现了更好的可解释性和任务性能。
conclusion: 端到端神经符号框架成功实现了可解释且高效的强化学习。
---

## Abstract
Neuro-symbolic reinforcement learning (NS-RL) has emerged as a promising paradigm for explainable decision-making, characterized by the interpretability of symbolic policies. NS-RL entails structured state representations for tasks with visual observations, but previous methods cannot refine the structured states with rewards due to a lack of efficiency. Accessibility also remains an issue, as extensive domain knowledge is required to interpret symbolic policies. In this paper, we present a neuro-symbolic framework for jointly learning structured states and symbolic policies, whose key idea is to distill the vision foundation model into an efficient perception module and refine it during policy learning. Moreover, we design a pipeline to prompt GPT-4 to generate textual explanations for the learned policies and decisions, significantly reducing users' cognitive load to understand the symbolic policies. We verify the efficacy of our approach on nine Atari tasks and present GPT-generated explanations for policies and decisions.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：深度强化学习在敏感领域（如医疗、自动驾驶）中因黑箱性质存在安全风险，缺乏可解释性。神经符号强化学习（NS-RL）通过结构化状态和符号化策略保证可解释性，但现有方法有两个主要缺陷：  
  - 对于视觉输入任务，结构化状态（如物体坐标）通常来自预训练模型（如SPACE），但无法利用奖励信号进行细化和优化，导致性能显著下降。  
  - 符号化策略虽可解释，但需要用户具备领域知识（如逻辑、文法），对非专家不友好，缺乏可访问性。  
- **整体含义**：本文提出端到端神经符号强化学习框架，旨在同时高效学习结构化状态和符号策略，并利用大语言模型生成自然语言解释，降低用户认知负荷。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将视觉基础模型的感知能力蒸馏到高效的感知模块中，在策略学习过程中随奖励信号端到端优化，同时设计GPT-4提示管道生成文本解释。

- **关键技术细节**：
  1. **视觉感知模块**：
     - 使用FastSAM和DeAot模型（零样本）从约10,000帧中提取物体边界框，生成帧-符号数据集（包含物体坐标、尺寸、存在性）。
     - 多任务CNN编码器：预测物体存在（平衡焦点损失）、坐标（L1损失）、尺寸。
     - 预训练感知模块，提高样本效率。
  2. **符号策略学习**：
     - 使用方程学习网络（EQL）表示符号策略，激活函数包括平方、立方、常数、恒等、乘、加。
     - 引入**神经引导**机制：用一个神经网络演员（π_neural）与环境交互探索，EQL演员（π_EQL）蒸馏π_neural的策略，两者联合优化。
     - 损失函数：PPO损失 + 蒸馏交叉熵损失 + L0.5稀疏正则化 + 坐标预测损失L_cnn。
     - 仅在每次更新的最后一步优化L_cnn和L_ng，避免感知模块剧烈变化。
  3. **文本解释生成**：
     - 概念接地：将任务描述、坐标语义、策略表达式输入GPT-4。
     - 分步骤链式思考：分析输入变量到中间变量映射、中间变量到动作logits映射、总结触发模式。
     - 决策解释：提供具体状态下的物体坐标值、动作、梯度，指导LLM生成原因分析。

## 3. 实验设计

- **数据集/场景**：
  - 9个Atari游戏：Pong、BeamRider、Enduro、Qbert、SpaceInvaders、Seaquest、Breakout、Freeway、MsPacman。
  - 额外使用MetaDrive自动驾驶环境（验证泛化性）。

- **Benchmark**：
  - 任务性能：10M环境步后的测试回报（均值±标准差）。
  - 坐标预测精度：MAE和F-MAE（仅针对策略相关物体）。
  - 推理速度：每步推理时间。

- **对比方法**：
  - 神经网络基线：Neural（相同网络结构但不使用帧-符号数据集）、Coor-Neural（使用预测坐标作为神经策略输入）、SA-Neural（槽注意力）、SPACE-Neural（SPACE模型）。
  - 现有NS-RL方法：CGP、DiffSES、DSP、NUDGE。
  - 消融变体：w/o Pre-train（不预训练）、Fixed（冻结感知模块）、w/o NG（去除神经引导）。

## 4. 资源与算力

- **硬件**：AMD Ryzen 9 5950X CPU、NVIDIA GeForce RTX 3090 Ti（24GB显存）。
- **训练时间**：文中未给出总训练时长，但报告了各部分平均耗时：
  - 感知模块预训练：2.6 ms/step
  - 策略学习（含微调）：7.3 ms/step
  - 策略学习（无微调）：6.2 ms/step
- **说明**：论文未明确列出总GPU小时数，但指出端到端训练中视觉模块的额外开销仅占总体约1/10，证明了效率优势。

## 5. 实验数量与充分性

- **实验数量**：
  - 主性能对比：9个Atari任务，每个任务3个种子。
  - 消融实验：4种变体（w/o Pretrain, Fixed, w/o NG, Coor-Neural）在5个Atari任务上报告性能及坐标精度。
  - 超参数鲁棒性实验：在SpaceInvaders上改变正则化权重、宽度、层数、L_cnn权重；并在其他8个任务上重复类似分析（见附录图A2）。
  - 额外基线：与CleanRL对比（表A8）。
  - 推理速度对比：与SPACE-Neural、SA-Neural对比。
  - 文本解释：展示了Pong的完整策略解释和决策解释示例。
- **充分性与客观性**：
  - 覆盖了多样化场景（简单/复杂、干净/噪声背景、恒定/变化物体）。
  - 消融实验设计合理，验证了每个关键组件（预训练、端到端微调、神经引导）的必要性。
  - 超参数鲁棒性良好，使用相同超参数集合于所有任务。
  - 坐标预测可视化（Fig. A3）直观展示了端到端训练后对策略相关物体预测的改善。
  - 但未对解释质量进行定量评估（如人工评估、一致性指标），这是客观性上的一个不足。

## 6. 主要结论与发现

- **性能**：INSIGHT在所有9个Atari任务上匹配甚至超过神经网络基线，并显著优于所有现有NS-RL方法。
- **效率**：推理速度比基于SPACE或槽注意力的方法快一个数量级。
- **坐标预测**：端到端策略学习能明显提升策略相关物体的坐标预测精度（F-MAE降低），而对无关物体精度有所下降，表明奖励信号引导了注意力焦点。
- **神经引导**：提出的神经引导机制对提升性能和改善坐标预测都至关重要。
- **解释**：GPT-4生成的策略解释和决策解释虽有小错误，但整体上能准确识别关键变量、揭示决策模式，对非专家用户友好。

## 7. 优点

- **端到端联合学习**：首次在NS-RL中实现视觉感知和符号策略的端到端优化，利用奖励信号细化状态，克服了先前方法的性能瓶颈。
- **高效感知模块**：通过蒸馏预训练模型（无需在线图像重建），既提高了样本效率又保持了计算效率。
- **可访问性提升**：使用LLM自动生成自然语言解释，无需用户具备符号知识，降低了使用门槛。
- **实验设计全面**：覆盖多个Atari任务、复杂驾驶场景，消融实验、超参数分析和可视化证明了方法的鲁棒性。
- **框架通用性**：方法不依赖特定任务假设，可推广到其他视觉RL任务。

## 8. 不足与局限

- **符号策略表达能力有限**：EQL网络无法表达逻辑运算（如与/或），不适用于需要推理的任务。
- **解释缺乏定量评估**：文本解释仅展示为示例，未进行人工评估、精确度分析或一致性检验，可靠性存疑。
- **感知模块依赖预训练模型**：虽然蒸馏提升了效率，但FastSAM/DeAot的质量会影响初始数据集，且分割过程中可能引入噪声（如MsPacman的低精度）。
- **实验环境限制**：仅在Atari和MetaDrive上验证，未涉及需要复杂物体关系推理的真实场景。
- **超参数调整空间**：虽然鲁棒，但λ_cnn和λ_reg等需要手动设定，理论上仍存在优化空间。
- **训练流程较复杂**：需要先训练神经网络采集帧-符号数据集，再进行预训练和策略学习，相比纯端到端方法更繁琐。

（完）
