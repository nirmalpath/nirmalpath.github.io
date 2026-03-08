# Machine Learning Notes

## Topics

- [Go to Accuracy](#accuracy)
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
- Regression
- Classification

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
