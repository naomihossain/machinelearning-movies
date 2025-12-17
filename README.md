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



















