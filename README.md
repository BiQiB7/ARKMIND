# Notebook Summary

At **Feature Selection** section, used .corrs function to find the correlation of all columns with the target 'applicationStatus'. Used the correlated features as attributes.


At the 'Model Training and Hyperparameter Tuning' section, experimented upsampling and downsampling method with 5 popular classifiers - Logistic Regression, Decision Tree, SVM, XGBoost, RandomForest. This is due to class imbalance in the original dataset.

Conducted tuning using GridSearchCV on hyperparameters suggested from websites below: [decisionTree](https://www.geeksforgeeks.org/how-to-tune-a-decision-tree-in-hyperparameter-tuning/), [Logistic Regression](https://medium.com/codex/do-i-need-to-tune-logistic-regression-hyperparameters-1cb2b81fca69),[SVM](https://www.geeksforgeeks.org/svm-hyperparameter-tuning-using-gridsearchcv-ml/).


### **Performance Analysis**
![image](https://github.com/BiQiB7/ARKMIND/assets/121548392/21d78bd2-3743-443a-9492-5c2f8afdaba4)

*  XGBoost performed best with F1 scores in the 0.7-0.8 range for the positive class across all categories. It performed best with none or upsampling the minority class, where it had an F1 score of 0.78 for the positive class.

*  Logistic Regression performed poorly across all categories with F1 scores below 0.35 for the positive class regardless of the data preprocessing technique. It performed best with upsampling where it had an F1 score of 0.3 for the positive class.


*  Upsampling the minority class seems to be the best data preprocessing technique for most of the models in this case. It improved the positive class recall for Logistic Regression, Decision Tree, and SVC. It also maintained a good positive class recall for Random Forest and XGBoost, the two models that performed best overall.

*  Hyperparameter tuning using GridSearchCV to maximize f1_macro (suitable for imbalance class) yield little to no improvement to model ROC_AUC score and F1 score.

### **Rationale behind choice of models**

*  Logistic Regression for its simplicity and interpretability.
*  SVM and Decision Trees for their ability to capture complex non-linear relationships.
*  Random Forest and XGBoost for their enhanced performance, robustness to outliers and imbalanced data.

 Random Forest constructs multiple decision trees using bootstrapped samples of the dataset. This means each tree is trained on a different subset of the data, which can help ensure that the minority class is represented in some of the trees. 
 
 XGBoost is based on the gradient boosting framework, which sequentially builds trees where each tree corrects the errors of the previous ones. This iterative process can help in focusing more on the minority class instances that are often misclassified, thereby improving model performance on the imbalanced data. 
