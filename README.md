# CharityML-project
CharityML is a fictitious charity organization that wants to expand their potential donor base by sending letters to residents of the region where it is located, but only to the ones who would most likely donate. After nearly 32000 letters were sent to people in the community, CharityML determined that every donation they received came from someone that was making more than $50000 annually. So our goal is to build an algorithm to best identify potential donors and reduce overhead cost of sending mail.
# Data Understanding
The dataset is composed by 45222 records and originates from the UCI Machine Learning Repository.
Features consist a : Age, workclass, education_level, education-num, marital status, occupation, relationship, race, sex, capital-gain, capital loss, hour-per-week, native country, income 
# Transforming Skewed Continuous Features.
Algorithms can be sensitive to such distributions of values and can underperform if the range is not properly normalized so it is common practice to apply a logarithmic transformation on the data so that the very large and very small values do not negatively affect the performance of a learning algorithm. With the census dataset two features fit this description: capital-gain and capital-loss
# Normalizing Numerical Features.
Applying a scaling to the data does not change the shape of each feature distribution. We will use sklearn.preprocessing.MinMaxScaler for this on age, education-num, hours-per-week, capital-gain and capital-loss.
# Prepare Data
Convert categorical variables is by using the one-hot encoding scheme.
As always, we will now split the data (both features and their labels) into training and test sets. 80% of the data will be used for training and 20% for testing.
# Data Modeling
The purpose of generating a Naive Predictor is simply to show what a base model without any intelligence would look like. As already said, by looking at the distribution of the data, it is clear that most individuals make less than $50000 annually. Therefore a model that always predicts '0' (i.e. the individual makes less than 50k) will generally be right.The fact that the dataset is imbalanced also means that Accuracy is not very helpful because even if we obtain high accuracy the actual predictions are not necessarily that good. It is usually recommended to use Precision and Recall in this cases.
# Let’s compare the results of 3 models:
1. Decision Trees 2.Support Vector machine. 3.AdaBoost.
As already said we are focusing on the model’s ability to precisely predict those that make more than $50000 which is more important than the model’s ability to recall those individuals. AdaBoostClassifier is the one that performs best on the testing data, in terms of both the Accuracy and F-score. Moreover AdaBoostClassifier is also pretty fast to train as shown int the Time-Training_set_size histogram
Finally we can find out which are the features that provide the most predictive power. By focusing on the relationship between only a few crucial features and the target label we simplify our understanding of the phenomenon. We can do that using feature_importance_
Our goal was to predict if an individual earns more than 50k annually because the individuals that fulfill this requirement are more willing to donate to a charity. After cleaning the data and modeling them into a dataset ready to be used for ML training we tested the performance of three different models. Considering F-1 Score the best model is AdaBoostClassifier.
# Evaluate the Results:
Our goal was to predict if an individual earns more than 50k annually because the individuals that fulfill this requirement are more willing to donate to a charity. After cleaning the data and modeling them into a dataset ready to be used for ML training we tested the performance of three different models. Considering F-1 Score the best model is AdaBoostClassifier.
# reference - 
Finding Donor for charity ML Project.(Simone Rigoni).
