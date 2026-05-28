---
title: "Reasoning Path Compression: Compressing Generation Trajectories for Efficient LLM Reasoning"
title_zh: 推理路径压缩：压缩生成轨迹实现高效LLM推理
authors: "Jiwon Song, Dongwon Jo, Yulhwa Kim, Jae-Joon Kim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=894Yo61h1P"
tags: ["query:ns-xai"]
score: 5.0
evidence: 压缩推理路径减少LLM推理内存
tldr: 该论文提出推理路径压缩（RPC），一种无需训练的方法，通过周期性选择重要KV缓存条目来压缩推理路径，从而减少长推理链的内存占用和令牌生成延迟。实验表明RPC在保持推理质量的同时显著提升吞吐量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1277, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1423, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 483, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1351, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1363, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-894yo61h1p/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1344, \"height\": 491, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 555, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1411, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1205, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1211, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1384, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1324, \"height\": 1051, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1273, \"height\": 1049, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-894yo61h1p/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1440, \"height\": 293, \"label\": \"Table\"}]"
motivation: 长推理路径导致高内存和低吞吐量，限制模型部署。
method: RPC利用选择窗口计算查询重要性得分，只保留高重要性的KV缓存条目，压缩推理轨迹。
result: 在不牺牲推理准确性的前提下，显著减少了内存使用并提高了生成速度。
conclusion: 通过KV缓存压缩可以有效缓解长推理路径的效率问题。
---

## Abstract
Recent reasoning-focused language models achieve high accuracy by generating lengthy intermediate reasoning paths before producing final answers.
While this approach is effective in solving problems that require logical thinking, long reasoning paths significantly increase memory usage and reduce throughput of token generation, limiting the practical deployment of such models.
We propose Reasoning Path Compression (RPC), a training-free method that accelerates inference by leveraging the semantic sparsity of reasoning paths.
RPC periodically compresses the KV cache by retaining cache entries that receive high importance score, which are computed using a selector window composed of recently generated queries.
Experiments show that RPC improves generation throughput of QwQ-32B by up to 1.60$\times$ compared to the inference with full KV cache, with an accuracy drop of 1.2\% on the AIME 2024 benchmark.
Our findings demonstrate that semantic sparsity in reasoning traces can be effectively exploited for compression, offering a practical path toward efficient deployment of reasoning LLMs. Our code is available at https://github.com/jiwonsong-dev/ReasoningPathCompression.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：推理型大语言模型（如 OpenAI o1、DeepSeek-R1、QwQ-32B）通过生成长推理路径（reasoning paths）来提升复杂任务的准确性，但长序列导致 KV 缓存急剧膨胀，内存占用剧增、生成吞吐量下降，严重限制了实际部署。
- **挑战**：现有 KV 缓存压缩方法（如 SnapKV、H2O、TOVA）主要针对长输入提示，不适用于推理模型生成的动态长输出；训练式压缩（如 LightThinker）在复杂推理任务上性能下降明显。
- **核心观察**：推理路径存在显著的语义稀疏性（semantic sparsity），即大量冗余、重复的推理步骤。利用这一特性，可以丢弃不重要的 KV 条目而不破坏推理连贯性。

## 2. 方法论：核心思想、关键技术细节
- **方法名称**：推理路径压缩（Reasoning Path Compression, RPC），**无需训练**，仅修改推理管道。
- **核心思路**：周期性压缩 KV 缓存，通过一个由最近生成令牌组成的“选择窗口”（selector window）计算历史令牌的重要性得分，保留得分高的条目，丢弃低分条目。
- **关键技术细节**：
  - **压缩周期（P）**：每生成 P 个新令牌触发一次压缩；首次需等待 P+R 个令牌（R 为选择窗口大小）。
  - **选择窗口（R）**：取最近生成的 R 个令牌作为查询，计算它们对历史令牌的注意力权重，并跨头、跨窗口、经局部平均池化（窗口 w=3）得到最终重要性得分。
  - **重要性公式**：  
    \[ \text{Importance}(t) = \frac{1}{2w+1}\cdot\frac{1}{R\cdot H} \sum_{i=-w}^{w} \sum_{r=1}^{R} \sum_{h=1}^{H} \text{Attn}_h^{\ell}(q_r, k_{t+i}) \]
  - **压缩流程**：第 N 次压缩时，从当前保留的 (N-1)·(P/c) 个旧令牌和 P 个新令牌中共选出 N·(P/c) 个最高重要性的条目保留，加上选择窗口内 R 个令牌始终保留。最终 KV 缓存大小保持为 N·(P/c) + R，实现线性增长而非线性爆炸。
  - **关键超参数**：压缩间隔 P（平衡精度与效率，推荐 1024 或 4096）、选择窗口大小 R（推荐 32）、压缩比 c（默认 4 倍）。

## 3. 实验设计
- **评估模型**：
  - DeepSeek-R1-Distill-Qwen-7B（7B 参数）
  - QwQ-32B（32B 参数）
- **基准数据集**：
  - **AIME 2024**（数学推理）
  - **LiveCodeBench**（编程任务）
  - **IFEval**（指令遵循）
- **对比方法**：
  - 全 KV 缓存（Full KV Cache）作为上界
  - H2O（基于 heavy-hitter 的缓存淘汰）
  - TOVA（类 RNN 的注意力门控）
  - LightThinker（训练式推理压缩）
- **评估指标**：pass@1 准确率、生成吞吐量（tokens/s）、峰值内存（GB）。
- **实现细节**：FlashAttention-2，HuggingFace Transformers，nucleus sampling（温度 0.6，top-p 0.95），QwQ-32B 额外设置 top-k=40，最大生成长度 32768 令牌。

## 4. 资源与算力
- **硬件**：
  - DeepSeek-R1-Distill-Qwen-7B：1× NVIDIA H100 SXM GPU
  - QwQ-32B：4× NVIDIA H100 SXM GPU
- **批处理大小**：吞吐/内存实验中使用 batch size = 8、16、32。
- **训练**：RPC 无需训练，因此无额外训练算力开销。

## 5. 实验数量与充分性
- **主要实验**：表 1 报告了三种基准下两个模型的 7 种方法（包括 RPC 的两个 P 值）的准确率，共约 7×3×2 = 42 个数据点（实际因 LightThinker 在 QwQ-32B 上未测试，略少）。
- **冗余分析**：图 6 展示了 RPC 后冗余率下降，使用嵌入相似度定性+定量验证。
- **效率评估**：图 7（吞吐量/内存对比），以及附录表 5、表 6 提供了不同 batch size 和生成长度的详细数据。
- **消融实验**：
  - 压缩间隔 P 的影响（图 8，从 4 到 16384）
  - 选择窗口 R 的影响（表 2，取值 1、8、32、128）
  - 注意力聚合粒度（表 4，逐层 vs. 逐头 vs. 逐组）
  - 更激进压缩比 8×（表 7）
- **充分性与公平性**：
  - 对比基线均使用相同硬件和压缩比（H2O/TOVA 按平均长度设定预算）。
  - 消融实验覆盖了关键超参数，分析合理。
  - 实验覆盖多个任务类型（数学、代码、指令），但缺少非推理任务验证（如长文本生成）和更小/更大模型验证。

## 6. 主要结论与发现
- RPC 在 4× 压缩比下，**准确率下降可控**（以 QwQ-32B 在 AIME 2024 为例，仅降 1.2%），生成吞吐量提升 **最多 1.60×**。
- 峰值内存减少 **超过 50%**，解决了 32B 模型在 32K 生成长度时的 OOM 问题。
- 冗余率定量分析（图 6）证明 RPC 有效降低了推理路径中的重复语句比例。
- 相比训练式方法（LightThinker）和传统缓存淘汰（H2O、TOVA），RPC 在复杂推理任务上显著更优。

## 7. 优点
- **无需训练**：不修改模型权重，易于集成到现有推理管道。
- **利用推理语义稀疏性**：观察新颖，量化了冗余重复，并据此设计压缩策略。
- **周期性压缩**：避免了逐步骤压缩的开销，同时通过联合评估新旧令牌实现自然淘汰。
- **选择窗口机制**：使用最近查询的注意力作为重要性信号，比全局平均或固定预算更适应动态推理过程。
- **广泛的消融与分析**：验证了 P、R、聚合方式等的影响，为实践提供指导。

## 8. 不足与局限
- **准确率仍有轻微下降**：在更高压缩比（8×）或较小 P 下，精度下降较明显（表 7）。
- **超参数调优**：P 和 R 需要根据任务和模型手动选择，缺少自适应机制。
- **实验覆盖有限**：
  - 仅在数学、代码、指令三个任务上测试，未涉及长文档生成、对话、翻译等场景。
  - 模型方面仅测试了 Qwen 系列蒸馏版和 QwQ，未验证其他架构（如 Llama、Mistral）。
- **潜在偏差风险**：选择窗口大小 R 固定为 32，可能在不同长度或注意力模式上不够鲁棒；重要性计算的局部池化窗口 w 未深入消融。
- **应用限制**：RPC 专门为“推理型 LLM”设计，非推理模型（如常规对话模型）可能不具语义稀疏性，效果未知。

（完）
