# Credit Card Fraud Detection

## Project Description
This project focuses on detecting fraudulent credit card transactions using machine learning, with special attention to handling highly imbalanced datasets.

The dataset contains a very small proportion of fraud transactions compared to non-fraud ones.  
To address this, I implemented **balanced sampling strategies** and explored multiple classification algorithms.

### Objectives
- Accurately detect fraudulent transactions while minimizing false positives.
- Compare model performance when handling imbalanced data using different techniques.
- Explore feature behavior differences between fraud and non-fraud classes.

### Modeling Approach
1. **Data Preprocessing**
   - Preserved fraud/non-fraud ratio in train/validation splits.
   - Created balanced chunks for training:
     - Each chunk contained all fraud transactions.
     - Added an equal number of randomly sampled non-fraud transactions.

2. **Models Used**
   - **Decision Tree Classifier**:
     - Used **chunked-balance approach** and averaged the decision trees results
     - Models with several parameters were teste using **stratified k-fold cross-validation**.
   - **Balanced Random Forest**:
     - Directly handles imbalanced data by adjusting class weights.
     - Evaluated using **stratified k-fold cross-validation** and grid search.

3. **Evaluation**
   - Used metrics more suitable for imbalanced data:
     - Precision
     - Recall
     - F1 Score

---

## Key Learnings from the Card Fraud Detection Project

### 1. Handling Imbalanced Data
- Real-world datasets are often highly imbalanced - in this case, there were far more non-fraud transactions than fraud ones.
- Steps taken:
  - Maintained consistent fraud/non-fraud ratios in training and validation splits.
  - For training, processed data in balanced chunks:
    - Each chunk contained **all fraud transactions**.
    - Added an **equal number of randomly sampled non-fraud transactions**.

### 2. Feature Analysis by Class
- For classification tasks, analyze each feature separately for each class.
- Approach:
  - Plotted feature distributions for fraud vs. non-fraud.

### 3. KDE Plots and Log Transformation
- KDE/Distribution plots with high peaks can hide the tails of the distribution.
- We should apply **log transformations** to such features to:
  - Reduce peak dominance.
  - Better visualize the full distribution.

### 4. Evaluation Metrics Beyond Accuracy
- Accuracy can be misleading in imbalanced datasets:
  - Example: Predicting "non-fraud" for every transaction in a dataset with 99% non-fraud gives 99% accuracy but detects no fraud.
- Used more reliable metrics:
  - **Precision**
  - **Recall**
  - **F1 Score**
