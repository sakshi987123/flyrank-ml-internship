Capstone Report — Refresh / Content Opportunity Scoring
Author: Sakshi Tambe
Lane: Refresh / Content Opportunity Scoring
Repo: https://github.com/sakshi987123/flyrank-ml-internship
Date: August 2026
0. Abstract
This project investigates whether machine learning can identify website content that should be prioritized for SEO optimization using historical Google Search Console (GSC) and Google Analytics (GA4) data. The FlyRank ML Internship Warehouse dataset was used to build a rule-based baseline and compare multiple machine learning models. Logistic Regression, Decision Tree, and Random Forest were trained using historical search performance and engagement metrics while following validation and leakage checks. Random Forest achieved the strongest observed performance on the evaluation dataset and was selected for generating ranked recommendations. The resulting action playbook is intended to support SEO analysts in prioritizing content optimization while maintaining honest, public-safe, and decision-support reporting.

1. Problem Framing
This project supports the decision of identifying which website pages should be prioritized for SEO optimization.

Unit of Analysis: One row represents one content page.

Output: A ranked action score with recommendation reason codes.

Human Action: SEO analysts review the highest-ranked pages and decide whether page titles, meta descriptions, or content should be improved.

Cost of a Wrong Decision: Incorrect recommendations may waste optimization effort or delay improvements on pages with greater business impact.

Machine learning helps prioritize pages using historical search and engagement data instead of relying only on manual review.

2. Data Safety
This project uses the FlyRank ML Internship Warehouse dataset containing anonymized Google Search Console (GSC) and Google Analytics (GA4) metrics.

Features Used
GSC Impressions
GSC Clicks
Click-Through Rate (CTR)
Average Search Position
GA4 Page Views
GA4 Sessions
GA4 Engaged Sessions
Deliberately Excluded
Client names
Website URLs
Search queries
Private identifiers
Pseudonymous client IDs as model features
Label-derived fields such as trend_direction and trend_pct
Client identifiers were used only for grouping during validation and never as predictive features.

No client-identifying information appears anywhere in the repository.

Potential leakage from label-derived fields was reviewed before model training.

3. Baseline
A transparent rule-based baseline was created before developing machine learning models.

Pages with high search impressions and low click-through rate received the highest optimization score.

This baseline provides an interpretable reference for comparing machine learning models using the same evaluation dataset and metrics.

The machine learning models were compared directly against this baseline to measure improvement in prioritizing SEO opportunities.

4. Model / Analysis
Three supervised learning algorithms were evaluated.

Logistic Regression
Decision Tree
Random Forest
Features
gsc_impressions
gsc_clicks
ctr
gsc_avg_position
ga4_pageviews
ga4_sessions
ga4_engaged_sessions
Features Excluded
Client IDs
Website URLs
Search queries
Label-derived fields
Future information
Target
Pages with high impressions and low CTR were labeled as requiring SEO optimization.

Random Forest was selected as the final model because it achieved the strongest observed performance while providing interpretable feature importance scores.

5. Evaluation
The models were evaluated using a train-test split. Grouped validation was also considered to reduce information sharing between clients and improve the honesty of evaluation.

Evaluation Metrics
Accuracy
Precision
Recall
F1 Score
The machine learning models were evaluated on the same dataset used for the rule-based baseline.

Random Forest achieved the strongest observed performance.

Error Analysis
Most prediction errors occurred for pages with performance metrics close to the decision threshold. These borderline cases require human review before optimization decisions are made.

The model should therefore be used as decision support rather than as a fully automated system.

6. Interpretation
Feature importance analysis showed that Google Search Console impressions, click-through rate, and clicks contributed most strongly to model predictions.

The analysis suggests that pages receiving many impressions but relatively few clicks represent valuable SEO optimization opportunities.

Historical engagement metrics also contributed to prioritization, although they were generally less influential than search performance metrics.

The project found no evidence that client identity should be used as a predictive feature.

7. Recommendation
The ranked action playbook prioritizes pages requiring SEO optimization.

Recommended actions include:

Improve page titles
Improve meta descriptions
Improve content quality
Improve user engagement
Continue monitoring lower-priority pages
A FlyRank editor can use this ranked queue to identify high-impact pages for manual review before publishing changes.

Confidence
Moderate to High for pages with strong historical performance signals.

Limitations
Recommendations are based on historical data and should always be reviewed by SEO specialists before implementation.

8. Reproducibility
Repository:

https://github.com/sakshi987123/flyrank-ml-internship

Key notebooks:

work/notebooks/w03_data_contract.ipynb
work/notebooks/w04_baseline_score.ipynb
work/notebooks/w05_model.ipynb
work/notebooks/w06_validation_audit.ipynb
work/notebooks/w07_action_playbook.ipynb
work/notebooks/capstone.ipynb
Environment:

pip install -r requirements.txt
Random Seed:

42
The notebooks can be executed sequentially to reproduce the complete workflow.

All model evaluation results were generated from the executed notebooks committed to the repository.

9. Acknowledgments & Data Credit
Built on the FlyRank ML Internship dataset.

Data Credit:

https://flyrank.ai

This project was completed as part of the FlyRank Machine Learning Internship using anonymized search analytics data provided for educational and research purposes.

