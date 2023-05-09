# MaybeYouLike
### Authors: Tai Ta - Ryan Power

Project link: https://github.com/thanhtaita/MaybeYouLike/tree/main

## 1. Introduction

For this project we had the goal of using the Spotify API to get songs, and predict whether the user would like these songs based on their listening history and preferences. We basically wanted to create a recommendation app, but instead of recommending new songs, we would give songs to the model and the model would output whether we will like that song or not. 

## 2. Methods / Case Study

To start out, we picked a dataset and decided what we wanted to do with it. In our case, we picked a dataset of songs from Spotify that were labeled “like” or “dislike”. Then, we wanted to create a model to predict, given a new song, whether it would be labeled “like” or “dislike”, based on the other songs that had been labeled. Each song had a variety of attributes which the model could assign weights to in order to predict which songs would be liked. Some of these attributes were things like danceability, energy, instrumentalness, loudness, and duration. So we wanted to create a model which could predict whether the user would like the song; for example, if the user tends to like to dance, then songs with higher danceability would have a higher chance of being a “like” by the user. 

Once we had fetched our data from the Spotify API, we decided to start out by testing a few different models using default parameters. Some of the popular algorithms for this type of problem are neural networks, KNN, Content-Based filtering, and decision trees or Random Forest. We decided to try out a few of these and pick the ones that performed better. We used the default parameters on a few algorithms included in the Sklearn library and fit them to our dataset to see the initial accuracy. We were evaluating the models on two datasets, one which we got from Kaggle and one which we made in the same format as the Kaggle database but with our own songs that we liked or disliked. We decided to add this second dataset for three reasons: 1) to have more data to train models on 2) so we could input new songs that we liked or disliked to test our model on 3) to see if different models would work better for different datasets.

We created a visualization of the features within the two datasets using a color-coded pie chart. The darker colors, like the dark blue and purple, indicate a negative correlation between that feature and the user liking the song, while the lighter colors indicate a positive correlation between that feature and the user liking the song. Further, the size of the slice indicates how relevant that feature is; the larger the slice, the more important the feature.  As we can see, danceability was the most important attribute in dataset 1, while speediness was the most important in dataset 2, both having a negative correlation with the user liking the song. Both datasets disliked songs with higher danceability, loudness, and speediness, and instead preferred longer songs with higher instrumentalness.

After visualizing the data, we tested the accuracy of a few algorithms with default parameters.

Based on the initial accuracy results, we decided to pick the best algorithm and go further with it. We tested our models on two datasets. On the first dataset, Random Forest did the best, and AdaBoost was slightly worse; on the second dataset, AdaBoost did the best, and Random Forest did slightly worse. For both datasets, the neural network did not do very well. This is probably because we used default parameters, and did not adjust it to do better. Also, the other algorithms may be better suited to this type of problem.

Since Random Forest did the best on the first dataset, which we tested with first, we selected this algorithm for the first dataset, and then went to try to find the best hyperparameters for this algorithm to further improve the accuracy. To do this, we created a function which would build a model using this algorithm on a variety of hyperparameters. So we had a very long loop that tested each combination of hyperparameters, and at the end, we picked the hyperparameters that gave us the best accuracy. Below is the figure to demonstrate the accuracy of model based on different sizes of data.

After using the new hyperparameters, we found that our accuracy had increased from the initial accuracy. Now, our accuracy was over 90%, and had increased from the initial accuracy which was around 87%.

Since AdaBoost did the best on the second dataset, we selected this algorithm for the second dataset, and then went to try to find the best hyperparameters for this algorithm to further improve the accuracy. To do this, we used a similar function that we used for dataset #1 which would build a model using this algorithm on a variety of hyperparameters. The function was similar, although the hyperparameters for Random Forest and AdaBoost are different, so it was not exactly the same. Again, we had a long loop that tested each combination of hyperparameters, and at the end, we picked the hyperparameters that gave us the best accuracy.

However, after using the new hyperparameters, we found that our accuracy had decreased from the initial accuracy. Now, our accuracy was about 89%, and had decreased from the initial accuracy which was around 92%.

We can say that the model is overfitting. There are some issues about the data features that make AdaBoost unsuitable in this case. While AdaBoost can be a powerful and effective method for improving the accuracy of machine learning models, it can also be prone to overfitting. First, we only have 100 songs in the training dataset. Secondly, due to the variety of songs and the features they have, there is a lot of noise, and AdaBoost is sensitive to noisy data, which can cause it to overfit the training data. In the presence of noisy data, the weak learners may be too specialized to the training data, leading to overfitting. Due to the low accuracy of AdaBoost, we decided to train the second dataset again but with a Random Forest model.

The result turned out to be better than the AdaBoost algorithm, increasing the accuracy from 89% to 92%.

## 3.Results and Discussion

After creating two models on two different datasets, we found that among the algorithms we tested, Random Forest was the algorithm best suited to our problem. Throughout the experiment, we saw that the AdaBoost algorithm is prone to overfitting on the given data, and Random Forest clearly does better on dataset 1. We believe the variation is simply due to the variation in the datasets; both datasets were relatively small, so it is possible that one algorithm simply conformed to the respective dataset slightly better than the other. We were able to get pretty high accuracy on both datasets because the playlists we used mostly fit a theme. Most of the songs in the “liked” playlist were of a similar genre, while most of the “disliked” songs were of a different genre. This made it easier for our model to train and be accurate. Since our dataset was not huge, we were not able to get near 100% accuracy, but we were satisfied with our final results being about 90% accuracy on both datasets.





