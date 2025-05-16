---
layout: default
title: Key Results and Findings
---

# Key Results and Findings

Experiments conducted on the ScEdit benchmark reveal important insights into the capabilities and limitations of current Knowledge Editing (KE) methods in script-based scenarios.

## Main Observations

1.  **Performance Drop on Script-Based Metrics:**
    * All comparable KE methods show a significant drop (average 27%) in the token-level Script-based Efficacy Success (S-ES) metric compared to similar paraphrase success (PS) metrics on simpler fact-based tasks. This indicates that script-based editing is more challenging.

2.  **Challenges in Balancing Efficacy and Locality:**
    * Some methods (e.g., Fine-Tuning) excel in S-ES but perform poorly on specificity metrics (S-NS, S-BO), indicating they struggle to contain the edit's impact.
    * Conversely, methods that preserve locality may not be as effective in making the desired edit propagate through the script.

3.  **Text-Level Performance Gaps:**
    * Even methods that perform well on token-level metrics show considerable room for improvement in text-level evaluations (Coherence, Consistency, Executability, Completeness).
    * For instance, while ROME and PROMPT show relatively good Coherence in text-level evaluations, scores are still far from perfect. Methods like Fine-Tuning can severely degrade text generation quality despite high token-level efficacy.

*Figure 3: Results of text-level metrics. For clarity, the vertical axes for ``Exec.'' and ``Cons.'' begin at 6, while those for others start at 2.*

4.  **Correlation Analysis Insights:**
    * Fact-based efficacy (ES) alone is insufficient to capture editing effectiveness in script scenarios.
    * Text-level metrics like Coherence and Consistency capture unique dimensions of editing quality not fully represented by token-level metrics.
    * Combining script-inherent features (Executability, Completeness) complements traditional specificity and generative ability measures.

*Figure 4: Clustered Spearman correlation heatmap of token-level and text-level metrics.*

## Conclusion from ScEdit

The ScEdit benchmark highlights that script-based knowledge editing is a challenging task. Current KE methods, while often successful in simpler settings, face difficulties in ensuring that edited knowledge is correctly applied and generalized within more complex, procedural ("How"-type) query contexts. This underscores the need for further research into KE techniques specifically designed for such real-world application scenarios.

*(Refer to Sections 4 and 5 of the paper for detailed experimental results and discussion.)*