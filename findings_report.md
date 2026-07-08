# Fake News Detection — Findings Report

## What We Tested
We built a hybrid fake news detector combining four ML models (Logistic Regression, Decision Tree, Random Forest, Gradient Boosting) with an LLM fallback (Groq) for low-confidence cases, and compared it against each model alone.

## Key Findings

**1. Synthetic training data inflated accuracy.**
~11% of the original dataset was AI-generated fake news. The model scored a perfect 1.000 accuracy on that source alone — a red flag, not a good result. It was replaced with the real-world Constraint@AAAI2021 dataset.

**2. The LLM fallback initially underperformed.**
On ambiguous cases, the LLM scored 46% accuracy — below the 66% majority-class baseline. Root cause: the prompt penalized short claims/tweets for "not looking like a news article." Rewriting the prompt to judge claims on content, not format, improved accuracy to 64% — still short of baseline, but a large, explainable improvement.

**3. Thresholds were tuned on validation data, not test data**, using a grid search balancing accuracy against LLM API cost. Final thresholds: `low=0.35`, `high=0.75`.

**4. The hybrid system did not clearly outperform Random Forest alone.**

| Model | Accuracy | F1 |
|---|---|---|
| Hybrid (ML + LLM) | 0.884 | 0.895 |
| Random Forest | 0.880 | 0.897 |

The difference is within noise. Despite the added complexity (ensemble weighting, threshold tuning, LLM fallback), Random Forest alone achieves essentially the same result.

## Conclusion
The most useful outcome of this project wasn't the accuracy number — it was testing our own assumptions. The hybrid architecture's added complexity is not clearly justified by the results; Random Forest alone performs comparably, with no API dependency or added latency.
