# Instructor Effectiveness Analysis

## Project Overview

This project analyzes instructor effectiveness using learner outcomes, student engagement, and learner feedback metrics.

The objective is to calculate an Instructor Effectiveness Score, classify instructors into Low, Medium, and High effectiveness tiers, and evaluate machine learning models that predict these tiers.

The project demonstrates data cleaning, exploratory data analysis (EDA), feature engineering, data visualization, statistical analysis, and model evaluation using Python.

## Business Problem

Educational platforms need to understand how instructors perform and identify areas where learners may need additional support.

This analysis explores how learner performance, engagement, and feedback can be combined into an effectiveness score to support data-driven decision-making.

The analysis also examines which features contribute most to the predicted effectiveness tiers and the limitations of using these metrics to evaluate instructors.

## Dataset

The dataset contains 2,000 batch-level records and 12 columns.

| Category | Features |
|---|---|
| Identifiers | Batch ID, Instructor ID, Course ID |
| Learner Outcomes | Completion Rate, Score Improvement, Average Quiz Score, Dropout Rate |
| Engagement | Average Watch Time, Assignment Submission Rate, Forum Activity Rate |
| Feedback | Average Feedback Submission, Feedback Response Rate |

The analysis aggregates batch-level data into instructor-level records for effectiveness classification.

## Tools and Technologies

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Workflow

### 1. Data Cleaning and Quality Checks

- Examined dataset structure, data types, and descriptive statistics.
- Checked for missing values and duplicate records.
- Verified unique batch identifiers.
- Investigated numerical feature distributions and potential outliers.

### 2. Exploratory Data Analysis (EDA)

- Analyzed distributions of learner outcomes, engagement, and feedback metrics.
- Examined relationships between numerical variables using correlation analysis.
- Used histograms and boxplots to understand distributions and identify potential outliers.
- Identified relationships between completion rate, dropout rate, and learner performance.

### 3. Instructor Effectiveness Score

Developed a weighted scoring methodology using three dimensions:

| Dimension | Weight |
|---|---:|
| Learner Outcomes | 50% |
| Student Engagement | 30% |
| Student Feedback | 20% |

The learner outcome score combines retention, normalized score improvement, and normalized quiz performance.

The engagement score combines watch time, assignment submission, and forum activity.

The feedback score combines normalized feedback ratings and feedback response rates.

The final score is calculated on a scale of 0 to 100.

### 4. Instructor-Level Aggregation

Aggregated batch-level effectiveness scores using instructor ID to calculate one average effectiveness score per instructor.

Used quantile-based tier assignment to classify instructors into three categories:

- Low Effectiveness
- Medium Effectiveness
- High Effectiveness

### 5. Machine Learning Classification

Evaluated two classification algorithms:

- Logistic Regression
- Random Forest Classifier

The instructor-level dataset was divided into training and testing sets using an 80:20 split with stratified sampling.

Model performance was evaluated using accuracy, Macro F1-score, confusion matrices, and classification reports.

### 6. Feature Importance

Used permutation importance to identify features that contributed most to the Logistic Regression model's predictive performance.

This helped examine the relative predictive usefulness of learner outcomes, engagement, and feedback metrics.

## Key Findings

### Exploratory Data Analysis

- The dataset contained no missing values or duplicate rows.
- Average completion rate was approximately 60.3%.
- Average dropout rate was approximately 39.5%.
- Average quiz score was approximately 77.96.
- Average feedback score was approximately 4.21 out of 5.
- Completion rate and dropout rate showed a strong negative correlation of approximately -0.95.

### Instructor Effectiveness Score

The calculated batch-level effectiveness scores had the following characteristics:

| Statistic | Value |
|---|---:|
| Mean | 64.03 |
| Median | 64.14 |
| Standard Deviation | 8.35 |
| Minimum | 31.77 |
| Maximum | 90.01 |

### Feature Importance

The most important features identified by permutation importance were:

1. Average Score Improvement
2. Average Quiz Score
3. Feedback Response Rate
4. Average Watch Time
5. Dropout Rate and Completion Rate

These results indicate that learner outcomes and retention-related metrics were particularly useful in predicting the constructed effectiveness tiers.

Feature importance represents predictive usefulness, not a causal relationship with instructor effectiveness.

## Model Comparison

### Test Set Results

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 95.83% | 91.67% |
| Macro F1-score | 0.9582 | 0.9153 |

Logistic Regression achieved higher performance on the held-out test set.

### Cross-Validation Results

Stratified 5-fold cross-validation was performed on the training data.

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Mean Accuracy | 0.8847 | 0.9063 |
| Mean Macro F1-score | 0.8804 | 0.9053 |

Random Forest achieved better average cross-validation performance and lower variability across validation folds.

Therefore, Random Forest was selected as the primary candidate model, while Logistic Regression was retained as a baseline.

## Limitations

- The dataset contains only 2,000 batch records from 120 instructors.
- Effectiveness tiers are generated using a manually defined scoring formula.
- The classification models predict these constructed tiers rather than independently measuring actual teaching quality.
- The dataset contains overlapping information between completion rate and dropout rate.
- Factors such as course difficulty, learner background, and instructor experience are not included.
- The model requires testing on new and diverse data before real-world use.

The model should be treated as a decision-support tool rather than the sole basis for instructor performance evaluation.

## Repository Structure

```text
instructor-effectiveness-analysis/
│
├── README.md
├── accredian_assignment.ipynb
├── dataset_accredian.csv
└── requirements.txt
```

## How to Run the Project

1. Clone the repository:

   ```bash
   git clone https://github.com/ankitj57020-oss/instructor-effectiveness-analysis.git
   ```

2. Navigate to the project directory:

   ```bash
   cd instructor-effectiveness-analysis
   ```

3. Install the required libraries:

   ```bash
   pip install -r requirements.txt
   ```

4. Open the notebook:

   ```bash
   jupyter notebook accredian_assignment.ipynb
   ```

5. Run the notebook cells sequentially to reproduce the analysis.

## Conclusion

This project demonstrates how data analytics and machine learning can be used to evaluate learner outcomes, engagement, and feedback in an educational setting.

The analysis highlights the importance of combining multiple performance indicators, investigating relationships between variables, and interpreting predictive results carefully.

The resulting effectiveness score and classification models can support the identification of areas for improvement, but should be supplemented with qualitative feedback and human judgment before making instructor performance decisions.
