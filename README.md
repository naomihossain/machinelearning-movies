# machinelearning-movies

## Objective
Build a Machine Learning Model that predicts whether a movie will be a hit or flop based on key features.

## Our Mission
We aim to look at which factors influence success in a movie and evaluate model performance.

## Why should we predict the success of movies?
* when a movie is produced, it takes resources, and it can become expensive/risky.
* production businesses want to be able to reduce the losses they may have and maximize return on investments.
* Predictive models help:
    * make budget decisions
    * perform better release strategy
    * streaming platfroms to identify which generes attract the biggest audience
    * predict-churn-reducing titles

## Dataset Used
The dataset we used was obtained from Kaggle's IMDB Movie Dataset. 
* contains 10,178 movies
* 12 features
    * features were mixed with some being numerical, others categorical, and even text-based attributes.
 
Kaggle: https://www.kaggle.com/datasets/ashpalsingh1525/imdb-movies-dataset

## Data Assesment and Cleaning
Isssues Encountered with Dataset:
* ‘Genre’ variable we found that there were 85 missing values
* ‘Crew’ variable we found 56 missing variables
* dataset had mixed data types that needs to be transformed
* 'Budget' and 'Revenue' variables contained zero values

Cleaning Dataset:
* categorical features such as genre, director, and country were convereted into numerical values
* made sure there were no nulls
* created a varaible hit_or_flop
* after labeling, revenue was dropped

## Target Variable
Hit_or_Flop Variable:
Since we did not have a label for success we created a binary variable, hit_or_flop, based on profitablity:
* 'Hit" if revenue > budget
* 'flop' otherwise

<knb><img width="535" alt="screenshot 1" src="images/screenshot 1.png"></kmb>

## Model 1 - Naive Bayes
We began our analysis by experimenting with a Naïve Bayes classifier to predict whether a movie would be categorized as a “hit” or a “flop”. Naïve Bayes is a relatively simple probabilistic model that assumes conditional independence among features.

With a Naïve Bayes model, we were only able to use numerical features. So, we were already limited in what features we could use. We build the model on “score” and “budget_x” only. We used Gaussian Naïve Bayes because it is designed for continuous features like what we have in our dataset. The accuracy resulted from the train dataset was 73% and the test data had 73% accuracy as well. This model resulted in a confusion matrix of 1488 true positives, 3 false positives, 544 false negatives, and 1 true negatives. This translates to 1488 flops correctly predicted as flops, 3 flops incorrectly predicted as hits, 544 hits incorrectly predicted as flops, and 1 hits correctly predicted as hits. The model strongly predicts flops, but struggles greatly at predicting hits because hits are a minority in the dataset based on features we have chosen. The classification report resulted in a very low recall for hits because the dataset is imbalanced. 

To improve this model we decided to use SMOTE so the classifier learns hits better. After using SMOTE, the model had a confusion matrix of 1058 flops correctly predicted as flops, 433 flops incorrectly predicted as hits, 349 hits incorrectly predicted as flops, and 196 hits correctly predicted as hits. This model had an accuracy score of 62%. Comparing the models, the Naive Bayes model using SMOTE predicts hits much better (from 1 to 196 correct) but it missclassifies more flops as hits (from 3 to 433 false positives). In addition, the overall accuracy of the model also decreased. The model did learn hits better, but the trade-off is more mistakes on flops.

## Model 2 - Decision Tree
To better capture interactions among features, we implemented a decision tree classifier using the movies dataset. Decision trees have a greater advantage for our dataset because they do not require assumptions of linearity or independence.
Key hyper parameters we tuned included:
* max-depth: to limit how deep the tree can grow and prevent excessive splitting
* min_samples_split: to ensure that splits only occur when enough data points are present
* min_samples_leaf: to avoid creating branches that rely on very small subsets of data
* criterion = “entropy”: selected to maximize information gain and produce more meaningful splits
* class_weights

We ran 5-fold cross validation to ensure accuracy of our model. From the confusion matrix, we can see that the model correctly identifies a large majority of successful movies, with 7,078 true positives. This demonstrates that the classifier is highly sensitive to the characteristics of films that are “hits”. The model correctly identifies 836 flops that are true flops, but it misclassifies 1,089 flops as hits. This might be because the movie's features are overlapping with “hits” making them more difficult to distinguish. These outcomes are to be expected since we had an imbalance dataset.
Across the five folds, model accuracy remained highly consistent, ranging from 0.7877, with a mean accuracy of 0.7776 and a very small standard deviation of 0.0090. This indicates that the model is stable and performs reliably across different subsets of the data. The relatively high mean accuracy suggests that our decision tree is effective at capturing the underlying patterns associated with move performance outcomes.

## Implications and Actions
We were able to find results and insights that movie studios are able to use. With these results studios can be able to make better informed production and investment decisions. Our findings are able to help know whether a movie becomes a hit or flop. 

First, we found that the budget is the strongest predictor in deciding whether a movie is a hit. Through our decision tree, we found that the first split was budget. Movies with higher budgets were seen as hits. Therefore movie productions should allocate their budget more towards movies they believe are more promising.

Next, we found audience score to be the second predictor in whether a movie is a hit. The way a movie has its cast, directors, and quality can impact the way an audience scores a movie. This can either negatively or positively impact box-office results and should be taken into consideration for performance. 

Moreover, we also found that the country where a movie is produced has an importance in whether a movie is a flop or not. Studios should take into consideration the region where their movies are filmed and consider partnering internationally as well. This should be done in order to produce successful films. 

Overall, predictive analytics can help us give greenlighting decisions. As shown our test accuracy is at 82% percent. Therefore this is a strong predictive performance for hits. Movie companies can be able to use data-driven methods in order to be able to financially invest into the best productions as well as be able to prioritize projects that have a higher predicted profitability.

## Recommendations 
Based on our findings we recommend the following steps to be taken:
* Production studios can create a model in a dashboard that evaluates proposals for new movies. This dashboard can include the estimates of budget, genre, and the expected rating. This can be able to help create a movie that is set to be a hit.
* If movies are to be predicted as hits or flops before they are released, allocate better marketing and promotional budgeting. Creating marketing campaigns that are stronger can influence the score from the audience and increase profitability.
* As seen from our analysis, we found that low-budget movies are only a hit when they have strong audience scores or genres that are favorable. Therefore, we recommend that studios should not combine low-budget films with storylines that are weak or inexperienced directors. This may lead to a movie to not hit. 
	
In summary, our recommendations emphasize how predictive analytics can meaningfully support decision-making in the film industry. By integrating data-driven models during the process of making a movie, stakeholders can strategically market resources more, align budget levels with proven audience preferences, and significantly reduce financial uncertainty and improve the likelihood of producing commercially successful films. This can be a powerful tool used for enhancing  profitability and guiding more informed, evidence based production strategies and decisions. 
















