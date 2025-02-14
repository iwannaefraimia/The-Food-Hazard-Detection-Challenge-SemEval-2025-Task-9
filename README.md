SemEval 2025 Task 9: The Food Hazard Detection Challenge
This repository contains my assignment for the SemEval 2025 Task 9: The Food Hazard Detection Challenge. The task focuses on explainable classification systems for food recall reports collected from web sources.

Task Overview
The challenge consists of two sub-tasks:

(ST1) Hazard & Product Category Prediction: Predicts the general hazard-category and product-category.
(ST2) Hazard & Product Label Prediction: Predicts the exact hazard and product involved in the recall.
Dataset
The dataset consists of food recall reports with the following features:

Dataset
The dataset consists of food recall reports with the following features:
title and text: The recall report’s title and full text.
year, month, day, country: Metadata about the report.
product-category & hazard-category: Broad categories of the recalled products and hazards.
product & hazard: Specific products and hazards involved in the recall.
The dataset is highly imbalanced, meaning that some hazard and product categories appear much more frequently than others.

Evaluation Metrics
Performance is evaluated using Macro-F1 and Micro-F1 scores:

Macro-F1: Measures how well the model performs across all classes, regardless of frequency.
Micro-F1: Gives more weight to frequently occurring classes.
The final competition score is calculated as:

Score = (Macro-F1 for Hazard + Macro-F1 for Product)/2
Score= (Macro-F1 for Hazard+Macro-F1 for Product)/2
​
 
Since hazard classification is more important, a model that correctly predicts hazards but not products will still receive a reasonable score.

Project Structure
The repository contains different classification models implemented for this task:

📂 HistGradientBoostingClassifier
📂 K-NearestNeighbour
📂 LGBMClassifier
📂 LogRegression
📂 MultinomialNB
📂 RandomForestEncoding
📂 SVM
📂 XGBoostClassification (Main model for final submission)
📄 incidents_train.csv – Training dataset
📄 incidents_test.csv – Testing dataset
📄 incidents_valid.csv – Validation dataset
📄 submission.csv – Submission file (Generated from validation data)

Modeling Approach
Each model was trained and evaluated on the validation dataset. Only XGBoostClassification makes predictions on both validation and test data. All models generate the submission.csv file on the validation set.

Results (XGBoostClassification model)
Final F1 Scores
Task	Macro F1	Micro F1
Hazard Category	0.71	0.92
Product Category	0.49	0.61
Hazard	0.44	0.78
Product	0.17	0.33
Final Competition Scores
Sub-Task	Final Score
ST1 (Category Prediction)	0.598
ST2 (Label Prediction)	0.308

Observations
Product classification performed the worst (Macro-F1: 0.17, Micro-F1: 0.33). The model struggled with product labels, likely due to their ambiguity and high class imbalance.
Hazard classification was better (Macro-F1: 0.44, Micro-F1: 0.78), but still challenging due to unseen hazards in the test set.

Future Improvements
🔹 Fine-tuning hyperparameters for XGBoost and LGBM.
🔹 Exploring transformer-based models (e.g., BERT) for better text understanding.
🔹 Using embeddings and sentence transformers instead of TF-IDF.
🔹 Applying data augmentation to balance the dataset.




