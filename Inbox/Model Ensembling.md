

27-02-2025 12:46

Status: #in_progress

Tags:

# Model Ensembling

### Real-life analogy
Model ensembling is like getting opinions from multiple experts instead of relying on just one person.
### In Technical terms
In machine learning, ensembling combines predictions from multiple models to produce a final prediction that's often more accurate and stable than any individual model alone. There are several ways to combine these models:

- **Voting/Averaging**: Simple combination of predictions (like taking the average of numerical predictions or majority vote for classifications)
- **Weighted Averaging**: Giving more influence to models that perform better
- **[[Stacking]]**: Using another model to learn how to best combine the predictions of base models
- **[[Bagging]]**: Training models on different random subsets of the data ([[Random Forest]] is a classic example)
- **[[Boosting]]**: Sequentially training models where each new model focuses on errors made by previous models like [[XGBoost]]

Usually each model is [[Weak Learner]]. In contrast, some other ensemble methods like [[Random Forest]] often use stronger base model 
but prevent [[overfitting]]  using other methods.





## My Questions


## References

