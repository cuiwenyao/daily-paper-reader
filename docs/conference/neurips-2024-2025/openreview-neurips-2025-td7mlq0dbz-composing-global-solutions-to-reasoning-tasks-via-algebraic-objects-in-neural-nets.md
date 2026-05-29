---
title: Composing Global Solutions to Reasoning Tasks via Algebraic Objects in Neural Nets
title_zh: 通过神经网络中代数对象组合推理任务的全局解
authors: Yuandong Tian
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tD7MLq0dbZ"
tags: ["query:ns-xai"]
score: 4.0
evidence: 神经网络中代数结构用于推理任务，类符号组合
tldr: 推理任务的神经网络解空间难以理解。本文证明两层网络权重空间具有半环代数结构，可将部分解分析组合为全局最优解。这种代数视角为神经符号融合提供理论基础，但仅限于小规模任务。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 567}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1316, \"height\": 411}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 541}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1317, \"height\": 539}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1167, \"height\": 430}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 506}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1170, \"height\": 387}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1320, \"height\": 553}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1424, \"height\": 285}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1318, \"height\": 551}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1318, \"height\": 549}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-td7mlq0dbz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1320, \"height\": 551}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1328, \"height\": 478}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 229}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-td7mlq0dbz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1604, \"height\": 1113}]"
motivation: 神经网络求解推理任务时结构不明，缺乏组合性。
method: 揭示权重空间的半环代数结构，利用环同态构造全局解。
result: 在模加等任务上分析构造全局最优解。
conclusion: 代数结构为神经符号推理提供理论桥梁，但需扩展至大模型。
---

## Abstract
We prove rich algebraic structures of the solution space for 2-layer neural networks with quadratic activation and $L_2$ loss, trained on reasoning tasks in Abelian group (e.g., modular addition). Such a rich structure enables \emph{analytical} construction of global optimal solutions from partial solutions that only satisfy part of the loss, despite its high nonlinearity. We coin the framework as \ours{} (\emph{\underline{Co}mposing \underline{G}lobal \underline{S}olutions}). Specifically, we show that the weight space over different numbers of hidden nodes of the 2-layer network is equipped with a semi-ring algebraic structure, and the loss function to be optimized consists of \emph{sum potentials}, which are ring homomorphisms, allowing partial solutions to be composed into global ones by ring addition and multiplication. Our experiments show that around $95\%$ of the solutions obtained by gradient descent match exactly our theoretical constructions. Although the global solutions constructed only required a small number of hidden nodes, our analysis on gradient dynamics shows that overparameterization asymptotically decouples training dynamics and is beneficial. We further show that training dynamics favors simpler solutions under weight decay, and thus high-order global solutions such as perfect memorization are unfavorable. The code is open sourced\footnote{\url{https://github.com/facebookresearch/luckmatters/tree/yuandong3/ssl/real-dataset}}.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：神经网络在推理任务（如模加法预测 $a+b \bmod d$）中的解空间结构高度非线性，难以理解。现有工作多关注可解释性或通过逆向工程寻找解析解，但缺乏系统性的代数框架来组合和构造全局最优解。
- **动机**：探索两层神经网络在阿贝尔群推理任务中的解空间是否具有代数结构，从而允许像搭积木一样从部分解分析组合出全局最优解。
- **整体含义**：揭示神经网络权重空间存在半环代数结构，损失函数中的“和势”（sum potentials）是环同态，使得全局解可通过环运算由部分解组合得到。这一框架（CoGS）为理解神经网络在推理任务中的学习机制提供了理论工具。

## 2. 论文提出的方法论
### 核心思想
- 将不同宽度（隐藏节点数）的两层神经网络权重集合 $\mathcal{Z} = \bigcup_{q\ge0} \mathcal{Z}_q$ 定义为一个**交换半环**，加法为拼接（concatenate），乘法为Khatri-Rao积（对应维度上的外积）。
- 损失函数 $L_2$ 可以分解为依赖于若干**和势**（sum potentials）$r_{k_1k_2k}(z)$ 和 $r_{p,k_1k_2k}(z)$ 的表达式。这些和势是**环同态**：$r(z_1+z_2)=r(z_1)+r(z_2)$，$r(z_1*z_2)=r(z_1)r(z_2)$。
- 利用环同态性质，可以将满足部分约束条件的部分解组合成满足全部约束的全局解。例如，先构造单频率的生成元，再通过多项式 $\rho(u)=\prod_{s\in\Omega_R(u)}(u+\hat{s})$ 得到部分解，最后通过环加法和乘法组合成全局最优解。

### 关键技术细节
- **损失函数解耦**：对于阿贝尔群的乘法预测，两层二次激活网络 $L_2$ 损失可写作 $\ell = d^{-1}\sum_{k\neq0}\ell_k + (d-1)/d$，其中 $\ell_k$ 包含对角项 $r_{kkk}$、交叉项 $r_{k_1k_2k}$ 以及 $r_{p,k',\cdot,k}$ 等。
- **全局最优的充分条件**：若权重 $z$ 满足 $r_{kkk}(z)=I(k\neq0)$，且所有其他 $r$ 项为零，则为全局最优解（损失为零）。
- **构造全局解的例子**：
  - **Order-6 Fourier解** $z_{F6}$：每个频率使用6个隐藏节点，由3阶和2阶部分解通过环乘法组合。
  - **Order-4/6混合解** $z_{F4/6}$：部分频率用Order-4解，其余用Order-6并添加偏置以抵消残留项，总阶数 $2d$ 低于 $z_{F6}$。
  - **完美记忆化解** $z_M$：阶数为 $d^2$，对应训练集上的完全记忆。
- **训练动力学分析**：
  - 权重衰减偏好低阶解（定理5）：若 $z = y * z'$ 且两者均为全局最优，则存在零损失路径连通，且低阶解 $L_2$ 范数更小。
  - 无限宽度时，和势的动力学解耦（定理6），过参数化有利于简化分析。

## 3. 实验设计
- **任务**：模加法（阿贝尔群乘法预测的特例），即给定 $a,b$ 预测 $(a+b)\bmod d$。
- **数据集**：合成数据，90%/10% 训练/测试划分。
- **模型**：两层神经网络，二次激活，隐藏节点数 $q$ 从 256 到 2048 不等。
- **基准对比**：主要对比**理论构造解**（Order-4、Order-6、完美记忆化）与梯度下降解。不涉及其他现有方法对比，而是检验梯度下降解是否匹配理论构造。
- **评价指标**：解阶分布（每个频率的隐藏节点数）、因子化误差（与理论构造的匹配程度）、MSE损失和准确率。

## 4. 资源与算力
- 文中明确说明：“Each training with a fixed set of hyperparameter configuration is conducted on NVIDIA V100 for a few minutes.”
- 未详细列出训练总时长、GPU 数量、分布式策略等，仅提及单次训练数分钟。对于不同 $d$ 和 $q$ 的组合，实验规模适中。

## 5. 实验数量与充分性
- **实验组数**：
  - 改变群大小 $d\in\{23,71,127\}$。
  - 改变隐藏节点数 $q\in\{256,512,1024,2048\}$。
  - 改变权重衰减系数（5个不同值）。
  - 每个配置运行5个随机种子。
  - 总计约 $3\times4\times5\times5=300$ 次独立训练（文中未完全列出所有组合，但 Fig.4,8,9,10,11 展示了分布）。
  - 还进行了因子化匹配分析（Table 2），覆盖 $d=23,71,127$，$q=512$，权重衰减 $5\times10^{-5}$。
- **充分性**：实验覆盖了不同群大小、不同宽度、不同正则化强度，统计了约95%的梯度下降解与理论构造匹配（Table 2），并展示了动力学演化（Fig.3）。整体较充分，但仅针对模加法单一任务，未扩展到其他阿贝尔群推理（虽然理论适用于任何有限阿贝尔群）。

## 6. 论文的主要结论与发现
1. **半环代数结构存在**：两层神经网络权重空间具有交换半环结构；和势是环同态，允许部分解组合成全局解。
2. **全局解可分析构造**：构造了 Order-4、Order-6 的 Fourier 型全局解，以及 Order-$d^2$ 的完美记忆化解。
3. **梯度下降解匹配理论**：约95%的梯度下降解可因子化为理论构造的 Order-4/6 解，且匹配度高（因子化误差接近0）。
4. **权重衰减偏好低阶解**：由于低阶解 $L_2$ 范数更小，且存在零损失路径连接所有全局解，因此动力学倾向于低阶解（如 Order-4/6），而高阶完美记忆化解不出现。
5. **过参数化有益**：无限宽度下和势的动力学解耦，但实际最终解仅需少量隐藏节点（每频率6个即可）。

## 7. 优点
- **理论创新**：首次发现神经网络解空间的代数结构，将组合数学（半环、环同态）引入深度学习训练分析。
- **系统性构造方法**：提供了从部分解到全局解的组合机制，超越了传统逆向工程或经验观察。
- **紧贴实验**：95% 匹配率说明理论构造并非空谈，而是真实解的结构。
- **动力学解释**：解释了权重衰减为何偏好低阶解，以及过参数化的作用。

## 8. 不足与局限
- **架构局限**：仅针对两层网络、二次激活函数（或可拓展至 σ(0)=0 且能用泰勒展开的激活），未覆盖 Transformer 或更深网络。
- **任务局限**：实验仅验证模加法（循环群），虽然理论适用于任意有限阿贝尔群，但未实验其他群。群作用预测扩展（Appendix F）未做实验验证。
- **未解释 grokking**：虽然提及可作为未来方向，但本文未直接分析泛化延迟涌现现象。
- **隐式偏差未完全解释**：某些理论可行的解（如 $z_{3c}*z_{syn}$）在梯度下降中未出现，表明存在额外的隐式偏好，但本文未完全刻画。
- **实验规模有限**：最大群大小 d=127，隐藏节点最多 2048，偏离实际大规模模型；训练时间仅数分钟，无法反映大规模语言模型的训练行为。
- **计算资源细节缺失**：未报告总 GPU 小时数、是否使用多卡、训练优化细节（除 Adam 学习率 0.01 外，batch size 等未说明）。

（完）
