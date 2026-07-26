# Capstone Report — <your lane>

- **Author:** Srinithi.A
- **Lane:** SEO Content Optimisation
- **Repo:** https://github.com/Srinithi-A/SRIML
- **Date:** July 2026

https://docs.google.com/document/d/e/2PACX-1vT9mnvUjQ6c5lI1iDV1BYURK0cCeTBuqzED3UvrOROhnnxsyltO6CPPHtXGl2dsRUc7csFKkodPffJw/pub
https://github.com/Srinithi-A/SRIML/blob/main/work/notebooks/capstone.ipynb

## 1. Problem framing

This project supports the decision of identifying webpages that should be prioritised for content optimisation. The unit of analysis is an individual webpage, and the output is a ranked recommendation score indicating whether a page should be reviewed. The recommended actions include refreshing outdated content, improving click-through rate (CTR), enhancing search visibility, or monitoring pages that are already performing well.

The cost of an incorrect recommendation is that editorial effort may be spent on pages with limited optimisation potential, while genuinely valuable pages could be overlooked. Machine learning helps prioritise large numbers of webpages more consistently than manual review by analysing historical search signals and content characteristics. The recommendations are intended to support human decision-making rather than replace editorial judgement.

## 2. Data safety

The project uses the anonymised FlyRank ML Internship dataset containing historical search performance and content-related features. Only historical information available before prediction time was used.

The following fields were deliberately excluded:

- Future click-through rate (Future CTR)
- Future impressions
- Future clicks
- Label-derived fields such as `trend_direction` and `trend_pct`
- Client identifiers
- URLs
- Any personally identifiable information

Pseudonymous identifiers were only considered for grouping during validation and were never included as model features. A final review confirmed that no client-identifying information appears anywhere within the repository or generated outputs.


## 3. Baseline

Before training the Decision Tree model, a transparent rule-based baseline was developed. The baseline assigned scores using simple business rules based on historical CTR, average search position, impressions, and content age.

Pages receiving low CTR, older content, or weaker search positions were assigned higher priority scores. This baseline provided an interpretable comparison against the machine learning model using the same validation split and evaluation metrics.

The baseline represents a realistic manual prioritisation process and serves as a fair benchmark for evaluating whether the Decision Tree provides additional value.

## 4. Model / analysis

The primary model used in this project is a Decision Tree Classifier. A Decision Tree was selected because it provides interpretable decision rules while handling nonlinear relationships between features.

The historical features considered include:

- Click-through Rate (CTR)
- Average Search Position
- Search Impressions
- Content Age
- Engagement Metrics

The following information was intentionally excluded:

- Future performance metrics
- Label-derived variables
- Client identifiers
- URLs

The target variable is a proxy indicating whether a webpage represents a potential content optimisation opportunity based on historical search performance.

## 5. Evaluation

The model was evaluated using the same train-test split applied to the baseline model to ensure fair comparison. Validation was designed to reduce leakage by ensuring only historical features were available during training.

Performance was evaluated using common classification metrics including Accuracy, Precision, Recall, and F1 Score.

Compared with the rule-based baseline, the Decision Tree produced more consistent prioritisation of webpages while maintaining interpretability.

Error analysis showed that pages experiencing temporary search fluctuations or seasonal traffic changes were occasionally misclassified. These observations suggest that additional contextual information could further improve recommendation quality.

## 6. Interpretation

The Decision Tree identified historical CTR, search position, impressions, and content age as the most influential features for ranking optimisation opportunities.

Pages combining low CTR with older content generally received higher recommendation scores. Pages already receiving strong engagement were typically assigned lower priority.

One notable observation was that content age alone was insufficient for identifying optimisation opportunities. Older pages with strong user engagement often continued to perform well, demonstrating that multiple historical signals should be considered together rather than individually.

The analysis provides directional insights rather than causal conclusions.

## 7. Recommendation
The generated action playbook supports the following recommendations:

| Priority | Recommended Action | Reason |
|-----------|-------------------|--------|
| High | Refresh Content | Older content with optimisation potential |
| High | Improve CTR | Low click-through rate despite impressions |
| Medium | Improve Search Position | Moderate ranking opportunities |
| Medium | Expand Content | Thin or incomplete content |
| Low | Monitor | Stable performance |

These recommendations should always be reviewed by SEO specialists or editors before implementation.

The model provides moderate confidence for prioritisation based on historical observations. It should not be used to automate publishing decisions or predict future search rankings.

## 8. Reproducibility

The project can be reproduced by cloning the repository and running each notebook sequentially.

