### Credit Risk Threshold Documentation

Below is the precision–recall summary for different decision thresholds used in PD segmentation.

|   Threshold |   Precision |   Recall |   F1_Score | Defaults_Flagged(%)   | True_Defaults(%)   | Comment     |
|------------:|------------:|---------:|-----------:|:----------------------|:-------------------|:------------|
|        0.25 |       0.391 |    0.46  |      0.423 | 23.06%                | 19.61%             | Low risk    |
|        0.35 |       0.458 |    0.283 |      0.35  | 12.14%                | 19.61%             | Medium risk |
|        0.5  |       0.538 |    0.12  |      0.197 | 4.39%                 | 19.61%             | High risk   |

**Interpretation:**
- High risk = likely default → decline / manual review
- Medium risk = borderline → additional verification
- Low risk = likely non-default → auto-approve
