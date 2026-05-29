---
title: Self-Supervised Interpretable End-to-End Learning via Latent Functional Modularity
title_zh: 基于潜在功能模块化的自监督可解释端到端学习
authors: "Hyunki Seong, Hyunchul Shim"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=dFEeI51O5j"
tags: ["query:ns-xai"]
score: 6.0
evidence: 通过功能模块化实现自监督可解释端到端学习
tldr: "针对端到端学习缺乏可解释性问题，本文提出MoNet，一种功能模块化网络。利用潜在引导对比损失在自监督下学习任务特定决策过程，并集成在线事后可解释性。在室内自主导航任务中，MoNet在任务特异性分析上优于基线7%至28%。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1738, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 810, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1657, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1750, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1744, \"height\": 1009, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 843, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dfeei51o5j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1755, \"height\": 1069, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-dfeei51o5j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 636, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-dfeei51o5j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 393, \"label\": \"Table\"}]"
motivation: 端到端学习通常缺乏可解释性，影响信任和调试。
method: 设计功能模块化网络MoNet，使用潜在引导对比损失实现自监督学习，并结合事后可解释方法。
result: 在视觉导航任务中提升了任务特异性分析和可解释性，性能超越基线。
conclusion: 功能模块化可有效增强端到端学习的可解释性。
---

## Abstract
We introduce MoNet, a novel functionally modular network for self-supervised and interpretable end-to-end learning. By leveraging its functional modularity with a latent-guided contrastive loss function, MoNet efficiently learns task-specific decision-making processes in latent space without requiring task-level supervision. Moreover, our method incorporates an online, post-hoc explainability approach that enhances the interpretability of end-to-end inferences without compromising sensorimotor control performance. In real-world indoor environments, MoNet demonstrates effective visual autonomous navigation, outperforming baseline models by 7% to 28% in task specificity analysis. We further explore the interpretability of our network through post-hoc analysis of perceptual saliency maps and latent decision vectors. This provides valuable insights into the incorporation of explainable artificial intelligence into robotic learning, encompassing both perceptual and behavioral perspectives. Supplementary materials are available at https://sites.google.com/view/monet-lgc.

---

## 论文详细总结（自动生成）

# 基于潜在功能模块化的自监督可解释端到端学习（MoNet）——论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：端到端传感器-运动学习（如模仿学习）在自动驾驶中虽已初步成功，但面临两大挑战：① 决策过程不透明，缺乏可解释性，影响信任与调试；② 传统方法需要任务级标注（如“直行”“左转”）才能处理多任务，限制了扩展性。
- **整体含义**：本文旨在设计一种**功能模块化**的端到端网络，使其既能自监督地学习任务相关的潜在决策（无需任务标签），又能通过事后解释方法将内部决策转化为可理解的形式（如空间显著图、概率化决策），从而增强端到端学习的可靠性、透明度和实际部署安全性。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 将端到端网络分为三个功能模块：**感知模块（P）**、**规划模块（Q）**、**控制模块（R）**，分别对应机器人系统中的感知、决策与控制。
- 利用**自监督的潜在引导对比损失（Latent-Guided Contrastive Loss，LGC）**，在不依赖任务标签的情况下，鼓励规划模块在相似感知场景下生成一致的决策，在不同场景下生成差异化的决策。
- 引入**事后解释机制**：通过平面SVM分类器将潜在决策向量解码为任务后验概率，并计算熵值作为决策不确定性度量。

### 关键技术细节
1. **网络架构**  
   - **感知模块**：接收前视图像（224×224×1）和拓扑地图（64×64×3）。图像经CNN提取特征后，经Vision Transformer编码器生成注意力矩阵与融合特征 `zp`。  
   - **规划模块**：基于Transformer，从 `zp` 提取上下文特征并输出连续潜在决策向量 `hd`（无非线性）。  
   - **控制模块**：同时接收 `zp` 和 `hd`，先经MLP提取预运动特征 `xpre`，再通过加法与 `hd` 调制，最后输出归一化转向角 δ 和油门 τ。

2. **潜在引导对比损失（LGC）**  
   - 公式：  
     - 若 `cos(zp_i, zp_j) >= κ`（κ=0.5），则 `L_LGC = 1 - cos(hd_i, hd_j)`（拉近同类决策）。  
     - 若 `cos(zp_i, zp_j) < κ`，则 `L_LGC = max(0, cos(hd_i, hd_j))`（推远异类决策）。  
   - 其中 `cos` 为余弦相似度。该损失仅反向传播至感知与规划模块，不影响控制模块。

3. **监督模仿损失**：采用L1损失，侧重于转向角的监督（油门权重λτ较小）。

4. **总损失**：`L = L_π + λ_LGC * L_LGC`（λ_LGC=5e-4）。

5. **事后解释方法**  
   - **感知解释**：对感知模块的注意力矩阵沿列平均并上采样，生成空间显著图 `S`。  
   - **行为解释**：利用训练好的多类线性SVM（one-vs-rest）将潜在决策 `hd` 映射到后验概率 `P(y=k|hd)`，并通过Platt校准得到可解释的概率分数，进一步计算熵作为决策不确定性。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **平台与环境**：1/10比例竞速车（TT-02底盘），搭载Jetson Xavier NX、Realsense D435i相机、Hokuyo UST-20LX 2D LiDAR。在室内走廊环境1（71m×16m）和环境2（88m×35m）中进行真实评估。
- **任务**：直行（ST）、直行交叉口（SI）、左转（LT）、右转（RT）、避障（CA）。训练数据包含单障碍或无障碍场景；评估时引入多障碍未见场景。
- **数据集**：2小时人类驾驶数据，共88,326对（传感器+指令），80/20训练/验证分割。
- **对比方法**：
  - **ViTNet**：仅含感知和控制模块的基线，无规划模块。
  - **MoNet-MUL**：控制模块中使用乘法调制替代加法。
  - **MoNet-Iden**：规划模块输出恒等映射（无学习）。
  - **MoNet-NoLGC**：不采用LGC损失。
  - 此外还对比了ViTNet的隐藏特征 `zp`（感知特征）和 `zc`（控制级特征）。

## 4. 资源与算力

- 论文中**未明确说明**训练所用的GPU型号、数量及训练时长。仅提到搭载Jetson Xavier NX作为机器人板载计算设备，但训练过程可能使用服务器或云资源。超参数设置包括：batch size=512，迭代650K，Adam优化器，初始学习率3e-4。未提供具体硬件信息。

## 5. 实验数量与充分性

- **主要定量实验**：
  - t-SNE可视化潜在决策聚类。
  - 表征相似性矩阵（RSM）及对角线相似性得分。
  - 学习曲线（L1损失 + 相似性得分随迭代变化）。
  - 成功率为每个任务16回合（共143个任务），统计ST、SI、LT、RT、CA的成功率。
- **消融实验**：对比MoNet、MoNet-MUL、MoNet-Iden、ViTNet（zp/zc）以及MoNet-NoLGC，覆盖了不同模块变体和损失函数影响。
- **可解释性分析**：展示实际导航中潜在决策、解码概率、熵值以及显著图可视化。
- **充分性与客观性**：
  - 实验在真实机器人上重复多次，统计成功率，具有实际意义。
  - 对比基线包含多种消融，验证了各组件贡献。
  - 局限性：仅测试室内静态环境（单一场景地图），未涉及动态物体、光照变化、户外场景，泛化性验证不足。不同方法公平比较，但任务定义（ST与SI合并）可能影响结果解读。

## 6. 论文的主要结论与发现

- MoNet在**任务特异性分析**中优于基线7%~28%（相似性得分：MoNet 1.47，ViTNet zp 1.37，ViTNet zc 1.15）。
- **成功率**：MoNet在所有任务上达到100%（ST、SI、LT、RT）和95%（CA），显著优于ViTNet（RT仅63%，CA 89%）。
- 自监督LGC损失有效防止了规划模块的“坍缩”现象，使潜在决策具有清晰的任务区分能力。
- 通过解码潜在决策为概率分数和熵，能够在线监测决策不确定性，且在任务切换时熵值升高，提供了行为层面的可解释性。

## 7. 优点：方法或实验设计上的亮点

- **无需任务标签**：LGC损失利用感知特征自监督地引导规划模块学习任务特异性，无需人类标注“直行/左转”等指令。
- **功能模块化设计**：显式分离感知、规划、控制，增强了内部表征的可访问性，便于事后解释。
- **实时可解释性**：后处理方法（SVM+校准）在不影响控制性能的前提下，在推理时提供视觉显著图和概率化决策，支持在线监控。
- **真实机器人验证**：在1/10比例平台上进行物理自主导航，证明了方法在实际硬件上的可行性。
- **对比分析全面**：既能与无规划模块的ViTNet对比，又能通过消融实验验证各设计选择（加法/乘法、恒等映射、LGC损失）的影响。

## 8. 不足与局限

- **场景限制**：实验仅在室内静态走廊环境中进行，未涉及动态物体、光照变化、户外道路等复杂条件，泛化性存疑。
- **缺失时间建模**：当前网络单帧处理，未利用时序信息（如LSTM），无法处理需要记忆的动态场景（如移动行人）。
- **解释方法依赖标签**：事后SVM需要任务标签进行训练，虽然避免在端到端网络内部引入额外监督，但标签获取仍可能成为瓶颈（如定义新任务）。
- **可解释性深度有限**：解码概率仅反映与预设任务类别的对齐，无法提供更高层次的因果解释（如“为何选择左转”）。
- **未报告算力消耗**：缺少GPU型号、训练时间等细节，不利于复现与资源评估。
- **统计量偏少**：成功率仅基于16回合（每任务），未给出方差或置信区间，统计显著性不足。

（完）
