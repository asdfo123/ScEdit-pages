---
layout: default # This assumes you are using a Jekyll theme
title: ScEdit - Script-based Assessment of Knowledge Editing
---

# <img src="assets/img/script-1-2.png" alt="ScEdit Logo" width="45" style="vertical-align: middle; margin-right: 10px;"> ScEdit: Script-based Assessment of Knowledge Editing

**ScEdit** is a novel script-based benchmark designed to evaluate Knowledge Editing (KE) techniques in Large Language Models (LLMs). It assesses the model's ability to handle "How"-type questions and generate coherent, goal-oriented scripts after knowledge updates.

**[Read the Paper](#paper-and-citation) | [View on GitHub](#code-and-data)**

---

## Abstract

Knowledge Editing (KE) has gained increasing attention, yet current KE tasks remain relatively simple. Under current evaluation frameworks, many editing methods achieve exceptionally high scores, sometimes nearing perfection. However, few studies integrate KE into real-world application scenarios (e.g., recent interest in LLM-as-agent). To support our analysis, we introduce a novel script-based benchmark -- **ScEdit** (Script-based Knowledge Editing Benchmark) -- which encompasses both counterfactual and temporal edits. We integrate token-level and text-level evaluation methods, comprehensively analyzing existing KE techniques. The benchmark extends traditional fact-based (``What''-type question) evaluation to action-based (``How''-type question) evaluation. We observe that all KE methods exhibit a drop in performance on established metrics and face challenges on text-level metrics, indicating a challenging task. Our benchmark is available at [https://github.com/asdfo123/ScEdit](https://github.com/asdfo123/ScEdit).

---

## Overview

Large Language Models (LLMs) can produce outdated or erroneous information. Knowledge Editing (KE) aims to efficiently update LLMs without the need for full retraining. However, existing KE evaluations often focus on simple fact recall ("What"-type questions) and do not adequately address real-world scenarios where users pose "How"-type questions that require procedural, multi-step responses (scripts).

ScEdit addresses this gap by:
* **Introducing a script-based evaluation framework:** This framework assesses whether models can integrate updated facts into complex reasoning and script generation tasks.
* **Focusing on "How"-type questions:** Shifting the evaluation from factual recall to action-oriented guidance.
* **Providing the ScEdit benchmark:** This benchmark includes both counterfactual and temporal edits, with comprehensive token-level and text-level evaluations.

*Figure 1: Overview of ScEdit. For token-level evaluation, we concatenate the Script Question and Truncated Script to form a cloze-format prompt. For text-level evaluation, we involve automatic and human evaluation.*

---

## Key Contributions

* **Develop a script-based assessment framework:** This framework leverages scripts—structured procedural knowledge—to capture a model’s ability to integrate updated facts into complex reasoning and generation tasks. To the best of our knowledge, this is the first attempt to integrate KE into script-based scenarios, presenting a more challenging task compared to existing KE and constrained script generation tasks.
* **Introduce ScEdit, a novel and challenging script-focused benchmark:** This benchmark is accompanied by comprehensive experiments to evaluate models' ability at both token and text levels.