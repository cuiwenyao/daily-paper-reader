---
title: Analysis for Abductive Learning and Neural-Symbolic Reasoning Shortcuts
title_zh: 溯因学习与神经符号推理捷径的分析
authors: "Xiao-Wen Yang, Wen-Da Wei, Jie-Jing Shao, Yu-Feng Li, Zhi-Hua Zhou"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=AQYabSOfci"
tags: ["query:ns-xai"]
score: 9.0
evidence: 分析神经符号模型中的推理捷径问题
tldr: 针对神经符号模型中的推理捷径问题，本文提出了一种量化分析方法。该方法揭示了影响泛化能力的三个关键因素，并探讨了缓解策略。通过实验验证，量化了推理捷径对模型性能的损害，为构建更可靠的神经符号系统提供了理论基础。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-aqyabsofci/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 831, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aqyabsofci/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aqyabsofci/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1596, \"height\": 924, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-aqyabsofci/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aqyabsofci/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 801, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aqyabsofci/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 848, \"height\": 117, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aqyabsofci/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1792, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aqyabsofci/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 1006, \"label\": \"Table\"}]"
motivation: 神经符号模型存在推理捷径问题，导致泛化能力受限，缺乏理论分析。
method: 提出一种量化分析方法，评估推理捷径的损害程度，并识别影响因素。
result: 量化了三个主要因素对神经符号算法的影响，验证了分析的有效性。
conclusion: 该分析方法有助于理解和缓解神经符号模型中的推理捷径问题。
---

## Abstract
Abductive learning models (ABL) and neural-symbolic predictive models (NeSy) have been recently shown effective, as they allow us to infer labels that are consistent with some prior knowledge by reasoning over high-level concepts extracted from sub-symbolic inputs. However, their generalization ability is affected by reasoning shortcuts: high accuracy on given targets but leveraging intermediate concepts with unintended semantics. Although there have been techniques to alleviate reasoning shortcuts, theoretical efforts on this issue remain to be limited. This paper proposes a simple and effective analysis to quantify harm caused by it and how can mitigate it. We quantify three main factors in how NeSy algorithms are affected by reasoning shortcuts: the complexity of the knowledge base, the sample size, and the hypothesis space. In addition, we demonstrate that ABL can reduce shortcut risk by selecting specific distance functions in consistency optimization, thereby demonstrating its potential and approach to solving shortcut problems. Empirical studies demonstrate the rationality of the analysis. Moreover, the proposal is suitable for many ABL and NeSy algorithms and can be easily extended to handle other cases of reasoning shortcuts.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的中文总结。

### 1. 论文的核心问题与整体含义

- **研究动机**：神经符号模型旨在结合神经网络的感知能力与符号系统的逻辑推理能力。然而，这类模型普遍存在**“推理捷径”**问题：模型虽然在目标任务上取得高准确率，但其用于推理的中间概念（如“红灯”、“行人”）可能学习到错误的语义。这严重损害了模型的**泛化能力**和**可解释性**。
- **核心问题**：此前虽有缓解推理捷径的经验性方法，但缺乏对其成因与影响因素的**理论分析**。论文的核心是填补这一空白，从理论上量化推理捷径的危害并提出缓解策略。
- **整体含义**：该研究为神经符号系统的可靠性提供了理论基础，通过量化关键因素（知识库复杂度、样本量、假设空间），揭示了导致推理捷径的根本原因，并为设计更鲁棒的算法提供了指导。

### 2. 论文提出的方法论

论文的核心是提出一个理论分析框架，用于量化推理捷径的风险，其核心思想是**将推理捷径的严重性定义为模型理想学习目标与实际优化目标之间的差距**。

- **关键定义**：
    - **快捷风险 (Shortcut Risk, Rs)**：定义为理想交叉熵损失与实际神经符号损失之差（`Rs = L - L_nesy`），直接度量了捷径问题的严重程度。
    - **知识库复杂度 (Complexity of KB, D)**：用与知识库矛盾的中间概念的平均数量来度量。复杂度越高，知识库对模型的约束越强，捷径风险越低。
- **技术细节与推导**：
    1. **定理4.1**：证明当模型假设空间足够大且知识库复杂度低时，\(R_s\)可能是无界的，揭示了捷径风险的根本来源。
    2. **定理4.4 & 4.5**：在两种常见的假设下，推导了\(R_s\)的上界：
        - **标签平滑假设 (Label Smooth Assumption)**：要求模型输出概率不应过于极端。
        - **预训练假设 (Pre-training Assumption)**：要求模型对错误标签的预测概率极小。
      这些上界表明，\(R_s\)的渐近复杂度为 `O(ln(C - D) + 1/√N + γ)`，其中：
      - `C`是概念空间大小
      - `D`是知识库复杂度
      - `N`是样本量
      - `γ`是与假设空间特性相关的常数。
    结论是：**知识库越复杂、训练样本越多、模型假设空间约束越强（如使用标签平滑或预训练），推理捷径风险越低**。
    3. **对ABL的分析**：
        - **定理5.2**：证明在简单距离函数下，ABL的快捷风险\(R_s^{ABL}\)总小于传统NeSy算法的\(R_s\)。
        - **定理5.3**：进一步证明，若ABL算法的距离函数能确保采样出错误中间概念的误差率\(κ\)足够小，那么\(R_s^{ABL}\)的期望上界可降至**O(κ)**，即捷径风险可被极大缓解。

### 3. 实验设计

- **数据集与场景**：
    1. **MNIST-Addition**：合成数据，输入为一对MNIST手写数字图片，输出为其和。通过控制训练数据中不同目标标签（如`0+0=0`和`1+1=2`）的比例，构建了**6个难度递进（I-VI）的数据集**来模拟不同的知识库复杂度。
    2. **BDD-OIA**：真实自动驾驶场景数据集，输入为驾驶场景图片或特征嵌入，输出为四种驾驶决策（前进、停止、左转、右转）。任务包含21个中间概念和复杂的知识规则。
- **Benchmark**：主要评测指标为**网格准确率（Grid Accuracy, GAcc）**，即模型对中间概念（如MNIST数字）的预测准确率，用以间接衡量捷径风险（GAcc越高，捷径风险越低）。
- **对比方法**：
    - **传统NeSy基线**：语义损失 (SL)、DeepProbLog (DPL)、逻辑张量网络 (LTN)。
    - **ABL基线 (ABL)**：使用平凡距离函数 `Dis=0`。
    - **ABL变体**：代表不同假设空间约束和距离函数：
        - `ABL+L`：带标签平滑。
        - `ABL+P`：带预训练模型。
        - `ABL(H)`：使用汉明距离。
        - `ABL(C)`：使用模型自身置信度作为距离（`1 - f(z|x)`）。
        - `ABL(P)`：使用预训练模型置信度作为距离（`1 - g(z|x)`）。
- **对比方式**：在MNIST任务上，所有方法在固定训练样本量（30，000）和相同测试集上，针对6个不同难度水平进行性能评估。在BDD-OIA任务上，比较不同ABL变体与DPL的性能。

### 4. 资源与算力

论文中未详细说明训练所耗费的总算力（如总GPU时数、具体训练epoch数）。仅在实验部分提到：
- **硬件**：所有实验均使用NVIDIA A800 GPU运行。
- **框架**：基于PyTorch 实现。
- **优化器**：均使用Adam优化器，学习率为`3e-4` (MNIST) 或 `5e-3` (BDD-OIA)。
- **重复实验**：每组实验均重复5次以报告均值与标准差。

### 5. 实验数量与充分性

- **实验数量**：
    - **MNIST任务**：在6个不同难度的子集上，对比了7种方法（3种NeSy + 4种ABL变体），结果以表格和折线图形式呈现。
    - **BDD-OIA任务**：在1个真实场景数据集上，对比了5种方法（1种NeSy + 4种ABL变体）。
    - **消融/变体分析**：研究了不同距离函数（`ABL(H)`, `ABL(C)`, `ABL(P)`）和不同假设空间约束（`ABL+L`, `ABL+P` 在表1中未单独列出，但在图2中有体现）的影响。
- **实验充分性与客观性**：
    - **充分性**：实验验证了理论中关于“知识库复杂度”和“假设空间约束”的核心结论，即随着知识库复杂度增加，GAcc普遍提高；使用预训练模型（`ABL(P)`）和标签平滑（`ABL+L`）能显著提升GAcc。
    - **公平性**：在MNIST任务上，严格控制了训练样本量和测试集，使得不同方法的比较具备一定公平性。
    - **存在不足**：实验主要在两个任务上进行，虽具有一定代表性，但规模相对有限。对于理论推导中“样本量N”的影响，实验中未设专门的控制变量实验。此外，未明确说明如何为所有方法选择最优超参数，可能影响对比的绝对公平性。

### 6. 论文的主要结论与发现

1. **理论框架有效**：提出的快捷风险定义`Rs`和知识库复杂度`D`能够有效量化推理捷径问题。
2. **影响因素量化**：理论证明了影响捷径风险的三大核心因素是**知识库复杂度、训练样本量和模型假设空间**。知识库越复杂、样本越多、假设空间约束越强，捷径风险越低。
3. **ABL显著优于NeSy**：理论和实验均表明，ABL框架在缓解推理捷径问题上优于传统的NeSy算法（如DPL、LTN），其核心优势在于通过伪标签迭代更新，而非一次性将所有可能概念纳入损失函数。
4. **距离函数至关重要**：ABL中距离函数的选择对性能有决定性影响。使用**预训练模型的置信度**作为距离函数（`ABL(P)`）能几乎完全消除捷径风险，在所有实验中获得最优的GAcc。
5. **常见策略有效**：标签平滑和预训练等策略，通过约束假设空间，能够有效降低推理捷径风险，与理论分析一致。

### 7. 优点

- **理论贡献突出**：首次为神经符号学习的“推理捷径”问题提供了系统、严谨的理论分析，提供了明确的数学定义和量化上界，为该领域奠定了理论基础。
- **分析视角独特**：将捷径风险归结为理想学习目标与实际优化目标的差距，并揭示了知识库复杂性的两个关键属性（数据依赖和规则依赖），视角新颖且深刻。
- **理论与实践结合紧密**：实验结果直接支持了理论推导的核心结论（如知识库复杂度的影响、ABL的优越性），增强了论文的说服力。
- **具有实用指导意义**：理论分析直接指出了缓解捷径问题的有效方法（增加数据、构建复杂知识库、使用标签平滑/预训练、为ABL设计高质量距离函数），具有重要的实践价值。

### 8. 不足与局限

- **实验覆盖范围有限**：仅使用了两个任务（一个合成任务、一个真实任务），且BDD-OIA任务使用了预处理后的嵌入特征，未涉及端到端的原始图像输入，其结论在更广泛、更复杂的NeSy应用上的泛化性有待验证。
- **“样本量”影响缺乏直接实验**：理论推导了样本量`N`的影响，但所有实验都在固定样本量（30，000）下进行，未通过改变`N`来直接验证这一结论。
- **未讨论数据分布影响**：论文指出定义的`D`（知识库复杂度）未考虑数据分布的方差，这可能影响分析的精细度。在不同分布偏差下，相同知识库的效果可能不同。
- **模型调优细节不明确**：对于所有对比方法，未详细说明超参数（如η、ϵ、学习率等）的搜索过程和最优结果，对比的公平性存在一定风险。
- **缺乏随机种子信息**：实验重复了5次，但未提及是否使用了固定的随机种子来控制不同方法实验间的随机性（如模型初始化、数据加载顺序），可能引入额外的方差。

（完）
