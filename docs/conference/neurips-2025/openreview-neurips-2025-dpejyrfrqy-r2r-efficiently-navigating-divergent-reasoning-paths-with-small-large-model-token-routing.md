---
title: "R2R: Efficiently Navigating Divergent Reasoning Paths with Small-Large Model Token Routing"
title_zh: R2R：通过大小模型Token路由高效导航分歧推理路径
authors: "Tianyu Fu, Yi Ge, Yichen You, Enshu Liu, Zhihang Yuan, Guohao Dai, Shengen Yan, Huazhong Yang, Yu Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DpeJYRFRQY"
tags: ["query:ns-xai"]
score: 5.0
evidence: 高效的大模型推理路径路由
tldr: 大模型推理时大部分token的推理路径一致，仅少量关键token存在分歧。本文提出R2R路由方法，仅对分叉token调用大模型，其余使用小模型，在保持推理性能的同时大幅降低开销。实验证明该方法在多种推理任务上取得效率与质量的平衡。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 235, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1349, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 648, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1424, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1350, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 682, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 690, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dpejyrfrqy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1353, \"height\": 358, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1325, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1378, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 675, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 750, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1456, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1433, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1252, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 959, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1079, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 989, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1124, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 726, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1282, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 975, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 793, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1078, \"height\": 730, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1201, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 750, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dpejyrfrqy/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1331, \"height\": 279, \"label\": \"Table\"}]"
motivation: 大模型推理开销大，小模型推理质量不足，两者在多数token上推理路径相似。
method: 设计R2R神经路由器，识别分叉token并选择性使用大模型。
result: 在多个推理基准上，R2R在接近大模型性能的同时显著降低推理成本。
conclusion: R2R是一种实用的推理加速方法，利用大小模型协作提升效率。
---

## Abstract
Large Language Models (LLMs) achieve impressive reasoning capabilities at the cost of substantial inference overhead, posing substantial deployment challenges. Although distilled Small Language Models (SLMs) significantly enhance efficiency, their performance suffers as they fail to follow LLMs' reasoning paths. Luckily, we reveal that only a small fraction of tokens genuinely diverge reasoning paths between LLMs and SLMs. Most generated tokens are either identical or exhibit neutral differences, such as minor variations in abbreviations or expressions. Leveraging this insight, we introduce **Roads to Rome (R2R)**, a neural token router that selectively utilizes LLMs only for these critical, path-divergent tokens, while leaving the majority of token generation to the SLM. We also develop an automatic data generation pipeline that identifies divergent tokens and generates token-level routing labels to train the lightweight router. We apply R2R to combine R1-1.5B and R1-32B models from the DeepSeek family, and evaluate on challenging math, coding, and QA benchmarks. With an average activated parameter size of 5.6B, R2R surpasses the average accuracy of R1-7B by 1.6×, outperforming even the R1-14B model. Compared to R1-32B, it delivers a 2.8× wall-clock speedup with comparable performance, advancing the Pareto frontier of test-time scaling efficiency.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

大语言模型（LLM）在推理任务中表现优异，但推理开销（尤其是长链思维生成）极大，导致部署成本高昂。蒸馏后的小语言模型（SLM）虽然效率高，但容易偏离LLM的推理路径，导致性能严重下降。论文观察到：LLM与SLM在生成的token中，**仅约11%的token预测不同**，其中又只有一部分是真正导致推理路径分叉的**分叉（divergent）token**，其余为中性差异（如缩写、表达方式）。基于此，论文提出一种神经路由方法R2R，旨在**仅对分叉token调用LLM进行修正，其余token由SLM生成**，从而在保持推理质量的同时大幅降低推理成本。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将token-level路由问题建模为路径跟随（path-following）策略。即：以LLM的推理路径为参考，只在SLM预测会偏离该路径时（分叉token）才切换到LLM，其余情况使用SLM。
- **关键技术细节**：
  - **数据标注流水线**：首先让LLM生成完整响应作为参考路径。然后让SLM预填充该路径，找出两者预测不同的token。对于每个不同token，分别让LLM从SLM预测和LLM预测处继续生成一个句子（sentence-level continuation），再用另一个LLM作为验证器判断该差异是否导致推理分叉（neutral vs divergent）。最终得到token级别的路由标签。
  - **神经路由器设计**：一个轻量级6层FFN（56M参数），输入为SLM的top-100 logits、token嵌入和最后一层隐藏状态。输出二分类概率，指示当前token是否分叉。
  - **路由推理方案**：在推理时，每步先由SLM生成token，路由器实时判断是否分叉。若分叉，立即用LLM修正该token，无需回滚（区别于投机解码的定期验证）。
- **算法流程**：简化描述为：对于每一步，先比较SLM和LLM的贪心预测。若相同则保留SLM；若不同，则让LLM从每个预测继续生成到句子结束，再用验证器比较两个完成句子的语义是否分叉。若不分叉，则接受SLM；否则使用LLM修正该token。

## 3. 实验设计

- **数据集**：数学推理（AIME 2024-2025）、代码任务（LiveCodeBench 2024-08至2025-01）、问答任务（GPQA-Diamond）。额外在Arena-Hard（对话）、MMLU-Redux-Philosophy上测试泛化性。
- **基准方法**：
  - **蒸馏模型**：DeepSeek-R1-Distill-Qwen系列（1.5B、7B、14B、32B）
  - **查询级路由**：RouteLLM框架的SW、MF、BERT、LLM等变体
  - **投机解码**：EAGLE2、HASS（使用R1-32B LLM）
- **评估指标**：准确率、平均激活参数量（硬件无关效率指标）、总成本（平均参数量×平均输出token数）、实际延迟（A800 GPU，SGLang框架）。

## 4. 资源与算力

- **数据标注**：使用8张A800 GPU，约2.3天生成760万个token级路由标签。
- **推理测试**：使用NVIDIA A800-80GB GPU（2张，tensor parallelism），SGLang框架。
- **路由器训练**：56M参数，训练50 epoch，early stopping，验证集选阈值。

## 5. 实验数量与充分性

- 实验覆盖三个核心基准（AIME、LiveCodeBench、GPQA），外加两个泛化基准（Arena-Hard、MMLU-Redux-Philosophy）。
- 消融实验：比较不同路由目标（仅分叉 vs 所有不同token）、不同路由器输入（完整 vs 去掉logits或token嵌入）、不同SLM-LLM组合、不同采样策略（greedy vs top-p+温度）。
- 与SOTA方法（查询级路由、投机解码）在相同设置下对比，包括延迟、吞吐量、计算量、内存访问量等。
- 实验设计较为全面，对比公平（固定生成温度、最大输出长度等）。

## 6. 论文的主要结论与发现

- R2R在5.6B平均参数量下，平均准确率超过R1-7B（1.6倍）和R1-14B（1.1倍），同时仅有12~15%的token需要调用LLM。
- 与R1-32B相比，R2R在相似准确率下实现2.8倍实际速度提升。
- 与查询级路由相比，R2R在效率-准确率Pareto前沿上显著更优。
- 路由器可泛化到不同任务、不同模型族（Qwen3系列）和不同采样策略。
- 分叉token集中在思维链的起始/结束位置以及推理步骤的转折点。

## 7. 优点

- **新颖洞察**：揭示了SLM与LLM在token预测上高度一致，仅少数token导致路径分叉，为token级路由提供依据。
- **高效数据标注**：利用sentence-level path-following策略，将全序列验证简化为局部句子验证，极大降低数据生成成本。
- **轻量路由器**：56M参数，实时判断，开销极小。
- **系统实现完整**：集成到SGLang框架，报告实际端到端延迟，而非仅理论加速。
- **泛化能力强**：在多个模型族、多任务、随机采样设置下均有效。

## 8. 不足与局限

- **采样策略覆盖有限**：主要针对greedy解码调优，虽验证了top-p+温度设置，但更广泛的随机采样场景未充分探索。
- **系统级优化仍有空间**：当前延迟分析显示路由器开销仅约6%，但LLM调用仍占65%，可进一步优化调度。
- **依赖LLM验证器质量**：数据标注中使用的验证器为Qwen2.5-72B，其性能与人类专家相当，但质量下降会降低路由效果（实验中验证器偏小则性能下降）。
- **需要预先生成LLM参考路径**：数据标注依赖LLM响应，若直接使用已有SFT数据可缓解，但自己生成仍需要额外算力。
- **未讨论agentic tasks等更复杂场景**：当前仅覆盖数学、代码、QA，对需要多步工具调用或环境交互的推理任务尚未验证。

（完）
