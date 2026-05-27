# Proposal Figures and CSV Files

This README lists only the figures and CSV files used directly in the bachelor thesis proposal.

**Proposal title:**  
Layout-Aware Multimodal Legal Document Understanding for Scanned Filings, Contracts, and Court Records

---

## Research Questions

This thesis is guided by the following research questions:

**RQ1:**  
How effectively can lexical and semantic textual representations classify expert-annotated legal clause categories in commercial contracts?

**RQ2:**  
To what extent do structural-layout cues contribute additional predictive value beyond textual representations for legal clause classification?

**RQ3:**  
Can contract-level missing-clause detection be formulated as a lightweight multimodal classification task using textual, structural, and retrieval-based representations?

**RQ4:**  
How does OCR-style textual degradation affect the performance of text-only and lightweight multimodal contract-review models?

**RQ5:**  
Can retrieval-based clause matching provide a reliable proxy for policy-aware comparison against standard clause repositories?

**RQ6:**  
Can weakly supervised risk-oriented ranking be constructed from clause absence, clause category, structural irregularities, and semantic deviation from retrieved reference clauses?

**RQ7:**  
To what extent does the proposed lightweight multimodal framework generalize from CUAD to related legal classification tasks in LexGLUE?

---

## RQ1 — Lexical and Semantic Clause Classification

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 1.1 | `rq1_fig1_lexical_vs_semantic_macro_f1.png` | Macro-F1 comparison of lexical and semantic textual representations |
| Figure 1.2 | `rq1_fig2_clause_distribution.png` | Distribution of frequent CUAD clause categories |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 1.1 | `rq1_repeated_split_summary_journal.csv` | Summary of repeated-split classification performance |
| Table 1.2 | `rq1_repeated_split_metrics_all_models.csv` | Full repeated-split metrics for all RQ1 models |

---

## RQ2 — Structural-Layout Feature Contribution

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 2.1 | `rq2_fig1_multimodal_ablation_macro_f1.png` | Comparison of text-only, semantic-only, layout-only, and fusion models |
| Figure 2.2 | `rq2_fig2_layout_feature_importance.png` | Importance of structural-layout features |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 2.1 | `rq2_ablation_summary_journal.csv` | Main ablation summary for structural-layout contribution |
| Table 2.2 | `rq2_layout_feature_importance_repeated.csv` | Layout feature importance across repeated splits |

---

## RQ3 — Contract-Level Missing-Clause Detection

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 3.1 | `rq3_fig1_missing_clause_ablation_f1.png` | Leakage-controlled clause-absence detection performance |
| Figure 3.2 | `rq3_fig2_missing_clause_categories.png` | Review-oriented ranking of missing clause categories |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 3.1 | `rq3_missing_clause_summary_journal.csv` | Overall performance of contract-level clause-absence detection models |
| Table 3.2 | `rq3_missing_clause_metrics_by_category_repeated.csv` | Category-level or paired diagnostic metrics for missing-clause detection |

---

## RQ4 — OCR-Style Robustness

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 4.1 | `rq4_fig1_macro_f1_under_noise_by_model.png` | Macro-F1 under increasing OCR-style noise |
| Figure 4.2 | `rq4_fig2_noise_degradation_by_model.png` | Performance degradation compared with clean text |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 4.1 | `rq4_noise_robustness_summary_journal.csv` | Main OCR robustness summary |
| Table 4.2 | `rq4_noise_robustness_metrics_all_models.csv` | Detailed OCR robustness metrics and examples |

---

## RQ5 — Retrieval-Based Proxy Policy Matching

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 5.1 | `rq5_fig1_retrieval_recall_at_k.pdf` | Leakage-controlled Recall@k for BM25 and SBERT retrieval |
| Figure 5.2 | `rq5_fig2_retrieval_mrr_at_k.pdf` | MRR comparison for BM25 and SBERT retrieval |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 5.1 | `rq5_fixed_retrieval_summary_journal_leakage_controlled.csv` | Leakage-controlled retrieval performance summary |
| Table 5.2 | `rq5_fixed_category_level_retrieval_diagnostics.csv` | Category-level Recall@5 and MRR@5 diagnostics |

---

## RQ6 — Weakly Supervised Risk-Oriented Ranking

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 6.1 | `rq6_fig1_proxy_risk_by_category.pdf` | Clause categories with the highest average proxy review-priority score |
| Figure 6.2 | `rq6_fig2_proxy_risk_distribution.pdf` | Distribution of proxy review-priority scores |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 6.1 | `rq6_proxy_risk_summary_by_category.csv` | Category-level summary of proxy review-priority scores |
| Table 6.2 | `rq6_ranked_proxy_risk_clauses_journal.csv` | Representative clause-level proxy review-priority ranking results |

---

## RQ7 — Cross-Dataset Generalization

### Figures

| Proposal Figure | File Name | Description |
|---|---|---|
| Figure 7.1 | `rq7_fig1_external_generalization_macro_f1.pdf` | Macro-F1 comparison across CUAD, LEDGAR, and UNFAIR-ToS |
| Figure 7.2 | `rq7_fig2_dataset_normalized_gain_over_majority.pdf` | Dataset-normalized gain over the majority baseline |

### CSV / Tables

| Proposal Table | CSV File | Description |
|---|---|---|
| Table 7.1 | `rq7_repeated_split_summary_journal_FAST(1).csv` | Main repeated-split cross-dataset performance summary |
| Table 7.2 | `rq7_split_and_leakage_diagnostics_FAST(1).csv` | Dataset construction, split, label, and leakage diagnostics |

---

# Complete Proposal File List

## Figures Used in the Proposal

```text
rq1_fig1_lexical_vs_semantic_macro_f1.png
rq1_fig2_clause_distribution.png

rq2_fig1_multimodal_ablation_macro_f1.png
rq2_fig2_layout_feature_importance.png

rq3_fig1_missing_clause_ablation_f1.png
rq3_fig2_missing_clause_categories.png

rq4_fig1_macro_f1_under_noise_by_model.png
rq4_fig2_noise_degradation_by_model.png

rq5_fig1_retrieval_recall_at_k.pdf
rq5_fig2_retrieval_mrr_at_k.pdf

rq6_fig1_proxy_risk_by_category.pdf
rq6_fig2_proxy_risk_distribution.pdf

rq7_fig1_external_generalization_macro_f1.pdf
rq7_fig2_dataset_normalized_gain_over_majority.pdf