# Capstone Report — Refresh / Content Opportunity Scoring

- **Author:** @subh-hub912
- **Lane:** Refresh / Content Opportunity Scoring
- **Repo:** https://github.com/subh-hub912/flyrank-ml-internship-starter
- **Date:** 2026-10-21

## 0. Abstract

This project asks which pages should be prioritized for refresh work to improve search discoverability. I used the anonymized FlyRank internship starter dataset (30,000 content rows) and compared a transparent baseline rule engine against supervised models on the same client-holdout split. The final model selection used Precision@50 and selected a random forest. On the observed split, Precision@50 improved from 0.240 (baseline) to 0.740 (model), showing stronger ranking quality for top-priority review candidates. The output is a ranked action queue with reason codes for editor decision support.

## 1. Problem framing

This work supports a triage decision: which existing pages should be reviewed first for refresh updates. The unit of analysis is a page-level record aggregated over the trailing 90-day window. The output is a ranked score plus action label (for example, refresh, refresh+CTR review, refresh+engagement review, monitor). Wrong calls cost limited editorial time and can miss higher-value opportunities, so ranking quality matters.

## 2. Data safety

Data source is `data/raw/content_refresh_anonymized.csv` (pseudonymized IDs, no client-identifying text). I excluded client-identifying artifacts and did not include raw URLs, domains, client names, or private queries in outputs. IDs (`content_id`, `client_id`) are used only for grouping and splitting, never as model features. Label leakage risks were controlled by excluding `trend_direction` and `trend_pct` from predictors because the decline label is derived from those fields.

## 3. Baseline

The baseline is the transparent rules score in `scripts/02_baseline_score.py`. It produces explainable reason codes and a ranked queue, making it a fair and practical benchmark. On the shared validation setup, baseline `Precision@50` is 0.240 and ROC AUC is 0.627.

## 4. Model / analysis

The model comparison in `scripts/03_train_model.py` evaluates logistic regression, decision tree, and random forest using the same feature frame and split logic. The target is a decline-risk proxy (`is_declining_label`) used for ranking refresh opportunities. Feature engineering and preprocessing are reproducible through the reference pipeline and exclude label-derived columns and IDs.

## 5. Evaluation

Validation uses a client-holdout split to test cross-client generalization. On the same split and metric, random forest achieved `Precision@50 = 0.740` versus baseline `0.240`, with ROC AUC 0.750 vs baseline 0.627. This is an observed uplift for this dataset/split and should be interpreted as directional decision-support evidence, not causal proof.

## 6. Interpretation

Top contributors in the final model include visibility and aging signals such as `days_with_impressions`, `log_impressions_90d`, `avg_position`, and `content_age_days`. The queue concentrates recommendations in actionable classes, especially refresh+CTR review and refresh-only buckets. The pattern suggests many opportunities are not low-visibility pages, but pages with visibility and weak interaction quality.

## 7. Recommendation

Action order for operations:
1. Prioritize high-confidence pages flagged for `refresh_and_review_ctr`.
2. Next, handle `refresh_and_review_engagement` where behavior metrics lag despite impressions.
3. Apply `refresh` for pages with concentrated decline risk but less CTR/engagement conflict.
4. Keep `monitor` pages in backlog until additional evidence accumulates.

These recommendations should be executed with human editorial review and tracked as decisions, not auto-published changes.

## 8. Reproducibility

From a fresh clone:
1. `pip install -r requirements.txt`
2. `python scripts/run_all.py`
3. Review `outputs/model_report.md` and generated charts in `outputs/charts/`
4. Open `work/notebooks/capstone.ipynb` and run all cells top to bottom.

Primary artifacts:
- Notebook: `work/notebooks/capstone.ipynb`
- Report: `outputs/model_report.md`
- Example queue committed in git: `outputs/refresh_queue_sample.csv`
- Deployed paper source: `docs/index.html`

## 9. Acknowledgments & data credit

Built on the FlyRank ML Internship dataset: https://flyrank.ai

---

Claims use observed/measured/directional language and avoid causal or private-data assertions.
