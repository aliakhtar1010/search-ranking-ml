# Search Ranking & Content Refresh ML

An end-to-end machine learning project built during my **FlyRank Machine Learning Internship**, focused on identifying which existing content pages should be reviewed for refresh first.

Instead of manually reviewing thousands of pages, the project uses anonymized search, engagement, and content signals to rank pages by observed decline risk and turn model predictions into a human-reviewed content action queue.

## What I Built

The project covers the full applied ML workflow:

- explored and validated anonymized search-performance data
- defined a decline prediction problem and engineered a 22-feature model input
- built a rule-based baseline for comparison
- trained and compared Logistic Regression and Random Forest models
- evaluated ranking quality using Precision@10, Precision@20, and Precision@50
- audited features for label leakage and validated performance using a client-grouped split
- analyzed false positives, false negatives, and model coefficients
- converted model scores into ranked content actions with interpretable reason codes
- deployed the final findings as a public research paper

## Results

The final Logistic Regression model was evaluated on **6,163 pages from 7 completely unseen clients**, with zero client overlap between training and test sets.

| Metric | Result |
|---|---:|
| Precision@10 | **0.60** |
| Precision@20 | **0.75** |
| Precision@50 | **0.72** |
| Test decline base rate | **0.511** |

The final action playbook identified **818 higher-risk pages** for prioritized human review:

- **102** stale, visible pages flagged for refresh review
- **415** recent, visible pages flagged for decline investigation
- **301** lower-visibility pages flagged for strategic review

These results are used as **decision support**, not automated content decisions or evidence of causal SEO effects.

## Validation & Leakage Checks

A random row split produced **0.82 Precision@50**, while the more realistic client-grouped split produced **0.72 Precision@50**.

The grouped evaluation keeps entire clients isolated between training and testing, measuring how the model generalizes to clients it has never seen.

A deliberate leakage test also demonstrated why feature auditing matters: adding the label-related `trend_pct` feature increased Precision@50 to **1.00**. It was excluded from the final model along with label-derived fields, identifiers, and outcome-window features.

## Content Action Playbook

Model probabilities are converted into interpretable recommendation categories:

- `stale_visible_decline_risk` → review for refresh
- `recent_visible_decline_risk` → investigate decline
- `low_visibility_decline_risk` → review if strategically valuable
- `monitor` → no immediate intervention

The system intentionally keeps a human in the loop. Search demand, competition, content accuracy, intent changes, seasonality, cannibalization, and business value should be reviewed before acting on a recommendation.

## Tech

`Python` · `pandas` · `scikit-learn` · `DuckDB` · `Jupyter/Colab` · `Git` · `GitHub Pages`

## Project Structure

```text
work/notebooks/
├── w01_research_question.ipynb
├── w02_ml_task_framing.ipynb
├── w03_data_contract.ipynb
├── w04_baseline_score.ipynb
├── w05_model.ipynb
├── w06_validation_audit.ipynb
├── w07_action_playbook.ipynb
└── capstone.ipynb

docs/          deployed research paper
submission/    deployed paper URL
```

## Research Paper

The completed capstone is published as a public research paper:

**[Read the deployed research paper](https://aliakhtar1010.github.io/search-ranking-ml/)**

It documents the research question, data, methodology, validation design, results, limitations, ranked recommendations, and reproducibility details.

## About the Data

The project was built on anonymized search-performance data provided through the **FlyRank Machine Learning Internship**.

No client names, domains, private queries, credentials, or raw private exports are included in this repository.

The starter repository and data framework were provided by FlyRank. The analysis, modeling, validation, action playbook, and capstone work under `work/` document my implementation and findings.
