# Project A To-Do (Exact Assignment Mapping)

## Non-Negotiable Constraints (Must-Have)

- [ ] Training signal is pairwise preferences: for user `u`, item `i > j`.
- [ ] At least one pairwise matrix factorization method is implemented (BPR or equivalent pairwise logistic loss).
- [ ] DBSCAN is used meaningfully (not only mentioned).
- [ ] One Bayesian classifier is used meaningfully (Naive Bayes or Bayesian logistic regression).
- [ ] One kNN method is used meaningfully.
- [ ] Evaluate both individual ranking quality and group recommendation quality.
- [ ] Include at least one fairness metric in group evaluation.

## Step 1: Data Exploration and Pairwise Construction

- [ ] Use MovieLens dataset (`100K` recommended, `1M` optional).
- [ ] Inspect ratings/movies/users tables and relevant metadata.
- [ ] Filter extremely sparse users/items.
- [ ] Decide tie/near-tie handling (drop, uncertain, or equivalent rule).
- [ ] Create train/validation/test split (temporal split or user-based split).
- [ ] Generate pairwise samples `(u, i, j)` from each user's rated items.
- [ ] Control pair explosion with sampling strategy (including hard negatives if used).
- [ ] Document: minimum ratings threshold, pair-sampling policy, tie handling, split strategy.

## Step 2: Pairwise Matrix Factorization (BPR)

- [ ] Train BPR (or equivalent pairwise MF) model.
- [ ] Tune/report latent dimension, regularization, learning rate, and negative sampling scheme.
- [ ] Use early stopping based on validation pairwise metric (AUC and/or NDCG@k).
- [ ] Export user embeddings `p_u` and item embeddings `q_i` for downstream tasks.
- [ ] Add sensitivity/ablation for hyperparameters and pair sampling.

## Step 3: DBSCAN in Embedding Space

- [ ] Choose clustering target: users (`p_u`), items (`q_i`), or joint space.
- [ ] Normalize/standardize embeddings before clustering.
- [ ] Choose distance metric (Euclidean or cosine) and justify it.
- [ ] Tune `eps` and `min_samples` (k-distance plot and/or downstream validation).
- [ ] Interpret cluster structure and DBSCAN noise points.
- [ ] Compare usefulness of user clustering vs item clustering for group recommendation.

## Step 4: Classical Pairwise Predictors (Bayesian + kNN)

- [ ] Build pairwise features from embeddings (for example: `p_u`, `q_i`, `q_j`, `q_i - q_j`).
- [ ] Train one Bayesian model (Naive Bayes or Bayesian logistic regression).
- [ ] Train one kNN model (user/item/pairwise feature space).
- [ ] Compare both against MF pairwise score baseline: `p_u · q_i - p_u · q_j`.
- [ ] Evaluate pairwise prediction metrics (accuracy/AUC).
- [ ] Evaluate calibration for probabilistic models (Brier score and/or log loss).
- [ ] Analyze when Bayesian or kNN outperforms MF.

## Step 5: Group Recommendation and Aggregation

- [ ] Generate groups of size `3-5` (or `3-8`).
- [ ] Build homogeneous groups (same cluster) and diverse groups (across clusters).
- [ ] Produce top-`k` group recommendations using:
- [ ] `average` aggregation.
- [ ] `least misery` aggregation.
- [ ] one fairness-aware aggregation/re-ranking method.
- [ ] Compare score sources: MF, Bayesian probabilities, kNN scores, and hybrid strategy.
- [ ] Add DBSCAN-aware fairness safeguard so cluster minorities are not ignored.

## Step 6: Evaluation (Individual + Group + Fairness)

- [ ] Pairwise prediction metrics on held-out comparisons: accuracy and/or AUC.
- [ ] Individual ranking metrics: Precision@k, Recall@k, NDCG@k.
- [ ] Group ranking metrics: Precision@k, NDCG@k using group relevance from member preferences.
- [ ] Fairness metrics (at least one, ideally multiple):
- [ ] satisfaction variance/standard deviation,
- [ ] Jain's fairness index,
- [ ] worst-member satisfaction.
- [ ] Optional but encouraged: coverage/diversity metrics (catalog coverage, novelty, intra-list diversity).
- [ ] Define user satisfaction function clearly for group lists.
- [ ] Show at least one case where best group NDCG does not equal best fairness.

## Step 7: Analysis and Ablations

- [ ] Ablation 1: MF alone vs MF + DBSCAN restrictions vs MF + DBSCAN group formation.
- [ ] Ablation 2: MF vs Bayesian vs kNN vs hybrid.
- [ ] Ablation 3: fairness-aware aggregation off vs on, with minority-taste impact.
- [ ] Summarize where gains come from (accuracy, fairness, coverage trade-offs).

## Report and Grading Alignment Checklist

- [ ] Data handling quality documented (10%).
- [ ] Pairwise MF implementation + hyperparameter justification documented (20%).
- [ ] Group aggregation + fairness definition and analysis documented (30%).
- [ ] Experiment design and results clarity (accuracy/fairness/coverage) documented (30%).
- [ ] Final report structure, readability, and conclusions polished (10%).

## Repo Execution Checklist

- [ ] `Main.ipynb` runs top-to-bottom without errors.
- [ ] `DevLog.md` updated with who did what and when.
- [ ] Final tables/plots are readable and labeled.
- [ ] Final write-up includes methods, metrics, ablations, and conclusion.
