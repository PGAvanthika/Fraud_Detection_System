Fraud Detection using XGBoost & SMOTE:
This project demonstrates an end-to-end pipeline for detecting fraudulent financial transactions using machine learning, specifically XGBoost, with techniques like data cleaning, feature engineering, SMOTE for class imbalance, and hyperparameter tuning. It also includes a simulation of real-time fraud detection.

📁 Dataset
fraud_simulation_dataset.csv: The dataset simulates transaction records. If it contains no fraud cases, the script will inject 5% fake fraud entries for experimentation.

Steps:

1. Data Loading & Exploration
Loads the transaction dataset.

Checks for missing values and basic statistics.

If no fraud cases exist, injects synthetic fraud labels.

2. Data Cleaning
Fills missing numerical values with column means.

Removes extreme outliers in the amount column (above 99th percentile).

Drops irrelevant features like nameOrig and nameDest.

3. Feature Engineering
Creates a new feature balanceDiff = oldbalanceOrg - newbalanceOrig.

Encodes the transaction type using LabelEncoder.

Removes highly correlated features (correlation > 0.85) to prevent multicollinearity.

4. Train-Test Split
Splits the dataset into training and test sets using train_test_split.

5. Handling Class Imbalance
Uses SMOTE (Synthetic Minority Over-sampling Technique) on the training data to balance fraud and non-fraud transactions.

6. Model Training
Trains an XGBoost classifier, accounting for class imbalance using scale_pos_weight.

7. Model Evaluation
Prints classification metrics including ROC-AUC, confusion matrix, and detailed report.

Displays a feature importance plot using XGBoost’s built-in plotting function.

8. Hyperparameter Tuning (Optional)
Uses RandomizedSearchCV to find optimal parameters based on ROC-AUC score.

9. Real-Time Detection Simulation
Simulates real-time detection by processing a small batch of transactions one-by-one and flagging those that exceed a fraud probability threshold (default: 0.8).
