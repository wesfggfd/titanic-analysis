V0:Initial EDA revealed a correlation between survival probability and gender. Selected high-weight features including Pclass, Sex, SibSp, and Parch.
V0.1.0:Implemented advanced feature extraction on the Age and Fare(e.g.,cabinning, imputation), resultng in a 1.1% accurarcy improvement.
V0.1.1:
   1.Extracted top label features and binarized the Sex feature.
   2.Generated heatmaps to analyze feature correlations.
   3.Optimized model performance by:
    Increasing the number of estimators
    Expanding tree depth and leaf nodes
    Final result: 1.85% accuracy boost, achieving top 7% ranking in titanic-get-survival-competition.

Key Technical Terms References:

Feature etraction (Age&Fare processing):Refers to techniques like handling missing value and creating VALUE GROUP.
Binarization:Converting categorical features like Sex(male/female) to 0/1 values.
Heatmap correlation analysis: A method to visualize relationships between variables using color gradients.
Hyperparameter tuning: Adjusting parameters like tree depth and estimator count aligns with optimization strategies in machine learning workflows.
