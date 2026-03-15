# Machine Learning Notes

## Topics

- Types
- Core Algorithm
- Bias-Variance Tradeoff
- Evaluation Metrics
- Cross Validation
- Regularization
- Feature Engineering
- Gradient Descent
- Overfitting Fixes
- Ensemble Models
- Model Selection
- Production Checklist
- Common Interview Questions
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Types
1. **Supervised**
    - Regression:
        - Definition: ML technique that learns from labeled data to predict continuous numerical values.
        - More: Fitting a line or curve thru data points.
        - Example: House Price / Temperature / Sales Revenue / Stock Price / Time to failure / Demand Forecasting / Credit Risk / Pricing Models / Energy Consumption / Healthcare Risk
        - Steps: Collect Training Data -> Train a Model -> Minimize Error (MSE/MAE).
        - Common Algorithm's: Linear / Ridge / Lasso / Decision Tree / Random Forest / Support Vector / Neural Network
  
    - Classification:
        - Definition: ML technique to predict a category (class label) from labelled input data.
        - More: Model learns f(X)Class
        - Types:
            - Binary (spam/not, disease/healthy) using logistic regression
            - Multiclass (multiple images) using Decision Tree / Random Forest / Support Vector Machine / Naive Bayes / Neural Network
        - Example: Predict spam email / Fraud detection / Medical diagnosis / Sentiment analysis / Document classification / Image Recognition
        - Steps: Training Data (Age, Income, Credit Score leads to approve/reject decision) -> Learn Decision Boundary (separating classes, income greater than 50k approve) -> Prediction
        - Evaluation Metrics: Accuracy / Precision / Recall / F1 Score / ROC-AUC --> leads to confusion matrix
  
2. **Unsupervised**
    - Clustering
        - Definition: Learning method that automatically groups similar data points without predefined labels
        - Example:
            - Creating clusters based on Age, Income n Spending habits (customer segmentation), Document clustering (similar articles), Image segmentation (grouping pixels with similar color), Anomaly detection (fraud)
            - In AI/LLM: vector embedding, topic discovery, document org in RAG
        - Common Algorithm's:
            - K-Means: Most commonly used, K has to be specified beforehand / Steps: Choose K cluster centers -> Assign each datapoint to nearest center -> recalc cluster centers -> Repeat until stable
            - DBSCAN: Groups dense regions / good for outlier detection / does not require K beforehand
            - Hierarchical: Builds tree like structure / 2 approaches - Agglomerative (bottom-up / start with each point as cluster and then progressively merge) and Divisive (top-down / start with one cluster and progressively split)
              
    - Dimension Reduction
      
    - Association Rules

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Core Algorithm
1. **Linear**
    - Linear Regression
        - Loss: MSE
    - Logistic Regression
        - Sigmoid Function
        - Log Loss

3. **Tree Based**
    - Decision Tree
        - Gini
        - Entropy
    - Random Forest
        - Ensemble
        - Reduces Variance
    - XGBoost
        - Gradient Boost
        - Regularized

4. **Distance Based**
    - KNN:
        - Lazy learner /
        - Sensitive to scale

5. **Margin Based**
    - Support Vector Machines:
        - Maximizes margin /
        - Kernel trick

6. **Clustering**
    - KMeans: Minimize within cluster variance / requires K
    - DBScan: Density based
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Bias Variance Tradeoff
1. Bias
    - Underfitting / Too simple
2. Variance
    - Overfitting / Too complex
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Evaluation Metrics
1. Regression
    - MAE / MSE / RMSE / R*R
      
2. Classification
    - Confusion Matrix
        - TN / TP / FP / FN
    - Metrics
        - Accuracy
        - Precision = TP/ (TP+FP)
        - Recall = TP / (TP+FN)
        - F1 score
        - ROC-AUC
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Cross Validation
1. Train/test split
2. K-fold CV
3. Stratified K-fold
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Regularization
1. L1: sparse
2. L2: shrinks weight / smooth
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Feature Engineering
1. Scaling
    - Standardization
    - Min/max
3. Encoding
    - One hot / lable
5. Handling Missing
    - Mean/Median
    - Model based
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Gradient Descent
1. Types
    - Batch
    - Stochastic
    - Mini-batch
2. Learning Rate
    - Small: slow
    - Large: diverge
      
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Overfitting Fixes
1. More data
2. Regularization
3. Drop features
4. Early stopping
5. Pruning (trees)
6. Ensembling
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Ensemble Methods
1. Bagging
    - Reduce variance
2. Boosting
    - Reduce bias
3. Stacking
    - Meta Model
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Model Selection Flow
1. Understanding problem type
2. Clean data
3. Baseline model
4. Cross validate
5. Tune hyper parms
6. Evaluate
7. Interpret
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Common Interview Questions
1. Curse of dimensionality
2. Multi-collinearity
3. Feature Importance
4. SHAP values
5. ROC vs PR curve
6. Class imbalance handling
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Production ML Checklist
1. Monitoring Drift
2. Re-training pipeline
3. Feature Store
4. Model versioning
5. Latency constraints
6. A/B Testing




