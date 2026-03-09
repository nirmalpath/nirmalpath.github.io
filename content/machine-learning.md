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

### Types
1. Supervised
- Regression:
-   Definition: ML technique that learns from labeled data to predict continuous numerical values.
-   More: Fitting a line or curve thru data points.
-   Example: House Price / Temperature / Sales Revenue / Stock Price / Time to failure / Demand Forecasting / Credit Risk / Pricing Models / Energy Consumption / Healthcare Risk
-   Steps: Collect Training Data -> Train a Model -> Minimize Error (MSE/MAE).
-   Common Algorithm's: Linear / Ridge / Lasso / Decision Tree / Random Forest / Support Vector / Neural Network
  
- Classification:
  Definition: ML technique to predict a category (class label) from labelled input data.
  More: Model learns f(X)Class
  Types:
    Binary (spam/not, disease/healthy) using logistic regression
    Multiclass (multiple images) using Decision Tree / Random Forest / Support Vector Machine / Naive Bayes / Neural Network
  Example: Predict spam email / Fraud detection / Medical diagnosis / Sentiment analysis / Document classification / Image Recognition
  Steps: Training Data (Age, Income, Credit Score leads to approve/reject decision) -> Learn Decision Boundary (separating classes, income greater than 50k approve) -> Prediction
  Evaluation Metrics: Accuracy / Precision / Recall / F1 Score / ROC-AUC --> leads to confusion matrix
  

2. Unsupervised
- Clustering
- Dimension Reduction
- Association Rules
<div style="margin-left:120px;">
Market Basket Analysis
</div>


### Core Algorithm
A) Linear
  a. Linear Regression
    Loss: MSE
  b. Logistic Regression
    Sigmoid Function
    Log Loss
B) Tree Based
  a. Decision Tree
    Gini
    Entropy
  b. Random Forest
    Ensemble
    Reduces Variance
  c. XGBoost
    Gradient Boost
    Regularized
C) Distance Based
  KNN: Lazy learner / Sensitive to scale
D) Margin Based
  Support Vector Machines: Maximizes margin / Kernel trick
E) Clustering
  KMeans: Minimize within cluster variance / requires K
  DBScan: Density based
