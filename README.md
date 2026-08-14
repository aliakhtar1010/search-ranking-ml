# Search Ranking & Content Refresh ML

ML project I'm working on during my **FlyRank Machine Learning Internship**, focused on using search performance data to figure out which pages are worth refreshing first.

The idea is pretty simple: instead of manually going through a large amount of existing content, use signals like impressions, clicks, CTR, and search position to build a ranked refresh queue.

## What I'm working on

The project follows an end-to-end ML workflow:

* explored and validated anonymized search data
* checked features for leakage and useful signal
* built a rule-based baseline
* trained and compared ML models
* evaluated recommendations using Precision@K
* working toward an actionable content refresh system for the final capstone

## Results so far

The provided reference pipeline establishes a baseline of around **0.24 Precision@50**, while the ML approach reaches roughly **0.68–0.74 Precision@50** on the anonymized dataset.

I'm currently building on that foundation through my own analysis, modeling, validation, and capstone work.

## Tech

`Python` · `pandas` · `scikit-learn` · `DuckDB` · `Jupyter/Colab` · `Git`

## Repo

```text
work/notebooks/   my analysis, experiments, and capstone
scripts/          ML pipeline
outputs/          model results, charts, and refresh queue
docs/             dataset and project documentation
```

## Current Progress

Currently working on **model development and comparison**.

Next up: validation, the action playbook, and the final capstone.

## About the data

The project uses anonymized search-performance data provided through the FlyRank internship. No private client data is included in this repository.

The starter framework and reference pipeline were provided by FlyRank; the work in `work/` documents my analysis, experiments, and capstone development.
