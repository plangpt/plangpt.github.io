---
title: "PlanBench and PlanBench-V"
thumbnail: https://plangpt.github.io/pictures/VLMbench250512.png
authors:
  - user: chichi56
date: 2026-06-05
tags:
  - benchmark
  - urban-planning
  - spatial-planning
  - vision-language-model
---

# PlanBench and PlanBench-V

PlanBench is the evaluation suite for the PlanGPT series. It focuses on whether language models and vision-language models can handle planning knowledge, spatial reasoning, and professional judgment in urban and spatial planning scenarios.

**Resources:** [Public Test Data](https://huggingface.co/datasets/chichi56/PlanBench) · [Code](https://github.com/zhuchichi56/PlanBench) · [PlanBench-V Paper](https://arxiv.org/abs/2606.05744) · [PlanGPT Project Page](https://plangpt.github.io/)

## What We Release

**PlanBench** evaluates planning knowledge in text. It targets professional concepts, regulations, scenario reasoning, and policy judgment rather than general knowledge recall.

**PlanBench-V** evaluates spatial planning map understanding. The benchmark is built around professional map interpretation, including fine-grained perception, spatial reasoning, policy-map association, and implementation-oriented decision making.

The public Hugging Face dataset contains the official test data only. Private construction data and internal annotation materials are not included in the public release.

## Why This Matters

Urban planning is not a standard visual question answering or general knowledge task. A model must connect planning terminology, map symbols, spatial relationships, regulations, and practical constraints. This makes planning a useful testbed for domain-specific reasoning.

For PlanBench-V, the paper introduces an expert-annotated spatial planning map benchmark. The evaluation framework covers four progressive capabilities: Perception, Reasoning, Association, and Implementation.

## Recommended Use

Use PlanBench as a fixed evaluation set for urban planning LLMs and multimodal models. The test data should be kept separate from instruction tuning, preference tuning, or synthetic data generation to avoid leakage.

For reproducible evaluation, report the model version, prompt template, decoding settings, and whether external tools or retrieval were used.

## Citation

```bibtex
@misc{planbenchv2026,
  title={PlanBench-V},
  year={2026},
  eprint={2606.05744},
  archivePrefix={arXiv}
}
```

---

# PlanBench 与 PlanBench-V

PlanBench 是 PlanGPT 系列的评测体系，关注大语言模型和视觉语言模型是否具备城市规划与国土空间规划场景中的专业知识、空间推理和方案判断能力。

**资源：** [公开测试数据](https://huggingface.co/datasets/chichi56/PlanBench) · [代码](https://github.com/zhuchichi56/PlanBench) · [PlanBench-V 论文](https://arxiv.org/abs/2606.05744) · [PlanGPT 项目页](https://plangpt.github.io/)

## 发布内容

**PlanBench** 面向规划文本知识评测，覆盖专业概念、规范条文、情境推理和政策判断，不只是通用知识问答。

**PlanBench-V** 面向空间规划图理解评测，强调规划图识读中的细粒度感知、空间推理、政策关联和实施判断。

Hugging Face 上公开的数据集只包含正式测试数据。内部构造数据、私有标注材料和训练相关中间数据不包含在公开版本中。

## 为什么需要这个评测

城市规划不是普通的视觉问答或通用知识问答。模型需要把规划术语、地图符号、空间关系、政策规范和现实约束连接起来，因此它适合作为领域推理能力的评测场景。

PlanBench-V 论文构建了专家标注的空间规划图评测基准。评测框架覆盖四类递进能力：Perception、Reasoning、Association 和 Implementation。

## 使用建议

建议将 PlanBench 作为城市规划大模型和多模态模型的固定测试集。测试数据不应混入指令微调、偏好训练或数据合成流程，避免数据泄漏。

为了保证评测可复现，建议报告模型版本、prompt 模板、解码参数，以及是否使用外部工具或检索系统。

## 引用

```bibtex
@misc{planbenchv2026,
  title={PlanBench-V},
  year={2026},
  eprint={2606.05744},
  archivePrefix={arXiv}
}
```
