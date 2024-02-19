# Titanic
Kaggle Titanic Challenge, applications for human resources

## Will employees leave or stay?
The following data set is an exploratory analysis of the Titanic challenge from Kaggle. 
https://www.kaggle.com/competitions/titanic/data

The purpose of this exercise is to practice using the Nearest Neighbor model.  While understanding the chances of surviving the Titanic are not terribly important in our modern day, the modeling methodology can be useful for various business needs.  

Instead of predicting survival, the KNN classifier could be used to predict which employees are most likely to leave. Understanding the clustering characteristics that predict those who stay, verses those who leave  can help a company identify patterns to optimize retention practices.  

For technical positions, employee turnover costs roughly one and a half times their annual salary (source: Builtin.com).  In addition to better morale and higher productivity, corporations that retain their employees have substantial monetary benefits from the savings that arise from lower recruitment needs.

## Evaluating the data
I began by researching and cleaning the dataset.  I could have used the KNN imputer to fill the missing age values predictively, but I decided to drop these values in addition to dropping the cabin column.  I created some simple histograms and countlpots to explore the dataset and then worked on my KNN classifier.

## KNN Classifier
Initially, I neglected to perform a GridSearchCV on the data and looked at the accuracy results of k values of 1, 3, and 5 (admittedly picked arbitrarily).  The KNN model predicts the outcome (survived or perished) based on the k datasets selected.  With k=1 chosen, when given a Titanic passenger to predict death or survival, the model will pick one individual with the most similar traits and use that as the result.  While this appears to be highly accurate, it is a case of overfitting.  Future data will produce unreliable results.  

Below is a plot of how the n_neighbors (k values) perform.

![k_neighbors](https://github.com/BotanicalAmy/Titanic/blob/main/n_neighbors.png)

After experimenting with the plot, I used GridSearchCV to validate my choice of n_neighbors = 9.

![test_results](https://github.com/BotanicalAmy/Titanic/blob/main/test_results.png)

### Euclidian geometry and limitations
The KNN algorithm is limited by the underlying Euclidian geometry used to calculate the nearest neighbors.  First, the computational power to run this algorithm is high.  As sample size (n) approaches infinity, the dataspace to compute distances gets crowded.  In the case of the human resource application, this method would function well for companies with 5,000 or fewer employees.  Many of these companies lack sophisticated human resource application; however, they have a small enough dataset to accurately predict which employees are most likely to leave based on past employee retention characteristics.

![Euclid](https://towardsdatascience.com/knn-algorithm-what-when-why-how-41405c16c36f)

![k_NNalgorithm](https://github.com/BotanicalAmy/Titanic/blob/main/k_NNalgorithm.png)

## Lecture notes:
I found these lecture notes on the k-NN algorithm particularly helpful in understanding the math behind this classifier.

[k-NN Lecture Notes]([https://pages.github.com/](https://www.cs.cornell.edu/courses/cs4780/2017sp/lectures/lecturenote02_kNN.html#:~:text=The%20k%2Dnearest%20neighbor%20classifier,%7Cp)1%2Fp)
