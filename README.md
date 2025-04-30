# Predicting Credit Risk using Decision Trees on the German Credit Dataset

## Project Overview

This project focuses on building a predictive model to assess credit risk using the well-known German Credit Dataset. The primary goal is to classify individuals as either 'good' or 'bad' credit risks based on their financial and demographic attributes, helping financial institutions make more informed lending decisions and mitigate potential losses.

We employ a **Decision Tree Classifier**, a widely used and interpretable machine learning technique, to learn patterns from historical data and predict the creditworthiness of new applicants.

The project is documented step-by-step in a Quarto document, covering data loading, exploration, preprocessing, model building, and initial evaluation.

## Dataset

The project utilizes the **German Credit Dataset**, sourced from the UCI Machine Learning Repository. This dataset contains information on 1000 individuals, described by various attributes such as Age, Sex, Job, Housing, Saving Accounts, Checking Account, Credit Amount, Duration, and Purpose. The target variable is 'CreditRisk', indicating whether an individual was assessed as 'good' or 'bad' risk.

## Methodology: Decision Trees

A Decision Tree model was chosen for its interpretability and ability to handle mixed data types. The model learns a series of decision rules based on the input features to classify individuals.

The process involves:

1. **Data Loading and Initial Inspection:** Loading the dataset and understanding its structure, data types, and summary statistics.

2. **Data Preprocessing:** Handling missing values (imputing 'NA' in account statuses with a 'missing' category) and encoding categorical features (Ordinal Encoding for ordered categories like account statuses, One-Hot Encoding for nominal categories like Sex, Housing, Purpose). The target variable ('CreditRisk') was remapped to 0 and 1 for standard classification metrics.

3. **Data Splitting:** Dividing the preprocessed data into training and testing sets (80/20 split) using stratification to maintain the original class distribution.

4. **Model Building:** Instantiating and training a Decision Tree Classifier on the training data.

5. **Model Evaluation:** Assessing the initial performance of the trained model on the unseen test set using metrics such as Accuracy, Confusion Matrix, and Classification Report.

## Initial Results and Analysis

The initial baseline Decision Tree model achieved an accuracy of approximately **57.5%** on the test set.

Analysis of the Confusion Matrix and Classification Report revealed significant issues:

* A high number of **False Positives** (predicting 'Good Risk' when the actual risk was 'Bad'), which is particularly costly in a credit risk scenario.

* Low **Precision** and **Recall** for the 'Bad Risk' class, indicating the model is poor at identifying actual bad risks and is often wrong when it does predict bad risk.

This poor performance strongly suggests that the unconstrained Decision Tree model **overfitted** the training data, failing to generalize well to new data.

## Next Steps

Based on the initial analysis, the next steps to improve the model's performance and generalization ability include:

* **Hyperparameter Tuning:** Optimizing Decision Tree parameters such as `max_depth`, `min_samples_split`, `min_samples_leaf`, and `ccp_alpha` (for pruning) using techniques like GridSearchCV or RandomizedSearchCV.

* **Pruning:** Explicitly applying pruning techniques to reduce the complexity of the tree and mitigate overfitting.

* **Feature Importance Analysis:** Examining the feature importance derived from the Decision Tree to understand which features are most influential in the classification process.

* **Exploring Other Models:** Comparing the performance of the Decision Tree with other classification algorithms suitable for this dataset.

## Project Files

* `your_quarto_file.qmd`: The main Quarto document containing the full analysis, code, and narrative.

* `style.css`: Custom CSS file for styling the HTML output (e.g., text alignment, width).

* `script.html`: HTML include file containing JavaScript for interactive features (e.g., image modal for plots).

* Other potential files: dataset file (if included in the repo), any other scripts or notebooks used.

## How to Run

1. Clone this repository.

2. Ensure you have Quarto installed (`https://quarto.org/docs/get-started/`).

3. Ensure you have Python and the necessary libraries installed (pandas, numpy, scikit-learn, matplotlib, seaborn, ucimlrepo). A `requirements.txt` file could be added for easier dependency management.

4. Open a terminal or command prompt in the project directory.

5. Render the Quarto document to HTML:

   ```bash
   quarto render your_quarto_file.qmd --to html
