---
title: On the Independence Assumption in Neurosymbolic Learning
title_zh: 论神经符号学习中的独立性假设
authors: "Emile van Krieken, Pasquale Minervini, Edoardo Ponti, Antonio Vergari"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=S1gSrruVd4"
tags: ["query:ns-xai"]
score: 9.0
evidence: 批判神经符号学习中的独立性假设
tldr: 该论文批判了神经符号学习系统中常用的条件独立性假设，理论证明了该假设会导致神经网络过度自信，无法表示不确定性，且损失函数最小值高度非凸难以优化。为神经符号推理的损失函数设计提供了重要理论指导。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 499, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 585, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 656, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1414, \"height\": 837, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-s1gsrruvd4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1418, \"height\": 854, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-s1gsrruvd4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1489, \"height\": 1039, \"label\": \"Table\"}]"
motivation: 神经符号学习中的独立性假设限制了模型表达能力和不确定性量化。
method: 理论分析假设对优化和不确定性表征的影响，给出数学证明。
result: 证明了独立性假设导致过度自信和高度非凸的损失景观。
conclusion: 应避免该假设以提升神经符号系统的鲁棒性和可解释性。
---

## Abstract
State-of-the-art neurosymbolic learning systems use probabilistic reasoning to guide neural networks towards predictions that conform to logical constraints. Many such systems assume that the probabilities of the considered symbols are conditionally independent given the input to simplify learning and reasoning. We study and criticise this assumption, highlighting how it can hinder optimisation and prevent uncertainty quantification. We prove that loss functions bias conditionally independent neural networks to become overconfident in their predictions. As a result, they are unable to represent uncertainty over multiple valid options. Furthermore, we prove that the minima of such loss functions are usually highly disconnected and non-convex, and thus difficult to optimise. Our theoretical analysis gives the foundation for replacing the conditional independence assumption and designing more expressive neurosymbolic probabilistic models.

---

## 论文详细总结（自动生成）

好的，请查收基于您提供的论文内容生成的详细中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：神经符号学习（Neurosymbolic Learning）旨在结合神经网络感知和符号推理，利用逻辑约束指导神经网络学习。然而，当前主流方法大多假设给定输入时，不同符号（symbol）的概率是**条件独立的**（Conditional Independence Assumption）。论文深刻批判了这一假设，指出它会导致模型过度自信、无法表示不确定性，并使得优化过程变得极为困难。
- **研究动机**：尽管条件独立性假设简化了概率推理，使其计算可行（如加权模型计数变为多项式时间），但作者认为其代价过于高昂。通过一个交通灯例子（红绿灯不能同时亮），他们直观地展示了：满足逻辑约束的可行解空间（三个可能世界：红亮、绿亮、都不亮）中，条件独立模型只能表示“要么红灯灭，要么绿灯灭”的确定性选择，而无法表示“红灯亮或绿灯亮等概率”这类合理的混合不确定性。这促使作者从理论上全面剖析该假设的缺陷。
- **整体含义**：论文为神经符号学习领域提供了关键的理论基础，解释了为何更富有表达力的感知模型（如软最大化、混合独立分布）在实践中表现更优，并指明了未来改进方向——设计能够合理表示不确定性的、更富有表达力的概率神经符号模型。

### 2. 论文提出的方法论：核心思想、关键技术细节

论文主要采用**理论分析与数学证明**的方法，不提出新的算法，而是对现有方法背后的假设进行系统剖析。其方法论核心可分解为：

- **定义与形式化**：
    - 将神经符号学习问题形式化为：通过神经网络 \(p_\theta(\mathbf{w}|\mathbf{x})\) 定义世界 \(\mathbf{w} \in \{0,1\}^n\) 上的分布，并利用约束 \(\phi(\mathbf{w})\)（布尔函数）计算加权模型计数（WMC）\(p_\theta(\phi=1|\mathbf{x})\)，通常以 **语义损失（Semantic Loss）** \(-\log p_\theta(\phi=1|\mathbf{x})\) 作为训练目标。
    - 条件独立性假设将联合分布简化为乘积形式：\(p_\theta(\mathbf{w}|\mathbf{x}) = \prod_{i=1}^n p_\theta(w_i|\mathbf{x})\)。

- **关键技术与证明**：
    1. **偏差向确定性解**：利用逻辑学中的**蕴涵项（implicant）** 概念。证明：独立分布 \(p_\mu(\mathbf{w})\) 最小化语义损失当且仅当其确定性部分（即概率为0或1的变量）形成了约束 \(\phi\) 的一个蕴涵项。这意味着模型被迫在部分变量上做出确定性选择，从而无法在多个有效解之间表达不确定性（定理3.1 & 4.3）。
    2. **不可表示的条件分布**：证明即使是对独立分布进行条件化（\(p_\mu(\mathbf{w}|\phi=1)\)），该条件分布能被另一个独立分布表示的唯一条件是：原始分布本身必须对某些变量是确定性的。这表明通过学习获得不确定性表达非常困难（定理4.4）。
    3. **几何与拓扑特征**：
        - 提出**蕴涵立方形集（cubical set）** \(C_\phi\)：由所有质蕴涵项（prime implicant）对应的立方体（固定确定性变量，其余变量取 \([0,1]\)）并集构成。证明 \(C_\phi\) 精确刻画了所有可行独立分布的参数空间（定理4.10）。
        - **非凸性**：证明语义损失在独立分布上为凸函数，当且仅当约束 \(\phi\) 只有一个质蕴涵项（即形如 \(\bigwedge_{i} l_i\)）。其他情况下，可行解空间是非凸的（定理4.11）。
        - **不连通性**：引入**质蕴涵图（Prime Implicant Graph）**，其顶点为可能世界，边连接被同一质蕴涵项覆盖的世界。证明 \(C_\phi\) 的连通分量与该图连通分量一一对应。对于大量约束（如XOR、MNIST加法），可行解空间由多个孤立顶点组成，优化时无法平滑迁移（定理4.13）。
    4. **计算同调**：指出可使用计算同调（computational homology）算法（如Smith标准形）计算 \(C_\phi\) 的拓扑结构（如孔洞数量），从而量化优化难度（第4.5节）。

### 3. 实验设计：数据集、benchmark与对比方法

- **核心实验**：论文并未进行大规模基准测试，而是在一个**高度可解释的玩具问题**（“红绿灯”问题 \( \phi = \neg r \vee \neg g \)）上进行可视化实验，用于直观验证理论结果。
- **场景**：
    - 比较**独立模型**（参数μ经sigmoid输出）与**富有表达力的模型**（4个logits经softmax输出）在最小化语义损失后的行为。
    - 可视化初始分布（\(p(r,g)=0.7\)），并观察训练后（10000次梯度下降，学习率0.1）分布收敛的位置。
    - 额外测试了**熵正则化**（最大化条件熵）对训练偏置的影响。
- **Benchmark与对比方法**：论文未设置经典的基准数据集（如MNIST加法、CLEVR-Hans等），主要将独立模型与软最大模型（代表富有表达力模型）进行理论对比。在附录A中，定性地讨论了模糊逻辑（Product t-conorm、Gödel、Łukasiewicz）也表现出类似的确定性偏置。

### 4. 资源与算力

- **未明确说明**：论文全文未提及实验所用的GPU型号、数量或训练时长。其“实验”部分仅基于玩具示例，计算量极小。因此，无法提供关于算力的具体细节。

### 5. 实验数量与充分性

- **实验数量**：实验数量非常少，集中于一个玩具示例（红绿灯问题）的可视化分析。附录中包含针对XOR、3变量示例以及混合独立分布的补充可视化实验。
- **充分性与客观性**：
    - **局限性**：作为一篇纯理论论文，其实验部分的主要目的是**验证理论结论**，而非提供性能对比。从这个角度看，实验是充分的：成功可视化了独立模型收敛于两个孤立线段（对应蕴涵项），而软最大模型覆盖了整个三角形；同时说明了熵正则化的不同效果。
    - **公平性**：实验本身并无不同方法之间的公平比较，主要服务于理论阐述。结论主要来自于严格的数学证明，而非实验归纳，因此理论部分的可靠性较高。
    - **风险**：实验结果仅基于低维（2变量）场景，未在高维真实数据集上验证独立性假设的实际影响。论文作者也承认这一点，并将大规模实证留作未来工作。

### 6. 论文的主要结论与发现

- **条件独立性假设导致确定性偏置**：独立模型被迫在部分变量上做出确定性选择（形成蕴涵项），无法表示对多个有效选项的不确定性。
- **损失函数难以优化**：语义损失在独立分布约束下的最小值通常是**非凸且高度不连通的**，导致模型难以在全局最优解间平滑移动，优化困难。
- **理论框架**：论文建立了从逻辑蕴涵项到几何立方体集的映射（\(C_\phi\)），为理解和分析独立性假设的影响提供了强大的数学工具（同调理论）。
- **对实践的启示**：明确建议放弃或放宽条件独立性假设，采用更有表达力的模型（如软最大化、混合独立分布、自回归模型），以更好地量化不确定性并改善优化效果。附录D证明，至少使用2个独立混合成分即可保证最小值集连通。

### 7. 优点

- **理论贡献深刻**：首次为“条件独立性假设有害”这一直觉提供了严格、通用的数学证明，填补了该领域的理论空白。
- **视角独特**：将逻辑学（蕴涵项）、几何（立方体集）和拓扑（同调）交叉用于分析机器学习假设，方法新颖且富有洞察力。
- **框架清晰**：从简单的例子出发，逐步建立形式化定义，最终给出可计算的特征（如质蕴涵图），逻辑链条严密，易于理解。
- **指导性强**：结论明确指出了现有主流方法的根本缺陷，并为设计更优的神经符号模型指明了具体方向（如使用富有表达力的分布、熵正则化等）。

### 8. 不足与局限

- **实证验证不足**：论文所有实验都基于低维玩具问题，缺乏在真实数据集（如MNIST加法、CLEVR任务）上的大规模性能对比实验。结论的有效性在真实场景下尚需验证。
- **忽视实际隐含问题**：论文仅关注了构造上的可行分布集，但未考虑**仅含逻辑约束、无监督信号时，模型通过蕴涵项确定性地选择一个解，可能学习到“推理捷径（Reasoning Shortcut）”** 这一更严重的问题。作者在相关工作部分提及，但未将其纳入核心分析。
- **应用限制**：完全放弃独立性假设通常会导致精确推理变得#P-hard，因此需要工程上的权衡。论文虽在附录D讨论了混合独立分布，但指出其参数效率通常很差。如何在实践中有原则地平衡表达力与可伸缩性，仍是未决问题。
- **不涉及连续变量**：论文仅考虑二进制符号（\(w_i \in \{0,1\}\)），未讨论连续变量上的逻辑约束，限制了其适用范围。
- **假设前提较为理想**：理论分析假设“约束完全正确”且“只有约束提供反馈（无标签）”，在实际弱监督或完全监督混合场景中，独立性假设可能影响较小，论文对此分析不足。

（完）
