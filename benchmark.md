---
layout: default
title: The ScEdit Benchmark
---

# The ScEdit Benchmark

**ScEdit** is a novel benchmark for evaluating Knowledge Editing (KE) in script-based scenarios. It emphasizes a model's ability to handle "How"-type questions and produce coherent, reliable guidance following targeted knowledge updates.

*Figure 2: Overview of dataset construction process via a counterfactual edit as an example.*

## Subtasks

ScEdit comprises two main subtasks:

1.  **ScEdit-CF (Counterfactual):**
    * Focuses on counterfactual knowledge, a common focus in KE, evaluating a method's ability to perform edits in script-based scenarios.
    * Built on the **CounterFact** dataset, adapting it to script-based scenarios.

2.  **ScEdit-T (Temporal):**
    * Utilizes temporal updates drawn from Wikipedia (via **WikiFactDiff**) to assess a model's adaptability to chronological updates.
    * Reflects practical scenarios in which facts evolve over time.

## Dataset Statistics

| Task        | Edit Cases | Samples for Script-Efficacy (S-Eff.) | Samples for Script-Specificity (S-Spec.) |
|-------------|------------|------------------------------------|----------------------------------------|
| ScEdit-CF   | 1830       | 7342                               | 13672                                  |
| ScEdit-T    | 1762       | 7038                               | 6597                                   |
*(Based on Table 1 from the paper)*

## Key Features

* **Focus on "How"-type Questions:** Shifts evaluation from simple factual recall to procedural understanding and generation.
* **Script-based Prompts:** Requires models to integrate updated knowledge into multi-step scripts.
* **Counterfactual and Temporal Edits:** Covers different types of knowledge updates.
* **Integration of Token and Text-Level Metrics:** Provides a comprehensive evaluation of KE techniques.
* **Real-world Relevance:** Simulates scenarios where LLMs act as agents providing procedural guidance.

## Construction Process

The ScEdit benchmark is constructed by:
1.  Starting with existing factual edit datasets (CounterFact for ScEdit-CF, WikiFactDiff for ScEdit-T).
2.  Generating "Script Questions" (How-type) using a large language model (GPT-4), designed to be significantly impacted by the factual edit.
3.  Generating corresponding "Scripts" based on *original* knowledge.
4.  Truncating these scripts at the point where the original (to-be-edited) fact appears, creating cloze-style prompts for token-level evaluation.
5.  Collecting neighbor facts for specificity evaluation, processed similarly.
6.  Applying human filtering and quality checks throughout the process.

*(More details can be found in Appendix B of the paper.)*