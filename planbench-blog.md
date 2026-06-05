---
title: "PlanBench: Comprehensive Benchmarks for Evaluating Urban Planning Capabilities in LLMs"
thumbnail: https://behavioral-spatial-ai-lab.github.io/pictures/planbench_text_show.png
authors:
  - user: chichi56
date: 2026-04-15
tags:
  - benchmark
  - urban-planning
  - multimodal
  - vision-language-model
  - evaluation
---

# PlanBench: Comprehensive Benchmarks for Evaluating Urban Planning Capabilities in LLMs

*He Zhu, Yijie Deng, Wen Wang, Minxin Chen, Junyou Su, Wenjia Zhang\**

*Tongji University, Behavioral Spatial AI Lab (BSAI)*

[[PlanBench-Text](https://behavioral-spatial-ai-lab.github.io/plangpt-bench/)] [[PlanBench-VL](https://behavioral-spatial-ai-lab.github.io/planvlm-bench/)] [[PlanGPT arXiv](https://arxiv.org/abs/2402.19273)] [[PlanGPT-VL arXiv](https://arxiv.org/abs/2505.14481)] [[PlanGPT-VL Model](https://modelscope.cn/models/chichi56/plangpt-VL-10K/files)] [[Project Page](https://behavioral-spatial-ai-lab.github.io/)]

**Language / 语言:** [English](#planbench-comprehensive-benchmarks-for-evaluating-urban-planning-capabilities-in-llms) | [中文](#中文版本)

**Updates:**
- 🔥 **Apr 2026** — We open-source the PlanBench benchmark suite (code + data) on HuggingFace and GitHub.
- 🚀 **May 2025** — PlanBench-Text, PlanBench-VL, and PlanGPT-VL publicly released. PlanGPT-VL open-sourced on [ModelScope](https://modelscope.cn/models/chichi56/plangpt-VL-10K).
- 🎉 **May 2025** — PlanGPT-1.5 accepted by **ACL 2025 Industry Track (Oral)**.

## Table of Contents

- [What is PlanBench?](#what-is-planbench)
- [Why Urban Planning?](#why-urban-planning)
- [Related Work](#related-work)
- [PlanBench-Text: Planning Knowledge Benchmark](#planbench-text-planning-knowledge-benchmark)
- [PlanBench-VL: Planning Visual Recognition Benchmark](#planbench-vl-planning-visual-recognition-benchmark)
- [What We Learned](#what-we-learned)
- [The PlanGPT Series](#the-plangpt-series)
- [Citation](#citation)

## What is PlanBench?

Can large language models truly understand urban planning? We built **PlanBench** to find out — a two-part benchmark suite that rigorously evaluates LLM and MLLM capabilities in the urban planning domain:

1. **PlanBench-Text** — A text-based benchmark assessing planning knowledge across 5 cognitive levels (Bloom's taxonomy), covering 4 major categories, 24 intermediate classes, and 81 subcategories.
2. **PlanBench-VL** — A multimodal benchmark evaluating spatial planning map understanding across 4 dimensions (Perception, Reasoning, Association, Application) with 8 fine-grained subcategories.

These benchmarks are part of the broader **PlanGPT** initiative, which also includes [PlanGPT](https://arxiv.org/abs/2402.19273) (the first domain-specific LLM for urban planning, ACL 2025 Industry Oral) and [PlanGPT-VL](https://arxiv.org/abs/2505.14481) (a 7B VLM achieving 59.2% improvement over general VLMs on planning tasks).

## Why Urban Planning?

Urban planning is a highly interdisciplinary and practice-oriented field. Unlike general knowledge domains, it demands:

- **Dense domain terminology** — regulations, zoning codes, planning standards
- **Complex spatial reasoning** — multi-level governance logic spanning national, city, and community scales
- **Long reasoning chains** — from policy interpretation to site selection, land allocation, and infrastructure planning
- **Visual-textual integration** — reading planning maps requires understanding symbols, legends, geographic features, and their policy implications simultaneously

Existing benchmarks like [MMLU](https://arxiv.org/abs/2009.03300) and [MMMU](https://arxiv.org/abs/2311.16502) cover standard academic disciplines but lack depth in specialized professional domains like urban planning. We built PlanBench to fill this gap.

## Related Work

**Domain-specific benchmarks.** The need for specialized evaluation has driven benchmarks across professional fields: [MedQA](https://arxiv.org/abs/2009.13081) for medicine (board exams across multiple countries), [LegalBench](https://arxiv.org/abs/2308.11462) for law (162 reasoning tasks), and [FinBen](https://arxiv.org/abs/2402.12659) for finance (35 NLP tasks). [ScienceQA](https://arxiv.org/abs/2209.09513) introduced multimodal science QA with chain-of-thought explanations. Urban planning, despite its significant societal impact, has lacked such a dedicated benchmark.

**Geospatial AI and urban computing.** [CityBench](https://arxiv.org/abs/2406.13945) (KDD 2025) is the first systematic benchmark evaluating LLMs on urban tasks across 13 cities — it found that LLMs struggle with tasks requiring professional knowledge, directly motivating our work. [GeoLLM](https://arxiv.org/abs/2310.06213) (ICLR 2024) showed that LLMs encode rich geospatial knowledge, and [UrbanGPT](https://arxiv.org/abs/2403.00813) tackled spatio-temporal prediction. [IMAGEO-Bench](https://arxiv.org/abs/2508.01608) evaluated image geolocalization, revealing notable geospatial biases.

**Multimodal geospatial benchmarks.** [RSGPT](https://arxiv.org/abs/2307.15266) built a VLM and benchmark for remote sensing. [Geo3DVQA](https://arxiv.org/abs/2512.07276) (WACV 2026) evaluates 3D geospatial reasoning from aerial imagery with 110K QA pairs. [GeoMMBench](https://arxiv.org/abs/2604.08896) (CVPR 2026 Highlight) is the most comprehensive multimodal benchmark for geoscience and remote sensing, testing 36 models. [MapQA](https://arxiv.org/abs/2211.08545) and [ChartQA](https://arxiv.org/abs/2203.10244) addressed map and chart understanding respectively.

**Concurrent work.** [UrbanPlanBench](https://arxiv.org/abs/2504.21027) (Zheng et al., 2025) from Tsinghua University is a concurrent effort that evaluates LLMs on urban planning knowledge across three dimensions (principles, professional knowledge, regulations) and releases UrbanPlanText, a 30K-entry SFT dataset. Their work focuses on text-based knowledge assessment with a Chinese-centric exam-driven approach. Our PlanBench differs in two key aspects: (1) we adopt Bloom's Revised Taxonomy as the cognitive framework, enabling evaluation across five hierarchical reasoning levels rather than knowledge categories alone; and (2) we extend beyond text to multimodal evaluation with PlanBench-VL, the first benchmark specifically targeting professional planning map understanding — a dimension not covered by UrbanPlanBench. The two benchmarks are complementary and together provide a more complete picture of LLM capabilities in urban planning.

While these works advance geospatial AI broadly, **none specifically targets the understanding of urban spatial planning maps**. PlanBench fills this gap with both a text-based and a vision-language benchmark tailored to the urban planning profession.

## PlanBench-Text: Planning Knowledge Benchmark

### Design Methodology

We designed PlanBench-Text through a rigorous five-stage process:

1. **Syllabus Reference** — We reviewed curricula from leading planning programs (Peking University, Tongji University, MIT, Harvard GSD) and analyzed professional qualification exams from China (Registered Urban Planner), the U.S. (AICP), the UK (RTPI), Australia (PIA), and Canada (CIP).
2. **Knowledge Classification** — A three-tier taxonomy with **4 major categories**, **24 intermediate classes**, and **81 subcategories**, validated using the Content Validity Index (S-CVI = 1.0).
3. **Competency Dimensions** — Based on Bloom's Revised Taxonomy, we assess five cognitive levels:

| Level | Description |
|:------|:------------|
| **Remember** | Recalling facts, terminology, and fundamental concepts |
| **Understand** | Interpreting, paraphrasing, and explaining key information |
| **Apply** | Synthesizing and contextualizing planning scenarios |
| **Analyze** | Deconstructing text structures, identifying implicit assumptions |
| **Evaluate** | Comparing standards, assessing judgments, critiquing solutions |

4. **Reasoning Design** — Chain-of-Thought (CoT) principles systematically embedded into question design, with contextual preconditions, guided prompts, and deliberate logical fallacies.
5. **Assessment Procedure** — Expert urban planners review all items. Each question has detailed scoring rubrics, and a dual human-machine scoring system is calibrated against human-annotated benchmarks.

![PlanBench-Text Architecture](https://behavioral-spatial-ai-lab.github.io/pictures/planbench_text_show.png)

*Figure 1: PlanBench-Text architecture — a five-stage benchmark design process grounded in international planning curricula and Bloom's Revised Taxonomy.*

### Full Leaderboard (22 Models)

We evaluated 22 models across all five cognitive levels. The complete results:

**Qwen Family**

| Model | Remember | Understand | Apply | Analyze | Evaluate | **Overall** |
|:------|:---------|:-----------|:------|:--------|:---------|:------------|
| **Qwen3-32B** | 97.5 | **86.4** | **95.1** | 86.1 | 39.5 | **80.9** |
| **Qwen3-14B** | 97.5 | 77.8 | 92.6 | 86.8 | **48.1** | **80.6** |
| **QwQ-32B** | 95.1 | 85.2 | 91.4 | **91.9** | 38.3 | **80.4** |
| **Qwen3-8B** | 93.8 | 80.2 | 90.1 | 90.4 | 45.7 | **80.0** |
| Qwen3-4B | 95.1 | 72.8 | 90.1 | 89.3 | 46.9 | **78.8** |
| Qwen3-30B-A3B | 97.5 | 79.0 | 88.9 | 89.5 | 37.0 | **78.4** |
| Qwen3-1.7B | 95.1 | 79.0 | 76.5 | 85.1 | 34.6 | **74.1** |
| Qwen2.5-3B-Instruct | **98.8** | 66.7 | 92.6 | 64.0 | 29.6 | **70.3** |
| Qwen2.5-7B-Instruct | **98.8** | 70.4 | 81.5 | 65.9 | 30.9 | **69.5** |
| Qwen2-VL-7B-Instruct | 93.8 | 65.4 | 76.5 | 65.7 | 39.5 | **68.2** |
| Qwen3-0.6B | 90.1 | 55.6 | 46.9 | 74.8 | 12.3 | **55.9** |
| Qwen2.5-0.5B-Instruct | 65.4 | 21.0 | 25.9 | 69.4 | 14.8 | **39.3** |

**DeepSeek Family**

| Model | Remember | Understand | Apply | Analyze | Evaluate | **Overall** |
|:------|:---------|:-----------|:------|:--------|:---------|:------------|
| DeepSeek-R1-Distill-Llama-8B | 93.8 | 64.2 | 75.3 | 78.8 | 28.4 | **68.1** |
| DeepSeek-R1-Distill-Qwen-7B | 96.3 | 69.1 | 77.8 | 73.4 | 23.5 | **68.0** |

**LLaMA Family**

| Model | Remember | Understand | Apply | Analyze | Evaluate | **Overall** |
|:------|:---------|:-----------|:------|:--------|:---------|:------------|
| Meta-Llama-3-8B-Instruct | 95.1 | 58.0 | 72.8 | 78.8 | 48.1 | **70.6** |
| Llama-3.1-Tulu-3-8B | 60.5 | 56.8 | 30.9 | 80.8 | 16.0 | **49.0** |

**Other Open-Source LLMs**

| Model | Remember | Understand | Apply | Analyze | Evaluate | **Overall** |
|:------|:---------|:-----------|:------|:--------|:---------|:------------|
| glm-4-9b-chat | 91.4 | 72.8 | 84.0 | 79.9 | 38.3 | **73.3** |
| Gemma-2-9B-it | 96.3 | 75.3 | 90.1 | 67.3 | 33.3 | **72.5** |
| Yi-6B-Chat | 93.8 | 48.1 | 75.3 | 85.6 | 26.2 | **65.8** |
| Gemma-2-2B-it | 87.7 | 44.4 | 75.3 | 69.0 | 28.4 | **61.0** |
| chatglm3-6b | 80.2 | 37.5 | 44.4 | 58.3 | 21.0 | **48.3** |
| Gemma-7B-it | 33.3 | 6.2 | 33.3 | 70.8 | 6.2 | **30.0** |

### Key Findings

Some interesting takeaways:

- **Qwen3 family dominates** — Qwen3-32B leads with 80.9, closely followed by Qwen3-14B (80.6), QwQ-32B (80.4), and Qwen3-8B (80.0). The top 4 are all Qwen models.
- **Remember is easy, Evaluate is hard** — Most models score 90+ on factual recall, but Evaluate scores range from only 6.2 to 48.1. Higher-order critical assessment is the biggest bottleneck.
- **Size isn't everything** — Qwen3-8B (80.0) outperforms many larger models, and Qwen3-4B (78.8) beats several 7-9B competitors. Meanwhile, Qwen3-0.6B still manages 55.9.
- **Reasoning models shine on Analyze** — QwQ-32B achieves the highest Analyze score (91.9), suggesting that reasoning-optimized models have an edge on structural decomposition tasks.
- **Older architectures struggle** — Gemma-7B-it (30.0) and chatglm3-6b (48.3) show that earlier-generation models lack the domain knowledge needed for urban planning.

## PlanBench-VL: Planning Visual Recognition Benchmark

### The Challenge of Planning Maps

National spatial planning maps visualize the concepts, goals, strategies, and specific measures of spatial planning. Understanding them requires recognizing fine-grained elements (symbols, legends, geographic features), comprehending spatial relationships (topology, proximity, orientation), and integrating domain-specific policy knowledge for holistic analysis. This makes planning map understanding a uniquely challenging task for multimodal models.

### Evaluation Framework

We designed a four-dimensional evaluation framework with 8 fine-grained subcategories:

| Dimension | Subcategories | What it tests |
|:----------|:--------------|:--------------|
| **Perception** | Element Recognition, Caption | Identifying visual elements; generating detailed map descriptions |
| **Reasoning** | Classification, Spatial Relationship, Professional Reasoning | Recognizing map types; understanding spatial relations; applying domain knowledge |
| **Association** | Policy-Map Linking | Connecting maps with policies, regulations, and planning indicators |
| **Application** | Task Abstraction, Task-Oriented Summarization | Extracting key info from complex scenarios; identifying answer-relevant content |

![PlanBench-VL Architecture](https://behavioral-spatial-ai-lab.github.io/pictures/VLMbench250512.png)

*Figure 2: PlanBench-VL architecture — a four-dimensional evaluation framework (Perception, Reasoning, Association, Application) with 8 fine-grained subcategories.*

### Data: Spatial Planning Map Database (SPMD)

We constructed an expert-annotated database featuring diverse planning map types from real-world Chinese spatial planning practice, with high-quality annotations by domain specialists. Questions are derived from the **Chinese Registered Urban Planner Qualification Examination**, which significantly reduces "hallucination-style normative citations" by the models.

### Evaluated Models

We tested 10 representative multimodal LLMs spanning different model families and scales:

| Model Family | Models Evaluated |
|:-------------|:-----------------|
| **Qwen2.5-VL** | 72B-Instruct-AWQ, 32B-Instruct, 7B-Instruct, 3B-Instruct |
| **Qwen2-VL** | 72B-Instruct-AWQ, 7B-Instruct, 2B-Instruct |
| **InternVL3** | 14B, 9B, 8B |

### Key Results

- **Qwen2.5-VL-32B-Instruct** achieved the highest overall score, leading across most dimensions — notably outperforming even the larger 72B variant.
- All models performed **worst on the Application dimension** — the gap between perception and application is substantial across every model tested.
- **Association** showed the largest variance across models, suggesting that the ability to link maps with policy frameworks is a key differentiator.
- **Expert Reasoning** and **Evaluation (Application)** are the dimensions where top models scored highest, indicating that strong models can perform professional-level reasoning when given sufficient visual context.
- Even the best models struggle with tasks requiring simultaneous visual understanding and policy reasoning — there is significant room for improvement.

## What We Learned

Our evaluations reveal that even state-of-the-art models have significant room for improvement in urban planning:

- **Text understanding** is reasonably strong for factual recall but drops sharply for higher-order cognitive tasks like evaluation and critique.
- **Visual understanding** of planning maps remains challenging, especially when policy reasoning is required.
- **The application gap** — the consistent weakness across the Application dimension suggests that current MLLMs struggle to bridge the divide between visual perception and actionable planning analysis.

These findings reinforce why urban planning needs specialized benchmarks. General benchmarks miss three critical requirements: (1) highly specialized domain knowledge that varies by country, (2) multi-scale reasoning across national, regional, city, and community levels, and (3) visual-textual interdependence where planning maps encode information through domain-specific conventions that require professional training to interpret.

## The PlanGPT Series

PlanBench is part of the broader **PlanGPT** initiative — our ongoing effort to build specialized AI for urban and spatial planning:

- **[PlanGPT](https://arxiv.org/abs/2402.19273)** — The first specialized language model for urban planning, developed with the China Academy of Urban Planning and Design. Features a customized retrieval framework, industry-based fine-tuning, and advanced tool capabilities. **Accepted at ACL 2025 Industry Track (Oral).**
- **[PlanGPT-VL](https://arxiv.org/abs/2505.14481)** — The first domain-specific VLM for urban planning maps, featuring the PlanAnno-V data framework, Critical Point Thinking for hallucination reduction, and the PlanBench-V evaluation benchmark. With only 7B parameters, it achieves a 59.2% average improvement over existing VLMs and rivals 72B+ models. **Open-sourced on [ModelScope](https://modelscope.cn/models/chichi56/plangpt-VL-10K/files).**

We hope PlanBench can drive improvements in LLM/MLLM performance on real-world planning tasks, establish a standard evaluation framework for the urban planning AI community, and demonstrate the value of domain-specific fine-tuning even at small model scales. We'd love to hear from the community — come try the benchmarks and let us know what you think! 🤗

## Citation

```bibtex
@article{deng2025planbench,
  title={PlanBench: A Comprehensive Benchmark for Evaluating Urban Planning
         Capabilities in Large Language Models},
  author={Deng, Yijie and Zhu, He and Wang, Wen and Chen, Minxin
          and Su, Junyou and Zhang, Wenjia},
  year={2025},
  note={Tongji University, Behavioral Spatial AI Lab}
}
```

---

# 中文版本

# PlanBench：面向城市规划能力评测的综合基准

*He Zhu, Yijie Deng, Wen Wang, Minxin Chen, Junyou Su, Wenjia Zhang\**

*同济大学 Behavioral Spatial AI Lab (BSAI)*

[[PlanBench-Text](https://behavioral-spatial-ai-lab.github.io/plangpt-bench/)] [[PlanBench-VL](https://behavioral-spatial-ai-lab.github.io/planvlm-bench/)] [[PlanGPT arXiv](https://arxiv.org/abs/2402.19273)] [[PlanGPT-VL arXiv](https://arxiv.org/abs/2505.14481)] [[PlanGPT-VL Model](https://modelscope.cn/models/chichi56/plangpt-VL-10K/files)] [[Project Page](https://behavioral-spatial-ai-lab.github.io/)]

**更新：**

- 🔥 **2026 年 4 月**：PlanBench 基准套件的代码和正式测试数据已在 GitHub 与 Hugging Face 开放。
- 🚀 **2025 年 5 月**：PlanBench-Text、PlanBench-VL 与 PlanGPT-VL 公开发布，PlanGPT-VL 已在 [ModelScope](https://modelscope.cn/models/chichi56/plangpt-VL-10K) 开源。
- 🎉 **2025 年 5 月**：PlanGPT-1.5 被 **ACL 2025 Industry Track** 接收，并获得 Oral Presentation 机会。

## 目录

- [PlanBench 是什么？](#planbench-是什么)
- [为什么需要城市规划基准？](#为什么需要城市规划基准)
- [相关工作](#相关工作)
- [PlanBench-Text：规划知识基准](#planbench-text规划知识基准)
- [PlanBench-VL：规划图识基准](#planbench-vl规划图识基准)
- [主要发现](#主要发现)
- [PlanGPT 系列](#plangpt-系列)
- [引用](#引用)

## PlanBench 是什么？

大语言模型是否真的理解城市规划？我们构建 **PlanBench** 来回答这个问题。PlanBench 包含两个互补的评测部分，分别面向规划文本知识和规划图纸理解：

1. **PlanBench-Text**：评估模型在规划知识、政策理解、推理与价值判断方面的能力。题目覆盖 5 个认知层级、4 个一级类别、24 个中类与 81 个细分类别。
2. **PlanBench-VL**：评估多模态模型对国土空间规划图、规划符号、图例、空间关系与政策含义的理解能力，覆盖感知、推理、关联、应用 4 个维度与 8 个细分类别。

PlanBench 是 **PlanGPT** 系列的一部分。该系列还包括 [PlanGPT](https://arxiv.org/abs/2402.19273)（面向城市规划的专用大语言模型，ACL 2025 Industry Oral）和 [PlanGPT-VL](https://arxiv.org/abs/2505.14481)（面向规划地图的领域视觉语言模型）。

## 为什么需要城市规划基准？

城市规划是高度跨学科、实践导向强的专业领域。与通用知识问答不同，规划任务通常要求模型同时具备：

- **密集的专业术语理解能力**：包括法规、标准、用地分类、规划指标等。
- **复杂空间推理能力**：需要理解国家、区域、城市、社区等多层级空间治理逻辑。
- **长链条决策能力**：从政策解释到选址、用地配置、交通组织与公共服务设施规划。
- **图文融合能力**：规划图纸将政策、空间结构、符号系统和专业判断压缩到一张图中，不能只依赖通用图像识别能力。

现有通用基准如 MMLU、MMMU 覆盖了广泛学科，但对城市规划这类专业实践领域的深度不足。PlanBench 的目标是补足这一空白。

## 相关工作

专业领域评测已经在医学、法律、金融等方向快速发展，例如 MedQA、LegalBench 与 FinBen。城市与地理空间智能方向也出现了 CityBench、GeoLLM、UrbanGPT、RSGPT 等工作，推动了地理空间推理、遥感理解与城市计算评测。

不过，现有多模态地理空间基准大多聚焦遥感影像、地图问答或通用地理任务，较少直接评测 **城市规划图纸** 的专业理解能力。PlanBench 的差异在于：一方面使用 Bloom 修订版分类法系统评估规划文本知识；另一方面通过 PlanBench-VL 把评测扩展到专业规划图纸的视觉语言理解。

## PlanBench-Text：规划知识基准

### 设计方法

PlanBench-Text 的构建流程包括五个阶段：

1. **课程与考试参考**：参考北京大学、同济大学、MIT、Harvard GSD 等规划课程体系，并分析中国注册城乡规划师、AICP、RTPI、PIA、CIP 等专业考试。
2. **知识分类体系**：建立 4 个一级类别、24 个中类、81 个细分类别，并由专家进行内容效度验证。
3. **能力维度设计**：基于 Bloom 修订版分类法，评估 Remember、Understand、Apply、Analyze、Evaluate 五个认知层级。
4. **推理题目设计**：在题目中嵌入上下文条件、链式推理提示与干扰项，避免简单记忆型答题。
5. **评测流程**：由规划专家审核题目和评分细则，并结合人工与模型评分进行校准。

![PlanBench-Text Architecture](https://behavioral-spatial-ai-lab.github.io/pictures/planbench_text_show.png)

*图 1：PlanBench-Text 架构。*

### 结果概览

我们评测了 22 个开源模型。总体来看，Qwen3 系列表现最强，Qwen3-32B、Qwen3-14B、QwQ-32B 和 Qwen3-8B 位居前列。模型在 Remember 层级通常表现较好，但在 Evaluate 层级显著下降，说明高阶价值判断、方案比较与批判性评估仍是当前模型的主要瓶颈。

关键观察包括：

- **Qwen3 系列整体领先**：前四名均来自 Qwen 系列。
- **记忆容易，评价困难**：多数模型在事实回忆上分数较高，但在评价类任务中表现明显不足。
- **模型大小不是唯一因素**：Qwen3-8B 与 Qwen3-4B 能超过部分更大规模模型。
- **推理模型在分析任务上更有优势**：QwQ-32B 在 Analyze 层级表现突出。

## PlanBench-VL：规划图识基准

### 规划图理解的挑战

国土空间规划图不仅包含道路、水系、用地、设施、边界等视觉元素，还承载规划目标、政策约束和空间治理逻辑。读懂规划图需要识别图例与符号，理解空间关系，并结合规划政策进行综合判断。

### 评测框架

PlanBench-VL 从四个维度评估多模态模型：

| 维度 | 子类别 | 评测能力 |
|:--|:--|:--|
| **感知** | 元素识别、图像描述 | 识别规划图中的视觉元素并生成描述 |
| **推理** | 图纸分类、空间关系、专业推理 | 判断图纸类型、理解空间关系并应用专业知识 |
| **关联** | 政策-图纸关联 | 将图纸内容与政策、规范和规划指标连接起来 |
| **应用** | 任务抽象、任务导向总结 | 从复杂场景中抽取与任务相关的关键信息 |

![PlanBench-VL Architecture](https://behavioral-spatial-ai-lab.github.io/pictures/VLMbench250512.png)

*图 2：PlanBench-VL 架构。*

### 数据与结果

我们构建了专家标注的 Spatial Planning Map Database (SPMD)，覆盖真实规划实践中的多类规划图纸。部分问答任务参考中国注册城乡规划师考试实务题，从而降低模型“幻觉式规范引用”的比例。

实验显示，Qwen2.5-VL-32B-Instruct 在总体上表现最好，并在多个维度领先。所有模型在 Application 维度上的表现最弱，说明当前多模态模型仍难以把视觉感知转化为可操作的规划分析。

## 主要发现

PlanBench 的结果说明，即使是当前较强的开源模型，在城市规划场景中仍存在明显短板：

- 文本知识评测中，事实回忆相对容易，高阶评价和批判性判断仍然困难。
- 规划图理解不仅是视觉识别问题，还需要政策、标准和专业经验参与推理。
- 应用维度是多模态模型最薄弱的一环，模型往往难以从图纸信息进一步抽象出可用于规划决策的结论。

这些结果说明，城市规划需要专门的评测体系。通用基准很难覆盖规划领域的专业知识、多尺度空间治理逻辑，以及图文政策联动的复杂性。

## PlanGPT 系列

PlanBench 属于 **PlanGPT** 系列研究的一部分：

- **[PlanGPT](https://arxiv.org/abs/2402.19273)**：首个面向城市规划的专用大语言模型，与中国城市规划设计研究院等机构合作开发，包含定制检索框架、行业模型微调与工具能力，并被 ACL 2025 Industry Track 接收为 Oral。
- **[PlanGPT-VL](https://arxiv.org/abs/2505.14481)**：首个面向城市规划地图的领域视觉语言模型，包含 PlanAnno-V 数据框架、关键点思维机制和 PlanBench-V 评测基准。模型已在 [ModelScope](https://modelscope.cn/models/chichi56/plangpt-VL-10K/files) 开源，代码开放在 [GitHub](https://github.com/zhuchichi56/PlanGPT-VL)。

我们希望 PlanBench 能推动大模型在真实规划任务中的能力提升，为城市规划 AI 社区建立统一、可复现的评测标准，并展示领域专用模型在专业场景中的价值。

## 引用

```bibtex
@article{deng2025planbench,
  title={PlanBench: A Comprehensive Benchmark for Evaluating Urban Planning
         Capabilities in Large Language Models},
  author={Deng, Yijie and Zhu, He and Wang, Wen and Chen, Minxin
          and Su, Junyou and Zhang, Wenjia},
  year={2025},
  note={Tongji University, Behavioral Spatial AI Lab}
}
```
