---
layout: default
title: Evaluation Metrics in ScEdit
---

# Evaluation Metrics in ScEdit

ScEdit employs a comprehensive set of metrics at both the token and text levels to assess Knowledge Editing (KE) performance.

## Token-Level Metrics

These metrics evaluate the model's ability to correctly predict the edited information in a cloze-format (fill-in-the-blank) setting, using script-based prompts.

* **Efficacy Success (ES):** Measures how often the model prefers the *edited target object* over the *original object* under a basic fact prompt.
    $$ \text{ES} = \mathbb{E}_i\Bigl[ \mathbb{P}_{f_\theta}\bigl(o_i \mid (s_i,r_i)\bigr) > \mathbb{P}_{f_\theta}\bigl(o_i^c \mid (s_i,r_i)\bigr) \Bigr] $$
* **Script-based Efficacy Success (S-ES):** Extends ES to script scenarios. It measures whether the model prefers the *edited target object* to the *original object* under a script-based prompt (Script Question + Truncated Script).
    $$ \text{S-ES} = \mathbb{E}_{i,k}\Bigl[ \mathbb{P}_{f_\theta}\bigl(o_i \mid\widetilde{Q_{i,k}}\bigr) > \mathbb{P}_{f_\theta}\bigl(o_i^c \mid\widetilde{Q_{i,k}}\bigr) \Bigr] $$
* **Script-based Neighborhood Success (S-NS):** (For ScEdit-CF) Measures if unrelated neighbor facts (that share the original object) remain unchanged after the edit. The model should still prefer the *original object* over the *newly edited object* in the neighborhood context.
    $$ \text{S-NS} = \mathbb{E}_{i,k}\Bigl[ \mathbb{P}_{f_\theta}\bigl(o_i^c \,\mid\,\widetilde{Q_{i,k}}^\prime\bigr) > \mathbb{P}_{f_\theta}\bigl(o_i \,\mid\,\widetilde{Q_{i,k}}^\prime\bigr) \Bigr] $$
* **Script-based Bleedover (S-BO):** (For ScEdit-T) Assesses the accuracy drop for unrelated neighbor facts (that do *not* share the original object but are semantically close) after an edit. Lower is better.
    $$ \text{S-BO} = \mathbb{E}_{i,k}\Bigl[\max\bigl( \mathbb{P}^{c}_{f_\theta}\bigl(o_j\mid\,\widetilde{Q_{i,k}}^\prime\bigr) - \mathbb{P}_{f_\theta}\bigl(o_j\mid\,\widetilde{Q_{i,k}}^\prime\bigr) ,0\bigr)\Bigr] $$

## Text-Level Metrics

These metrics assess the quality of the entire generated script when the LLM answers a "Script Question" after an edit. Evaluations are conducted using 7-point Likert scales (via automatic GPT-4 evaluation and human evaluation).

* **Executability (Exec.):** Are the script steps logical and executable? (Focuses on linguistic performance, not the edit itself).
* **Coherence (Coh.):** Is the generated script aligned with the newly updated fact?
* **Consistency (Cons.):** Does the script remain free of internal contradictions (e.g., mixing old and new facts)?
* **Completeness (Comp.):** Does the script adequately address all parts of the question with sufficient procedural detail to be followed?

*(Detailed evaluation criteria and prompts for text-level metrics are provided in Appendix C of the paper.)*