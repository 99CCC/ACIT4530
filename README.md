# ACIT4530

Repository for the ACIT4530 Data Mining course project.

## Project Selection

Selected project: **Project A**.

Title: **Building a Group Recommender System with Matrix Factorization**

## Current Repository Structure

- `Main.ipynb`: Main notebook for the final integrated solution.
- `Carl/dataExploration.ipynb`: Carl's exploration and testing notebook.
- `Davyd/`: Davyd's workspace for exploration and implementation.
- `DevLog.md`: Collaboration notes and task-splitting updates.

## Project A Scope (Exact Requirement Summary)

The system is built around **pairwise preferences** (`u: i > j`) rather than only raw ratings.

Core and required methods:
- Pairwise matrix factorization (BPR or equivalent pairwise loss).
- DBSCAN clustering in learned embedding space.
- One Bayesian classifier for pairwise preference prediction.
- One kNN method for pairwise prediction / recommendation support.
- Group recommendation with fairness-aware aggregation.

Non-negotiable constraints:
- Training signal must be pairwise.
- At least one pairwise MF method must be used.
- DBSCAN, one Bayesian model, and one kNN model must each be used meaningfully.
- Evaluate both individual ranking quality and group recommendation quality.
- Include at least one fairness metric.

## Dataset

- MovieLens benchmark (`100K` recommended for speed, `1M` optional if time permits).
- Source: GroupLens Research.

## Workflow (Assignment Step Mapping)

- Step 1: Data exploration, filtering, and pairwise sample construction.
- Step 2: Pairwise MF training (BPR), tuning, and embedding export.
- Step 3: DBSCAN analysis on embedding space.
- Step 4: Bayesian + kNN pairwise predictors and baseline comparison.
- Step 5: Group recommendation with multiple aggregation rules.
- Step 6: Evaluation across pairwise, individual, group, and fairness metrics.
- Step 7: Ablation studies and discussion.

## Required Evaluation Outputs

- Pairwise prediction: accuracy/AUC (plus calibration where applicable).
- Individual ranking: Precision@k, Recall@k, NDCG@k.
- Group ranking: Precision@k, NDCG@k.
- Fairness: satisfaction variance/std, Jain's fairness index, and/or worst-member satisfaction.
- Ablations:
- MF alone vs DBSCAN-informed variants.
- MF vs Bayesian vs kNN vs hybrid.
- Fairness-aware aggregation off vs on.

## Collaboration Workflow

We are alternating task ownership and reviewing each other's step outputs before merging into `Main.ipynb`.
