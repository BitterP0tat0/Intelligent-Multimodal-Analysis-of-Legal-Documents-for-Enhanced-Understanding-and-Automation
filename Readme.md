# Layout-Aware / Structure-Aware Legal Document Understanding Experiments

This repository contains the experimental outputs for a lightweight legal document understanding framework focused on contract clause classification, structure-aware feature fusion, clause-absence detection, OCR-style robustness, retrieval-based clause comparison, proxy risk ranking, and external validation on selected LexGLUE tasks.

The project is organized around seven research questions (RQ1–RQ7). Each RQ produces figures and CSV tables intended for use in the proposal / journal-style manuscript.

---

## Research Questions and Main Output Files

| RQ | Main Figure 1 | Main Figure 2 | Main Table / CSV 1 | Main Table / CSV 2 |
|---|---|---|---|---|
| **RQ1** | `rq1_fig1_lexical_vs_semantic_macro_f1.png` | `rq1_fig2_clause_distribution.png` | `rq1_repeated_split_summary_journal.csv` | `rq1_repeated_split_metrics_all_models.csv` |
| **RQ2** | `rq2_fig1_multimodal_ablation_macro_f1.png` | `rq2_fig2_layout_feature_importance.png` | `rq2_ablation_summary_journal.csv` | `rq2_layout_feature_importance_repeated.csv` |
| **RQ3** | `rq3_fig1_missing_clause_ablation_f1_journal_strong.pdf` | `rq3_fig3_missing_clause_ranking_recall_at5_journal_strong.pdf` | `rq3_missing_clause_summary_journal_strong.csv` | `rq3_paired_improvement_over_textonly_missing_auroc.csv` |
| **RQ4** | `rq4_fig1_macro_f1_under_noise_by_model.png` | `rq4_fig2_degradation_rate.png` | `rq4_ocr_robustness_summary_journal.csv` | `rq4_real_cuad_with_synthetic_ocr_preview.csv` |
| **RQ5** | `rq5_fixed_fig1_leakage_controlled_recall_at_k.png` | `rq5_fixed_fig2_leakage_controlled_mrr.png` | `rq5_fixed_retrieval_summary_journal_leakage_controlled.csv` | `rq5_fixed_category_level_retrieval_diagnostics.csv` |
| **RQ6** | `rq6_fig1_proxy_risk_by_category.png` | `rq6_fig2_proxy_risk_distribution.png` | `rq6_proxy_risk_summary_by_category.csv` | `rq6_ranked_proxy_risk_clauses_journal.csv` |
| **RQ7** | `rq7_fig1_external_generalization_macro_f1.pdf` | `rq7_fig2_gain_over_majority.pdf` | `rq7_repeated_split_summary_journal_FAST.csv` | `rq7_dataset_statistics_used_FAST.csv` + `rq7_split_and_leakage_diagnostics_FAST.csv` |

---

## RQ3: Clause-Absence Detection Outputs

RQ3 was revised into a stronger journal-safe experiment. Missing clause categories are treated as the positive class, and CUAD contracts are split at contract level to avoid train/test leakage.

### Main RQ3 Figures

| Figure | File | Recommended Caption |
|---|---|---|
| **Figure 3.1** | `rq3_fig1_missing_clause_ablation_f1_journal_strong.pdf` | Leakage-Controlled Clause-Absence Detection Performance |
| **Figure 3.2** | `rq3_fig3_missing_clause_ranking_recall_at5_journal_strong.pdf` | Review-Oriented Top-5 Ranking of Missing Clause Categories |

### Main RQ3 Tables

| Table | File | Recommended Title |
|---|---|---|
| **Table 3.1** | `rq3_missing_clause_summary_journal_strong.csv` | Overall Performance of Contract-Level Clause-Absence Detection Models |
| **Table 3.2** | `rq3_paired_improvement_over_textonly_missing_auroc.csv` | Paired AUROC Improvement of Structure-Aware Models over Text-Only Baseline |

### Supplementary RQ3 CSV Files

| File | Purpose |
|---|---|
| `rq3_contract_clause_presence_matrix_real_cuad(1).csv` | Contract-by-clause-category presence matrix derived from CUAD. |
| `rq3_contract_split_leakage_diagnostics_FAST_text_layout.csv` | Contract-level split diagnostics; train/validation/test overlap should be zero. |
| `rq3_data_diagnostics_journal_strong.csv` | Dataset construction diagnostics, including number of contracts, samples, and eligible clause categories. |
| `rq3_missing_as_positive_metrics_FAST_text_layout.csv` | Per-category repeated metrics with missing treated as the positive class. |
| `rq3_missing_clause_category_summary_journal_strong.csv` | Category-level summary for clause-absence detection. |
| `rq3_missing_clause_topk_ranking_metrics_FAST_text_layout.csv` | Contract-level top-k ranking metrics for missing clause categories. |
| `rq3_missing_predictions_seed42_FAST_text_layout.csv` | Seed-42 prediction-level output for inspection and qualitative examples. |
| `rq3_paired_improvement_over_textonly_missing_f1.csv` | Paired improvement analysis over TextOnly using missing-class F1. |
| `rq3_paired_improvement_over_textonly_missing_recall.csv` | Paired improvement analysis over TextOnly using missing-class recall. |
| `rq3_topk_missing_ranking_summary_journal_strong.csv` | Aggregated top-k ranking summary. |

### RQ3 Interpretation Note

The strongest evidence for RQ3 is not missing-class recall, because the missing class is highly frequent for many clause categories. The strongest evidence is the statistically significant AUROC improvement of `TextPlusLayout` over `TextOnly`, together with zero contract overlap in the split diagnostics. The RQ3 conclusion should therefore be framed as improved clause-absence discrimination and balanced decision quality, not as universal improvement across all metrics.

---

## RQ7: External Validation Outputs

RQ7 evaluates whether the portable components of the framework retain predictive value across independent legal datasets. The experiment uses within-dataset training/testing on CUAD, LexGLUE-LEDGAR, and LexGLUE-UNFAIR-ToS. It is not a direct CUAD-to-LexGLUE transfer experiment.

### Main RQ7 Figures

| Figure | File | Recommended Caption |
|---|---|---|
| **Figure 7.1** | `rq7_fig1_external_generalization_macro_f1.pdf` | External Generalization Across Legal Datasets |
| **Figure 7.2** | `rq7_fig2_gain_over_majority.pdf` | Dataset-Normalized Predictive Gain over Majority Baseline |

### Supplementary RQ7 Figures

| Figure | File | Purpose |
|---|---|---|
| **Figure S7.1** | `rq7_fig3_generalization_gap_from_cuad.pdf` | Shows Macro-F1 gaps relative to CUAD. |
| **Figure S7.2** | `rq7_fig4_domain_shift_centroid_distance.pdf` | Shows SBERT centroid cosine-distance diagnostics between datasets. |

### Main RQ7 Tables

| Table | File | Recommended Title |
|---|---|---|
| **Table 7.1** | `rq7_repeated_split_summary_journal_FAST.csv` | Cross-Dataset Performance of Portable Legal Classification Models |
| **Table 7.2** | `rq7_dataset_statistics_used_FAST.csv` + `rq7_split_and_leakage_diagnostics_FAST.csv` | Dataset Construction and Split Diagnostics for External Validation |

### Supplementary RQ7 CSV Files

| File | Purpose |
|---|---|
| `rq7_repeated_split_metrics_all_datasets_FAST.csv` | Full per-split metrics for all evaluated datasets and models. |
| `rq7_normalized_gain_over_majority.csv` | Dataset-normalized Macro-F1 gain over the majority baseline. |
| `rq7_size_controlled_metrics_all_datasets.csv` | Metrics from the size-controlled robustness analysis. |
| `rq7_size_controlled_summary_journal.csv` | Summary of size-controlled RQ7 evaluation. |
| `rq7_dataset_statistics_raw.csv` | Raw dataset statistics before filtering. |
| `rq7_CUAD_loaded_preview(1).csv` | Loaded preview of CUAD samples used for RQ7. |
| `rq7_LexGLUE_ledgar_loaded_preview.csv` | Loaded preview of LexGLUE-LEDGAR samples. |
| `rq7_LexGLUE_unfair_tos_loaded_preview.csv` | Loaded preview of LexGLUE-UNFAIR-ToS samples. |
| `rq7_domain_shift_centroid_distances.csv` | Pairwise SBERT centroid-distance values between datasets. |
| `rq7_domain_shift_centroid_stats.csv` | Dataset-level SBERT centroid statistics. |
| `rq7_generalization_gap_from_cuad(1).csv` | Macro-F1 gap from CUAD for each model/dataset combination. |
| `rq7_model_rank_stability_spearman.csv` | Spearman rank-stability diagnostics across datasets. |
| `rq7_model_rank_stability_wide.csv` | Wide-format model rank stability table. |

### RQ7 Interpretation Note

RQ7 should be interpreted as external validity of the portable modelling pipeline. The full fusion model (`TF-IDF + SBERT + PortableStructure`) achieves the strongest Macro-F1 on CUAD, LexGLUE-LEDGAR, and LexGLUE-UNFAIR-ToS in the current FAST evaluation. However, these experiments use within-dataset training and testing, so the result should not be described as direct cross-dataset transfer from CUAD to LexGLUE. LEDGAR and UNFAIR-ToS results are based on selected label subsets rather than the full official LexGLUE benchmark setting.

---

## Recommended Proposal / Journal Table Notes

### Table 3.1 Note

Results are reported as mean ± standard deviation across repeated contract-level splits. Missing clause categories are treated as the positive class. `FrequencyPrior` represents a majority-prior baseline and is useful for exposing the effect of class imbalance. `TextPlusLayout` achieves the strongest missing-class F1, AUROC, and balanced accuracy, while `TextOnly` achieves slightly higher missing-class recall. Therefore, the RQ3 conclusion should emphasize discrimination and balanced decision quality rather than universal recall improvement.

### Table 3.2 Note

Positive values indicate improvement over the TextOnly baseline. `TextPlusLayout` achieves a statistically significant AUROC improvement over TextOnly, indicating that structural-layout features improve missing-clause discrimination. `FrequencyPrior` performs substantially worse than TextOnly in AUROC, confirming that learned models provide discriminative value beyond majority-class guessing.

### Table 7.1 Note

Results are reported as mean ± 95% confidence interval across three repeated splits. CUAD is evaluated using a contract-level split, while LexGLUE-LEDGAR and LexGLUE-UNFAIR-ToS are evaluated using stratified splits on selected label subsets. The table measures external validity of the portable modelling pipeline across independent legal datasets, not direct cross-dataset transfer from CUAD to LexGLUE.

### Table 7.2 Note

CUAD is evaluated using a contract-group split, resulting in zero train/test contract overlap across repeated splits. LexGLUE-LEDGAR and LexGLUE-UNFAIR-ToS are evaluated using stratified splits because they are used as external validation datasets rather than CUAD-style contract-level review datasets. Group-overlap values for LexGLUE should be interpreted only as diagnostic indicators, not as confirmed contract leakage.

---

## Current Notebook Files

| File | Description |
|---|---|
| `RQ3_missing_clause_detection_JOURNAL_STRONG.ipynb` | Stronger RQ3 notebook for leakage-controlled clause-absence detection. |
| `RQ3_missing_clause_detection_JOURNAL_V2.ipynb` | Earlier RQ3 notebook version. |
| `RQ7_lexglue_generalization_JOURNAL_STRONG.ipynb` | Stronger RQ7 notebook for external validation across legal datasets. |
| `RQ7_lexglue_generalization_JOURNAL_V2.ipynb` | Earlier RQ7 notebook version. |

---

## Word Proposal Output

| File | Description |
|---|---|
| `RQ7_Figures_Tables_for_Proposal.docx` | Word version containing selected RQ7 figures, tables, captions, notes, and interpretation text for the proposal. |

---

## Claim-Safety Notes for Journal Writing

- Use **structure-aware** or **portable structural features** rather than claiming full visual multimodality unless true PDF/image layout features are evaluated.
- Use **clause-absence detection** or **clause-category absence modelling** rather than claiming true legal missing-safeguard detection.
- Use **retrieval-based reference clause comparison** rather than claiming real organizational policy compliance.
- Use **proxy risk prioritization** rather than true legal risk prediction unless expert risk labels are added.
- Use **external validity across selected legal datasets** rather than direct CUAD-to-LexGLUE transfer for RQ7.

